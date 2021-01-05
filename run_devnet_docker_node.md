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
Now changing the docker-compose file:
In [docker/devnet/docker.compose.yml](docker/devnet/docker.compose.yml) you’ll need to set your p2p port in line 8 twice *and* in line 14. 
First one opens the ports to the container, second one tells `dashd` to use this port.

Docker-compose also generates the volume `core_data`(according to *mn-bootstrap*) which holds the blockchain data. 
This way you can flush and restart the container without reindexing.

(If you need this one day, search for ID of the image with `docker image list` and remove with `docker image rm <id>`.)

## Dash.conf File
Docker-compose tells the container in line 11 to copy file [docker/devnet/files/dash.conf](docker/devnet/files/dash.conf) into config-directory.
In there you need to change:
- Line 1 with your pre-committed `devnet`-name,
- Line 13 with your p2p port,
- Line 14 with your RPC port (and settings if wished)
- and your `externalip` if you have one. Otherwise comment this line out with `#`.

(Maybe you’ll try other settings. But let `daemon=0`, since this is a Docker container running by a daemon anyways.)

Now you can redirect to folder `docker/devnet` and give `docker-compose up -d` a try.
Since option `-d` 

## Jump into your Dash-Docker
To talk to your "just-set-up" Dash-container, get first letters of container-id from `docker ps`. 
Look for `dashpay/dashd` in column image resp. `_core_` in column names.  
Jump into container with:
	
	docker exec -it <cotainer-id> /bin/bash

From here you can run commands `dashd` and `dash-cli` (they are linked already).
