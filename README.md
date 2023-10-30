Ansible Playbook to deploy Cisco Meeting Server with :
- callbridge
- webbridge3
- webadmin
- scheduler
- ldap integration

# How to use 
#before
You need to have preinstalled VM with Cisco Meeting Server (version tested 3.8) and asigned IP.

#To asign IP on CMS VM you need to:
- Access console VM CMS :
        - ipv4 a add ip/mask gw
        - ipv4 a enable 

After that you have to coplete vaiable.yml and hosts file

Then, modify hosts file to replace ip address of your CMS node.

```
cms1 ansible_host=<your cms node>
```

Run ansible-playbook command

```
ansible-playbook -i hosts playbook.yml --ask-pass 
```


