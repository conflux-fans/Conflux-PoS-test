## Conflux PoS Testnet 3rd Round Public Test Tutorial

### Start Time: Oct.20 18:00(GMT+8)

### Version: v1.2.0-beta-5

### Timeline: (GMT+8)
- #### Start fullnode running at around Oct.20 18:00.
- #### The PoS registration will start at Blocknumber 129600 (around Oct.21 12:00).
- #### The PoS registration will close at Blocknumber 302400 (around Oct.22 12:00). After registration closes, you can start adding pos_config.
- #### The deadline for adding pos_config is at Blockheight 345000 (around Oct.23 18:00).

## 
## 

## 1 Install ConfluxPortal
 
You can refer to ConfluxPortal v0.6.10 update tutorial for installing: https://forum.conflux.fun/t/confluxportal-v0-6-10-upgrade-tutorial/9291

## 2 Fullnode Start (around Oct.20 18:00)

### 1. Network setting

Set a new blockchain network

<img src="https://pic1.zhimg.com/80/v2-5fe71055fdff2d3a7df1b8746da93c4e_1440w.png" width="250" height="250">

Blockchain Name: PoS testnet1
 
RPC URL：http://101.132.158.162:12537

<img src="https://pic1.zhimg.com/80/v2-403d25687e73feecbc58eec31deca56a_1440w.png" width="250" height="400">

### 2. Set configuration of the fullnode program

#### Running test notes on Windows：
- We recommend you to close your anti-virus software(including Windows Defender)
- Your Windows 10's version must be 1903 or higher

#### You need to download the following files：

Fullnode GitHub download：
 
#### Preparation of running full node program：
- Create a directory named conflux
- Extract the download package to the directory
 
 ⚠ The directory structure should look like this:
 
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

```
# mining_author="net8888:xxxxxxxxxx..."
```

Please edit "net8888:xxxx..." and set it to your own wallet address. (starts with net8888:)

Delete "#" and the space before "mining_author..."

<img src="https://pica.zhimg.com/80/v2-811a1708df8093a2d2acc12df5a2dbcf_1440w.png" width="250" height="300">

should look like this after edition:
![](https://pic2.zhimg.com/80/v2-7a04a058af9a2fd9173eb41075dfb4be_1440w.png)

```
# mining_type = "stratum"
```

Replace "stratum" with "cpu", and delete "#" and the space before "mining_type...".
 
should look like this after edition:
![](https://pic2.zhimg.com/80/v2-001304b360c1ecfa3c9c9391e0fddd55_1440w.png)



### 3. Turn on the test mode
 
Open the `log.yaml` file and find the commands shown in the following figures, replace all the "info" with "debug", then save the file.
 
<img src="https://pic1.zhimg.com/80/v2-a4fb4d17d2aa1db41941bf220d4cc4f3_1440w.png" width="300" height="300">

The command should look like this after edition:

<img src="https://pic3.zhimg.com/80/v2-c280474886569245ea8855a5025c66be_1440w.png" width="300" height="300">
 
### 4. Run the full node programme
 
Open the `run` folder. Right-click your mouse to copy the directory path as the following picture shown.

![](https://pic1.zhimg.com/80/v2-f489ab81ba3981bb298a2e80fd98abfb_1440w.png)
 
Press `win and R` on the keyboard. Open the command window by entering "cmd".

<img src="https://pica.zhimg.com/80/v2-44af7c027eb3af8bb57f00cb847b6de5_1440w.png" width="270" height="150">
 
Enter `cd` + space + the directory path you copied before.
 
![](https://pic1.zhimg.com/80/v2-53902b06958d58f2f3ca26556556c147_1440w.png)
 
Start full node by entering the command `start.bat`.
 
![](https://pic3.zhimg.com/80/v2-48fc0b24d573deafb0bbb3f56b58205f_1440w.png)

Attention: here you need to enter the password and confirm it:

![](https://pic2.zhimg.com/80/v2-e01c23ae83913f65068eed33ecc335ef_1440w.png)


## 3 PoS Registration (Blocknumber 129600, around Oct.21 12:00)
 
## PoS Registration 
 
### 1. Password setting
We need to set the password when starting the node for the first time. This password is used to encrypt the private key of PoS. Enter the password and confirm it when you see the content on the screen as below:

```
PoS key is not detected and will be generated instead, please input your encryption password. This password is needed when you restart the node
Password:
Repeat Password:
```

### 2. PoS Registration
Right-click the "Start" icon on the left corner of your screen and then press "Windows PowerShell";

Copy the directory path of the `run` directory using right-click. Enter `cd` + space + the directory path you copied in Powershell.

<img src="https://pic1.zhimg.com/80/v2-24eddea02c61f7ee17b0b0793651cdfe_1440w.png" width="400" height="160">

And then run the command:

```
./conflux rpc local pos register --power 1
```

![](https://pic1.zhimg.com/80/v2-7044b4ec2c74b6a4a6078e59434a7fe1_1440w.png)
 
The first returned value is the data field requied when registering for PoS transactions. The second returned value is the address of the PoS account. 
 
### 3. Staking

Access `https://votetest.confluxnetwork.org/en/` in the browser and connect your Portal(using the conflux PoS testnet1). Your balance will be updated soon. 

![](https://pic3.zhimg.com/80/v2-53b33544fda88e42eb39b6248230258c_1440w.png)

Choose the staking CFX amount (at least 100). Then click "Deposit". This action need to be confirmed in the portal.

<img src="https://pic1.zhimg.com/80/v2-29049f14691983ab544b9a63c8ae46b5_1440w.png" width="320" height="160">

### 4. Locking

After staking, choose PoS here. 

![](https://pic2.zhimg.com/80/v2-738f6dfbf19eba927e885ca048a408de_1440w.png)

Then paste the data field you received in step 2 to "Full node data"，and enter the votes you would like to lock (100 CFX for 1 vote). Confirm in the portal.

<img src="https://pic2.zhimg.com/80/v2-cbafbbbe85b0fd7b7162aa08ed730ff6_1440w.png" width="400" height="450">



## 4 PoS Transition Test (Blockheight 302400, around Oct.22 12:00; finish before Blockheight 345000, around Oct.23 18:00)

GitHub download link：will release later

Download the package in the link `pos_config-v1.2.0-beta-5.tgz` and uncompress the package. Put the files under `run`-`pos_config` folder.





## Q&A
**Q1: If I accidentally delete the `pos_key` file under `pos_config` folder, what should I do?**
 
A1: You shold not delele the file `pos_key`. If you deleted it, you need to reconnect and withdraw the staking. You need to wait for 9 hours for the CFX to be unlocked and then re-register. We suggest you to skip the wait and using a new Chrome account to test.
 
**Q2: The program has stuck for more than 20 minutes, what should I do?**
 
A2：Restart your program.
 
**Q3: What should I do if the transaction failed when approving the locking CFX transaction while succeeded when approving staking CFX transaction**
 
A3: Go to Conflux portal->account profile->settings->advanced, look for the "custom nonce" and turn it on. When you turn on the "custom nounce", each time when you need to approve for a transaction, a textbox will pop-up and ask you to enter a nounce. Enter nounce each time when you are asked. 

**Q4: Where can I report bugs during testing?**

A4: upload `stderr.txt`, `pos.log` and `log` folder to a Google Drive folder, and share the link with Cike in Discord.
 
**Q5: What should I be cautious about when I restart the node?**

A5: Enter the same password you set in the first time and you should be fine:

```
PoS key detected, please input your encryption password.
Password:
```
 
