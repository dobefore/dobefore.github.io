---
title: token-economy
readmore: true
date: 2022-07-24 19:44:25
tags: 
- web3
- smart-contract
- distributed-ledger
---
from the book <<token economy how the web3 reinvents the Internet>>.
# Web3 basics
## Tokenized Networks:  Web3, the Stateful Web
 The Web3 changes the data structures in the backend of the Internet, introducing a universal state layer, often by incentivizing network actors with a token.
The backbone of this Web3 is represented by a series of blockchain networks or similar distributed ledgers.
The Web2 allowed us to enjoy peer-to-peer (P2P) interactions on a global scale, but always with a middleman: a platform acting as a trusted intermediary。

State refers to information, or the status of “Who is who?”; “Who owns what?”; and “Who has the right to do what?” in a network. 
## Decentralized Applications in the Web3
A decentralized application is a blockchain client - often also referred to as the “wallet.” It uses the same technologies to render a webpage or a mobile app (like HTML, CSS, Javascript) but communicates with a blockchain network instead of a server and, in the case of smart contract networks,
How can a "wallet" get ledger data(nodes info) ?
## Keeping Track of the Tokens: Bitcoin, Blockchain, & Other Distributed Ledgers
Blockchain networks build on the idea of P2P networks, providing a universal data set that every actor can trust, even though they might not know or trust each other. Immutable copies of that data are stored and managed on every node in the network.  (How can I get the immutable 
copy of data (the ledger) ?)

**Chain of Blocks**: In a blockchain network, token transactions are recorded in batches of data called “blocks” that are “hashed.” This cryptographic hash creates a digital fingerprint of the block . Each block includes the hash of the prior block, thereby linking one block with another into a chain of blocks. This process guarantees the historic integrity of all the blocks back to the first block, also referred to as the genesis block. 

***he ledger** is a file that maintains a growing list of transaction records, chained in blocks that are cryptographically secured from tampering and revision.the ledger of a blockchain network is a document that is not centrally stored. Instead, each node of the network keeps an identical copy of the same file at all times (with temporary exceptions every time a new block is created).
**Distributed Ledger**: A copy of the ledger is stored on multiple nodes of a cryptographically secured P2P network. In order to change the ledger data on all copies of the ledger throughout the whole network, the network nodes need to reach a mutual agreement about such a change.Each independent node has the latest version of the ledger （how can I get this?）, which contains all transactions that have ever been made, and can verify transactions.
**Tokens**:  a token does not represent a digital file that is sent from one device to the other. Instead, it manifests as an entry in the ledger that belongs to a blockchain address. Only the person who has the private key for that address can access the respective tokens, 
using a wallet software, which acts as a blockchain client (read more:

Every node of network is a client as well as a server,holding indentical copies of application 
state  (the ledger).
## Cryptoeconomics, Consensus & Proof-of-Work
When tokens are sent over the network, each node in the network can propose new entries to be added to the ledger. These nodes validate transactions and compete with each other to solve a complex computational puzzle. In this process, they have to collect all recent network transactions, including some additional metadata, verify the transactions, guess a pseudo-random number (“nonce”), and run all the data through a cryptographic algorithm (SHA-256) to find the hash of the new block. This means that they have to perform computational work, which is the reason why this process is referred to as “Proof-of-Work.”

If a node is the first one in the network to find that hash value, it can add the block to its ledger and broadcast the hash value of the new block, including all block data, to the rest of the network. The other nodes can now verify the validity of the hash. If they accept this newly added block of transactions as valid, they add the new block to their copy of the ledger.The winning node is rewarded with the “block reward” in the form of newly minted network tokens (plus potential transaction fees). This is why the process is referred to as “mining.”
## smart contract
many smart contract use cases will only be possible interplaying with other technologies like big data applications and the “Internet of Things.”
use case:Alice wants to buy Bob's second-hand car using web3 page 341.


> Szabo justified the term “smart” with the functionality that comes with digital contracts to be automatically verified and executed:

## institutional economies of web3 or other DAOs
DAOs tackle an age-old problem of governance which is referred to as the “principal-agent dilemma,” which occurs when the agent of an organization has the power to make decisions on behalf of, or impacting, the principal—another person or entity in the organization. Examples thereof could be managers that act on behalf of shareholders or politicians that act on behalf of citizens.
This dilemma usually increases when there is underlying information asymmetry at play.



## Token
Traditionally, tokens can represent any form of economic value or access right. Shells and beads were probably the earliest types of tokens used.  Paper money or coins are also tokens.

### Properties of Tokens
- Rights Perspective
- “Asset tokens” can represent a unit of account (fungible) or a unique good (non-fungible).
- “Credentials tokens” can be used to attest identity
- Fungibility Perspective: Fungibility refers to the interchangeability of a unit of an asset with other units of the same asset.Fungible assets have two key properties: (i) Only quantity matters, which means that units of fungible assets of the same kind are indistinguishable. (ii) Any amount can be merged or divided into a larger or smaller amount of it, making it indistinguishable from the rest. If you were to lend 10 EUR to someone, for example, it would not matter if that person returns the exact same 10 EUR bill or another one, 
- Transferability Perspective:
- Durability Perspective: In economics, durability refers to the ability of a currency to withstand repeated use

# The Future of Money & Decentralized Finance (DeFi)
The primary purpose of money is to facilitate an economic exchange of goods and services within and between economies， avoiding the inefficiencies of such systems like the “coincidence of wants” problem.
The coincidence of wants problem refers to the improbability that two parties, each of which own different goods, can agree on a deal, unless each party wants the specific good the other party offers,
Money needs to serve as a medium of exchange, store of value, and unit of account in which debt can be denominated.
## Types of Money
 the dominant type of money is fiat money. Prior to the existence of modern day fiat currencies, commodity money and representative money were in widespread use.

