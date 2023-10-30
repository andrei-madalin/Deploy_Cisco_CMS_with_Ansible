# Deploy Cisco Meeting Server  with ANSIBLE

This guide provides step-by-step instructions for deploying Cisco Meeting Server (CMS) in your environment with Ansible. Cisco Meeting Server is a powerful collaboration platform that enables video and audio meetings for organizations. It offers scalability, security, and integration capabilities for effective communication.

## Table of Contents
- [Prerequisites](#prerequisites)
  - [Step 1: Configure WSL ](#step-1-Configure-WSL)(skip if you have already installed WSL or Linux)
  - [Step 2: Install Ansible packeges ](#step-2-Install-Ansible)
- [Variable Steps](#Variable-steps)
- [Tasks Steps](#Tasks-steps)
- [Deployment Steps](#deployment-steps)
  - [Step 1: One step only](#step-1-one-step-only)
  - [Step 2: One or more tasks](#step-2-run-one-or-more-tasks)
  
## Prerequisites
        Before you begin the Cisco Meeting Server deployment, ensure you have the following prerequisites:
        1. Ansible workstation (Windows with WSL or Linux)
        2. 
        3. A server or virtual machine with Cisco Meeting Server
                - To asign IP on CMS VM you need to:
                        - Access console VM CMS :
                                - ipv4 a add ip/mask gw
                                - ipv4 a enable 

                a. Cisco Meeting Server software installation package ( CMS version tested 3.8).
                b. Network connectivity to integrate with your existing environment.

## Variable Steps
        1. Complete hosts file with VM CMS IP (ansible_host) and username (ansible_user).
        2. Complete variable.yml with your details.

## Tasks 
        1. Network config and generate certificate 
                gen_cert.yml
                
        2. Configure webadmin component
                webadmin.yml
                
        3. Configure callbridge  component
                callbridge.yml

        4. Configure webbridge3
                webbridge3.yml

        5. Configure scheduler  component
                scheduler.yml
                
        6. Configure LDAP  integration
                ldap.yml


##  Deployment Steps
        1. One step only:
                run ansible-playbook command to config one step:
                        $ ansible-playbook -i hosts playbook.yml --ask-pass 

        2. Run only one or more tasks:
                a. Edit main.yml file and comment tasks you don't want to play.

                        ex:
                        if you want to configure just callbridge and webadmin your main.yml file may look like this:
                                                                        
                                                        # Call task gen_cert.yml
                                                        - name: Generate certificate
                                                        import_tasks: gen_cert.yml
                                                        tags: Gen_self_signed_certificate

                                                        # Call Webadmin yml file to config Webadmin interface
                                                        - name: Configure WebAdmin
                                                        import_tasks: webadmin.yml
                                                        tags: Configure_webadmin

                                                        # Call callbridge yml file to config callbridge component
                                                        - name: Configure Callbridge
                                                        import_tasks: callbridge.yml
                                                        tags: Configure_callbridge

                                                        # #    Call webbridge3 yml file to config Webbridge3 component
                                                        # - name: Configure webbridge3
                                                        #   import_tasks: webbridge3.yml
                                                        #   tags: Configure_webbridge3

                                                        #  #  Call scheduler yml file to config scheduler component
                                                        # - name: Configure scheduler
                                                        #   import_tasks: scheduler.yml
                                                        #   tags: Configure_scheduler

                                                        # #    Call ldap yml file to config ldap component
                                                        # - name: Configure ldap
                                                        #   import_tasks: ldap.yml
                                                        #   tags: Configure_ldap   


                b. run ansible-playbook command:
                        $ ansible-playbook -i hosts playbook.yml --ask-pass 
