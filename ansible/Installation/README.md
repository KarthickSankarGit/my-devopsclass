## Ansible-install on AWS ubuntu👇🚀
==========================================

### 1. launch ubuntu-22 instance

ami --> ubuntu-22 , instance types --> t2.micro , key pair --> mykey.pem , sg --> ubuntu-SG (ssh,all traffic = ANYWHERE)

### 2. Connect EC2 instance and install ansible

go to terminal

cd downloads

ssh -i "mykey.pem" ubuntu@(public dns of ec2)

`sudo apt-add-repository ppa:ansible/ansible`

`sudo apt update`

`sudo apt install ansible -y`

`ansible --version`
