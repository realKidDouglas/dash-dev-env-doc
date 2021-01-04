


## Jump into your Dash-Docker
Get first letters of container-id from `docker ps`. 
Look for `dashpay/dashd` in column image resp. `_core_` in column names.  
Jump into container with:
	
	docker exec -it <cotainer-id> /bin/bash

From here you can run `dashd` and `dash-cli` (they are linked already).


## Find your current IP

If you have a DN, you can use `nslookup`, `host` or just `ping` to retrieve IP.

If not you could use IPecho's API:

	curl http://ipecho.net/plain
	
You can even use it in shell-scripts: 

	externalip=$(curl http://ipecho.net/plain)
	
(Found in https://github.com/kxcd/Masternode-Zeus/blob/main/masternode_zeus.sh#L753)


Testnet-Blockexplorer: https://testnet-insight.dashevo.org/insight/

faucets





Straight forward:
# set ssh port
cd /etc/ssh/
nano sshd_config
#Port 22 —>
Port 5321
reboot

sudo apt-get update

# install docker https://docs.docker.com/engine/install/ubuntu/ (ubuntu)
sudo apt-get install apt-transport-https ca-certificates curl gnupg-agent software-properties-common
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -
sudo apt-key fingerprint 0EBFCD88
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io

# install docker-compose https://docs.docker.com/compose/install/ 
sudo curl -L "https://github.com/docker/compose/releases/download/1.27.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose

# install npm (incl. node)
apt install npm

# install mn-bootstrap
git clone -b master https://github.com/dashevo/mn-bootstrap.git
cd mn-bootstrap/
npm install
npm link

# config mn-bootstrap (from mn-bootstrap folder)
mn config:default testnet
# find external ip and set
curl http://ipecho.net/plain
mn config:set externalIp 104.248.135.44




after register be patient...

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



OPERATOR KEY = masternodeblsprivkey

COLLATERAL (≈Pfand) ADRESS: da ist das Geld jetzt 



docker-compose --env-file ./config/.env.dev up 




Troubleshoot
mn restart --update

chmod -R 777 mn-bootstrap (FOLDER)


clean install of mn-bootstrap on Ubuntu
https://github.com/dashevo/mn-bootstrap/issues/104#issuecomment-663415856

