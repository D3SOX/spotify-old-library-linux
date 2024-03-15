# Spotify Old Library Linux

Restore the old Spotify library on Linux.


## Installation

Clone the repo, construct the DEB and run the script

```sh
git clone https://github.com/D3SOX/spotify-old-library-linux
cd spotify-old-library-linux
./construct.sh
```

### Arch Linux

Fixing on Arch Linux is supported when using [`spotify-launcher`](https://archlinux.org/packages/spotify-launcher/)

```sh
./fix-spotify-archlinux.sh
```

### Debian

Fixing on Debian is supported when using the Spotify DEB package 

```sh
./fix-spotify-debian.sh
```

### Exclude from auto updating

> [!IMPORTANT]  
> You might have to exclude Spotify from auto updating when using this

### Arch Linux

On Arch Linux you have to modify the application menu entry and always start it with `--skip-update`

```sh
sed -i sed -i "s/^Exec=.*/Exec=spotify-launcher --skip-update %U/" /usr/share/applications/spotify-launcher.desktop
```

### Debian

On Debian you have to exclude the package from being updated

```sh
sudo apt-mark hold spotify-client
```
