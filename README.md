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


## Basic facts
* you will get: apache, mysql, php 5.6
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
