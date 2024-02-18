# Notes and dotfiles for my linux setup

## Notes

* [Install the nice things](notes/install.md)
* [Dotfiles](dotfiles/readme.md)
* [Fix audio problems after wakeup from suspend](notes/audio_suspend.md)
* Grant to a flatpak app access to additional directories
    ```shell
    flatpak override -u --filesystem=$PATH $APP
    ```
* Set default browser: 
    ```shell
    xdg-settings set default-web-browser org.mozilla.firefox.desktop
    ```
* [git stuff](notes/git.md)