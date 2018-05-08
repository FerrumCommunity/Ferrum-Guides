# Windows Cold Wallet Setup

## Description.

The Ferrum Controller wallet, also called the Cold wallet is so called because

* a:) It controls the Master Node, and holds the collateral (2500 FRM per master node).
* b:) Its referred to as cold because unlike the Master Node wallet, this wallet may be shutdown once the master node has been started .

## Step One - Collateral.

* 1: Don't Encrypt wallet until you are happy that the Masternode is running.

     Download the Ferrum windows wallet, ferrumcoin-qt.exe from 
     https://bitbucket.org/FerrumCommunity/ferrumdownload/downloads/ferrumcoin-win-1.2-qt.zip
     
* 2: Create a new receiving address. Give it a name (label) like MN01.  Its not a bad idea to edit the name of the existing address  to something like Landing (or mining).

* 3: When buying FRM to setup a Master Node it is neccesary to obtain at least 2501 to allow for transactional costs.

  ![alt text](https://github.com/FerrumCommunity/Ferrum-Guides/blob/master/Windows%20Cold%20Wallet/ColdWallet_newAddress.PNG)

* 4: **If you already have a Master Node running off this wallet goto Step 4B.**
     Send **EXACTLY 2500 FRM** to the Master Node address (in this case MN01)
     
     ![alt text](https://github.com/FerrumCommunity/Ferrum-Guides/blob/master/Windows%20Cold%20Wallet/ColdWallet_sendCollateral.PNG)

* 4B **If this is going to be the second or more Masternode off this wallet.**

* 5:  The wallet will look like the image below.  Now wait until at least 10 confirmations. 

   ![alt text](https://github.com/FerrumCommunity/Ferrum-Guides/blob/master/Windows%20Cold%20Wallet/ColdWallet_CollateralReceived.PNG)

* 6: **Generate private key & transaction Id, index**
     
     Click on `<Help>` then `<Debug Window>` then `<Console>` Tab.
     
     In the console type
     
     ```masternode genkey```
     
     Then type
     
     ```masternode outputs```
     
    It should look like the image below.  If it doesn't you have done something wrong.
    
    ![alt text](https://github.com/FerrumCommunity/Ferrum-Guides/blob/master/Windows%20Cold%20Wallet/ColdWallet_genkey.PNG)
    
    This will give 3 items of information:
    * a:  Master Node private key.  (keep this private)
    * b:  Transmission Id of the collateral transmision (you sent earlier).
    * c:  Transmission Index (always 0 or 1)
    
    You should copy these into a notepad file for convience as you'll need these later.  You should also keep a record of these            numbers.
    
 * 7 **Edit masternode.conf**
 
     To create masternode.conf file it is easier to 
     
     click on `<Masternodes>` then `<My Master Nodes>` tab then press `<Create>` button.
     
     Enter the following items  (refer to image below):
     * 1: Alias, not critical, just some descriptive name for this masternode.
     * 2: Address, this is the IP address (plus :49046) for your VPS given to by Digital Ocean etc.
     * 3: Masternode private key. (from the masternode genkey instruction)
     * 4: Transaction Id. (from the masternode outputs instruction)
     * 5: Transaction Index. Will be 0 or 1. (from the masternodes outputs instruction)
     
 ![alt text](https://github.com/FerrumCommunity/Ferrum-Guides/blob/master/Windows%20Cold%20Wallet/ColdWallet_initialMasternodeConf.PNG)
 
* 8: **Re-Start**
    Close the Ferrum wallet program, wait for it finish closing, then restart the wallet.
    
    Now it is time to complete the Master Node HOT wallet on your VPS.
    
* 9: **Start Masternode**
      With the Master Node on the VPS syncronised and running, it need to be started.
      click `<MASTERNODES>` then `<My Master Nodes>` 
      Select the masternode you are starting.
      Click the `<Start>` button.
      ![alt text](https://github.com/FerrumCommunity/Ferrum-Guides/blob/master/Windows%20Cold%20Wallet/ColdWallet_start.PNG)
      
      
