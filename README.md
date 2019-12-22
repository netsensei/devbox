# Devbox

[![Software License](https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square)](LICENSE.md)

> “I've always said to myself that if a little pocket calculator can do it why shouldn't I?” 
-- Roald Dahl, Matilda

Devbox is a barebones virtual machine. You get CentOS with a basic unconfigured LAMP stack. 
That's it. Everything else is up to you.

## Installation

Clone or download the repo, provision, run.

```bash
$ git clone https://github.com/netsensei/devbox.git devbox
$ cd devbox
$ ansible-galaxy install -p provisioning/roles -r provisioning/requirements.yml
$ vagrant up
```

## Why a minimalist approach?

Because I wanted a virtual machine I can take off the shelf and have up and 
running in 5 minutes tops.

Building countless ansible boxes has taught me a few things:

* One-off tweaks and glue code are inevitable.
* Duplication and adaptation make maintenance a hard problem.
* Using third party boilerplate entails importing someone else's problems.

A barebones box serves as a jumping board leaving the choice entirely with the 
developer whether or not to add specific boilerplate, glue code or tweaks.

... or simply configure everything by hand inside the VM.

## What's inside?

The box comes with an Ansible playbook and several roles by [Jeff Geerling](http://github.com/geerlingguy).

* Git
* Apache
* PHP
* MySQL
* PostgreSQL
* Composer

Optional:

* php-xdebug
* php-xprof

## Shared folders on Fedora 31

NFS sharing will be blocked by firewalld on Fedora. You will need to add these rules
to allow nfs, mountd and rpc-bind to communicate with the nfs-client in the box:

```bash
firewall-cmd --permanent --add-service=nfs
firewall-cmd --permanent --add-service=mountd
firewall-cmd --permanent --add-service=rpc-bind
firewall-cmd --reload
```

## License

The MIT License (MIT). Please see [LICENSE](LICENSE.md) File for more information.
