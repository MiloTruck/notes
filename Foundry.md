# Foundry Cheatsheet

- [Setup](#setup)
  - [Creating new projects](#creating-new-projects)
  - [Usage in existing projects](#usage-in-existing-projects)
- [Dependencies](#dependencies)
  - [Adding dependencies](#adding-dependencies)
  - [Remappings](#remappings)
- [Testing](#testing)
  - [Fork testing](#fork-testing)
  - [Cheatcodes](#cheatcodes)
    - [Context](#context)
    - [Storage and memory](#storage-and-memory)
    - [Caller](#caller)
    - [Calls](#calls)
    - [Reverts](#reverts)
    - [Snapshots](#snapshots)
  - [Std Libraries](#std-libraries)
    - [Balances](#balances)
    - [Errors](#errors)
    - [Assertions](#assertions)
    - [Addresses and Keys](#addresses-and-keys)
    - [Math](#math)
  - [Fuzzing](#fuzzing)

## Setup

### Creating new projects

Create a new project:
```sh
forge init <project_name>
```

Create a new project using a template:
```sh
forge init --template <template> <project_name>

# Example
forge init --template https://github.com/zobront/paradigm-ctf paradigm_ctf
```

### Usage in existing projects

Initialize Foundry:

```sh
# Create required directories
mkdir out lib

# Add `forge-std` module to `lib`
git submodule add https://github.com/foundry-rs/forge-std lib/forge-std

# Create foundry.toml
touch foundry.toml
```

Specify directories in `foundry.toml`:

```toml
[profile.default]
src = "contracts"
out = "out"
lib = "lib"
```

## Dependencies

### Adding dependencies

Install dependencies in an existing project:
```sh
forge install
```

To add a new dependency:
```sh
forge install <dependency>

# Example
forge install openzeppelin/openzeppelin-contracts
```

To add dependencies to existing git repositories:
```sh
# Do not create a commit
forge install --no-commit <dependency>

# Do not create a git repository
forge install --no-git <dependency>
```

### Remappings

Forge can automatically deduce remappings:
```sh
forge remappings > remappings.txt
```

To customize a remapping, simply add it to `remappings.txt`:
```sh
echo "@openzeppelin/=lib/openzeppelin-contracts/" > remappings.txt
```

## Testing

To run tests:
```sh
forge test
```

Verbosity
- `-vv` shows `console.log` output.
- `-vvv` shows execution traces for failing tests. 
- `-vvvv` shows execution traces for all tests, and setup traces for failing tests.
- `-vvvvv` shows execution and setup traces for all tests.

To run specific tests:
- `--match-test` runs tests matching the specified regex.
- `--match-contract` runs tests in contracts matching the specified regex.
- `--match-path` runs tests in source files matching the specified path.

### Fork testing

To fork a network:
```sh
forge test --fork-url <rpc_url>
```

To identify contracts in a forked environment, pass your Etherscan API key using `--etherscan-api-key`:
```sh
forge test --fork-url <rpc_url> --etherscan-api-key <etherscan_api_key>
```

### Cheatcodes

Refer to [Cheatcodes Reference](https://book.getfoundry.sh/cheatcodes/) for all available cheatcodes.

#### Context

```solidity
// Set block.timestamp
vm.warp(uint256 timestamp)

// Increase block.timestamp by specified seconds
skip(uint256 time)

// Decrease block.timestamp by specified seconds
rewind(uint256 time) 

// Set block.number
vm.roll(uint256 blockNumber)
```

#### Storage and memory

```solidity
// Load a storage slot from an address
vm.load(address account, bytes32 slot) 

// Store a value to an address' storage slot
vm.store(address account, bytes32 slot, bytes32 value)

// Set code at address
vm.etch(address addr, bytes calldata code)
```

#### Caller

```solidity
// Set msg.sender for the next call
vm.prank(address msgSender)

// Set msg.sender for subsequent calls
vm.startPrank(address msgSender)

// Reset msg.sender for subsequent calls
vm.stopPrank()

// Change msg.sender for subsequent calls
changePrank(address msgSender) 

// Set msg.sender and give it ether for the next call
hoax(address who)
hoax(address who, uint256 give)
hoax(address who, address origin)
hoax(address who, address origin, uint256 give)

// Set msg.sender and give it ether for subsequent calls
startHoax(address who)
startHoax(address who, uint256 give)
startHoax(address who, address origin)
startHoax(address who, address origin, uint256 give)
```

#### Calls

```solidity
// Mock calls to an address `where`. If the call data `data` matches, return `retdata`  
vm.mockCall(address where, bytes calldata data, bytes calldata retdata);

// Same as the above, but msg.value also has to match `value`
vm.mockCall(address where, uint256 value, bytes calldata data, bytes calldata retdata);
```

Example usage:
```solidity
function testMockCall() public {
    // Without value
    vm.mockCall(
        address(token),
        abi.encodeWithSelector(token.balanceOf.selector, ALICE),
        abi.encode(10)
    );
    assertEq(token.balanceOf(ALICE), 10);

    // With value
    vm.mockCall(
        address(market),
        10 ether,
        abi.encodeWithSignature("pay(address,uint256)", ALICE, 10 ether),
        abi.encode(true)
    );
    assertTrue(market.pay{value: 10 ether}(ALICE, 10 ether));
}
```

#### Reverts

```solidity
// Expect the next call to revert
vm.expectRevert()

// Expect the next call to revert with `message`
vm.expectRevert(bytes calldata message)

// Expect the next call to revert with `bytes4 data` (used for custom error selectors)
vm.expectRevert(bytes4 data)
```

#### Snapshots

```solidity
// Take a snapshot of the current state
uint256 snapshot = vm.snapshot();

// Restore the state
vm.revertTo(uint256 snapshot);
```

### Std Libraries

Refer to [Forge Std's `Test`](https://book.getfoundry.sh/reference/forge-std/#forge-stds-test) for all functionality.

#### Balances

```solidity
// Set ether balance for an address
deal(address to, uint256 balance)

// Set ERC20 token balance for an address
deal(address token, address to, uint256 balance)

// Set ERC20 token balance for an address and increase totalSupply if `adjust` is true
deal(address token, address to, uint256 balance, bool adjust)

// Give ERC721 token with `id` to an address
dealERC721(address token, address to, uint256 id)

// Set ERC1155 token balance for an address
dealERC1155(address token, address to, uint256 id, uint256 balance)

// Set ERC1155 token balance for an address and adjust totalSupply
dealERC1155(address token, address to, uint256 id, uint256 balance, bool adjust)
```

#### Errors

From [`forge-std/std-errors`](https://book.getfoundry.sh/reference/forge-std/std-errors), used to catch internal Solidity errors:

- `stdError.assertionError` - an `assert` fails.
- `stdError.arithmeticError` - an arithmetic operation fails (e.g. overflow/underflow).
- `stdError.divisionError` - a division fails (e.g. division by zero).
- `stdError.indexOOBError` - accessing an element of an array that is out of bounds.
- `stdError.popError` - popping from an empty array. Does not work for empty arrays in external contracts.
- `stdError.enumConversionError` - converting a number larger than the number of enum variants to an enum.
- `stdError.encodeStorageError` - accessing data in storage that is corrupted using inline assembly.
- `stdError.memOverflowError` - allocating a dynamic memory array with more than 2^64-1 items.
- `stdError.zeroVarError` - calling a function via a function pointer that has not been initialized.

#### Assertions

From [`forge-std/std-assertions`](https://book.getfoundry.sh/reference/forge-std/std-assertions).

```solidity
// Fail a test with a message
fail(string memory err)

// Assert true/false
assertTrue(bool data)
assertTrue(bool data, string memory error)

assertFalse(bool data)
assertFalse(bool data, string memory err)

// Assert equal
assertEq(<type> a, <type> b)
assertEq(<type> a, <type> b, string memory err)

// Asserts `a` is approximately equal to `b` with delta in absolute value.
assertApproxEqAbs(uint256 a, uint256 b, uint256 maxDelta)
assertApproxEqAbs(uint256 a, uint256 b, uint256 maxDelta, string memory err)

// Asserts `a` is approximately equal to `b` with delta in percentage, where `1e18` is 100%. 
assertApproxEqRel(uint256 a, uint256 b, uint256 maxPercentDelta)
assertApproxEqRel(uint256 a, uint256 b, uint256 maxPercentDelta, string memory err)
```

#### Addresses and Keys

```solidity
// Create a labelled address
address addr = makeAddr(string memory name)

// Create a labelled address with private key
(address addr, uint256 privateKey) = makeAddrAndKey(string memory name)

// Sign data
(uint8 v, bytes32 r, bytes32 s) = vm.sign(uint256 privateKey, bytes32 digest)
```

#### Math

From  [`forge-std/std-math`](https://book.getfoundry.sh/reference/forge-std/std-math).

```solidity
// Returns the absolute value of a number.
uint256 v = abs(int256 a)

// Returns the difference between two numbers in absolute value.
uint256 v = delta(uint256 a, uint256 b)
uint256 v = delta(int256 a, int256 b)

// Returns the difference between two numbers in percentage, where `1e18` is 100%.
uint256 v = percentDelta(uint256 a, uint256 b)
uint256 v = percentDelta(int256 a, int256 b)
```

### Fuzzing

Use `vm.assume()` to specify conditions for inputs. It should only be used for narrow checks:
```solidity
function testSomething(uint256 v) public {
    vm.assume(v != 0);
    require(v != 0);
    ... 
}
```

Use `bound()` to restrict inputs to a certain range:
```solidity
function testSomething(uint256 v) public {
    v = bound(v, 100, 500);
    require(v >= 100 && v <= 500);
    ... 
}
```
