> [!WARNING]  
> No longer maintained. I have since switched to a current Spotify version and can therefore no longer guarantee that this still works.

# Spotify Old Library Linux

Restore the old Spotify version which still has the old library on Linux.


## Installation

Clone the repo, construct the DEB and run the script

```sh
git clone https://github.com/D3SOX/spotify-old-library-linux
cd spotify-old-library-linux
./construct.sh
```

### Arch Linux

Fixing on Arch Linux (and distros based on it) is supported when using [`spotify-launcher`](https://archlinux.org/packages/spotify-launcher/)

```sh
./fix-spotify-archlinux.sh
```

### Debian

Fixing on Debian (and distros based on it) is supported when using the Spotify DEB package 

```sh
./fix-spotify-debian.sh
```

## Exclude from auto updating

> [!IMPORTANT]  
> You might have to exclude Spotify from auto updating when using this

### Arch Linux

On Arch Linux you have to modify the application menu entry and always start it with `--skip-update`

```sh
sed -i "s/^Exec=.*/Exec=spotify-launcher --skip-update %U/" /usr/share/applications/spotify-launcher.desktop
```

You should probably also add a hook that preserves this change. To do so create a file at `/etc/pacman.d/hooks/spotify-launcher.hook` with the following contents
```ini
[Trigger]
Operation = Install
Operation = Upgrade
Type = Package
Target = spotify-launcher
[Action]
Description = Disabling spotify-launcher updates...
Depends = sed
When = PostTransaction
Exec = /usr/bin/sed -i -e 's/^Exec=.*/Exec=spotify-launcher --skip-update %U/' /usr/share/applications/spotify-launcher.desktop
```

### Debian

On Debian you have to exclude the package from being updated

```sh
sudo apt-mark hold spotify-client
```

## Actually disable the new library

You might have to still disable the new library inside the experimental features menu. You can get that by installing [Spicetify](https://spicetify.app/). The last confirmed working version is [v2.34.1](https://github.com/spicetify/spicetify-cli/releases/tag/v2.34.1). Then follow the steps
- Click on your name in the top right
- Click on "Experimental features"
- Search for `library x`
- Disable all checkboxes
