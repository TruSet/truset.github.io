# TruSet Developer Resources

[Truset.com](https://truset.com) is an application that incentivizes accurate collection of data.  It runs on a distributed ledger and allows people to directly collaborate on data accuracy by connecting to the ethereum blockchain.

TruSet has a few different data collection communities, for example - we gather data on [tokens](https://tokens-beta.truset.com) and [real estate](https://realestate.truset.com).  These deployments are quite similar and mostly differ by the data model relevant to the data records.

This site is intended as a developer reference for our application, to showcase our open source work and give you an introduction to how our platform works, and how you might integrate with it.  If you are interested in working with us - get in touch!

## Open Source

We have open sourced a few aspects of our application that we believe would be useful to other people developing apps on ethereum.

- [Role Based Access Control](https://truset.github.io/bitmask-rbac/) Our role based access control (rbac) compactly manages the different roles that a user (or smart contract) might have in a family of smart contracts - allowing you to limit which functions can be called by which ethereum accounts.
  - [React RBAC interface](https://truset.github.io/bitmask-rbac/portal/) A reference implementation of an interface for viewing and managing the users in an RBAC.
  - [QBAC](https://github.com/truset/RevealerAPI/) When onboarding users, we whitelist them in a "QBAC" once they complete KYC.  Then, they can interact with the QBAC to be added to the RBAC, to get an initial allocation of ERC-20 tokens, and to get a little ether to pay for gas
  
- [Commit Reveal Voting](https://truset.github.io/commit-reveal-voting/) Our application allows people to cast votes on the accuracy data that are later tallied to determine what data should be validated, and how rewards will be distributed.  Because blockchains are inherently public and we don't want people to bias their votes based on how other people vote, we needed a scheme wherein people could commit their votes - keeping the vote secret - and then later reveal them.

- [Commit Reveal Delegated Reveal](https://github.com/truset/RevealerAPI/) To simplify the commit/reveal process for our users, we allow them to delegate the reveal of votes to this service, so that they don't have to come back to the application to reveal their votes when the poll closes.

## Data Organization
TruSet captures data by deploying a smart contract per data record (ie token data, or real estate jurisdiction).  This smart contract allows people to publish data and manages the reward with our ERC-20 contribution token

The smart contract address is thus the unique id for referencing a data record.

For instance, this api url has data on the Maker token, `0x2Cb7E2...` is the [TruSet smart contract](https://rinkeby.etherscan.io/address/0x2Cb7E247c4691D35D6C47771f99D09deEb2b7f04) for the data collection

[http://tokens-beta-api.truset.com/api/v0.1/data/0x2Cb7E247c4691D35D6C47771f99D09deEb2b7f04](http://tokens-beta-api.truset.com/api/v0.1/data/0x2Cb7E247c4691D35D6C47771f99D09deEb2b7f04) 

And this would be the corresponding url for viewing the data on the react app (dApp)

[https://tokens-beta.truset.com/data/0x2Cb7E247c4691D35D6C47771f99D09deEb2b7f04](https://tokens-beta.truset.com/data/0x2Cb7E247c4691D35D6C47771f99D09deEb2b7f04)

The data for each record is further organized by data section.  Ie, the nesting “/listings” corresponds to an array of exchanges where the token is listed, and the symbol on that exchange.  Under the hood, we index these sections by data identifiers, which in this case would be `sha3(“/listings”)`.
