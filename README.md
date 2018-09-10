# Galatium
Shell script to install a [Galatium Masternode](https://www.galatium.org/) on a Linux server running Ubuntu 14.04 or 16.04. Use it on your own risk.

***
## Installation:
```
git clone https://github.com/gltproject/glt-install/
cd glt-install
bash glt-install.sh
```
***

## Desktop wallet setup

After the MN is up and running, you need to configure the desktop wallet accordingly. Here are the steps for Windows Wallet
1. Open the Galatium Coin Desktop Wallet.
2. Go to RECEIVE and create a New Address: **MN1**
3. Send **1000** **Galatium** to **MN1**.
4. Wait for 15 confirmations.
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
* Output index:  **Second value from Step 6**
9. Save and close the file.
10. Go to **Masternode Tab**. If you tab is not shown, please enable it from: **Settings - Options - Wallet - Show Masternodes Tab**
11. Click **Update status** to see your node. If it is not shown, close the wallet and start it again. Make sure the wallet is unlocked.
12. Open **Debug Console** and type:
```
startmasternode "alias" "0" "MN1"
```
***

## Usage:
```
galatium-cli getinfo
galatium-cli mnsync status
galatium-cli masternode status
```
Also, if you want to check/start/stop **Galatium** , run one of the following commands as **root**:

**Ubuntu 16.04**:
```
systemctl status Galatium #To check the service is running.
systemctl start Galatium #To start Galatium service.
systemctl stop Galatium #To stop Galatium service.
systemctl is-enabled Galatium #To check whetether Galatium service is enabled on boot or not.
```
**Ubuntu 14.04**:  
```
/etc/init.d/Galatium start #To start Galatium service
/etc/init.d/Galatium stop #To stop Galatium service
/etc/init.d/Galatium restart #To restart Galatium service
```
***
