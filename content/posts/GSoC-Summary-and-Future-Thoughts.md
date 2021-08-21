---
title: "GSoC Summary and Future Thoughts"
date: 2021-08-22T00:49:02+05:30
draft: false
---

## Datalad and git-annex with IPFS as remote
### Why is DataLad important?
Modern science is characterized by heavy reliance on empirical data, which has led to a dramatic increase in the creation of data resources. The past few decades have seen major improvements in the ability to share these data resources for collaboration. But the accessibility is far from ideal - data is largely siloed in disconnected warehouses with incompatible interfaces. Interoperability is still just a dream in the minds of most scientists. 

Even when the data becomes available, there is usually no version control for informing customers about data updates. This leads to a lot of friction for researchers and peer reviewers and does not allow citizen scientists and hobbyists to even take part.

Traditional storage providers have several inherent issues: 
- They are monolithic and expensive solutions that may act as a single point of failure
- This monolithic property also allows easy censoring (location-based or otherwise)
- Further, several simultaneous downloads lead to bandwidth limits, making
downloads of large datasets time-consuming, expensive, and ultimately impractical.

The Interplanetary File System (IPFS) protocol is an emerging web standard that offers a unified
open-source service for peer-to-peer sharing of datasets. On IPFS, multiple peers may share
components of a dataset simultaneously, offering greater bandwidth. Data is immutable, and
easily verifiable by checking the hash of the Merkle root. This enables provenance tracking of datasets, verification of authenticity, the potential for open access, and a tool against
Censorship, and towards open access.

The datalad utility enables data sharing and collaboration by providing uniform access to available data, independent of storage providers or authentication schemes. It pairs this with reliable versioning using git-annex, which allows obtaining file contents upon request.

### IPFS remote for git-annex and datalad
In order to use IPFS for git-annex storage, we need a script for a special remote that git-annex can communicate with. There was a pre-existing bash script for this, but there were problems getting it to run - once you add files to an annex on one machine, they just didn’t show up in the same repository on another machine. As part of my GSoC work, I investigated this issue.

After trying out many different angles, the solution turned out to be relatively simple. It was an issue with the way github and other git based services prioritize branches. Git-annex makes several branches to keep track of metadata, versions, and annex locations. The default branch on cloning this repository on another machine is incorrect, and changing this manually fixes the bug. Thanks to the wonderful git-annex forum members who pointed me in the right direction!

Steps to set up git-annex with IPFS remote:
- [Changed document from above PR](https://github.com/kinshukk/brainhack2020_DeSci)
- [Demo video](https://www.youtube.com/watch?v=2JV8ZpiIntY)
- [Pull Request](https://github.com/opscientia/brainhack2020_DeSci/pull/1)

Once the special remote for git-annex works, integration with datalad is simple. We just need to specify the remote to be used before we want to upload to IPFS. 

- [Document showing detailed steps](https://github.com/kinshukk/brainhack2020_DeSci/blob/main/README_datalad.md)
- [Demo video](https://www.youtube.com/watch?v=3WDMfnEFMoA)

---

## Opsci Data Wallet
In my original GSoC proposal, I had outlined an application for storage of large neuroimaging datasets. As the weeks passed, the entire Opscientia team iterated on the idea, and we decided to build a prototype so that we can gather feedback from peers.

The data wallet that we ended up implementing is a web application that has the following features:
Simple user login using an Ethereum wallet (Metamask)
Drag-and-drop file upload to IPFS storage, through Textile.io bucket API
Scientific kudos using POAP (Proof Of Attendance Protocol)

- [Github repository](https://github.com/opscientia/web3weekend-hackathon)
- [Demo Video](https://www.youtube.com/watch?v=LquRin_Dve4)
- [My commits](https://github.com/opscientia/web3weekend-hackathon/commits?author=kinshukk)

As we implemented this simple data wallet and gathered more user data, we refined our idea of the larger ecosystem of Decentralized Science tools, of which the data wallet is an integral component.

---

## Thoughts about the future
### Extending datalad
In its current form, datalad has several UX limitations. If you are a seasoned Linux user or have programming experience, using datalad via CLI feels natural. But we cannot make that assumption for the majority of scientists who can make use of the DeSci stack.

As of now, you need to run local node for using IPFS as a remote. Datalad has support for extensions, which can be used to create a REST API, which can be used inside a webapp for better UI. But even then, the above two problems persist.

Given a choice between a technically sophisticated but difficult to use tool, and a simple and extremely easy to use tool, most people will pick the latter. We need a way to reduce the barrier to entry and technical frictions in the onboarding process

### Some approaches for better UX:
- A git-annex equivalent of a tool like GitKraken (GUI based git) would be a good step towards usability
- Providing a gateway which provides API access to datalad functions will enable remote access as well as usability for non linux users. Just like you don’t need a local IPFS node to access content on IPFS (you can access via public gateways like infura, ipfs community gateway, etc.)
- This would be complex in practice, but a Python-to-JS transpiler to create a JS datalad package might be feasible. This can be combined with js-ipfs to create a web-native composable tool.
- Improving discoverability and access by integration with Ocean Protocol (Coral)

The long term aim is to make a composable building block that is easy to integrate with the larger Web3 ecosystem. For example, we would like to integrate datalad’s provenance tracking features with proof-of-publication on chain and integration with data marketplaces.

---

### QRI as a datalad alternative
QRI is a protocol for distributed dataset version control and sharing, using IPFS as the main storage layer. In QRI, raw data (assumed to be structured in tabular form - csv, json, xml, cbor) is combined with metadata, transforms, and version history of all changes to form a QRI dataset. 

Dataset search is made easy through qri.cloud - an in-house platform for making datasets public. 

##### Pros:
Metadata, analyses (transforms), structure (schema) are first class citizens along with the raw data itself, and changes to all of them is tracked in the history.
Search and discovery made easy through qri.cloud - an aggregation service.
IPFS is the default storage method. QRI clients embed an IPFS node which runs locally, pinning your datasets.
##### Cons:
Requires data to be in tabular format - this greatly limits the kinds of data we can store
There seems to be a cap (1GB) on data set sizes that can be published (This limit is only for publishing on their cloud storage, not a protocol limitation)

We cannot directly use QRI in its current form, but we can take cues for a more complete system. The concept of transforms is really powerful - the dataset comes with code bound to a dataset, which gets executed whenever there is a new commit to the dataset.

---
## To Conclude
It has been an amazing summer getting to work on such an important project with guidance by my always-helpful mentor Shady. We presented parts of the project in both the Web3Weekend Hackathon and OHBM BrainHack. It was a summer filled with learning, and I am very excited to continue working on decentralizing science with Opscientia post-GSoC.
