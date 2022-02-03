# Provison a Web Server with Automation and Deploy a Website on it 
Project #1 in a series implementing a list of [Practical DevOps Project Ideas](https://www.tutorialworks.com/devops-project-ideas/): "Website"


## Introduction & Goals 
This is a simple project to:
- Create a virtual machine 
- Install a web server on the VM 
- Configure the server to serve up some basic HTML 
- Make the server accessible locally

## Technologies Used 
- [Vagrant](https://www.vagrantup.com/) for provisioning a [Ubuntu](https://ubuntu.com/) VM 
- [Nginx](http://nginx.org/) for web server 

## Architecture Diagram (if any) / Infrastructure 
- Created infrastructure: a Ubuntu VM with Nginx web server

## How It Works (High-Level)
- Vagrant creates the VM, through shell provisioner sets up nginx and appropriate files
(including a Hello World), and through file provisioner brings a server block config file from the host machine directory(simple-site) to the sites-available and sites-enabled folders for nginx to pick it up.
- UFW is used to set up a host-based firewall to open up port 81 
- Nginx is restarted to make it aware of changes, as it starts upon installation by default. 

## Pre-reqs
- Vagrant 

## How To Use
- Run ` vagrant up` 
- Access the hello world at ` http://192.168.33.10:81/ ` 

## TO-DOs
- Could use config.vm.synced_folder to not have to upload --> copy the file 
- Deploy analogous solution to the cloud
- Incorporate a non-Vagrant shell provisioner like Ansible to configure the server

## Lessons Learned / Observations
- Systemctl vs. other ways of managing services: https://allthings.how/how-to-fix-systemctl-command-not-found-error-in-linux/
- Setting up nginx was mostly complicated by not knowing server blocks, but those are simple once you start to work with the config files. 

## Resources
- https://devopscube.com/vagrant-tutorial-beginners/
- https://jgefroh.medium.com/a-guide-to-using-nginx-for-static-websites-d96a9d034940
- https://stackoverflow.com/questions/65329229/multiple-site-on-localhost-served-by-nginx-without-domain-name
