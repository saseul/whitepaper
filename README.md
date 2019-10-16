# SASEUL Whitepaper

## ArtiFreinds inc.


### 1. Introduction 

#### 1.1 What is SASEUL  
Blockchain is, an immutable time-stamped series record of data that is distributed and managed by a cluster of computers.  

In a simple phrase, blockchain (originally block chain) is a growing list of records, called blocks, that are linked using cryptography. Each block contains a cryptographic hash of the previous block, a timestamp, and transaction data (generally represented as a Merkle tree).  

By design, blockchain is resistant to modification of data. It is "an open, distributed ledger that can record transactions between two parties efficiently and in a verifiable and permanent way". To implement a ​distributed ledger,​ blockchain is typically managed by a peer-to-peer network, where participants collectively adhere to a protocol for inter-node communication and block validation. Once recorded, data in any given block cannot be altered retroactively without alteration of all subsequent blocks, which requires consensus of the network majority. Blockchain records are not ​impossible to a​ lter. However, blockchain technology is inherently designed to boost security and exemplify a distributed computing system with high Byzantine fault tolerance. Decentralized consensus is therefore a perfect fit to implement inter-node communication within the blockchain network.  

For these reasons, many industry leaders expect to achieve significant business benefits, including greater transparency, enhanced security, improved traceability, increased efficiency and speed, and reduced costs.  

Unfortunately, there are no blockchain technologies out there that can satisfy the industrial standards. To surpass industrial standards, blockchain technology needs three features - decentralization, stability and fast speed (transactions per second). All existing blockchains lack at least one of them. However, SASEUL is the first blockchain technology that holds all three values - decentralization with fast tps and stability. SASEUL is proving that it satisfies industrial standards through a lot of use cases.  

#### 1.2 Disclaimer
This document has been prepared by the management of ArtiFriends Inc. and its subsidiaries (“we”, “us” or the “Company”) solely for informational purposes and is being furnished to a limited number of prospective investors who have expressed an interest in evaluating the Company’s proposed financing transaction. By reviewing or saving this document, you agree that you have been informed of the confidential nature of the information provided in this document and that you will treat such information as confidential.
By receiving and accepting this presentation, you (i) acknowledge that you have read and understand this notice and disclaimer, (ii) agree to be bound by the terms hereof and to comply with the obligations set forth herein and (iii) make the representations and warranties set forth herein. You and your directors, officers, employees, agents, advisors and affiliates must hold the information provided in this presentation and any update, supplementary statements made in connection herewith in strict confidence and may not communicate, reproduce, distributor disclose the any of same publicly or to any other without the Company’s prior written consent.
You should not rely on this documentation to form the basis of any investment decision or as an inducement to enter into any contract, commitment or action whatsoever with respect to the proposed financing or otherwise. In all cases, you should conduct your own investigation and analysis of the Company and its business, prospects, results of operations and financial condition, perceived risks, market opportunity and any other relevant information. You represent to us that you are not relying on any information contained herein or any statement by making an investment decision with regard to the proposed financing transaction or otherwise. Neither we, nor any of our affiliates, directors, officers, employees, advisors or agents (collectively, the “Related Parties”) make any representation or warranty, express or implied, in relation to the accuracy or completeness of the information contained in this presentation and any updates, supplements and oral statements made in connection herewith, or as to the achievement or reasonableness of future projections, management targets, estimates, prospects or returns, and the Company and the Related Parties expressly disclaim any and all liability for losses or claims arising out of or arising out of such information, including any errors or omissions there from. Any views contained herein of the terms of the financing transaction are preliminary only and based on market and financial conditions prevailing as of the date hereof, and therefore subject to change.
The information contained in this document is based on financial, economic, market and other conditions prevailing as of the date of this presentation and are therefore subject to change due to unforeseen circumstances any time without notice. The Company has no obligation to update this presentation.
This document may contain statements of intention, forward-looking statements, forecasts, estimates, assumptions simulations and opinions relating to the business, financial performance and results of the Company and/or the industry in which it operates (“Forward Statements”). Such Forward Statements, whether the views Company or those cited by third party sources, are solely opinions and forecasts which are uncertain and subject to risks, uncertainties and other factors that could cause actual results to vary materially from those anticipated by the Forward Statements. Neither the Company nor the Related Parties make any representations that the assumptions upon which the Forward Statements may be based are reasonable.
Neither this document nor anything contained herein constitute an offer to sell or the solicitation of an offer to buy any securities or financial instruments or participate in the financing transaction or any other transaction whether as investor or in any other capacity. This document does not constitute and should not be considered as any form of financial opinion or recommendation by the Company or any of its affiliates.

## 2. Terminology

#### 2.1. Node

Node is a machine just like a computer or cell phone, which has Memory, Storage(HDD, SDD) and CPU (or GPU) including communication protocol and equipment between nodes.
Node has only one Network Address and one Key Address. A person can own multiple nodes. Distributed processing system like Load Balancer allows many nodes to operate like a single node.

#### 2.2. Network
Network in this whitepaper is basically the Blockchain Network. Blockchain Network is the group of nodes sharing same block data and should generate same transactions and decisions. If nodes make different blocks or decisions, the node will be in a different network. This process is called a ‘Fork’.

#### 2.3. Block data
Block data is all the data shared by Blockchain Network and consists of Status data, Transaction data, Decision data and Hash data.  
Status data is the dataset of databases in general internet service. Each node changes the status according to the result of transaction handling.  
Transaction data is a request made to the network to change the status data. Nodes process transactions according to a set rule. Accepted transaction changes the status, denied transactions do not change the status.  
Blockhash is created using decision data and transaction data, and each data is connected using the hash of previous block together.  

#### 2.4. Generation
Certain nodes compress the block data when a sufficient number of block data accumulates. Each compressed block is called a Generation Block.  

### 3. Consensus - HAP-2 (or POR)
SASEUL has invented Proof of Rule (POR) consensus algorithm without BFT issue and HAP(Hypothesis Acceptance Protocol), the piece of software, was implemented with this consensus. HAP-2 is the second version of HAP and HAP-2 is used synonymously with POR.  

The core idea of HAP-2 is that all nodes of SASEUL are very selfish decision makers, who focus on building their own blocks. A node builds a hypothetical block after gathering and merging all the transactions from other nodes and rearranging them by timestamp. The node compares this hypothetical block with others’ blocks and finally decide to attach it selfishly.  

#### 3.1. Network Lifecycle
Background Activity: Sync  
A node that has shorter blocks than others, just pull the extra blocks from a node that has the longest blocks and sync the extra blocks one by one after verifying them. After this process, the node begins the process below.  
   
      a) Ping  
         Nodes periodically collect information about status from others

      b) Receive a transaction  
         Nodes(Validators) participating in consensus collect transactions requested from the network.

      c) Rounding  
         The node that collects transaction creates a Hypothesis (data Chunk) to become the next block.

      d) Data pulling  
         After completing the c) Rounding phase, Nodes collect the network hypotheses.  
         Collecting hypotheses is a process that starts when nodes find hypotheses of other nodes during the a) Ping phase.  
         Nodes must ensure that their hypotheses do not reverse the decision by putting their Signature on the hypothesis they present.

      e) Make a decision  
         Collected hypotheses in d) step are disassembled and the disassembled transactions are rearranged by timestamp and other factors. Approval or disapproval of the respective transaction is decided by verification. After all these processes, Blockhash will be generated.

      f) Pre-commit
         Block is created with the accepted hypotheses in d) step and Blockhash in e) step. The node will then compare the Block with others’ Blocks . Depending on the result of comparison, the node decides whether it merges the Block or Fork the Node based on several rules.

      g) Commit
         Confirm Block and repeat from a) step.

#### 3.2. Transaction Verifying - Smart Contract
All the Transactions are definitely controlled by a Smart Contract. Contract Code follows the 4 steps below.

1. Check transaction structure & validity  
Check the structure and speculation of requested Transaction. Transaction should include all the variables set accordingly and have the signature created by Private key of Requestor.

2. Load status  
Get the Status from Block data for handling Transaction.

3. Make a decision  
Decide the ‘Accept/Deny’ depending on Status.

4. Set status  
   If accepting the Transaction, change the Status and SASEUL Engine basically provide below four System Contracts.

   1. Genesis
   This is the Contract to create the first Block. Attribute, Method, and Contract can be predefined. First declarator is always validator.

   2. UpdateAttribute
   This is the Contract to change the structure of Status defined by Network. The time of changing the structure could be assigned.

   3. UpdateMethod
   This is the Contract to change and define the Methods in Contract. The time of changing the structure could be assigned.

   4. UpdateContract
   This is the Contract to define new Contract or change existing Contract. The time of changing the structure could be assigned.

### 4. Definitions of SASEUL Nodes 

#### 4.1 Light node

Light nodes are the most basic and simple nodes on the network. They are directly related to blockchain wallet and practical services for the end users who do not actively contribute to the network. Each ​node has its unique private key and tracker and is capable of requesting transactions and viewing the transaction results.

#### 4.2 Supervisor
Supervisors are nodes that sync all existing blocks on the network. Theydifferfroml​ight nodes because they are meant to monitor and supervise the blockchain network. The supervisors check whether the network has
Light nodes are the most basic and simple nodes on the network. They are directly related to blockchain wallet and practical services for the end users who do not actively contribute to the network. Each ​node has its unique private key and tracker and is capable of requesting transactions and viewing the transaction results.

#### 4.3 Validator
Validators also sync all existing blocks on the network and are authorized to participate in the consensus process. ​They are
capable of receiving transaction requests and either accepting or denying them based on consensus to generate data in a block form. The fundamental consensus is derived from the SASEUL Consensus Algorithm. Validators communicate directly with light nodes, periodically hash generated blocks, and transfer those blocks to the arbiters.

#### 4.4 Arbiter
Arbiters are storage nodes for all blocks created in the network. They do not participate in the consensus process. The only responsibility they have is sending past data when a validator requests them for reference during validation.

### 5. Requirements
   Validator, Supervisor Node  

   Minimum: 2 Core, 4 Thread CPU  
   Recommendation: 4 Core, 8 Thread CPU  
   
   Minimum: 250 GB SSD  
   Recommendation: 1 TB SSD  
   
   Minimum: 8GB Memory  
   Recommendation: 16GB Memory  
   
   Minimum: 5 Gbps Network Capacity  
   Recommendation: 20 Gbps Network Capacity  
   
   Arbiter  
   Minimum: 4 Core, 8 Thread CPU  
   Recommendation: 8 Core, 16 Thread CPU or GPU equivalent spec of the CPU.  
   
   Minimum: 1 TB SSD  
   Recommendation: The more, the better.  

   Minimum: 16GB Memory  
   Recommendation: 64GB Memory  

   Minimum: 20 Gbps Network Capacity   
   Recommendation: The more, the better.  
   