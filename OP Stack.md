# OP Stack

## How OP Stack works

- [OP Stack Documentation](https://docs.optimism.io/stack/protocol/overview)
- [Optimism Bedrock Specs](https://github.com/ethereum-optimism/optimism/blob/master/specs/README.md)
- [OP Stack Specs](https://specs.optimism.io/)
- [Diff of `op-geth`](https://op-geth.optimism.io/)

## Related Past Audits

Audits & Contests

- [Past Audits](https://github.com/ethereum-optimism/optimism/tree/develop/docs/security-reviews)
- [Optimism Contest 01/23](https://github.com/sherlock-audit/2023-01-optimism-judging/issues?q=is%3Aopen+is%3Aissue+label%3AHigh%2CMedium)
- [Optimism Contest 03/23](https://github.com/sherlock-audit/2023-03-optimism-judging/issues?q=is%3Aopen+is%3Aissue+label%3AHigh%2CMedium)
- [BASE Contest 05/23](https://github.com/code-423n4/2023-05-base-findings/issues)
- [Blast Contest 02/24](https://cantina.xyz/code/c90131b4-5c7c-4ebc-a1f3-8002d219bfe0/findings)

Bugs

- [Abuse re-entrancy protection to force withdrawal to fail in `CrossDomainMessenger`](https://github.com/code-423n4/2023-05-base-findings/issues/119)
- [TRST M-3: Memory expansion cost not accurate in `baseGas()`](https://github.com/ethereum-optimism/optimism/blob/develop/docs/security-reviews/2023_12_Trust_SuperchainConfigUpgrade.pdf)
- `CrossDomainMessenger` is a proxy, `baseGas()` inaccurate (see gist)

## Geth

- [Geth Documentation](https://geth.ethereum.org/docs)
- **Dissecting EVM using go-ethereum Eth client implementation** by [@deliriusz_eth](https://twitter.com/deliriusz_eth)
  - [Part 1 - Transaction execution flow](https://medium.com/@deliriusz/dissecting-evm-using-go-ethereum-eth-client-implementation-part-i-transaction-execution-flow-960a1533e994)
  - [Part 2 - EVM](https://medium.com/@deliriusz/dissecting-evm-using-go-ethereum-eth-client-implementation-part-ii-evm-ce7653f31c6f)
  - [Part 3 - Bytecode interpreter](https://medium.com/@deliriusz/dissecting-evm-using-go-ethereum-eth-client-implementation-part-iii-bytecode-interpreter-8f144004ed7a)

