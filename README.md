# TxQuick Proof-of-Reserves

Welcome to the TxQuick Proof-of-Reserves audit tools.  This document explains the TxQuick Proof of Reserves system, and the accompanying tools which we provide to make it easy for our clients to participate.

## Table of Contents

- [Proof-of-Reserves](#txquick-proof-of-reserves)
    - [Table of Contents</strong>](#table-of-contents)
    - [Released Audit Assessments](#released-audit-assessments)
    - [Background](#background)
    - [Getting Started As A TxQuick Client](#getting-started-as-a-txquick-client)
    - [Client Participation Overview](#client-participation-overview)
    - [Full Audit Process](#full-audit-process)
    - [Technical Background](#technical-background)
    - [Installation](#installing-this-software-yourself)
    - [Usage](#usage)
    - [Credits](#credits)
    - [License](#license)

## Released Audit Assessments

| Proof Id | Date | Audit Organization | Status |
| ---------- | ------ | ------------------------ | -------- |
| TBD          | TBD           |               | WIP      |


## Background

One of the core problems with cryptocurrency exchanges such as MtGox, WeExchange, BitFunder, and QuadrigaCX is transparency. All were operating as fractional reserve exchanges for a long period of time and subsequently collapsed.

Customers need a way to confirm that the service they are using does in fact hold 100% of their funds and is not insolvent. Hence, developers in the crypto community have come up with the idea to utilize sha256 hashes and use a Merkle Trees approach to give customers the ability to verify their funds are fully represented in a set of exchange-provided public balance data.

Previous implementations of Proof of Reserves systems were too difficult for non-techies to use, reducing the ability of customers to participate. TxQuick has fine tuned these concepts to make it as easy as possible to participate in our Proof of Reserves process because we believe the integrity of the process depends on having as many participants as possible.

## Getting Started As A TxQuick Client

If you want to dive right in, you can start by browsing to one of the Participating Verification Websites:

[TxQuick - Proof of Reserves](https://txquick.com/proof-of-reserves) 
[Quadriga Initiative](https://quadrigainitiative.org/proof-of-reserves) (coming soon)

Then follow the instructions provided.

## Client Participation Overview

### STEP 1 - Copy your Proof Sentence from the TxQuick website

Log into your TxQuick account and browse to [Account], [Proof of Reserves]. (https://ca.txquick.com/account/profile/proofOfReserves) On that page you can see a list of all of the audits that have been done and your Proof Sentence for each audit. Copy your Proof Sentence from the Proof of Reserves audit you want to participate in, then paste it in the field below. If it is a valid Proof Sentence, we will automatically detect what file we need to load. 

   <p align="center"> 
    <img src="images/userdata.png" style="width:600px;"/>
   </p>

### STEP 2 - Verify you were included in the Proof of Reserves File

After you have pasted your Proof Sentence into the Verification Website, click the "Load Audit File" button.  The tool will download the Proof of Reserves file from GitHub. After the Audit File is loaded, next click the "Run Verification" button.

   <p align="center">
    <img src="images/validate.png" alt="" style="width:600px;"/>
   </p>

You should see a successful result looking something like this:

   <p align="center">
    <img src="images/validate2.png" alt="" style="width:600px;"/>
   </p>

And further down on the page you should see verification of the Merkle Proof Result as well:

   <p align="center">
    <img src="images/validate3.png" alt="" style="width:600px;"/>
   </p>

That's it!

## Full Audit Process

### PART 1 - (Trusted Third Party / Auditor Tasks) Proof of Liabilities

#### STEP 1(A): A trusted third party (typically in the role of an auditor) generates the Merkle Tree with data provided by TxQuick.

TxQuick provides the trusted third party with the GitHub link to download anonymous details of user data and user balances on a per-token basis.  Every download of audit data from the exchange platform generates a unique "Proof Id", which can be used to reference each unique Merkle Tree Proof throughout the process. The trusted third party then imports the downloaded CSV file into root-hash-generator.html to generate an audit report, including the total balances and the Merkle Tree Root Hash.

   <p align="center">
    <img src="images/root-hash-generator.png" alt="" style="width:600px;"/>
   </p>

#### STEP 1(B): The auditor verifies the total user balances and publishes the merkle tree and root hash

After the Merkle Tree is successfully generated in root-hash-generator.html, its root hash together with user count and total amount of user balances will be calculated and displayed to the trusted third party for verification.

The leaves of the Merkle tree will be saved in a plain text file, which will be publicly shared to customers via this GIT repository, allowing all users to verify their account balances are properly represented.

#### STEP 1(C): The trusted third party publishes a table of the Assets, Proof Id's, and the Merkle Tree hashes for each Proof

The trusted third party now must independently publish the resulting data from their audit process, this should include a table indicating each asset audited, it's Proof Id, and the resulting Merkle Tree Root Hash. Following this publication, the trusted third party will provide TxQuick with the generated Merkle Tree proof file for publication to the TxQuick GIT repository. 

### PART 2 - (Independent And Optional TxQuick User Tasks) Proof of Liabilities

#### STEP 2(A): Users collect their Proof Sentence from the TxQuick website

Users wishing to verify their balance is represented in the Merkle Tree will need to log into their TxQuick account, browse to their account Proof of Reserves page, and look up their Proof Sentence as of the time that Merkle Tree Proof was created.

   <p align="center"> 
    <img src="images/userdata.png" style="width:600px;"/>
   </p>

#### STEP 2(B): Users download and install this software

Users wishing to run their own in-depth proof may download, inspect, install, and run this software from their local desktop, or optionally use one of the Participating Verification Websites listed above. We recommend using either this software directly or using one of the 3rd party verification sites rather than the TxQuick site because we could theoretically alter it on our servers, and thus it is better if you are able to run the proof somewhere outside our control.

#### STEP 2(C): Users independently verify their account balances are represented

Finally users must open index.html in their browser. Then the user must input their own Proof Sentence and follow the instructions to run the verification process. If the user data and balance provided matches the record in the Merkle Tree, a successful result will be displayed together with the node location of the user information within the Merkle tree. The Merkle Tree's root hash will be re-calculated using the imported file so that the user can verify the root hash and compare it to the root hash the trusted third party published in Step 1(C) above to ensure the correctness and completeness of the Merkle Tree.

   <p align="center">
    <img src="images/validate.png" alt="" style="width:600px;"/>
   </p>

### PART 3 - (All Participants) Proof of Assets

#### STEP 3(A): The public and/or trusted third party identifies and verifies TxQuick owned blockchain wallets

TxQuick provides the public with the blockchain addresses used to store customer assets. TxQuick provides these addresses publicly at https://ca.txquick.com/walletStatus. To prove TxQuick owns the blockchain addresses in question, the public and a trusted third party may periodically observe TxQuick conducting transactions moving small pre-determined amounts from each major wallet identified.

   <p align="center">
    <img src="images/walletstatus.png" alt="" style="width:600px;"/>
   </p>

#### STEP 3(B): The public and/or trusted third party adds up the balances all TxQuick public chain wallets

The public or a trusted third party is able to take all of the balances of the wallets owned by TxQuick and sum them all up, Coming up with a total value of each asset.

### PART 4 - (All participants) Final Proof of Reserves

#### The trusted third party proves TxQuick is not operating as a fractional reserve

The trusted third party takes the resulting sum of the value of the assets from Step 3(B), and subtracts the resulting sum of the value of the liabilities from Step 1(B). The assets should always exceed the liabilities, otherwise the exchange is operating as a fractional reserve and deposits are not fully backed.

## Technical Background

* ### What is a Merkle Tree?

In cryptography and computer science, a hash tree or Merkle tree is a tree in which every leaf node is labelled with the cryptographic hash of a string of data, and every non-leaf node is labelled with the hash of the labels of its child nodes. Hash trees allow efficient and secure verification of the contents of large data structures.

   <p align="center">
    <img src="images/merkletree.png" alt="" style="width:800px;"/>
   </p>

* ### How do you build the Merkle tree with user Proof Sentences and Balances?

The user's Proof Sentence Hash and balances are first exported from TxQuick's database. Prior to export, each Proof Sentence is hashed using sha256 so that your Proof Sentence is protect.  Then when generating the Merkle Tree and the Root Hash we combine your Proof Sentence Hash and your Balances String, hash them using sha256, and the resulting hashes are used to generate the leaf nodes of the Merkle tree. 

We then use a third party Merkle Tree library (Javascript: merkle-tools) to input all of the sha256 leaf nodes and generate the tree, visually represented in the illustration above. After the merkle tree is successfully built, the data used to build it and the final Root Hash are exported into a plain text file, which is published to GitHub for public access.

* ### How do you verifying a user's Proof Sentence and Balances using a Merkle Tree Proof?

In order to verify the Proof Sentence and Balances, we need to construct a the entire Merkle Tree and generate a Merkle Proof to verify inclusion within the Merkle Tree.

Merkle Proofs are created by starting with the sha256 hash of the Proof Sentence and Balances String combine, and then climbing up the tree until obtaining the Root Hash, which has been published to GitLab by the auditor in Step 1(C).

After re-creating the tree using the third party Merkle Tree library (Javascript: merkle-tools) you can fully climb the tree and calculate the Root Hash at the top.  If the Root Hash calculated in your proof matches the Root Hash the auditor published to GitHub, then you have proven that your Proof Sentence and Balances as represented in the Audit File were included in the same Merkle Tree the auditor used to calculate the total exchange balances.


## Installing This Software Yourself

Please reference the LICENSE prior to installation. This software is FREE to use for most parties, but not all.

> Install dependencies

  ```shell
  npm install
  ```

> Install build tool

  ```shell
  npm install -g browserify watchify
  ```

> Create bundle.js to make it runanble in browser

  ```shell
  browserify js/proof.js -o js/bundle.js
  ```

> To achieve auto build of bundle.js, use watchify as shown below, or use nohup to make watchify command running at background

  ```shell
  nohup watchify js/proof.js -o js/bundle.js -v > nohup.out 2>&1 </dev/null &
  ```

## Usage

* If you are the Auditor, you open **`root-hash-generator.html`** in your browser, import the exchange provided file with user data and user balances to build and export the Merkle Tree file.

* Users open **`index.html`** in their browser, paste their Proof Sentence, and follow the instructions to validate their Proof Sentence and balance combination exists in the Merkle Tree File.

## Credits

Th process of using Merkle Trees as a tool for Proof of Reserves is conceptually derrived from the work of many.  Development of this specific implementation utilizing Proof Sentences is the result of a collaborative effort between TxQuick and The Quadriga Initiative (https://www.quadrigainitiative.org/) as well as many long discussions with the Calgary based CryptOasis crew.

This software was created by TxQuick to provide a reference implementation and to facilitate adoption.

## License

Copyright ©2021 TxQuick Blockchain Trading Corp.

Licensed under the **[TxQuick Proof Of Reserves](LICENSE)** license. Please review the license prior to use.
