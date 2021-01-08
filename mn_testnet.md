# Setup a Masternode on Testnet with mn-bootstrap

Overview
  * [Starting at zero](#starting-at-zero)
    + [Set default `ssh` port](#set-default--ssh--port)
  * [Straight forward with mn-boostrap](#straight-forward-with-mn-boostrap)
    + [From scratch](#from-scratch)
    + [Config](#config)
      - [Find your current IP](#find-your-current-ip)
    + [Register masternode](#register-masternode)
  * [Troubleshoot](#troubleshoot)
  
## Starting at zero

Create a Testnet-wallet.
Get one address to collect (a bit more than) 1000 tDash:

	getnewaddress

And corresponding private Key:

	dumpprivkey <address>
	
This private key you'll need to give `mn-bootstrap` later.

Now be patient and ask [faucets](https://docs.dash.org/en/stable/developers/testnet.html#faucets) for tDash until you reached above 1000.


### Set default `ssh` port
Since I used a VPS with a static IP somewhere in the internet, I first changed `ssh` port for security reasons.
```
cd /etc/ssh/
nano sshd_config
#Port 22 —> Port e.g. 5432
reboot
```
To not need to remember, I added this `Host`to my `.ssh/config`-file:
```
Host dash_vps
    Hostname <ip>
    Port 5432
    User root
```
Now I can start `ssh`-connection easily with:
```
ssh dash_vps
```

## Straight forward with mn-boostrap

### From scratch
This is all you need to do from scratch on an Ubuntu machine.

Install Docker as it stated here: https://docs.docker.com/engine/install/ubuntu/
```
sudo apt-get update

sudo apt-get install apt-transport-https ca-certificates curl gnupg-agent software-properties-common
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -
sudo apt-key fingerprint 0EBFCD88
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
```

Now docker-compose: https://docs.docker.com/compose/install/ 
``` 
sudo curl -L "https://github.com/docker/compose/releases/download/1.27.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
```

`npm` including `node`:
```
apt install npm
```

And finally install `mn-bootstrap`. The link is optional but helpful.
```
git clone -b master https://github.com/dashevo/mn-bootstrap.git
cd mn-bootstrap/
npm install
npm link
```

### Config
Note to `cd` to `mn-bootstrap` folder.

Choose Testnet as default config:
```
mn config:default testnet
```

Find your external IP and set in config:
```
mn config:set externalIp <ip>
```

Config done.

#### Find your current IP

If you have a DN, you can use `nslookup`, `host` or just `ping` to retrieve IP.

If not you could use IPecho's API:

	curl http://ipecho.net/plain
	
You can even use it in shell-scripts: 

	externalip=$(curl http://ipecho.net/plain)
	
(Found in https://github.com/kxcd/Masternode-Zeus/blob/main/masternode_zeus.sh#L753)

### Register masternode

For this step you have to bring some patience.
First `mn-bootstrap` will sync blockchain and verify you have the stated funds.
It makes the collateral transferal on its own.
Then it waits for 15 confirmations before broadcasting in the network.
```
mn-bootstrap# mn register <key>
❯ Register masternode
  ✔ Start Core
  ✔ Import funding private key
  ✔ Sync Core with network
  ✔ Check funding address balance
  ✔ Generate a masternode operator key
    › Public key: xxx
      Private key: xxx
  ✔ Create a new collateral address
    › Address: xxx
      Private key: xxx
  ✔ Create a new owner addresses
    › Address: xxx
      Private key: xxx
  ✔ Send 1000 dash from funding address to collateral address
    › Collateral transaction ID: xxx
  ⠇ Wait for 15 confirmations
    › 0 confirmation
  ◼ Broadcast masternode registration transaction
  ◼ Wait for 1 confirmation
  ◼ Stop Core 
```

If everything went well so far, you now can start your masternode easily with:

	mn start

Status you can get with:
	
	mn status:services
	
What's very similar to `docker ps`.


## Troubleshoot

Be sure you have the latest services:

	mn restart --update

Be sure `mn` can `rwx` in its folder:

	chmod -R 777 <mn-bootstrap-directory>


##Links 
- Testnet-Blockexplorer:  
	https://testnet-insight.dashevo.org/insight/
- Testnet Faucets:  
	


