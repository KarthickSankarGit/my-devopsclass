# Docker installation on Ubuntu ( AWS EC2 :- Ubuntu )

## 1. Create a Ubuntu ec2 instance

AMi = ubuntu-22  --->  keypair = ubunu-key.pem/.ppk   --->  instance types = t2.micro

## 2. Connect your instance & then run below commands

```sh
sudo apt update
sudo apt install docker.io -y
docker --version
```

SUCCESSFULLY  INSTALLED
