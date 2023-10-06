# To use the single node kubernetes deployment use the file
Use the file ```docker/kubernetes/sawtooth-kubernetes-default.yaml```
Install the kubectl command:
````
 curl -Lo kubectl https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl \
&& chmod +x kubectl && sudo cp kubectl /usr/local/bin/ && rm kubectl
```

Install minikube :
```
 curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 \
&& chmod +x minikube && sudo cp minikube /usr/local/bin/ && rm minikube
```
start minikube:
```
minikube start
```
check pods:
```
kubectl get pods
```
to start the sawtooth you have to be present in this directory
```
kubectl apply -f sawtooth-kubernetes-default.yaml
```
to start minikube dsahboard:
```
minikube dashboard
```
Connect to the Kubernetes Shell Container:
```
kubectl exec -it $(kubectl get pods | awk '/sawtooth-0/{print $1}') --container sawtooth-shell -- bash
```
Confirm Connectivity to the REST API (for Kubernetes)
```

root@sawtooth-0# curl http://localhost:8008/blocks
```
Test Basic Sawtooth Functionality:
Display the list of blocks on the Sawtooth blockchain.
```
root@sawtooth-0# sawtooth block list
```
display more information about the block.
```
root@sawtooth-0# sawtooth block show {BLOCK-ID}
```
Use Sawtooth Commands as a Client:
Use intkey create_batch to prepare batches of transactions that set a few keys to random values, then randomly increment and decrement those values. These batches are saved locally in the file batches.intkey
```
root@sawtooth-0# intkey create_batch --count 10 --key-count 5
```
Use intkey load to submit the batches to the validator, which commits these batches of transactions as new blocks on the blockchain.
```
root@sawtooth-0# intkey load -f batches.intkey
```
```OR``` YOU CAN USE BATCH SUBMIT
create a batch of transactions:
```
root@sawtooth-0# intkey create_batch --count 6 --key-count 3
```
Submit the batch file with sawtooth batch submit:
```
root@sawtooth-0# sawtooth batch submit -f batches.intkey
```
Viewing Blockchain and Block Data with sawtooth block:

# To use the multi node (5 nodes) deployment use the file
## for poet
```
docker/kubernetes/sawtooth-kubernetes-default-poet.yaml
```
## for pbft
```
docker/kubernetes/sawtooth-kubernetes-default-pbft.yaml
```
