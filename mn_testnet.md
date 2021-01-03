
Testnet-Blockexplorer: https://testnet-insight.dashevo.org/insight/

faucets

nur 2 Container

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



KONTO MIT 1005 Dash (confirmed)
besser mehr als 1000. Von dieser Adresse werden dann die exakt 1000 dann überwiesen ;)
1005: yMdNmomQp3U4ZDdzE9oMH49xdbACk7itZg
cVSH2papyer9Pz5R2iu82Yt4WHUbVD6WqJeg6gYuYhwQdmzR2XGQ

nach register: warten….

mn-bootstrap# mn register cVSH2papyer9Pz5R2iu82Yt4WHUbVD6WqJeg6gYuYhwQdmzR2XGQ
❯ Register masternode
  ✔ Start Core
  ✔ Import funding private key
  ✔ Sync Core with network
  ✔ Check funding address balance
  ✔ Generate a masternode operator key
    › Public key: 0a5c47983c44aa99ce5f04b32cfbdff42e7f92b1410558559dcbff3ca8aacc3c2fcaf05db6f021a9f335ba05b…
      Private key: 6f324c08213e99c24dfe79f2671eaa10b6b47bfa275bcbae32c554ce2ac85528
  ✔ Create a new collateral address
    › Address: yXS3HjGfzjV39Sa2i8hWpAuZzk3qgEqXar
      Private key: cVV7uzVJaagmqRAjMbhjaKXkjcvAh7jQEER3gPnK6hVKUEuCvZon
  ✔ Create a new owner addresses
    › Address: ygdLnih3aMvggg4FdnqYrxdhPy37CVh6dz
      Private key: cPFwYqDGULnGRFzgWd8gBPyghVzceDQgvyopTnz88mP98bU63QLk
  ✔ Send 1000 dash from funding address to collateral address
    › Collateral transaction ID: 3efd4cf14ecfe820a7fc3efd3d7eed5a692f37b4eb8dc8d3f287f0773715b37b
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

