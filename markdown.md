---
title: Sublime + Markdown总结
tags: []
notebook: Markdown
---

<div markdown="1" style=";">

# Sublime替代马克飞象编辑Markdown文件

## PackageControl

> Sublime 安装包内已经集成

## Evernote插件

  * 直接用PackageControl进行下载与安装
  * 获得印象笔记授权 
    * 中国版印象笔记客户打开<https://app.yinxiang.com/api/DeveloperToken.action>
    * 国际版的印象笔记用户打开<http://evernote.com/api/DeveloperToken.action>
    * 登陆并登陆，获取应用授权Developer Token 和 NoteStore URL
  * 配置Evernote插件 
    * 打开用户配置文件 > Preferences > Package Settings > Evernote > Settings - User
    * 用Developer Token 和 NoteStore URL值配置用户文件
```js
    {
         "noteStoreUrl": "你的 NoteStore URL",
         "token": "你的 Developer Token"}

    {
         "noteStoreUrl": "https://app.yinxiang.com/shard/s30/notestore",
         "token": "S=s30:U=61b6fc:E=160296c9282:C=158d1bb64c8:P=1cd:A=en-devtoken:V=2:H=6a09b4776b39ad4ad78968e4688b09df"
    }```

  * 配置Evernote快捷键 
    * 打开Sublime 热键配置文件 Preferences > keybinding - users
```js
    { "keys": ["super+e"], "command": "show_overlay", "args": {"overlay": "command_palette", "text": "Evernote: "} }, 
    { "keys": ["ctrl+e", "ctrl+s"], "command": "send_to_evernote" }, //保存至印象笔记
    { "keys": ["ctrl+e", "ctrl+o"], "command": "open_evernote_note" }, // 打开印象笔记
    { "keys": ["ctrl+e", "ctrl+u"], "command": "save_evernote_note" },//同步印象笔记
    // ctrl + shift + p ;  输入 'ene' 新建印象笔记
    //["ctrl+e", "ctrl+s"] 即使先按ctrl+e,后按ctrl+s ```

  * 配置印象笔记中代码高亮 
    * 通过在用户文件中配置`code_highlighting_style`的属性值进行配置；
    * 若选用monokai样式或其它黑色样式会造成普通文本看不清的问题，通过将代码格式配置成css或bash即可看清楚；

> `code_highlighting_style` | a pygments style among `autumn`, `default`, `github`, `monokai`, `perldoc`, `vim`, `borland`, `emacs`, `igor`, `murphy`, `rrt`, `vs`, `bw`, `friendly`, `native`, `tango`, `xcode`, `colorful`, `fruity`, `manni`, `pastie`, `trac`.

* * *

## Markdown Editing插件

### 基本功能

  * 直接用PackageControl进行安装

  * Asterisks and underscores are autopaired and will wrap selected text

    * If you start an empty pair and hit backspace, both elements are deleted
    * If you start an empty pair and hit space, the right element is deleted

> 若没有选中任何文本，当输入* 或者 _ 时，也会成对出现，此时若按下退格键，则两个都会删除，若按下空格键，则右面的哪一个会被删除； aotupaired:自动补全；asterisk ：星号； underscore :下划线; 星号'与 '_' 都是自动补全的 而且会将选中的文本包起来

  * Backticks are paired

> 引号是成对的

  * At the end of a list item, pressing <kbd>Enter</kbd> will automatically insert the new list item bullet.

    * Pressing <kbd>Tab</kbd> on the blank list item will indent it and switch the list bullet to another one (Order is `*`, `-`, `+` in a cycle).
    * Pressing <kbd>Shift</kbd> <kbd>Tab</kbd> on the blank list item will unindent it in the same way as above.
    * Sequential <kbd>Tab</kbd> s or <kbd>Shift</kbd> <kbd>Tab</kbd> s are supported.
    * You can disable automatic bullet switching or choose which bullets to be used, in your settings file.
    * If a list item contains a [GFM task][GFM], pressing <kbd>Enter</kbd> at the end of the line will continue with a new blank task.

> 在列表的最后按Enter键，会在新换起行自动插入列表项目符号； 在新换起行自动插入列表项目符号后，再按一次Enter键制表符将会被删除；按tap键，则表符会被缩进，且表符会被转换为其它表符（顺序是`*`, `-`, `+`）； 按shift + tap 将缩进回退，并将表符变回来； 连续按tap 或连续按 shift+tap都是支持的

  * At the end of a blockquote line, pressing <kbd>Enter</kbd> will automatically extend blockquote.
  * Selecting some text and pressing <kbd>></kbd> will convert it to blockquote. The first and the last line don't have to be fully selected; partial select works, too.

> 在注释块的行尾，按回车键，可以将块域扩至新起的一行； 随便选中某一个段落中的某一部分文字，并按下>都会将选中文字所在的段，转化为块，即使段首与段尾未被选中，依旧工作；

  * Left bracket pairing is modified to eliminate the selection and leave the cursor at a point where you can insert a `[]` or `()` pair for a link

> 左括号`[`补全被修改为，先是将选中的部分括起来`[selection]`,而后将光标放到一个可以插入`[]`()`的位置，以便配合插入图片与插入链接的语法；

  * Displays Markdown headers in the Project Symbol List (<kbd>Ctrl</kbd> <kbd>Shift</kbd> <kbd>R</kbd>). They will start with `#`, so you will know they belong to markdown files at a glance. Also they will be on top of the list because of the presedence of `#`.

  * <kbd>~</kbd> wraps selected text with `~~` (strikethrough).

> 选中文字后 按 `~` 键，会自动用`~~`将选中文字包围，将选中文字打上删除线；

  * Typing `#` when there's a selection will surround it with `#` to make it a headline. Multiple presses add additional hashes, increasing the level of the header. Once you hit 6 hashes, it will reset to 0 on the next press. The `mde.match_header_hashes` will determine if the `#` are mirrored on both sides or just at the beginning of the line.

> 选中文字后按`#`可将选中文字提升为标题，按多次可以提升标题的等级；

  * Typing return at the end of a line that begins with hashmarks will insert closing hashmarks on the headline. They're not required for Markdown, it's just aesthetics, and you can change the `mde.match_header_hashes` option in your settings to disable.
  * Setext-style headers can be completed with `Tab`. That is, typing `Tab` on a line containing only `=` or `-` characters will add or remove enough characters to it to match the length of the line above.
  * New documents will be named au tomatically based on the first header.

> 新文档会自动命名为首行文字

### Markdown Editing 快捷键
<table style="border-collapse: collapse; border-spacing: 0; margin: 1em;">
<thead><tr><th style="border: 1px solid #DDD; padding: 6px 13px;">快捷键</th><th style="border: 1px solid #DDD; padding: 6px 13px;">效果</th><th style="border: 1px solid #DDD; padding: 6px 13px;">注释</th></tr></thead><tr style="border: 1px solid #DDD; padding: 6px 13px;"><td style="border: 1px solid #DDD; padding: 6px 13px;">ctrl + win + v</td><td style="border: 1px solid #DDD; padding: 6px 13px;"><code style="color: #000000; font-family: monospace,monospace; padding: 0.1em 0.2em; margin: 0.1em; font-size: 85%; background-color: #F5F5F5; border-radius: 3px; border: 1px solid #cccccc;">[]()</code></td><td style="border: 1px solid #DDD; padding: 6px 13px;">快速链接</td></tr><tr style="border: 1px solid #DDD; padding: 6px 13px; background-color: #F8F8F8;"><td style="border: 1px solid #DDD; padding: 6px 13px;">ctrl + win + r</td><td style="border: 1px solid #DDD; padding: 6px 13px;"><code style="color: #000000; font-family: monospace,monospace; padding: 0.1em 0.2em; margin: 0.1em; font-size: 85%; background-color: #F5F5F5; border-radius: 3px; border: 1px solid #cccccc;">[][]</code></td><td style="border: 1px solid #DDD; padding: 6px 13px;">参考链接</td></tr><tr style="border: 1px solid #DDD; padding: 6px 13px;"><td style="border: 1px solid #DDD; padding: 6px 13px;">shift + win + k</td><td style="border: 1px solid #DDD; padding: 6px 13px;"><code style="color: #000000; font-family: monospace,monospace; padding: 0.1em 0.2em; margin: 0.1em; font-size: 85%; background-color: #F5F5F5; border-radius: 3px; border: 1px solid #cccccc;">![]()</code></td><td style="border: 1px solid #DDD; padding: 6px 13px;">插入图片</td></tr><tr style="border: 1px solid #DDD; padding: 6px 13px; background-color: #F8F8F8;"><td style="border: 1px solid #DDD; padding: 6px 13px;">alt +b</td><td style="border: 1px solid #DDD; padding: 6px 13px;"/><td style="border: 1px solid #DDD; padding: 6px 13px;">字体加粗</td></tr><tr style="border: 1px solid #DDD; padding: 6px 13px;"><td style="border: 1px solid #DDD; padding: 6px 13px;">alt + i</td><td style="border: 1px solid #DDD; padding: 6px 13px;"/><td style="border: 1px solid #DDD; padding: 6px 13px;">斜体</td></tr>
</table>


* * *

## Table Editor插件

> 参看Evernote/Tools/Markdown/TableEditor/README

## Monokai Extended 高亮主题 & Markdown Extended 语法

> Markdown Extended 用于扩展Sublime的语法，配置如下；Monokai Extended是一套主题，切换方法与其它Sublime的主题都是一样的； 这套方案用于Markdown 文件在 Sublime 编辑器中的语法高亮；

  * Markdown 格式在 Sublime 中默认无高亮，很多主题也不支持 Markdown 的高亮（包括 Markdown 代码块内的代码），Monokai Extended 和 Markdown Extended 是一套解决方案。

  * 注意需要将 Markdown 的文件格式与 Markdown Extended 这种语法关联起来，做法是点击 Sublime 右下角文档格式，在列表最上方名为 Open all with current extension as 二级列表中选择 Markdown Extended

  * 另一种临时设置方式可以是 Shift + Command + P 调出 Command Palette，输入 ssm，选择 Set Syntax: Markdown Extended

  * 一定要在Open all with current extension as 二级列表中选择 Markdown Extended，这样以后打开相同后缀的文件就会自动选择了* 在Preferences -> Color Scheme -> Monokai Extended -> Monokai Extended Bright 就会显示高亮

> 其它语言的配置方法与此类似；先让编辑器看懂你的语法，而后在说高亮的事；

## OmniMarkupPreviewer

> 在要预览的文件窗口内直接右键，菜单中即有三项功能； 另外OmniMarkupPreviewer还支持多部设备同时预览，这以后自己再研究；

## 配置七牛图床

### 配置七牛账户

  * 注册七牛账号，个人主页直接填自己的qq邮箱，或其它网址都行；

> value:lhx1010339808@outlook.com; key:lhx......

  * 并绑定支付宝进行实名认证；认证成功之后会有10G的免费空间与下载流量；
  * 在对象存储栏 点击添加空间；

> 空间添加成功后，七牛会为空间添加一个临时域名( ohstyiifx.bkt.clouddn.com)此类测试域名，限总流量，限单 IP 访问频率，限速，仅供测试使用，不能用于自定义域名的 CNAME 相关文档, 所以就想办法使用自定义的域名；

### 花生壳申请域名

> 18元买的，域名地址：baihua.xicp.cn

### 七牛空间CNAME

> 参考 Evernote/Tools/Markdown/七牛CNAME

### 配置极简图床

  * 配置yotuku七牛账户
<en-media hash="e952105692a6ab75228027316995aebf" type="image/jpeg" style="height: auto;"/>

  * 配置yotuku chrome快捷键
<en-media hash="2ed52bf351381cc2a1c8a892a9e25c48" type="image/jpeg" style="height: auto;"/>

> 配合faststone 截图编辑之后，直接粘贴到yutuku中，操作舒服的不要不要的；

</div>
