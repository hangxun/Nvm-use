# Nvm-use
nvm 安装 node.js
### NVM工具的使用

> Node Version Manager（Node版本管理工具）

由于以后的开发工作可能会在多个Node版本中测试，而且Node的版本也比较多，所以需要这么款工具来管理


#### 安装操作步骤

1. 下载：[nvm-windows](https://github.com/coreybutler/nvm-windows/releases/download/1.1.0/nvm-noinstall.zip)
2. 解压到一个全英文路径
3. 编辑解压目录下的`settings.txt`文件（不存在则新建）

  + `root 配置为当前 nvm.exe 所在目录`
  + `path 配置为 node 快捷方式所在的目录`
  + `arch 配置为当前操作系统的位数（32/64）`
  + `proxy 不用配置`

4. 配置环境变量 可以通过 window+r  : sysdm.cpl
  > window 中的PATH环境变量，当要求系统运行一个程序而没有告诉程序所在的完整路径时，系统除了在当前目录下寻找该程序之外，还
  > 该到PATH中指定的路径之中去寻找；
  
  + `NVM_HOME = 当前 nvm.exe 所在目录`
  + `NVM_SYMLINK = node 快捷方式所在的目录`
  + `PATH += %NVM_HOME%;%NVM_SYMLINK%;`
  + 打开CMD通过`set [name]`命令查看环境变量是否配置成功
  + PowerShell中是通过`dir env:[name]`命令

5. node 的使用
  + $ nvm ls ;查看当前node 版本列表；
  + $ nvm use 5.7.0 使用5.7.0版本的Node.js 
6. NVM使用说明：

  + https://github.com/coreybutler/nvm-windows/

7. NPM的目录之后使用再配置

# git的使用

## git的安装与配置
请参阅[windows安装git和环境变量的配置](https://wuzhuti.cn/2385.html)

## 版本管理员的操作
1. 初始化中央仓库[实验链接](./02.Git 暂存区的理解.mhtml)
+ 创建一个目录 c:\develop\software\repository\git 用于存放版本库
- 在目录下运行命令 $ git init --bare shared.git

2. 将中央版本库，克隆到本地
+ 创建一个目录 c:\develop\workroom\user1 与 c:\develop\workroom\user2 用于存放本地版本库；
- 在目录下运行 $ git clone /c/develop/software/repository/git/share.git . (注意有个点，表明当前目录)
- 克隆之后，有可能看不到，是因为文件被隐藏了；

3. 设置个人信息

git config user.name "user1"
git config user.email "user1@163.com"

> 利用 ls (-al) 查看目录 cd (打开目录) cat (打开文件) cd ..（返回上一级） clear (清空控制台) 查看配置文件 看个人信息是否设置成功

4. 在 .git 同级目录下，新建一个文件

echo "User1 add content" > index.jsp 

5. 提交文件

git add index.jsp 追踪文件 将文件添加到缓存区；

git commit 提交文件 会进到一个 vim 窗口来强制用户提交本次改动信息

[vim命令图解](http://jingyan.baidu.com/article/48206aeaf07f37216ad6b3a6.html)：

![vim窗口](./imgs/vim.PNG) 
> commit 是将文件提交到，本地版本库里面；

git commit -m "User1 add the file"


6. 把自己的仓库提交到公共服务器

git push origin master  
> 'origin' 这个本地库是从那地方 clone 出来的，这个origin 便指向哪里；



7. git 常用命令
- $ pwd 可以看到自己当前所在的目录位置
- $ ls -al 查看所有的目录 （包含隐藏的目录）
- $ vim text 打开vim 编辑器 编辑指定文件；
- $ git log --pretty=raw 查看完整日志 （紧接着按‘q’退出输入模式）
- $ git log --graph 查看日志 每个动作都有对应的哈希值

![哈希值](./imgs/git哈希值.PNG)

- $ git get-file -t 当自己拿到一个哈希值时 用于查看哈希值指代的对象类型
- $ git get-file -p 看哈希值指向对象内的具体内容

## git的相关概念

![git工作结构图](./imgs/git工作结构图.PNG)

### 工作区
### 暂存区
### 版本库
![git版本库结构图](./imgs/git版本库结构图.PNG) 


***

# TortoiseGit的使用

## Tortoise的安装及配置

## Tortoise的使用
+ 创建空的'中央版本库' 
    右键-->git creat repository here..
+ clone 中央版本库到本地仓库
    右键-->git clone
+ 在.git 平级目录下新建一个文件

+ 配置程序员信息
    右键--TortoiseGit--setting--Git 
+ 提交文件 至本地仓库
    右键文件--add--commit--输入注释--success
+ 推送文件至中央仓库
    右键--TortoiseGit--push 
> 将push按钮 配置到tortoiseGit第一面 右键--TortoiseGit--setting--context menu

+ 若有人比自己本地先提交，且与自己本地库有冲突；
1. 先将中央版本库的文件 Pull 下来；与手动将自己本地文件整合在一起；
2. 右键文件-- TortoiseGit -- Edit conflicts
 
git 就是不知道该怎样处理，所以才会交给程序员去处理，但cinflicts 处理完之后，git不知道
得去通知git conflicts已经处理完毕； 
右键 -- TortoiseGit -- resolve 

## vscode 使用git 教程

## 如何管理好自己的包包

- 由于`Node`本身并没有太多的功能性`API`，所以市面上涌现出大量的第三方人员开发出来的`Package`
![www.npmjs.com](./img/npm.png)
- 包的生态圈一旦繁荣起来，就必须有工具去代替人脑或者文档的方式管理
- 这时候`NPM`诞生了


### NPM

- 随着时间的发展，NPM 出现了两层概念：
  + 一层含义是 Node 的开放式模块登记和管理系统，亦可以说是一个生态圈，一个社区
  + 另一层含义是 Node 默认的模块管理器，是一个命令行下的软件，用来安装和管理 Node 模块。

- 官方链接： https://www.npmjs.com/
- 国内加速镜像： https://npm.taobao.org/

### 安装NPM

- NPM 不需要单独安装。默认在安装 Node 的时候，会连带一起安装 NPM。
- 但是，Node 附带的 NPM 可能不是最新版本，最好用下面的命令，更新到最新版本。

```bash
$ npm install npm -g
```

- 默认安装到当前系统 Node 所在目录下。
- 由于之前使用 NVM 的方式安装的 Node 所以需要重新配置 NPM 的全局目录

### 配置NPM的全局目录
> 注：未配置之前的问题；npm 的程序执行文件以及 npm的全局包安装目录 是存放在，node.js 程序文件所在的路径里，每个版本的node 
  都有一个对应的路径，导致与node不同版本配套的npm全局包安装目录 node_modules是相互区分的（不能共用）；
  node(4.3.1) 的Npm默认全局包安装路径 ：node_modules: C:\dev\nvm\v4.3.1
  node(4.3.1) 的npm默认全局包安装路径：node_modules: C:\dev\nvm\v5.7.0  即当node版本切换时，前版本全局安装的包，
  当前版本无法继续使用；

> 配置目的是将 npm的默认全局包安装路径node_modules提取出来 放到nvm路径下面的 npm目录里面；
  C:\dev\nvm\npm\node_modules；


```bash
$ npm config set prefix [pathtonpm]
```

- 将NPM目录配置到其他目录时，必须将该目录放到环境变量中，否则无法再全局使用

### npm配置
npm config ls 打印当前npm的数值清单；
> ; 注释符；
> user-agent: 用户代理字符串；
> userconfig c:\\user\chunping\.npmrc 用户配置文件；
  >找到 配置文件 .npmrc 并将其打开：

#### 配置prefix属性值
+ prefix=c:\dev\nvm\npm 前缀：用来指定npm全局包安装目录node_modules所在的路径；
+ 一般都是将prefix的属性值 配置为 nvm\npm 目录内；配置方法：直接修改 .npmrc 文件
  利用 npm config set prefix c:\dev\nvm\npm
+ 配置完成之后 npm的全局包 就放在了：
  C:\dev\nvm\npm\node_modules内；

#### 配置cache属性值
+ cache 缓存目录；npm install或npm update命令，从 registry 下载压缩包之后，都存
放在本地的缓存目录。这个缓存目录，在 Linux 或 Mac 默认是用户主目录下的.npm目录，在 
Windows 默认是%AppData%/npm-cache。通过配置命令，可以查看这个目录的具体位置。
- 查看cache路径：
```bash
  $ npm config get cache
```
- 查看cache内容：
```bash
  $ npm cache ls
```
- 清空cache：
```bash
  $ npm cache clean
```
- 配置cache路径：
  $ npm config set cache 
```bash
```

####配置registry属性值
+  npm的数据源下载非常慢，大部分情况下，我们都会从国内淘宝的镜像源上去加速；
  > 官方链接 http://www.npmjs.com/
  > taobao镜像源 hhtp://npm.taobao.org/
+ 配置命令 : $ npm config set registry http://registry.npm.taobao.org/

+ 利用工具进行配置：推荐使用；
  - 全局工具 NRM: npm registry manager 用于切换 npm 镜像源；
  - 常用指令：
  1. nrm ls 查看源列表
  2. nrm use [name] 切换至目标源
  3. nrm test 抓取源列表各项的链接速度






### 常用NPM命令
>nodejs npm常用命令

npm是一个node包管理和分发工具，已经成为了非官方的发布node模块（包）的标准。有了npm，可以很快的找到特定服务要使用的包，进行下载、安装以及管理已经安装的包。

1、npm install moduleNames：安装Node模块
安装完毕后会产生一个node_modules目录，其目录下就是安装的各个node模块。

node的安装分为全局模式和本地模式。
一般情况下会以本地模式运行，包会被安装到和你的应用程序代码的本地node_modules目录下。
在全局模式下，Node包会被安装到Node的安装目录下的node_modules下。

全局安装命令为$npm install -g moduleName。
获知使用$npm set global=true来设定安装模式，$npm get global可以查看当前使用的安装模式。

示例：
npm install express 
默认会安装express的最新版本，也可以通过在后面加版本号的方式安装指定版本，如npm install express@3.0.6

npm install <name> -g 
将包安装到全局环境中

但是代码中，直接通过require()的方式是没有办法调用全局安装的包的。全局的安装是供命令行使用的，就好像全局安装了vmarket后，就可以在命令行中直接运行vm命令

npm install <name> --save 
安装的同时，将信息写入package.json中项目路径中如果有package.json文件时，直接使用npm install方法就可以根据dependencies配置安装所有的依赖包，这样代码提交到github时，就不用提交node_modules这个文件夹了。

2、npm view moduleNames：查看node模块的package.json文件夹
注意事项：如果想要查看package.json文件夹下某个标签的内容，可以使用$npm view moduleName labelName

3、npm list：查看当前目录下已安装的node包
注意事项：Node模块搜索是从代码执行的当前目录开始的，搜索结果取决于当前使用的目录中的node_modules下的内容。$ npm list parseable=true可以目录的形式来展现当前安装的所有node包

4、npm help：查看帮助命令

5、npm view moudleName dependencies：查看包的依赖关系

6、npm view moduleName repository.url：查看包的源文件地址

7、npm view moduleName engines：查看包所依赖的Node的版本

8、npm help folders：查看npm使用的所有文件夹

9、npm rebuild moduleName：用于更改包内容后进行重建

10、npm outdated：检查包是否已经过时，此命令会列出所有已经过时的包，可以及时进行包的更新

11、npm update moduleName：更新node模块

12、npm uninstall moudleName：卸载node模块

13、一个npm包是包含了package.json的文件夹，package.json描述了这个文件夹的结构。访问npm的json文件夹的方法如下：
$ npm help json 
此命令会以默认的方式打开一个网页，如果更改了默认打开程序则可能不会以网页的形式打开。

14、发布一个npm包的时候，需要检验某个包名是否已存在
$ npm search packageName

15、npm init：会引导你创建一个package.json文件，包括名称、版本、作者这些信息等

16、npm root：查看当前包的安装路径
npm root -g：查看全局的包的安装路径

17、npm -v：查看npm安装的版本

更多命令请参看npm官方文档：https://www.npmjs.org/doc/

- https://docs.npmjs.com/
- 

```bash
npm config [ls|list|set|get] [name] [value] 
npm init [--yes|-y]
npm search [name]
npm info [name]
npm install [--global|-g] [name]
npm uninstall [--global|-g] [name]
npm list [--global|-g]
npm outdated [--global|-g]
npm update [--global|-g] [name]
npm run [task]
npm cache [clean]
```


*****

