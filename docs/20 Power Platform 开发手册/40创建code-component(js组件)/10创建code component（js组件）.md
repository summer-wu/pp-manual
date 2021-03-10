# 创建code component（js组件）
+ pcf：PowerApps Component Framework
+ 本文仅为技术要点总结，需要参考官方文档一起阅读
+ Power Apps支持用代码构建前端组件，然后可以插入到 model-driven app 中或 canvas app 中。在 canvas app 中使用code component需要手动开启，默认是**不支持**在canvas app 中使用code component的。
+ 组件是**基于field的**，组件的输出就是这个field的值！
+ 一个component由三部分组成：manifest、implementation（js）、resources（依赖的js、css、images）。

## 创建滑块组件
+ `pac`(Power Apps CLI),pac需要手动下载,仅支持windows 10系统，安装后会修改path环境变量。

```
pac pcf init --namespace SampleNamespace --name TSLinearInputComponent --template field
npm install 
修改Manifest中的版本号、display-name、description
删除sample property，添加自己的properties，name为sliderValue，类型组为numbers，numbers不是一个固定类型，需要用户选择一个具体类型（四选一）。
<type-group name="numbers">
    <type>Whole.None</type> <type>Currency</type> <type>FP</type> <type>Decimal</type>
</type-group>
<property name="sliderValue" display-name-key="sliderValue_Display_Key" description-key="sliderValue_Desc_Key" of-type-group="numbers" usage="bound" required="true" />
添加资源文件
<css path="css/TS_LinearInputComponent.css" order="1" />
```
+ `<property usage=xxx`。这里usage有两个取值，`bound`和`input`。`bound`用于Model-Driven app，比如详情页的一个年龄字段，可以保存到db中。`input`适用于Canvas，不能保存到db，是designer中设置好的值。
+ `npm run build`后，会输出到`out/controls`目录，其中有`bundle.js ControlManifest.xml 其他资源文件`。一个npm项目可以有多个components，每个component放在一个文件夹（有ControlManifest.Input.xml的文件夹会自动识别为component）。
+ `npm run start`会启动一个server，在浏览器中可以测试这个组件。`npm run start watch`可以自动观察文件，改动后自动刷新网页。
+ 用`document.createElement("input")`创建html元素。
+ 组件有两种类型：field类型、dataset类型。
```
pac pcf init
usage: init --namespace --name --template
  --namespace                 组件的命名空间 (别名: -ns)
  --name                      组件的名称 (别名: -n)
  --template                  为组件选择模板 (别名: -t)  值:field, dataset
```

## 打包为solution package
+ 需要使用MSBuild（Microsoft Build Engine）。需要下载Visual Studio Community，或仅下载`Build Tools for Visual Studio 2019`
```
pac solution init --publisher-name mslearn --publisher-prefix msl
pac solution add-reference --path ../ #会在 Solutions.cdsproj 中添加一个 ItemGroup
msbuild /t:build /restore #等于msbuild -target:build -restore:True。需要安装.Net SDK（默认电脑上只有runtime）。默认是Managed，可以修改配置文件改为Unmanged
```
+ `/restore`的作用似乎是：构建依赖。
+ `msbuild`默认生成的是`Debug`包，位于`bin/Debug/Solutions.zip`。可以改为`Release`，增加`/p:configuration=Release`
+ 导入后名字是`solution`，这个名字可以修改，位于`src/Other/Solution.xml`，修改`<SolutionManifest><UniqueName>xxx`

## 在canvas中使用component
+ 需要在`admin center`中打开这个feature，`Power Apps component framework for canvas apps`
+ 开启feature后，在Canvas app内才可以引入code component。

## 调试
+ 用`Test Harness`可以进行调试。可以配置Context Inputs和Data Inputs。
+ 可以用console.log打印日志。可以使用所有js生态工具，比如Chrome中的inspect element、设置breakpoint。
+ webApi不能在`test harness`中测试。


