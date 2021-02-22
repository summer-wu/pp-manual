# 准备账号
+ Power Platform 是给企业使用的，使用者应该是企业的员工。企业有自己的域名，一个域名对应一个tenant（租户）。user1@a.com跟user2@a.com都属于`a.com租户`。`user1@x.a.com`属于`x.a.com租户`,它和`x.com`没有关系，是一个独立租户。
+ 获取账号有两种方式：a员工自己注册账号、b管理员直接开通账号。
+ a员工自己注册账号: 员工用自己的邮箱注册账号，这个账号会自动进入到所属租户(如用`user1@a.com`注册的账号，自动成为`a.com`租户的一个user)，管理员可以在`Active Users`中看到这个邮箱。注册账号时只能用**企业邮箱**，qq邮箱、163、gmail、hotmail这些常用邮箱都不支持注册。员工自己注册的账号，初始是Trial License，默认只可以访问Default Environment和”自己创建的Trial Environment“。要使用Sandbox或Production环境，需要管理员手动分配license，分配license后，这个账号就是正式账号了。
+ b管理员直接开通账号：管理员可以直接为员工开通账号，开通账号时直接分配license。管理员帮员工设置好密码，员工直接登录即可。
+ 推荐方式b。


> Note: 如何开通租户、如何购买license、license的价格，不在本手册讨论范围之内。
