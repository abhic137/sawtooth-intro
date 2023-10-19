to initiate docker swarm network
```
docker swarm init

```
paste the token that you get after the init command into another physical pc.
use this command to see the connected nodes:
```
docker node ls

```
Create an Overlay Network (if not created already):

If you don't already have a custom overlay network for Sawtooth, you can create one. This isolates the Sawtooth containers from other networks:
```

sudo docker network create --driver overlay sawtooth-net
```
inorder to deploy the services use this command, you can use your own name insted of my-sawtooth-stack
```
docker stack deploy -c sawtooth-swarm-pbft.yaml my-sawtooth-stack

```
Here are a couple of useful Docker commands:

    docker service ls: List all the services in your Swarm and their status.
    docker service ps <service-name>: Check the status of a specific service.
    docker stack rm <stack-name>: Remove a stack and its services.

To check if the containers are running:
```
sudo docker stack ps my-sawtooth-stack

```
```
 docker service ls

```
to down the setup:
```
sudo docker stack rm my-sawtooth-stack

```
to check if the setup is down:
```
sudo docker stack ps my-sawtooth-stack

```
