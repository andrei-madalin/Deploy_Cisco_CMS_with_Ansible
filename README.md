# Deploy Cisco Meeting Server  with ANSIBLE

This guide demonstrate how Ansible can configure almost all components of Cisco Meeting Server (CMS).

## Table of Contents
- [Prerequisites](#prerequisites)
  - [Step 1: Configure WSL ](#step-1-Configure-WSL)(skip if you have already installed WSL or Linux)
  - [Step 2: Install Ansible packages ](#step-2-Install-Ansible)
  - [Step 3: Configure network on CMS ](#step-3-configure-netork-CMS)
- [Variable Steps](#Variable-steps)
  - [Step 1: host file](#step-1-host-file)
  - [Step 2: variable file](#step-2-variable-file)
- [Tasks Steps](#Tasks-steps)
  - [Step 1: Network config & generate certificate](#step-1-gen_cert)
  - [Step 2: Configure Webadmin](#step-2-Webadmin)
  - [Step 3: Configure Callbridge](#step-3-Callbridge)
  - [Step 4: Configure Webbridge3](#step-4-Webbridge3)
  - [Step 5: Configure Scheduler](#step-5-Scheduler)
  - [Step 6: Configure LDAP](#step-6-LDAP)
  - [Step 7: Create Call_Leg_Profiles](#step-7-Call_Leg_Profiles)
  - [Step 8: Create Call_Profiles](#step-8-Call_Profiles)
  - [Step 9: Create CoSpaceTemplates](#step-9-CoSpaceTemplates)
- [Deployment Steps](#deployment-steps)
  - [Step 1: One step only](#step-1-one-step-only)
  - [Step 2: One or more tasks](#step-2-run-one-or-more-tasks)
  
## Prerequisites
        Before you begin the Cisco Meeting Server deployment, ensure you have the following prerequisites:
        
        1. Ansible workstation (Windows with WSL or Linux)
                - for WSL: https://learn.microsoft.com/en-gb/windows/wsl/install
        
        2. Install Ansible packages
                # apt install ansible
        
        3. A server or virtual machine with Cisco Meeting Server
                
                a. Cisco Meeting Server software installation package ( CMS version tested 3.8).
        
                b. Asign IP on CMS VM you need to:
                        - Access console VM CMS :
                                - ipv4 a add ip/mask gw
                                - ipv4 a enable 

                c. Network connectivity between Asible and CMS

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

        7. Create Call Leg Profiles  
                call_leg_profiles.yml

        8. Create Call  Profiles  
                call_profiles.yml

        7. Create CoSpaceTemplates 
                cospace_templates.yml




##  Deployment Steps

        1. One step only:
                Run ansible-playbook command to config one step:
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
