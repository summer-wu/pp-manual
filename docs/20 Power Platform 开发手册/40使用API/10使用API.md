# 使用API
+ API有两种：Organization Service、Web API。
+ 这两种都是基于HTTP协议的，但Organization Service中数据是以SOAP（XML）格式呈现，Web API中数据是以JSON格式呈现的。
+ Organization Service 时间久，有微软封装好的C# library
+ Web API 可以用任何语言（python或java）调用，没有封装好的library

## 认证方式
+ 如果作为Plug-in部署到Dataverse中，自然不需要认证了
+ 如果作为桌面程序，推荐使用