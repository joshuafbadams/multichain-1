# Multichain

[![License Apache 2][badge-license]](LICENSE)
[![GitHub version](https://badge.fury.io/gh/nlamirault%2Fmultichain.svg)](https://badge.fury.io/gh/nlamirault%2Fmert)

## Description

Setup your blockchain using [Multichain][] with [Vagrant][] and [Ansible][]

* Create the blockchain nodes

        $ vagrant up

* Enter the interactive mode:

        $ multichain-cli minechain
        minechain: getinfo
        {
            "version" : "1.0 alpha 16",
            "protocolversion" : 10003,
            "chainname" : "lamchain",
            "description" : "MultiChain minechain",
            "protocol" : "multichain",
            "port" : 4781,
            "setupblocks" : 60,
            "nodeaddress" : "minechain@192.1.2.46:4781",
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


[Vagrant]: https://www.vagrantup.com/
[Ansible]: https://www.ansible.com/
[Multichain]: http://www.multichain.com/
