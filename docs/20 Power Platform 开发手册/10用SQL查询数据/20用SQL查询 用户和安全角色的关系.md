# 用SQL查询 用户和安全角色的关系
+ 要查看某个用户有哪几个security roles，可以通过`legacy PPac`中查看。
+ 但想查看某个security role分配给了哪几个users，无法通过web查看。SQL接口可以实现此功能。
```
select  systemuser.fullname ,role.name, role.modifiedbyname,role.createdbyname from  systemuser,role,systemuserroles
where systemuser.systemuserid=systemuserroles.systemuserid and systemuserroles.roleid = role.roleid

-- 下面是用join方式，更加explicit。上面是多表查询方式，更加简洁
select fullname as systemuser_fullname,role.name as role_name,role.modifiedbyname,createdbyname from role 
join (
    select systemuser.fullname,roleid
    from systemuser 
    join systemuserroles on systemuserroles.systemuserid=systemuser.systemuserid
) as t on role.roleid=t.roleid
```
