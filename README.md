# Build dockerfiles and deploy K8s pods

This repository include 2 Dockerfile that we build on a remote k8s masternode and create pods :
- first one is oraclelinux image with a MySQL server installed
- second one is Alpine image with php, php-mysqli and mysql-client packages installed

# Before running pipeline

If you are using a private key for SSH connection, please reach Gitlab CI/CD settings of this repository and click on "add a variable", name it "ANSIBLE_SSHKEY" then input the private key as "value", make it protected and you're good to go.

If you are not using a private key for SSH connection : remove "--private-key secret/ansible.key" from ansible command in .gitlab-ci.yml and also remove from step predeploy and deploy :

``` 
  - mkdir secret # create secret dir
  - echo "$ANSIBLE_SSHKEY" > secret/ansible.key # create priv key from gitlab variable
  - chmod 400 secret/ansible.key
```

# Pipeline process

Pipeline connects in SSH and import this repository to remote k8s masternode. It then creates a local registry with docker, build our dockerfiles and push it to that registry. 
After that, it automatically applies configuration files (yaml) to create our 2 pods.

