# Private Ethereum Network in Docker
It's a repository to create Private ethereum blockchain network with 10 nodes in a docker.

# Getting started

## 1. Installing

### 1.1. Standalone Ethereum node

#### Prerequisites

Docker Toolbox installed. 
> To download and install Docker Toolbox for your environment please
follow [the Docker Toolbox instructions](https://www.docker.com/products/docker-toolbox). 

After Docker Toolbox has been installed, create a ```default``` machine to run Docker against.

#### Lets go

To run a single test Ethereum node run the following:

```
$ docker-compose -f docker-compose-standalone.yml up -d
```

If using docker-machine you should be able to get to the JSON RPC client by doing:

```
open http://$(docker-machine ip default):8545
```
### Scaling the number of nodes/containers in the cluster

You can scale the number of Ethereum nodes by running:

```
docker-compose scale eth=3
```
### Test accounts ready for use

As part of the bootstrapping process we bootstrap 10 Ethereum accounts for use pre-filled with 20 Ether for use in transactions by default.

If you want to change the amount of Ether for those accounts
See `files/genesis.json`.

## 2. Interact with geth

To get attached to the `geth` JavaScript console on the node you can run the following
```
docker exec -it ethereumdocker_eth geth attach ipc://root/.ethereum/devchain/geth.ipc
```
Then you can `miner.start()`, and then check to see if it's mining by inspecting `web3.eth.mining`. 
