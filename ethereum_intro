📌 Ethereum & Smart Contracts
📆 Last Updated: March 2025

🌍 Ethereum & Blockchain
Ethereum is a decentralized, open-source blockchain platform that enables developers to create and deploy smart contracts.  Smart contracts are self-executing agreements written in code. Unlike Bitcoin, which primarily functions as digital money, Ethereum extends blockchain technology to programmable applications without the need for intermediaries.

Ethereum's strength lies in its decentralization and immutability, ensuring that applications run exactly as programmed, with no downtime, fraud, or third-party interference.

📌 How Ethereum Works
Ethereum operates on a decentralized blockchain, a type of distributed ledger technology (DLT). This means that:
✔ Transactions are recorded on multiple nodes (computers) across the network.
✔ No single entity controls the ledger—it’s managed by a peer-to-peer (P2P) network.
✔ Transactions are grouped into blocks, which are linked together using cryptographic hashes to form a Merkle tree.

This structure makes Ethereum highly resistant to alteration, as changing any data in one block would require recomputing the cryptographic links for all subsequent blocks, making tampering practically impossible.

📌 Smart Contracts: The Core of Ethereum
A smart contract is a piece of code stored and executed on the Ethereum blockchain. It runs automatically when predefined conditions are met.

🔹 Key Features of Smart Contracts
✅ Self-executing – No need for third parties (banks, lawyers).
✅ Immutable – Once deployed, the contract code cannot be changed.
✅ Trustless – Parties don’t need to trust each other; they trust the blockchain.

🔹 Example Use Cases
Decentralized Finance (DeFi) – Automated lending, borrowing, and trading.
NFTs & Digital Ownership – Tokenized assets representing art, collectibles, or real estate.
Supply Chain Management – Verifying product authenticity and tracking goods transparently.
A simple Solidity smart contract example:

solidity

// SPDX-License-Identifier: MIT
pragma solidity ^0.8.26;

contract SimpleContract {
    uint256 public value;

    function setValue(uint256 _value) public {
        value = _value;
    }

    function getValue() public view returns (uint256) {
        return value;
    }
}
This contract allows users to store and retrieve a value on the blockchain.

📌 Common Smart Contract Vulnerabilities & Security Risks
Despite their benefits, smart contracts can contain vulnerabilities that hackers exploit. Below are some of the most common security risks.

🔹 1. Access Control Issues
Problem: Developers forget to restrict sensitive functions, allowing unauthorized users to modify contract states.
Example Fix:

solidity

modifier onlyOwner() {
    require(msg.sender == owner, "Not the contract owner");
    _;
}
🔹 2. Unchecked External Calls
Problem: Contracts interacting with other contracts or addresses don’t verify responses, leading to unintended behaviors or exploits.
Example Attack: A malicious contract tricking another contract into executing unintended actions.

Fix: Always check for success before proceeding.

solidity

(bool success, ) = externalContract.call{value: 1 ether}("");
require(success, "External call failed");
🔹 3. Integer Overflow & Underflow
Problem: Before Solidity 0.8.x, mathematical operations exceeding allowed limits could wrap around, leading to incorrect calculations.
Example Fix: Use SafeMath or Solidity’s built-in overflow protection:

solidity

uint256 public number;
function add(uint256 _num) public {
    require(number + _num >= number, "Overflow detected"); // Manual check
    number += _num; // Safe in Solidity 0.8+
}
🔹 4. Price Oracle Manipulation
Problem: Smart contracts relying on a single price source can be manipulated.
Example Fix: Use decentralized oracles (Chainlink) instead of a single price feed.

solidity

uint256 public ethPrice;
function updatePrice(uint256 _price) public {
    require(msg.sender == trustedOracle, "Not authorized");
    ethPrice = _price;
}
🔹 5. Reentrancy Attacks (One of the Most Dangerous)
Problem: An external contract can repeatedly call back into the vulnerable contract before the first function call completes, draining funds.
Example Attack:

solidity

function withdraw() public {
    require(balances[msg.sender] > 0, "Insufficient balance");
    (bool success, ) = msg.sender.call{value: balances[msg.sender]}("");
    require(success, "Transfer failed");
    balances[msg.sender] = 0;
}
💥 If the attacker re-calls withdraw() before the balance is set to 0, they can drain funds!

Fix:

solidity

function withdraw() public nonReentrant {
    uint256 amount = balances[msg.sender];
    balances[msg.sender] = 0;
    (bool success, ) = msg.sender.call{value: amount}("");
    require(success, "Transfer failed");
}
✅ Updates state before making external calls (prevents reentrancy).
✅ Use OpenZeppelin’s nonReentrant modifier for better protection.

📌 Final Thoughts
Ethereum and smart contracts enable decentralized applications, removing middlemen and providing trustless execution. However, they come with security risks that can result in millions in losses if not properly mitigated.

🔹 Key Takeaways
✅ Ethereum uses a decentralized blockchain, making it immutable and tamper-proof.
✅ Smart contracts execute predefined logic automatically.
✅ Security risks (like access control flaws & reentrancy) must be carefully handled.
✅ Bug bounties exist to incentivize finding & fixing these vulnerabilities.

📌 Additional Resources
📖 Ethereum Whitepaper → ethereum.org/whitepaper
🔒 Smart Contract Security Best Practices → consensys.net
🔍 Bug Bounty Platforms → Immunefi | Code4rena
