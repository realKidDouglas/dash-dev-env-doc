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

## Docker Devnet
[Run `devnet` node with Docker](run_devnet_docker_node.md) and setup your own Devnet locally and/or with friends and colleagues worldwide. 

Connecting to it is "trivial" since you commit on `name` and `port` (whereas mentioned above in [Dash Nets](net_configs.md)).
	
## `mn-bootstrap`

Now - we learned everything about Dash, nets, esp. Devnets and Docker - lets have a look at *[mn-bootstrap](https://github.com/dashevo/mn-bootstrap/)*.
This is a tool that guides you through setting up *masternodes* in the Dash-network with Docker really easy;)

Here i stated my [walkthrough](mn_testnet.md) for running a `testnet`-masternode with *mn-bootstrap*.

