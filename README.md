# Mun-Blockchain Launch the Validator Node

![3A3986A5-9118-4826-B759-69DAC4FBE84B](https://user-images.githubusercontent.com/108979536/194869031-4e68b5a4-32f7-45dc-8a58-bebd978e5a54.jpeg)


𝐈𝐧𝐭𝐫𝐨𝐝𝐮𝐜𝐭𝐢𝐨𝐧 𝐭𝐨 𝐌𝐔𝐍

MUN Coin is a new cryptocurrency that is gaining buzz in the crypto community. Here’s an introduction to what it is and why you might want to consider investing. MUN Coin is a decentralized digital currency that allows for fast, secure, and anonymous transactions. It’s built on the newest blockchain technology and uses peer-to- peer networking. This means that there are no intermediaries between sender and receiver – they can transact directly with each other.

![EBFDBE6F-97BC-478D-9D15-03E62CCF8665](https://user-images.githubusercontent.com/108979536/194870596-6c66f0aa-eee4-4b4d-b811-7a3c52697637.png)

               #Alex 
            𝐇𝐞𝐚𝐝 𝐃𝐞𝐯𝐞𝐥𝐨𝐩𝐞𝐫
           
Join the team on discord
![image](https://user-images.githubusercontent.com/108979536/194872464-3608bdcc-c325-4323-814f-0991a08b6199.png)

https://discord.gg/mun

![image](https://user-images.githubusercontent.com/108979536/194873093-7c146462-78ef-4fd8-9532-90dc10ae780d.png)

https://twitter.com/munblockchain


1-𝐅𝐢𝐫𝐬𝐭𝐥𝐲 𝐨𝐩𝐞𝐧 𝐲𝐨𝐮𝐫 𝐭𝐞𝐫𝐦𝐢𝐧𝐚𝐥,𝐮𝐩𝐝𝐚𝐭𝐞 𝐲𝐨𝐮𝐫 𝐩𝐚𝐜𝐤𝐚𝐠𝐞𝐬 𝐚𝐧𝐝 𝐢𝐧𝐬𝐭𝐚𝐥𝐥 𝐭𝐡𝐞 𝐝𝐞𝐩𝐞𝐧𝐝𝐞𝐧𝐜𝐢𝐞𝐬

      sudo apt update -y
      
      sudo apt upgrade -y
      
      sudo apt full-upgrade -y
      

2-𝐈𝐧𝐬𝐭𝐚𝐥𝐥 𝐝𝐞𝐩𝐞𝐧𝐝𝐞𝐧𝐜𝐢𝐞𝐬

      sudo apt install build-essential jq -y
      
3-𝐈𝐧𝐬𝐭𝐚𝐥𝐥 𝐠𝐢𝐭

      wget -q -O - https://raw.githubusercontent.com/canha/golang-tools-install-script/master/goinstall.sh | bash -s -- --version 1.18
      source ~/.profile
      
 Check go version
 
       go version
       
 4-𝐎𝐩𝐞𝐧 𝐏𝐨𝐫𝐭𝐬
 
      apt install ufw -y
      
      sudo ufw allow ssh
      
      sudo ufw allow 22
      
      sudo ufw allow 60000:61000/tcp
      
      ufw enable (yes enter)
      
      
5-𝐒𝐞𝐭𝐮𝐩 𝐓𝐡𝐞 𝐌𝐔𝐍𝐜𝐡𝐢𝐚𝐧 (clone respository)

       git clone https://github.com/munblockchain/mun
       
      
+Go mun repository

       cd mun
  
+Install executables

       sudo rm -rf ~/.mun
       go mod tidy
       make install
       clear
       mkdir -p          ~/.mun/upgrade_manager/upgrades
       mkdir -p  ~/.mun/upgrade_manager/genesis/bin
       
+Symlink genesis binary to upgrade 

        cp $(which mund)     ~/.mun/upgrade_manager/genesis/bin
        sudo cp $(which mund-manager) /usr/bin
        
       
 6-𝐈𝐧𝐢𝐭𝐢𝐚𝐥𝐢𝐳𝐞 𝐭𝐡𝐞 𝐯𝐚𝐥𝐢𝐝𝐚𝐭𝐨𝐫
    (init)
    
    
       mund init xxxxxxxxx --chain-id testmun
       
       
  + Replace xxxxxx with your moniker name must be three words like moon-moon-moon
  
 7-𝐂𝐫𝐞𝐚𝐭𝐞 𝐚 𝐰𝐚𝐥𝐥𝐞𝐭 (wallet name can be just one word not like your moniker)
 
  
        mund keys add yyyyyyyy --keyring-backend test
       
 
 + Replace yyyyyyyyy with your wallet name like moon
 + Save all information in a notepad

8-𝐒𝐞𝐭𝐮𝐩 𝐆𝐞𝐧𝐞𝐬𝐢𝐬.𝐣𝐬𝐨𝐧 𝐚𝐧𝐝 𝐂𝐨𝐧𝐟𝐢𝐠.𝐭𝐨𝐦𝐥

   + Fetch genesis.json from genesis node: :
    
    
         curl --tlsv1   https://node1.mun.money/genesis? | jq ".result.genesis" > ~/.mun/config/genesis.json
        
        
   + Update seed in config.toml to make p2p connection:
   

          nano ~/.mun/config/config.toml 
        
        
   + Go to the P2P section and fill in the seed with the information below 
    
            "6a08f2f76baed249d3e3c666aaef5884e4b1005c@167.71.0.38:26656"
        
        
   (to save click Ctrl X and than Y enter)
   

   + Replace stake to TMUN:


             sed -i 's/stake/utmun/g' ~/.mun/config/genesis.json


9-𝐂𝐫𝐞𝐚𝐭𝐞 𝐚𝐧𝐝 𝐬𝐞𝐭 𝐭𝐡𝐞 𝐬𝐞𝐫𝐯𝐢𝐜𝐞 𝐟𝐢𝐥𝐞

   + Create the service file:


              sudo nano /etc/systemd/system/mund.service
       
       
    (and past the info bellow)   
    
    
    
       [Unit]
       Description=mund
       Requires=network-online.target
       After=network-online.target
       [Service]
       Restart=on-failure
       RestartSec=3
       User=root
       Group=root
       Environment=DAEMON_NAME=mund
       Environment=DAEMON_HOME=/root/.mun
       Environment=DAEMON_ALLOW_DOWNLOAD_BINARIES=on
       Environment=DAEMON_RESTART_AFTER_UPGRADE=on
       PermissionsStartOnly=true
       ExecStart=/usr/bin/mund-manager start --pruning="nothing" --rpc.laddr "tcp://0.0.0.0:26657"
       StandardOutput=file:/var/log/mund/mund.log
       StandardError=file:/var/log/mund/mund_error.log
       ExecReload=/bin/kill -HUP $MAINPID
       KillSignal=SIGTERM
       LimitNOFILE=4096
       [Install]
       WantedBy=multi-user.target
       
       
(to save click Ctrl X and than Y enter)

10-𝐂𝐫𝐞𝐚𝐭𝐞 𝐥𝐨𝐠 𝐟𝐢𝐥𝐞𝐬 𝐚𝐧𝐝 𝐬𝐭𝐚𝐫𝐭𝐬 𝐫𝐮𝐧𝐧𝐢𝐧𝐠 𝐭𝐡𝐞 𝐧𝐨𝐝𝐞


        make log-files
        
        
        sudo systemctl enable mund
        
        
        sudo systemctl start mund
        
        
     (Press CTRL+C)
          
+ Verify node is running properly:
 
 
        mund status
        
        
   (after catching up the block ask on discord the admin alex to get the tokens to become a validator )
   
   
11-𝐁𝐞𝐜𝐨𝐦𝐞 𝐕𝐚𝐥𝐢𝐝𝐚𝐭𝐨𝐫
 
 
 
        mund tx staking create-validator --from yyyyyyyy --moniker xxxxxxxx --pubkey $(mund tendermint show-validator) --chain-id testmun --keyring-backend test --amount 50000000000utmun --commission-max-change-rate 0.01 --commission-max-rate 0.2 --commission-rate 0.1 --min-self-delegation 1 --fees 200000utmun --gas auto --gas=auto --gas-adjustment=1.5 -y
   
   
   
  +  Remplace “yyyyyyyy” by “your-wallet-name” and remplace “your moniker” by “moon-moon-moon”.




12-fill the forms 1 and 2

+ 1 : Validator application = https://www.cognitoforms.com/MUN14/MUNBlockchainValidatorApplication

+ 2 : 100K TMUN Request Form = https://www.cognitoforms.com/MUN14/MUNTestnetValidator100KTMUNRequestForm

Enjoy.



       



