# AutoApiSecret-加密版
AutoApi系列：AutoApi、AutoApiSecret、AutoApiSR、AutoApiS

# 置顶 #
* 本项目是建立在[原教程](https://blog.432100.xyz/index.php/archives/50/)可以正确调用api的**假设**上的，核心是paran/黑幕大佬的py脚本。
* 本项目只是提供一个自动、免费、无需额外设备的脚本运行方式，换句话说，**借用github的电脑/服务器来干活**。（因为原教程需要服务器/超长时间运转的设备，大部分人都不具备，本项目应运而生）
* 本项目运行依赖**github action**服务，此功能github固有而**非私人提供**的服务器，且整个运行过程只涉及你与github。
* 请务必先阅读理解[原教程](https://blog.432100.xyz/index.php/archives/50/)的**原理说明、设计理念**。
* **不保证一定能续期！不保证一定能续期！不保证一定能续期**！或者说，**只是增大续订可能性**。过期前、后30天都可能续期！！！
* 若理解并接受上述说明，请接着操作；**若否，请点击浏览器右上角 X 。**

### 项目说明 ###
* 利用github action实现**定时自动调用api**，保持E5开发活跃。
* **免费，不需要额外设备/服务器**，部署完不用管啦。
* 加密版，隐藏应用id+机密，保护账号安全。

### 特别说明/Thanks ###
* 原教程博主-黑幕（酷安id-Paran）：https://blog.432100.xyz/index.php/archives/50/
* 普通版地址：https://github.com/wangziyingwen/AutoApi
* 加密版地址（推荐）：https://github.com/wangziyingwen/AutoApiSecret
* 模仿人为应用开发版（包含升级步骤）：https://github.com/wangziyingwen/AutoApiSR
* 超级版地址： https://github.com/wangziyingwen/AutoApiS
* **常见错误及解决办法/更新日志**：https://github.com/wangziyingwen/Autoapi-test
* 网页获取refresh_token小工具（不建议使用）：https://github.com/wangziyingwen/GetAutoApiToken
* 视频教程：（我操作很慢，自行倍速/快进）
   * 在线/下载地址：https://kino-onemanager.herokuapp.com/Video/AutoApi%E6%95%99%E7%A8%8B.mp4?preview
   * B站：https://www.bilibili.com/video/av95688306/

           

### 区别 ###
   [普通版（弃用）](https://github.com/wangziyingwen/AutoApi)：密钥暴露，不在乎的话可以使用
   
   [加密版（推荐）](https://github.com/wangziyingwen/AutoApiSecret)：应用id机密加密隐藏，提高安全性

   [模仿人为应用开发版（半弃用）](https://github.com/wangziyingwen/AutoApiSR)：顾名思义，加密版的升级版。由于超级版兼容模拟版的功能，此版本处于一种尴尬位置。（当然也可以正常使用）
   
   [超级版（不建议）](https://github.com/wangziyingwen/AutoApiS)：进一步升级版，增加自定义参数、模式。按目前情况，微软续订要求很低，暂时不需要使用此项目。
   
   **以上推荐/不建议等只是个人意见，请自行选择版本，可同时使用**。

--------------------------------------------------------------

### 步骤 ###
   *** **有错误/问题请看**:    [常见错误及解决办法/更新日志](https://github.com/wangziyingwen/Autoapi-test) ***   

* 第一步，先大致浏览[原教程](https://blog.432100.xyz/index.php/archives/50/)，了解如何获取应用id、机密、refresh_token 3样东西，以方便接下来的操作。

* 第二步，登陆/新建github账号，回到本项目页面，点击右上角fork本项目的代码到你自己的账号，然后你账号下会出现一个一模一样的项目，接下来的操作均在你的这个项目下进行。（看不到图片/图裂请科学上网）

  ![image](https://github.com/wangziyingwen/ImageHosting/blob/master/AutoApi/fork.png)
  
* 根据[原教程](https://blog.432100.xyz/index.php/archives/50/)获取应用id、机密、refresh_token（自己复制保存，注意区分id机密，别弄混了）
   
  然后在线编辑你项目里的1.txt，将整个refresh_token覆盖粘贴进去（里面是我的数据，先删掉或者覆盖掉）。（千万不要改1.py）
  
    > refresh_token位置如图下。复制refresh_token紧接着的双引号里的内容（红竖线框起来的），不要把双引号复制进去。复制进1.txt后，留意结尾不要留空格或者空行
     
    ![image](https://github.com/wangziyingwen/ImageHosting/blob/master/AutoApi/token地方.png)
  
* 第三步，依次点击上栏Setting > Secrets > Add a new secret，新建两个secret如图：CONFIG_ID、CONFIG_KEY。

  内容分别如下: ( 把你的应用id改成你的应用id , 你的应用机密改成你的机密，单引号不要动 )
  
  CONFIG_ID
  ```shell
  id=r'你的应用id'
  ```
  CONFIG_KEY
  ```shell
  secret=r'你的应用机密'
  ```
  ![image](https://github.com/wangziyingwen/ImageHosting/blob/master/AutoApi/机密.png)
  
  最终格式应该是类似这样的：
  
  ![image](https://github.com/wangziyingwen/ImageHosting/blob/master/AutoApi/格式.png)
  
* 第四步，进入你的个人设置页面(右上角头像 Settings，不是仓库里的 Settings)，选择 Developer settings > Personal access tokens > Generate new token,

  ![image](https://github.com/wangziyingwen/ImageHosting/blob/master/AutoApi/Settings.png)
  ![image](https://github.com/wangziyingwen/ImageHosting/blob/master/AutoApi/token.png)

  设置名字为GITHUB_TOKEN , 然后勾选 repo , admin:repo_hook , workflow 等选项，最后点击Generate token即可。
  
  ![image](https://github.com/wangziyingwen/ImageHosting/blob/master/AutoApi/repo.png)
  ![image](https://github.com/wangziyingwen/ImageHosting/blob/master/AutoApi/adminrepo.png)
  ![image](https://github.com/wangziyingwen/ImageHosting/blob/master/AutoApi/workflow.png)
  
* 第五步，点击右上角星星/star立马调用一次，再点击上面的Action就能看到每次的运行日志，看看运行状况

（必需点进去Test Api看下，api有没有调用到位，有没有出错。外面的Auto Api打勾只能说明运行是正常的，我们还需要确认10个api调用成功了，就像图里的一样。如果少了几个api，要么是注册应用的时候赋予api权限没弄好；要么是没登录激活onedrive，登录激活一下）

  ![image](https://github.com/wangziyingwen/ImageHosting/blob/master/AutoApi/日志.png)

* 第六步，没出错的话，就搞定啦！！再看看下面的定时次数要不要修改，不打算改就忽略。

  **然后第二天回来确认下是否自动运行了（ation里是否多出来几个）**,是的话就不用管了，完结。
  
  我设定的每3小时自动运行一次，每次调用3轮（点击右上角星星/star也可以立马调用一次），你们自行斟酌修改（我也不知道保持活跃要调用多少次、多久）：

  * 定时自动启动修改地方：（在.github/workflow/AutoApiSecret.yml文件里，自行百度cron定时任务格式，最短每5分钟一次）
   
  ![image](https://github.com/wangziyingwen/ImageHosting/blob/master/AutoApi/定时.png)
   
  * 每次轮数修改地方：（在1.py最后面）
   
  ![image](https://github.com/wangziyingwen/ImageHosting/blob/master/AutoApi/次数.png)
  
------------------------------------------------------------
### 题外话 ###
> Api调用
  你们可以自己去graph浏览器看一下，学着自己修改要调用什么api(最重要的是调用outlook、onedrive)
  https://developer.microsoft.com/zh-CN/graph/graph-explorer/preview

### GithubAction介绍 ###
提供的虚拟环境：

· 2-core CPU
· 7 GB RAM 内存
· 14 GB SSD 硬盘空间

使用限制：
* 每个仓库只能同时支持20个 workflow 并行。
* 每小时可以调用1000次 GitHub API 。
* 每个 job 最多可以执行6个小时。
* 免费版的用户最大支持20个 job 并发执行，macOS 最大只支持5个。
* 私有仓库每月累计使用时间为2000分钟，超过后$ 0.008/分钟，公共仓库则无限制。

（我们这里用的公共仓库，按理，你们可以设定无限循环调用，然后6小时启动一次，保证24小时全天候调用）

### 最后 ###
  教程很直白了，应该都会弄吧！
  
  代码小白，多包涵！有问题/修改建议可以点击上方issues发布一下，或者PY给我:
  wz.lxh@outlook.com
  
  Q群：[657581700](https://jq.qq.com/?_wv=1027&k=5FQJbWmV)  （项目相关讨论）
  
  tg群：[OneDrive E5](https://t.me/joinchat/OLlK9RsbBlmTYOJS_BU4Mg)   （**非项目相关**讨论！**tg可能不会及时在线回答问题**，任何项目相关的问题或出错请进Q群/邮箱/issue）
  

  
  最后的最后，再次感谢黑幕/paran大佬
  
  ————wangziyingwen/酷安id-卷腿毛菌
  
  ### 附录：原教程
  > 不保证一定能续订!!!
不保证一定能续订!!!
不保证一定能续订!!!
重要的事情说三遍，微软从未说过有一定的续订标准，所以不保证一定能续订，请不要在e5子号的onedrive存放重要数据，使用本脚本造成的一切后果概不负责。

> 最近e5订阅很火，但是玄学的续订方式也让人摸不着头脑，有的人说挂个oneindex就续订了，有的人说所有第三方程序都挂了一遍也没续订，所以我按照微软的官方文档写了一个刷api的脚本，原理很简单，就是重复调用microsoft graph的api，一次调用10个api，5个onedrive的api还有4个outlook的api,剩下一个是组的api，调用一次后延时等待五分钟再重复调用.
教程开始:
> 1.首先去https://portal.azure.com/#home注册一个应用,这一步网上的教程实在是太多了,我就不详细写了,大致写一下流程
先用e5管理员账号登录网站,然后在主页找到Azure Active Directory点进去，再在左侧目录找到点击应用注册，再点上方的新注册就会跳出一个新建应用的界面，应用名字随意填写,然后选择任何组织目录(任何 Azure AD 目录 - 多租户)中的帐户，重定向url选web，填入http://localhost:53682/,最后点注册即可
> 2.注册好应用会跳转到应用概述界面,你会看到一个应用程序(客户端) ID,复制这个Id记录下来，后面要用到,然后点击左侧目录的API权限,依次点击添加权限、 Microsoft Graph 、委托的权限,然后依次搜索以下这12个权限并勾选:

> Files.Read.All Files.ReadWrite.All Sites.Read.All Sites.ReadWrite.All

> User.Read.All User.ReadWrite.All Directory.Read.Al Directory.ReadWrite.All

> Mail.Read Mail.ReadWrite MailboxSettings.Read MailboxSettings.ReadWrite

> 全部勾选好后点击底部的添加权限，然后又返回到了API权限界面，这时候你一定要再点一下代表xxx授予管理员同意,不点这个,outlook api会无法调用
> 3.点击左侧证书和密码,点+新客户端密码,说明随便填，年限随便选多久都行,然后点添加,添加好后,客户端密码下面会有一个值,复制值下面的那一串代码，这是应用秘钥，后面会用到,到这一步，注册应用已经结束了
> 4.windows下载rclone获取token,点击这里下载rclone,随意下载到电脑的任意一个目录,下载后不要双击rclone.exe安装!,而是在rclone.exe同目录下,按住shift后点鼠标右键，选择在此处打开cmd窗口或在此处打开power shell窗口,弹出窗口后,CMD窗口就执行:

> rclone authorize "onedrive" "之前保存的应用id" "之前保存的应用秘钥"
> 请自行将双引号内的替换为之前我们保存的应用id和秘钥,示例:

> rclone authorize "onedrive" "729xx16f-8x70-4xb8-8fd6-1xxx9b582b1f" "?@P@4u/fxxcxxx28:B-3i_QxxFxc6_ZO"
> 如果是power shell的窗口请执行:

> .\rclone authorize "onedrive" "729xx16f-8x70-4xb8-8fd6-1xxx9b582b1f" "?@P@4u/fxxcxxx28:B-3i_QxxFxc6_ZO"
执行后电脑浏览器会弹出一个界面,登陆自己的e5账号,然后看到浏览器显示Success!，说明获取token成功了。然后我们返回的cmd窗口或者power shell窗口，你会看到一大段Paste the following into your remote machine --->开头,<---End paste结尾的代码，找到"refresh_token":"复制后面的代码直到","expiry"，说白了就是复制refresh_token，不要带双引号,类似格式如下:

> OAQABAAAAAABeAFzDwllzTYxxxx_qYbH8UALCVjtv_6YeHHOwXExxxxxywOKSg2Hd_GSjW1vcLzqL
