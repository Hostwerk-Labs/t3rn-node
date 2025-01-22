# Multilanguage Readme

[![en](https://img.shields.io/badge/lang-en-blue.svg)](https://github.com/Hostwerk-Labs/t3rn-node/blob/main/Readme-EN.md)
[![ru](https://img.shields.io/badge/lang-ru-red.svg)](https://github.com/Hostwerk-Labs/t3rn-node/blob/main/Readme.md)

# T3RN Executor Node

Using Ansible and Docker for scalable deployments

We always use open-source containerized versions of executors.

# Guide

## Requirements

- Ansible core >= 2.17.4
- Docker >= 26.1

## Setting up and running the node

1. Deploy the configuration to our target servers

   `ansible-playbook -i inventory --limit "cluster0" t3rn.yml`

   Or for all clusters

   `ansible-playbook -i inventory --limit "cluster0" t3rn.yml`

2. Log into the server and start the node

   `cd /storage/nodes/hostwerk`

   `docker compose up -d`

3. Check the logs of the running server

   `docker compose logs -f --tail=300`

# Operation

## Node Update

Navigate to the node directory and update it:

`cd /storage/nodes/hostwerk`

`docker compose pull`

`docker compose up -d`

## Common Errors

    - {"level":"error","time":1737492475413,"environment":"testnet","sourceNetwork":"blss","address":"0x9c5eE6A43e9823D95518cCBDe598D4C7feae3228","code":"NETWORK_ERROR","error":"could not detect network (event=\"noNetwork\", code=NETWORK_ERROR, version=providers/5.7.2)","msg":"❌ RPC error at getBalance"} - Incorrectly specified RPC network, in our case blss - Blast

    - `👨‍⚖️Your bid was not accepted because it failed our Bid Difficulty measures filter. This helps ensure bids remain fair & saves on your gas.` - current bids and your gas in the config do not match the deal

    - `💔 Order is not profitable. Skip order` - your gas settings and current deals do not fall into a profitable zone

## Common Success logs

    - `🥊 Start processing txs in Transmitter...` - you are trying to process something - chance to complete the transaction and get a token for it

    - `🧡 Processing new profitable Order` - most likely your bid won and you got a transaction to execute

More about nodes and web3 infrastructure in our [Telegram](https://t.me/+irchepr8HtllZWIy)
