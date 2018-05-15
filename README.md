# Ansible playbook - Nginx with SSL certificate
Quickly setup your Raspberry Pi - with nginx and SSL certificate using Let's encrypt for multiple services and sub-domains.

## Installation

Clone and setup the ansible script. 

```
git clone https://github.com/reindrich/ansible-nginx-lets-encrypt.git
cd ansible-nginx-lets-encrypt
cp hosts.example hosts
```

Edit the `hosts` files.

Deploy using [ansible](http://www.ansible.com) (install instructions for ansible are in [requirements](#requirements) below).

```
ansible-playbook playbook.yml -i hosts
```

## Requirements
[Ansible](http://www.ansible.com/) is required. 

### Installing Ansible on Mac
if you haven't installed ansible yet please go to: [ansible for mac](http://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#latest-releases-via-pip)
