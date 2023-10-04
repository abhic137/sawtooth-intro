# sawtooth-intro
Sawtooth in blockchain is a modular and flexible platform for building, deploying, and running distributed ledgers (also called blockchains). It is part of the Hyperledger project, which is an open source initiative to develop blockchain technologies for business use.

Sawtooth is designed to be scalable and secure, and it supports a variety of features that make it suitable for enterprise applications. For example, Sawtooth supports multiple consensus algorithms, including PBFT and PoET. This allows businesses to choose the consensus algorithm that best meets their needs.

Sawtooth also supports parallel transaction processing, which can improve the performance of blockchain applications. Additionally, Sawtooth is modularly designed, which makes it easy to add new features and capabilities.

Here are some of the key features of Sawtooth in blockchain:

    Modular design: Sawtooth is designed to be modular, which makes it easy to add new features and capabilities.
    Scalability: Sawtooth is designed to be scalable to handle large volumes of transactions.
    Security: Sawtooth uses a variety of security features to protect the blockchain from attack.
    Flexibility: Sawtooth supports a variety of features and capabilities, making it suitable for a wide range of enterprise applications.

Here are some examples of how Sawtooth can be used in blockchain applications:

    Supply chain management: Sawtooth can be used to track the movement of goods through a supply chain, from raw materials to finished products. This can help to improve transparency and efficiency in the supply chain.
    Trade finance: Sawtooth can be used to facilitate trade finance transactions, such as letters of credit and invoices. This can help to reduce risk and improve efficiency in the trade finance process.
    Healthcare: Sawtooth can be used to store and manage patient medical records. This can help to improve the quality and efficiency of healthcare services.

Hyperledger Sawtooth supports both public and permissioned modes for blockchain networks, and the choice between them depends on the use case and the level of control and access you want over the network. Here's a comparison of the two modes:

Public Mode:

    Open Access: In public mode, the network is open to anyone who wants to participate. There are no restrictions on who can join as a validator node or transact on the blockchain.

    Decentralization: Public networks are typically more decentralized because anyone can participate as a validator. This decentralization can enhance security and censorship resistance.

    Lack of Control: The downside of open access is that you have less control over who participates. This may lead to security challenges and scalability concerns.

    Anonymity: Participants in a public network can often maintain a level of anonymity, which can be important for privacy-focused applications.

    Examples: Bitcoin and Ethereum are examples of public blockchains.

Permissioned Mode:

    Access Control: Permissioned networks require participants to be authorized before they can join. This means that you have control over who can run validator nodes and transact on the network.

    Consensus Flexibility: Permissioned networks often offer more flexibility in choosing and configuring consensus mechanisms. This allows you to tailor the network to your specific requirements.

    Privacy and Confidentiality: Permissioned blockchains are often used for business and enterprise applications where data privacy and confidentiality are crucial. Participants can be identified and may have varying levels of access to data.

    Compliance: Permissioned networks are often designed to meet regulatory and compliance requirements, making them suitable for industries like finance and healthcare.

    Examples: Hyperledger Sawtooth itself is often used in permissioned deployments, and other examples include Hyperledger Fabric and R3 Corda.

In summary, the key difference between public and permissioned modes in blockchain networks, including Hyperledger Sawtooth, is the level of access control and openness. Public networks are open to anyone and are more decentralized, while permissioned networks are restricted to authorized participants and offer more control over consensus and data privacy. The choice between these modes depends on the specific requirements and goals of the blockchain application.

## Consensus algos:
### Devmode:

"Devmode" is a term often used in the context of blockchain development environments. It refers to a mode in which a blockchain platform, like Hyperledger Sawtooth, can be configured for local development and testing. Devmode is typically used by blockchain developers to create and test smart contracts, experiment with transactions, and build and debug applications in a controlled and simplified environment. Here's how it works:

    Local Environment: Devmode allows you to run a blockchain network locally on your development machine. It's not intended for production use but is ideal for rapid development and testing.

    Simplified Consensus: In a devmode setup, consensus mechanisms are usually simplified to make it easy for developers to quickly validate and add transactions to the blockchain. It may use a basic consensus algorithm or no consensus at all, depending on the specific blockchain platform.

    Faster Transactions: Transactions are processed quickly, and new blocks are added rapidly, which is useful for testing and debugging purposes. In a production blockchain, consensus and block creation may take more time and involve multiple validators.

    No Decentralization: Devmode often involves a single-node or limited-node configuration, which doesn't reflect the decentralized nature of a production blockchain network. In a real-world scenario, multiple nodes participate in consensus, whereas in devmode, you might have only one node.

    Isolation: Devmode provides isolation from the real blockchain network, ensuring that any experiments or tests you perform don't affect a live network.

In summary, devmode is a development environment that simplifies and accelerates blockchain development by providing a local and controlled setup. It's an essential tool for developers to build and test blockchain applications before deploying them to a production blockchain network.
### PBFT (Practical Byzantine Fault Tolerance):

PBFT stands for "Practical Byzantine Fault Tolerance," and it's a consensus algorithm used in some blockchain networks, including Hyperledger Fabric. PBFT is designed to address the Byzantine Generals Problem, which is a classic problem in distributed computing and consensus.

Here's how PBFT works:

    Node Roles: In a PBFT-based network, there are two types of nodes: clients and validators.

    Client Transactions: Clients initiate transactions by sending them to the network.

    Preparation Phase:
        Validators receive and validate incoming transactions.
        They propose a specific order for the transactions and send their proposals to other validators.
        Validators gather proposals from their peers and select a specific order based on a two-thirds majority vote.

    Commitment Phase:
        Validators send a "commit" message once they've received enough matching proposals from other validators.
        Once a validator collects enough commit messages from others, it enters the committed state for that block.

    Finalization and Consensus:
        When a validator has entered the committed state for a block, it considers that block as "finalized."
        Blocks that are finalized by a sufficient number of validators become part of the blockchain.

Key features of PBFT:

    Safety: PBFT ensures that once a block is committed, it's never reverted. This provides strong consistency and finality.
    Performance: PBFT is efficient and can achieve consensus quickly, making it suitable for permissioned blockchains.
    Tolerant to Byzantine Faults: PBFT can tolerate up to one-third of the nodes behaving maliciously or failing, making it a robust consensus algorithm.

In summary, PBFT is a consensus algorithm used in some permissioned blockchain networks to achieve consensus among validators while tolerating a certain number of malicious or faulty nodes. It provides strong consistency and high performance, making it suitable for enterprise and consortium blockchain applications.

"PoET" stands for "Proof of Elapsed Time," and it's a consensus algorithm used in some blockchain platforms, including Hyperledger Sawtooth. PoET is designed to achieve consensus in a more energy-efficient and fair manner compared to traditional Proof of Work (PoW) or Proof of Stake (PoS) algorithms.

### Here's an explanation of how PoET works:

    Random Wait Times:
        In PoET, the process of selecting the next validator to create a new block is based on a random wait time.
        Each validator participating in the consensus process generates a random wait time and waits for the specified duration before proposing a new block.

    Trusted Execution Environment (TEE):
        To ensure that validators cannot manipulate their wait times and cheat the system, PoET relies on a Trusted Execution Environment (TEE).
        A TEE is a secure hardware component that provides a trusted and isolated environment for running code.

    Wait Certificate:
        Validators request a wait time from the TEE and receive a "wait certificate" that contains the actual wait time.
        Validators must include this wait certificate in their block proposal.

    Shortest Wait Time Wins:
        Validators broadcast their block proposals along with their wait certificates to the network.
        The validator with the shortest wait time is given the privilege to add the new block to the blockchain.

Key characteristics of PoET:

    Fairness: PoET aims to achieve fairness by ensuring that no single validator has a significant advantage in proposing new blocks. Validators are selected based on random wait times.

    Energy Efficiency: PoET does not require the energy-intensive computational work that PoW does. Validators only need to wait for a specified time, which is energy-efficient.

    Decentralization: PoET allows for a decentralized network of validators, similar to PoW, while avoiding the high energy consumption associated with PoW.

    Security: The use of TEEs helps prevent validators from manipulating wait times or cheating the system, enhancing the security of the consensus process.

    Low Latency: PoET can achieve low-latency block creation since validators don't need to solve complex cryptographic puzzles like in PoW.

It's important to note that PoET is typically used in permissioned or consortium blockchain networks where there is a level of trust among participants. In these networks, validators are known entities, and the focus is on achieving efficiency, fairness, and security in consensus while avoiding the resource-intensive nature of PoW.

Overall, PoET is an innovative consensus algorithm that addresses some of the limitations of traditional consensus mechanisms and is designed for specific use cases where energy efficiency and fairness are important considerations.


## Installing on docker 
Using Docker for a Single Sawtooth Node

This procedure explains how to set up Hyperledger Sawtooth for application development using a multi-container Docker environment. It shows you how to start Sawtooth and connect to the necessary Docker containers, then walks you through the following tasks:

        Checking the status of Sawtooth components
        Using Sawtooth commands to submit transactions, display block data, and view global state
        Examining Sawtooth logs
        Stopping Sawtooth and resetting the Docker environment

After completing this tutorial, you will have the application development environment that is required for the other tutorials in this guide. The next tutorial introduces the XO transaction family by using the xo client commands to play a game of tic-tac-toe. The final set of tutorials describe how to use an SDK to create a transaction family that implements your application's business logic.
About the Docker Test Node Environment

This Docker environment is a single Sawtooth node that is running a validator, a REST API, the Devmode consensus engine, and three transaction processors. The environment uses Devmode consensus and parallel transaction processing.

Environment with one node 3 TPS

This environment introduces basic Sawtooth functionality with the IntegerKey and Settings transaction processors for the business logic and Sawtooth commands as a client. It also includes the XO transaction processor, which is used in later tutorials.

The IntegerKey and XO families are simple examples of a transaction family, but Settings is a reference implementation. In a production environment, you should always run a transaction processor that supports the Settings transaction family.

    Note

    The Docker environment includes a Docker Compose file that handles environment setup steps such as generating keys and creating a genesis block. To learn how the typical startup process works, see Using Docker for a Single Sawtooth Node

Prerequisites

This application development environment requires Docker Engine and Docker Compose.

    Windows: Install the latest version of Docker Engine for Windows (also installs Docker Compose).
    macOS: Install the latest version of Docker Engine for macOS (also installs Docker Compose).
    Linux: Install the latest versions of Docker Engine and Docker Compose. Then follow Post-Install steps.

In this procedure, you will open six terminal windows to connect to the Docker containers: one for each Sawtooth component and one to use for client commands.

    Note

    The Docker Compose file for Sawtooth handles environment setup steps such as generating keys and creating a genesis block. To learn how the typical startup process works, see Using Docker for a Single Sawtooth Node

Step 1: Download the Sawtooth Docker Compose File

Download the Docker Compose file for the Sawtooth environment, sawtooth-default.yaml.

This example Compose file defines the process for constructing a simple Sawtooth environment with following containers:

    A single validator using Devmode consensus
    A REST API connected to the validator
    The Settings transaction processor (sawtooth-settings)
    The IntegerKey transaction processor (intkey-tp-python)
    The XO transaction processor (xo-tp-python)
    A client (shell) container for running Sawtooth commands

The Compose file also specifies the container images to download from Docker Hub and the network settings needed for all the containers to communicate correctly.

After completing the tutorials in this guide, you can use this Compose file as the basis for your own multi-container Sawtooth development environment or application.
Step 2: Configure Proxy Settings (Optional)

To configure Docker to work with an HTTP or HTTPS proxy server, follow the instructions for proxy configuration in the documentation for your operating system:

    Windows - See "Get Started with Docker for Windows".
    macOS - See "Get Started with Docker for Mac".
    Linux - See "Control and configure Docker with Systemd".

Step 3: Start the Sawtooth Docker Environment

To start the Sawtooth Docker environment, perform the following tasks:

    Open a terminal window.

    Change your working directory to the same directory where you saved the Docker Compose file.

    Run the following command:

    user@host$ docker-compose -f sawtooth-default.yaml up

        Tip

        If you previously ran docker-compose ... up without a clean shut down, run the following command first:

        docker-compose -f sawtooth-default.yaml down

    Downloading the Docker images for the Sawtooth environment can take several minutes. Wait until you see output that shows the containers registering and creating initial blocks. Once you see output that resembles the following example, you can move on to the next step.

    ...
    sawtooth-settings-tp-default | [2018-03-08 22:55:10.537 INFO     core] register attempt: OK
    sawtooth-settings-tp-default | [2018-03-08 22:55:10.538 DEBUG    core] received message of type: TP_PROCESS_REQUEST
    sawtooth-settings-tp-default | [2018-03-08 22:55:10.550 INFO     handler] Setting setting sawtooth.settings.vote.authorized_keys changed from None to 039fa17f2962706aae83f3cc1f7d0c51dda7ffe15f5811fefd4ea5fdd3e84d0755
    sawtooth-validator-default | [2018-03-08 22:55:10.557 DEBUG    genesis] Produced state hash 53d38378e8c61f42112c39f9c84d42d339320515ef44f50d6b4dd52f3f1b9054 for genesis block.
    sawtooth-validator-default | [2018-03-08 22:55:10.560 INFO     genesis] Genesis block created: 60e79c91757c73185b36802661833f586f4dd5ef3c4cb889f37c287921af8ad01a8b95e9d81af698e6c3f3eb7b65bfd6f6b834ffc9bc36317d8a1ae7ecc45668 (block_num:0, state:53d38378e8c61f42112c39f9c84d42d339320515ef44f50d6b4dd52f3f1b9054, previous_block_id:0000000000000000)
    sawtooth-validator-default | [2018-03-08 22:55:10.561 DEBUG    chain_id_manager] writing block chain id
    sawtooth-validator-default | [2018-03-08 22:55:10.562 DEBUG    genesis] Deleting genesis data.
    sawtooth-validator-default | [2018-03-08 22:55:10.564 DEBUG    selector_events] Using selector: ZMQSelector
    sawtooth-validator-default | [2018-03-08 22:55:10.565 INFO     interconnect] Listening on tcp://eth0:8800
    sawtooth-validator-default | [2018-03-08 22:55:10.566 DEBUG    dispatch] Added send_message function for connection ServerThread
    sawtooth-validator-default | [2018-03-08 22:55:10.566 DEBUG    dispatch] Added send_last_message function for connection ServerThread
    sawtooth-validator-default | [2018-03-08 22:55:10.568 INFO     chain] Chain controller initialized with chain head: 60e79c91757c73185b36802661833f586f4dd5ef3c4cb889f37c287921af8ad01a8b95e9d81af698e6c3f3eb7b65bfd6f6b834ffc9bc36317d8a1ae7ecc45668 (block_num:0, state:53d38378e8c61f42112c39f9c84d42d339320515ef44f50d6b4dd52f3f1b9054, previous_block_id:0000000000000000)
    sawtooth-validator-default | [2018-03-08 22:55:10.569 INFO     publisher] Now building on top of block: 60e79c91757c73185b36802661833f586f4dd5ef3c4cb889f37c287921af8ad01a8b95e9d81af698e6c3f3eb7b65bfd6f6b834ffc9bc36317d8a1ae7ecc45668 (block_num:0, state:53d38378e8c61f42112c39f9c84d42d339320515ef44f50d6b4dd52f3f1b9054, previous_block_id:0000000000000000)
    ...

This terminal window will continue to display log messages as you run commands in other containers.

    Note

    If you need to reset the environment for any reason, see Stop the Sawtooth Docker Environment

Step 4: Log Into the Docker Client Container

Sawtooth includes commands that act as a client application. The client container is used to run these Sawtooth commands, which interact with the validator through the REST API.

To log into the client container, open a new terminal window and run the following command:

user@host$ docker exec -it sawtooth-shell-default bash
root@client#

In this procedure, the prompt root@client# is used for commands that should be run in the terminal window for the client container.

    Important

    Your environment is ready for experimenting with Sawtooth. However, any work done in this environment will be lost once the container in which you ran docker-compose exits. In order to use this application development environment for application development, you would need to take additional steps, such as mounting a host directory into the container. See the Docker documentation for more information.

Step 5: Confirm Connectivity to the REST API (for Docker)

    To confirm that the REST API and validator are running and reachable from the client container, run this curl command:

    root@client# curl http://rest-api:8008/blocks

    To check connectivity from the host computer, open a new terminal window on your host system and run this curl command:

    user@host$ curl http://localhost:8008/blocks

    If the validator and REST API are running and reachable, the output for each command should be similar to this example:

    {
      "data": [
        {
          "batches": [],
          "header": {
            "batch_ids": [],
            "block_num": 0,
            "mconsensus": "R2VuZXNpcw==",
            "previous_block_id": "0000000000000000",
            "signer_public_key": "03061436bef428626d11c17782f9e9bd8bea55ce767eb7349f633d4bfea4dd4ae9",
            "state_root_hash": "708ca7fbb701799bb387f2e50deaca402e8502abe229f705693d2d4f350e1ad6"
          },
          "header_signature": "119f076815af8b2c024b59998e2fab29b6ae6edf3e28b19de91302bd13662e6e43784263626b72b1c1ac120a491142ca25393d55ac7b9f3c3bf15d1fdeefeb3b"
        }
      ],
      "head": "119f076815af8b2c024b59998e2fab29b6ae6edf3e28b19de91302bd13662e6e43784263626b72b1c1ac120a491142ca25393d55ac7b9f3c3bf15d1fdeefeb3b",
      "link": "http://rest-api:8008/blocks?head=119f076815af8b2c024b59998e2fab29b6ae6edf3e28b19de91302bd13662e6e43784263626b72b1c1ac120a491142ca25393d55ac7b9f3c3bf15d1fdeefeb3b",
      "paging": {
        "start_index": 0,
        "total_count": 1
      }
    }

    If the validator process or the validator container is not running, the curl command will time out or return nothing.

Step 6: Use Sawtooth Commands as a Client

Sawtooth includes commands that act as a client application. This step describes how to use the intkey and sawtooth commands to create and submit transactions, display blockchain and block data, and examine global state data.

    Note

    Use the --help option with any Sawtooth command to display the available options and subcommands.

To run the commands in this section, use the terminal window for the client container.
Creating and Submitting Transactions with intkey

The intkey command creates and submits IntegerKey transactions for testing purposes.

    Use intkey create_batch to prepare batches of transactions that set a few keys to random values, then randomly increment and decrement those values. These batches are saved locally in the file batches.intkey.

    root@client# intkey create_batch --count 10 --key-count 5
    Writing to batches.intkey...

    Use intkey load to submit the batches to the validator.

    root@client# intkey load -f batches.intkey --url http://rest-api:8008
    batches: 11 batch/sec: 141.7800162868952

    The terminal window in which you ran the docker-compose command displays log messages showing that the validator is handling the submitted transactions and that values are being incremented and decremented, as in this example:

    sawtooth-intkey-tp-python-default | [2018-03-08 21:26:20.334 DEBUG    core] received message of type: TP_PROCESS_REQUEST
    sawtooth-intkey-tp-python-default | [2018-03-08 21:26:20.339 DEBUG    handler] Decrementing "GEJTiZ" by 10
    sawtooth-intkey-tp-python-default | [2018-03-08 21:26:20.347 DEBUG    core] received message of type: TP_PROCESS_REQUEST
    sawtooth-intkey-tp-python-default | [2018-03-08 21:26:20.352 DEBUG    handler] Decrementing "lrAYjm" by 8
    ...
    sawtooth-validator-default | [2018-03-08 21:26:20.397 INFO     chain] Fork comparison at height 50 is between - and 3d4d952d
    sawtooth-validator-default | [2018-03-08 21:26:20.397 INFO     chain] Chain head updated to: 3d4d952d4774988bd67a4deb85830155a5f505c68bea11d832a6ddbdd5eeebc34f5a63a9e59a426376cd2e215e19c0dfa679fe016be26307c3ee698cce171d51 (block_num:50, state:e18c2ce54859d1e9a6e4fb949f8d861e483d330b363b4060b069f53d7e6c6380, previous_block_id:e05737151717eb8787a2db46279fedf9d331a501c12cd8059df379996d9a34577cf605e95f531514558b200a386dc73e11de3fa17d6c00882acf6f9d9c387e82)
    sawtooth-validator-default | [2018-03-08 21:26:20.398 INFO     publisher] Now building on top of block: 3d4d952d4774988bd67a4deb85830155a5f505c68bea11d832a6ddbdd5eeebc34f5a63a9e59a426376cd2e215e19c0dfa679fe016be26307c3ee698cce171d51 (block_num:50, state:e18c2ce54859d1e9a6e4fb949f8d861e483d330b363b4060b069f53d7e6c6380, previous_block_id:e05737151717eb8787a2db46279fedf9d331a501c12cd8059df379996d9a34577cf605e95f531514558b200a386dc73e11de3fa17d6c00882acf6f9d9c387e82)
    sawtooth-validator-default | [2018-03-08 21:26:20.401 DEBUG    chain] Verify descendant blocks: 3d4d952d4774988bd67a4deb85830155a5f505c68bea11d832a6ddbdd5eeebc34f5a63a9e59a426376cd2e215e19c0dfa679fe016be26307c3ee698cce171d51 (block_num:50, state:e18c2ce54859d1e9a6e4fb949f8d861e483d330b363b4060b069f53d7e6c6380, previous_block_id:e05737151717eb8787a2db46279fedf9d331a501c12cd8059df379996d9a34577cf605e95f531514558b200a386dc73e11de3fa17d6c00882acf6f9d9c387e82) ([])
    sawtooth-validator-default | [2018-03-08 21:26:20.402 INFO     chain] Finished block validation of: 3d4d952d4774988bd67a4deb85830155a5f505c68bea11d832a6ddbdd5eeebc34f5a63a9e59a426376cd2e215e19c0dfa679fe016be26307c3ee698cce171d51 (block_num:50, state:e18c2ce54859d1e9a6e4fb949f8d861e483d330b363b4060b069f53d7e6c6380, previous_block_id:e05737151717eb8787a2db46279fedf9d331a501c12cd8059df379996d9a34577cf605e95f531514558b200a386dc73e11de3fa17d6c00882acf6f9d9c387e82)

    You can also use docker logs to examine at the Sawtooth log messages from your host system. For example, this command displays the last five entries in the log:

    user@host$ docker logs --tail 5 sawtooth-validator-default
    sawtooth-validator-default | [2018-03-08 21:26:20.397 INFO     chain] Fork comparison at height 50 is between - and 3d4d952d
    sawtooth-validator-default | [2018-03-08 21:26:20.397 INFO     chain] Chain head updated to: 3d4d952d4774988bd67a4deb85830155a5f505c68bea11d832a6ddbdd5eeebc34f5a63a9e59a426376cd2e215e19c0dfa679fe016be26307c3ee698cce171d51 (block_num:50, state:e18c2ce54859d1e9a6e4fb949f8d861e483d330b363b4060b069f53d7e6c6380, previous_block_id:e05737151717eb8787a2db46279fedf9d331a501c12cd8059df379996d9a34577cf605e95f531514558b200a386dc73e11de3fa17d6c00882acf6f9d9c387e82)
    sawtooth-validator-default | [2018-03-08 21:26:20.398 INFO     publisher] Now building on top of block: 3d4d952d4774988bd67a4deb85830155a5f505c68bea11d832a6ddbdd5eeebc34f5a63a9e59a426376cd2e215e19c0dfa679fe016be26307c3ee698cce171d51 (block_num:50, state:e18c2ce54859d1e9a6e4fb949f8d861e483d330b363b4060b069f53d7e6c6380, previous_block_id:e05737151717eb8787a2db46279fedf9d331a501c12cd8059df379996d9a34577cf605e95f531514558b200a386dc73e11de3fa17d6c00882acf6f9d9c387e82)
    sawtooth-validator-default | [2018-03-08 21:26:20.401 DEBUG    chain] Verify descendant blocks: 3d4d952d4774988bd67a4deb85830155a5f505c68bea11d832a6ddbdd5eeebc34f5a63a9e59a426376cd2e215e19c0dfa679fe016be26307c3ee698cce171d51 (block_num:50, state:e18c2ce54859d1e9a6e4fb949f8d861e483d330b363b4060b069f53d7e6c6380, previous_block_id:e05737151717eb8787a2db46279fedf9d331a501c12cd8059df379996d9a34577cf605e95f531514558b200a386dc73e11de3fa17d6c00882acf6f9d9c387e82) ([])
    sawtooth-validator-default | [2018-03-08 21:26:20.402 INFO     chain] Finished block validation of: 3d4d952d4774988bd67a4deb85830155a5f505c68bea11d832a6ddbdd5eeebc34f5a63a9e59a426376cd2e215e19c0dfa679fe016be26307c3ee698cce171d51 (block_num:50, state:e18c2ce54859d1e9a6e4fb949f8d861e483d330b363b4060b069f53d7e6c6380, previous_block_id:e05737151717eb8787a2db46279fedf9d331a501c12cd8059df379996d9a34577cf605e95f531514558b200a386dc73e11de3fa17d6c00882acf6f9d9c387e82)

Submitting Transactions with sawtooth batch submit

In the example above, the intkey create_batch command created the file batches.intkey. Rather than using intkey load to submit these transactions, you could use sawtooth batch submit to submit them.

    As before, create a batch of transactions:

    root@client# intkey create_batch --count 10 --key-count 5
    Writing to batches.intkey...

    Submit the batch file with sawtooth batch submit:

    root@client# sawtooth batch submit -f batches.intkey --url http://rest-api:8008
    batches: 11,  batch/sec: 216.80369536716367

Viewing Blockchain and Block Data with sawtooth block

The sawtooth block command displays information about the blocks stored on the blockchain.

    Use sawtooth block list to display the list of blocks stored in state.

        root@client# sawtooth block list --url http://rest-api:8008

        The output shows the block number and block ID, as in this example:

        NUM  BLOCK_ID                                                                                                                          BATS  TXNS  SIGNER
        61   9566426220751691b7463e3c1ec1d8c4f158c98e89722672721d457182cb3b3d48e734ddceabf706b41fc3e1f8d739451f7d70bd5a8708bc4085b6fb33b40bef  1     4     020d21...
        60   309c0707b95609d4ebc2fad0afd590ec40db41680a3edbbeb0875720ed59f4d775e1160a2c6cbe2e9ccb34c4671f4cd7db1e5ed35a2ed9a0f2a2c99aa981f83c  1     5     020d21...
        59   e0c6c29a9f3d1436e4837c96587ae3fa60274991efa9d0c9000d53694cd2a0841914b2f362aa05c2385126288f060f524bac3a05850edb1ac1c86f0c237afdba  1     3     020d21...
        58   8c67a1ec68bfdd5b07bb02919019b917ed26dbc6ec0fc3de15d539538bd30f8a1aa58795578970d2e607cd63cf1f5ef921476cbc0564cbe37469e5e50b72ecf2  1     3     020d21...
        57   879c6cb43e244fb7c1676cf5d9e51ace25ad8e670f37e81b81e5d9e133aebba80282913677821c14fe2ccb2aae631229bdd044222e6a8927f4f5dabb6d62c409  1     4     020d21...
        ...
        5    dce0921531472a8f9840e256c585917dfc22b78c5045a3416ed76faf57232b065b8be5a34023e8a8cdab74ab24cf029a5c1051f742b9b5280b8edab5a80d805d  2     4     020d21...
        4    0007380e98fc6d63de1d47261b83186bce9722023f2e6ab6849916766e9be29f4903d76a642dfc27579b8a8bf9adba5f077c1f1457b2cad8f52a28d7079333a6  1     8     020d21...
        3    515c827b9e84c22c24838130d4e0f6af07ab271c138a61c555a830c4118a75815f54340ef3f04de009c94c3531f3202690708cf16fcfee04303972cb91e3b87a  1     10    020d21...
        2    9067bcb093bb095ca436d8868914ecf2630215d36bfd78b0b167554c544b9842193dd309f135e6959a664fe34b06b4f16a297528249550821cda9273291ebe70  1     5     020d21...
        1    3ab950b2cd370f26e188d95ee97268965732768080ca1adb71759e3c1f22d1ea19945b48fc81f5f821387fde355349f87096da00a4e356408b630ab80576d3ae  1     5     020d21...
        0    51a704e1a83086372a3c0823533881ffac9479995289902a311fd5d99ff6a32216cd1fb9883a421449c943cad8604ce1447b0f6080c8892e334b14dc082f91d3  1     1     020d21...

    From the output generated by sawtooth block list, copy the ID of a block you want to view, then paste it in place of {BLOCK_ID} in the following command:

    root@client# sawtooth block show --url http://rest-api:8008 {BLOCK_ID}

    The output of this command can be quite long, because it includes all data stored under that block. This is a truncated example:

    batches:
    - header:
        signer_public_key: 0276023d4f7323103db8d8683a4b7bc1eae1f66fbbf79c20a51185f589e2d304ce
        transaction_ids:
        - 24b168aaf5ea4a76a6c316924a1c26df0878908682ea5740dd70814e7c400d56354dee788191be8e28393c70398906fb467fac8db6279e90e4e61619589d42bf
      header_signature: a93731646a8fd2bce03b3a17bc2cb3192d8597da93ce735950dccbf0e3cf0b005468fadb94732e013be0bc2afb320be159b452cf835b35870db5fa953220fb35
      transactions:
      - header:
          batcher_public_key: 0276023d4f7323103db8d8683a4b7bc1eae1f66fbbf79c20a51185f589e2d304ce
          dependencies: []
          family_name: sawtooth_settings
          family_version: '1.0'
    ...
    header:
      batch_ids:
      - a93731646a8fd2bce03b3a17bc2cb3192d8597da93ce735950dccbf0e3cf0b005468fadb94732e013be0bc2afb320be159b452cf835b35870db5fa953220fb35
      block_num: 3
      consensus: RGV2bW9kZQ==
      previous_block_id: 042f08e1ff49bbf16914a53dc9056fb6e522ca0e2cff872547eac9555c1de2a6200e67fb9daae6dfb90f02bef6a9088e94e5bdece04f622bce67ccecd678d56e
      signer_public_key: 033fbed13b51eafaca8d1a27abc0d4daf14aab8c0cbc1bb4735c01ff80d6581c52
      state_root_hash: 5d5ea37cbbf8fe793b6ea4c1ba6738f5eee8fc4c73cdca797736f5afeb41fbef
    header_signature: ff4f6705bf57e2a1498dc1b649cc9b6a4da2cc8367f1b70c02bc6e7f648a28b53b5f6ad7c2aa639673d873959f5d3fcc11129858ecfcb4d22c79b6845f96c5e3

Viewing State Data with sawtooth state

The sawtooth state command lets you display state data. Sawtooth stores state data in a Merkle-Radix tree; for more information, see Global State.

    Use sawtooth state list to list the nodes (addresses) in state:

    root@client# sawtooth state list --url http://rest-api:8008

    The output will be similar to this truncated example:

    ADDRESS                                                                                                                                SIZE DATA
    1cf126ddb507c936e4ee2ed07aa253c2f4e7487af3a0425f0dc7321f94be02950a081ab7058bf046c788dbaf0f10a980763e023cde0ee282585b9855e6e5f3715bf1fe 11   b'\xa1fcCTdcH\x...
    1cf1260cd1c2492b6e700d5ef65f136051251502e5d4579827dc303f7ed76ddb7185a19be0c6443503594c3734141d2bdcf5748a2d8c75541a8e568bae063983ea27b9 11   b'\xa1frdLONu\x...
    1cf126ed7d0ac4f755be5dd040e2dfcd71c616e697943f542682a2feb14d5f146538c643b19bcfc8c4554c9012e56209f94efe580b6a94fb326be9bf5bc9e177d6af52 11   b'\xa1fAUZZqk\x...
    1cf126c46ff13fcd55713bcfcf7b66eba515a51965e9afa8b4ff3743dc6713f4c40b4254df1a2265d64d58afa14a0051d3e38999704f6e25c80bed29ef9b80aee15c65 11   b'\xa1fLvUYLk\x...
    1cf126c4b1b09ebf28775b4923e5273c4c01ba89b961e6a9984632612ec9b5af82a0f7c8fc1a44b9ae33bb88f4ed39b590d4774dc43c04c9a9bd89654bbee68c8166f0 13   b'\xa1fXHonWY\x...
    1cf126e924a506fb2c4bb8d167d20f07d653de2447df2754de9eb61826176c7896205a17e363e457c36ccd2b7c124516a9b573d9a6142f031499b18c127df47798131a 13   b'\xa1foWZXEz\x...
    1cf126c295a476acf935cd65909ed5ead2ec0168f3ee761dc6f37ea9558fc4e32b71504bf0ad56342a6671db82cb8682d64689838731da34c157fa045c236c97f1dd80 13   b'\xa1fadKGve\x...

    Use sawtooth state show to view state data at a specific address (a node in the Merkle-Radix database). Copy the address from the output of sawtooth state list, then paste it in place of {STATE_ADDRESS} in the following command:

    root@client# sawtooth state show --url http://rest-api:8008 {STATE_ADDRESS}

    The output shows the bytes stored at that address and the block ID of the "chain head" that the current state is tied to, as in this example:

    DATA: "b'\xa1fcCTdcH\x192B'"
    HEAD: "0c4364c6d5181282a1c7653038ec9515cb0530c6bfcb46f16e79b77cb524491676638339e8ff8e3cc57155c6d920e6a4d1f53947a31dc02908bcf68a91315ad5"

Step 7: Connect to Each Container (Optional)

Use this information when you need to connect to any container in the Sawtooth application development environment. For example, you can examine the log files or check the status of Sawtooth components in any container.
Use the following docker command to list all running Docker containers

    user@host$ docker ps

    The output should resemble the following example:

    CONTAINER ID IMAGE                                     COMMAND               CREATED       STATUS       PORTS                            NAMES
    76f6731c43a9 hyperledger/sawtooth-all:chime              "bash -c 'sawtooth k" 7 minutes ago Up 7 minutes 4004/tcp, 8008/tcp               sawtooth-shell-default
    9844faed9e9d hyperledger/sawtooth-intkey-tp-python:chime "intkey-tp-python -v" 7 minutes ago Up 7 minutes 4004/tcp                         sawtooth-intkey-tp-python-default
    44db125c2dca hyperledger/sawtooth-settings-tp:chime      "settings-tp -vv -C " 7 minutes ago Up 7 minutes 4004/tcp                         sawtooth-settings-tp-default
    875df9d022d6 hyperledger/sawtooth-xo-tp-python:chime     "xo-tp-python -vv -C" 7 minutes ago Up 7 minutes 4004/tcp                         sawtooth-xo-tp-python-default
    93d048c01d30 hyperledger/sawtooth-rest-api:chime         "sawtooth-rest-api -" 7 minutes ago Up 7 minutes 4004/tcp, 0.0.0.0:8008->8008/tcp sawtooth-rest-api-default
    6bbcda66a5aa hyperledger/sawtooth-validator:chime        "bash -c 'sawadm key" 7 minutes ago Up 7 minutes 0.0.0.0:4004->4004/tcp           sawtooth-validator-default

The Docker Compose file defines the name of each container. It also specifies the TCP port and host name, if applicable. The following table shows the values in the example Compose file, sawtooth-default.yaml.
Component 	Container Name 	Port 	Host Name
Validator 	sawtooth-validator-default 	4004 	validator
REST API 	sawtooth-rest-api-default 	8008 	rest-api
Settings TP 	sawtooth-settings-tp-default 	  	settings-tp
IntegerKey TP 	sawtooth-intkey-tp-python-default 	  	intkey-tp-python
XO TP 	sawtooth-xo-tp-python-default 	  	xo-tp-python
Shell 	sawtooth-shell-default 	  	 

    Note that the validator and REST API ports are exposed to other containers and forwarded (published) for external connections, such as from your host system.

    Use the following docker exec command from your host system to connect to a Sawtooth Docker container.

    user@host$ docker exec -it {ContainerName} bash

    For example, you can use the following command from your host system to connect to the validator container:

    user@host$ docker exec -it sawtooth-validator-default bash

    After connecting to the container, you can use ps to verify that the Sawtooth component is running.

    # ps --pid 1 fw

    In the validator container, the output resembles the following example:

    PID TTY      STAT   TIME COMMAND
     1 ?        Ss     0:00 bash -c sawadm keygen && sawtooth keygen my_key
    && sawset genesis -k /root/.sawtooth/keys/my_key.priv && sawadm genesis
    config-genesis.batch && sawtooth-validator -vv --endpoint

Step 8: Examine Sawtooth Logs

As described above, you can display Sawtooth log messages by using the docker logs command from your host system:

user@host$ docker logs {OPTIONS} {ContainerName}

In each container, the Sawtooth log files for that component are stored in the directory /var/log/sawtooth. Each component (validator, REST API, and transaction processors) has both a debug log and an error log.

For example, the validator container has these log files:

root@validator# ls -1 /var/log/sawtooth
validator-debug.log
validator-error.log

The IntegerKey container has these log files:

root@intkey-tp# ls -1 /var/log/sawtooth
intkey-ae98c3726f9743c4-debug.log
intkey-ae98c3726f9743c4-error.log

    Note

    By convention, the transaction processors use a random string to make the log file names unique. The names on your system may be different than these examples.

For more information on log files, see Log Configuration.
Step 9: Stop the Sawtooth Docker Environment

Use this procedure if you need to stop or reset the Sawtooth environment for any reason.

    Important

    Any work done in this environment will be lost once the container exits. To keep your work, you would need to take additional steps, such as mounting a host directory into the container. See the Docker documentation for more information.

    Log out of the client container.

    Enter CTRL-c from the window where you originally ran docker-compose. The output will resemble this example:

    ^CGracefully stopping... (press Ctrl+C again to force)
    Stopping sawtooth-shell-default            ... done
    Stopping sawtooth-rest-api-default         ... done
    Stopping sawtooth-intkey-tp-python-default ... done
    Stopping sawtooth-xo-tp-python-default     ... done
    Stopping sawtooth-settings-tp-default      ... done
    Stopping sawtooth-validator-default        ... done

    After all containers have shut down, run this docker-compose command:

    user@host$ docker-compose -f sawtooth-default.yaml down
    Removing sawtooth-shell-default            ... done
    Removing sawtooth-intkey-tp-python-default ... done
    Removing sawtooth-xo-tp-python-default     ... done
    Removing sawtooth-settings-tp-default      ... done
    Removing sawtooth-rest-api-default         ... done
    Removing sawtooth-validator-default        ... done
    Removing network testsawtooth_default


Sawtooth is a powerful and flexible blockchain platform that can be used for a wide range of enterprise applications. It is still under development, but it has the potential to revolutionize the way that businesses operate.
https://sawtooth.hyperledger.org/docs/1.2/app_developers_guide/installing_sawtooth.html

https://sawtooth.hyperledger.org/docs/1.2/app_developers_guide/creating_sawtooth_network.html

## Installing on K8's

Using Kubernetes for a Single Sawtooth Node

This procedure explains how to create a single Hyperledger Sawtooth validator node with Kubernetes. This environment uses Minikube to deploy Sawtooth as a containerized application in a local Kubernetes cluster inside a virtual machine (VM) on your computer.

    Note

    This environment has one Sawtooth node. For a multiple-node environment, see Creating Sawtooth Network.

This procedure walks you through the following tasks:

        Installing kubectl and Minikube
        Starting Minikube
        Starting Sawtooth in a Kubernetes cluster
        Connecting to the Sawtooth shell container
        Using Sawtooth commands to submit transactions, display block data, and view global state
        Examining Sawtooth logs
        Stopping Sawtooth and deleting the Kubernetes cluster

After completing this procedure, you will have the environment required for the other tutorials in this guide, Playing with the XO Transaction Family and Using the SDKs.
Prerequisites

This application development environment requires kubectl and Minikube with a supported VM hypervisor, such as VirtualBox.
About the Kubernetes Test Node Environment

This Kubernetes environment is a single Sawtooth node that is running a validator, a REST API, the Devmode consensus engine, and three transaction processors. The environment uses Devmode consensus and parallel transaction processing/

Environment with one node 3 TPS

The Kubernetes cluster has one pod with a container for each Sawtooth component. After the container is running, you can use the Kubernetes dashboard to view pod status, container names, Sawtooth log files, and more.

This example environment includes the following transaction processors:

        Settings handles Sawtooth's on-chain settings. Thesawtooth-settings-tp transaction processor is required for this environment.
        IntegerKey is a basic application (also called transaction family) that introduces Sawtooth functionality. The sawtooth-intkey-tp-python transaction processor works with the int-key client, which has shell commands to perform integer-based transactions.
        XO is a simple application for playing a game of tic-tac-toe on the blockchain. The sawtooth-xo-tp-python transaction processor works with the xo client, which has shell commands to define players and play a game. XO is described in a later tutorial.

    Note

    Sawtooth provides the Settings transaction processor as a reference implementation. In a production environment, you must always run the Settings transaction processor or an equivalent that supports the `Sawtooth methodology for storing on-chain configuration settings

Step 1: Install kubectl and Minikube

This step summarizes the kubectl and Minikube installation procedures. For more information, see the Kubernetes documentation.

    Install a virtual machine (VM) hypervisor, such as VirtualBox, VMWare, KVM-QEMU, or Hyperkit. The steps in this procedure assume VirtualBox (the default).
    Install the kubectl command as described in the Kubernetes document Install kubectl.

        Linux quick reference:

        $ curl -Lo kubectl https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl \
        && chmod +x kubectl && sudo cp kubectl /usr/local/bin/ && rm kubectl

        Mac quick reference:

        $ curl -Lo kubectl https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/darwin/amd64/kubectl \
        && chmod +x kubectl && sudo cp kubectl /usr/local/bin/ && rm kubectl

    Install minikube as described in the Kubernetes document Install Minikube.

        Linux quick reference:

        $ curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 \
        && chmod +x minikube && sudo cp minikube /usr/local/bin/ && rm minikube

        Mac quick reference:

        $ curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-darwin-amd64 \
        && chmod +x minikube && sudo mv minikube /usr/local/bin/

Step 2: Start and Test Minikube

This step summarizes the procedure to start Minikube and test basic functionality. If you have problems, see the Kubernetes document Running Kubernetes Locally via Minikube.

    Start Minikube.

    $ minikube start

    Start Minikube's "Hello, World" test cluster, hello-minikube.

    $ kubectl run hello-minikube --image=k8s.gcr.io/echoserver:1.10 --port=8080

    $ kubectl expose deployment hello-minikube --type=NodePort

    Check the list of pods.

    $ kubectl get pods

    After the pod is up and running, the output of this command should display a pod starting with hello-minikube....

    Run a curl test to the cluster.

    $ curl $(minikube service hello-minikube --url)

    Remove the hello-minikube cluster.

    $ kubectl delete services hello-minikube

    $ kubectl delete deployment hello-minikube

Step 3: Download the Sawtooth Configuration File

Download the Kubernetes configuration file for a single-node environment: sawtooth-kubernetes-default.yaml.

This file defines the process for constructing a one-node Sawtooth environment with following containers:

    A single validator using Devmode consensus
    A REST API connected to the validator
    The Settings transaction processor (sawtooth-settings)
    The IntegerKey transaction processor (intkey-tp-python)
    The XO transaction processor (xo-tp-python)
    A shell container for running Sawtooth commands (a command-line client)

The configuration file also specifies the container images to download (from DockerHub) and the network settings needed for the containers to communicate correctly.
Step 4: Start the Sawtooth Cluster

    Note

    The Kubernetes configuration file handles the Sawtooth startup steps such as generating keys and creating a genesis block. To learn about the full Sawtooth startup process, see see Using Docker for a Single Sawtooth Node

Use these steps to start Sawtooth:

    Change your working directory to the same directory where you saved the configuration file.

    Make sure that Minikube is running.

    $ minikube status
    minikube: Running
    cluster: Running
    kubectl: Correctly Configured: pointing to minikube-vm at 192.168.99.100

    If necessary, start it with minikube start.

    Start Sawtooth in a local Kubernetes cluster.

    $ kubectl apply -f sawtooth-kubernetes-default.yaml

    (Optional) Start the Minikube dashboard.

    $ minikube dashboard

    This command opens the dashboard in your default browser. The overview page shows the Sawtooth deployment (sawtooth-0) and pod sawtooth-0-{POD-ID}.

Step 5: Connect to the Kubernetes Shell Container

Connect to the shell container.

$ kubectl exec -it $(kubectl get pods | awk '/sawtooth-0/{print $1}') --container sawtooth-shell -- bash

    Note

    In the rest of this procedure, the prompt root@sawtooth-0# marks the commands that should be run in a Sawtooth container. (The actual prompt is similar to root@sawtooth-0-5ff6d9d578-5w45k:/#.)

Step 6: Confirm Connectivity to the REST API (for Kubernetes)

To verify that you can reach the REST API, run this curl command from the shell container:

root@sawtooth-0# curl http://localhost:8008/blocks

If the validator and REST API are running and reachable, the output for each command should be similar to this example:

{
  "data": [
    {
      "batches": [],
      "header": {
        "batch_ids": [],
        "block_num": 0,
        "mconsensus": "R2VuZXNpcw==",
        "previous_block_id": "0000000000000000",
        "signer_public_key": "03061436bef428626d11c17782f9e9bd8bea55ce767eb7349f633d4bfea4dd4ae9",
        "state_root_hash": "708ca7fbb701799bb387f2e50deaca402e8502abe229f705693d2d4f350e1ad6"
      },
      "header_signature": "119f076815af8b2c024b59998e2fab29b6ae6edf3e28b19de91302bd13662e6e43784263626b72b1c1ac120a491142ca25393d55ac7b9f3c3bf15d1fdeefeb3b"
    }
  ],
  "head": "119f076815af8b2c024b59998e2fab29b6ae6edf3e28b19de91302bd13662e6e43784263626b72b1c1ac120a491142ca25393d55ac7b9f3c3bf15d1fdeefeb3b",
  "link": "http://localhost:8008/blocks?head=119f076815af8b2c024b59998e2fab29b6ae6edf3e28b19de91302bd13662e6e43784263626b72b1c1ac120a491142ca25393d55ac7b9f3c3bf15d1fdeefeb3b",
  "paging": {
    "start_index": 0,
    "total_count": 1
  }
}

If the validator process or the validator container is not running, the curl command will time out or return nothing.
Step 7: Test Basic Sawtooth Functionality

Run these commands from the shell container.

    Display the list of blocks on the Sawtooth blockchain.

    root@sawtooth-0# sawtooth block list

    Because this is a new blockchain, there is only one block. Block 0 is the genesis block. The output is similar to this example:

    NUM  BLOCK_ID                                                                                                                          BATS  TXNS  SIGNER
    0    20d7b6657721758d1ad1a3392daadd57473d84e1e1c8c58c14ec862ff7fbf44a3bef4d82c40052dd8fc2808191f830447df59fe074aea02a000ff64bc458e256  1     1     025f80...

    Copy the block ID from the previous output, then use the following command to display more information about the block.

    root@sawtooth-0# sawtooth block show {BLOCK-ID}

    The output of this command is quite long, because it includes all data stored under that block.

    batches:
    - header:
        signer_public_key: 03f257dee6f021b579cb59d34f2489603892d44bb2e181eaa444e1bb4f4b4b812d
        transaction_ids:
        - 3f6c2f60a66317f09d052757dba605d0c1c56caa38cdfdefbd7f4511a830a1fc22d8e13ff86201ac309344605b5df77a85e59799c16c3ba9e3cba950b709be04
      header_signature: 6e5446e99bae1fe2d7d4a7561880bd069cc404e099dd4380a7f491dd0588584b0b6b558d636eb42720d6c839c6755182d3004b905429088413df00f82ec0fd1e
       ...

At this point, your environment is ready for experimenting with Sawtooth. The rest of this section introduces you to Sawtooth functionality.

    To use Sawtooth client commands to create and submit transactions, view block information, and check state data, see Use Sawtooth Commands as a Client.
    To check the Sawtooth components, see Verify the Sawtooth Components.
    For information on the Sawtooth logs, see Examine Sawtooth Logs
    To stop the Sawtooth environment, see Stop the Sawtooth Kubernetes Cluster.

    Important

    Any work done in this environment will be lost once you stop Minikube and delete the Sawtooth cluster. In order to use this environment for application development, you would need to take additional steps, such as defining volume storage. See the Kubernetes documentation for more information.

Step 8: Use Sawtooth Commands as a Client

Sawtooth includes commands that act as a client interface for an application. This step describes how to use the intkey and sawtooth commands to create and submit transactions, display blockchain and block data, and examine global state data.

    Note

    Use the --help option with any Sawtooth command to display the available options and subcommands.

To run the commands in this step, connect to the shell container as described in an earlier step.
Creating and Submitting Transactions with intkey

The intkey command creates and submits IntegerKey transactions for testing purposes.

    Use intkey create_batch to prepare batches of transactions that set a few keys to random values, then randomly increment and decrement those values. These batches are saved locally in the file batches.intkey.

    root@sawtooth-0# intkey create_batch --count 10 --key-count 5
    Writing to batches.intkey...

    Use intkey load to submit the batches to the validator, which commits these batches of transactions as new blocks on the blockchain.

    root@sawtooth-0# intkey load -f batches.intkey
    batches: 11 batch/sec: 141.7800162868952

    Display the list of blocks to verify that the new blocks appear on the blockchain.

    root@sawtooth-0# sawtooth block list
    NUM  BLOCK_ID                                                                                                                          BATS  TXNS  SIGNER
    8    b46c58121d7bf04cf8489a8b937f1478e8699edd0cf023e2cac9b44827caadd441b8c013a4f6e976d799bb59ad602cfb2ea7a765d7abeb954f9013ded464e94c  1     8     025f80...
    7    a0d0e594672c5ae45ff5dfaa9c2e26d148e80190dfe88bc9ac915ed6a9d7b33c27e24d1c891e6b24dcaf59e0e6a6128aab956010b100daf81e9307b66b04d519  1     2     025f80...
    6    0a7739e9d778d65c0fa5ba21e18a8d375072907cec2ec3cbdd8dbcd20f81f2c42d30a4a65b2a63a7aa69d398677542fbf05efbd4a9b7f4aac1fb955b7913d7aa  1     8     025f80...
    5    71efa1c3297e95b7ffb7014ab425e87ff8240a51fb30faf280038882c9bfb3a060fe3ecee12bb9b064195f13ace582c0ab0a3b25808bf87081e33987d8313472  1     3     025f80...
    4    11f177a274d893c22d9bca763a88fdbf020922c68f2231ce0ca0aaa4d80559e52fa67fa059e23ceb0d006acf0b4f2bf315b77ced24959f4a556ac59bd9312356  2     3     025f80...
    3    e3b7692bb070c3d51bf3d975e6cf974d763f893232d305d36bcdbbc2b2859ad425bb0f5aaf068114d05056133a6c8ca84cfdcda6ce7a888a6486090f1f188242  2     5     025f80...
    2    06506f0599ad59b92c13bc2a96ca0c4ca59cdc8c8065df1dc27349c88566293f498c0e3dfe3f06be9b5e889beec0369dd9b94decc309aceb6f57e238e9037e04  1     3     025f80...
    1    327aede38ab395bbdba711911414a9a68166b5378af4bdc15206089a2adf0cb62448f9fc4d749f0c8677849f7fe19c734f05f86687201666e8899437f903102d  2     8     025f80...
    0    20d7b6657721758d1ad1a3392daadd57473d84e1e1c8c58c14ec862ff7fbf44a3bef4d82c40052dd8fc2808191f830447df59fe074aea02a000ff64bc458e256  1     1     025f80...

Submitting Transactions with sawtooth batch submit

In the example above, the intkey create_batch command created the file batches.intkey. Rather than using intkey load to submit these transactions, you could use sawtooth batch submit to submit them.

    As before, create a batch of transactions:

    root@sawtooth-0# intkey create_batch --count 6 --key-count 3
    Writing to batches.intkey...

    Submit the batch file with sawtooth batch submit:

    root@sawtooth-0# sawtooth batch submit -f batches.intkey
    batches: 7,  batch/sec: 216.80369536716367

Viewing Blockchain and Block Data with sawtooth block

The sawtooth block command displays information about the blocks stored on the blockchain.

    Use sawtooth block list again to display the list of blocks stored in state.

        root@sawtooth-0# sawtooth block list

        The output shows the block number and block ID, as in this example:

        NUM  BLOCK_ID                                                                                                                          BATS  TXNS  SIGNER
        8    b46c58121d7bf04cf8489a8b937f1478e8699edd0cf023e2cac9b44827caadd441b8c013a4f6e976d799bb59ad602cfb2ea7a765d7abeb954f9013ded464e94c  1     8     025f80...
        7    a0d0e594672c5ae45ff5dfaa9c2e26d148e80190dfe88bc9ac915ed6a9d7b33c27e24d1c891e6b24dcaf59e0e6a6128aab956010b100daf81e9307b66b04d519  1     2     025f80...
        6    0a7739e9d778d65c0fa5ba21e18a8d375072907cec2ec3cbdd8dbcd20f81f2c42d30a4a65b2a63a7aa69d398677542fbf05efbd4a9b7f4aac1fb955b7913d7aa  1     8     025f80...
        5    71efa1c3297e95b7ffb7014ab425e87ff8240a51fb30faf280038882c9bfb3a060fe3ecee12bb9b064195f13ace582c0ab0a3b25808bf87081e33987d8313472  1     3     025f80...
        4    11f177a274d893c22d9bca763a88fdbf020922c68f2231ce0ca0aaa4d80559e52fa67fa059e23ceb0d006acf0b4f2bf315b77ced24959f4a556ac59bd9312356  2     3     025f80...
        3    e3b7692bb070c3d51bf3d975e6cf974d763f893232d305d36bcdbbc2b2859ad425bb0f5aaf068114d05056133a6c8ca84cfdcda6ce7a888a6486090f1f188242  2     5     025f80...
        2    06506f0599ad59b92c13bc2a96ca0c4ca59cdc8c8065df1dc27349c88566293f498c0e3dfe3f06be9b5e889beec0369dd9b94decc309aceb6f57e238e9037e04  1     3     025f80...
        1    327aede38ab395bbdba711911414a9a68166b5378af4bdc15206089a2adf0cb62448f9fc4d749f0c8677849f7fe19c734f05f86687201666e8899437f903102d  2     8     025f80...
        0    20d7b6657721758d1ad1a3392daadd57473d84e1e1c8c58c14ec862ff7fbf44a3bef4d82c40052dd8fc2808191f830447df59fe074aea02a000ff64bc458e256  1     1     025f80...

    From the output generated by sawtooth block list, copy the ID of a block you want to view, then paste it in place of {BLOCK_ID} in the following command. In this example, block 1 shows the first intkey block (from the previous step) with 5 transactions

    root@sawtooth-0# sawtooth block show 327aede38ab395bbdba711911414a9a68166b5378af4bdc15206089a2adf0cb62448f9fc4d749f0c8677849f7fe19c734f05f86687201666e8899437f903102d

    The output of this command can be quite long, because it includes all data stored under that block. This is a truncated example:

    batches:
    - header:
        signer_public_key: 0383b79f4ea95d8fcb409233703fb4c0606b403f485541b62e582600a35742642a
        transaction_ids:
        - b1626c1a9ab389556208b05bc3973e82177a152b19a061be53e351884cb506a241074f36eae62de2bfd85873bc916f803b1f3c53840f2ab6f03b21513dc1ac7a
        - 2e481fd71c30d3e39399f90654ccf9c0b64e6e67f54576a7e9004fe81bf3145023e9012ec89df898e1143126b3497c5e4acf2e21ec1d27938610c0bfc73ea8c8
        - 5b8a2ff9fafa2184640b3e917b993abc5dfd07b751145c328183670c499fdc9827711a52e927a233d62d4d22e55ed1b53b9cae4caa66d0f237f0968bbe676475
        - bea74bc920297a16294b915df1fcf267f3a6e701e769539d2e33f41aee01521e6301b734ef01edc74354ab77981eb1a4527da1f64d17d446b2b33d2d58e97051
        - 020732f598e9ff3bc0b41614ab043f3d425b7a655561da313965f0dab667c48940060a3e86d2feb7c7681efa24cdf3b1c1093ca19ee5eb6d87f555e50dde9194
      header_signature: 0362c4f928d4e39b1d13746a7023b1d8c2b5e798fc968dd36b2ea13e51f7a8d21d2865f71a4a6f00c11348699047d774eb4ebb3708c914558e81db0e04c4ff03
      trace: false
      transactions:
      - header:
          batcher_public_key: 0383b79f4ea95d8fcb409233703fb4c0606b403f485541b62e582600a35742642a
          dependencies: []
          family_name: intkey
          family_version: '1.0'
           .
           .
           .

Viewing State Data with sawtooth state

The sawtooth state command lets you display state data. Sawtooth stores state data in a Merkle-Radix tree (for more information, see Global State.

    Use sawtooth state list to display addresses in state with their size and associated data. The default output format truncates each line; use --format with csv, json, or yaml to display the entire line.

    root@sawtooth-0# sawtooth state list --format csv

    The output will be similar to this truncated example:

    ADDRESS,SIZE,DATA
    000000a87cb5eafdcca6a8cde0fb0dec1400c5ab274474a6aa82c12840f169a04216b7,110,b'\nl\n&sawtooth.settings.vote.authorized_keys\x12B03f257dee6f021b579cb59d34f2489603892d44bb2e181eaa444e1bb4f4b4b812d'
    1cf12601b514e0270939cf20cacf61ce341f68f383cd1839f0b0cbb363792ef26fb711,11,b'\xa1fxAdnqS\x19N\xaf'
    1cf12604ff7d37163341d6002ff1d8fb07611bbb2bdac0d7ce181671bc728cf2c0d849,11,b'\xa1fryxDcP\x19%\xd1'
    1cf1267f20354576067b5cd3cc53c30657a159d23a9a0bc02ee6693dae132004f73e90,13,b'\xa1fFJcKOs\x1a\x00\x01B\xbb'
    1cf126a2ef5597d9095b6dd7b65d1fa0320ec8624c8c9ad1c2195f872ab83faee0ab90,13,b'\xa1fRxmfbf\x1a\x00\x01S\x86'
    1cf126aa8fe078d07e4e1aad84d9b0c1ca192cfe4ed72cc93f2354bdecd7295c110f79,11,b'\xa1fOqcdTQ\x19\xab-'
    1cf126ab6c1df0a237b170c783b4ec6c010c379159d942f67d812edac9969496a9ff88,11,b'\xa1fvHgUhX\x19\x91\xaf'
    1cf126b3c1240bebf2a1d4ca3b3f6b83ce1ebee9764ac36f1076e6c7202bf73f0f5117,11,b'\xa1fjKLuTS\x19\xe6_'
    1cf126d3d7b97e3e3c6bc2dd3b750c17f9c311aee81aee90cd2c5bf53ed4e5ec6d73b3,11,b'\xa1fVVpUdq\x19\xd2\xc5'
    1cf126d4e2b632193b17b17ae0c9c1331f8e37915fe547568fab6322b516a57e108d88,11,b'\xa1fRoYclW\x19\xc6\x1e'
    1cf126d7a0dbe68f8ac9d207843054b24e211c9821b851cb748f1f7f9c528a37fe0e4a,13,b'\xa1fYhuGwm\x1a\x00\x01\x18\xa9'
    1cf126dbe0c0b5dc8aeaa176d4cd98046aef4d12a6921e357344a56c8520df9d04b61f,13,b'\xa1fDWtxbO\x1a\x00\x01p\n'
    1cf126ef1db314433d0a887ec7f2d105600898b486e72b9eee02160dd93c7572c450b8,11,b'\xa1fcOHrSu\x19\xd7\x92'
    1cf126f4fef1dcf6fa07442d004120f48129996b81480209252871dd51b7d851c4b216,13,b'\xa1fXqhSBG\x1a\x00\x01 \xec'
    (data for head block: "100fae26d4cd15808dc59c1221a289ccefc4ac5643bd80b2d6c7e1c55e6c349b0a1082cd5e787c32233c5048279bf8aea5c9fe2f9e495aed2d7363d1918b3f90")

    Use sawtooth state show to view state data at a specific address (a node in the Merkle-Radix database). Copy the address from the output of sawtooth state list, then paste it in place of {STATE_ADDRESS} in the following command:

    root@sawtooth-0# sawtooth state show {STATE_ADDRESS}

    The output shows the bytes stored at that address and the block ID of the "chain head" that the current state is tied to, as in this example:

    DATA: "b'\xa1fcCTdcH\x192B'"
    HEAD: "0c4364c6d5181282a1c7653038ec9515cb0530c6bfcb46f16e79b77cb524491676638339e8ff8e3cc57155c6d920e6a4d1f53947a31dc02908bcf68a91315ad5"

    You can use sawtooth block show (as described above) with block number of the chain head to view more information about that block.

Step 9: Verify the Sawtooth Components

To check whether a Sawtooth component is running, connect to the component's container and run the ps command.

    Use the kubectl exec command from your computer to connect to a Sawtooth container. On the Kubernetes dashboard, the Pods page displays the container names.

    For example, connect to the validator container with the following command:

    $ kubectl exec -it $(kubectl get pods | awk '/sawtooth-0/{print $1}') --container sawtooth-validator -- bash

    After connecting to the container, you can use ps to verify that the Sawtooth component is running.

    root@sawtooth-0# ps -A fw

    In the sawtooth-validator container, the output resembles the following example:

    PID TTY      STAT   TIME COMMAND
     77 pts/0    Ss     0:00 bash
     96 pts/0    R+     0:00  \_ ps -A fw
      1 ?        Ss     0:00 bash -c sawadm keygen && if [ ! -e config-genesis.batch ]; then sawset genesis -k /etc/sawtooth/keys/vali
     27 ?        Sl     0:17 /usr/bin/python3 /usr/bin/sawtooth-validator -vv --endpoint tcp://10.96.15.213:8800 --bind component:tcp:

Step 10: Examine Sawtooth Logs

The Sawtooth log files are available on the Kubernetes dashboard.

        From the dashboard's overview page, click on the Sawtooth pod name.

        On the Sawtooth pod page, click on the LOGS button.

        On Logs page, select the Sawtooth component. For example, to view the validator log messages, select sawtooth-validator.

        The following extract shows the genesis block being processed and committed to the blockchain.

            writing file: /etc/sawtooth/keys/validator.priv
            writing file: /etc/sawtooth/keys/validator.pub
            Generated config-genesis.batch
             .
             .
             .
            [2018-08-16 19:12:51.106 INFO     genesis] Producing genesis block from /var/lib/sawtooth/genesis.batch
            [2018-08-16 19:12:51.106 DEBUG    genesis] Adding 1 batches
            [2018-08-16 19:12:51.107 DEBUG    executor] no transaction processors registered for processor type sawtooth_settings: 1.0
            [2018-08-16 19:12:51.108 INFO     executor] Waiting for transaction processor (sawtooth_settings, 1.0)
            [2018-08-16 19:12:51.120 INFO     processor_handlers] registered transaction processor: connection_id=57ec10822a6345a908533ea00c44dbdacbe029e6073b3b709bd144e7275aae6f5f1a01de529664861c7598eb4e87dcd229a474fb868958cbee72b0b307311a5e, family=xo, version=1.0, namespaces=['5b7349']
            [2018-08-16 19:12:51.191 INFO     processor_handlers] registered transaction processor: connection_id=bdbf6d96c1b456a311e7a12842765d8061af1bbefb47f9923379ccdf9f07076da1b6a65028ebd31fe5f84cdb3adfdfa1cc9d98b1b46265b49e47250e04e08910, family=intkey, version=1.0, namespaces=['1cf126']
            [2018-08-16 19:12:51.198 INFO     processor_handlers] registered transaction processor: connection_id=084ecc34848d7293821a3f2c58adc4f703572a368783afd901004bfd982e82ce5fe6e1f6e6e08de9fe6fc25c98ae20e55fa493f4f510824a2bb4a5fe00210c81, family=sawtooth_settings, version=1.0, namespaces=['000000']
            [2018-08-16 19:12:51.235 DEBUG    genesis] Produced state hash 0e682c25c3390a718ec560bb45d5180924f255210d9d4521eaac019800603731 for genesis block.
            [2018-08-16 19:12:51.238 INFO     genesis] Genesis block created: 20d7b6657721758d1ad1a3392daadd57473d84e1e1c8c58c14ec862ff7fbf44a3bef4d82c40052dd8fc2808191f830447df59fe074aea02a000ff64bc458e256 (block_num:0, state:0e682c25c3390a718ec560bb45d5180924f255210d9d4521eaac019800603731, previous_block_id:0000000000000000)
            [2018-08-16 19:12:51.238 DEBUG    chain_id_manager] writing block chain id
            [2018-08-16 19:12:51.239 DEBUG    genesis] Deleting genesis data.
            [2018-08-16 19:12:51.239 DEBUG    selector_events] Using selector: ZMQSelector
            [2018-08-16 19:12:51.240 INFO     interconnect] Listening on tcp://eth0:8800
            [2018-08-16 19:12:51.241 DEBUG    dispatch] Added send_message function for connection ServerThread
            [2018-08-16 19:12:51.241 DEBUG    dispatch] Added send_last_message function for connection ServerThread
            [2018-08-16 19:12:51.243 DEBUG    gossip] Number of peers (0) below minimum peer threshold (3). Doing topology search.
            [2018-08-16 19:12:51.244 INFO     chain] Chain controller initialized with chain head: 20d7b6657721758d1ad1a3392daadd57473d84e1e1c8c58c14ec862ff7fbf44a3bef4d82c40052dd8fc2808191f830447df59fe074aea02a000ff64bc458e256 (block_num:0, state:0e682c25c3390a718ec560bb45d5180924f255210d9d4521eaac019800603731, previous_block_id:0000000000000000)
            [2018-08-16 19:12:51.244 INFO     publisher] Now building on top of block: 20d7b6657721758d1ad1a3392daadd57473d84e1e1c8c58c14ec862ff7fbf44a3bef4d82c40052dd8fc2808191f830447df59fe074aea02a000ff64bc458e256 (block_num:0, state:0e682c25c3390a718ec560bb45d5180924f255210d9d4521eaac019800603731, previous_block_id:0000000000000000)

You can also access a component's log messages by connecting to the container and examining the local log files. In each container, the Sawtooth log files for that component are stored in the directory /var/log/sawtooth. Each component (validator, REST API, and transaction processors) has both a debug log and an error log.

For example, you can connect to the validator container and display the contents of /var/log/sawtooth:

$ kubectl exec -it $(kubectl get pods | awk '/sawtooth-0/{print $1}') --container sawtooth-validator -- bash
root@sawtooth-0# ls -1 /var/log/sawtooth
validator-debug.log
validator-error.log

    Note

    By convention, the log files for the transaction processors use a random string to make the log file names unique. For example:

    $ kubectl exec -it $(kubectl get pods | awk '/sawtooth-0/{print $1}') --container sawtooth-intkey-> tp-python -- bash

    root@sawtooth-0# ls -1 /var/log/sawtooth
    intkey-ae98c3726f9743c4-debug.log
    intkey-ae98c3726f9743c4-error.log

For more information on log files, see Log Configuration.
Step 11: Stop the Sawtooth Kubernetes Cluster

Use the following commands to stop and reset the Sawtooth environment.

    Important

    Any work done in this environment will be lost once you delete the Sawtooth cluster. To keep your work, you would need to take additional steps, such as defining volume storage. See the Kubernetes documentation for more information.

    Log out of all Sawtooth containers.

    Stop Sawtooth and delete the pod. Run the following command from the same directory where you saved the configuration file.

    $ kubectl delete -f sawtooth-kubernetes-default.yaml
    deployment.extensions "sawtooth-0" deleted
    service "sawtooth-0" deleted

    Stop the Minikube cluster.

    $ minikube stop
    Stopping local Kubernetes cluster...
    Machine stopped.

    Delete the Minikube cluster, VM, and all associated files.

    $ minikube delete
    Deleting local Kubernetes cluster...
    Machine deleted.

