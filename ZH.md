## Conflux PoS 测试网第二次公开测试

### 预计启动时间：10月9日18时

### 版本号：v1.2.0-beta-4

### 测试时间表：
- #### 预计10月9日18时 启动fullnode
- #### 预计10月9日18时10分 开始PoS注册（提前注册会失败）（区块数1200）
- #### 预计10月10日11时 停止注册 添加pos.config（区块数122400）
- #### 预计10月11日10时前 完成添加（区块高度200000）

## 
## 

## 一、启动 fullnode（10月9日18时开始）
### 1.设置新的 Chorme账户
1. 打开Chrome浏览器，点击右上角用户头像，点击弹出窗口最下方添加个人资料
![](https://pic3.zhimg.com/80/v2-ed09d962c40401a35b1c666e295d06ac_1440w.png)
2. 选择“在不登录账号的情况下继续”，创建访客账号
3. 自定义个人新账号，点击“完成”
4. 此时，右上角已自动切换为新账号

### 2.安装ConfluxPortal
在新的 Chorme账户中安装ConfluxPortal

参见：ConfluxPortal v0.6.10 更新指南 ：https://forum.conflux.fun/t/confluxportal-v0-6-10/9284
### 3.配置网络
网络名称填写：PoS testnet1

RPC填写：http://101.132.158.162:12537

### 4.配置fullnode程序
#### Windows 测试说明
测试须知
1. 建议关闭杀毒软件（包括Windows defender）
2. win 10 版本1903以上

#### 运行文件


Fullnode 程序 GitHub 下载链接：https://github.com/conflux-fans/Conflux-PoS-test/releases/tag/conflux_v1.2.0-beta-4

#### 运行 conflux 准备

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

一、
```
# mining_author="net8888:xxxxxxxxxx..."
```
> 设置成自己的地址（以net8888:开头）

> 移除前缀: `#`

![](https://pica.zhimg.com/80/v2-285472e88802350f6366768e50c5f0b0_1440w.png)

修改完成后如图所示：

![](https://pic2.zhimg.com/80/v2-7a04a058af9a2fd9173eb41075dfb4be_1440w.png)

二、
```
 # mining_type = "stratum"
```
> 移除前缀: `#`

> 将"stratum"替换为"cpu"

修改完成后如图所示：

![image](https://user-images.githubusercontent.com/32668688/135205134-095e5921-bd7d-4302-bcfd-12621820ea38.png)

### 5.开启测试模式

在常规布置之外，再将log.yaml文件打开后找到改图位置，将所有info替换成debug，后保存并退出。

![image](https://user-images.githubusercontent.com/32668688/135205205-266ad82f-55e5-44b5-b38a-e5400017d6ca.png)

修改完成后如图所示：

![image](https://user-images.githubusercontent.com/32668688/135205230-f542e6f0-0824-49aa-9b60-e0ad352bbad6.png)

### 6.运行 fullnode 程序

- 打开 **run** 文件夹，按如图所示，右键复制地址

![image](https://user-images.githubusercontent.com/32668688/135205297-0a68a0c6-9683-473c-99bd-2fc31a11c241.png)

- 键盘输入`win+R` ，在弹出窗口中输入 `cmd` ，进入命令行界面

![image](https://user-images.githubusercontent.com/32668688/135205319-b0f1aba6-5ab0-408d-903b-82f4d134cd69.png)

- 输入`cd`+空格+粘贴刚才复制的地址

![image](https://user-images.githubusercontent.com/32668688/135205344-b4fd0f8e-f715-4c64-9ee2-b3c6fd8e9522.png)

- 输入命令`start.bat`，启动 fullnode

![](https://pic3.zhimg.com/80/v2-48fc0b24d573deafb0bbb3f56b58205f_1440w.png)

## 二、 PoS 注册（区块数1200，预计10月9日18时10分开始）
### 1

第一次启动节点，会需要设置密码，用来加密PoS的私钥。屏幕上显示如下内容的时候输入密码，回车继续。

```
PoS key is not detected and will be generated instead, please input your encryption password. This password is needed when you restart the node
Password:
```
- 如遇到运行停止，尝试“回车”
- 如遇到输入密码后如图所示
![](https://pic1.zhimg.com/80/v2-076499d5fddcbaf4f67420e36c80dee8_1440w.png)

打开`run`文件夹下`stderr.txt`文件，如显示如图内容：
![](https://pic1.zhimg.com/80/v2-cb083d039c54a099b81fddf256ecd5a9_1440w.png)
则为密码错误，打开`run`文件夹下`pos_config`文件夹，删除`pos_key`文件，如图所示

![](https://pica.zhimg.com/80/v2-d2428f117cc6b604cd0cac835961b7b5_1440w.png)

然后输入命令`start.bat`，重新启动fullnode

### 2
右键左下角“开始”图标，打开Windows Powershell；

![](https://pic3.zhimg.com/80/v2-912969000d96074df5b9ef178b4ce805_1440w.png)

### 3
复制`run`文件夹地址，在Powershell中输入`cd`+空格+粘贴刚才复制的地址

![](https://pic1.zhimg.com/80/v2-24eddea02c61f7ee17b0b0793651cdfe_1440w.png)

### 4
然后执行下面的命令：

```
./conflux rpc local pos register --power 1
```

![](https://pic1.zhimg.com/80/v2-7044b4ec2c74b6a4a6078e59434a7fe1_1440w.png)

命令行返回值的第一项为注册pos的交易需要的data字段，第二项为pos的账户地址（暂时用不到）。

### 5
打开 http://8.142.2.208/ 页面，登录自己的钱包（确认配置在测试网），等待账户余额变化，此过程可能需要数分钟

![](https://pic1.zhimg.com/80/v2-bcba1fc3774a7504515aa3b2789b1ff4_1440w.png)
![](https://pic1.zhimg.com/80/v2-3a23b44056fc8a66d1f705dda48f78a7_1440w.png)

### 6
点击“Stake CFX 以获得票数”，选择抵押CFX的数量（至少100个），并点击“抵押”按钮，抵押需要进行portal确认；

![](https://pic1.zhimg.com/80/v2-498a9b71b069ba64bc24fa95d3fc41c4_1440w.png)


### 7
抵押成功后，点击按钮“进行PoS锁仓以获得利息”，粘贴填入第4步获取到的data字段，选择锁仓票数（100CFX算1票），点击“首次注册”按钮，并在portal中签名确认。

![](https://pic3.zhimg.com/80/v2-629f907d3874c0e3bf7779eb43f22659_1440w.png)

## 三、PoS过渡测试（区块数122400，预计10月10日11时开始；区块高度200000，约10月11日10时前完成）

GitHub下载链接:https://github.com/conflux-fans/Conflux-PoS-test/releases/tag/conflux_v1.2.0-beta-3

下载链接内的压缩包`pos.config_conflux_win10_x64_v1.2.0-beta-1`，将解压后文件夹内的所有文件移至`run`文件夹的`pos_config`目录下，期间保持程序正常运行

    
### Q&A
**Q1: pos_config文件下的pos_key删除了怎么办？**

A1: “pos_config文件下的pos_key”这个文件不要轻易删除。
如果删除了，需要重新连接 http://8.142.2.208/ ，退出质押，等9个小时之后CFX解锁后重新注册。
这时候建议使用新Conflux地址（账户）重新开始测试。

**Q2:卡了有20多分钟了，如何处理？**

A2：重启程序

**Q3：第一轮测试结束，第二轮测试的时候，抵押CFX执行合约无法完成交易。**

A3: 在portal->点击头像->设置->高级 中找到“自定义 nonce”开关打开，发交易时就会多出一个填写 nonce 的框，将nonce改成0

**Q4: 测试遇到问题，该如何反馈？**

A4：测试遇到问题，请将stderr.txt、pos.log和log文件夹，打包上传至百度网盘，并将链接分享给群内@Coding

**Q5：如何退出？**

A5: 点击锁仓页面中的“解锁退出”按钮即可。

![](https://pic2.zhimg.com/80/v2-ce5ace290c84107cb0e1adc3d811285d_1440w.png)

**Q6: 重启节点注意：**

A6: 需要输入和第一次启动的时候相同的密钥才能正常启动：

```
PoS key detected, please input your encryption password.
Password:
```



