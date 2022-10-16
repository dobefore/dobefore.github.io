---
title: web3-basics
readmore: true
date: 2022-07-31 09:54:36
tags: 
- blockchain
- web3
---
以下是我根据书本Build web3 APP 观察整理总结而来。
**the Concept  of the P2P network**:

**About hash and public-private key pair**
keypair can be used inversely as digital signatures. a user send a msg, along with its digest encrypted with his private key,the recipient can verify that the digest was signed by the owner of the public key.

**About Smart Contract**：A smart contract is a short  program uploaded to the blockchain,which can reacted to the transactions by its arbitrary logic .Each smart contract has its own arbitrary state as well,which can be updated on any transaction and can keep any data whatsoever.And of course,a smart contract can also hold ETH,the native currency of the Ethereum network.In other words,the Ethereum network holds both a digital currency(the ether)and
executable code (the smart contracts)with their own state.

**Dapp的响应速度**：all DApps need to account for the long confirmation times of the network。
in Ethereum,a transaction may take several seconds to be mined,and even more to be confirmed.

**degrees of DApp(我们如何对待Dapp和c/sApp)**:a DApp can be fully decentralized:it can be hosted on a decentralized storage location,load its data from the blockchain,and rely on smart contracts for any business logic.We can even build fully centralized applications that interact with a decentralized protocol powered by smart contracts on the Ethereum blockchain.By managing our users'assets on a decentralized layer,we guarantee that their data is safe.(这不就是我的猜想：在Anki加一层Dapp确保data is encrypted)

 **use cases**:in a situation where it need a third trusted party.            

Q1：了解或者实践部署Dapp的大致过程。
Q2: How can one get latest state of the Ledger in his Dapp？ 

Q3:How p2p network works?
Whenever a user requests a file from the network,that file is downloaded from the nearest node that has the file and is made available for other users to download from this new location.
Any data unit in IPFS is not identified by its location,but by its content.When requesting a file from the IPFS network,you address it by its identifier,which is nothing else than a hash of the content.

To enable IPFS support in our application,we first need to connect to an IPFS node.We can either host our own IPFS public node as part of our application or rely on a  third-party provider.

All our application's client-side code can be uploaded to IPFS and served from there.But how can our users access it from a regular browser?Or address it without having to specify a hash?
The first problem can be solved via IPFS gateways(see Listing 6-26 for examples).

An IPFS gateway is a regular web site that serves content from the IPFS network.It allows
you to access any IPFS item at the path /ipfs/CID,where CID is the content hash that identifies each object on the network.
The second problem,having user-friendly names for IPFS sites,can be solved
using DNSLink.DNSLink is a process for mapping DNS names to IPFS content using
DNS TXT records.Let's say we want to map our site in IPFS to the domain example.com.By adding a TXT record to_dnslink.example.com with the value dnslink=/ipfs/CID,any IPFS gateway
will automatically map any requests to/ipfs/example.com to the specified content.

