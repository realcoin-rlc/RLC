What is RealCoin (REA) ?
===

* Real-Coin (REA) is a digital currency that enables instant payments to anyone, anywhere in the world. 
* It uses different key features technology to operate with no central authority allowing everyone to operate the way they want to.
* Realcoin has a "undefined":1 parity with Romania’s currency (RON), which means it’s protected against price volatility.
* Each "undefined" REA units are backed by 1 RON in the RealCoin platform’s reserve account, and this way each "undefined" RealCoin is 100 percent backed by real assets. 
* Regardless of the changes that appear on the crypto market, "undefined" REA will always be equal to 1 RON.

This software is the REA client.
It downloads and stores the entire history of REA transactions; depending on the speed of your computer and network connection, the synchronization process could take a day or more once the blockchain has reached a significant size.

---
Coin properties:
---
```
Source branch - 3.3
Algorithm - SHA256CSM
Block type - Proof-of-Work/Proof-of-Stake
Coin name - RealCoin
Coin abbreviation - REA
Address letter - R
Address letter testnet - Q
RPC port - 26913
P2P port - 26914
Block reward - 10 coins
Block reward (PoS) - 4 coins
Coin supply - 100.000.000 coins
Premine amount - 20.000.000 coins
```

---
Advanced properties:
---
```
Last PoW block - 8.000.000
Superblock reward - 10%
Masternode reward - 40%
Masternode amount - 10.000 coins
Masternode confirmations - 15 blocks
Coinbase maturity - 20 ( + 1 default confirmation) blocks
Target spacing - 2 minutes
Target timespan - 10 minutes
Transaction confirmations - 6 blocks
```

---
Security Warnings
---

**REA is experimental and a work-in-progress.** Use at your own risk.

---

Building
---

### Update your Ubuntu machine.

```
$ sudo apt-get update
$ sudo apt-get upgrade
```
### Install the required dependencies.

```
$ sudo apt-get install build-essential libtool autotools-dev automake pkg-config libssl1.0-dev libevent-dev bsdmainutils python3 curl libboost-system-dev libboost-filesystem-dev libboost-chrono-dev libboost-test-dev libboost-thread-dev libboost-all-dev libboost-program-options-dev libminiupnpc-dev libzmq3-dev libqt5gui5 libqt5core5a libqt5dbus5 qttools5-dev qttools5-dev-tools libprotobuf-dev protobuf-compiler libqrencode-dev unzip libgmp3-dev
```

### Install Berkeley DB.

```
$ sudo add-apt-repository ppa:bitcoin/bitcoin
$ sudo apt-get update
$ sudo apt-get install libdb4.8-dev libdb4.8++-dev
```

### Build Linux/MAC

Ensure you have successfully installed all system package dependencies as described above. Then run the build, e.g.:
```
$ git clone https://github.com/realcoin-rea/rea.git
$ chmod -R +x rea/
$ cd rea
$ ./autogen.sh
$ ./configure --with-incompatible-bdb
$ make
```

This should compile our dependencies and build `realcoind`

---

How do I enable staking?
---
* Use the following instructions to enable staking in your wallet.
* Open your wallet, and make sure you are connected to another wallet.
* You are connected if you see the icon Wallet connections REA in the lower right corner of your wallet.
* Leave your wallet open and unlocked to stake.
* Keep in mind that stake can only be generated when you have a balance in your wallet.
* The following only applies if you encrypted your wallet.
* You can unlock your wallet to stake using the following instructions.

1) Go to Settings > Unlock Wallet.
2) Tick the “For anonymization and staking only” option.
3) Enter your passphrase.
4) Click the button OK.
---

How do I mine a block?
---
* Use the following instructions to mine a block.
* Open your wallet, and make sure your wallet is connected with a node.
* Your wallet is connected when you see the icon Wallet connections REA in the lower right corner of your wallet.
1) Go to Help.
2) Click Debug Window.
* This is the console where you will execute all commands.
3) Type this command to start mining your first block:
```
setgenerate true -1
```
* If you want to use a specific number of CPU cores, instead of -1, type the number of cores.
* You can type the following command to see the status of generation.
```
getmininginfo
```
* It will take about +/- 5 minutes to mine your first block, depending on your computer hardware.
---

How do I setup a masternode?
---
* Use the following instructions to setup a masternode for REA on Ubuntu Server 18.04.
* Create the config file.
```
mkdir $HOME/.realcoin
nano $HOME/.realcoin/realcoin.conf
```
* Paste the following lines in realcoin.conf.
```
rpcuser=rpc_realcoin
rpcpassword=kuw05sqio7bcm8z96o7redv17xws1lw6xpd1qf33
rpcallowip=127.0.0.1
listen=1
server=1
daemon=1
maxconnections=64
masternode=1
masternodeprivkey=
externalip=REPLACE_WITH_EXTERNAL_IP_OF_VPS
```
* Leave the fields “masternode” and “masternodeprivkey” commented out.
* Replace the text “REPLACE_WITH_EXTERNAL_IP_OF_VPS” with the external IP address of your VPS.

E.G. externalip=136.144.171.201

* Start your node with the following command.
```
realcoind
```
* Wait until the daemon has finished downloading the blockchain.
* Send the collateral (10000)
* Open your wallet and wait until your wallet has downloaded the blockchain.

1) Go to “Tools”.
2) Click “Debug console”.
This is the console where you will execute all commands.

* Create a new masternode private key.
```
createmasternodekey
```
* Example output
```
7VatfYVk5fFMTymPDhgSURAESDACJhWpd89WHGoh35d9fbLQPj5
```
* Show your collateral address.
```
getaccountaddress "MN1"
```
* Example output
```
TDC99hZmSmYEcBu4WcxA2TCT6KBqHB6Hos
```
* Transfer the required amount of coins (10000) to the “collateral address” that you created using the command “getaccountaddress "MN1"”.
* Wait until the transaction has the required masternode confirmations (15).
* Go to “Tools”.
* Click “Debug console”.
* Enter the following command.
```
getmasternodeoutputs
```
* Example output
```
  {
    "txhash": "506a242ccbfd2555bcd9cff5f4041752c911f39cb2905acc83ccfe0cf8808df9",
    "outputidx": 1
  }
```

1) Go to “Tools”.
2) Click “Open Masternode Configuration File”.
3) Modify the following line and paste it into notepad.

MN1 136.144.171.201:9999 7VatfYVk5fFMTymPDhgSURAESDACJhWpd89WHGoh35d9fbLQPj5 506a242ccbfd2555bcd9cff5f4041752c911f39cb2905acc83ccfe0cf8808df9 1

* MN1 - Alias for your masternode.

136.144.171.201 - External IP address of your VPS.

9999 - Replace with P2P port of RealCoin (26914).

7VatfYVk5fFMTymPDhgSURAESDACJhWpd89WHGoh35d9fbLQPj5 - Masternode private key from the command “createmasternodekey”.

506a242ccbfd2555bcd9cff5f4041752c911f39cb2905acc83ccfe0cf8808df9 - Value “txhash” from the command “getmasternodeoutputs”.

1 - Value “outputidx” from the command “getmasternodeoutputs”.

4) Save the file and close notepad.
5) Close your wallet.
* Register your masternode
* Place the masternode private key in the config file of your masternode and uncomment the values “masternode” and “masternodeprivkey”.

### Example config:
```
rpcuser=rpc_realcoin
rpcpassword=kuw05sqio7bcm8z96o7redv17xws1lw6xpd1qf33
rpcallowip=127.0.0.1
listen=1
server=1
daemon=1
maxconnections=64
masternode=1
masternodeprivkey=7VatfYVk5fFMTymPDhgSURAESDACJhWpd89WHGoh35d9fbLQPj5
externalip=136.144.171.201
```
* Restart your masternode using the following commands.
```
realcoin-cli stop
realcoind
```
1) Open your wallet.
2) Go to “Settings”.
3) Click “Unlock Wallet”.
4) Enter your wallet passphrase and unlock your wallet.
5) Go to “Tools”.
6) Click “Debug console”.
7) Start your masternode using the command.
```
startmasternode alias false MN1
```
* Your masternode is now registered and will appear in the masternode list.
* You can check the status of your masternode using the command "getmasternodestatus".
```
realcoin-cli getmasternodestatus
```
* Example output
```
{
  "txhash": "506a242ccbfd2555bcd9cff5f4041752c911f39cb2905acc83ccfe0cf8808df9",
  "outputidx": 1,
  "netaddr": "136.144.171.201:9999",
  "addr": "TDC99hZmSmYEcBu4WcxA2TCT6KBqHB6Hos",
  "status": 4,
  "message": "Masternode successfully started"
}
```

---

### Need Help?

* Ask for help on the [REA](https://discord.gg/cxCeTNcRTm) discord channel.
---
