#React Native for iOS 安装过程

###安装准备
#####1.系统：OS X
#####2.xcode7.0及以上

####好，现在开始

######T-CSdeMacBook-Pro:~ t$ `ruby -v`

ruby 2.0.0p645 (2015-04-13 revision 50299) [universal.x86_64-darwin15]

######T-CSdeMacBook-Pro:~ t$ `pwd`

/Users/t-cs
####首先安装 Homebrew：
######T-CSdeMacBook-Pro:~ `t$ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`

==> This script will install:
/usr/local/bin/brew
/usr/local/Library/...
/usr/local/share/man/man1/brew.1

Press RETURN to continue or any other key to abort 
######按回车
==> /usr/bin/sudo /bin/mkdir /Library/Caches/Homebrew
######Password:
######输入密码******，然后按回车
==> /usr/bin/sudo /bin/chmod g+rwx /Library/Caches/Homebrew

==> /usr/bin/sudo /usr/sbin/chown t /Library/Caches/Homebrew

==> Downloading and installing Homebrew...

remote: Counting objects: 4049, done.

remote: Compressing objects: 100% (3898/3898), done.

remote: Total 4049 (delta 36), reused 2000 (delta 20), pack-reused 
0
Receiving objects: 100% (4049/4049), 3.34 MiB | 51.00 KiB/s, done.

Resolving deltas: 100% (36/36), done.

From https://github.com/Homebrew/homebrew

 * [new branch]      master     -> origin/master
 
HEAD is now at c99e5c4 daemon: add 0.6.4 bottle.

==> Installation successful!

==> Next steps

Run `brew help` to get started
####好了，现在输入 `brew help` 
######T-CSdeMacBook-Pro:~ t$` brew help`
Example usage:

  brew [info | home | options ] [FORMULA...]
  
  brew install FORMULA...
  
  brew uninstall FORMULA...
  
  brew search [foo]
  
  brew list [FORMULA...]
  
  brew update
  
  brew upgrade [FORMULA...]
  
  brew pin/unpin [FORMULA...]

Troubleshooting:

  brew doctor
  
  brew install -vd FORMULA
  
  brew [--env | config]

Brewing:

  brew create [URL [--no-fetch]]
  
  brew edit [FORMULA...]
  
  https://github.com/Homebrew/homebrew/blob/master/share/doc/homebrew/Formula-Cookbook.md

Further help:

  man brew
  
  brew home
####使用 Homebrew 安装 nvm 
######T-CSdeMacBook-Pro:~ t$ `brew install nvm`
==> Downloading https://github.com/creationix/nvm/archive/v0.31.0.tar.gz

==> Downloading from https://codeload.github.com/creationix/nvm/tar.gz/v0.31.0
######################################################################## 
100.0%

==> Caveats

Please note that upstream has asked us to make explicit managing
nvm via Homebrew is unsupported by them and you should check any
problems against the standard nvm install method prior to reporting.

You should create NVM's working directory if it doesn't exist:

  mkdir ~/.nvm

Add the following to ~/.bash_profile or your desired shell
configuration file:

  export NVM_DIR=~/.nvm
  
  . $(brew --prefix nvm)/nvm.sh

You can set $NVM_DIR to any location, but leaving it unchanged from

/usr/local/Cellar/nvm/0.31.0 will destroy any nvm-installed Node installations
upon upgrade/reinstall.

Type `nvm help` for further information.

Bash completion has been installed to:

  /usr/local/etc/bash_completion.d
  
==> Summary

🍺  /usr/local/Cellar/nvm/0.31.0: 6 files, 85.6K, built in 21 seconds
####nvm 安装成功，但是当你输入 nvm -v 时不能调用
######T-CSdeMacBook-Pro:~ t$ `nvm -v`
-bash: nvm: command not found
####现在请按以下操作设置 shell 配置文件
######T-CSdeMacBook-Pro:~ t$ `brew info nvm`
nvm: stable 0.31.0, HEAD

Manage multiple Node.js versions

https://github.com/creationix/nvm

/usr/local/Cellar/nvm/0.31.0 (6 files, 85.6K) *
  Built from source

From: https://github.com/Homebrew/homebrew/blob/master/Library/Formula/nvm.rb

==> Caveats

Please note that upstream has asked us to make explicit managing
nvm via Homebrew is unsupported by them and you should check any
problems against the standard nvm install method prior to reporting.

You should create NVM's working directory if it doesn't exist:

  mkdir ~/.nvm

Add the following to ~/.bash_profile or your desired shell
configuration file:


  export NVM_DIR=~/.nvm
  . $(brew --prefix nvm)/nvm.sh

You can set $NVM_DIR to any location, but leaving it unchanged from
/usr/local/Cellar/nvm/0.31.0 will destroy any nvm-installed Node installations
upon upgrade/reinstall.

Type `nvm help` for further information.

Bash completion has been installed to:

  /usr/local/etc/bash_completion.d

####根据上面的方法，在用户根目录下创建 .nvm 文件
######T-CSdeMacBook-Pro:~ t$ `mkdir ~/.nvm`

####紧接着，把 nvm-exec 文件拷贝到创建了的 .nvm 目录里

######T-CSdeMacBook-Pro:~ t$ `cp $(brew --prefix nvm) /nvm-exec ~/.nvm/`
###第一个方法（参考原文：[ReactNativeiOS（一）安装](http://blog.csdn.net/oiken/article/details/50016549)）：
####然后要编辑 bash 配置文件 $HOME/.bashrc ,如果wq 使用你使用 zsh 那么编辑 $HOME/.zshrc 配置文件
`nano ~/.nvm`

#####或

`nano ~/.nvm`

####将下面的内容粘贴进去

`export NVM_DIR=~/.nvm`

`source $(brew --prefix nvm)/nvm.sh`

####让 shell 配置及时生效

`source ~/.bashrc`

#####或


`source ~/.zshrc`

####这样就不会出现关闭终端重启或重启机器后发现 node,npm 等系统环境变量失效的问题
###第二个方法（直接进入 zsh 下操作,本人用的是第二个方法）：
######T-CSdeMacBook-Pro:~ t$` ZSH`
######T-CSdeMacBook-Pro% `export NVM_DIR=~/.nvm`
######T-CSdeMacBook-Pro% `source $(brew --prefix nvm)/nvm.sh`
######T-CSdeMacBook-Pro% `source ~/.bashrc`
######T-CSdeMacBook-Pro% `nvm list`
               
->       system

node -> stable (-> N/A) (default)

iojs -> N/A (default)
######T-CSdeMacBook-Pro% `nvm ls-remote`
        v0.1.14
        v0.1.15
        v0.1.16
        v0.1.17
        v0.1.18
        v0.1.19
        ~省略~~~
         v5.0.0
         v5.1.0
         v5.1.1
         v5.2.0
         v5.3.0
         v5.4.0
         v5.4.1
         v5.5.0
         v5.6.0
         v5.7.0
####接下来运行 `nvm install node $$ nvm alias default node`
######T-CSdeMacBook-Pro% `nvm install node $$ nvm alias default node`
Downloading https://nodejs.org/dist/v5.7.0/node-v5.7.0-darwin-x64.tar.gz...

######################################################################## 100.0%

Now using node v5.7.0 (npm v3.6.0)

Creating default alias: default -> node (-> v5.7.0)

####安装 watchman
######T-CSdeMacBook-Pro% `brew search watchman`
watchman
######T-CSdeMacBook-Pro% `brew info watchman`
watchman: stable 4.4.0 (bottled), HEAD

Watch files and take action when they change

https://github.com/facebook/watchman

Not installed

From: https://github.com/Homebrew/homebrew/blob/master/Library/Formula/watchman.rb

==> Dependencies

Build: autoconf ✘, automake ✘

Required: pcre ✘
######T-CSdeMacBook-Pro% `brew install watchman`

==> Installing dependencies for watchman: pcre

==> Installing watchman dependency: pcre

==> Downloading https://homebrew.bintray.com/bottles/pcre-8.38.el_capitan.bottle

######################################################################## 100.0%

==> Pouring pcre-8.38.el_capitan.bottle.tar.gz

🍺  /usr/local/Cellar/pcre/8.38: 146 files, 5.4M

==> Installing watchman

==> Downloading https://homebrew.bintray.com/bottles/watchman-4.4.0.el_capitan.b

######################################################################## 100.0%

==> Pouring watchman-4.4.0.el_capitan.bottle.tar.gz

🍺  /usr/local/Cellar/watchman/4.4.0: 20 files, 341.5K

######T-CSdeMacBook-Pro% `watchman -v`
4.4.0

####安装 flow
######T-CSdeMacBook-Pro% 	`brew info flow`
flow: stable 0.22.0 (bottled), HEAD

Static type checker for JavaScript

http://flowtype.org/

Not installed

From: https://github.com/Homebrew/homebrew/blob/master/Library/Formula/flow.rb

==> Dependencies

Build: ocaml ✘

######T-CSdeMacBook-Pro% `brew install flow`

==> Downloading https://homebrew.bintray.com/bottles/flow-0.22.0.el_capitan.bott

######################################################################## 100.0%

==> Pouring flow-0.22.0.el_capitan.bottle.tar.gz

==> Caveats

Bash completion has been installed to:

  /usr/local/etc/bash_completion.d

zsh completion has been installed to:

  /usr/local/share/zsh/site-functions
  
==> Summary

🍺  /usr/local/Cellar/flow/0.22.0: 6 files, 5.7M

###建议定期运行 `brew update && brew upgrade` 让应用程序保持最新
####重要时刻来了
######T-CSdeMacBook-Pro% `npm install -g react-native-cli`
/Users/t-cs/.nvm/versions/node/v5.7.0/bin/react-native -> /Users/t-cs/.nvm/versions/node/v5.7.0/lib/node_modules/react-native-cli/index.js

/Users/t-cs/.nvm/versions/node/v5.7.0/liba└─┬ react-native-cli@0.1.10 

  ├─┬ chalk@1.1.1 
  
  │ ├─┬ ansi-styles@2.2.0 
  
  │ │ └── color-convert@1.0.0 
  
  │ ├── escape-string-regexp@1.0.5   
  
  │ ├─┬ has-ansi@2.0.0 
  
  │ │ └── ansi-regex@2.0.0 
  
  │ ├── strip-ansi@3.0.1 
  
  │ └── supports-color@2.0.0 
  
  ├─┬ prompt@0.2.14 
  
  │ ├── pkginfo@0.3.1 
  
  │ ├─┬ read@1.0.7 
  
  │ │ └── mute-stream@0.0.6 
  
  │ ├── revalidator@0.1.8 
  
  │ ├─┬ utile@0.2.1 
  
  │ │ ├── async@0.2.10
   
  │ │ ├── deep-equal@1.0.1 
  
  │ │ ├── i@0.3.4 
  
  │ │ ├─┬ mkdirp@0.5.1 
  
  │ │ │ └── minimist@0.0.8 
  
  │ │ ├── ncp@0.4.2 
  
  │ │ └─┬ rimraf@2.5.2 
  
  │ │   └─┬ glob@7.0.0 
  
  │ │     ├─┬ inflight@1.0.4 
  
  │ │     │ └── wrappy@1.0.1 
  
  │ │     ├── inherits@2.0.1 
  
  │ │     ├─┬ minimatch@3.0.0 
  
  │ │     │ └─┬ brace-expansion@1.1.3
   
  │ │     │   ├── balanced-match@0.3.0 
  
  │ │     │   └── concat-map@0.0.1 
  
  │ │     ├── once@1.3.3 
  
  │ │     └── path-is-absolute@1.0.0 
  
  │ └─┬ winston@0.8.3 
  
  │   ├── colors@0.6.2 
  
  │   ├── cycle@1.0.3 
  
  │   ├── eyes@0.1.8 
  
  │   ├── isstream@0.1.2 
  
  │   └── stack-trace@0.0.9
   
  └── semver@5.1.0 
  
######T-CSdeMacBook-Pro% `react-native init AwesomeProject`
This will walk you through creating a new React Native project in /Users/t-cs/AwesomeProject

Installing react-native package from npm...

Setting up new React Native app in /Users/t-cs/AwesomeProject

`To run your app on iOS:`

   cd /Users/t-cs/AwesomeProject
   
   react-native run-ios
   
 -or-
   
   Open /Users/t-cs/AwesomeProject/ios/AwesomeProject.xcodeproj in Xcode
   
   Hit the Run button
   
`To run your app on Android:`

   Have an Android emulator running (quickest way to get started), or a device connected
   
   cd /Users/t-cs/AwesomeProject
   
   react-native run-android
   
####根据上面的提示，`To run your app on iOS or Android` 
######运行 iOS 应用程序：
######在 Xcode 中打开 ios/AwesomeProject.xcodeproj 并且点击运行。

######在选定的文本编辑器中打开 index.ios.js 并且编辑代码。

######点击 iOS 模拟器中的 ⌘-R 来重新加载应用程序。
 
####成果展示


     Running packager on port 8081.   
     Keep this packager running while developing on any JS projects. Feel free to close this tab and run your own packager instance if you prefer. 
     https://github.com/facebook/react-native    
                                                                            
                                                                  
                                                                            
  https://github.com/facebook/react-native    

  Running packager on port 8081.                                            
                                                                            
  Keep this packager running while developing on any JS projects. Feel      
  free to close this tab and run your own packager instance if you          
  prefer.                                                                   
                                                                            
  https://github.com/facebook/react-native 
               
Looking for JS files in

   /Users/t-cs/AwesomeProject 

[10:31:20 PM] <START> Building Dependency Graph

[10:31:20 PM] <START> Crawling File System

[10:31:20 PM] <START> Loading bundles layout

[10:31:20 PM] <END>   Loading bundles layout (1ms)

[Hot Module Replacement] Server listening on /hot

React packager ready.

[10:31:25 PM] <START> request:/index.ios.bundle?platform=ios&dev=true

[10:31:25 PM] <START> find dependencies

[10:31:32 PM] <END>   Crawling File System (11497ms)

[10:31:32 PM] <START> Building in-memory fs for JavaScript

[10:31:32 PM] <END>   Building in-memory fs for JavaScript (338ms)

[10:31:32 PM] <START> Building in-memory fs for Assets

[10:31:32 PM] <END>   Building in-memory fs for Assets (330ms)

[10:31:32 PM] <START> Building Haste Map

[10:31:33 PM] <START> Building (deprecated) Asset Map

[10:31:33 PM] <END>   Building (deprecated) Asset Map (61ms)

[10:31:33 PM] <END>   Building Haste Map (342ms)

[10:31:33 PM] <END>   Building Dependency Graph (12527ms)

[10:31:33 PM] <END>   find dependencies (8417ms)

[10:31:33 PM] <START> transform

transforming [========================================] 100% 408/408

[10:31:33 PM] <END>   transform (91ms)

[10:31:33 PM] <END>   request:/index.ios.bundle?platform=ios&dev=true (8534ms)

[10:21:46 AM] <START> request:/index.ios.bundle?platform=ios&dev=true

[10:21:47 AM] <END>   request:/index.ios.bundle?platform=ios&dev=true (132ms)

[11:59:50 AM] <START> find dependencies

[11:59:50 AM] <END>   find dependencies (228ms)

[11:59:50 AM] <START> transform

transforming [========================================] 100% 408/408

[11:59:50 AM] <END>   transform (112ms)

[12:00:42 PM] <START> request:/index.ios.bundle?platform=ios&dev=true

[12:00:42 PM] <END>   request:/index.ios.bundle?platform=ios&dev=true (48ms)

####本人用的方法和上文若有安装错漏等不对的地方，还请多多指教。



####参考原文：[ReactNativeiOS（一）安装](http://blog.csdn.net/oiken/article/details/50016549)


