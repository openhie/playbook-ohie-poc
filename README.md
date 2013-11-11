playbook-ohie-poc
======================

Ansible playbook for deploying [openmrs](http://openmrs.org).

## What it does
* Installs Openjdk-jre-7, tomcat7, and mysql-server.
* Configures tomcat and mysql.
* Downloads and installs OpenMRS war file

## Requirements
* Ansible **1.3+** installed on client.
* Debian based distro installed on server (tested with Ubuntu 12.04).
* root username/password on server, ssh installed.

## Vars and setup
You will need to copy `group_vars/all.example` to `group_vars/all` then edit `group_vars/all` with the mysql root password you want to set or have already set.

Also copy `hosts.example` to `hosts` and enter the ip or hostname of your server in place of the ip.

By default we try to login with root via ssh, if you have another user with sudo access on your server(e.g. Amazon) edit `site.yml` and change the user and uncomment the sudo line.

## Running the play
`ansible-playbook -k -i hosts site.yml`

Drop the -k if you are logging in with a public/private key. 

`ansible-playbook -i hosts site.yml`

After this is complete your initial setup should be available at $ip:8080/openmrs
