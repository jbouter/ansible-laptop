# README

These playbooks will setup my basic machine to my liking.

Tested on:

* Ubuntu 20.04

## Install base packages

A certain set of packages I always want installed

* htop
* atop
* iotop
* direnv
* borgbackup
* ffmpeg
* imagemagick
* libreoffice
* pwgen
* wireguard
* qemu
* libvirt
* virt-manager
* tmux
* vim
* ubuntu-restricted-extras
* ubuntu-restricted-addons

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

## Chrony

Install the NTP daemon chrony and configure it.

This disables `systemd-timesyncd`.

## dnsmasq

Install dnsmasq and configure it to be used as the internal caching mechanism
used within NetworkManager.

This disables `systemd-resolved`.

## etckeeper

etckeeper will keep a git repository of `/etc` and update it when your package manager is run

## gnome

The gnome tasks is specifically for Ubuntu, and set **gdm3** to have the default look

## google-chrome

Configure the Google Chrome repositories and install `google-chrome-stable`

## GRUB

Configure the default GRUB settings

## hardening

Execute some basic hardening based upon [CIS Benchmarks](https://www.cisecurity.org/cis-benchmarks/)

## libinput

Configure libinput to have support for my Magic Trackpad 2

## Nextcloud

Configure repositories and install nextcloud-client
