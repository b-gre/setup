# Install the nice things

## On Fedora (sway spin)

```shell
sudo rpmkeys --import https://gitlab.com/paulcarroty/vscodium-deb-rpm-repo/-/raw/master/pub.gpg
printf "[gitlab.com_paulcarroty_vscodium_repo]\nname=download.vscodium.com\nbaseurl=https://download.vscodium.com/rpms/\nenabled=1\ngpgcheck=1\nrepo_gpgcheck=1\ngpgkey=https://gitlab.com/paulcarroty/vscodium-deb-rpm-repo/-/raw/master/pub.gpg\nmetadata_expire=1h" | sudo tee -a /etc/yum.repos.d/vscodium.repo

sudo dnf install \
    https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-39.noarch.rpm \
    https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-39.noarch.rpm

sudo dnf install vim mc ripgrep pv git bat btop htop reptyr openh264 fontawesome-fonts-all fira-code-fonts mold clang codium dnf-automatic flatpak
sudo dnf install stow zoxide
sudo dnf swap mesa-vdpau-drivers mesa-vdpau-drivers-freeworld
sudo dnf swap dunst mako
sudo dnf remove firefox

flatpak install org.chromium.Chromium org.mozilla.firefox org.libreoffice.LibreOffice

xdg-settings set default-web-browser org.mozilla.firefox.desktop
```
