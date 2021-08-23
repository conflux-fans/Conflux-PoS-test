### 1.设置新的 Chorme账户
1. 打开Chrome浏览器，点击右上角用户头像，点击弹出窗口最下方添加个人资料

![](https://forum.conflux.fun/uploads/default/original/2X/7/73a8893c699bd52b4cd01d0e76957749a061733b.png)


2. 选择“在不登录账号的情况下继续”，创建访客账号
3. 自定义个人新账号，点击“完成”
4. 此时，右上角已自动切换为新账号

### 2.安装ConfluxPortal
在新的 Chorme账户中安装ConfluxPortal

参见：ConfluxPortal v0.6.10 更新指南 ：https://forum.conflux.fun/t/confluxportal-v0-6-10/9284
### 3.配置网络

![](https://forum.conflux.fun/uploads/default/original/2X/9/918ed1396d77909922f4f7440894426ec33d548f.png)

网络名称填写：PoS testnet1

RPC填写：http://101.132.158.162:12537

![](https://forum.conflux.fun/uploads/default/original/2X/4/4f8287063151f8a549a4d23e9e57e6c379833c8c.png)

### 4.配置fullnode程序
#### Windows 测试说明
测试须知
1. 建议关闭杀毒软件
2. win 10 版本1903以上

#### 运行文件


**Fullnode 程序**:conflux_win10_x64_pos_testnet.zip

#### 运行 conflux 准备

- 创建目录：conflux
- 分别将下载包解压至目录

⚠ 目录结构为

```
conflux
└── run
    └── conflux.exe
    └── pos_testnet.toml
    └── log.yaml
    └── pos_config
```

#### 配置说明

`pos_testnet.toml` 文件中需要进行两步修改

一、
```
# mining_author="net8888:xxxxxxxxxx..."
```
> 设置成自己的地址（以net8888:开头）

> 移除前缀: `#`


二、
```
 # mining_type = "stratum"
```
> 移除前缀: `#`

> 将"stratum"替换为"cpu"


### 5.开启测试模式

在常规布置之外，再将log.yaml文件打开后找到改图位置，将所有info替换成debug，后保存并退出。


![](https://forum.conflux.fun/uploads/default/original/2X/4/4a8e65cadc1e4193373888a00ded57a10f43eda6.png)


### 6.运行 fullnode 程序

- 打开 **run** 文件夹，按如图所示，右键复制地址

![](https://forum.conflux.fun/uploads/default/original/2X/7/7f6ae163acbfdc91c3627341d9e7af3b8f00da8f.png)

- 键盘输入`win+R` ，在弹出窗口中输入 `cmd` ，进入命令行界面
- 输入`cd`+空格+粘贴刚才复制的地址
- 输入以下命令，启动 fullnode：
```bash
start.bat
```

### 7.启动 PoS

1. 第一次启动节点，会需要设置密码，用来加密PoS的私钥。屏幕上显示如下内容的时候输入密码，回车继续。

```
PoS key is not detected and will be generated instead, please input your encryption password. This password is needed when you restart the node
Password:
```

2. 右键左下角“开始”图标，打开Windows Powershell；
3. 复制`run`文件夹地址，在Powershell中输入`cd`+空格+粘贴刚才复制的地址，然后执行下面的命令：

```
./conflux rpc local pos register --power 1
```
命令行返回值的第一项为注册pos的交易需要的data字段，第二项为pos的账户地址（暂时用不到）。

4. 打开 http://8.142.2.208/ 页面，登录自己的钱包（确认配置在测试网），等待账户余额变化，此过程可能需要数分钟
5. 点击“Stake CFX 以获得票数”，选择抵押CFX的数量（至少100个），并点击“抵押”按钮，抵押需要进行portal确认；
6. 抵押成功后，点击按钮“进行PoS锁仓以获得利息”，粘贴填入第三步获取到的data字段，选择锁仓票数（100CFX算1票），点击“首次注册”按钮，并在portal中签名确认。

___

#### 关闭 POS 挖矿
想要退出时，点击锁仓页面中的“解锁退出”按钮即可。
___
    
 ### 重启节点
 
    之后重启节点的时候需要输入和第一次启动的时候相同的密钥才能正常启动：


```
PoS key detected, please input your encryption password.
Password:
```
    










