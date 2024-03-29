# Netbox - Ansible

Gather all the devices mapped in your ansible-inventory (hosts) and populate the information into netbox automatically
(For now the script is only supported to gather Windows information)

## Functionalities:
Netbox areas that will be required:
- Devices
- IPAM
- Custom Fields (Arquitecture OS, Cores, Number of CPU, Threads, CPU model, Disk Partition, Memory )

Tested on:
- Netbox = 3.3.2
- ansible-playbook = core 2.13.1
- python version = 3.8.10
- jinja version = 3.1.2

## Architecture:
![image](https://user-images.githubusercontent.com/86939628/224460873-fbf4040f-dc70-4729-8ad1-43bf1a8864d3.png)

## Requirements:
Hosts:
  - Install WinRM on Windows OS to access from the CM (Control Machine)

Control Machine (Ansible):
  - Install Kerberos/sshkeys to access to the hosts of your ansible inventory.
  - Install Ansible.
  
Netbox:
  - Create and Adapat the variables of the file _main.yml_ (Create the temporary objects o relate them to those that already exist
 )
 _main.yml_:
  ```yml
---
- hosts: win
  vars:
    #################################################
    ################# MANAGMENT #####################
    
    site_temporal: 5     # site.id that will be used for the gathered devices  
    device_type : "HP Proliant Gen 10" #The device type that will be used for the gathered devices  
    device_type_interface: "ge0/4" # The interface Netbox where the IP will be assigned
    device_role: "Servidores Fisicos" # The Device Role that will be used for the gathered devices  

    
    url_nb: "http://192.168.1.203" # NETBOX URL
    token_nb: "4c121d2ed2103e10fd2f4d9532dcb8e040fd0fc9" # NETBOX TOKEN
```
 
  - Set the inventory (IP or DomainName) in hosts.
  - Then run the ansible playbook and populate your server information into NETBOX.
  * ansible-playbook main.yml -i hosts

EXECUTION:

https://user-images.githubusercontent.com/86939628/224464231-f5942094-e4aa-4383-88a9-8528a22439d0.mp4


  
  
