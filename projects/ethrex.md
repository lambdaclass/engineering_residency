# Ethereum Project: Use Ethrex

This project is a little more real-world than the previous ones. 
To cement the concepts you read about in the Blockchain and Ethereum sections, it involves running and using the [ethrex](https://github.com/lambdaclass/ethrex) Ethereum execution client. 

Download the repo, build it, run tests, read the [documentation](https://docs.ethrex.xyz/).

Your end goal is to: 
- run Ethrex as a [vanilla L2 rollup](https://docs.ethrex.xyz/l2/deployment/vanilla.html) (with the `--features l2,l2-sql` feature set) with contracts on the [Hoodi](https://cloud.google.com/application/web3/faucet/ethereum/hoodi) test network,
- run the prover client in [exec mode](https://docs.ethrex.xyz/CLI.html?highlight=exec#ethrex-l2-prover) (see the documentation for `ethrex l2 prover --proof-coordinators tcp://localhost:3900`)
- create two accounts and fund them through the Hoodi faucet, 
- and finally bridge between the L1 and L2 by [depositing](https://docs.ethrex.xyz/l2/interacting/deposit.html) on the first L2 account, transfer to the second L2 account, and then [withdrawing](https://docs.ethrex.xyz/l2/interacting/withdraw.html) from this second account back to the L1. 
