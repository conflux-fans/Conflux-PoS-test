## Conflux PoS 测试网第三次公开测试

### 预计启动时间：10月20日18时

### 版本号：v1.2.0-beta-5

### 测试时间表：
- #### 预计10月20日18时 启动fullnode
- #### 预计10月21日12时 开始PoS注册（提前注册会失败）（区块数129600）
- #### 预计10月22日12时 停止注册 添加pos.config（区块数302400）
- #### 预计10月23日18时前 完成添加（区块高度345000）

## 

## 一、安装ConfluxPortal

参见：ConfluxPortal v0.6.10 更新指南 ：https://forum.conflux.fun/t/confluxportal-v0-6-10/9284

## 二、启动 fullnode（10月20日18时开始）

### 1. 配置网络

在 ConfluxPortal 中切换至自定义测试网络

<img src="https://pic1.zhimg.com/80/v2-5fe71055fdff2d3a7df1b8746da93c4e_1440w.png" width="250" height="250">

网络名称填写：PoS testnet1

RPC填写：http://101.132.158.162:12537

<img src="https://pic1.zhimg.com/80/v2-403d25687e73feecbc58eec31deca56a_1440w.png" width="250" height="400">

### 2.配置fullnode程序
#### Windows 测试说明

- 建议关闭杀毒软件（包括Windows Defender）
- win 10 版本1903以上

#### 运行文件

Fullnode 程序 GitHub 下载链接：

#### 运行准备

- 创建目录：conflux
- 将下载包解压至目录

⚠ 目录结构为

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

#### 配置说明

`pos_testnet.toml` 文件中需要进行两步修改

```
# mining_author="net8888:xxxxxxxxxx..."
```
改成自己的地址（net8888:开头），并移除前缀： `#`

net8888:开头的地址如图所示：

<img src="https://pica.zhimg.com/80/v2-285472e88802350f6366768e50c5f0b0_1440w.png" width="250" height="250">

修改完成后如图所示：

![](https://pic2.zhimg.com/80/v2-7a04a058af9a2fd9173eb41075dfb4be_1440w.png)

```
 # mining_type = "stratum"
```

将"stratum"替换为"cpu"，移除前缀： `#`

修改完成后如图所示：

<img src="https://pic2.zhimg.com/80/v2-001304b360c1ecfa3c9c9391e0fddd55_1440w.png" width="420" height="160">

### 3. 开启测试模式

在常规布置之外，再将log.yaml文件打开后找到改图位置，将所有info替换成debug，后保存并退出。

![image](https://user-images.githubusercontent.com/32668688/135205205-266ad82f-55e5-44b5-b38a-e5400017d6ca.png)

修改完成后如图所示：

![image](https://user-images.githubusercontent.com/32668688/135205230-f542e6f0-0824-49aa-9b60-e0ad352bbad6.png)

### 4. 运行 Fullnode 程序

- 打开 **run** 文件夹，按如图所示，右键复制地址

<img src="https://pic1.zhimg.com/80/v2-f489ab81ba3981bb298a2e80fd98abfb_1440w.png" width="420" height="190">

- 键盘输入`win+R` ，在弹出窗口中输入 `cmd` ，进入命令行界面

<img src="https://pica.zhimg.com/80/v2-44af7c027eb3af8bb57f00cb847b6de5_1440w.png" width="300" height="160">

- 输入`cd`+空格+粘贴刚才复制的地址

<img src="https://pic1.zhimg.com/80/v2-53902b06958d58f2f3ca26556556c147_1440w.png" width="410" height="160">

- 输入命令`start.bat`，启动 Fullnode

![](https://pic3.zhimg.com/80/v2-48fc0b24d573deafb0bbb3f56b58205f_1440w.png)

注意，此时需要输入密码和确认密码，防止手误输错：

![](https://pic2.zhimg.com/80/v2-e01c23ae83913f65068eed33ecc335ef_1440w.png)

## 三、 PoS 注册（区块数129600，预计10月21日12时开始）

### 3.1 设置密码

第一次启动节点，会需要设置密码，用来加密PoS的私钥。屏幕上显示如下内容的时候输入密码和确认密码，回车继续。

```
PoS key is not detected and will be generated instead, please input your encryption password. This password is needed when you restart the node
Password:
Repeat Password:
```

### 3.2 PoS注册 
右键点击“开始”图标，选择Windows Powershell打开；

<img src="https://pic3.zhimg.com/80/v2-912969000d96074df5b9ef178b4ce805_1440w.png" width="200" height="400">

复制`run`文件夹地址，在Powershell中输入`cd`+空格+粘贴刚才复制的地址

<img src="https://pic1.zhimg.com/80/v2-24eddea02c61f7ee17b0b0793651cdfe_1440w.png" width="400" height="160">

然后执行下面的命令：

```
./conflux rpc local pos register --power 1
```

![](https://pic1.zhimg.com/80/v2-7044b4ec2c74b6a4a6078e59434a7fe1_1440w.png)

命令行返回值的第一项为注册pos的交易需要的data字段，第二项为pos的账户地址。

### 3.3 质押
打开 https://votetest.confluxnetwork.org/zh/ 页面，登录自己的钱包（确认配置在PoS testnet1测试网），等待账户余额变化。

![](https://pic1.zhimg.com/80/v2-4ebc6070e8c109d1d493817cd21ce9db_1440w.png)

在当前页面填写质押CFX的数量（至少100个），并点击“质押”按钮，质押需要进行portal确认；

<img src="https://pic2.zhimg.com/80/v2-bf3b8713876a98e0607d409fa21c1fa1_1440w.png" width="320" height="160">

### 3.4 锁仓
质押成功后，页面上栏选择“PoS锁仓”，粘贴填入第4步获取到的data字段，选择锁仓票数（100CFX算1票），点击“首次注册”按钮，并在portal中签名确认。

![](https://pic1.zhimg.com/80/v2-6c5b2c716919addb532866945e038ea2_1440w.png)




## 四、PoS过渡测试（区块数302400，预计10月22日12时开始；区块高度345000，约10月23日18时前完成）

GitHub下载链接: 稍后发布

下载链接内的压缩包`pos.config_conflux_win10_x64_v1.2.0-beta-5`，将解压后文件夹内的所有文件移至`run`文件夹的`pos_config`目录下，期间保持程序正常运行

    
### Q&A
**Q1: pos_config文件下的pos_key删除了怎么办？**

A1: “pos_config文件下的pos_key”这个文件不要轻易删除。
如果删除了，需要重新连接  https://votetest.confluxnetwork.org/zh/  ，退出质押，等9个小时之后CFX解锁后重新注册。
这时候建议使用新Conflux地址（账户）重新开始测试。

**Q2:卡了有20多分钟了，如何处理？**

A2：重启程序

**Q3：第一轮测试结束，第二轮测试的时候，抵押CFX执行合约无法完成交易。**

A3: 在portal->点击头像->设置->高级 中找到“自定义 nonce”开关打开，发交易时就会多出一个填写 nonce 的框，将nonce改成0

**Q4: 测试遇到问题，该如何反馈？**

A4：测试遇到问题，请将stderr.txt、pos.log和log文件夹，打包上传至百度网盘，并将链接分享给群内@Coding

**Q5: 重启节点注意：**

A5: 需要输入和第一次启动的时候相同的密钥才能正常启动：

```
PoS key detected, please input your encryption password.
Password:
```



