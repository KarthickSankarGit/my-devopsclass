## GRAFANA INSTALL ON UBUNTU 
===================================

### 1. Go to EC2, create ubuntu-instance and connect it ( terminal )


ami = ubuntu

instance types = t2.micro

keypair = grafana-key.pem

security group = all traffic ( anywhere )


### 2. install grafana


#### 2.1 Updates the list of available packages ( ubuntu )

```sh
sudo apt update
```


#### 2.2 Install the prerequisite packages

```sh
sudo apt-get install -y apt-transport-https software-properties-common wget
```


#### 2.3 Import the GPG key

```sh
sudo mkdir -p /etc/apt/keyrings/
wget -q -O - https://apt.grafana.com/gpg.key | gpg --dearmor | sudo tee /etc/apt/keyrings/grafana.gpg > /dev/null
```


#### 2.4 To add a repository for stable releases

```sh
echo "deb [signed-by=/etc/apt/keyrings/grafana.gpg] https://apt.grafana.com stable main" | sudo tee -a /etc/apt/sources.list.d/grafana.list
```


#### 2.5 Updates the list of available packages again

```sh
sudo apt update
```


#### 2.6 To install Grafana OSS

```sh
sudo apt-get install grafana -y
```

#### 2.7 To check Grafana OSS installed or not

```sh
grafana-server -v
```


#### 2.8 Start the Grafana server service

```sh
sudo systemctl daemon-reload
sudo systemctl start grafana-server
```


#### 2.9 To verify that the service is running

```sh
sudo systemctl status grafana-server
```



### 3. Open grafana in your browser

`instance pub-ip:3000`  ----> Grafana default port number :- 3000 



### 4. Grafana log-in

`Email or username`  ---->  admin  `default username`

`Password`  ------>  admin  `default password`


### 5. Configure Grafana

`Update your password`




===============================end========================
