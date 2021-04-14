<a href="https://github.com/jbouter/ansible-laptop" style="color: black;">
    <h1 align="center">Ansible Laptop</h1>
</a>
<p align="center">
    <img src="images/laptop.png" alt=laptop-ansible width="50%", height="50%" />
    <hr>
</p>
<p align="center">
    <a href="https://github.com/jbouter/ansible-laptop/actions">
        <img src="https://img.shields.io/github/workflow/status/jbouter/ansible-laptop/Ansible%20Lint?style=for-the-badge&color=blue"
            alt="GitHub Workflow Status">
    </a><br>
    <b>ansible laptop</b> will set up my laptop to my liking. Supports both KDE and GNOME.<br>
    <a href="https://docs.ansible.com/ansible/latest/index.html"><strong>Explore the Ansible docs »</strong></a>
    <hr>
</p>

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
apt install -y python3-virtualenv python3-dev python3-wheel libxml2-dev libxslt-dev libssl-dev linux-headers-generic build-essential
```

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
python3 -m venv ~/.venvs/ansible
source ~/.venvs/ansible/bin/activate
pip install wheel
pip install ansible
```

Every time you work with Ansible, source the virtualenv (`source ~/.venvs/ansible/bin/activate`)

## Downloading the required ansible collections from Ansible Galaxy

Download the required Ansible collections from galaxy by running the following command

```bash
ansible-galaxy install -r collections/requirements.yml
```

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

## Sources

Icons made by [Prosymbols](https://www.flaticon.com/authors/prosymbols) from [www.flaticon.com](https://www.flaticon.com/)
