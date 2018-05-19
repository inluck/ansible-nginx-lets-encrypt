# Ansible playbook - Nginx with SSL certificate
Quickly setup your Raspberry Pi - with nginx and SSL certificate using Let's encrypt for multiple services and sub-domains.

### The reason why:
You want to route the traffic from a public domain like example.com to a service running in your local network at home.
So if a user visit foo.example.com you want him (or her) to be able to access the service your are running in your local network.
In this case sub-domains of example.com (foo.example.com) is being routed via DNS, to the public ip of your ISP.
Using Ip Forwarding we are redirecting all traffic trow the port 80 and 443 to the nginx service ip.

Nginx is then redirecting the traffic to the different services  
foo.example.com -> 192.168.x.y:1234  
bar.example.com -> 192.168.x.z:4321

## Pre-installation 
So in this case there are some steps to be taken.
1. You need to have a domain registered (example.com)
2. You should in the case above create the subdomain foo.
3. Point the subdomain (foo.example.com) to the ip of our ISP by changing the "A record"
   host record: foo -> points to Ip of your ISP (xx.xx.xx.xx)  
   you can do this by connecting to the network and googling "what's my ip")
4. In your Router/modem you should route all traffic coming on port 80 and 443 to the ip of the raspberry pi where nginx will be installed
5. follow the [installation](#installation) steps below

## Installation

Clone and setup the ansible script. 

```
git clone https://github.com/reindrich/ansible-nginx-lets-encrypt.git
cd ansible-nginx-lets-encrypt
cp hosts.example hosts
cp vars-example.yml vars.yml
```

Edit the `hosts` and `vars.yml` files.

Deploy using [ansible](http://www.ansible.com) (install instructions for ansible are in [requirements](#requirements) below).

```
ansible-playbook playbook1.yml -i hosts
```

## Requirements
[Ansible](http://www.ansible.com/) is required. 

### Installing Ansible on Mac
if you haven't installed ansible yet please go to: [ansible for mac](http://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#latest-releases-via-pip)
