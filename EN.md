## Conflux PoS Testnet 1st Round Public Test Tutorial

### Start Time: Sept.26 18:00(GMT+8)

### Version: v1.2.0-beta-2

### Timeline: (GMT+8)
- #### We will start fullnode running at around Sept.26th 18:00.
- #### The PoS registration will start at Blocknumber 129600 (around Sept.27 12:00).
- #### The PoS registration will close at Blocknumber 475200 (around Sept.29 12:00). After registration closes, you can start adding pos_config.
- #### The deadline for adding pos_config is at Blockheight 720000 (around Oct.1st 18:00).

## 
## 

## Fullnode Start (around Sept.26 18:00)
### 1. Set up your new Chrome account
1. Open the Chrome browser, click the account profile picture in the top-right corner, click the "add" in the pop-up window to set up a new Chrome profile.

![image](https://pic1.zhimg.com/80/v2-2f0c84de6400228b1ce041abe7dfe2e0_1440w.png)

2. Select "Continue without an account" to continue as a guest account. 
3. Click "Done" and finish account set-up. You can chance your profile afterwards. 
4. Chrome will automatically switch to the new account after set-up. Your account name will be displayed on the top-right corner.
 
### 2. Install ConfluxPortal
Install the Conflux Portal in the newly created Chrome account.
 
You can refer to ConfluxPortal v0.6.10 update tutorial for installing: https://forum.conflux.fun/t/confluxportal-v0-6-10-upgrade-tutorial/9291
 
### 3. Set a new blockchain network
Blockchain Name: PoS testnet1
 
RPC URL：http://101.132.158.162:12537
 
### 4. Set configuration of the full node program
#### Running test notes on Windows：
- We recommend you to close your anti-virus software
- Your Windows 10's version must be 1903 or higher
 
#### You need to download the following files：

- Fullnode GitHub download：https://github.com/conflux-fans/Conflux-PoS-test/releases/tag/conflux_v1.2.0-beta-2
 
#### Preparation of running full node program：
- Create a directory named conflux
- Extract the download package to the directory
 
#### ⚠ The directory structure should look like this:
 
```
conflux
└── run
    └── conflux.exe
    └── conflux.pdb
    └── pos_testnet.toml
    └── log.yaml
    └── clear_state.bat
    └── clear_state.sh
    └── libcrypto-1_1-x64.dll
    └── libssl-1_1-x64.dll
    └── start.bat
    └── start.sh
    └── throttling.toml
```

#### Configuration set-up instructions

You need follow these two steps to edit `pos_testnet.toml` file in order to set up the configuration.
 
##### 1

```
# mining_author="net8888:xxxxxxxxxx..."
```

- Please edit "net8888:xxxx..." and set it to your own wallet address. (starts with net8888:)
- Delete "#" and the space before "mining_author..."
![image](https://pica.zhimg.com/80/v2-811a1708df8093a2d2acc12df5a2dbcf_1440w.png)
 
The command should look like this after edition:
![](https://pic2.zhimg.com/80/v2-7a04a058af9a2fd9173eb41075dfb4be_1440w.png)
 
##### 2 

```
# mining_type = "stratum"
```

- Delete "#" and the space before "mining_type..."
- Replace "stratum" with "cpu"
 
The command should look like this after edition:
![image](https://user-images.githubusercontent.com/32668688/135205780-ff562c90-5d8d-484d-b12f-cb5f8eeaead7.png)
 
### 5. Turn on the test mode
 
Open the `log.yaml` file and find the commands shown in the following figures, replace all the "info" with "debug", then save the file.
 
![image](https://user-images.githubusercontent.com/32668688/135205797-49d9d10f-98e0-4bbb-a918-b2da72f31a77.png)
 
The command should look like this after edition:
 
![image](https://user-images.githubusercontent.com/32668688/135205813-674f7edd-7679-427d-a973-d68319cfed45.png)
 
### 6. Run the full node programme
 
Open the `run` folder. Right-click your mouse to copy the directory path as the following picture shown.

![image](https://user-images.githubusercontent.com/32668688/135205832-9f34fafb-9cc5-44bd-9f68-8ac6198d218c.png)
 
Press `win and R` on the keyboard. Open the command window by entering "cmd".
 
![image](https://user-images.githubusercontent.com/32668688/135205847-7bb179bc-27db-4452-8078-a0ab17034042.png)
 
Enter `cd` + space + the directory path you copied before.
 
![image](https://user-images.githubusercontent.com/32668688/135205864-efc734bc-3baf-4cc9-9ef1-6446d87e0d27.png)
 
Start full node by entering the command `start.bat`.
 
![](https://pic3.zhimg.com/80/v2-48fc0b24d573deafb0bbb3f56b58205f_1440w.png)
 
## PoS Registration (Blocknumber 129600, around Sept.27 12:00)
 
### 1
We need to set the password when starting the node for the first time. This password is used to encrypt the private key of PoS. Press "enter" when you see the content on the screen as below:

```
PoS key is not detected and will be generated instead, please input your encryption password. This password is needed when you restart the node
Password:
```

- Try pressing `enter` if it stops running.
- If you see the following output after you enter the password:![](https://pic1.zhimg.com/80/v2-076499d5fddcbaf4f67420e36c80dee8_1440w.png)
please open the `stderr.txt` file under `run` directory. And if you see the following output after you open the `stderr.txt` file, you must have entered a wrong password:
![](https://pic1.zhimg.com/80/v2-cb083d039c54a099b81fddf256ecd5a9_1440w.png)
 Open the `pos_config` under `run` directory and delete the `pos_key` file as shown below.
 ![](https://pica.zhimg.com/80/v2-d2428f117cc6b604cd0cac835961b7b5_1440w.png)
 Restart the full node by entering `start.bat` command.
 
### 2
Right-click the "Start" icon on the left corner of your screen and then press "Windows PowerShell";

### 3

Copy the directory path of the `run` directory using right-click. Enter `cd` + space + the directory path you copied in Powershell.

![](https://pic1.zhimg.com/80/v2-24eddea02c61f7ee17b0b0793651cdfe_1440w.png)

### 4

Run the command:

```
./conflux rpc local pos register --power 1
```

![](https://pic1.zhimg.com/80/v2-7044b4ec2c74b6a4a6078e59434a7fe1_1440w.png)
 
The first returned value is the data field requied when registering for PoS transactions. The second returned value is the address of the PoS account (you won't be using this for the testing)
 
### 5

Access `http://13.212.200.174/` in the browser and connect your wallet(using the conflux testnet). Your balance will be updated. This process might take a couple minutes. 

![image](https://pic3.zhimg.com/80/v2-a10cf1a4ce272310169a10cacd8c8b7b_1440w.png)
![image](https://pic3.zhimg.com/80/v2-e74edf180abf321aaadf94c29087999d_1440w.png)

### 6

Click "Stake CFX to get the right to vote"  and choose the staking CFX amount (at least 100). Then click "Deposit". This action need to be confirmed in the portal.
![image](https://pic3.zhimg.com/80/v2-46015957ebbfbb6b3448862213f7c584_1440w.png)

### 7

Click "Lock your staking to obtain interest" after staking successfully. Then paste the data field you received in step 4 and enter the votes you would like to lock (100 CFX for 1 vote). Confirm in the portal.
![image](https://pic1.zhimg.com/80/v2-4918accb94594a9fa1a8ebf802b52ca1_1440w.png)
![image](https://pic2.zhimg.com/80/v2-7dce9e6868e5e6d40117d303c2fb9385_1440w.png)

## PoS Transition Test (Blockheight 475200, around Sept.29 12:00; finish before Blockheight 720000, around Oct.1st 18:00)

PoS Transition test will start at Blockheight 475200 and end at Blockheight 720000. 

GitHub download link：https://github.com/conflux-fans/Conflux-PoS-test/releases/tag/conflux_v1.2.0-beta-2

Download the package in the link `pos_config-v1.2.0-beta-2.tgz` and uncompress the package. Put the files under `run`-`pos_config` folder.





## Q&A
**Q1: If I accidentally delete the `pos_key` file under `pos_config` folder, what should I do?**
 
A1: You shold not delele the file `pos_key`. If you deleted it, you need to reconnect to http://13.212.200.174/ and withdraw the staking. You need to wait for 9 hours for the CFX to be unlocked and then re-register. We suggest you to skip the wait and using a new Chrome account to test.
 
**Q2: The program has stuck for more than 20 minutes, what should I do?**
 
A2：Restart your program.
 
**Q3: What should I do if the transaction failed when approving the locking CFX transaction while succeeded when approving staking CFX transaction**
 
A3: Go to Conflux portal->account profile->settings->advanced, look for the "custom nonce" and turn it on. When you turn on the "custom nounce", each time when you need to approve for a transaction, a textbox will pop-up and ask you to enter a nounce. Enter nounce each time when you are asked. 

**Q4: Where can I report bugs during testing?**

A4: upload `stderr.txt`, `pos.log` and `log` folder to a Google Drive folder, and share the link with Cike in Discord.

**Q5: How to unlock votes?**

Q5: Cilck the "Unlock votes".
![image](https://pic2.zhimg.com/80/v2-dfe231dc87c70f7b9d0abe7f31803030_1440w.png)
 
**Q6: What should I be cautious about when I restart the node?**

A6: Enter the same password you set in the first time and you should be fine:

```
PoS key detected, please input your encryption password.
Password:
```
 
