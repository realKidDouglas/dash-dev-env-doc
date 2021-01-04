# Useful CLI Arguments and Commands

Here I show the few commands I needed most. 
But check here for all: https://dashcore.readme.io/docs/dash-core-wallet-arguments-and-commands  
(Esp. look for [`dashd`](https://dashcore.readme.io/docs/dash-core-wallet-arguments-and-commands-dashd) resp. [`dash-cli`](https://dashcore.readme.io/docs/dash-core-wallet-arguments-and-commands-dash-cli))


## CLI Commands

Send Dash:

	dash-cli sendtoaddress <address> <amount>

Check if you are "connected" with `getblockchaininfo` and look for best block:

	$ dash-cli -conf="/home/kiddouglas/dashcore/dash-devnet.conf" -rpcport=19998 getblockchaininfo | grep blocks

Check (confirmed) balance of wallet:

	getbalance
	
Balance is confirmed after app. 15 minutes.
To find also unconfirmed try:

	getunconfirmedbalance

or

	getwalletinfo

## CLI Arguments

If you use a different ports you have to specify it with **every** cli call :/  
**No matter if it's already in `conf`-file.**

`dashd` needs both `port` and `rpcport`.  

	$ dashd -conf="<absolute-path-to-conf-file>" -port=<port> -rpcport=<rpcport> <command>

`dash-cli` only needs `rpcport`.  

	$ dash-cli -conf="<absolute-path-to-conf-file>" -rpcport=<rpcport> <command>

Note the path to `conf`-file should be absolute.
And the given ports should match the ports in `conf`-file. 

To make CLI calls easier, I set some bash aliases similar to the [macOS wallets](managing_wallets.md).
E.g.

	alias ddash-cli='dash-cli -conf="/home/kiddouglas/dashcore/dash-devnet.conf" -rpcport=19998'

And use it as common: 

	$ ddash-cli getblockchaininfo | grep blocks





