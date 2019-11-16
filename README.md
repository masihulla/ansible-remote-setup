#! /bin/bash
yum update -y
echo "please enter user name same as in controller"
read id
adduser $id
passwd $id
echo "$id ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers
sed -i s'/#PermitRootLogin yes/PermitRootLogin yes/g' /etc/ssh/sshd_config
sed -i s'/PasswordAuthentication no/PasswordAuthentication yes/g' /etc/ssh/sshd_config
service sshd restart
