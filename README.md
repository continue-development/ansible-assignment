# Ansible-assignment
Python, Nginx, Postgresql deployment to Ubuntu 18.04 server using Ansible 

# Note
This is my first Ansible playbook. All major issues are solved but the postgresql user password is not setup because of the deadline 2021/03/23.
I am going to continue to make it perfect.

## Prerequisites

1. Install Ansible to your local host:
$ sudo apt install -y ansible

2.Add host ip address to your local machine (with Ansible) hosts file:
sudo vim /etc/hosts

192.168.1.170   ubuntu
192.168.1.170   helloworld.com

### Login to Ubuntu remote server and create a new user:

$ useradd user
$ passwd user
$ usermod -aG sudo user

3. Generate A New SSH Key Pair on local machine (with Ansible)
The first step will be to generate a new SSH key on your local system. To do this, issue the following command in Terminal:

$ ssh-keygen -t rsa
Press Enter to accept all fields as defaults.

### Copy Public Key to Remote Machine
In this next step, copy the public key to the remote system that you want to access from your local system without passwords. We will use the ssh-copy-id command that is by default available in most Linux distributions. This command will copy the public key id_rsa.pub to the .ssh/authorized_keys file in the remote system.

The syntax for ssh-copy-id is as follows:

$ ssh-copy-id remote_user@remote_IP
In our example, the command would be:

$ ssh-copy-id user@192.168.1.170

### Login to Ubuntu Remote Server Using SSH Keys
After performing the above steps, try logging into your remote sever. This time, you will be able to log into your remote server without entering a password.
$ ssh user@ubuntu

# Run Ansible from your local machine (with Ansible) in Ansible playbook direcotry

ansible-assignment$ ansible-playbook -i inventory tasks.yml -u user

# Known issues
### Postgresql
Task: set postgresql user password.
Issue: the password hasn't been setup.
