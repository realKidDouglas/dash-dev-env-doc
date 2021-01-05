# Build up your own Dash Development Environment

Notes about connecting to Dash, setting up different nodes (and masternodes) and keeping overview.  
These are my experience and strategies dealing with Dash nodes making it easier for me to manage.


## Keeping overview
Especially for macOS this is not always trivial...

- At first - of course - we start with a Dash desktop wallet on `mainnet` from https://www.dash.org/de/downloads/.

- Next we try out configurations for `testnet`, own `devnets` and `evonet`.  
	In [Dash Nets](net_configs.md) you'll find parameters	 needed for `conf`-file to change nets and build up your own `devnet`.
	Corresponding example configuration files you'll find in [core_configs/](core_configs/).
	
- To keep track of wallets for different nets, here are my most used commands (and pitfalls):  
	[Useful CLI Arguments and Commands](args_n_commands.md)
	
- Managing multiple wallets with one OS (esp. macOS) and switch between nets using bash aliases you'll find in 
	[Managing wallets](managing_wallets.md).
	Also stated how to create and import HD-wallets into macOS desktop client.

## Docker 
- [Run `devnet` node with Docker]() and setup your own Devnet locally and/or with friends and colleagues worldwide. 
	- Connecting to it is "trivial" whereas mentioned above ([Dash Nets](net_configs.md)).#
	
## Coming steps: 

(Almost done; I'm on it at this moment ;) )

- Walkthrough: Run a `testnet`-masternode with *mn-bootstrap* and/or Docker.
	- Now "upgrade" to `evonet` (no longer needed since `evonet` is on `testnet` ;) )

