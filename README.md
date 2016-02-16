symfony3ansible
========

Symfony3 bootstrap project. Provisioning via Vagrant+Ansible. PHP7

## Requisites

You need this your host machine:

- Virtualbox
- Vagrant
- Ansible


## Configuration
- Clone the project: # git clone git@github.com:xabierlegasa/symfony3ansible.git
- From your project root: vagrant up
- Go into the VM and download vendors: vagrant ssh; cd /var/www/symfony3ansible; composer install
- Add host name to hosts file: # echo "127.0.0.1 symfony3ansible.localhost" >> /etc/hosts
- Symfony3 is now available in symfony3ansible.localhost:8080/app_dev.php


## Keywords

Symfony3, PHP7, Vagrant, Ansible

