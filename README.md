# Ansible playbook - Nginx with SSL certificate
Quickly setup your Raspberry Pi - with nginx and SSL certificate using Let's encrypt for multiple services and sub-domains.

### The reason why:
Let's say you want to route the traffic from a public sub-domain like "foo.example.com" to a service/website running in your local network at home.
So if a user visit "foo.example.com" you want him (or her) to be able to access the service/website your are running in your local network.
In this case sub-domains of example.com (foo.example.com) is being routed via DNS, to the public IP of your ISP.
Using IP forwarding you can redirect all traffic from the port 80 and 443 to the nginx service IP.

Nginx is then redirecting the traffic to the different services  
foo.example.com -> 192.168.x.y:1234  
bar.example.com -> 192.168.x.z:4321

## Pre-installation 
So in this case there are some steps to be taken.
1. You need to have a domain registered (example.com)
2. You should in the case above create the subdomain foo.
3. Point the sub-domain (foo.example.com) to the IP of our ISP by changing the "A record"
   host record: foo -> points to IP of your ISP (xx.xx.xx.xx)  
   you can do this by connecting to the network and googling "what's my ip")
4. In your router/modem you should route all traffic from port 80 and 443 to the IP of the raspberry pi where nginx will be installed
5. Setup your Raspberry Pi by following the [installation](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) guide on the official site.
6. After all of this is done follow the [installation](#installation) steps below

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
ansible-playbook playbook.yml -i hosts
```

## Requirements
[Ansible](http://www.ansible.com/) is required. 

### Installing Ansible on Mac
if you haven't installed ansible yet please go to: [ansible for mac](http://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#latest-releases-via-pip)
