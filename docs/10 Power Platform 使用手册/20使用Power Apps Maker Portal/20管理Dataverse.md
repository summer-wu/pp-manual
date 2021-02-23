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
+ ![](imgs/42-access-levels-privileges-2.jpg)

## 管理columns
+ columns之前叫fields，有些文档中也称作attribute、property
+ 新建column时需要选`Data type`，大部分都很容易理解，这里只描述几个不容易理解的type：Lookup类型、Owner类型、Customer类型、PartyList类型。
+ Lookup类型的字段。类似于单选，但单选是从“固定的列表”中选择一个，Lookup是从”特定的表“中选择一个。比如一个网购订单，订单的”卖家字段“就是Lookup字段。在数据库中存储的的是一个整数GUID。
+ Owner类型的字段。当表的ownership为`User or team`时，会自动添加一个`owner`字段，它的DataType是`Owner`。在选择时，可以选择User表中的一个user，也可以选择Team表中的一个team。在底层数据库中实际会占用两个字段(`ownerid`和`owneridtype`)，但在web端只能看到一个字段`ownerid`。（通过API可以看到`owneridtype`）
+ Customer类型的字段。在选择时，可以选择Account表中的一个account，也可以选择Contact表中的一个contact。在底层数据库中实际会占用两个字段
+ PartyList类型的字段。比如会议有多个参会人，参会人字段就可以是PartyList。比如`Appointment`表的`requiredattendees`字段就是PartyList类型。这种字段一般是系统创建。PartyList字段从Account、Users、Contact、Queues中进行选择。PartyList在底层数据库中实际是用了2个中间表（`activityparty`和`activitypointer`，用API可以看到）。
