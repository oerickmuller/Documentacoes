# Post Install Arch Linux

## Install yay
Yay is a helper for packages install: [yay](https://github.com/Jguer/yay)

```bash
sudo pacman -S --needed git base-devel
git clone https://aur.archlinux.org/yay-bin.git
cd yay-bin
makepkg -si
```

## Install zsh and oh-my-zsh
```bash
yay -S zsh
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

## Install some command line utilities

- **micro** is a command line editor that's simpler than nano.
- **exa** is a `ls` replacement
- **ripgrep**, or `rg`, a faster grep
- **bat** is a `cat` replacement
- **zellij** and **tmux** are terminal multiplexers, not required but useful for command line freaks (like me)

```sh
yay -S micro exa ripgrep bat zellij tmux
```

## Enable bluetooth

```
yay -S bluez blueman bluez-utils
sudo modprobe btusb
sudo systemctl enable bluetooth && sudo systemctl start bluetooth
```

## Install media codecs and software

```bash
yay -S gst-libav gst-plugins-base gst-plugins-good gst-plugins-bad gst-plugins-ugly gstreamer-vaapi x265 x264 lame vlc
```

## Install fonts

```bash
yay -S adobe-source-sans-pro-fonts ttf-dejavu ttf-opensans noto-fonts freetype2 terminus-font ttf-bitstream-vera ttf-dejavu ttf-droid ttf-fira-mono ttf-fira-sans ttf-freefont ttf-inconsolata ttf-liberation libertinus-font ttf-ms-win11-auto
```

## Enable pacman autoclean 

If you're short on space disk, this is *recommended*:

```bash
yay -S pacman-contrib
sudo mkdir /etc/pacman.d/hooks
sudo micro /etc/pacman.d/hooks/clean_package_cache.hook
```

On the editor, paste this code:

```
[Trigger]
Operation = Upgrade
Operation = Install
Operation = Remove
Type = Package
Target = *
[Action]
Description = Cleaning pacman cache...
When = PostTransaction
Exec = /usr/bin/paccache -rk 2
```

## Install browsers

```bash
yay -S firefox google-chrome vivaldi microsoft-edge-stable-bin
```

## Install image editors and a screenshot helper

```bash
yay -S shutter gimp inkscape conjure
```

## Some tweaks:

### Adjust swappiness:

If your machine has enough memory, you can reduce the frequency of disk use for offloading memory.

```
sudo micro /etc/sysctl.d/99-swappiness.conf
```

Add this line:

```
vm.swappiness = 10
```

## For developers:

### Install some nerd fonts

### Install visual studio code

```bash
yay -S visual-studio-code-bin
```

### Build and install neovim

```bash
yay -S base-devel cmake unzip ninja curl
git clone https://github.com/neovim/neovim
cd neovim && make CMAKE_BUILD_TYPE=RelWithDebInfo
sudo make install
```

### Install python via pyenv

```bash
yay -S --needed base-devel openssl zlib xz tk
curl https://pyenv.run | bash
```

Don't forget to update the `.zshenv`  file as needed.

Install python 3.9, 3.10 and 3.11 using 

```bash
for i in 9 10 11; do
  pyenv install "3.$i"
done
```

### Install nodejs via nvm

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.4/install.sh | bash
```

Install latest node.js LTS version using

```bash
nvm install --lts
```

### Install docker

```bash
yay -S docker
sudo usermod -aG docker $USER
yay -S docker-compose
sudo systemctl enable docker.service
sudo systemctl start docker.service
```

### Install go

Download the Linux installer from https://go.dev/dl/

```bash
sudo tar -C /usr/local -xzf go1.20.6.linux-amd64.tar.gz 
mkd
```

### Install rust

### Install openjdk

### Install .net/mono

### Bonus: set a special python environment for tools
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE1ODc3NjM0OTQsLTIwODc4NTMxNTgsLT
Y0ODU1Mzg5NSw1NTAwNDA4NjEsNDE5ODgyNzE4LDE3MzU4OTcw
NiwzMDA2MDg4NDIsLTEwMzgwMDEwMDldfQ==
-->