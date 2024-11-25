## Ansible and Worker-system Connection ✌️😎
===================================================

### 1. launch ubuntu-22 instance ( ANSIBLE SYSTEM )  

ami --> ubuntu-22 , instance types --> t2.micro , key pair --> mykey.pem , sg --> ubuntu-SG (ssh,all traffic = ANYWHERE)

### 2. Connect EC2 instance and install ansible

go to terminal

cd downloads

ssh -i "mykey.pem" ubuntu@(public dns of ec2)

sudo apt-add-repository ppa:ansible/ansible

sudo apt update

sudo apt install ansible -y

ansible --version

### 3. Create 2-EC2 instances & Declare as Worker system

ami --> ubuntu-22 , instance types --> t2.micro , key pair --> mykey.pem , sg --> ubuntu-SG (ssh,all traffic = ANYWHERE)

### 4. Go to Ansible-system , mention worker node ip inside inventory 

sudo vi /etc/ansible/hosts

(go to ex-2 line below , enter once(goto below line) and delete #)

```sh
[workers]
worker_1 ansible_ssh_host=(worker-sys pub ip)
worker_2 ansible_ssh_host=(worker-sys pub ip)

```

:wq(save it)


### 5. create a directory for storing key inside

```sh
mkdir keys
cd keys/

```

### 6. open another terminal box for adding key from local system to ansible

```sh
cd downloads
ls mykey.pem
scp -i "mykey.pem" mykey.pem ubuntu@<ansible-system-pub-dns>:/home/ubuntu/keys

[ goto ansible-system and check again "ls" , pvt-key is now available ]

```

### 7. Go to Ansible-system , update in inventory and check connection


sudo vim /etc/ansible/hosts


```sh
[workers:vars]
ansible_python_interpreter=/usr/bin/python3
ansible_user=ubuntu
ansible_ssh_private_key_file=/home/ubuntu/keys/mykey.pem

```

:wq(save it)

sudo ansible workers -m ping

ansible-inventory --list
