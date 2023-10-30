# Cisco Meeting Server Deployment Guide

This guide provides step-by-step instructions for deploying Cisco Meeting Server (CMS) in your environment. Cisco Meeting Server is a powerful collaboration platform that enables video and audio meetings for organizations. It offers scalability, security, and integration capabilities for effective communication.

## Table of Contents
- [Prerequisites](#prerequisites)
- [Variable Steps](#Variable-steps)
- [Deployment Steps](#deployment-steps)
  - [Step 1: Obtain Cisco Meeting Server Software](#step-1-obtain-cisco-meeting-server-software)
  - [Step 2: Install and Configure Hardware](#step-2-install-and-configure-hardware)
  - [Step 3: Installation of CMS Software](#step-3-installation-of-cms-software)
  - [Step 4: Initial Configuration](#step-4-initial-configuration)
  - [Step 5: Licensing](#step-5-licensing)


Ansible Playbook to deploy Cisco Meeting Server with :
- callbridge
- webbridge3
- webadmin
- scheduler
- ldap integration


## Prerequisites
Before you begin the Cisco Meeting Server deployment, ensure you have the following prerequisites:

- A server or virtual machine 
        - To asign IP on CMS VM you need to:
                - Access console VM CMS :
                        - ipv4 a add ip/mask gw
                        - ipv4 a enable 

- Cisco Meeting Server software installation package ( CMS version tested 3.8).
- Network connectivity to integrate with your existing environment.

## Variable Steps
1. Complete hosts file with VM CMS IP (ansible_host) and username (ansible_user).
2. Complete vaiable.yml with your details.


##  Deployment Steps
1. One step only:
        Run ansible-playbook command to config one step:
                 $ ansible-playbook -i hosts playbook.yml --ask-pass 

2. Run only one or more tasks:
        Edit main.yml file and comment tasks you don't want to play.


        

