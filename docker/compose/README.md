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
To check the status and configuration of a Docker Swarm, you can use the following Docker commands:

1. Check if you are part of a Docker Swarm:

   ```
   docker info
   ```

   Look for the "Swarm: active" section to determine if you are already part of a Swarm. If you're not, you can create a new Swarm with `docker swarm init` (for manager nodes) or join an existing Swarm with `docker swarm join` (for worker nodes).

2. List nodes in the Swarm:

   ```
   docker node ls
   ```

   This command will list all the nodes in the Swarm, including their status, availability, and version.

3. List services running in the Swarm:

   ```
   docker service ls
   ```

   This command lists all the services running in the Swarm, showing their names, replicas, and other information.

4. Inspect a specific service in the Swarm:

   ```
   docker service inspect <service_name>
   ```

   Replace `<service_name>` with the name of the service you want to inspect. This command provides detailed information about the service's configuration and tasks.

5. Get the status of tasks in a service:

   ```
   docker service ps <service_name>
   ```

   This command shows the tasks (containers) associated with a specific service, along with their current status and more.

6. Check the logs of a service's task:

   ```
   docker service logs <service_name>
   ```

   You can use this command to view the logs of a specific service's tasks.

7. Check the status of overlay networks:

   ```
   docker network ls
   ```

   This command lists all the networks in the Swarm, including overlay networks used for service communication.

These commands should help you check the status and configuration of your Docker Swarm. Adjust them as needed to inspect specific services or tasks within your Swarm.
