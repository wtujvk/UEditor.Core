# UEditor.Core
[![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](https://mit-license.org/)
[![UEditor.Core](https://img.shields.io/nuget/dt/UEditor.Core.svg)](https://www.nuget.org/packages/UEditor.Core/)

> 首先给大家安利另外一个基于UEditor写的富文本框编辑器[neditor](https://github.com/notadd/neditor) ，看起来相当不错，不过我还没有来得及尝试！最起码它是基于UEditor的，肯定不会比UEditor差。其次，他的接口没有变化，所以理论上来说，本项目的接口也可以适配到neditor中，有人已经试过了。如果在适配NEditor的过程中遇到什么问题，我也可以协助解决！

**作者一直在，只是没有什么太多问题，所以版本更新较少，有ISSUE会第一时间处理，请放心使用**

# 示例代码

- [传统多页应（MPA）用中使用UEditor.Core](https://github.com/baiyunchen/UEditor.Core/tree/master/Sample.Web)
- [API中使用UEditor.Core（支持跨域）](https://github.com/baiyunchen/UEditor.Core/tree/master/Sample.Mvc)
- [.NET Framework MVC 中使用UEditor.Core](https://github.com/baiyunchen/UEditor.Core/tree/master/Sample.Mvc)

# 使用方法

对于在.NET Core和.NET Framework中使用UEditor,分别有详细的文档，请参阅：
- [.NET Core中使用UEditor.Core](Docs/DotnetCore中的使用.md)
- [.NET Framework中使用UEditor.Core](Docs/NETFramework中使用.md)
- [UEditor.Core多环境](Docs/多环境配置.md)

另外，可以参考网络上其他人写的相关文章：
- [关于ASP.NET Core如何使用UEditor编辑器](https://blog.csdn.net/qq_34220236/article/details/80581811)
- [.net core + angular 项目中使用ueditor遇到的问题](https://cloud.tencent.com/developer/article/1191886)

# 安装
> 强烈建议从nuget安装

- 方式1：可以直接在Nuget中搜索UEditor.Core并安装

- 方式2：通过命令行安装
```
Install-Package UEditor.Core
```

Nuget地址：https://www.nuget.org/packages/UEditor.Core/

# 配置

## 可选配置项

在注入Service时，可以支持一些可选的配置，具体参数如下：

### configFileRelativePath
后端配置文件的相对路径，默认值为`ueditor.json`,即项目根目录的`ueditor.json`文件，这个文件是从UEditor官方提供的.NET版本下载包中的`utf8-net\net\config.json`复制过来的
### isCacheConfig
是否缓存配置文件，默认值为true。当设置为不缓存时，每次都会从文件中读取配置文件；当设置为缓存时，则第一次从配置文件中读取，以后都从内存中读取
### basePath
相对路径的根目录，默认值为项目的根目录，即`env.ContentRootPath`。系统中的后端配置文件、各种上传的路径都是基于该地址去计算其实际地址的。

> **特别注意：**

> 在修改`basePath`后，一定要注意调整后端配置文件中的`imageUrlPrefix`、`scrawlUrlPrefix`等等各种文件访问路径的前缀，否则可能出现文件可以上传，但是前端编辑器中总显示不出来的问题。

## 配置项使用方式
配置项需要在注入Service时设置，示例代码如下：
```
public void ConfigureServices(IServiceCollection services)
{
   services.AddUEditorService(configFileRelativePath: "config.json",
       isCacheConfig: false,
       basePath: "C:/basepath");
   services.AddMvc();
}
```

# 特别感谢
  优秀的开源项目离不开大家的支持，非常感谢为以下为本项目提供好的建议或PR的朋友：
  - [wtujvk](https://github.com/wtujvk)
  - [BruceAndLee](https://github.com/BruceAndLee)

## 大功告成，祝你大吉大利，今晚吃鸡
