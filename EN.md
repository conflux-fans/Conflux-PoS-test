v1.2.0-alpha-5

## Start Fullnode
### 1. Set up your new Chrome account
1. Open the Chrome browser, click the avatar of the user in the upper and right corner, click on the bottom of the pop-up window to set up a new Chrome profile.

![image](https://pic1.zhimg.com/80/v2-2f0c84de6400228b1ce041abe7dfe2e0_1440w.png)

2. Choose "Continue without an account" to create a guest account for Chrome.
3. You can customize your new account's profile after set up clicks the button "Done".
4. At this moment, Chrome switch to the new account, also the upper right corner of Chrome will show you the account name.
 
### 2. Install ConfluxPortal
Install the Conflux Portal in the newly created Chrome account.
 
You can refer ConfluxPortal v0.6.10 update tutorial: https://forum.conflux.fun/t/confluxportal-v0-6-10-upgrade-tutorial/9291
 
### 3. Set a new blockchain network
The name of the network is set to: PoS testnet1
 
RPC URL：http://101.132.158.162:12537
 
### 4. Configuring the full node program
#### Test notes on Windows platform：
- We recommend you to close your anti-virus software
- Your Windows 10's version must be 1903 or higher
 
#### The file that needs to run：

- Full node program: conflux_win10_x64_pos_testnet.zip
 
#### Preparation of running Conflux：
- Create a directory: conflux
- Extract the download package to the directory separately
 
#### ⚠ The directory structure list below
 
```
conflux
└── run
└── conflux.exe
└── pos_testnet.toml
└── log.yaml
└── pos_config
```

#### Configuration instructions

You need follow two-step to modify `pos_testnet.toml` file
 
##### 1

```
# mining_author="net8888:xxxxxxxxxx..."
```

- Set it to your own address (starts with net8888:)
- remove prefix of mining_author in the file：#
![image](https://pica.zhimg.com/80/v2-811a1708df8093a2d2acc12df5a2dbcf_1440w.png)
 
After the modification is completed as shown in the figure:
![](https://pic2.zhimg.com/80/v2-7a04a058af9a2fd9173eb41075dfb4be_1440w.png)
 
##### 2 

```
# mining_type = "stratum"
```

- remove prefix of mining_type in the file: #
- Replace "stratum" with "cpu"
 
After the modification is completed as shown in the figure:
![](https://pic2.zhimg.com/80/v2-001304b360c1ecfa3c9c9391e0fddd55_1440w.png)
 
### 5. Turn on the test mode
 
In addition to the regular layout, then open the `log.yaml` file and find the corresponding location in the following figure, replace all the "info" with "debug", then save and exit.
 
![](https://pic1.zhimg.com/80/v2-a4fb4d17d2aa1db41941bf220d4cc4f3_1440w.png)
 
After the modification is completed as shown in the figure:
 
![](https://pic3.zhimg.com/80/v2-c280474886569245ea8855a5025c66be_1440w.png)
 
### 6. Run the full node programme
 
Open the `run` document. Right-click your mouse to copy the address as the following picture.

![](https://pic1.zhimg.com/80/v2-f489ab81ba3981bb298a2e80fd98abfb_1440w.png)
 
Press `win+R` on the keyboard. And then enter the command window by inputting "cmd".
 
![](https://pica.zhimg.com/80/v2-44af7c027eb3af8bb57f00cb847b6de5_1440w.png)
 
Input `cd`+ space + paste the address you copied above.
 
![](https://pic1.zhimg.com/80/v2-53902b06958d58f2f3ca26556556c147_1440w.png)
 
Start full node by inputting the command `start.bat`.
 
![](https://pic3.zhimg.com/80/v2-48fc0b24d573deafb0bbb3f56b58205f_1440w.png)
 
## PoS Registry
 
### 1
We need to set the password when starting the node the first time. This password is used to encrypt the private key of PoS. Press enter when you see the content on the screen as below:

```
PoS key is not detected and will be generated instead, please input your encryption password. This password is needed when you restart the node
Password:
```

- Try pressing `enter` if it stops running.
- If it showed as the picture below after you input the password:![](https://pic1.zhimg.com/80/v2-076499d5fddcbaf4f67420e36c80dee8_1440w.png)
Open the `stderr.txt` under the `run` document. And if the content is listed as below:
![](https://pic1.zhimg.com/80/v2-cb083d039c54a099b81fddf256ecd5a9_1440w.png)
 Then it is because of the wrong password. Open the `pos_config` under the run document. And then delete the `pos_key` file as below.
 ![](https://pica.zhimg.com/80/v2-d2428f117cc6b604cd0cac835961b7b5_1440w.png)
 And then restart the full node by inputting the command `start.bat`.
 
### 2
Right-click the "Start" icon on the left corner of your screen. And press "Windows PowerShell";

### 3

Copy the address of the run document(Same operation as above). And input `cd`+ space + paste the address you copied in Powershell.

![](https://pic1.zhimg.com/80/v2-24eddea02c61f7ee17b0b0793651cdfe_1440w.png)

### 4

Try to run the command below:

```
./conflux rpc local pos register --power 1
```

![](https://pic1.zhimg.com/80/v2-7044b4ec2c74b6a4a6078e59434a7fe1_1440w.png)
 
The first returned value in the command line is the data field requied by registering the PoS transaction. And the second returned value is the address of the PoS account(Not required at present)
 
### 5

Access `http://13.212.200.174/` in the browser and connect your wallet(Using the conflux testnet). Then relax and wait for several minutes. Your balance will be changed.

![image](https://pic3.zhimg.com/80/v2-a10cf1a4ce272310169a10cacd8c8b7b_1440w.png)
![image](https://pic3.zhimg.com/80/v2-e74edf180abf321aaadf94c29087999d_1440w.png)

### 6

Press the "Stake CFX to get the right to vote" button and choose the staking CFX amount(100 at least). Then press the "Deposit" button. This action should be confirmed in the portal.
![image](https://pic3.zhimg.com/80/v2-46015957ebbfbb6b3448862213f7c584_1440w.png)

### 7

Press the "Lock your staking to obtain interest" button after staking successfully. Then paste the data field you received in the command line above(In Step 4) and choose the number locked votes(100cfx for 1). Confirm it with signature in the portal at last.
![image](https://pic1.zhimg.com/80/v2-4918accb94594a9fa1a8ebf802b52ca1_1440w.png)
![image](https://pic2.zhimg.com/80/v2-7dce9e6868e5e6d40117d303c2fb9385_1440w.png)

## PoS Transition Test
Unzip the archive `pos_config-v1.2.0-alpha-5.tgz` （the archive will be released later）

Put the documents under `run`-`pos_config` folder.










## Q&A
**Q1: If I delete the `pos_key` under the `pos_config` folder, what should I do?**
 
A1: The file `pos_key` under the `pos_config` folder should not be deleted easily. If you deleted it, you need to reconnect to http://13.212.200.174/, exit the staking, wait for 9 hours for CFX to unlock, and re-register. At this point, it is recommended to start testing again with a new Conflux address (account).
 
**Q2: It's been stuck for more than 20 minutes, what should I do?**
 
A2：Restart your program.
 
**Q3: What should I do if the transaction failed when executing the staking CFX contract? I completed the first test and received such a problem during the second test.**
 
A3: In Conflux portal->click avatar->settings->advanced, find the "custom nonce" switch and turn it on, then there will be a box to fill in the nonce when you send a transaction, change the transaction's nonce to 0

**Q4: What should I do when I meet problems?**

A4: upload `stderr.txt`, `pos.log` and `log` folder to Google Drive, and share the link with Cike in Discord.

**Q5: How to unlock votes?**

Q5: Press the "Unlock votes" button if you want to close it.
![image](https://user-images.githubusercontent.com/32668688/133567650-67b947ea-47c3-4b90-848a-06ee9befb031.png)
 
**Q6: About restart?**

A6: The password that you set at the very first time is required when you restart the node:

```
PoS key detected, please input your encryption password.
Password:
```
 
