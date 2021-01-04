# Notes about connecting to Dash and setting up different nodes

These are my experience dealing with Dash nodes making it easier for me to manage.

Especially for macOS this is not always trivial.

# Keeping overview
- At first of course we start with a Dash desktop wallet on `mainnet` from https://www.dash.org/de/downloads/.

- Next we try out configurations for `testnet`, own `devnets` and `evonet`.  
	In [Dash Nets](net_configs.md) you'll find parameters needed for `conf`-file to change nets and build up your own `devnet`.
	
- To keep track of wallets for different nets, here are my most used commands (and pitfalls):  
	[Useful CLI Arguments and Commands](args_n_commands.md)
	
- Managing multiple wallets with one OS (esp. macOS) and switch between nets using bash aliases you'll find in 
	[Managing wallets](managing_wallets.md).
	Also stated how to create and import HD-wallets into macOS desktop client.

Coming steps: 
- run devnet in docker.
- run docker mn testnet (mn-bootstrap)
- now "upgrade" to evonet (no longer needed since evonet is on testnet ;)

