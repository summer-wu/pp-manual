# Event Framework
+ Event Framework 文档`https://docs.microsoft.com/en-us/powerapps/developer/data-platform/event-framework`

## Event execution pipeline
+ `PreValidation stage` 还没有开始database transaction，在这个阶段**可以cancel掉操作**。此阶段尚未执行security checks，不应在这个阶段修改数据。
+ `PreOperation stage` 已经开始了database transaction，在这个阶段不建议cancel，cancel会导致transaction rollback（回滚会消耗大量资源）。可以**对entity进行修改**
+ `MainOperation stage` 仅internal use，普通开发者无法使用这个阶段
+ `PostOperation stage` 可以**修改response message**，仍然处于transaction阶段。在这个阶段不建议cancel，cancel会导致transaction rollback。在这个阶段不建议对entity进行修改，修改会触发新的Update event，可能导致死循环。