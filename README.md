# ansible

Lets get started with ansible

=============================
# Ansible Inventory Set Up []
-----------------------------
Server 1 - Ubuntu@ip
Server 2 - Ubuntu@ip
Server 3 - Ubuntu@ip
Workstation1 - Captain-levi@ip



===================================================================================
# START YOUR NEW INVENTORY FOR VM STEP 1
===================================================================================
# Shell in using incus instead of SSH
incus exec <vm-name> -- bash

# Install and enable SSH
apt update && apt install -y openssh-server
systemctl enable --now ssh

# Verify it's running
systemctl status ssh

# Add user (Can also look this up will be how you go from ubuntu@ip - levi@ip
sudo adduser sudo -aG sudo
==================================================================================
# REAL EXAMPLE OF COMMANDS TO RUN 
===================================================================================
Sabo:~/Bowheadwork$ incus exec server1 -- bash
root@server1:~# ls /home
ubuntu
root@server1:~# exit
root@server1:~# passwd ubuntu
New password:
Retype new password:
passwd: password updated successfully
root@server1:~# exit
exit
$ ssh ubuntu@172.168.192.3

Welcome to Ubuntu 24.04.4 LTS (GNU/Linux 6.8.0-124-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/pro

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

==================================================================================
# HOST MACHINE ACTIONS 
===================================================================================
ssh keygen  = genereate the public and private keys
ls -la .ssh = will show all of the ssh keys that were made
ls -l /etc/suduoers.d = see the user that you created inside of your playbook
sudo cat /etc/sudoers.d/sabo = seeing the password that you created
cat ~/.ssh/ansible.pub = showing the public key
cat .ssh    = any of these keys that were made from the ssh keygen command
ssh -i ~/.ssh/ansible (user@ip) = sudoer created, log in as him in server
Remember for the suduoer file you have to be aware of the created pw



===================================================================================
# Ansible play book
===================================================================================
ansible-playbook --ask-become-pass install_apache.yml/site.yml
ansible-playbook --ask-become-pass remove_apache.yml
bootstrap.yml = for sudoer creation
roles_site.yml = the way that the roles work in all the vms



