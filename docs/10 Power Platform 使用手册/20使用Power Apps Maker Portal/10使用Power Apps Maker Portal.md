# 使用Power Apps Maker Portal
+ 先区分一下三个单词：
+ Power Apps，是微软的一个产品，app开发者主要操作 Power Apps Maker Portal。Power Apps Maker Portal是一个网页，地址是`https://make.powerapps.com/`，官方文档很多时候省略了`Maker Portal`。
+ Canvas App，Power Apps中的一种App，目的是在手机中使用（也可以在网页中使用），可以访问手机硬件（包括定位、相机）。
+ Model-Driven App，Power Apps中的一种App，目的是在PC浏览器中使用，不可以访问手机硬件。

## 查看apps
+ 点击左侧导航条中的Apps，右侧列出所有Apps，右上角可以修改filter和执行搜索。
+ 注意：**默认显示的是My apps，看不到别人分享给你的apps**，要看到别人分享给你的apps，需要切换filter为Org apps。
+ ![](imgs/10My_Apps.jpg)

### 查看apps的另外两种方法
+ 除了在Power Apps Maker Portal中可以查看apps，还可以在另外两个地方查看apps。
+ 在`O365`中查看：
+ ![](imgs/20-O365.jpg)
+ 在`home.dynamics.com`中查看：
+ ![](imgs/30-home.dynamics.com.jpg)



## 创建apps
+ app有两种类型：canvas和model-driven。创建的方式各不相同。
+ canvas app 中的数据来自于connectors，其中有`CDS connector`，也有`Google Drive Connector`，共一百多个connector。
+ model-driven app 中的数据仅来自CDS
+ 具体创建步骤参考官方文档，此处略过。


## 切换环境
+ 一个tenant中有多个environment。environment是一个容器，其中包括一个dataverse instance、n个apps、n个automate flows。
+ 第一次进入Maker Portal，查看的都是`Default Env`，在顶部可以切换环境。管理员可以看到所有环境，员工能看到哪些环境是管理员配置的，员工肯定可以看见`Default Env`

## 使用advanced settings（legacy PowerApps admin center） 
