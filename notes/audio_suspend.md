# Fix audio problems after wakeup from suspend

* Written: 2024-01-13
* System: Fedora 39

## Problem

Sometimes on my ASUS PM53, after waking up from suspend, the headphones don't work.
The output is "(unplugged) (not available)" and physically unplugging and re-plugging
does not help.

## Solution
Reset sound chip after wakeup with systemd.

1. Create and make executable `/usr/local/bin/reset_audio`
    ```bash
    #!/bin/bash
    set -euo pipefail
    device_id=$(lspci -D | grep 'Family 17h/19h HD Audio Controller' | head -n1 | cut -d' ' -f1)
    echo 1 > "/sys/bus/pci/devices/$device_id/remove"
    echo 1 > /sys/bus/pci/rescan
    ```
2. Create `/etc/systemd/system/reset_audio.service`
    ```ini
    [Unit]
    Description=Reset audio chip
    After=suspend.target hibernate.target hybrid-sleep.target suspend-then-hibernate.target

    [Service]
    ExecStart=/usr/local/bin/reset_audio

    [Install]
    WantedBy=suspend.target hibernate.target hybrid-sleep.target suspend-then-hibernate.target
    ```
3. Enable the service: 
    ```bash
    sudo systemctl enable reset_audio
    ```
