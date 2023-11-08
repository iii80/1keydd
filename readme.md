1keydd: 省事一键DD云虚拟机云容器云桌面云开发(带镜像有演示)
=====

1keydd是一套可在线一键安装构建系统的脚本和os最小核心，及一套学习编程语言的最小实践环境选型方案。   

 * 作为1keydd的安装和构建脚本和最小核心部分，基于debianinstaller增强,onekeydevdesk可将你的日用os接入onekeydevdesk核心，变成可一键安装，可同步可集群的容器多版本的虚拟机。  
 * 作为1keydd的实用os shell，基于pve in a nutshell+racketlang，devdeskos实现了一套统一透明ve+一套统一语言（作为pve的developermode存在），及一套学习编程语言的最小实践环境选型方案。    

> 1keydd也指代：1keystokedd,1keydowndd,1keynotedevdesk,1keydevabledocker,1keydiskdump,1keydeepindsm,1keydebiandist,1keydebiandesk,1keydevdeploy,1keydebugdemo,1key desk dock,1key datacenter and desk,1key dir disk,1key deconterized desk,1kilometer distance to dev,1key for dev over dev(second dev),etc ..

项目地址：[https://github.com/minlearn/1keydd](https://github.com/minlearn/1keydd)

演示与特性
-----

onekeydevdesk支持多种在线安装方式(nativedi,wgetdd,liveuntar,nc restore,inplace dd)及丰富的可调试信息，双进度显示(vnc,web)，支持双架构amd,arm双网栈ipv4,ipv6，支持自扩硬盘和智能嵌入静态ip参数(包括/32这样的特殊掩码支持)，支持免d坏模式，可达成90%的linux成功率,80%的other os成功率  
![](https://github.com/minlearn/minlearnprogramming/raw/master/_build/assets/1keydevdesk.png)

onekeydevdesk支持一键dd和构建devdeskos，devdeskos是onekeydevdesk的shell os，作为构建+集成范例存在。支持左栏清爽模式，集成pbs服务和存储（ 安装演示：[https://www.bilibili.com/video/BV1pr4y1j75w/](https://www.bilibili.com/video/BV1pr4y1j75w/) ）,原生lxc vnc桌面（ 安装演示：[https://www.bilibili.com/video/BV1PV4y1o7f2/](https://www.bilibili.com/video/BV1PV4y1o7f2/) ），512m小内存可安装，todo:支持分离式前端pveman，支持原生redriod+scrcpyws,支持容器级debugger接入和edtior ide  
![](https://github.com/minlearn/minlearnprogramming/raw/master/_build/assets/1keydevdeskos.png)

onekeydevdesk支持一键dd其它多种os，如，支持win uefi/bios gpt二合一兼容，无视机型差别和无须手动，毫无修改毫无感知地以同一效果运行（安装演示：[https://www.bilibili.com/video/BV17B4y1b79Y/](https://www.bilibili.com/video/BV17B4y1b79Y/) ）,支持dsm直接安装在云主机上，dsm无须嵌套虚拟化支持>2T硬盘作为启动硬盘（安装演示：[https://www.bilibili.com/video/BV1ug411N7tn/](https://www.bilibili.com/video/BV1ug411N7tn/) ）,支持osx使用标准全套kvm驱动和bios机型配置，需要安装在支持嵌套虚拟化的2C2G以上云主机上（1c1.5g/2c2g给osx, 2c2g/3c3g给osx母鸡留1c1g最好），与本地组matedesk，win11类同。不做说明的情况下，上述镜像均为脚本内置镜像，第三方gz镜像并不提供开放托管和安装。  

onekeydevdesk+devdeskos支持扩展，包括az,servarica,oracle/oracle arm,ksle,bwg10g512m,及接入无限增加的机型和系统：   
完整支持查看hub页，更多演示和特性请看和项目文档库[《更多文档》](/1keydd/docs/)部分

下载安装及用法
-----

以下尽量在debian系linux云主机或本地虚拟机下完成,centos不推荐  

基本用法:  

 * 简单前端交互模式  
`wget -qO- inst.sh | bash`   

 * 指定安装目标os镜像：debian是原生方式安装的纯净debian10,devdeskos是live方式安装的devdeskos,debian10r是dd方式安装的debian10的raw系统硬盘格式经过gzip打包,自定义镜像是dd方式安装的raw系统硬盘格式经过gzip打包后托管的http/https地址  
`wget -qO- inst.sh | bash -s - -t debian,devdeskos,debian10r,或自定gz镜像`  

脚本运行后会重启进入dd过程，进入后，如有网络直接访问ip:80，会看到vnc进度，如果要进一步查看问题访问ip:8000。如无网络5分钟后会重启,并进入DD前的正常系统。免破坏系统。
目标os安装后，会自动扩展磁盘空间和调整网络,用户名为root/admininistraor，密码为1keydd。  

高级用法:  

 * 指定debian镜像源  
`wget -qO- inst.sh | bash -s - -m http/https/xxxx ......`  

 * 指定第一张网卡名  
`wget -qO- inst.sh | bash -s - -i enp0s1 ......`  

 * 指定静态网络配置  
`wget -qO- inst.sh | bash -s - -n ipv4,netmask,gateway .....`  

 * 指定第一个硬盘名(你也可以填分区名把镜像d到仅一个分区里)  
`wget -qO- inst.sh | bash -s - -p nvme0n1 ......`  

 * 指定用户密码(不指定为1keydd)  
`wget -qO- inst.sh | bash -s - -w mypass ......`  

 * 指定dd完成后动作(不扩盘,不注入静态ip,不重启)  
`wget -qO- inst.sh | bash -s - -o 1:noexpanddisk/2:noinjectnetcfg/3:noreboot ......` 

 * 进入救援/DRYRUN/DEBUG模式,此模式进入dd环境开启一个可sshd空密码登录的ssh,可作DD前验证  
`wget -qO- inst.sh | bash -s - -d`  

自托管1keydd:   

 * 通过docker:  
`docker pull minlearn/1keydd`  
`docker run -d --name my1keydd -e m=你的托管顶层地址 -p 80:80 minlearn/1keydd`  

建立托管后，用"你的托管顶层地址/1keydd/inst.sh"脚本地址调用脚本即可  

服务
-----

项目分免费部分和服务性收费部分  

| 项目                      | 是否免费 | 说明 |
| :------:                 | :-:     | :-: |
| inst.sh                  |  √      | 拥有常见vps和独服机型上DD常见系统能力，可解决你DD中大部分问题，提供常见内建镜像 |
| devdeskos                |  √      | 已经开放的devdeskos全部功能 |
| 安装服务                  |  ×      | 本人长期接有偿付费dd，解决疑难机型DD问题并总结DD方案1次60元起，可送加群服务 |
| 镜像定制                  |  ×      | 本人长期接有偿付费dd，定制镜像服务1次60元起，可送加群服务 |
| 加内部群和社区             |  ×      | 基于debian11和pve7核心的inst.sh,devdeskos + 一个tg群和一个论坛 = 群内邀请团资格 + 坛内终身免费咨询技术支持 + 更多不定期福利,比如[《更多第三方镜像》](/1keydd/hub/) |
| ci.sh                    |  ×      | 支持为inst.sh扩展驱动定制机型/为devdeskos集成功能/生成内置镜像，终身源码仓库和开发过程全共享 |
| ...                      | ...     | ... |

项目维护需要长期付出大量精力，请捐助或付费支持作者  

如何支持：

 * 本人长期接有偿付费dd含解决疑难机型DD问题和定制镜像服务，价格各60元起，加如下作者个人TG：简单说明需求或说明来意即可  
[minlearn_1keydd](https://t.me/minlearn_1keydd)

 * 或直接任意捐助打赏我任意数值虚拟币,直接打赏60rmb/10u可送加群服务  
`怎么捐助: 用支持tron链或polygon链的钱包APP扫描下列钱包地址，或二维码`  

USDT/BTC/ETH/TRX: [TPvrETkN21H8fagFjyYAECihyRhrRAMCTR](https://tronscan.io/#/address/TPvrETkN21H8fagFjyYAECihyRhrRAMCTR)  
USDT/MATIC: [0x650d3325f875a17fb7555611cfc9ad365eb5821b](https://polygonscan.com/address/0x650d3325f875a17fb7555611cfc9ad365eb5821b)   

![](https://github.com/minlearn/minlearnprogramming/raw/master/_build/assets/donate.png)

-----


此项目关联 https://github.com/minlearn/minlearnprogramming/raw/master/p/1keyddopen/ ，同时它是为配合我在《minlearnprogramming》最小编程/统一开发的想法的一个支持项目。作为一套"虚拟机管理器"到系统最小核心，及由基于此核心+入devops，并相关管理工具和相关脚本，最终组合实现的一套"一键开发桌面理念"系统存在。  

本项目长期保存

