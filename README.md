# Mun-Blockchain Launch the Validator Node

![3A3986A5-9118-4826-B759-69DAC4FBE84B](https://user-images.githubusercontent.com/108979536/194869031-4e68b5a4-32f7-45dc-8a58-bebd978e5a54.jpeg)


๐๐ง๐ญ๐ซ๐จ๐๐ฎ๐๐ญ๐ข๐จ๐ง ๐ญ๐จ ๐๐๐

MUN Coin is a new cryptocurrency that is gaining buzz in the crypto community. Hereโs an introduction to what it is and why you might want to consider investing. MUN Coin is a decentralized digital currency that allows for fast, secure, and anonymous transactions. Itโs built on the newest blockchain technology and uses peer-to- peer networking. This means that there are no intermediaries between sender and receiver โ they can transact directly with each other.

![EBFDBE6F-97BC-478D-9D15-03E62CCF8665](https://user-images.githubusercontent.com/108979536/194870596-6c66f0aa-eee4-4b4d-b811-7a3c52697637.png)

               #Alex 
            ๐๐๐๐ ๐๐๐ฏ๐๐ฅ๐จ๐ฉ๐๐ซ
           
Join the team on discord
![image](https://user-images.githubusercontent.com/108979536/194872464-3608bdcc-c325-4323-814f-0991a08b6199.png)

https://discord.gg/mun

![image](https://user-images.githubusercontent.com/108979536/194873093-7c146462-78ef-4fd8-9532-90dc10ae780d.png)

https://twitter.com/munblockchain


1-๐๐ข๐ซ๐ฌ๐ญ๐ฅ๐ฒ ๐จ๐ฉ๐๐ง ๐ฒ๐จ๐ฎ๐ซ ๐ญ๐๐ซ๐ฆ๐ข๐ง๐๐ฅ,๐ฎ๐ฉ๐๐๐ญ๐ ๐ฒ๐จ๐ฎ๐ซ ๐ฉ๐๐๐ค๐๐ ๐๐ฌ ๐๐ง๐ ๐ข๐ง๐ฌ๐ญ๐๐ฅ๐ฅ ๐ญ๐ก๐ ๐๐๐ฉ๐๐ง๐๐๐ง๐๐ข๐๐ฌ

      sudo apt update -y
      
      sudo apt upgrade -y
      
      sudo apt full-upgrade -y
      

2-๐๐ง๐ฌ๐ญ๐๐ฅ๐ฅ ๐๐๐ฉ๐๐ง๐๐๐ง๐๐ข๐๐ฌ

      sudo apt install build-essential jq -y
      
3-๐๐ง๐ฌ๐ญ๐๐ฅ๐ฅ ๐ ๐ข๐ญ

      wget -q -O - https://raw.githubusercontent.com/canha/golang-tools-install-script/master/goinstall.sh | bash -s -- --version 1.18
      source ~/.profile
      
 Check go version
 
       go version
       
 4-๐๐ฉ๐๐ง ๐๐จ๐ซ๐ญ๐ฌ
 
      apt install ufw -y
      
      sudo ufw allow ssh
      
      sudo ufw allow 22
      
      sudo ufw allow 60000:61000/tcp
      
      ufw enable (yes enter)
      
      
5-๐๐๐ญ๐ฎ๐ฉ ๐๐ก๐ ๐๐๐๐๐ก๐ข๐๐ง (clone respository)

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
        
       
 6-๐๐ง๐ข๐ญ๐ข๐๐ฅ๐ข๐ณ๐ ๐ญ๐ก๐ ๐ฏ๐๐ฅ๐ข๐๐๐ญ๐จ๐ซ
    (init)
    
    
       mund init xxxxxxxxx --chain-id testmun
       
       
  + Replace xxxxxx with your moniker name must be three words like moon-moon-moon
  
 7-๐๐ซ๐๐๐ญ๐ ๐ ๐ฐ๐๐ฅ๐ฅ๐๐ญ (wallet name can be just one word not like your moniker)
 
  
        mund keys add yyyyyyyy --keyring-backend test
       
 
 + Replace yyyyyyyyy with your wallet name like moon
 + Save all information in a notepad

8-๐๐๐ญ๐ฎ๐ฉ ๐๐๐ง๐๐ฌ๐ข๐ฌ.๐ฃ๐ฌ๐จ๐ง ๐๐ง๐ ๐๐จ๐ง๐๐ข๐ .๐ญ๐จ๐ฆ๐ฅ

   + Fetch genesis.json from genesis node: :
    
    
         curl --tlsv1   https://node1.mun.money/genesis? | jq ".result.genesis" > ~/.mun/config/genesis.json
        
        
   + Update seed in config.toml to make p2p connection:
   

          nano ~/.mun/config/config.toml 
        
        
   + Go to the P2P section and fill in the seed with the information below 
    
            "6a08f2f76baed249d3e3c666aaef5884e4b1005c@167.71.0.38:26656"
        
        
   (to save click Ctrl X and than Y enter)
   

   + Replace stake to TMUN:


             sed -i 's/stake/utmun/g' ~/.mun/config/genesis.json


9-๐๐ซ๐๐๐ญ๐ ๐๐ง๐ ๐ฌ๐๐ญ ๐ญ๐ก๐ ๐ฌ๐๐ซ๐ฏ๐ข๐๐ ๐๐ข๐ฅ๐

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

10-๐๐ซ๐๐๐ญ๐ ๐ฅ๐จ๐  ๐๐ข๐ฅ๐๐ฌ ๐๐ง๐ ๐ฌ๐ญ๐๐ซ๐ญ๐ฌ ๐ซ๐ฎ๐ง๐ง๐ข๐ง๐  ๐ญ๐ก๐ ๐ง๐จ๐๐


        make log-files
        
        
        sudo systemctl enable mund
        
        
        sudo systemctl start mund
        
        
     (Press CTRL+C)
          
+ Verify node is running properly:
 
 
        mund status
        
        
   (after catching up the block ask on discord the admin alex to get the tokens to become a validator )
   
   
11-๐๐๐๐จ๐ฆ๐ ๐๐๐ฅ๐ข๐๐๐ญ๐จ๐ซ
 
 
 
        mund tx staking create-validator --from yyyyyyyy --moniker xxxxxxxx --pubkey $(mund tendermint show-validator) --chain-id testmun --keyring-backend test --amount 50000000000utmun --commission-max-change-rate 0.01 --commission-max-rate 0.2 --commission-rate 0.1 --min-self-delegation 1 --fees 200000utmun --gas auto --gas=auto --gas-adjustment=1.5 -y
   
   
   
  +  Remplace โyyyyyyyyโ by โyour-wallet-nameโ and remplace โyour monikerโ by โmoon-moon-moonโ.




12-fill the forms 1 and 2

+ 1 : Validator application = https://www.cognitoforms.com/MUN14/MUNBlockchainValidatorApplication

+ 2 : 100K TMUN Request Form = https://www.cognitoforms.com/MUN14/MUNTestnetValidator100KTMUNRequestForm

Enjoy.



# [Buy me a cup of coffee.](https://paypal.me/AbdelAkridi?country.x=NL&locale.x=en_US)       



