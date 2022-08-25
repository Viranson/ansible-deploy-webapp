
# Deploy webapp with ansible

## Setup
- [x] Provision an instance as controller node for Ansible
- [x] Follow the [**Ansible Installation Guide**](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html) to install and configure ansible on the controller node.
- [x] Clone this repo : 
```sh
git clone https://github.com/Viranson/ansible-deploy-webapp.git && cd ansible-deploy-webapp
```
 - [x] Provision a client Linux host based on CentOS
 - [x]  Install docker and docker-compose
 - [x] On the ansible instance, edit *inventory.yml* file and update the client host IP address on line "**ansible_host**"
 - [x] Edit *group_vars/prod.yml* file and update the client host user on line "**ansible_user**"
 - [x] Remove files/secrets/credentials.vault
 - [x] Create new file *files/secrets/credentials.vault* and edit with the following content: 
```sh
---
ansible_password: clientpass
```
> Note: *Replace* `clientpass` *with your client instance real password*.
 - [x] Encrypt the credentials file by running : 
```sh
ansible-vault encrypt files/secrets/credentials.vault
```
Set your encryption password when it will be prompted.

## deploy simple webapp with ansible
 - [x] Deploy the webapp by running the ansible playbook "*deploy.yml*" with the command : 
```sh
ansible-playbook -i inventory.yml --ask-vault-pass deploy.yml
```
Enter the client password first then the credentials encryption password when prompted.

## deploy simple webapp with ansible roles
 - [x] Deploy the webapp by running the ansible playbook "webapp.yml" with the command : 
```sh
ansible-playbook -i inventory.yml --ask-vault-pass webapp.yml
```
Enter the client password first then the credentials encryption password when prompted.

## deploy Wordpress-MySQL stack with ansible roles
 - [x] Edit *wordpress.yml* file and update the client host user on line "**system_user**"
 - [x] Deploy the stack by running the ansible playbook "wordpress.yml" with the command :
```sh
ansible-playbook -i inventory.yml --ask-vault-pass wordpress.yml
```
Enter the client password first then the credentials encryption password when prompted.
