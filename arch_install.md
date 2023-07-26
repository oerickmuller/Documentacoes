# Post Install Arch Linux

## Install yay
Yay is a helper for packages install: [yay](https://github.com/Jguer/yay)

```bash
$ sudo pacman -S --needed git base-devel
$ git clone https://aur.archlinux.org/yay-bin.git
$ cd yay-bin
$ makepkg -si
```

## Install zsh and oh-my-zsh
```bash
$ yay -S zsh
$ sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

## Install some command line utilities

- **micro** is a command line editor that's simpler than nano.
- **exa** is a `ls` replacement
- **ripgrep**, or `rg`, is a fast grep replacement
- **bat** is a `cat` replacement

```sh
$ yay -S micro exa ripgrep bat
```

## Install media codecs

```bash
$ yay -S gst-libav gst-plugins-base gst-plugins-good gst-plugins-bad gst-plugins-ugly gstreamer-vaapi x265 x264 lame
```

## Install fonts

```bash
yay -S adobe-source-sans-pro-fonts ttf-dejavu ttf-opensans noto-fonts freetype2 terminus-font ttf-bitstream-vera ttf-dejavu ttf-droid ttf-fira-mono ttf-fira-sans ttf-freefont ttf-inconsolata ttf-liberation libertinus-font ttf-ms-win11-auto
```