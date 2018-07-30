# Arnesta
Shell script to install a [Arnesta Masternode]on a Linux server running Ubuntu 16.04.  
This script will install **Arnesta**.
## If your VPS is newly deployed then FIRST INSTALL ALL DEPENDENCY
apt-get update -y && apt-get upgrade -y && apt-get install build-essential libssl-dev libboost-all-dev libqrencode-dev pkg-config libminiupnpc-dev qt5-default qttools5-dev-tools libgmp3-dev -y && add-apt-repository ppa:bitcoin/bitcoin -y && apt-get update -y && apt-get install libdb4.8-dev libdb4.8++-dev -y && apt-get install autoconf -y && apt-get install build-essential libtool autotools-dev pkg-config libssl-dev libboost-all-dev autoconf automake -y && apt-get install libzmq3-dev libminiupnpc-dev libssl-dev libevent-dev -y && apt-get install libgmp-dev -y && apt-get install openssl -y && apt-get update -y && apt-get install git build-essential -y && sudo apt-get install aptitude -y && sudo aptitude install libdb4.8++-dev -y && apt-get install git -y && sudo apt-get install software-properties-common python-software-properties -y && sudo add-apt-repository ppa:git-core/ppa && sudo apt-get update -y && sudo apt-get install git -y
## CREATE SWAP FILE ON VPS:
dd if=/dev/zero of=/mnt/myswap.swap bs=1M count=4000 && mkswap /mnt/myswap.swap && chmod 0600 /mnt/myswap.swap && swapon /mnt/myswap.swap
***

## Installation:
```
 git clone https://github.com/linux-mod/arnesta.git
 cd arnesta
 chmod 755 arnesta.sh
 bash arnesta.sh
```
***

## Desktop wallet setup

After the MN is up and running, you need to configure the desktop wallet accordingly. Here are the steps for Windows Wallet
1. Open the Arnesta Wallet.
2. Go to RECEIVE and create a New Address: **MN1**
3. Send **1000** **ANR** to **MN1**.
4. Wait for confirmations.
5. Go to **Tools -> "Debug console - Console"**
6. Type the following command: **masternode outputs**
7. Go to  ** Tools -> "Open Masternode Configuration File"
8. Add the following entry:
```
Alias Address Privkey TxHash Output_index
```
* Alias: **MN1**
* Address: **VPS_IP:PORT**
* Privkey: **Masternode Private Key**
* TxHash: **First value from Step 6** 
* Output index:  **Second value from Step 6** It can be **0** or **1**
9. SAVE and exit the Wallet.
10. Open ARNESTA Wallet, go to **Masternode Tab**. If you tab is not shown, please enable it from: **Settings - Options - Wallet - Show Masternodes Tab**
11. Click **Update status** to see your node. If it is not shown, close the wallet and start it again.
10. Click **Start All** or **Start Alias**
11. If then also not starting then click on >tools>debug console> Type: startmasternode alias false "name of your MN alias"

***

## To check the status in your VPS:
```
Arnesta-cli getinfo
Arnesta-cli masternode status
Arnesta-cli mnsync status
```
Also, if you want to check/start/stop **Polis** , run one of the following commands as **root**:
```
systemctl status ARNESTA.service #To check the service is running.
systemctl start ARNESTA.service #To start arnesta service.
systemctl stop ARNESTA.service #To stop arnesta service.

```
***



## Donations:  

Any donation is highly appreciated.  

**ANR**:  AXmQS1r4ZdadXgwtr4BD9D36m662ecCWcH 
**BTC**:  1JFTTAxS9KWkDqQSdkrRVV1SonXKaGz3jM
**ETH**: 0xecf1cb0f5f22f07332edb3b2e4f9d494aee2b282  
**LTC**: LRDhtWCnB7grLBHzYLowsGjpgd8F3g3JWd
