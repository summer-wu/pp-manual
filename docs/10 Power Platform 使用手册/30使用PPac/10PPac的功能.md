# PPac的功能
+ morden PPac中可以管理environment（包括新建、删除、备份、管理可访问用户、开关某个feature），查看capacity，设置Data policies。morden PPac很多功能会跳转到legacy PPac，比如添加user和添加security roles都会打开legacy PPac中的对应页面。
+ legacy PPac可以管理当前environment中的features、管理dataverse、管理users、分配security roles。

## 新建环境、环境的类型
+ 新建环境时需要选择环境的类型，有这些类型：Production Sandbox Trial(Subscription-based) Trial。除了这四种之外，还有两种类型：Developer和Default，这两种都是系统创建的。
+ `Trial`有效期是30天，所有成员都可以创建
+ `Trial(Subscription-based)`有效期也是30天，只有管理员可以创建
+ `Sandbox`和`Production`的区别主要是备份保存时长，可能性能上也有区别（未测试）。所有backups，包括system backups和manual backups，对于Production环境保留28天；对于sandbox环境保留7天。如果对production执行`switch to sandbox`，会立即丢弃21天的备份数据。

## 环境的备份
+ 文档见`https://docs.microsoft.com/en-us/power-platform/admin/backup-restore-environments`
+ 所有backups，包括system backups和manual backups，对于Production环境保留28天；对于sandbox环境保留7天。如果switch to sandbox，会立即丢弃21天的备份数据。
+ 备份是持续创建的，依赖于底层的 Azure SQL Database 
+ backup不提供下载功能，只支持restore到sandbox类型的环境。

