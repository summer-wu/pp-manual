# 管理Dataverse
+ Dataverse就是一个关系型数据库+Web管理界面。和所有的关系型数据库一样，需要定义table、relation（也叫外键或foreign key或reference key）、view、stored procedure。
+ 在mysql中，stored procedure是一个函数，需要用SQL调用。在Dataverse中，stored procedure是以Business rules的形式提供的。

## 新建table（entity）
+ table之前叫entity
+ table type有两种：Standard table和Activity table。
+ Activity table 的 ownership 只能是`User or team`，比如给员工分配的任务、比如预约的会议，都可以作为Activity类型。Activity可以显示在timeline上。
+ Standard table的 ownership 有2个选项：`User or team`和`Organization`。
+ 两种ownership的区别：ownership会影响`Security Role`中可选的access level和privileges。如果选择`User or team`，则access level有5种(`None Selected;Users;Business Unit; Parent:Child Business Units;Organization`)，privilege有8种；如果选择`Organization`，则access level只有2种(`None Selected;Organization`)，privilege有6种（缺少了Assign和Share）。
+ ===
+ 新建table时需要选择ownership：
+ ![](imgs/41-ownership.jpg)
+ privilege和access level：
+ ![](imgs/42-access-levels-privileges.jpg)

## 管理columns
+ columns之前叫fields，有些文档中也称作attribute、property
+ 新建column时需要选`Data type`，大部分都很容易理解，这里只描述几个不容易理解的type：
+ 