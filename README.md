# PimpMyArch
Set-up Arch rapidement

## First Step : Archinstall
Installation [Arch](https://fr.mirrors.cicku.me/archlinux/iso/2024.08.01/archlinux-2024.08.01-x86_64.iso) via script [archinstall](https://github.com/archlinux/archinstall)

```shell
sudo pacman -S archinstall
```

## Second Step : Architect
Script post-installation [Architect](https://github.com/Cardiacman13/Architect)

```bash
sudo pacman -S --needed git base-devel \
  && git clone https://github.com/Gaming-Linux-FR/Architect.git ~/Architect \
  && cd ~/Architect \
  && chmod +x ./architect.sh \
  && ./architect.sh
```

## Optionnal : Hyprland
Window Manage [Hyprland](https://github.com/JaKooLit/Arch-Hyprland) customized by JaKooLit

```bash
git clone --depth=1 https://github.com/JaKooLit/Arch-Hyprland.git ~/Arch-Hyprland
cd ~/Arch-Hyprland
chmod +x install.sh
./install.sh
```

## Installation AUR

### Installation yay

Installation de [yay](https://github.com/Jguer/yay)

```bash
sudo pacman -S --needed git base-devel
git clone https://aur.archlinux.org/yay-bin.git
cd yay-bin
makepkg -si
```

### Installation PARU

(Si on péfère utiliser [PARU](https://github.com/Morganamilo/paru) au lieu de yay)

```bash
sudo pacman -S --needed git base-devel
git clone https://aur.archlinux.org/paru.git
cd paru
makepkg -si
```

## Installation des paquets via Ansible

D'abord il nous faut installer Ansible sur notre machine
```bash
sudo pacman -S python-pipx
pipx ensurepath
pipx install --include-deps ansible
pipx install ansible-lint ansible-creator
git clone https://github.com/Hav0k94/PimpMyArch.git
cd PimpMyArch
ansible-playbook installation.yml
```

Certains paquets nécessitant AUR ne sont pas encore installable via le playbook

## Installation de paquet à la main

Installation de paquets supplémentaires pour l'utilisation de fish

 - **Eza** : Alternative moderner à *ls*. ([Repo](https://github.com/eza-community/eza))
 ```shell
sudo pacman -S eza
```

 - **bat** : Alternative à *cat* avec syntax highlighting. ([Repo](https://github.com/sharkdp/bat))
 ```shell
sudo pacman -S bat
```

 - **find-the-command** : Advanced command-not-found hook for bash, fish and zsh using the power of pacman. ([Repo](https://github.com/agura-lex/find-the-command))
```shell
yay find-the-command
```

 - **OnlyOffice** : Alternative à Office365. ([Repo](https://github.com/ONLYOFFICE/DesktopEditors))
 ```shell
yay -S onlyoffice-bin
```

 - **alacritty** : Alacritty is a simple, GPU-accelerated terminal emulator. ([Repo](https://github.com/ONLYOFFICE/DesktopEditors))
 ```shell
sudo pacman -S alacritty
```

 - **neovim** : Better Vim ([Repo](https://github.com/neovim/neovim))
 ```shell
sudo pacman -S neovim
```

 - **NvChad** : Combiné à nvim ([Repo](https://github.com/NvChad/NvChad))
 ```shell
git clone https://github.com/NvChad/starter ~/.config/nvim && nvim
```

 - **Starship** : Prompt customisé ([Repo](https://github.com/starship/starship))
 ```shell
curl -sS https://starship.rs/install.sh | sh
```

Ajouter le fichier *starship.toml* dans le dossier *.config* de l'utilisateur.

## Config à changer

- **fish**
 ```shell
mv ~/.config/fish ~/.config/fish.old
git clone https://github.com/Hav0k94/PimpMyArch.git
cd PimpMyArch
cp .config/fish ~/.config/fish
```
