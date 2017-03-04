# Sublime Text 3 配置远程同步 - 使用指南

## 简介

这个项目用于 [Sublime Text 3](https://www.sublimetext.com/) 的配置同步。
Sublime 是很强大的编辑器，它的强大很大一点在于拥有可以满足各种个性化需求的插件和配置。

当在一个新环境使用 Sublime 时，只需下载这个项目
到你的 Sublime 配置文件夹覆盖原有配置，就可以体验插件齐全、个性化配置的 Sublime 编辑器了。

这个项目的配置会根据我个人的使用随时更新，欢迎使用。  

> 插件及配置详情见最后  

如果你想要使用自己的个性化配置，也欢迎 fork 到你自己的仓库，
然后就可以在自己的仓库下面通过 push 和 pull 进行自己的配置管理了。

## 配置教程

### 1. 安装 Sublime Text 3

在[官网](https://www.sublimetext.com/3)根据自己的环境下载相应的最新 Sublime Text 3.

### 2. 安装 [Package Control](https://packagecontrol.io/)

Package Control 是非常推荐的 Sublime 插件管理用的插件（好像有点绕口？）.
安好它之后，只要将配置文件夹同步好，其他的插件 Package Control 会自动为你下载安装.

#### 最简单的安装方式

打开 Sublime Text 3，在主界面下按下 `ctrl + ~(反引号)` 快捷键，
或者单击主界面菜单栏的 `View -> Show Console`，
在底部出现的 command panel 中键入以下 python 代码：

```python
import urllib.request,os,hashlib; h = 'df21e130d211cfc94d9b0905775a7c0f' + '1e3d39e33b79698005270310898eea76'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)
```

这份代码会在你的 Sumelime 配置下创建一个 Package 目录（如果必要的话），然后下载
`Package Control.sublime-package` 到里面。

在主界面下按 `ctrl + shift + p`（Windows）或者 `command + shift + p`（Mac OS X），
键入`pci`，如果出现 `package control: install`，说明已经安装完成。  

> 你也可以查看[官网](https://packagecontrol.io/installation)的安装教程

### 3. 开始同步

安装好 Package Control 插件之后，我们只要同步好配置文件，剩下的就不需要我们操心啦~  
单击主界面菜单栏的 `Preferences -> Browse Packages` 打开配置文件夹，
将里面的 `User` 目录改名为 `User.old`,然后执行 git 命令
(windows 通过 git bash 或者 win10 的 bash，Max OS X 或 Linux 通过 terminal)  

`git clone https://github.com/Cibifang/User.git`  

> 如果是 fork 到你自己的仓库，这里 clone 你自己的仓库即可  

> 如果你只是想下载配置文件，没有搭好的 git 环境，也可以通过 zip 下载然后解压到配置文件夹  

> 如果你对 git 使用不熟练，推荐这个[教程](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)  

重启 Sublime，Package Control 插件会根据配置文件自动下载插件，稍作等待再次重启即可完成配置同步。


## 已安装插件及配置

### 插件

* [Package Control](https://packagecontrol.io/) : 插件管理  
* [BracketHighlighter](https://github.com/facelessuser/BracketHighlighter) : 括号匹配  
* [CTags](https://github.com/SublimeText/CTags) : 将你的 sublime 打造成类似于ide的效果
(需要再做单独的配置，具体查看[官网](https://github.com/SublimeText/CTags))  
* [FileDiffs](https://github.com/colinta/SublimeFileDiffs) : 
查看选定文件之间的差别，用于和别人或者自己的历史代码比较/查看更改  
* [Markdown Preview](https://github.com/revolunet/sublimetext-markdown-preview) : 
Markdown 格式绝对是你写文档节省时间的利器！而这个插件提供了在 sublime 上预览 markdown 格式文档效果的能力  
* [TrailingSpaces](https://github.com/SublimeText/TrailingSpaces) : 高亮多余的空格，帮你养成良好的代码风格  
* [ConvertToUTF8](https://github.com/seanliang/ConvertToUTF8) : 中文环境好帮手，避免中文乱码~  
* [SublimeLinter](http://www.sublimelinter.com/en/latest/) : 代码校验工具，为习惯了ide的你提供（同样需要单独配置）  
* [SideBarEnhancements](https://github.com/titoBouzout/SideBarEnhancements/tree/st3) : 侧边栏加强  
* [IMESupport](https://github.com/chikatoike/IMESupport) : 解决中文输入法光标不跟随的问题  
* [GraphvizPreview](https://github.com/munro/SublimeGraphvizPreview) : graphviz 预览

### 配置

```c
{
    "color_scheme": "Packages/User/SublimeLinter/Monokai (SL).tmTheme",     //主题
    "default_line_ending": "unix",                                          //避免在windows环境编写linux代码产生不必要的格式错误
    "dpi_scale": 1.0,                                                       //避免高分屏下sublime标题栏中文乱码
    "font_size": 14,                                                        //字体大小
    "ignored_packages":
    [
        "Vintage"
    ],
    "rulers":                                                               //在第80/100/120行先是竖线，养成良好代码风格
    [
        80,
        100,
        120
    ],
    "translate_tabs_to_spaces": true                                        //自动将tab转化为space，避免跨平台代码出错
}
```