Ansible Playbook to deploy Cisco Meeting Server stand alone node.

# How to use 
It needs CMS beforehand with the following settings:

- Access console VM CMS :
        - ipv4 a add ip/mask gw
        - ipv4 a enable 

- add host key on trust



Then, modify hosts file to replace ip address of your CMS node.

```
cms1 ansible_host=<your cms node>
```

Run ansible-playbook command

```
ansible-playbook -i hosts playbook.yml --ask-pass 
```

