# Master Node HotWallet (Linux VPS)

### Description

## 1:  Download Putty

  Putty is a well known communications program.  We will using Putty to connect to the VPS via SSH protoocol.
  Download Putty from their website https://www.putty.org/
  
## 2:  Get Your VPS (Digital Ocean)

  This guide is using Digital Ocean but Vultr is very popular also.
  Goto https://www.digitalocean.com/ and sign up.
  
  Navigate to the Dashboard and click `<Create>` button.
  
  Select `<Droplet>`
  
  ![alt text](https://github.com/FerrumCommunity/Ferrum-Guides/blob/master/Hot_Wallet_Linux%20VPS/DO-1.PNG)
  
  Select 
  
   * `Ubuntu` 
   * `1Gig $5`
   *  Any Data Centre
   * `Monitoring` option
   * choose a host name eg "Ferrum.MasterNode.01"
  
  Click the `<Create>` button
  
    
  ![alt text](https://github.com/FerrumCommunity/Ferrum-Guides/blob/master/Hot_Wallet_Linux%20VPS/DO-2.PNG)
            
  
## 3:  Putty Login

  Launch Putty
  
  Digital Ocean will send you an email with the IP address and password for your VPS.
  
  Paste the IP address into Putty and make sure SSH is selected.
  
  Click `<Open>`
  
  
  ![alt text](https://github.com/FerrumCommunity/Ferrum-Guides/blob/master/Hot_Wallet_Linux%20VPS/DO-3.PNG)
  
  
  When you first connect to a new IP address you will get the following Warning.
  
  Click `<Yes>`
  
  
  ![alt text](https://github.com/FerrumCommunity/Ferrum-Guides/blob/master/Hot_Wallet_Linux%20VPS/DO-4.PNG)
  

  As in the image below you will use `root` as the login.
  
  You copy and paste the password from the email Digital Ocean sent you.
  
  For windows users, to paste into Putty, a **single RIGHT click** will paste.  You will not see anything happen.
  
  Press `<Enter>` 


  ![alt text](https://github.com/FerrumCommunity/Ferrum-Guides/blob/master/Hot_Wallet_Linux%20VPS/DO-6.PNG)
  

  You should be logged in now.  Digital Ocean VPS insist that you change passwords straight away.
  
  Paste the same password next and `<Enter>` It will prompt you twice for a new password.
  
  When you're done it should look like this.
  
  
  ![alt text](https://github.com/FerrumCommunity/Ferrum-Guides/blob/master/Hot_Wallet_Linux%20VPS/DO-8.PNG)
  
  
  ## 4:   Create Script File
  
  The next step is to create the installation script file.
  (Windows users will **hate** the nano text editor)  Don't stray from the instructions and you should be right.  *FYI Do not use the mouse to move the cursor and do not use the Numeric keypad of the keyboard.*
  
  copy `nano /root/mnscript.sh`
  
  Single Right click to paste onto the command line and `<Enter>`
  
  Then copy the following
  
  ```
  sudo apt-get update
sudo apt-get upgrade -y
sudo apt-get install wget nano unrar unzip libboost-all-dev libevent-dev software-properties-common -y
sudo add-apt-repository ppa:bitcoin/bitcoin -y
sudo apt-get update
sudo apt-get install libdb4.8-dev libdb4.8++-dev -y

sudo fallocate -l 1500M /mnt/1500MB.swap
sudo dd if=/dev/zero of=/mnt/1500MB.swap bs=1024 count=1572864
sudo mkswap /mnt/1500MB.swap
sudo swapon /mnt/1500MB.swap
sudo chmod 600 /mnt/1500MB.swap
sudo echo '/mnt/1500MB.swap  none  swap  sw 0  0' >> /etc/fstab

sudo ufw allow 22/tcp
sudo ufw limit 22/tcp
sudo ufw allow 49046/tcp
sudo ufw logging on
sudo ufw --force enable

sudo apt-get install libzmq3-dev libminiupnpc-dev -y

wget https://bitbucket.org/FerrumCommunity/ferrumdownload/downloads/ferrum.zip

unzip ferrum.zip
rm ferrum.zip
chmod +x ./ferrum/src/ferrumcoind
sudo mv ./ferrum/src/ferrumcoind /usr/local/bin
cd ~
ferrumcoind
  ```
  
  Single right click to paste the above into the editor.
  
  
  ![alt text](https://github.com/FerrumCommunity/Ferrum-Guides/blob/master/Hot_Wallet_Linux%20VPS/DO-10.PNG)
  

  Press `<Ctrl> + <x>` 
  Press `<Y>`
  Press `<Enter>`
  
  
## 5:   Execute Script


   Copy and paste each of follwing lines and `<Enter>` 
   `chmod 740 mnscript.sh` 
   `./mnscript.sh`
   
   
  
