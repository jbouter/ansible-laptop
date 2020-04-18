# README

These playbooks will setup my basic machine to my liking.

Tested on:

* Ubuntu 20.04
* Fedora 32

## Install base packages

A certain set of packages I always want installed

* htop
* atop
* iotop
* direnv
* borgbackup
* ffmpeg *(Ubuntu only)*
* imagemagick
* libreoffice
* pwgen
* wireguard
* qemu
* libvirt
* virt-manager
* tmux
* vim
* ubuntu-restricted-extras *(Ubuntu only)*
* ubuntu-restricted-addons *(Ubuntu only)*

## Install base snaps

A certain set of snap packages I always want installed

* cawbird
* discord
* docker
* mattermost-desktop
* spotify
* telegram-desktop
* codium *(classic)*
* kubectl *(classic)*

## etckeeper

etckeeper will keep a git repository of `/etc` and update it when your package manager is run

## gnome

The gnome tasks will only be run specifically on Ubuntu, and set **gdm3** to have the default look

## google-chrome

Configure the Google Chrome repositories and install `google-chrome-stable`

## hardening

Execute some basic hardening based upon [CIS Benchmarks](https://www.cisecurity.org/cis-benchmarks/)

## libinput

Configure libinput to have support for my Magic Trackpad 2

## Nextcloud

Configure repositories *(Ubuntu/Debian only)* and install nextcloud-client
