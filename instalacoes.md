# Keychain

## Instalando

```bash
$ sudo apt install keychain -y
```

## Configurando

Adicionar ao arquivo de env (`.zshrc`, `.bashrc`, etc.)

```bash
/usr/bin/keychain --clear $HOME/.ssh/id_rsa --quiet
source $HOME/.keychain/$(cat /etc/hostname)-sh
```
