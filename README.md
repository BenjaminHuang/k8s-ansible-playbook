# Ansible playbook used to initialize k8s deploy environment on Ubuntu 18.04 LTS

## Features
* Automatically prepare k8s running environment, eg: disable swap and ufw, ensure ipvs kernel modules have been loaded, install docker, kubeadm, kubelet etc. You can use the prepared environment for kubeadm bootstrap lately
* Handle gcr docker image pulling issue specific to GFW

## User Guide
1. Prepare your ubuntu server with sshd installed
2. Install python3.6 and pipenv where ansible will be run
3. Checkout source code and cd to the checked out directory, then run 'pipenv shell' and 'pipenv update'
4. Modify inventories/production/hosts to suite your needs
5. Run ansible-playbook -i inventories/production/hosts k8s-deploy.yml
6. You may limit the playbook running on specific hosts by using '-l' option, or retrict it on tagged tasks with '-t' option. For more information, see ansible-playbook -h 

## TODO
* distinguish docker image pulling between master and worker
* migrate actions from bash script to ansible directives, in order to make it explicitly idempotent.
