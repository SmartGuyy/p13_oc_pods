# Build dockerfiles and deploy K8s pods

This repository include 2 Dockerfile that we build on a remote k8s masternode and create pods :
- first one is Alpine image with a MySQL server installed
- second one is Alpine image with php, php-mysqli and mysql-client packages installed

# Before running pipeline

If you are using a private key for SSH connection, please reach Gitlab CI/CD settings of this repository and click on "add a variable", name it "ANSIBLE_SSHKEY" then input the private key as "value", make it protected and you're good to go.

If you are not using a private key for SSH connection : remove the parts where we create private key from gitlab variable + give permissions, also remove "-i ansible.key" with "ssh" command and you should be good to go.

# Pipeline process

Pipeline connects in SSH and import this repository to remote k8s masternode. It then creates a local registry with docker, build our dockerfiles and push it to that registry. 
After that, it automatically applies configuration files (yaml) to create our 2 pods.

