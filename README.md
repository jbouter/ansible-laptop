# README

These playbooks will setup my basic machine to my liking. 

Supports both KDE and GNOME, and will detect which is being used at runtime.

Tested on:

* Arch Linux
* Debian Sid
* Fedora 33
* Ubuntu 20.04 & 20.10
* KDE Neon

## Preface/Notes

Before starting, a few things must be configured on the OS.

### Ubuntu/Debian

```bash
apt install -y python3-virtualenv python3-dev libxml2-dev libxslt-dev libssl-dev linux-headers-generic build-essential
```

Specifically for Ubuntu, there's the option to use the stock GDM theme. Do this by specifying `-e gdm_default_look=yes`

### Fedora

```bash
dnf install -y python3-virtualenv
dnf groupinstall -y "Development Tools"
```

### Arch Linux

```bash
sudo pacman -S python-pip python-virtualenv base-devel
```

## Setting up the Virtual Environment

Set up the virtual environment as follows:

```bash
mkdir ~/.venvs
virtualenv -p python3 ~/.venvs/ansible
source ~/.venvs/ansible/bin/activate
pip install ansible
```

Every time you work with Ansible, source the virtualenv (`source ~/.venvs/ansible/bin/activate`)

## Configuration

Username can be changed from `jeffrey` to whatever you like in `inventory/host_vars/localhost/user.yml`
GRUB password must be reconfigured by yourself in `inventory/host_Vars/localhost/vault.yml` by creating a new vault:

Create a new `yaml` file with the following content:

`inventory/host_vars/localhost/vault.yml`:

```yaml
---
grub_PBKDF2: grub.pbkdf2.sha512.10000.....
user_fullname: Firstname Lastname
user_email: email@example.com
git_signingkey: 123412341234ABCD
```

Fill in the variable from the output of the following command:

```bash
grub-mkpasswd-pbkdf2
```

Encrypt the new `yaml` file:

```bash
ansible-vault encrypt inventory/host_vars/localhost/vault.yml
```

Please read through roles for an explanation on what it all does.

```bash
ansible-playbook playbooks/provision.yml
```
