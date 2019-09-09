## TruSet developer resources

[Truset.com](https://truset.com) is an application that incentivizes accurate collection of data.  It runs on a distributed ledger and allows people to directly collaborate on data accuracy by connecting to the ethereum blockchain.

TruSet has a few different data collection communities, for example - we gather data on [tokens](https://tokens-beta.truset.com) and [real estate](https://realestate.truset.com).  These deployments are quite similar and mostly differ by the data model relevant to the data records.

This site is intended as a developer reference for our application, to showcase our open source work and give you an introduction to how our platform works, and how you might integrate with it.  If you are interested in working with us - get in touch!

## Open Source

We have open sourced a few aspects of our application that we believe would be useful to other people developing apps on ethereum.

- [Role based Access Control](https://truset.github.io/bitmask-rbac/) Our role based access control (rbac) compactly manages the different roles that a user (or smart contract) might have in a family of smart contracts - allowing you to limit which functions can be called by which ethereum accounts.  Also provide a reference implementation of a [rbac interface](https://truset.github.io/bitmask-rbac/portal/) for viewing and managing the users in an rbac.

- [Commit Reveal voting](https://truset.github.io/commit-reveal-voting/) Our application allows people to cast votes on the accuracy data that are later tallied to determine what data should be validated, and how rewards will be distributed.  Because blockchains are inherently public and we don't want people to bias their votes based on how other people vote, we needed a scheme wherein people could commit their votes - keeping the vote secret - and then later reveal them.

- [Commit Reveal Delegated Reveal](https://github.com/truset/RevealerAPI/) To simplify the commit/reveal process for our users, we allow them to delegate the reveal of votes to this service, so that they don't have to come back to the application to reveal their votes when the poll closes.
