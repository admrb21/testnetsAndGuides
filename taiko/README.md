# Taiko Node Instalation Guide
![image](https://user-images.githubusercontent.com/101635385/210137987-bdc3fe6f-270d-40f8-b843-d927a58ca6e9.png)


<h1 align="center"> Taiko Node </h1>

Before you can install Node, you need to do the Platform testnet. We will use the wallet address you used in the platform testnet here. The system works with 6060 port, if you have installed a node like celestia, it will conflict. <br>

Information about the platform testnet <br>

* [Platform Test](https://twitter.com/Hercules4413/status/1608026986164748288)


### Explorer:
 * [Explorer](https://l2explorer.a1.taiko.xyz/)


 ## 🟢 System requirements

Minimum:
- CPU with 2+ cores
- 4GB RAM
- 500 Gb 


Recommended:
- Fast CPU with 4+ cores
- 16GB+ RAM
- High-performance SSD with at least 1TB of free space

 ## 🟢 Installing

```shell
sudo apt update
```

```shell
sudo apt upgrade
```

```shell
apt install docker-compose
```

```shell

sudo apt-get update && sudo apt install jq && sudo apt install apt-transport-https ca-certificates curl software-properties-common -y && curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add - && sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable" && sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin && sudo apt-get install docker-compose-plugin

```


```
git clone https://github.com/taikoxyz/simple-taiko-node.git
```

```
screen -S taiko
```

```
cd simple-taiko-node
```

```
cp .env.sample .env
```

```
nano .env
```

<br>

*ENABLE_PROPOSER=true  ( false to true ) <br>
*L1_PROPOSER_PRIVATE_KEY= private key of your wallet <br>
*L2_SUGGESTED_FEE_RECIPIENT= wallet address <br>
*ctrl + x Yes and save. <br>

<br>

![image](https://user-images.githubusercontent.com/101635385/210138160-c01d12f1-c1d1-40b5-96f0-ac907d3110cc.png)

<br>

```
docker compose up
```

![image](https://user-images.githubusercontent.com/101635385/210138255-d7c31fb4-bbe4-4d6d-8703-6ee16f1a0b47.png)


## 🟢 Viewing blocks via explorer

Write your address on Explorer, if it is as in the picture below, there is no problem, of course, it needs to be synchronized first.

 * [Explorer](https://l2explorer.a1.taiko.xyz/)

![image](https://user-images.githubusercontent.com/101635385/210138905-3baea6ea-5424-4197-b4c4-0c23d9578247.png)


### Useful commands

```
cd simple-taiko-node
docker compose logs -f
```

```
docker compose down
```

```
docker compose down -v
cd
rm -fr simple-taiko-node
```

