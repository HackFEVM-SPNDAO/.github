# Welcome to SPN DAO

SPN stands for spending. Our team has created a data DAO that empowers consumers to turn their data, in particular, their credit card transaction data, into assets and have true ownership over their data. DAO members could curate and govern how and when the crowd-sourced data could be used. More importantly, by contributing to an evolving data economy governed by the DAO, members will receive tangible financial rewards whenever their contribution of data is accessed and processed. 


## Problem Statement

Our credit card transaction data reveal a lot about our behaviors. Aggregated together, they tell even more powerful stories about the economy. Is there a spike in Netflix subscriptions? Is there a dip in spending at hardware stores? Credit card transaction data is the highest-grossing data source in the “alternative data” market. The global alternative data market is anticipated to reach 143.31 billion USD by 2030 and is expected to grow at a 54.4% CAGR. North America alone accounted for a revenue share of more than 67.0% in 2021. 

There are more than 400 alternative data providers. Among them are credit card issuers like MasterCard and Visa, institutions like Bloomberg and Goldman Sachs, and numerous analytics firms. These businesses have been monetizing from selling purportedly anonymized and aggregated credit card transaction data and analytics services. The emergence of machine learning and AI have accelerated the growth of these services.

Despite mixed outcomes, hedge funds have spent billions of dollars acquiring such data with the hope to forecast stock performance more accurately. Google spent millions of dollars purchasing data from MasterCard, trying to link online ads to store purchases. 

However, consumers have little control over how and when their personal data, including credit card transaction data, is used. Consumers’ personal data fuels a multi-billion dollar industry while they receive almost no financial rewards. In practice, data from a single person is of little value. And there is no marketplace where consumers could coordinate and pool their data together. 


## Our Solution

Leveraging web3.0 technologies, SPN DAO makes it possible! Our first product release is a dApp on the FEVM chain that facilitates the creation and operation of a data DAO. 

These are the core functionalities of the POC. 

### For consumers/end-users: 

- If someone opts in to become a DAO member and to contribute to the data economy, they will be able to upload anonymized credit card transaction data as a .csv file, have it encrypted immediately and store the encrypted data on decentralized storage provided by IPFS. 
- The user will proceed to mint a soul-bound token (SBT). The token is non-transferable and represents provable membership of the DAO. More importantly, IPFS link is tied to the metadata of the SBT. Only a wallet containing the “admin NFT” will be able to decrypt the data. 
- Any existing DAO members have the option to burn their SBTs if they wish to exit the DAO and stop sharing their data. 

### For the admin of the DAO:

- The “admin NFT” will be held in a multi-sig wallet. The multi-sig will be jointly managed by the admin and signers elected by DAO members. 
- When the admin connects to the dApp and authenticates ownership of the “admin NFT”, they could unlock the admin portal. 
- The admin is able to view all the wallet addresses that own the SPN DAO SBT, and initiates decryption of the credit card transaction data tied to a given SBT. 
- Whenever a decryption is initiated, a payment will be triggered to send rewards in FIL to the holder of a given SBT. 


## How It's Made

The dApp utilizes two contracts on Wallaby. The first is an SBT generated from the data that DAO members provide. The second is an admin NFT which allows the decryption of DAO members' SBTs.

When a user uploads anonymized credit card transactions, the information will be encrypted using Lit Protocol (currently support unavailable on Wallaby) and stored on IPFS. As a workaround, we have currently set up a Pinata Submarine gateway that provides the user access to upload files into a private IPFS link using the API keys that are configured inside the dApp. Only the DAO admin has access to decrypting the info uploaded by the user. The user can generate SBTs with the response information from IPFS using the SpendSBT.sol contract deployed on Filecoin Wallaby.

We have token-gated the admin portal by validating the wallets that contain the "admin NFT" minted from SpendAdmin.sol contract. Admin users have access to decrypt the SBTs minted by the user and access the information from Submarine. Every decrypt action by admin users dispatches rewards to the corresponding user that shared the data. Rewards will be based on tFIL.

###### Architecture

- FEVM - For deploying zpdap smart contracts
- IPFS - protocol and peer-to-peer network for storing and sharing data in a distributed file system.

###### Technologies

- Smart Contracts - Solidity
- Backend - TypeScript
- Testnet - Filecoin Wallaby
- Tools - Hardhat, Remix, Metamask
- UX & UI Design - Figma

## Related source code repo

* dApp - https://github.com/zpdao/frontend
* Smart Contracts - https://github.com/zpdao/core

## Demo URL

https://spend-dao.vercel.app/

##  Future Road Maps

- To mitigate the risk of Sybil attacks, we will implement some solutions to enforce ZK proof of personhood. 
- When threshold cryptography-based encryption solutions (e.g., Lit Protocol, Medusa) begin to support the FEVM chain, we will update the encryption & decryptoin mechanism. 
- Deploy Gnosis Safe on FEVM and build out the UI. 
- Fork the voting contracts from snapshot.org and build on-chain voting on FEVM. 
- Make the metadata of the membership SBT upgradeable and enable stacking more data contributions from holders. 
- Leverage confidential computing infrastructure, and set up data warehouse that stores and encrypts the combined data.  


## Team

* Jonathan Conn: Backend Developer
* Ram Vittal Kumar: Full-stack Developer
* Tobias Leinss: Full-stack Developer
* Karen Sheng: Product Manager
* Yifeng Wang: UX & UI Designer
