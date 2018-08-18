Obsidian QT wallet docker
=========================
[![Build Status](https://travis-ci.org/chrishasl/obsidian-qt-docker.svg?branch=master)](https://travis-ci.org/chrishasl/obsidian-qt-docker)

Easily provision an [Obsidian](https://obsidianplatform.com/) wallet on a VPS.

## Docker build and run
```
docker build -t odn-qt-wallet .
docker run --rm -d -v ~/odn-wallet/wallet.dat:/root/.obsidian/wallet.dat --name=odn-qt-wallet odn-qt-wallet
```

## Wallet setup
```
docker exec odn-qt-wallet obsidiand encryptwallet **YOUR_SECRET_PASS**
```
(encrypting the wallet for the first time causes obsidiand to stop, and `docker run` ran again from the first step)


## Commands
Unlock your wallet for staking: 
```
docker exec odn-qt-wallet obsidiand walletpassphrase YOUR_SECRET_PASS 999999 true
```

Generate an ODN address:
```
docker exec odn-qt-wallet obsidiand getaccountaddress 0
```
