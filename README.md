# Encrypted Voting System (EVS)

## 🗳 Overview

The **Encrypted Voting System (EVS)** is a Solidity-based smart contract designed to facilitate secure, transparent, and decentralized voting on the Ethereum blockchain. The contract enables administrators to manage an election by adding candidates and allowing users to cast their votes securely while ensuring integrity and immutability.

## 🔒 Key Features

* **Owner-Based Access Control:**
  Only the contract owner can manage sensitive functions like adding or removing candidates, resetting the election, or transferring ownership.

* **Candidate Management:**
  Admins can add or remove candidates to/from the election dynamically.

* **One-Vote Policy:**
  Ensures that each voter can cast a single vote per election.

* **Secure Vote Casting:**
  Voters can vote only once, and only for valid candidates.

* **Result Calculation:**
  Provides a function to determine the winner based on the highest number of votes.

* **Election Reset:**
  Enables the contract owner to reset the election data to prepare for a new voting session.

## 🔧 Requirements

* Solidity ^0.8.30
* Hardhat (for development and testing)
* MetaMask or another Ethereum-compatible wallet (for interaction)

## 📁 Project Structure

* `EVS.sol` – Core smart contract containing all logic for managing the election lifecycle.

## ✅ How It Works

1. **Deployment:**
   The contract is deployed by the election organizer, who becomes the owner.

2. **Candidate Setup:**
   The owner adds a list of eligible candidates.

3. **Voting:**
   Users cast their votes by selecting a candidate. The system enforces that each address votes only once.

4. **Results:**
   At any time, the current winner can be queried.

5. **Resetting:**
   Once the election is over, the owner can reset the contract to start a new election cycle.

## 🚫 Limitations

* Does not currently support handling ties in vote counts.
* Voting is not anonymous; votes are linked to Ethereum addresses.

## 📜 License

This project is licensed under the MIT License.

## 🤝 Contributions

Contributions are welcome! Please open an issue or submit a pull request for feature suggestions, improvements, or bug fixes.
