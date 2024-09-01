# Navigators Season 2: Growth Grants Proposal

# z2zlib
A formalization and Typescript API of p2p state channels for Mina Protocol

## Project Background
This project will aim at levraging Mina's unique infinite recursive proving capabilities for the development of a peer-to-peer state channel infrastructure. This library will allow developers to build decentralized apps such as multiplayer on-chain games where actors will be able to interact in a zero-trust setup, peer-to-peer and optionally settle disputes using a zkApp smart contract.  

This project proposal builds upon a hackathon project in which I developed a dice betting game. The initial version of this game necessitated interactions with a smart contract for every game state transition. However, a significant limitation of this architecture was the unecessary use of the consensus layer of Mina at each intermediate interactions, which introduced substantial delays between each player's actions. An alternative to this architecture would have been to have the players set up a state channel through which they would exchange proofs for each state transition and eventually settling with a smart contract using sending out the proof of winning state.

## Proposal Overview

- **Problem:** Traditional multiplayer decentralized apps on Mina often rely on smart contracts to handle state-changes. This enforces a general consensus on state transitions which induces considerable delay.

- **Solution:** 
    - Standardization of an off-chain p2p state channel to handle state transitions making use of Mina's unique constant size recursive proving cabability.
    - Development of a p2p state channel library. Abstracting away the network stack for p2p proofs exchange.
    - Development of three examples showcasing uses of the library
        - multiplayer game 
        - p2p defi protocols
        - b2b zk use like supply-chain
    - Writing of a detailed documentation

- **Impact:** This project improves tooling which therefore encourages adoption. To what degree does this proposal contribute to enhancing the Mina ecosystem? Does it encourage adoption, offer improved tools, or attract more users and developers? Does it enable novel applications?
    - This project will improve current infrastructure regarding the development of multi-actor turn-based apps which will enable Mina developers to write zkApps with a better ux in a more efficient manner thanks to the abstraction and formalization of z2zlib.

- **Audience:** Mina builders.



## Architecture & Design
Outline:
<div align="center">
<br>
<img style="align: center" src="./z2z-Alice-Bob-architecture-diagram.png" height=256/>
</div>
<br>

The z2zlib will be composed of sevral elements:
- Network stack:
    - Connection setup: the connection between peers will be setup using a hole-punching protocol which will be aided by either:
            - A network of users incentivized to act as relays 
            - An ICE server.
- Interface with o(1)js:
    - Types representing actors
    - Types representing states machines 
    - Types representing proofs of states
    
    - Contract interfaces for dispute settlements

- **Vision:** What is your long-term vision for this project if your proposal is funded?
    - The long-term vision for this project is to scale zkApps whithout compromising decentralization.
    
- **Production Timeline :** In three month from the start of the project. 

##  Budget & milestones
This section should detail the deliverables at the end of the funding period, mid-point milestones, timeline and the budget requested. It should explain how the budget will be spent.

- **Deliverables**:
    - research paper specifying state channels for the Mina Protocol.
    - z2zlib
    - Docuementation
    - Game example use-case
    - Defi example use-case
    - Supply chain example use-case

- **Mid-Point milestones:** What milestones would you aim to deliver half-way through.
- **Project Timeline :** 3M
- **Budget Requested :** 100,000 MINA
- **Budget Breakdown:**:
    - 10,000 MINA : Initial research
    - 20,000 MINA : Reasearch paper formalizing the state channel
    - 50,000 MINA : Production of the library
    - 10,000 MINA : Documentation
    - 10,000 MINA : Production of the three examples above mentionned

- **Wallet Address:** 
    - B62qpc15dgfgxyJNSeETCvB7Pf16cgBL7z7oNML45vzgyZCQAwTygm9



## Team Info
This section provides details about team.

-  **Proposer Github**: https://github.com/YofiY
- **Proposer Experience**:
    - EPFL graduate pursuing a master's degree in Theoretical Computer Science at ETH Zurich.
-  **Team Members**: Yofi
-  **Achievements**: 
    - won the 2nd place for the Mina track building the ZK Dice Game (https://github.com/YofiY/zk-dice-roll), during Lambda Hack Week in Brussels.
    - won the 3rd place for the general track of ZkHack Montréal building a proof-of-location app https://github.com/remicolin/zalileo

## Risks & Mitigations
- What risks or dependencies do you foresee with building this project ?
    - One possible technical risk is that the proving time might incur some delay between interactions. 
- In general state channels present some issues such as:
    - liveness : what happens if the connection between the peers drops ? 
    - Data availability : Bob's hardrive may have a mechanical failure ?
    - Griefing attacks : An attacker may want to grief bob by having dispute settled.
- What are your migtigations if any?
    - Intricate specification of the settlement process.