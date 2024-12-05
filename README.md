
![GXbm5mtaEAAzb4q](https://github.com/user-attachments/assets/d5b850d4-866b-4904-9857-93b584dd1dac)

------

# Hardware Requirements
| Hardware | Light Validator | Full Validator |
| ------------- | ---------------- | ---------------- |
Processor | 2 Cores | 4 Cores
OS Architecture | x86-64 (x64, x86_64, AMD64, and Intel 64) | x86-64 (x64, x86_64, AMD64, and Intel 64)
Ram | 2 GB | 8 GB
OS | Ubuntu 22.04.2 or higher version (x86-64) | Ubuntu 22.04.2 or higher version (x86-64)
Disk Size | 20 GB | 256 GB
Bandwidth | 1MB/s | 64Mb/s

# Dill Public Testnet (Alps Testnet) Network Information
| Network Name     | Dill Testnet Alps |
| ------------- | ---------------- |
Network Name | Alps Testnet
Rpc URL | https://rpc-andes.dill.xyz/
Chain ID | 102125
Currency Symbol | DILL
Explorer URL | https://andes.dill.xyz/


## Installation Instructions

1- Run the command below
```ABNF
curl -sO https://raw.githubusercontent.com/DillLabs/launch-dill-node/main/dill.sh  && chmod +x dill.sh && ./dill.sh
```
2- After starting the installation, you will be presented with the option ```Please choose an option for mnemonic source [1, From a new mnemonic, 2, Use existing mnemonic] [1]:``` If you are going to install with a new mnemonic, type 1, if you are going to install with an existing mnemonic, type 2 and press enter 

3- It will start downloading the necessary files. After you get the output ```Step 1 Completed. Press any key to continue...``` press any key and continue.

4- During the installation, we came to the Mnemonic section. If you are going to create a new Mnemonic, select 1 or if you are going to use your Mnemonic from the Andres testnet, select 2 and press enter. Don't forget to save your words. You can also see your created Mnemonic in this file in the ```dill/validator_keys/mnemonic-xxxxxx.txt``` directory

> [!CAUTION]
> ```dill/validator_keys/mnemonic-xxxxxx.txt``` Don't forget to backup the file

5- After the mnemonic is created, your Validator Keystore password will be randomly generated. Save this as well. You can see your randomly generated password in the file ```dill/validator_keys/keystore_password.txt``` Press any key again

6- Token stake amounts are different for full validator and light validator setups. For this, you will see an option like this ```Please choose an option for deposit token amount [1, 3600, 2, 36000]``` If you are selected for light validator, type 1, if you are selected for full validator, type 2 and press enter

7- In this step, the option ```Please enter your withdrawal address:``` will appear. Enter the address you requested the tokens from the faucet in Dill Discord twice

8- When you get the output ```Step 2 Completed. Press any key to continue...``` press any key again and continue the installation

9- When the installation is completed without any problems, it will give the output ```node running, congratulations``` It will also give your validator_pubkey in the output


## Staking

1- First, request tokens from the faucet bot in the Alps channel ($request [YOUR_WALLET_ADDRESS]). Use a different wallet than the one you created in your node

2- Visit https://staking.dill.xyz/ 

> [!CAUTION]
> It is recommended that you perform staking operations after your node is synchronized. Please use the commands at the bottom of the repo to check the synchronized status of your node
> Remember that you can only claim tokens from Faucet once!



3- Upload your ```deposit_data-xxxxx.json``` file to this site. You can find and get this file from the ```/dill/validator_keys``` directory in your server

4- After uploading the ```Deposit_data-xxxx.json``` file to the site, click Connect to MetaMask, make sure you have enough test tokens (>3600 DILL)


  5- After connecting the wallet, click Continue to continue. Then click ```Confirm Deposit``` to deposit tokens


6- After completing the staking process, you can search for your validator information on the page using your validator public key. It may take 30 minutes to 1 hour for your validator to appear. Be patient



# Adding a Validator to an Existing Node

- If you have extra WL you can add it as a new validator to your existing Node. To do this:
  - Login to your server and run the command ```dill/2_add_validator.sh``` 
  - Next you will enter mnemonics. Select ```1``` to create a new mnemonic (make sure you save this safely)
If you already have a mnemonic and want to use it, select ```2```
```ABNF
    ********** Step 1: Generating Validator Keys **********
Validator Keys are generated from a mnemonic
Please choose an option for mnemonic source [1, From a new mnemonic, 2, Use existing mnemonic] [1]:
```
 - Now we will select the amount of tokens to be deposited and enter our withdraw address. For Light Validator (3600 DILL) select ```1```. For Full Validator (36000 DILL) select ```2```. Then enter your Withdraw address, press enter and enter again and confirm.

> [!IMPORTANT]
> Here it will ask us for the ```Index``` number. You will accept your current Node as index:0. Therefore, the index of the validator you will add will be ```1```. (From now on, the index of the validator you will add will go as n+1. In other words, it will be 2 for the 3rd Validator.).
> As a result ```1```
> Another thing you should pay attention to is that each validator's PubKey will be different. If you enter the indexes correctly, they will be different anyway
  
 - You can proceed to the staking phase
 - You can see your current Validators in the ```dill``` directory using this command:
   ```./show_pubkey```

## Useful Commands

- If you are not in the Dill directory, you can switch to the Dill directory with this command. (You need to run the commands in the "dill" directory)
```ABNF
cd dill 
```

- To check node status
```Processing
./health_check.sh -v
```

- To check node sync status. If you get an output like this, it means node sync is happening. ({"head_slot":"173420","sync_distance":"0","is_syncing":false,"is_optimistic":false,"el_offline":false}}
```ABNF
curl -s localhost:3500/eth/v1/node/syncing
```
