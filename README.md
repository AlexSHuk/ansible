# Ansible
This repository contains Ansible playbook and roles for managing Docker on a remote server, as well as:
- cloning a repository;  
- building Docker images;  
- running Docker containers.  
## Playbooks:  
### playbook_install_docker.yml  
**Сontains the following tasks**:  
Installation Docker , Add user to the docker group , Installing Python , Installing pip , Installing module Docker  
Usage:  
`ansible-playbook playbook_install_docker.yml` 

### playbook_docker_build_and_run.yml  
**Сontains the following tasks**: 
cloning a repository, building a docker image, running a container based on a docker image  
Usage:  
`ansible-playbook playbook_docker_build_and_run.yml`  

## Roles

### 1. clone_repository
This role clones a repository from a remote Git repository.

### 2. build_docker_images
This role builds Docker images based on the cloned repository.

### 3. run_docker_containers
This role runs Docker containers using the built images.

## Usage  
1. Clone the repository to your local machine:  
git clone `https://github.com/AlexSHuk/ansible.git`  

2. Update the inventory file (`hosts.txt`) with your remote server's information.
For example , hosts.txt can be contain this:  

`[$name_of_group_hosts]`    
`$host_name ansible_host=ip_address`  
`$host_name ansible_host=ip_address`  
  
3. Modify the variables in `group_vars/all.yml` and variables in `roles/*/vars/main.yml` to fit your requirements.  
For example , all.yml can be contain this :  

`---`  
`ansible_user                  : $user_name`  
`ansible_ssh_private_key_file  : $path_to_private_key`    
4. Run the desired playbook using the `ansible-playbook` command.


###!PLEASE NOTE!

You must have ansible installed on the control host and docker module. If not, use the commands below (for Ubuntu) 

`sudo apt update`  
`sudo apt install ansible`  
`ansible-galaxy collection install community.docker`  

