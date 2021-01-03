# Dash nets

To manage several `conf`-files check [Managing wallets](managing_wallets.md).

Absolute path to config file for different OS you can find [here](https://dashcore.readme.io/docs/dash-core-wallet-arguments-and-commands).


- `mainnet`: Leave `dash.conf` empty.

- `testnet`: Just add one line: `testnet=1`  
  On macOS there are no params needed when runnings testnet.  
  On Linux you'll have to start with option `-port=19999`.  
  (Add some bash aliases as described in [Useful CLI Arguments](args_n_commands.md))
  
- `devnet`: This is where the fun begins ;)

	The devnet builds a 2nd layer on bitcoins `regtest`.
	To build up your own devnet, you'll have to commit on a `devnetname` and a p2p-`port`.

	Here I choose:
	
		devnet=kiddouglasdevnet
		port=29998
		
	Note that you need to give this port as argument for `dash-cli`.
	On some OS you have to give `devnetname` as argument to `dashd` and `dash-cli` (next to `port`, `rpcport` and `conf`-file).

		--devnet="kiddouglasdevnet" 

	Since the RPC-port should only used by `dash-cli` locally this doesn't need to be same for every client in the devnet.
	Further you should set a `user` and a `password` for RPC both (`dashd` and `dash-cli` use to communicate).
	I choose: 
	
		rpcport=19998
		rpcuser=dashrpc
		rpcpassword=rpcpassword

	Since you usually use RPC on localhost (or from private network) the following lines ensures this.
		
		rpcallowip=127.0.0.1
		rpcallowip=172.16.0.0/12
		rpcallowip=192.168.0.0/16

	To find peers in local network, too you need to set (which is disabled by default).
	
		allowprivatenet=1

	Optionally you can set your static IP (in case of eg. an VPS) so well-connected peers can reconnect to you.

		externalip=X.X.X.X
		
	For all this now accept connections from outside.

		listen=1

	If there is a server running your devnet you can add it as seed to build up connections from.

		addnode=<seed-ip-or-dns>:29998
		
	Be sure to choose the correct port of your p2p settings above.
	When `dashd` is already running you can add nodes in a similar way as `dash-cli`-command:
	
		$ dash-cli addnode "<seed-ip-or-dns>:29998" "add"

	This this example devnet `conf`-file you can find [here](core_configs/dash-devnet.conf).

	There are [many many other useful parameter](https://dashcore.readme.io/docs/dash-core-wallet-arguments-and-commands-dashd) you can set. 
	This is just the minimum. 
	
	If you change your devnet-setup or are in trouble syncing with other nodes you can start over again.
	Herefore remove the corresponding folder in `dashcore`-folder:
	
		rm -r ~/.dashcore/devnet-<your-devnet-name>
	
	Now you can rerun `dashd` again and start from zero.

- `evonet`: This is just a `devnet` itself. 
	To join this net, just use the [Evonet-8 config file](core_configs/dash-evonet-8.conf).
	
	Remember to give different [ports as arguments](args_n_commands.md) when running `dashd` resp. `dash-cli`.
	
	

This is just a short overview. 
Here some further links (with links):
- About testnet and devnets: https://docs.dash.org/en/stable/developers/testnet.html
- Devnet setup info: https://blog.dash.org/dash-devnets-bc27ecbf0085 
