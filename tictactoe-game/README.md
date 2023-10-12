To start the block chain use with 5 nodes 
```
docker-compose -f sawtooth-default-pbft.yaml up
```
to get into the rest api for the 0 - node
```
docker exec -it sawtooth-rest-api-default-0 bash

```
to get into the bash 
```
docker exec -it sawtooth-shell-default bash

```
to generate keys for jack and jill (2 players)
```
sawtooth keygen jack
sawtooth keygen jill
```
to create a game on node 0
```
xo create my-game --username jack --url http://sawtooth-rest-api-default-0:8008
```
Verify that the create transaction was committed by displaying the list of existing games:
```
xo list --url http://sawtooth-rest-api-default-0:8008
```
Start playing tic-tac-toe by taking a space as the first player, Jack. In this example, Jack takes space 5:
```
xo take my-game 5 --username jack --url http://sawtooth-rest-api-default-0:8008

```
Next, take a space on the board as player 2, Jill. In this example, Jill takes space 1:
```
xo take my-game 1 --username jill --url http://sawtooth-rest-api-default-0:8008
```
Whenever you want to see the current state of the game board, enter the following command:
```
xo show my-game --url http://sawtooth-rest-api-default-0:8008
```

result:
```
GAME:     : my-game
PLAYER 1  : 023d47
PLAYER 2  : 0265ef
STATE     : P1-NEXT

  O |   |  
 ---|---|---
    | X |  
 ---|---|---
    |   |  
```

