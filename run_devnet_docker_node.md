# Run Devnet Docker Node

## Prerequisites
You’ve installed [Docker](https://docs.docker.com/engine/install/ubuntu/) and [`docker-compose`](https://docs.docker.com/compose/install/).

For sure `docker-compose` is not necessary to do this job, but it makes it easier to remember all parameters a Docker container needs to be run within a single `yml`-file.

## Devnet Params

Commit with your team/colleagues/friends/yourself on a:
- `devnet`-name,
- p2p `port`,
- and maybe on some RPC-rules, esp. a port (makes it easier to share same configs).
(As you hopefully done already by reading [Dash Nets](net_configs.md) ;).

## Docker-compose File
Now changing the docker-compose file in [docker/devnet/docker.compose.yml](./docker/devnet/docker-compose.yml).
You’ll need to set your p2p port *twice* in line 8 *and* in line 14. 
First one opens the ports to the container, second one tells `dashd` to use this port.

Docker-compose also generates the volume `core_data`(according to *[mn-bootstrap](https://github.com/dashevo/mn-bootstrap/)*) which holds the blockchain data. 
This way you can flush and restart the container without reindexing the blockchain.  
(If you need to flush your volume one day, search for it with `docker volume list` and remove with `docker volume rm <name>`.
You won't need to flush if you switch between nets. 
Every net gets its own folder in this volume.)

## `dash.conf` File
Docker-compose tells the container in line 11 to copy file [docker/devnet/files/dash.conf](./docker/devnet/files/dash.conf) into config-directory.
In there you need to change:
- Line 1 with your pre-committed `devnet`-name,
- Line 13 with your p2p port,
- Line 14 with your RPC port (and following settings if you wish)
- and your `externalip` if you have one. Otherwise comment this line out with `#`.

(Maybe you’ll try other settings. But let `daemon=0`, since this is a Docker container running by a daemon anyways.)

Now you can redirect to folder `docker/devnet`.

Here you start your pwn Devnet-conatiner with:
	
	`docker-compose up -d` a try.
	
Option `-d` detaches you from the container and lets it sync abd work in background. 
If you wish to talk to `dash-cli` follow these steps.

## Jump into your Dash-Docker
To talk to your "just-set-up" Dash-container, get first letters of container-id from `docker ps`. 
Look for `dashpay/dashd` in column *image* resp. `_core_` in column *names*.  
Jump into container with:
	
	docker exec -it <cotainer-id> /bin/bash

From here you can run commands `dashd` and `dash-cli` (they are linked already).
