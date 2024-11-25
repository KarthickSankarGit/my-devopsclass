## Ansible PLAYBOOK 👨‍💻
===========================

### 1. Go to Ansible system , create playbook for project

cd ..

mkdir ansible-project

cd ansible-project

vi index.html


```sh
<html>
<head>
<body>
<h1> WELCOME TO INDIA </h1>
<h1> Jay Hind </h1>
</body>
</head>
</html>

```

:wq(save it)

### 2. now create playbook file and write code inside


sudo vim myansible_playbook.yml


```sh
-
 name: this is a simple html project deploy using ansible
 hosts: servers
 become: true
 tasks:
   - name: install nginx
     apt:
       name: nginx
       state: latest

   - name: start nginx
     service:
       name: nginx
       state: started

   - name: Deploy webpage
     copy:
       src: index.html
       dest: /var/www/html



```

:wq(save it)

### 3. test this

sudo ansible-playbook myansible_playbook.yml
