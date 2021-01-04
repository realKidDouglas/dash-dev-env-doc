# Managing wallets

## Setup different nets (on macOS)

Currently there is no `dashd` program on macOS release of Dash Core.
But you can run it similar to Linux with different config files and parameters the following way:

	/Applications/Dash-Qt.app/Contents/MacOS/Dash-Qt -conf=<absolute-path-to-your-conf> -port=<port>

Default path for configs is:

	~/Library/Application\ Support/DashCore
(note the space-char. So either escape it or put path in quotes)

So just put your configs for different nets here. For me it looks like:

	$ ls *.conf
	dash-devnet.conf    
	dash-devnet2.conf
	dash-evonet-8.conf
	dash.conf
	dash-testnet.conf

## Bash Aliases

With every start in a net different to `mainnet`you'll have to give a different `conf`-file and different ports as parameters 
(even if the `port` is mentioned in the config file, `dashd` needs it as parameter, too. On Ubuntu you even have to give `rpcport` as parameter).
To switch easily between nets I put some alias into my `.bash_profile`(aka `.bashrc` on Linux).

	$ nano ~/.bash_profile

And add somewhere in this file:

	alias dashdevnet="/Applications/Dash-Qt.app/Contents/MacOS/Dash-Qt -conf=/Users/kiddouglas/Library/Application\ Support/DashCore/dash-devnet.conf -port=29998 &"
	alias dashdevnet2="/Applications/Dash-Qt.app/Contents/MacOS/Dash-Qt -conf=/Users/kiddouglas/Library/Application\ Support/DashCore/dash-devnet2.conf -port=29998 &"
	alias dashevonet-8="/Applications/Dash-Qt.app/Contents/MacOS/Dash-Qt -conf=/Users/kiddouglas/Library/Application\ Support/DashCore/dash-evonet-8.conf -port=20001 &"
	alias dashtestnet="/Applications/Dash-Qt.app/Contents/MacOS/Dash-Qt -conf=/Users/kiddouglas/Library/Application\ Support/DashCore/dash-testnet.conf &"

Now you can easily start different nets from Terminal using eg. `dashdevnet2`.
To start the default `mainnet` just start the DashQt from Applications folder without any params.



## Importing HD-wallet

For `evonet` it is interesting to import your HD-wallet (generated eg. by tutorials [here](https://dashplatform.readme.io/docs/tutorial-create-and-fund-a-wallet)) into your Desktop wallet.
On **first** start you need to give parameters `usehd=1` and your `mnemonic`as follows:

	/Applications/Dash-Qt.app/Contents/MacOS/Dash-Qt -conf=/Users/kiddouglas/Library/Application\ Support/DashCore/dash-evonet-8.conf -port=20001 --usehd=1 --mnemonic="<super-secret-mnemonic>"

If you don't give `mnemonic` a new HD-wallet will be created. 

In the Dash Core Application you will see a small icon for `HD`.

![HD-ico](./images/hdico.png)

From now your wallet is installed and you can run your evonet-wallet easily without the wallet info as above with the alias `dashevonet-8`.

Check HD-wallet info containing mnemonic in cli with:

	dumphdinfo

(from: https://docs.dash.org/en/stable/wallets/dashcore/advanced.html)