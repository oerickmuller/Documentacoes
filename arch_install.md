# Post Install Arch Linux

## Install yay
Yay is a helper for packages install: [yay](https://github.com/Jguer/yay)

```bash
# pacman -S --needed git base-devel
$ git clone https://aur.archlinux.org/yay-bin.git
$ cd yay-bin
$ makepkg -si
```

## Install zsh and oh-my-zsh

```bash
$ yay -S zsh
$ sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

