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

5. 下载并切换node 的版本
  + $ nvm help 查看nvm的命令列表；
  + $ nvm list [<availab></availab>le] 查看远端服务器中，nodejs的可用版本列表；
  + $ nvm install <version> [arch] 安装相应的node版本 32bit || 64bit
  + $ nvm ls ;查看本地node 版本列表；
  + $ nvm use <version> 切换相应的Node.js版本； 
  + $ nvm uninstall <version> 卸载相应版本的node ;
  + ``$ nvm on  ?``
  + ``$ nvm off ?``
6. NVM使用说明：

  + https://github.com/coreybutler/nvm-windows/

7. NPM的目录之后使用再配置
