# How to understand Blast 101

## OP Stack

### How OP Stack works

- [OP Stack Documentation](https://docs.optimism.io/stack/protocol/overview)
- [Optimism Bedrock Specs](https://github.com/ethereum-optimism/optimism/blob/master/specs/README.md), relevant parts are:
  - [Introduction](https://github.com/ethereum-optimism/optimism/blob/master/specs/introduction.md)
  - [Overview](https://github.com/ethereum-optimism/optimism/blob/master/specs/overview.md)
  - [Deposits](https://github.com/ethereum-optimism/optimism/blob/master/specs/deposits.md)
  - [Withdrawals](https://github.com/ethereum-optimism/optimism/blob/master/specs/withdrawals.md)
  - [Messengers](https://github.com/ethereum-optimism/optimism/blob/master/specs/messengers.md)
  - [Bridges](https://github.com/ethereum-optimism/optimism/blob/master/specs/bridges.md)
  - [Predeploys](https://github.com/ethereum-optimism/optimism/blob/master/specs/predeploys.md)
- [Diff of `op-geth`](https://op-geth.optimism.io/)

### Related Past Audits

- [Optimism Contest 01/23](https://github.com/sherlock-audit/2023-01-optimism-judging/issues?q=is%3Aopen+is%3Aissue+label%3AHigh%2CMedium)
- [Optimism Contest 03/23](https://github.com/sherlock-audit/2023-03-optimism-judging/issues?q=is%3Aopen+is%3Aissue+label%3AHigh%2CMedium)
- [BASE Contest 05/23](https://github.com/code-423n4/2023-05-base-findings/issues)

## Geth

**Dissecting EVM using go-ethereum Eth client implementation** by [@deliriusz_eth](https://twitter.com/deliriusz_eth)
- [Part 1 - Transaction execution flow](https://medium.com/@deliriusz/dissecting-evm-using-go-ethereum-eth-client-implementation-part-i-transaction-execution-flow-960a1533e994)
- [Part 2 - EVM](https://medium.com/@deliriusz/dissecting-evm-using-go-ethereum-eth-client-implementation-part-ii-evm-ce7653f31c6f)
- [Part 3 - Bytecode interpreter](https://medium.com/@deliriusz/dissecting-evm-using-go-ethereum-eth-client-implementation-part-iii-bytecode-interpreter-8f144004ed7a)

**Fun fact:** If a contract does `selfdestruct(address(this))`, [it doesn't get the ETH back](https://twitter.com/milotruck/status/1748370053094084833) (before EIP-6780 at least). There might be bugs related to `selfdestruct`, [EIP-6780](https://eips.ethereum.org/EIPS/eip-6780) and share calculation on the L2 side. Or maybe not.

## Maker

- [DSR Manager Documentation](https://docs.makerdao.com/smart-contract-modules/proxy-module/dsr-manager-detailed-documentation)
- [Pot Documentation](https://docs.makerdao.com/smart-contract-modules/rates-module/pot-detailed-documentation)
- [Join Documentation](https://docs.makerdao.com/smart-contract-modules/collateral-module/join-detailed-documentation)
- [Peg Stability Module (PSM) Repository](https://github.com/makerdao/dss-psm)

## Lido

- [Lido Contracts Documentation](https://docs.lido.fi/contracts/lido/)
- [WithdrawalQueueERC721.sol](https://docs.lido.fi/contracts/withdrawal-queue-erc721/)
