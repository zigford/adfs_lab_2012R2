# adfs_lab_2012R2
Ansible and Vagrant config files to produce an ADFS lab

Creates an ADFS Lab using Ansible (and optionally vagrant) based on the Networked Minds video series: Understanding ADFS

Part 1: https://www.youtube.com/watch?v=xwWb7S6OvFI  
Part 2: https://www.youtube.com/watch?v=l91_X7CfHfM  
Part 3: https://www.youtube.com/watch?v=lwVIxNeCrg0  
Part 4: https://www.youtube.com/watch?v=n5r3l7pw2kg  

# Notes

Included Vagrantfile uses libvirt provider. In order to use the ansible
playbooks, with another provider or without Vagrant, you will need to
alter the hosts file, and the roles/dc\_dns/tasks/main.yml

Edit vars.yml to choose the domain name you want the playbook you want
to create.

Then run: 

`ansible-playbook -i hosts playbook.yml`

# Known Issues

These playbooks faithfully recreates the lab in the video series and includes a bug where WindowsAuthentication did not work in the lab. The fix is to add an SPN for the ADFS service account. This is fixed in the proxy branch
