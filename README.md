﻿# Vagrant-Ansible---ProvisionVMS

---------------------------Use this provisioning only as a lab basis-------------------------------------------

Provisioning virtual machines via VirtualBox, using Vagrant, and automating tasks with Ansible. In this lab, three machines are being created: Ansible Control, AD Server,  

For this provisioning, Oracle virtual box is required and the Vagrant tool Install.

After repository downloading, validate the vagratfile file from the "vagrant validate" shell command.

To start provisioning, run the command: "vagrant up"

After completion, validate the provisioning from the "vagrant status" command

Access via ssh the AnsibleControl machine with username and password "vagrant"

from the /vagrant/Ansible/ directory

Start automating tasks.

Run the command: ansible-playbook -i hosts install_ad_client.yml -vvv

after completion, you access the "ADWIN" or "ClientWindows11" machines with the account:

Username: lab.local\suporte
Password: SenhaSegura@123

If you have any questions, send us a message!!














