# README

These playbooks will setup my basic machine to my liking.

Tested on:

* Ubuntu 20.04
* Fedora 32


## Preface/Notes

In order to allow this to run, install the following packages

Ubuntu:

```bash
apt install -y python3-virtualenv python3-dev libxml2-dev libxslt-dev libssl-dev linux-headers-generic build-essential
```

Fedora:

```bash
dnf install -y python3-virtualenv
dnf groupinstall -y "Development Tools"
```

Set up the virtual environment as follows:

```bash
mkdir ~/.venvs
virtualenv -p python3 ~/.venvs/ansible
source ~/.venvs/ansible/bin/activate
pip install ansible
```

Every time you work with Ansible, source the virtualenv (`source ~/.venvs/ansible/bin/activate`)

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
