<p style="text-align:center;"><span style="font-size:20px;"><strong>IPFS 下载快速入门，只想知道怎么下载看这个就可</strong></span></p>

<p style="text-align:center;">https://www.youtube.com/watch?v=Xof9kek1orU</p>

<p style="text-align:center;">如果看不了油管视频，可以在 <a href="https://gateway.pinata.cloud/ipfs/bafybeietvf3b44xlecktxegyutdwtedse42qriv7tisc4c7nzhmloqdq6i?filename=1.mp4" rel="noreferrer noopener" target="_blank"><strong>备选线路1</strong></a> <a href="https://lensshare.4everland.link/ipfs/bafybeietvf3b44xlecktxegyutdwtedse42qriv7tisc4c7nzhmloqdq6i?filename=1.mp4" rel="noreferrer noopener" target="_blank"><strong>备选线路2</strong></a>&nbsp; <a href="https://gw.ipfs-lens.dev/ipfs/bafybeietvf3b44xlecktxegyutdwtedse42qriv7tisc4c7nzhmloqdq6i?filename=1.mp4" rel="noreferrer noopener" target="_blank"><strong>备选线路3</strong></a> 观看</p>

本文首发在绅士仓库：
[https://cangku.moe/archives/212530](https://cangku.moe/archives/212530)
[https://www.south-plus.net/read.php?tid-2357385.html](https://www.south-plus.net/read.php?tid-2357385.html)

IPFS 下载辅助油猴脚本：[https://github.com/cenglin123/ipfs-cid-copy-helper](https://github.com/cenglin123/ipfs-cid-copy-helper)

## IPFS 分享资源快速上手及其适用场景浅议

![IPFS](https://pic.cangku.moe/images/2025/06/06/1UPB2.png)

## 前言

其实早在 2020 年（即秒传时代的开端）就已经有[贴子](https://gmgard.com/gm108719)推荐 IPFS 作为分享方案了，属于分享账号大封禁之后众多分享技术路线探索中的一支。只是限于当时的 IPFS 仍然处于早期阶段，各种平台等配套设施并不完善，大部分人对其理解也是变种的 BT，没有成功普及，随后和其他路线一样，在秒传的兴起中变得无人问津。

随着 2023 年末期百度开始逐步修复秒传，寻找新路线又重新开始被重视。期间从分卷压缩、专有加密到文件隐写等方法不一而足。这些探索都是值得肯定的，但是另一方面，对于网盘分享领域的诸多问题其实一直没有得到解答，对于炸链现象的解释显得笼统且不精确，由此带来的防炸方案也是五花八门，谁也不能说服谁。

比如，关于【为什么会炸链】这个问题，就有在线解压说、文件名敏感说、账号监控说、玄学说、严格审查说、举报说等；对应的防炸方法也就是分卷压缩/多层压缩、改后缀名、换 IP、以及使用 VeraCrypt 等专业加密程序方案、伪装MP4/图片/二进制转码等文件隐写方案。

对上述问题最终取得突破的是文件隐写方案，但并不是因为证明了隐写方案才是最有效的方案，而是以隐写文件为基础，通过[控制变量试验](https://bafybeiadpfp7wu6qwmyighdel3qw2eqqqacrmyuxfdwc5u4vwmhiw4mqce.ipfs.dweb.link/)证明了在百度网盘上的举报是【[无解](https://hxcy.top/541697.html)】的，进而整体否定了通过改进打包技术来防炸这条路线。（对此问题感兴趣可以点击链接中的文章详细查看）

在这样的情况下，IPFS 方案又逐渐成为了可选项了，尽管当前的 IPFS 仍不能说拥有足够充分的配套设施，但是相比于 2020 年，已经有了一些进步和积累，比如本文第 4 节会谈及的文件托管平台，使得 IPFS 在保留 BT 优点(无法举报)、解决 BT 的某些缺点(低安全性)的同时，在方便性上部分甚至绝对超过了以百度为代表的传统中心化网盘。

本文则是 IPFS 快速上手教程，旨在快速入门 IPFS 的基本操作。详细介绍了 IPFS（星际文件系统）的使用方法、优缺点及其在资源分享中的应用场景。文章首先讲解了 IPFS 的基本操作，包括文件的上传、固定、分享和下载。随后，介绍了 IPFS 本地文件管理和使用托管平台的方法。最后，文章对比了 IPFS 与传统网盘分享方案，提出了分场景使用不同级别分享方案的建议， 分析了 IPFS 作为最终手段，在应对恶意举报问题上的优势。

文件结构说明：
> 1、2、3 节主要讲解 IPFS 的基本使用方法；
> 4 节讲如何使用托管平台托管文件；
> 5 节讲使用 IPFS 轻量化做种；
> 6 、7 节讨论了 IPFS 安全性方面的问题。


**更新**：

> 2025/05/28 把本地做种部分进一步调整，将另一篇进阶教程文章的内容合并。
> 2025/05/19 IPFS 上手教程结构调整，把移动仓库调整到第一节，同时去除了 Chainsafe 相关内容，加入了 aleph 相关的内容
> 2024/11/03：4.4 节更新 IPNS 用法相关内容介绍，可以在无服务器的情况下创建类似于域名的网址用于可更新的分享，详见目录；同时修正了一些文章错漏。


**文章目录**

![1qnHD.jpg](https://pic.cangku.moe/images/2025/06/22/1qnHD.jpg)


## 关于 IPFS 的几个要点：

1. IPFS 上传和下载都**不需要公网 IP，也不需要 VPS**，但是注意如果挂了梯子【**不要开启 TUN 模式**，否则你的流量很快就没了】。
2. IPFS 发布文件需要先**固定**（类比 BT 的做种），然后可以通过浏览器整合下载。
3. IPFS 除了自己固定（做种），也可以选择**托管平台**托管，代为做种。
3. IPFS 发布的文件大部分都可以**直连下载**。

先在这里下载 IPFS 客户端并安装：

[https://docs.ipfs.tech/install/ipfs-desktop/#windows](https://docs.ipfs.tech/install/ipfs-desktop/#windows)

以下是操作流程的详细说明。

如果上面的链接打不开，或者找不到，可以从下面的备用镜像链接下载（）

> IPFS 直链：[https://bafybeifh2jdor3r26x4adskx2rlz33ada64mducx2iq6oa3iqh5ir42zby.eth.sucks?filename=IPFS-Desktop-Setup-0.38.0.exe](https://bafybeifh2jdor3r26x4adskx2rlz33ada64mducx2iq6oa3iqh5ir42zby.eth.sucks?filename=IPFS-Desktop-Setup-0.38.0.exe)

以下是操作流程的详细说明。


## 1. 固定并分享文件

### 1.1 固定想要共享的文件

在 IPFS 中，每一个文件都有一个独一无二的标识符 CID ，CID 在 IPFS 中对应具体文件，类似于 BT 的磁链，**分享 CID 就等于分享文件**，只需要知道 CID 即可下载文件。

CID 的示例如下（有两种格式 v0 和 v1，分别以 Qm 和 ba 开头）：

```
QmPKhevNWUx89XBU82XF4UYs2xsdxZnG2xPz2uZsA6Yatm  
```
```
bafybeibcr7x6d2bo43ce6xaye6d6aogvbfmeokphpsvjlqv27udl34ads4
```

目前推荐使用后者。

在配置中的 Import 部分把 CidVersion 参数改为 1 ，然后保存并重启 IPFS 即可。

![2622b838c9ffae6bff2194898b9fbb31.webp](https://file.cangku.moe/images/2622b838c9ffae6bff2194898b9fbb31.webp)

配置完毕后，就可以开始固定文件了

![1rqjK.png](https://pic.cangku.moe/images/2025/07/09/1rqjK.png)

右键点击上传后的文件，设置固定

![右键点击上传后的文件，设置固定](https://github.com/user-attachments/assets/911ea750-86e4-4507-8729-88f45ae7bbdf)


固定在本地节点

![1rxe6.png](https://pic.cangku.moe/images/2025/07/09/1rxe6.png)



### 1.2 复制 CID 以发布文件

固定成功后再次点击右键，选择复制 CID ，就可以发布文件了。

可以采用分享链接的方式分享文件，由于默认的公共网关被墙了，在分享前建议修改 IPFS 公共网关。

![1rT4i.webp](https://pic.cangku.moe/images/2025/07/09/1rT4i.webp)


可用 IPFS 公共网关（随时更新）参考：
[https://k51qzi5uqu5djx3hvne57dwcotpc8h76o2ygrxh05kck11j6wnhvse8jrfzf2w.ipns.dweb.link/](https://k51qzi5uqu5djx3hvne57dwcotpc8h76o2ygrxh05kck11j6wnhvse8jrfzf2w.ipns.dweb.link/)

在下面的网址可以找到更多的可用公共网关
[https://ipfs.github.io/public-gateway-checker/](https://ipfs.github.io/public-gateway-checker/)

设置完成后右键文件-分享链接即可

![79b302b20e96503aab461e9af616234c.webp](https://file.cangku.moe/images/79b302b20e96503aab461e9af616234c.webp)

![b06de1123161326c350d2207be76cb7c.webp](https://file.cangku.moe/images/b06de1123161326c350d2207be76cb7c.webp)

分享前可以检测一下自己网络的可用性。

此网址可以检查自己的 IPFS 网络的可用性：
https://check.ipfs.network/ 

下面的 4 个检查得至少满足前 3 个，如果你有公网 IP 则会有第 4 个。

![](https://pic.cangku.moe/images/2025/05/19/y5LRk.png)

![](https://img.picgo.net/2024/12/05/20241205203239f608787b9912c03c.png)

### 1.3 移动本地文件仓库

IPFS 安装以后，默认会在用户路径（C:\\Users\\你的用户名）下方创建一个名为 `.ipfs` 的文件夹，用来存放固定的文件，如果 C 盘空间不足，可以选择移动 IPFS 仓库的默认位置。右键任务栏 IPFS 程序的图标，然后选择 Move Repository Location 即可。

![](https://img.picgo.net/2024/12/05/202412052026210a72f57affe47d3b.png)



## 2. 根据 CID 下载文件

### 2.1 使用 IPFS 原生下载功能下载文件

下载文件和上传文件是类似的，首先需要导入文件

![](https://img.picgo.net/2024/12/05/2024120520224833893768347565be.png)

在弹出的窗口中输入 CID ，可以自行指定文件名

![](https://img.picgo.net/2024/12/05/2024120520230362a89a25b8b826ca.png)

在下载前建议先设置固定，只要固定完成了，文件就一定可以保存到本地，以避免直接下载过程中出现错误。（固定一个来自 IPFS 路径的 CID 可能会需要一定时间，因为要从其他节点拉取文件）

固定完成后点击右键，选择下载：

![](https://img.picgo.net/2024/12/05/202412052023126cc4be7ad143ecdc.png)

接下来会使用浏览器的下载功能进行文件下载，先固定后下载或者直接下载这 2 种下载方式，原理都类似于 BT 是 P2P 的，能否下载成功取决于是否有人在做种。

![1rXkq.png](https://pic.cangku.moe/images/2025/07/09/1rXkq.png)

如果安装了 IDM、FDM 等下载软件，也可以使用这些软件接管下载，比如我用的是 FDM ：

![1rmIp.png](https://pic.cangku.moe/images/2025/07/09/1rmIp.png)


### 2.2 使用 IPFS 公共网关下载文件

除了类似于 BT 的 P2P 以外，IPFS 还可以采用公共网关创建分享链接的方式分享文件，公共网关本身也是一个 IPFS 节点，但拥有公网 IP ，连接速度较快，可以帮助其他节点下载，具体来说就是用它生成直链，让下载者用这个直链下载，这是比较推荐的 IPFS 分享方式。

IPFS下载链接结构为 **网关+CID** 

示意图如下：
![](https://file.cangku.moe/images/132ec0b5c32bdd957bfa2678dec8f809.webp)

使用这种方式分享的时候下载者不需要软件，用浏览器、IDM 等即可直连下载。

由于默认的公共网关被墙了，在分享前需要修改 IPFS 的公共网关，可以修改为以下网关中的一个：

```
https://ipfs.hypha.coop
https://gw.ipfs-lens.dev
https://gateway.pinata.cloud
https://eth.sucks
https://i0.img2ipfs.com
https://gw.crustgw.work
https://gw.crust-gateway.xyz
```

按照下图所示设置：

![](https://img.picgo.net/2024/12/05/6d4b9322548aaf6cb90f580afda8c06a9205a4ba7e9a6380.webp)

然后右键文件-分享链接即可

![](https://img.picgo.net/2024/12/05/79b302b20e96503aab461e9af616234c6d3fabd073778c2a.webp)

![](https://img.picgo.net/2024/12/05/b06de1123161326c350d2207be76cb7c0d6f3e975b476753.webp)


其他寻找公共网关的方法：

1. 可以在 [Best IPFS Gateway](https://www.bestipfs.net/) 输入 CID 来搜索更多合适的网关，搜索到以后点击右侧的下载按钮即可。
2. 在下面的网址中可以找到更多的可用公共网关
[https://k51qzi5uqu5djx3hvne57dwcotpc8h76o2ygrxh05kck11j6wnhvse8jrfzf2w.ipns.dweb.link/](https://k51qzi5uqu5djx3hvne57dwcotpc8h76o2ygrxh05kck11j6wnhvse8jrfzf2w.ipns.dweb.link/)
[https://ipfs.github.io/public-gateway-checker/](https://ipfs.github.io/public-gateway-checker/)


### 2.3 使用 IPFS 本地网关下载文件

**公共网关本身也是一个 IPFS 节点**，经由公共网关访问文件或文件夹 CID 可以理解为由对方代理来连接到 IPFS 网络中的资源，由于这些网关有公网 IP ，速度也比普通的家宽更快，所以通常建议用公共网关访问并下载资源。

但是公共网关也可能**面临被恶意举报导致封 CID 的情况**，这种时候除了更换其他公共网关，也可以用自己 IPFS 节点的本地网关访问资源，这种访问类似于 BT 是纯 P2P 的，也就是说，**即使这个 CID 在所有公共网关上都被屏蔽了，只要你自己不屏蔽这个 CID 就能访问**。

在本地的 IPFS 启动后，在浏览器地址栏中输入 CID，后面加上 `.ipfs.localhost:8080` ，即可用 IPFS 的本地网关查看并下载文件，示例如下：

http://bafybeihon37a3qtxqynvphkt4ebe3hd42tdrfw4gstsadka5yijz3fjbfe.ipfs.localhost:8080
或者在 CID 前面加上路径形式的本地网关：
http://127.0.0.1:8080/ipfs/bafybeihon37a3qtxqynvphkt4ebe3hd42tdrfw4gstsadka5yijz3fjbfe/
（注意是 http 不是 https ，这里的 http 只用来连接本地的 IPFS 节点，相当于 IPFS 成了代理，所以不必担心安全性）

这个 CID 对应的是一个 html 文件，因此被浏览器渲染成了网页的样子，按 ctrl+s 可以把这个文件下载到本地查看，对于其他格式资源也是同理，这也就是为什么 IPFS 分享的东西能被浏览器或者 IDM 或者 FDM 等下载器直接下载的原因了。

![](https://img.picgo.net/2025/01/10/PixPin_2025-01-10_17-56-16727e15eafe5521eb.jpg)

此外，在安装 IPFS 客户端的情况下，在浏览器地址栏输入：

```
ipfs://bafybeihon37a3qtxqynvphkt4ebe3hd42tdrfw4gstsadka5yijz3fjbfe
```

也会自动打开刚才的本地网关。

从上面这个例子可以看出，ipfs 某种意义上可以代替 http 来访问互联网中的内容，CID 就是内容的地址，IPFS 的这种特性称为“**内容寻址**”，也就是不根据 IP 地址而根据内容本身的哈希值来在网络中查找（这点类似于 BT）。

`.ipfs.localhost:8080` 中最后 4 位数字为本地网关的端口号，通常为 `8080`，但是有时候也可能变化，此时端口被占用就无法使用，常见原因比如酸奶网盘与 IPFS 客户端冲突等，如果发现本地网关无法使用，如下图所示：

![](https://img.picgo.net/2025/01/10/PixPin_2025-01-10_17-47-21698d8847b5155f08.jpg)

此时需要查看本地节点的 .`ipfs` 仓库中的 `config` 文件，右键用记事本打开后，下图中箭头所指的四位数字就是你的本地网关端口号，使用这个端口号即可。

![](https://img.picgo.net/2025/01/10/PixPin_2025-01-10_17-41-459321c657d8751ada.jpg)

![](https://img.picgo.net/2025/01/10/PixPin_2025-01-10_17-44-225dc315a75c33eb11.jpg)


### 2.4 使用 FDM 批量下载 IPFS 链接

在安装此[油猴脚本](https://cangku.moe/archives/214632)的情况下，可以使用 FDM 来批量下载。

[**FDM**](https://www.freedownloadmanager.org/zh/) **(Free Download Manager)** 是一款完全免费的下载软件，不会存在破解版 IDM 可能的弹窗问题，这里使用 FDM 来说明如何批量下载已复制的下载链接。

首先在这里下载最新版的 FDM 并安装：

[https://files2.freedownloadmanager.org/6/latest/fdm_x64_setup.exe](https://files2.freedownloadmanager.org/6/latest/fdm_x64_setup.exe)

安装完成后，复制链接，点右上角的三根横线，从剪贴板粘贴链接，选择下载路径进行下载即可。

  
![1c7d5560f8d3e0fbf6fb2e9b57ed5933.webp](https://file.cangku.moe/images/1c7d5560f8d3e0fbf6fb2e9b57ed5933.webp)


## 3. IPFS 其他细节操作

### 3.1 清理非固定文件释放磁盘空间

当 IPFS 的本地文件过多，可以选择任务栏图标中的 Run Garbage Collector 进行清理，这个操作会清理所有没有在文件选项卡中显示的文件释放磁盘空间。

![](https://pic.cangku.moe/images/2025/05/19/y51dL.jpg)


### 3.2 IPFS 辅助油猴脚本

此油猴脚本用于自动识别网页中的 IPFS 链接和 CID，提供一键复制、网关测速和批量操作功能。

1. 安装后鼠标移到 CID 上可以弹出悬浮窗。
2. 在右下角显示**批量复制 CID 、文件名、下载链接**按钮，浮窗可以收起。
3. IPFS 测速器功能，可以测试各大网关能否访问（功能类似[IPFS分享助手](https://github.com/cenglin123/IPFS-ShareAssistant/releases)），内置常见网关，支持自定义网关。

![](https://pic.cangku.moe/images/2025/06/21/1qC9p.jpg)

**Github**：IPFS CID Copy Helper [https://github.com/cenglin123/ipfs-cid-copy-helper](https://github.com/cenglin123/ipfs-cid-copy-helper)

### 3.3 IPFS 分享助手

[IPFS 分享助手](https://github.com/cenglin123/IPFS-ShareAssistant/releases)是本人开发的一个小程序，用来简化 IPFS 分享的流程，主要功能有：

CID 批量计算、文件批量导入、CID 批量拉取、CID 格式转换、分享链接批量生成、批量固定到 Crust 等分享相关的一站式功能。

![](https://img.picgo.net/2024/12/05/20241205202749fc11eecbec452fa3.png)

此处仅简单介绍，具体用法请参阅 [GitHub](https://github.com/cenglin123/IPFS-ShareAssistant/releases)

### 3.4 开启 DHT 加速

**2024-10-09 更新：实际测试，DHT 加速会显著增加 IPFS 的资源消耗，并且相比于其消耗的资源来说对效率的提升较为有限（氪佬随意），在使用 Crust 等托管平台而非自己做种时，不建议开启 DHT 加速**。

在上传之前可以在配置选项卡中如下修改配置信息，开启 DHT 加速，DHT 加速可以提高连接节点数量，增加效率。

```
"AcceleratedDHTClient": true,
```

![](https://img.picgo.net/2024/12/05/20241205203249b7e89dfd81133733.png)

### 3.5 关于分享文件的可用性

IPFS 类似于磁链，也需要有人“做种”，需要有人固定文件（做种），并且在线，才可以下载。

可以在这个网址中检测 CID 是否可用：

[https://explore.ipld.io/](https://explore.ipld.io/)

![](https://img.picgo.net/2024/12/05/20241205203301feb92e5d8dbef6b6.png)

也可以使用 IPFS 分享助手进行测速来确认文件是否可用。

## 4. 使用 IPFS 托管平台托管文件

由于 IPFS 类似 BT 属于去中心化的分享方式，假如没人开机做种，就会导致后续的下载者没有办法下载。这种时候可以使用托管平台托管文件，代为“做种”。用法类似于网盘，但是分享不通过分享系统，而是采用 CID 进行，因此没有审核、举报系统，不管文件保存在哪里，只要 CID 匹配就可以下载到文件。

IPFS 的托管平台有很多，和 IPFS 的网关不同，这些托管平台大多数都没有被墙可直连，比如支付加密货币把文件托管给矿工的 [**Crust**](https://crust.network/) 以及基于 Crust 开发的 [**酸奶网盘**](https://cangku.moe/archives/212970) 、以及目前免费的 [Aleph](https://www.south-plus.net/read.php?tid-2504124-keyword-Aleph.html)。


### 4.1 使用酸奶网盘托管文件到 Crust 平台

```
2025/05/19 更新：由于 Crust 网络现在状态不佳，本节部分的内容仅供参考。
```

本节内容**是一个操作流程**，旨在快速上手，只需要按照流程操作即可，具体的原理及解释详见 4.3 节。

以下正式开始

打开 [https://yoghourt.cloud/](https://yoghourt.cloud/) 酸奶网盘的官网，下载最新版酸奶网盘并安装，或者在这里下载
[https://gw.crustgw.work/ipfs/bafybeiaeq2sblmnjvs27qr7romzc6ryqz5qiy6ng2ltrs7tgxux7rdeqh4?filename=yogurt-cloud-client-0.1.4-setup.exe](https://gw.crustgw.work/ipfs/bafybeiaeq2sblmnjvs27qr7romzc6ryqz5qiy6ng2ltrs7tgxux7rdeqh4?filename=yogurt-cloud-client-0.1.4-setup.exe)

当右下角显示 IPFS 连接成功，即可拖入上传文件

![](https://img.picgo.net/2024/11/06/20241106002704a068479ff75ee1f9.png)

然后等待上传完毕

![](https://img.picgo.net/2024/11/06/202411060027465568a922957fbee4.png)

上传完毕后等待至副本数大于 0

![](https://img.picgo.net/2024/11/06/20241106002939eda4e5db20620942.png)

然后打开 [IPFS 分享助手](https://cangku.moe/archives/213088)：

[https://k51qzi5uqu5dh1ts2qvcw3069src00zyjw0qmwdkb102k8q4ft8bztw75iwi25.eth.sucks/](https://k51qzi5uqu5dh1ts2qvcw3069src00zyjw0qmwdkb102k8q4ft8bztw75iwi25.eth.sucks/)

1. 在右下角的计算器中拖入那个文件，然后计算 CID 后点击【填写CID和文件名到主输入框】，  
2. 填写后点击【下载网关测速】，  
3. 测速完成后点击【生成下载链接】，即可得到能直接链接到资源的链接了，  
4. 再点击【复制下载链接】，即可复制链接并发布，下载的时候只需要打开这个链接，用浏览器或 IDM 就能下载。

![](https://img.picgo.net/2024/11/06/20241106003400214b19f1a669894e.png)


如果某个链接不能用了，把链接中的 CID (即 baf...6cwe 这样的字符串) 复制后填入图中的位置，重复 2 3 4 步骤即可。

下面是最终得到的链接，可以直接在浏览器中打开使用：

```
[img]https://i0.img2ipfs.com/ipfs/bafkreibm2z34rvt5qhbiz3cv4524skjefg2mard7h4i7stqinpi5sl6cwe?filename=%E4%B8%BA%E4%BB%80%E4%B9%88%E8%A6%81%E5%88%86%E4%BA%AB%EF%BC%9F.jpg[/img]
```

这是刚才上传的图

![](https://i0.img2ipfs.com/ipfs/bafkreibm2z34rvt5qhbiz3cv4524skjefg2mard7h4i7stqinpi5sl6cwe?filename=%E4%B8%BA%E4%BB%80%E4%B9%88%E8%A6%81%E5%88%86%E4%BA%AB%EF%BC%9F.jpg)


### 4.2 使用 aleph.im 进行托管

使用 aleph 可以实现类似于 BT 的做种后离线的方式托管给 IPFS 矿工，就目前而言（2025/05/19），效果比 Crust 更好。

详见这 2 篇仓库文章：
[[技巧分享] [IPFS] 通过aleph.im网络存储固定ipfs文件](https://cangku.moe/archives/217781)
[[技巧分享][IPFS] Aleph拉取教程入门版](https://cangku.moe/archives/219272)

IPFS托管网页（上面的访问不了可以看这个）
[[技巧分享] [IPFS] 通过aleph.im网络存储固定ipfs文件](https://bafybeifm5rkvyjlw3mb6n5ymlfjrj25352mz6ixqsxz2uog5gdwipizgtm.eth.sucks/)
[[技巧分享][IPFS] Aleph拉取教程入门版](http://bafybeieccjo7iis64hbq64jz2zrjjhiys2scfpp2gqrdvdxqpxrock5c24.eth.sucks/)

南+
 [[技巧分享] [IPFS] 通过aleph.im网络存储固定ipfs文件](https://www.south-plus.net/read.php?tid-2504124-keyword-IPFS.html)

Aleph 分享助手下载
[https://github.com/cenglin123/aleph-managerGUI](https://github.com/cenglin123/aleph-managerGUI/releases/latest)


### 4.3 使用托管平台搭配 IPNS 托管文件夹

接下来说明一些仅在使用托管平台时推荐的分享技巧。  
  
我们可以使用 **CrustFiles** 或者 [**酸奶网盘**](https://cangku.moe/archives/212970) 、Aleph 等把文件分别托管 (又称上链) 到 IPFS 网络中，然后通过**本地 IPFS 客户端聚合文件以进行管理**。

具体来说，先把文件上传到t托管平台进行托管，然后再把这些已经托管的文件的 CID 导入并聚合到本地 IPFS 的一个文件夹中（不必固定到本地，这样就不会占用本地空间），这样一来，本地做种**只需要做种聚合文件夹即可**，使得文件夹中的内容能被 IPFS 网络访问，**内容则交由托管平台保存，不占用本地空间**。

也因此，在使用托管的情况下 IPFS 的做种比 BT 更轻量，希望大家可以积极帮助他人做种，只需要把别人的文件夹 CID 导入但不固定在本地即可（注意不要改动文件路径中的文件名，否则会导致 CID 发生变化，想重命名进行管理的话，可以新建一个文件夹把东西整个丢进去），如此可以帮助他人保持文件夹路径的可用性。内容托管在矿工那里，做种不消耗自己的流量，也可以减少被运营商查水表的可能性。  
 
由于 IPFS 内容寻址的特性，不同内容的 CID 都是不同的，假如你的内容需要频繁更新，每次都要改链接无疑很不方便。此时可以把聚合文件夹发布到 **IPNS**，把文件夹的 CID 与 IPNS 地址相关联。  

和 CID 不同， IPNS 地址是不变的，特别适合需要持续更新的内容，其内容需要使用你节点的私钥才能更改，可以当成自己的一个“**域名**”来使用。这个“域名”也是去中心化的，保存在 DHT （分布式哈希表）中，只要你的节点**每天至少上一次线**，就可以保证这个“域名”可用，和传统的 HTTP 域名不同， **IPNS 即使关机也不会造成“域名”无法访问**。（如果你有普通域名的的话，可以把 CID 和域名关联起来）  

下面是我用 IPNS 发布的 IPFS 分享助手软件，其中 k51...wi25 就是 IPNS “域名”，.eth.sucks 则是子域名形式的公共网关。

[https://k51qzi5uqu5dh1ts2qvcw3069src00zyjw0qmwdkb102k8q4ft8bztw75iwi25.eth.sucks](https://k51qzi5uqu5dh1ts2qvcw3069src00zyjw0qmwdkb102k8q4ft8bztw75iwi25.eth.sucks/)

上面是子域名形式的链接，路径形式的链接则应该如下：

[https://eth.sucks/ipns/k51qzi5uqu5dh1ts2qvcw3069src00zyjw0qmwdkb102k8q4ft8bztw75iwi25](https://eth.sucks/ipns/k51qzi5uqu5dh1ts2qvcw3069src00zyjw0qmwdkb102k8q4ft8bztw75iwi25)

用本地网关进行访问时，子域名形式和路径形式的链接如下：

http://k51qzi5uqu5dh1ts2qvcw3069src00zyjw0qmwdkb102k8q4ft8bztw75iwi25.ipns.localhost:8080

http://127.0.0.1:8080/ipns/k51qzi5uqu5dh1ts2qvcw3069src00zyjw0qmwdkb102k8q4ft8bztw75iwi25

接下来我新生成一个名为 test 的 IPNS 密钥用来发布其他文件夹， IPNS 密钥的地址是固定的，这样每次更新内容后只需要把更新后的文件夹 CID 重新发布一次 IPNS 即可，不用更新链接。

![f3d7d49820eff9869192e8db63618515.webp](https://file.cangku.moe/images/f3d7d49820eff9869192e8db63618515.webp)

 ![8bd2890e02a1b8ace4d0e3674d7da23d.webp](https://file.cangku.moe/images/8bd2890e02a1b8ace4d0e3674d7da23d.webp)

点击发布，然后稍作等待：

![bd1f34ac459e15aa7ad3c31d608f91ab.webp](https://file.cangku.moe/images/bd1f34ac459e15aa7ad3c31d608f91ab.webp)

复制上面的地址就可以发布了，由于 DHT 网络的广播需要时间，让 IPNS “域名”生效可能需要半个小时至一个小时左右，发布后稍作等待即可。

效果如下：
[https://ipfs.io/ipns/k51qzi5uqu5dk5cbbjykfthqkz6qh9r98zauauz2n6j843rv3e93fgbfh4abiu](https://ipfs.io/ipns/k51qzi5uqu5dk5cbbjykfthqkz6qh9r98zauauz2n6j843rv3e93fgbfh4abiu)
也可以通过比如 [4everland.org](https://dashboard.4everland.org/) 这样的平台来免费托管 IPNS 地址，具体可以参考[这篇文章](https://cangku.moe/archives/216179#heading-13)的第 3 节。

关于更多托管平台：[盘点主流IPFS托管平台:功能、限制与推荐指数全面对比](https://hxcy.top/548738.html)

## 5. IPFS 本地文件管理：把 IPFS 当作网盘来用

### 5.1 IPFS 能否像网盘那样“转存”？

IPFS 全称“**星际文件系统**”，既然是文件系统，自然是能够进行文件管理的，使用时的手感**非常类似秒传链接**。

具体来说，就是把 CID 导入到 IPFS 中但不固定到本地节点，这样就能在不占用本地空间的情况下进行文件管理了。

可以给大家看一下我的某个 IPFS 仓库，注意右上角的显示大小和实际占用大小。

![](https://img.picgo.net/2024/11/14/PixPin_2024-11-14_16-20-32f54afe96d14f94af.jpg)

在这样的情况下，**CID 也就可以类比百度网盘的秒传链接了，本地的 IPFS 节点则类比一个网盘客户端**。而导入 CID 的过程自然就是“**转存**”了。不过这里的转存我加了双引号，是因为虽然很类似，但是 IPFS 节点导入 CID 和网盘转存还是有区别的。

IPFS 是一个去中心化的系统，由众多节点组成，就像下面这张图里一样，每个节点都是网络的一部分，彼此平等，不存在客户端和服务端的区别，或者说节点既是客户端也是服务端。

![](https://img.picgo.net/2024/11/14/2024111416255245078ca26837916b.png)

这一点熟悉 BT 的朋友应该能理解是什么意思，因为 IPFS 的底层大量地借鉴了 BT。

### 5.2 IPFS 的默克尔树与虚空做种

不过 BT 并不能对一个你没有的文件做种，但是 IPFS 可以。

IPFS 为什么能做到呢？这里就必须提一下 IPFS 对于文件的处理方式了——**默克尔树**(Merkel Tree)（严格来说是 Merkel DAG ，不过这里为了不干扰理解就叫默克尔树了）

大家不要觉得这个词高大上，这个东西并不是什么很高深的东西，其实就是在 IPFS 中，文件会被**拆成小块进行保存和传输**，而这些小块由一个像树一样的结构被组织起来进行管理，因为是一个叫做默克尔的人申请的专利，所以叫做默克尔树。

这个结构中每个小块像叶子一样长在树上，所以也叫做“叶子节点”。

每个叶子都有自己的独特且唯一的身份牌，这样才能证明你位于树的哪个位置，对于 IPFS 而言，就是 CID（通过哈希值算得）。

IPFS 下载文件也就可以理解为是根据树的结构在整个 IPFS 网络中找对应小块，然后把它们组装起来的过程。

**这些块具体由谁保存并不重要**，只要 IPFS 网络中存在这个 CID 所对应的块，即使相隔很远，也能通过多次节点跳转找到。

![](https://img.picgo.net/2024/11/14/PixPin_2024-11-14_16-42-2991c05a31e417c17f.jpg)

一个 CID 只能对应一个独立的文件块，并不能表示这个树长什么样，这个树的结构其实被保存在你本地的 IPFS 节点的 DHT （分布式哈希表）中。

相比于保存整个文件，DHT 中只保存了每个 CID 所对应的树的关系，纯文本，因此非常的轻量。

下载的时候，照着树按图索骥，拿全所有的块即可组装出完整的文件。

而这个默克尔树也正是 IPFS 能做到 BT 做不到的“**虚空做种**”的理由，因为做种只需要给出 CID 对应的树结构，做种者实际上并不需要保存文件块本身，仅保存**文件的 CID 和树结构**，提供一个指路的效果即可，具体的文件块完全可以交给网络中的**矿工**保存。

### 5.3 批量“转存”文件到本地 IPFS 节点

对于已经存储在 IPFS 公网中的 CID，是可以被任意新加入的 IPFS 节点访问的，具体来说，按下图操作即可把一个 CID 连同其树结构，一起导入到本地 IPFS 节点中。

![](https://img.picgo.net/2024/11/14/PixPin_2024-11-14_17-49-3719c7fc52f36d3943.jpg)

使用 IPFS 分享助手的情况下，点击右下角的 【WebUI】 按钮可以打开上述界面。

![](https://img.picgo.net/2024/11/14/PixPin_2024-11-14_17-53-2068f695e709457e91.jpg)

这种情况并没有导入数据，所以如果要进行下载，需要右键文件，然后点击【设置固定】，选择固定到【本地节点】才能保存文件数据到本地节点（也就是矿工所做的事情）。

![](https://img.picgo.net/2024/11/14/PixPin_2024-11-14_17-57-142d5973848ed1309c.jpg)

不过，假如需要导入的 CID 很多就很不方便了。

这时可以使用 [IPFS 分享助手](https://github.com/cenglin123/IPFS-ShareAssistant/releases)的批量导入功能。

首先在 Crust 或者酸奶网盘确认文件确实已经上链（如果没有上链，导入会卡住，因为要在 IPFS 网络中查找）

然后通过各种办法收集到这些要导入文件的 CID 以及文件名，可以通过油猴脚本在网页或 IPFS 文件夹页面中复制，如果有本地文件的话，也可以通过 IPFS 分享助手的 CID 计算器算出 CID 并填写到主输入框中，然后点击导入。

具体如下图所示：

![](https://img.picgo.net/2024/11/14/PixPin_2024-11-14_18-16-348a5ebbe4af257e16.jpg)

然后点击【WebUI】可以进行确认

![](https://img.picgo.net/2024/11/14/PixPin_2024-11-14_18-21-1467a355d7bfcbcd3f.jpg)

IPFS 程序有一个小问题，即使在配置中设置了默认启用 cidv1，新建文件夹时依然是 cidv0，这里有个权宜之计是先单独从 IPFS 路径导入一个 cidv1 格式的空文件夹，然后再把文件导入到里面。

cidv1 格式的空文件夹 CID 如下
```
bafybeiczsscdsbs7ffqz55asqdf3smv6klcw3gofszvwlyarci47bgf354
```

注意**文件名会影响文件夹 CID 的计算**，需要注意保持文件夹下文件的文件名不变才能保证文件夹 CID 正确，文件夹自身的名字则无所谓，这点在进行文件管理时需要注意。

实在求稳的话，可以新建一个文件夹把所有内容原样丢进去，然后重命名最上层的文件夹进行文件管理。

### 5.4 IPFS 轻量化做种：通过P2P网络辅助公共网关发现文件

在 IPFS 节点中导入 CID 完毕后就可以开始做种了，文件保存在矿工手里，因此流量也由矿工承担。

如此就可以实现轻量化的做种（本地只是提供一个指路的效果，做了一个**结构意义上的种**，可以叫做“结构种”，或者中二点叫“虚空种”也行）

这种做种方式尤其适合做种聚合大量文件的文件夹的 CID，由于聚合后文件夹的总大小往往很大（比如 200GB），这种大小的文件夹是很难单独上链被矿工保存的，此时把多个小文件聚合成大文件夹，然后做种这个文件夹的及其下面的文件的 CID ，就可以在不占用本地空间的情况下维持可用性。

并且，更多的 IPFS 节点数量也有助于 IPFS 公共网关更快地发现文件。

有些时候某个 CID 用某个公共网关找不到，但是用 [IPFS 分享助手](https://github.com/cenglin123/IPFS-ShareAssistant)测速或者 [IPFS-SCAN](https://ipfs-scan.io/) 测速以后，这个 CID 就能被该网关找到了。因此测速这个动作，可以理解为向各个公共网关广播询问有没有这个 CID，然后公共网关会就近查找，节点越多查找的速度就越快（有人称这种现象为“预热”）。

也就是说做种的人越多，公共网关就有更高的概率通过询问最近的做种者找到某个 CID，然后通过实际保存了文件块的矿工那里下载实际的文件块。作为查找中转的节点实际上不需要真的持有这些文件块，只要持有文件结构即可，等同于起了一个为公共网关指路效果。

注意前面提到过，CID 本身不能表示树结构，因此做种除了做文件夹自身的 CID，还需要连同整个文件夹的树结构一起做种，具体来说，做种后要确认文件夹下方的内容确实可以访问，保证树结构是建立起来了的。

如果是多级目录的话，文件夹需要保证点开能看见下方内容，文件的话能看见就行，不必打开；单层目录则只要能看见目录下的内容就可以了。（参考上一节最后一张图）

## 6. IPFS的安全性探讨

### 6.1 IPFS无法举报的原理：权责不明

小结一下，上文中所提到的， IPFS 在拆分、组装、存储、查找、传输、下载文件的特性，叫做“**内容寻址**”，这是 IPFS 区别于中心化网盘的最重要的点。

内容寻址使得 IPFS 网络中的内容不必保存在某个具体的位置，只要网络中有人保存了，就能从他那里下载（保存的人通常是矿工，当然也可以自己保存并做种，把文件固定在本地就可以了）。

这样的做法极大地提升了内容的安全性，这样一来举报者就没有办法向某个具体的网盘或者机构恶意举报，一次性封禁文件了。换言之 IPFS 通过主动割裂分享和存储之间的联系，从而达成了在内容托管上的权责不明。

权责不明就是安全分享的最佳实践方案（不能伤害一个无法选中的单位）。

并且做种时的流量是走的矿工的而不是分享者的，能减少 BT 做种那样因为流量异常被运营商查水表的概率。做种者所需要做的仅仅只是“联结他人”而已，通过 P2P 的联结建立起一个能查找资源的网络，辅助各大公共网关下载文件。**IPFS 在网络层有基本的 TLS 加密，不是裸奔，这可以说极大地降低了做种者的安全性方面的压力**。

### 6.2 IPFS是如何防止吸血的？

此外为了**防止 BT 中的吸血行为**，IPFS 有一个 Bitswap 信用度，如果一个节点交换数据不积极，只下载不上传，那么其他节点给它数据的概率和速度都会降低，需要经常挂机和其他节点交换数据刷一些信用度，才能解决这个问题（信用度账本是节点双方的各执一份的，一方造假是没用的，账本冲突会导致信用度重置，重头再来）。

对于个人来说，信用度不见得很高，如果纯用 P2P 的方式通过本地网关下载（先固定再下载可以降低断连的概率），下载大文件有可能下到后面就被其他节点限速了。因此，假如想要快速下载，比较好的方式是使用 IPFS 网关来下载，目前网络上有很多可供使用的公共网关。

**公共网关本身也是一个 IPFS 节点**，经由公共网关访问文件或文件夹 CID 可以理解为由对方代理来连接到 IPFS 网络中的资源，由于这些网关有公网 IP ，速度也比普通的家宽更快。

但是公共网关不比百度这种大厂，大部分由个人提供（这些网关提供者通常也是矿工），承载能力有限，如果短时间大量的人挤着下，可能会导致出现问题。因此建议生成下载链接的时候分摊到多个网关上，以进行负载均衡。（当然，如果有能力还是建议用 P2P 下载，以减轻公共网关的压力，有条件也可以自己用服务器搭一个公共网关来自用）

目前 1.1.5 版本以后的 IPFS 分享助手已经内置了网关负载均衡功能，具体可以参考 [IPFS 分享助手](https://github.com/cenglin123/IPFS-ShareAssistant)的文章。

### 6.3 公共网关的恶意举报问题、本地网关

但是公共网关也可能**面临被恶意举报导致封 CID 的情况**，这种时候除了更换其他公共网关，也可以用自己 IPFS 节点的本地网关访问资源，这种访问类似于 BT 是纯 P2P 的，也就是说，**即使这个 CID 在所有公共网关上都被屏蔽了，只要你自己不屏蔽这个 CID 就能访问**。

不过普通家宽没有公网 IP，直接下载的话速度会比公共网关慢，一般用来获取文件夹中的 CID 列表，然后自行找其他公共网关生成下载连接下载会更好一些。

具体操作如下：

![](https://file.cangku.moe/images/abc506f0cade92113faa2ae701fa5448.webp)

然后可以通过纯 P2P 的本地网关打开文件夹，使用油猴脚本进行复制 CID、文件名等操作：

![](https://file.cangku.moe/images/467dec0c4541f60a477d16518c97c366.webp)

N+
[[技巧分享] 把IPFS当作网盘来用-IPFS进阶教程](https://www.south-plus.net/read.php?tid-2369384.html)

更多托管平台可以参考这篇文章：
[[技巧分享] 盘点主流IPFS托管平台：功能、限制与推荐指数全面对比](https://cangku.moe/archives/216179)

## 7. IPFS 的优缺点及适用场景的个人浅见

### 7.1. 资源分享的安全级别排名

本人在 [**之前的文章**](https://hxcy.top/541697.html)中讨论过分享的几种安全级别，这里简要带过一下：

> 1. **多层加密压缩包**：可以防止网盘扫描，但是无法防止在线解压（手机端可以解压包括 .7z 在内的所有格式）
> 2. **分卷压缩包**及**自解压压缩包**：无法被在线解压，安全性高于前者。
> 3. **专有格式加密文件**：如 Veracrypt 加密卷等，相比于通用的压缩文件，安全性更高一些。但无法应对举报造成的强制违规。
> 4. **隐写文件**：无法被在线解压，并且违规可申诉，如果被举报到无法分享/下载，申诉即可。安全性高于前述所有。
> 5. **BT、IPFS 等去中心化分享方案**：没有审核系统，安全性最高。但缺点是做不到长时有效稳定。

总的来说，根据 【**1. 能否加密**】 【**2. 能否在线解压**】 【**3. 能否被举报**】，可以把分享方式大致划分出 3 个大的安全级别。

那么上述这么多级别，应该怎么选择呢？

在机器学习领域有一个定理叫做“**没有免费午餐定理**”（NFL），是说没有一种算法可以在所有问题上都表现最好。对于安全分享方案这个问题，也是类似的，即**不可能存在能够同时兼顾所有场景的分享方案，我们总是需要根据特定场景选择最适合的方案**。

对于压缩包方案安全级别问题，我在 [**之前的文章**](https://hxcy.top/541697.html)中已经讨论过，这里就不再赘述了，感兴趣可以参看，本文我想重点讨论一下 IPFS 方案的适用场景。

### 7.2. IPFS 分享方案的优缺点分析

个人认为，IPFS 分享相比于网盘分享，其最大优势在于无法被举报，虽然做不到网盘那样长时有效稳定，但是其去中心化分享的特点令其在应对倒卖者的举报上具有无与伦比的优势。相比于同属去中心化分享的磁链方案，**IPFS 可以选择托管平台，也可以自己做种**，在 [**托管平台**](https://cangku.moe/archives/212812)[7] 选得比较靠谱的情况下，也可以做到类似于网盘那样的长期保存。

由于 IPFS 类似磁链的去中心化特点，分享的安全性有了很大的保障。即使托管平台被攻击或者跑路，只要网上还有人固定文件（做种），就仍有机会下载。并且**相比于磁链完全靠用户做种，IPFS 可以选择托管也可以选择做种**，具有更佳的**灵活性**，可以减轻分享者的负担。

不过 IPFS 作为去中心化的分享方案，也自然有其该有的缺点：首先靠谱的托管平台不好找，其次如果资源比较冷门没人长时间固定（做种），也会出现类似于磁链那样死种的情况。但是相比于磁链， IPFS 在保种这个问题上已经有很大程度的改进了，因为可以选择托管，做种也不需要公网 IP。

### 7.3 IPFS 分享方案与网盘分享方案的对比

分析完上述优缺点，我们可以设想一下其适用的最佳场景，在设想之前，我们需要先对比一下网盘分享的方案。

如果我们想进行长期有效稳定的资源分享，网盘一定是最佳选择，因为运营商代替用户保管文件，拿了钱自然要办事。为了更具体的分析，我们需要知道各大个人网盘的市场占比，限于成本问题，只查到了 2022 年的行业报告，虽然不是最新的，也应该能够反映一些问题，我们先看一下各家网盘的知名度：

根据# 2022年中国个人网盘市场研究报告(https://www.iimedia.cn/c400/84607.html)

![](https://img.picgo.net/2024/12/05/20241205202818a5353189588aefb4.png)

图中的和彩云是现在的中国移动云盘。

我们可以看到，从数据角度，至少在 2022 年，百度网盘仍以绝对的优势占据了榜首。因此，尽管百度网盘一直被人诟病，但是依然是大部分人心目中“网盘”这个概念的体现，因此也是分享的首选（所谓“**不是我非得用百度网盘，而是大家都在用百度网盘**”）。

所以，就分享资源的长期有效稳定方面考虑，百度网盘必然是最优选择，但是相应地就存在审核机制。

根据[这篇文章](https://hxcy.top/541734.html)，**百度网盘的审核机制其实并没有想象中那样严格**，对于不分享的显然违规的文件，百度网盘通常是不会管的；对于包含违规文件的分享压缩包，只要无法解密，百度网盘也是不会管的。总之，只要不能显式地定位到违规文件，百度网盘通常是不会管的。

这似乎和部分人的认知不符，百度明明就天天炸链，怎么能说不管呢？

根据 [**试验证据**](https://bafybeiadpfp7wu6qwmyighdel3qw2eqqqacrmyuxfdwc5u4vwmhiw4mqce.ipfs.dweb.link/) 表明，大多数炸链的真实原因是：

**有这么一帮潜藏在各个资源站的特殊行业人群，这些人获取资源后非但不会感谢分享者，还会举报分享文件使之炸链，保证只有自己一个来源，然后再对此资源开价售卖**。

这帮人就是资源倒卖者，俗称“**倒狗**”。

在百度网盘一家独大的情况下，倒卖者对于百度网盘审核机制的研究也最为深入（所谓盗墓的也一定是半个考古学家），他们充分利用了百度网盘的违规机制（即达到举报阈值自动一刀切），发明了批量转存+脚本举报的技术，即先转存想要使之违规的文件，然后调用举报脚本，自动化批量创建分享链接，以大量账号池组成的举报轰炸逐个炸掉文件，对于隐写文件，则可能会先修改其后缀以破坏其伪装。

倒卖者可以做到全程不下载任何文件，直接就能流水线式地在云端进行转存举报等一系列操作；倒卖者也不需要关注具体举报哪个文件，只需要源源不断地把转存后的文件放入举报池中即可，如此构建起一个简单易操作、成本又可控的举报工作流。只要每天开机运行一遍，就可以让所有举报池中的文件违规（隐写文件因为可申诉，时不时会复活，需要每天都举报）。

目前对于倒卖者的举报，网盘分享方案也确实没有太好的办法，之前试验的各种外网盘（Mega、PikPak、Gofile、ModsFire、MediaFire 等）也纷纷败下阵来。外网盘的封禁政策颇为严厉，一炸链就封号（尤以 Mega 为甚，会追踪 ip、cookies 及设备信息封禁新号），不像国内网盘一般只是禁止该文件分享。出于安全角度考虑，分享还是最好选择国内网盘。

### 7.4 IPFS 分享方案的适用场景：恶意举报

小结一下，网盘分享方案虽然在长时间维持资源有效性和可用性方面具有优势，但是在面对倒卖者时是无能为力的。但是与之相反，无法举报的 IPFS 方案在面对这个问题时就具有优势了。

如资源被倒卖者盯上，在资源发出的时候可以采用 IPFS + 网盘隐写文件的办法，可以在 IPFS 有效期间保证资源的可用性，当 IPFS 失效或者不稳定以后，通常也过了这个资源的热度，此时除了倒卖者很少会有人关注。

俗话说只有千日做贼没有千日防贼，倒卖者不可能无限制累积举报池的文件，迟早有一天会移除失效已久的文件，此时若有人再要资源，只需要申诉隐写文件解除违规（**采用尝试分享的方式申诉解封最快**），再进行分享即可，不需要重新压缩上传。

![4e3b022c952cffc89376061f9809c595.webp](https://file.cangku.moe/images/4e3b022c952cffc89376061f9809c595.webp)

提示反馈成功即申诉成功，文件就解除违规了，解除违规后不急着分享，先观察一天，看会不会再次违规。

一天后在文件详情中点一下申诉，如果提示“**请勿申诉正常文件**”，就证明文件已经被倒卖者移出了举报池，可以分享了；如果显示“**申诉成功**”则说明文件又违规了，还没有被倒卖者移出举报池。

资源生效以后不要在评论区说明，以免被倒卖者注意到。

![f0a471315c6a32ff22b5e0f0f852ed14.webp](https://file.cangku.moe/images/f0a471315c6a32ff22b5e0f0f852ed14.webp)

想要成功申诉需要注意隐写文件的伪装有效性问题，不要选到一些自己就是违规文件的视频。

关于更具体的防炸策略，可以参考这篇文章：

**防炸教程：如何安全分享资源？** 
绅士仓库：[https://cangku.moe/archives/215860](https://cangku.moe/archives/215860)
南+：[https://www.south-plus.net/read.php?tid-2437901.html](https://www.south-plus.net/read.php?tid-2437901.html)
幻想次元：[https://hxcy.top/541697.html](https://hxcy.top/541697.html)


## 8. 总结

本文详细地总结了 IPFS 作为一种去中心化文件分享方案的特点和使用方法：

1. IPFS 程序操作: 详细介绍了文件上传、固定、分享 CID 和下载的步骤，以及本地文件管理方法。
2. IPFS 托管平台：以 Crust+酸奶网盘为例，说明了如何使用托管平台来保证文件的长期可用性。
3. IPFS 优缺点分析：IPFS 的主要优势在于其去中心化特性，不怕举报，因此适合应对倒卖者问题；缺点是可能因缺乏固定节点而导致资源失效。
4. IPFS 与网盘对比：相比传统网盘，IPFS 在应对恶意举报方面更有优势，但在长期稳定性上略逊一筹。
5. 应用建议：文章提出了 IPFS 与网盘隐写文件结合使用的策略，以平衡安全性和长期可用性。

这里需要需要强调的是，大部分情况下，**网盘+隐写**已经足够安全，如果你的分享本身就属于比较安全的资源（普通音乐、普通影视之类），不大可能被倒卖者盯上，那么此时采用隐写甚至 IPFS 就是多余的，反而会增加不必要的负担。此时采用传统的压缩包方案甚至不压缩可能更好一些。

没有免费午餐定理除了告诉我们事物不存在唯一终极解以外，也告诉我们面对问题需要**对症下药，过犹不及**。

## 9. 致谢

本文中 IPFS 相关内容特别感谢 [@yo](https://cangku.moe/user/155378/post) [@sandbox](https://cangku.moe/user/26977/post)

## 10. 参考


**主要内容**

[1] [**[技巧分享] 防炸教程：如何安全分享资源？**](https://rentry.org/safe_sharing)  
[2] [**[技巧分享] 网盘资源分享的几种安全级别、审核与举报原理 [资源防炸链解决方案倡议]**](https://www.south-plus.net/read.php?tid-2348648.html)  
[3] [**[工具分享] 隐写者：把资源嵌入MP4文件的隐写工具 [资源安全分享]**](https://www.south-plus.net/read.php?tid-2314135.html)  
[4] [**[技巧分享] 关于评论区地毯式炸链现象的一些测试及初步猜想 [资源防炸链解决方案倡议]**](https://bafybeiadpfp7wu6qwmyighdel3qw2eqqqacrmyuxfdwc5u4vwmhiw4mqce.ipfs.dweb.link/)  
[5] [**[技巧分享] 百度网盘大号传小号分享的操作方法 [资源安全分享方案]**](https://www.south-plus.net/read.php?tid-2359248.html)  
[6] [**[技巧分享] IPFS分享资源快速上手及其适用场景浅议 [资源防炸链解决方案]**](https://www.south-plus.net/read.php?tid-2357385.html)  
[7] [**[技巧分享] [IPFS] 无法被举报的文件分享神器CRUST IPFS操作指南 PART.I**](https://www.south-plus.net/read.php?tid-2255715.html) ( IPFS 托管平台教程)  
[8] [**IPNS 可用公共网关汇总**](https://k51qzi5uqu5djx3hvne57dwcotpc8h76o2ygrxh05kck11j6wnhvse8jrfzf2w.ipns.dweb.link/)

**幻想次元链接**

[1] [**[技巧分享] 防炸教程：如何安全分享资源？**](https://hxcy.top/541697.html)  
[2] [**[工具分享] 隐写者：把资源嵌入MP4文件的隐写工具**](https://hxcy.top/542433.html)  
[3] [**[技巧分享] IPFS分享资源快速上手及其适用场景浅议**](https://hxcy.top/544580.html)  
[4] [**[技巧分享] 百度网盘大号传小号分享的操作方法**](https://hxcy.top/542051.html)  
[5] [**[技巧分享] 关于评论区地毯式炸链现象的一些测试及初步猜想**](https://bafybeiadpfp7wu6qwmyighdel3qw2eqqqacrmyuxfdwc5u4vwmhiw4mqce.ipfs.dweb.link/)  
[6] [**[技巧分享] 网盘资源分享的几种安全级别、审核与举报原理**](https://www.south-plus.net/read.php?tid-2348648.html)  
[7] [**[技巧分享] [IPFS] 无法被举报的文件分享神器CRUST IPFS操作指南 PART.I**](https://www.south-plus.net/read.php?tid-2255715.html) ( IPFS 托管平台教程)
[[8] 百度网盘应该如何开车评论区传火教程 2.0](https://hxcy.top/541734.html )



**延伸阅读**

[X1] [[技术分享] 如何在.mkv格式视频里夹带隐藏文件，附带mkvtoolnix，MkvEdit和gMKVExtractGUI工具](https://cangku.moe/archives/199992)  
[X2] [[杂谈] 给新司机的一个简单的科普](https://cangku.moe/archives/186292) (笔者注：此文是关于安全分享的科普)  
[X3] [**[技巧分享] IPFS分享资源快速上手及其适用场景浅议 [资源防炸链解决方案]**](https://cangku.moe/archives/212530)  
[X4] [[技巧] 利用网盘离线下载分享规避审查](https://cangku.moe/archives/212031)  
[X5] [[技巧分享] [自建网盘] 自建网盘cloudreve+离线下载](https://cangku.moe/archives/209596)  
[X6] [[高阶文章] 关于新时代文件分享机制的思考](https://cangku.moe/archives/178593) (笔者注：此文介绍了除网盘外的其他分享方案)  
[X7] [[技巧分享] 图种的制作与使用](https://cangku.moe/archives/204982)  
[X8] [[技巧分享] 防炸教程](https://cangku.moe/archives/179329) (笔者注：本文介绍了网盘常用的分享方案，不过作者有可能要吃电脑屏幕了)  
[X9] [[教程] BitTorrent (种子文件) 扫盲 [绅士仓库 tracker 更新] [2020 Rev]](https://cangku.moe/archives/92314) (笔者注：本文是磁力做种的教程)  
[X10] [**[技巧分享] [IPFS] 无法被举报的文件分享神器CRUST IPFS操作指南 PART.I**](https://cangku.moe/archives/212812) ( IPFS 托管平台教程)  
[X11] [关于百度近日封号的相关措施](https://cangku.moe/archives/178107) (此文也是秒传时代的开端)  
[X12] [[南+] 本坛还是有牛马用户啊，低能儿请远离互联网好吗？一口一个敬语问我要资源下载了之后反手就去微软举报，你咋不去网信部举报？说不定给你颁一个好市民奖](https://www.south-plus.net/read.php?tid-1978508.html)  
[X13] [[南+] 看看单纯的举报行为会对百度网盘资源有多大的影响](https://www.south-plus.net/read.php?tid-2203531.html)  
[X14] [**[Pixiv] 一个网警的心法教学-P站写色文发黄图到底安不安全【全网最全最细致】**](https://www.pixiv.net/novel/show.php?id=23561589)   
[X15] [[工具分享] IPFS分享助手：IPFS资源分享一站式解决方案 [资源防炸链解决方案]](https://cangku.moe/archives/213088)  
[X16] [[工具分享] [油猴脚本] 自动抓取 IPFS CID-文件名-下载链接的辅助脚本](https://cangku.moe/archives/214632)  
[X17] [[技巧分享] 把IPFS当作网盘来用-IPFS进阶教程 [资源安全分享解决方案]](https://cangku.moe/archives/214947)
[X17] [[网盘防炸教程]新的一年网盘应该如何开车](https://bafybeianyrlu2hxgbgdtrzqwbnzjwcgnnvguq3hupdysi626nxu4ptjwwu.ipfs.dweb.link)
[X18] [[杂谈] [通过隐写+大号传小号打造网盘分享防御体系](https://cangku.moe/archives/220203)
