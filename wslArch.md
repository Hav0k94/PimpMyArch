# wslArch
Installation d'Arch avec WSL

## Installation Arch

```shell
wsl --install -d archlinux # Installation
wsl -d archlinux # Lancement
```

## Première Configuration

Création utilisateur :

```shell
useradd -m -G wheel -s /bin/bash <votre_nom_utilisateur>
passwd <votre_nom_utilisateur>
```

Mise à jour système :

```shell
pacman-key --init # Initialise le trousseau
pacman-key --populate archlinux # Ajoute les clés pour vérifier les paquets
pacman -Syu # Met à jour arch
```

Installation et configuration sudo

```shell
pacman -S sudo vim
visudo
```

Decommenter la ligne suivante :

```shell
%wheel ALL=(ALL) ALL
```

Installation paquets nécessaires :

```shell
pacman -S --noconfirm base-devel linux-headers git wget curl
```

Pour démarrer directement sur notre utilisateur :

```shell
echo "[boot]
systemd=true
[user]
default=<votre_nom_utilisateur>" >> /etc/wsl.conf
```

## Installation Ansible + Lancement playbook

```shell
sudo pacman -S python-pipx
pipx ensurepath
pipx install --include-deps ansible
pipx install ansible-lint ansible-creator
git clone https://github.com/Hav0k94/PimpMyArch.git
cd PimpMyArch
ansible-galaxy collection install -r ansible-requirements.yml
ansible-playbook installation.yml
```

Changement du Shell par défaut:

```shell
chsh -s /usr/bin/fish
```
