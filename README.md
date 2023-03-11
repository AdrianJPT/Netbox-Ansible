# Netbox - Ansible

Gather all the devices mapped in your ansible-inventory (hosts) and populate the information into netbox automatically
(For now the script is only supported for Windows OS)

## Functionalities:
Netbox areas that will be required:
- Devices
- IPAM
- Custom Fields (Arquitecture OS, Cores, Number of CPU, Threads, CPU model, Disk Partition, Memory )

## Architecture:
![image](https://user-images.githubusercontent.com/86939628/224460873-fbf4040f-dc70-4729-8ad1-43bf1a8864d3.png)

## Requirements:
Hosts:
  - Install WinRM on Windows OS to access from the CM (Control Machine)

CM (Ansible):
  - Install Kerberos/sshkeys to access to the hosts of your ansible inventory.
  - Install Ansible.
  
  - Adapat the variables of the file main.yml (Create the temporary objects o relate them to those that already exist
 )
  
  ![image](https://user-images.githubusercontent.com/86939628/224456020-4c4954c4-1fde-479e-85e7-90cabafb49cd.png)
 
  - Set the inventory (IP or DomainName) in hosts.
  - Then run the ansible playbook and populate your server information into NETBOX.
  * ansible-playbook main.yml -i hosts

  
