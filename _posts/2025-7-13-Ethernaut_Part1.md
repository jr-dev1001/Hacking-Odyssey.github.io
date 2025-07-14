---
layout: post
title: Ethernaut CTF Part-1!
subtitle: 1 - 8 challenges
excerpt_image: 
categories: CTF
tags: [solidity]
---
<h3 align="center">Ethernaut CTF Part-1</h3>
<p align="center">
  <img src="https://raw.githubusercontent.com/jr-dev1001/Hacking-Odyssey.github.io/refs/heads/main/images/ethernaut.png" alt="Ethernaut">
</p>

---

## Introduction
I've started doing work arounds on blockchain, as a part of it I started solving Ethernaut CTF, as this is long making this into parts.

---

## TLDR;

### Level Name - 0.Hello

☢️ Vulnerability Concept:
No actual vulnerability — this level is for setup, interaction, and basic Solidity understanding. It's about exploring and understanding the Ethernaut environment, ABI, and on-chain data.

🛠️ Exploit Mechanism:
Interact with the contract using the console to:
1. Navigate function calls step-by-step (info → info1 → info2 → info42 → method7123949)
2. Read the private password from storage slot 0
3. Pass the password to `authenticate()` to clear the level

🔁 Real-World Example:
Understanding that private variables in Solidity are not really hidden — they're stored on-chain and can be read by anyone. Also introduces contract introspection using web3 or ethers.js.

✍️ My Attack Summary (in 2-3 steps):
1. Used `await contract.info()` and followed function hints
2. Read `password` from slot 0 using `web3.eth.getStorageAt(instance.address, 0)`
3. Called `authenticate(password)` to complete the level

📦 Solidity Snippet I learned:
```solidity
function authenticate(string memory passkey) public {
    if (keccak256(abi.encodePacked(passkey)) == keccak256(abi.encodePacked(password))) {
        cleared = true;
    }
}
```
---
### Level Name - 1.Fallback

☢️ Vulnerability Concept:
Misused `receive()` fallback function allows ownership transfer when certain conditions are met. Ownership logic is unintentionally duplicated in the fallback, creating a secondary path to become owner.

🛠️ Exploit Mechanism:
1. Make a small contribution using `contribute()` (less than 0.001 ETH)
2. Send ETH directly to the contract to trigger the `receive()` function
3. This changes the `owner` to `msg.sender` if contribution was > 0
4. Call `withdraw()` to drain the contract balance

🔁 Real-World Example:
Poorly designed fallback functions in contracts can become unauthorized entry points. This mimics real DeFi attacks where fallback/receive is over-permissive or improperly guarded.

✍️ My Attack Summary (in 2-3 steps):
1. Called `contribute()` with a tiny amount to satisfy `contributions[msg.sender] > 0`
2. Sent ETH directly to the contract address (triggered `receive()`), became `owner`
3. Called `withdraw()` and drained the contract balance

📦 Solidity Snippet I learned:
```solidity
receive() external payable {
    require(msg.value > 0 && contributions[msg.sender] > 0);
    owner = msg.sender;
}
```
🧠 This showed me how fallback functions can be dangerous when they change critical contract state like ownership.

---
### Level Name - 2.Fallout

☢️ Vulnerability Concept:
Incorrect constructor declaration in older Solidity versions — `Fal1out()` is just a public function, not a constructor, due to a typo. This allows anyone to call it after deployment and set themselves as the contract owner.

🛠️ Exploit Mechanism:
1. Identify that `Fal1out()` is not a constructor (misspelled, lowercase `L` and digit `1`)
2. Call `Fal1out()` directly — it sets `owner = msg.sender`
3. Now that you're owner, you can call `collectAllocations()` to drain the contract

🔁 Real-World Example:
Before Solidity 0.4.22 introduced the `constructor` keyword, constructor functions relied on matching the contract name exactly. Typos allowed malicious actors to claim ownership post-deployment — seen in older DeFi codebases.

✍️ My Attack Summary (in 2-3 steps):
1. Called the misnamed `Fal1out()` function directly to become owner
2. Verified ownership with the `owner()` public getter
3. Called `collectAllocations()` to transfer contract balance to myself

📦 Solidity Snippet I learned:
```solidity
function Fal1out() public payable {
    owner = msg.sender;
    allocations[owner] = msg.value;
}
```
---
### Level Name - 3.CoinFlip

☢️ Vulnerability Concept:
Predictable randomness using `blockhash(block.number - 1)` — this value is deterministic and publicly accessible on-chain, making it possible to compute the same result as the contract and always win the flip.

🛠️ Exploit Mechanism:
1. The contract derives the "random" coin flip from `blockhash(block.number - 1)` divided by a known constant `FACTOR`
2. This hash is available to all contracts, so an attacker contract can calculate the same result
3. By predicting the flip outcome before calling `flip()`, you can win repeatedly

🔁 Real-World Example:
Multiple real DeFi and gaming contracts have been exploited due to on-chain randomness misuse (e.g., games using `block.timestamp`, `block.number`, or `blockhash()` for RNG).

✍️ My Attack Summary (in 2-3 steps):
1. Created an attack contract that reads `blockhash(block.number - 1)` and calculates the expected outcome using the same logic as `CoinFlip`
2. Sent that guess to the target contract via `flip()`
3. Won flips repeatedly by submitting the correct prediction every time

📦 Solidity Snippet I learned:
```solidity
uint256 blockValue = uint256(blockhash(block.number - 1));
uint256 coinFlip = blockValue / FACTOR;
bool side = coinFlip == 1;
```
---
### Level Name - 4.Telephone

☢️ Vulnerability Concept:
Improper use of `tx.origin` for ownership authentication — leads to logic bypass when function is called via contract.

🛠️ Exploit Mechanism:
Call `changeOwner()` through an attacker contract so that `msg.sender != tx.origin`, satisfying the contract's condition and allowing ownership takeover.

🔁 Real-World Example:
Phishing attacks where malicious contracts exploit `tx.origin` checks to perform unauthorized actions on behalf of unsuspecting users (e.g., Parity Multisig vulnerability pattern).

✍️ My Attack Summary (in 2-3 steps):
1. Deploy a contract that calls `changeOwner(tx.origin)` on the target.
2. Call that contract from your EOA (externally owned account).
3. Since `msg.sender` (contract) ≠ `tx.origin` (EOA), condition passes and owner becomes EOA.

📦 Solidity Snippet I learned:
```solidity
function attack() external {
    telephone.changeOwner(tx.origin);
}
```
---
### Level Name - 5.Token

☢️ Vulnerability Concept:
Integer underflow — in Solidity <0.8.0, subtracting a larger number from a smaller one wraps around to a huge value. This breaks balance checks and allows attackers to gain unearned tokens.

🛠️ Exploit Mechanism:
1. The contract checks `require(balances[msg.sender] - _value >= 0)`  
   This looks safe, but in Solidity 0.6.0, underflow wraps to max `uint256`
2. Call `transfer()` with `_value > balance` (e.g., transfer 21 tokens with only 20 in balance)
3. `balances[msg.sender]` underflows → becomes huge number
4. This lets you send massive value and claim balance you didn’t have

🔁 Real-World Example:
Before Solidity 0.8.x added automatic overflow/underflow protection, many DeFi hacks abused this behavior. For example, the 2017 `Parity Wallet` vulnerability was partly caused by unsafe math operations.

✍️ My Attack Summary (in 2-3 steps):
1. I started with 20 tokens (default)
2. Called `transfer(<any address>, 21)` — underflow bypassed the balance check
3. `balances[msg.sender]` became huge — effectively giving me infinite tokens

📦 Solidity Snippet I learned:
```solidity
require(balances[msg.sender] - _value >= 0); // looks safe, but unsafe in Solidity <0.8.0
balances[msg.sender] -= _value;
balances[_to] += _value;
```
---
### Level Name - 6.Delegation

☢️  Vulnerability Concept:
Misuse of `delegatecall` in fallback allows unauthorized execution of external contract logic in the caller’s storage context.

🛠️ Exploit Mechanism:
Send the function selector for `pwn()` directly to the `Delegation` contract. The fallback triggers, performing a `delegatecall` to `Delegate`, executing `pwn()` in the storage of `Delegation`, and setting `owner = msg.sender`.

🔁 Real-World Example:
Improper proxy setups or upgradeable contracts have suffered this — notably, the Parity Multisig Wallet hack (2017) where the delegate context overwrote critical storage.

✍️ My Attack Summary (in 2-3 steps):
1. Sent `0xdd365b8b` (`pwn()` selector) to `Delegation` from EOA
2. `fallback()` was triggered → `delegatecall` to `Delegate.pwn()`
3. Storage of `Delegation` updated → `owner = my EOA`

📦 Solidity Snippet I learned:
```solidity
fallback() external {
    (bool result,) = address(delegate).delegatecall(msg.data);
}
```
---
### Level Name - 7.Force

☢️  Vulnerability Concept:
A contract cannot prevent receiving Ether sent via `selfdestruct()`. This bypasses normal transfer logic, including `receive()` and `fallback()` functions.

💡 How Ether Can Be Sent to a Contract:
1. **During contract deployment**  
   Using a `payable constructor`, you can send ETH to the contract at the time of deployment.
2. **By receiving ETH through `receive()` or `fallback()`**  
   The contract must implement these functions with the `payable` modifier to accept ETH directly via calls or transfers.
3. **Using `selfdestruct(address)` from another contract** ✅  
   Ether is forcefully sent to the target address when a contract self-destructs. This method **cannot be refused**, even if the target contract lacks payable functions.
4. **(Advanced)** Set `block.coinbase = contractAddress`  
   If the miner chooses your contract address as the block reward recipient, the block reward ETH is transferred there.


🛠️ Exploit Mechanism:
Deploy a contract with ETH and call `selfdestruct(payable(target))`. The ETH is forcefully transferred to the target contract's address, even if it has no payable functions or fallback.

🔁 Real-World Example:
Used in griefing or poisoning attacks — e.g., breaking logic in vaults or DeFi contracts that assume `address(this).balance == 0` or control over incoming funds.

✍️ My Attack Summary (in 2-3 steps):
1. Created and deployed a contract with a `payable` constructor and a `selfdestruct()` call targeting the Force contract.
2. Funded the attack contract with ETH at deployment.
3. Called `attack()` → triggered `selfdestruct()` → ETH forcibly sent to the Force contract.

🧠 Why We Use `selfdestruct`:

- **Bypasses contract logic**  
  ETH is sent regardless of whether the contract has a payable function or not.
- **Cannot be refused**  
  The target contract has no way to prevent receiving Ether this way.
- **Enables forced ETH injection**  
  Useful in CTFs and real-world exploits where you want to “break” assumptions like `balance == 0` in contracts that seem ETH-proof.

📦 Solidity Snippet I learned:
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract ForceAttack {
    constructor () public payable {}
    function attack(address payable _contract) public {
        selfdestruct(_contract);
    }
}
```
---
### Level Name -8.Vault  

☢️  Vulnerability Concept:  
Solidity's `private` visibility does not prevent on-chain access. All contract storage, even private variables, is publicly accessible by anyone who knows the storage slot index.

🛠️ Exploit Mechanism:  
Use off-chain tooling (`web3.eth.getStorageAt`) to read the password stored in slot 1, then call `unlock(password)` from any EOA or contract. Solidity contracts cannot read another contract’s storage directly.

🔁 Real-World Example:  
Many contracts that store sensitive information (like admin secrets or cryptographic keys) have been compromised because of improper assumptions about `private` visibility in Solidity. Example: early DeFi wallets exposing private variables on-chain.

✍️ My Attack Summary (in 2–3 steps):  
1. Located the password in storage slot 1 using `web3.eth.getStorageAt(contractAddress, 1)`  
2. Retrieved the password value from chain state using JavaScript/Web3 tools  
3. Called `unlock(bytes32 password)` using the retrieved value → contract unlocked

📦 Solidity Snippet I Learned:
```solidity
function unlock(bytes32 _password) public {
    if (password == _password) {
        locked = false;
    }
}

```
---
