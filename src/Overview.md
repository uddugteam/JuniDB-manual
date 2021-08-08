* **Project Name:** JuniDB
* **Team Name:** Uddug
* **Payment Address:** 0xc45eAd98E95D1962133d9c15847e2EA4E16dfD0b

## Project Overview

### Overview

It's a very highload action to store large amounts of data on-chain. The most-common and useful solution for decentralised apps is to use IPFS as a data storage and store on-chain only hashes. Our team inspired by the OrbitDB will focus on the scalability, decentralised, easy-learning solution for substrat developers that want to manipulate big amounts of data easily.
#### Key advantages

* **Usability** - just integrate and code
* **Security** - built-in encryption
* **Scaling** - ready for changes and big data

#### Available  storage data types

* **Key-value** - simple key-value storage
* **Hash** - hash storage like Redis hash

#### Motivation

Working a lot with blockchain technologies, our team found that it’s data-driven, and thus there are rapidly growing interests in integrating them for more secure and efficient data storage and sharing.We are convinced that blockchain technologies change the world, and have been working hard to create more transparent solutions. We designed and built core infrastructure for decentralised projects.

We have been observing and learning Substrate technologies and find Polkadot as the best ecosystem for us to join depending on technology and strong market position. We believe that our protocol will be useful for other projects in the Polkadot ecosystem.

### Project Details
Substrate pallet provides a configurable database module allows to store and  manipulate a big amount of data. Pallet works as an offchain worker and connect data between blockchain and ipfs via offchain::worker.

#### Encryption module
Built-in encryption module allows to create a secure database and encrypt all data before its uploading to the database with user account keys. With enabled encryption only account users have access to the database. Data could be decrypted via Web-application after receiving. Module is based on asymmetrical cryptography and uses an account public key to encrypt data on the blockchain side and a private key to decrypt data on the client side.

We plan to make it based on ed25519 crypto scheme and use [ecies-ed2551](https://github.com/phayes/ecies-ed25519) crate to implement encryptions on backend side.

![scheme A](https://i.postimg.cc/gJds3kj9/encryption.png)

- receive data by RPC request
- Encrypt data by account public key
- Insert encrypted data into ipfs via offfchain::ipfs
- Insert received ipfs hash into storage

![scheme B](https://i.postimg.cc/Y9h66G7s/decryption.png)

- catch request to get data by RPC request
- get ipfs hash from storage
- fetch encrypted data from ipfs via offchain::ipfs
- receive encrypted data in RPC response
- decrypt data using user account private key via app ddecryption module

#### Technical stack

* **Rust** - main language

* **Substrate** - blockchain framework

* **Substrate-front-end-template** - web-app template

* **Offchain::ipfs** - substrate-ipfs bridge

* **IPFS** - data storage

* **ecies-ed25519** - encryption crate

#### Public Methods
* **KeyValueInit(name)** - initialise new keyValue database
* **KeyValueSet(key, value)** - set given value in keyValue database
* **KeyValueGet(key)** - get value for given key
* **KeyValueDel(key)** - delete value from keyValue database
* **KeyValueAll()** - fetch all values from keyValue database

* **HashInint(name)** -  initialise Hash database
* **HashCreate(hashName)** - create new empty cash
* **HashSetField(hash, field, value)** - set hash field with given value
* **HashGetField(hash, field)** - get hash field
* **HashDelFied(hash, field)** - delete field from hash
* **HashAll(hash)** - get all hash fields

#### Storage
* **Data Map** - mapping ipfs hashes and data keys
* **Key-value** - database meta info

#### Scheme 1. Palett structure
![scheme C](https://i.postimg.cc/Hn1nkxGD/pallet.png)

##### Data uploading

- Rpc/wss request to pallet to insert data
- Validating data based on database schema
- Formatting data
- Encrypted (if needed)
- Store to ipfs via offchain::ipfs
- Retrieving ipfs hash with data
- Store ipfs hash into pallet storage

##### Data retrieving
- RPC/wsss request to pallet to fetch get data
- Validating data query
- Get ipfs hash from storage
- Fetch data from ipfs via offchain::ipfs
- Return data object in response

#### Scheme 2. Interaction with Substrate
![scheme D](https://i.postimg.cc/1zzJvmjQ/scheme.png)

#### Infrastructure
Testing substrate nodes with offchain::orbitDB pallet orchestrated by kubernetes cluster deployed on GCP.
#### Ci/Cd
Ci/Cs organized by github actions
#### Frontend
Simple SPA web application powered by react and polkadot.js. Using for testing purposes.

### Ecosystem Fit

Pallet is suitable for substrate developers and strives to become a complex solution for data storage and manipulation.

We expect that the project will be useful for the Web3 community.









