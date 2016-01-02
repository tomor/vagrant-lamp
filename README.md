# Vagrant LAMP
**! this project in development - not ready to use !**

This project was created basically for myself to be able to quickly prepare web development
environment, but feel free to use it or fork it and change according to your needs.

## Installation
* Install [Vagrant](https://docs.vagrantup.com/v2/installation/index.html "Vagrant docs - Istallation")
* Install [VirtualBox](https://www.virtualbox.org/)
* Install [Ansible](http://docs.ansible.com/intro_installation.html)
* Install Vagrant plugin for VirtualBox guest additions
```bash
> vagrant plugin install vagrant-vbguest
```
* Install NFS server on your host (do not forget to allow it in firewall)


## Basic facts
* you will get: Apache/2.4.17 (Fedora), mysql, php 5.6
* tested on host: Fedora23, Vagrant 1.8.1, VirtualBox 5.0.10, ansible 1.9.4
* you are expected to create multiple virtualhosts
* vagrant base box: fedora/23-cloud-base
* vagrant provisioned by Ansible


## Anatomy of the development environment
- actual `.` vagrant directory on the host is shared with the guest `/vagrant` directory via NFS
- there are several directories, each with own purpose
```bash
  ansible  # provisioning for the vagrant box
  config   # directory with configurations (e.g. apache virtualhosts)
  projects # all web project source codes are meant to be stored here in subdirectories
  tools    # scripts (mostly bash) which should help with some dev tasks

## Configuraton of host machine
* to be able to use adminer (mysql web admin) add this line to your `hosts` file
```bash
192.168.25.25 mysql.vg
```

# TODOs
- install php
- install mysql
- setup apache
 - allow virtualhosts in the config/apache/virtualhosts
- test a php project
- create tool for quick virtualhost creation
- install adminer (create default virtualhost for it)
- domains for the box - idea:
   - mysql.vg - access adminner(mysql)
   - project01.vg  - access some project
   - general idea: machine is connected with 1st lvl domain (this one will be \*.vg)
- install composer
- install npm
- install mail catcher - see https://box.scotch.io/  

## Similar projects
* https://github.com/geerlingguy/ansible-vagrant-examples/tree/master/lamp
* https://box.scotch.io/  
* https://github.com/pesterhazy/vagrant-lamp-ansible

## Another good sources
* https://github.com/geerlingguy?tab=repositories
* https://github.com/ansible/ansible-examples/tree/master/lamp_simple
* https://github.com/dustymabe/vagrantdirs
* https://github.com/ansible/ansible-examples/tree/master/lamp_simple_rhel7
* http://phansible.com/#section-webservers
