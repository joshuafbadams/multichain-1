# Multichain

[![License Apache 2][badge-license]](LICENSE)
[![GitHub version](https://badge.fury.io/gh/nlamirault%2Fmultichain.svg)](https://badge.fury.io/gh/nlamirault%2Fmert)

Experiments on [Multichain][]

## Description

Setup your blockchain using [Multichain][] with [Vagrant][].

* Create the virtual machine and login:

        $ vagrant up
        $ vagrant ssh

* On the VM, create a blockchain

        $ multichain-util create lamchain
        MultiChain utilities build 1.0 alpha 16 protocol 10003

        Blockchain parameter set was successfully generated.
        You can edit it in /home/vagrant/.multichain/lamchain/params.dat before running multichaind for the first time.

        To generate blockchain please run "multichaind lamchain".

* On the VM, initialize the blockchain:

        $ multichaind lamchain -daemon
        MultiChain Core Daemon build 1.0 alpha 16 protocol 10003
        Multichain server starting
        vagrant@Multichain:~$ Looking for genesis block...
        Genesis block found
        New users can connect to this node using
        multichaind lamchain@10.0.2.15:4781
        Node started

* On the host :

        $ multichaind lamchain@10.4.4.4:4781

        MultiChain Core Daemon build 1.0 alpha 16 protocol 10003

        Retrieving blockchain parameters from the seed node 10.4.4.4:4781 ...
        Blockchain successfully initialized.

        Please ask blockchain admin or user having activate permission to let you connect and/or transact:
        multichain-cli lamchain grant 1F6km6qxta5p5gqtFF3XMCspKT1cCsDDeCADuS connect
        multichain-cli lamchain grant 1F6km6qxta5p5gqtFF3XMCspKT1cCsDDeCADuS connect,send,receive

* On the VM, add connection permissions :

        $ multichain-cli lamchain grant 1F6km6qxta5p5gqtFF3XMCspKT1cCsDDeCADuS connect
        {"method":"grant","params":["1F6km6qxta5p5gqtFF3XMCspKT1cCsDDeCADuS","connect"],"id":1,"chain_name":"lamchain"}

        fb3d017973988b6ebbbb233ab39f9d2b27285b9277862ba9d12493a172b8bcd8

* On the host, try reconnecting agin :

        $ multichaind lamchain@10.4.4.4:4781 -daemon

        MultiChain Core Daemon build 1.0 alpha 16 protocol 10003

        Retrieving blockchain parameters from the seed node 10.4.4.4:4781 ...
        New users can connect to this node using
        multichaind lamchain@10.33.1.116:4781

        Node started

* Enter the interactive mode:

        $ multichain-cli lamchain
        lamchain: getinfo
        {
            "version" : "1.0 alpha 16",
            "protocolversion" : 10003,
            "chainname" : "lamchain",
            "description" : "MultiChain lamchain",
            "protocol" : "multichain",
            "port" : 4781,
            "setupblocks" : 60,
            "nodeaddress" : "lamchain@192.1.2.46:4781",
            "burnaddress" : "1XXXXXXWsXXXXXXXRXXXXXXXZxXXXXXXat6JD4",
            "walletversion" : 60000,
            "balance" : 0.00000000,
            "blocks" : 55,
            "timeoffset" : 0,
            "connections" : 2,
            "proxy" : "",
            "difficulty" : 0.00001526,
            "testnet" : false,
            "keypoololdest" : 1457004398,
            "keypoolsize" : 2,
            "paytxfee" : 0.00000000,
            "relayfee" : 0.00000000,
            "errors" : ""
        }



## License

See [LICENSE](LICENSE) for the complete license.


## Changelog

A [changelog](ChangeLog.md) is available


## Contact

Nicolas Lamirault <nicolas.lamirault@gmail.com>


[badge-license]: https://img.shields.io/badge/license-Apache2-green.svg?style=flat

Vagrant: https://www.vagrantup.com/
Multichain: http://www.multichain.com/
