# Auditing Notes

- [Topics](#topics)
- [AMM](#amm)
  - [Uniswap](#uniswap)
  - [Balancer](#balancer)
- [Chainlink](#chainlink)
  - [Price Feeds](#price-feeds)
- [Beacon Chain](#beacon-chain)
- [EVM](#evm)
  - [General](#general)
  - [Re-orgs](#re-orgs)
  - [Specific](#specific)
- [L2s](#l2s)
- [Vyper](#vyper)


## Topics

- [Foundry Cheatsheet](/Foundry.md)
- [OP Stack](/OP%20Stack.md)
- [Blast L2](/Blast.md)

## AMM

### Uniswap

- [Uniswap V3 Math Part 1](https://blog.uniswap.org/uniswap-v3-math-primer)
- [Uniswap V3 Math Part 2](https://blog.uniswap.org/uniswap-v3-math-primer-2)
- [Uniswap V3 TWAP Manipulation](https://chaoslabs.xyz/posts/chaos-labs-uniswap-v3-twap-market-risk#783c9150ebcf)

### Balancer

- [Balancer Weighted Pool Math](https://medium.com/balancer-simulations/understanding-balancer-pools-c2b877dcc082)

## Chainlink

### Price Feeds

- [Ackee](https://ackeeblockchain.com/blog/chainlink-data-feeds/)
- [Dacian](https://medium.com/cyfrin/chainlink-oracle-defi-attacks-93b6cb6541bf)
- [0xMacro](https://0xmacro.com/blog/how-to-consume-chainlink-price-feeds-safely/)

## Beacon Chain

General

- [ETH 2.0 Beacon Chain Explained](https://consensys.io/blog/the-ethereum-2-0-beacon-chain-explained)
- [Consensus Spec](https://github.com/ethereum/consensus-specs)
- [Annotated Consensus Spec](https://github.com/ethereum/annotated-spec)

ETH Staking

- [eth2book](https://eth2book.info/capella/part2/)
- [EIP 4895 - Withdrawals](https://eips.ethereum.org/EIPS/eip-4895)
- [EIP 4788 - Beacon block root in EVM](https://eips.ethereum.org/EIPS/eip-4788)
- [Beacon Chain Proofs](https://github.com/Layr-Labs/eigenlayer-contracts/blob/dev/docs/core/proofs/BeaconChainProofs.md)

Re-orgs

- [Investigating why reorgs happen in POS Ethereum](https://www.samlewis.me/2022/03/beacon-chain-reorgs/)
- [Statistical Analysis of Reorgs](https://ethresear.ch/t/the-second-slot-itch-statistical-analysis-of-reorgs/16333)
- [Etherscan - Reorged blocks](https://etherscan.io/blocks_forked)

Indexers

- [beaconscan](https://beaconscan.com/)
- [beaconcha.in](https://beaconcha.in/)

## Account Abstraction

- [EIP 4337 - Account Abstraction](https://eips.ethereum.org/EIPS/eip-4337)
- [EIP 7579 - Modules](https://eips.ethereum.org/EIPS/eip-7579)
- [EIP 7484 - Registry](https://eips.ethereum.org/EIPS/eip-7484)
- [Infinitism Repository](https://github.com/eth-infinitism/account-abstraction)
- [Checklist by aviggiano](https://github.com/aviggiano/security/blob/main/audit-checklists/ERC-4337.md)

## EVM

### General

- [evm.codes](https://www.evm.codes) and [evm.storage](https://evm.storage/)
- [EVM Handbook](https://noxx3xxon.notion.site/The-EVM-Handbook-bb38e175cc404111a391907c4975426d)
- [Understanding the EVM - Part I](https://leftasexercise.com/2021/09/12/understanding-the-ethereum-virtual-machine-part-i/)
- [Understanding the EVM - Part II](https://leftasexercise.com/2021/09/15/understanding-the-ethereum-virtual-machine-part-ii/)
- [Understanding the EVM - Part III](https://leftasexercise.com/2021/09/19/q-understanding-the-ethereum-virtual-machine-part-iii/)

### Specific

- [Gas costs after Berlin](https://hackmd.io/@fvictorio/gas-costs-after-berlin)

## L2s

- [EVM Diff](https://www.evmdiff.com/)
- [rollup.codes](https://www.rollup.codes/)
- [Cross-chain](https://jumpcrypto.com/writing/cross-chain/)

## Vyper

- [Vyper compiler overview](https://jtriley.substack.com/p/the-vyper-compiler)
- [Finding vulnerable vyper contracts](https://banteg.xyz/posts/vyper-opcodes/)
- [Vyper compiler audit by Consensys](https://consensys.io/diligence/audits/2019/10/vyper/)

