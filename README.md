# Power Platform 使用手册、Power Platform 开发手册
+ PP的官方文档都是英文的，为了能让新成员快速上手工作，特地总结了此两份手册。

# 如何修改手册内容？
+ 要修改手册内容，直接修改对应的markdown文件即可
+ 如果需要预览,或构建 static html，需要安装mkdocs

# 安装mkdocs及依赖
+ 要求python3.8
+ requirements.txt中记录了pip的依赖内容
+ 用`pip freeze >  docs/requirements.txt`生成requirements.txt，然后删除`pkg-resources==0.0.0`(ubuntu中才有这行)
+ 用`pip install -r requirements.txt`恢复requirements.txt
