# macOS 设置指南

主要记录我的Mac开发环境的设置，以及一些优秀软件，使用技巧等。所有的设置 、软件 以及技巧 都追求极致简洁和极致效率，最大可能提升工具效率，提升生产力。

## 系统

第一件事件是**升级系统**，左上角图标 -> 关于本机 -> 软件更新...

### 系统偏好设置

安全性与隐私:

* 通用，勾选 进入睡眠后活开始屏幕保护程序`立即`要求输入密码

触发角:

* 系统偏好设置/屏幕保护程序/触发角, 选择(右上桌面，左下启动台，右下启动屏幕保护)

触摸板(Trackpad):

* 选中`轻点来点按`(用起来方便)
* 修改`辅助点按`为`点按右下角`

程序坞(Docker):

* Dock只放置常用App
* 大小设置到最小(拖到最左边)，以显示最小图标
* 选中`自动显示和隐藏程序坞`，建议移动至左侧

键盘(Keyboard):

* F1 - F12 设置为标准功能键
* 设置`按键重复` 最快
* 设置`重复前延迟` 最短

节能:

* 系统偏好设置/辅助功能/显示, 勾选 (减弱动态效果、减少透明度)

取消自动更新:

* AppStore → Preference → Automaticallycheck forupdates

## Homebrew

[Homebrew](https://brew.sh/) 是一款Mac OS平台下的软件包管理工具，拥有安装、卸载、更新、查看、搜索等很多实用的功能。简单的一条指令，就可以实现包管理，而不用你关心各种依赖和文件路径的情况，十分方便快捷 小编注: macOS缺失的软件包的管理器，通过命令行安装 Mac 软件的工具(大部分是命令行工具)。

### Homebrew的安装

安装依赖:

```sh
xcode-select --install
```

安装:

```sh
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

最后确认是否安装成功:

```sh
brew doctor
```

### Homebrew的常用命令

安装软件:

```sh
brew install <formula>
```

查看是否有需更新软件:

```sh
brew outdated
```

更新软件:

```sh
brew upgrade <formula>
```

删除老版本的软件:

```sh
brew cleanup
```

查看已安装的软件列表:

```sh
brew list --versions
```

搜索软件:

```sh
brew search <formula>
```

查看软件详情:

```sh
brew info <formula>
```

卸载软件:

```sh
brew uninstall <formula>
```

### 安装常用工具

工具名 | 安装命令 | 备注
---- | ---- | ----
git | brew install git | 版本管理工具
wget | brew install wget | 下载工具
curl | brew install curl | 下载工具
tmux | brew install tmux | 终端复用神器
vim | brew install vim | 升级 vim 至8.x版本，替代系统自带的
JDK | brew cask install java | open jdk java
tree | brew install tree | 目录展示工具
lua | brew install lua | lua编程语言
coreutils | brew install coreutils | gnu 核心工具
bin | brew install binutils | gnu bin工具
diff | brew install | diffutils | gnu 比较工具
find | brew install findutils | gnu 查找工具
ag | brew install the_silver_searcher | 高效内容查找
rzsz | brew install lrzsz | ssh 上传下载文件，适用于跳板机环境
go | brew install go | go 语言
node | brew install node | node
jq | brew install jq | 命令行json处理工具
htop | brew install htop | 替代top
axel | brew install axel | 多线程下载工具
cloc | brew install cloc | 代码统计工具
shellcheck | brew install shellcheck | shell 脚本检查工具
tldr | brew install tldr | 命令行示例
ncdu | brew install ncdu | 磁盘空间占用分
glances | brew install glances | 监控工具
figlet | brew install figlet | 艺术字转换
screenFetch | brew install screenFetch | 系统信息
nmap | brew install nmap | 网络扫描工具
ctop | brew install ctop | docker 容器监控工具
pstree | brew install pstree | 进程树查看
bash-completion | brew install bash-completion | bash补全
lolcat | brew install lolcat | 彩虹文字
peco | brew install peco | go 写的极简过滤工具
cowsay | brew install cowsay | ascii图片
graphviz | brew install graphviz | 拓扑图绘制工具

### 扩展1 - brew cask

通过 Homebrew Cask 优雅、简单、快速的安装和管理 OS X 图形界面程序。不会再出现了“要安装，请拖动此图标......”。

安装:

```sh
#安装Homebrew Cask（可选 正常安装的Homebrew不需要）
brew tap caskroom/cask
brew install brew-cask

#使用Homebrew Cask安装软件
brew cask install <appName>
#多包一起安装
brew cask install <appName1> <appName2> <appName3>

#更新 Homebrew Cask
brew cask update

#使用Homebrew Cask卸载软件
brew cask uninstall <appName>

#使用Homebrew Cask搜索软件
#列出所有可以被安装的软件
brew cask search
#查找所有与keyword关键词有关的软件
brew cask search keyword

#查看软件信息
brew cask info <appName>

#删除 Homebrew Cask 下载的包
brew cask cleanup

#列出通过 Homebrew Cask 安装的包
brew cask list
```

brew cask 安装常用工具:

[quick-look-plugins](https://github.com/sindresorhus/quick-look-plugins)

* QLColorCode - Preview source code files with syntax highlighting
* QLStephen - Preview plain text files without or with unknown file extension. Example: README, CHANGELOG, index.styl, etc.
* QLMarkdown - Preview Markdown files
* QuickLookJSON - Preview JSON files
* BetterZipQL - Preview archives
* qlImageSize - Display image size and resolution
* ...

APP类:

* switchhosts - Switch hosts quickly<https://github.com/oldj/SwitchHosts>
* hiddenbar - A ultra-light MacOS utility that helps hide menu bar icons <https://formulae.brew.sh/cask/hiddenbar>
* Caffeine - Don't let your Mac fall asleep <https://formulae.brew.sh/cask/caffeine>
* spectacle - Move and resize windows with ease <https://formulae.brew.sh/cask/spectacle>
* Transmission - a cross-platform BitTorrent client. <https://formulae.brew.sh/cask/transmission>
* iina - The modern media player for macOS. <https://formulae.brew.sh/cask/iina>
* flux - makes the color of your computer's display adapt to the time of day, warm at night and like sunlight during the day. <https://formulae.brew.sh/cask/flux>

### 扩展2 - Homebrew Services

A nice extension to Homebrew is [homebrew-services](https://github.com/Homebrew/homebrew-services). It will automatically launch things like databases when your computer starts, so you don't have to do it manually every time.

手动添加服务(一般情况 安装时已经添加):

```sh
brew services <formula>
```

启动服务:

```sh
brew services start <formula>
```

查看服务状态:

```sh
brew services list
```

### brew 的备份和恢复

如果要在两台 Mac 间备份和恢复 brew 安装的包，可以使用：

```sh
brew bundle dump    # dump
brew bundle         # 恢复
```

brew bundle dump 会生成一个 Brewfile 文件，这是一个纯文本的文件，里面列举了系统上的 brew 配置和安装的列表，那么我只需要维护一个 Brewfile 文件就可以一键安装必备的命令和桌面软件了。

### 使用Homebrew中遇到的问题记录

Q1: cannot load such file -- active_support/core_ext/object/blank (LoadError):

```sh
brew doctor
Traceback (most recent call last):
 4: from /usr/local/Homebrew/Library/Homebrew/brew.rb:23:in `<main>'
 3: from /usr/local/Homebrew/Library/Homebrew/brew.rb:23:in `require_relative'
 2: from /usr/local/Homebrew/Library/Homebrew/global.rb:13:in `<top (required)>'
 1: from /System/Library/Frameworks/Ruby.framework/Versions/2.6/usr/lib/ruby/2.6.0/rubygems/core_ext/kernel_require.rb:54:in `require'
/System/Library/Frameworks/Ruby.framework/Versions/2.6/usr/lib/ruby/2.6.0/rubygems/core_ext/kernel_require.rb:54:in `require': cannot load such file -- active_support/core_ext/object/blank (LoadError)
```

解决方案:

```sh
brew update-reset
```

Q2:error: The last gc run reported the following. Please correct the root cause and remove .git/gc.log. Automatic cleanup will not be performed until the file is removed.

warning: There are too many unreachable loose objects; run 'git prune' to remove them.

```sh
# fix
cd "$(brew --repo)" # Navigate to Homebrew's git repository
git prune && git gc # Remove loose objects
rm -rf /usr/local/Homebrew/Library/Taps/homebrew/homebrew-core/.git/gc.log

# check
cd - # Go back to the original location
brew update
```

参考: <https://stackoverflow.com/questions/34859640/error-when-trying-to-brew-update/34869798>

Q3: Error: Another active Homebrew update process is already in progress.

```sh
rm -rf /usr/local/var/homebrew/locks # 删除临时文件
```

Q4: 卡在 Updating Homebrew 好久

关闭自动更新，在. zshrc 文件中加入下方命令，如果是 bash 请加在. bash_profile 文件中，全局变量可以 sudo vi /etc/profile

```sh
vim ~/.zshrc
export HOMEBREW_NO_AUTO_UPDATE=true

# 刷新环境变量
source ~/.zshrc
```

## iTerm2

Mac命令行终端神器，更优雅地 command-line 工作姿势，请使用 [iTerm2](http://www.iterm2.com/)。

使用 `Homebrew` 安装

```sh
brew cask install iterm2
```

再说说配置。

### 偏好设置(Preference)

前往 **iTerm2 > Preferences...**，**General** tab - Closing，取消"Confirm closing multiple sessions"和"Confirm 'Quit iTerm2(Cmd+Q)'"的打勾。

在 **Profiles** tab，点击"+"图标，新建一个以自己名字命名的Profile，同时设置为默认的(Other Actions... > Set as Default)，然后在**General**中设置**Working Directory**为**Reuse previous session's directory**。最后，在**Window**中调整显示大小至合适的(i.e. Columns: 125 and Rows: 35)。

最后记得设置静音模式，Go to profiles -> Default(or yours) -> Terminal -> Check silence bell to disable the terminal session from making any sound。

### 快捷键(⌘←, ⌘→ and ⌥←, ⌥→)

日常编码习惯使用⌘←, ⌘→ and ⌥←, ⌥→来快速切换光标，通过以下方式来设置iTerm2实现这四个快捷键。

设置路径: preferences (⌘ + ,) -> Profiles -> Keys -> Click on + icon (add new Keyboard shortcut)

快捷键 | action | Esc+
---- | ---- | ----
⌘← | Send Escape Sequence | OH
⌘→ | Send Escape Sequence | OF
⌥← | Send Escape Sequence | b
⌥→ | Send Escape Sequence | f

### 配色

[iterm2 配色官网](https://iterm2colorschemes.com/)

> iterm2 > preference > profiles > colors > Color Presets > solarized dark

### zsh

Mac系统自带了zsh，但不是新版的，如果喜欢新版可以通过Homebrew来安装:

```sh
# 安装 zsh 及 补全
brew install zsh zsh-completions
```

接下来，修改相关配置，在/etc/shells文件中加入如下一行:

```sh
/usr/local/bin/zsh
```

然后运行命令

```sh
chsh -s /usr/local/bin/zsh
```

注意，zsh的配置文件是`.zshrc`。`~/.bash_profile`将不再被加载，该文件是默认shell(bash)的配置文件。

下面你需要[Oh My Zsh](https://github.com/robbyrussell/oh-my-zsh) 或者 [Prezto](https://github.com/sorin-ionescu/prezto) 来管理`zsh`的配置，这里选择`oh-my-zsh`。

#### Oh My Zsh

安装

```sh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

配置

```sh
# 设置主题
ZSH_THEME=pygmalion
# 设置插件
plugins=(git colorize github jira vagrant virtualenv pip python brew osx docker)

# ls 配色生效
unset LSCOLORS
export CLICOLOR=1
export CLICOLOR_FORCE=1

# 生效
source ~/.env.sh
```

其他`插件`、`主题`请参考[oh-my-zsh wiki](https://github.com/ohmyzsh/ohmyzsh/wiki)。

#### env.sh

可以用`env.sh`做些预定义设置，在`~/.zshrc`添加，

```sh
source ~/<path to file>/env.sh
```

添加配置信息(个人的配置，大伙自定义):

```sh
#!/bin/zsh

# Add commonly used folders to $PATH
export PATH="/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin"

# Specify default editor. Possible values: vim, nano, ed etc.
export EDITOR=vim

# File search functions
function f() { find . -iname "*$1*" ${@:2} }
function r() { grep "$1" ${@:2} -R . }

# Create a folder and move into it in one command
function mkcd() { mkdir -p "$@" && cd "$_"; }

# Example aliases
alias cppcompile='c++ -std=c++11 -stdlib=libc++'
alias g='git'
```

## Git

Mac有预安装 [Git](https://git-scm.com/)，不过 还是通过Homebrew 来安装、管理Git。

```sh
brew install git

which git
```

将得到 `/usr/local/bin/git`。

### 基本配置信息

下载 [.gitconfig](https://raw.githubusercontent.com/nicolashery/mac-dev-setup/master/.gitconfig)

```sh
cd ~
curl -O https://raw.githubusercontent.com/nicolashery/mac-dev-setup/master/.gitconfig
```

以上做个一些基本命令(`status`,`branch`, `diff`)的配色，以及新增一些别名(tags, branches, remotes)。

用户信息配置:

```sh
git config --global user.name "Your Name Here"
git config --global user.email "your_email@youremail.com"
```

添加全部`.gitignore`，小编的工作环境是Mac，需要将`.DS_Store`默认加入每个项目的`.gitignore`。

```sh
cd ~
curl -O https://raw.githubusercontent.com/nicolashery/mac-dev-setup/master/.gitignore
git config --global core.excludesfile ~/.gitignore
```

常用的gitignore信息 请参见<https://www.gitignore.io/>。

### GitHub配置

```sh
brew cask install github
```

## Python

MacOS自身已经带有[Python](https://python.org/)，这个Python主要用于支持系统文件和XCode，我们为了不跟系统的混淆，安装自己所需的Python吧。

安装方式有两种:

* Homebrew
* Pyenv - Python 版本管理工具

### 安装 Homebrew方式

```sh
brew install python # Python 3(default)

brew install python@2 # Python 2.7
```

### 安装 通过Pyenv方式

通过 [Pyenv](https://github.com/pyenv/pyenv) 方式来安装，为方便管理不同版本的Python。

```sh
brew install pyenv
```

配置环境变量:

```sh
echo 'eval "$(pyenv init -)"' >> ~/.zshrc
# commands.md <https://github.com/pyenv/pyenv/blob/master/COMMANDS.md>

eval "$(pyenv virtualenv-init -)" >> ~/.zshrc
# 如果使用默认的shell，添加配置至 ~/.bash_profile
```

根据[pyenv wiki](https://github.com/pyenv/pyenv/wiki)建议，安装一些依赖:

```sh
brew install openssl readline sqlite3 xz zlib
```

### pyenv 常用命令

```sh
pyenv commands # 显示所有可用命令

pyenv install --list # 查看可安装 Python 版本

pyenv install 3.x.x # look for the latest 3.x version, and install it (replace the .x.x with actual numbers)
pyenv uninstall 3.x.x

pyenv versions # 查看本机安装 Python 版本

pyenv shell 3.x.x # 设置面向 shell 的 Python 版本，通过设置当前 shell 的 PYENV_VERSION 环境变量的方式。这个版本的优先级比 local 和 global 都要高。–unset 参数可以用于取消当前 shell 设定的版本。
pyenv shell --unset

pyenv global 3.6.8 # 设置全局的 Python 版本，通过将版本号写入 ~/.pyenv/version 文件的方式
pyenv rehash # 创建垫片路径

pyenv local 3.x.x # 独立项目的python版本设置，保存在项目目录里的`.python-version`

pyenv virtualenv 3.6.8 env-3.6.8 # 创建虚拟环境
pyenv activate env-3.6.8 # 激活虚拟环境
pyenv deactivate #退出虚拟环境
```

全部命令参见 [pyenv commands](https://github.com/pyenv/pyenv/blob/master/COMMANDS.md)。

### pyenv 安装慢问题

pyenv install 下载非常慢甚至卡住，还会出错`error: failed to download`。

加速方式:

* 使用淘宝镜像源加速：<https://npm.taobao.org/mirrors/python/>
* 下载需要的版本放到~/.pyenv/cache文件夹下面
* 然后执行 pyenv install 版本号 安装对应的python版本

### pip python包管理

Python安装时，同时会安装[pip](https://pip.pypa.io/en/stable/)。

#### pip 配置文件

```sh
# 创建 pip 配置目录
mkdir ~/.pip

# 编辑配置
vim ~/.pip/.pip.conf

# 添加以下内容
[list]
format=columns
[global]
download_cache = ~/.cache/pip
index-url = http://mirrors.aliyun.com/pypi/simple/
[install]
trusted-host=mirrors.aliyun.com
```

#### pip 常用命令

```sh
pip install <package> # to install a Python package

pip install --upgrade <package> # to upgrade a package

pip freeze # to see what's installed

pip uninstall <package> # to uninstall a package
```

### virtualenv

[virtualenv](https://virtualenv.pypa.io/) is a tool that creates an isolated Python environment for each of your projects. virtualenv 就是一个能够创建隔离的 python 环境的工具。

这里使用一个基于 pyenv 的插件：pyenv-virtualenv。

```sh
brew install pyenv-virtualenv

# 创建工作环境
pyenv virtualenv (python-version) (workspace-name)
# 激活环境
pyenv activate (workspace-name)
# 退出环境
pyenv deactivate
## 在这个隔离的虚拟环境中，可以使用 pip 安装需要的包，而不会影响到其他的 python 版本。但是可能会在 home directory 下创建一些隐藏目录（如 keras、matplotlib、jupyter 等）

```

## Java 环境

先检查`是否已经安装`:

```sh
java -version
```

若得到以下信息，说明本地具有Java的开发环境。

```sh
java version "1.8.0_74"
Java(TM) SE Runtime Environment (build 1.8.0_74-b02)
Java HotSpot(TM) 64-Bit Server VM (build 25.74-b02, mixed mode)
```

若没有，则参考下面信息安装。

### 通过Oracle官网下载

[Oracle website](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)

### Homebrew(推荐)

#### 注意: 更新

Java8 is no longer available on Homebrew. Use below command instead :

```sh
brew cask install adoptopenjdk/openjdk/adoptopenjdk8
```

* [Java8 not working anymore](https://github.com/Homebrew/homebrew-cask-versions/issues/7253)
* [adoptopenjdk](https://adoptopenjdk.net/)

===========================================================

```sh
brew update
brew tap caskroom/versions
```

安装 java 9:

```sh
brew cask install java
```

或者，安装java 8:

```sh
brew cask install java8
```

### 设置`JAVA_HOME`

往`env.sh`添加环境变量 `JAVA_HOME`:

```sh
export JAVA_HOME="`/usr/libexec/java_home -v 1.8`"
```

或者，你使用Java 9:

```sh
export JAVA_HOME="`/usr/libexec/java_home -v 9`"
```

Java开发IDE推荐[IntelliJ](https://www.jetbrains.com/idea/download/)，另附 [IntelliJ-IDEA-Tutorial](https://github.com/judasn/IntelliJ-IDEA-Tutorial)。

jetbrains-agent 参考: <https://zhile.io/2018/08/25/jetbrains-license-server-crack.html>

### 小工具

* jd-gui: a standalone graphical utility that displays Java sources from CLASS files. `brew cask install JD-GUI`

## Node.js

The recommended way to install [Node.js](http://nodejs.org/) is to use [nvm](https://github.com/creationix/nvm) (Node Version Manager) which allows you to manage multiple versions of Node.js on the same machine.

### Installing and Updating nvm

script command: <https://github.com/nvm-sh/nvm#install--update-script>

常用命令:

```sh
# verify that it was installed correctly
command -v nvm

# View the all available stable versions of Node
nvm ls-remote --lts

# Install the latest stable version, also set the first version installed as your default version.
nvm install node

# install another specific version
nvm install 10

# switch between versions
nvm use 10
nvm use default

# See which versions you have install
nvm ls

# Change the default version
nvm alias default 10

# create a .nvmrc file containing the Node.js version the project uses
echo "10" > .nvmrc
# load the correct version of Node.js
nvm use
```

### yarn

[yarn](https://classic.yarnpkg.com/en/) 是由Facebook、Google、Exponent 和 Tilde 联合推出了一个新的 JS 包管理工具， 是为了弥补 npm 的一些缺陷而出现的。

Intall command: `brew install yarn`.

配置:

```sh
yarn config set registry http://registry.npm.taobao.org
```

Yarn 和 npm 的区别：

* [npm和yarn的区别，我们该如何选择？](https://zhuanlan.zhihu.com/p/27449990)
* [Npm vs Yarn 之备忘详单](https://www.jeffjade.com/2017/12/30/135-npm-vs-yarn-detial-memo/)

## MySQL

一般通过`Homebrew`来安装[MySQL](http://www.mysql.com/)。*注: 我们常用5.7版本，可以通过命令`brew install mysql@5.7`来安装*

```sh
# 安装
brew install mysql

# 启动(开机自启动)
brew services start mysql

# mysql path
echo 'export PATH="/usr/local/opt/mysql@5.7/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc

# 修改密码(默认无密码，不影响本地的开发)
mysqladmin -u root password 'new-password'
```

### GUI Tool

[Sequel Pro](http://www.sequelpro.com/):

```sh
brew cask install sequel-pro
```

使用Sequel Pro 导出表结构图:

1. 安装graphviz： `brew install graphviz`
2. 用Sequel Pro导出Dot文件
3. 用dot命令: `dot -Tjpg test.dot > test.jpg`

DataGrip：jetbrains 旗下跨平台的数据库管理工具。

Navicat：<https://www.navicat.com/en/>，及科学安装教程 <https://zhuanlan.zhihu.com/p/108692959>

Falcon<https://github.com/plotly/falcon>: 一个免费的、开源的SQL编辑器，具有内联数据可视化功能。它目前支持连接RedShift、MySQL、PostgreSQL、IBM DB2、Impala、MS SQL、Oracle、SQLite 等。

## Redis

安装:

```sh
brew install redis
```

启动:

```sh
brew services start redis
```

more information refer to Redis' [documentation](http://redis.io/documentation).

redis GUI tool: [medis]<https://github.com/luin/medis>

## Visual Studio Code

[Visual Studio Code](https://code.visualstudio.com/) 是一款免费开源的现代化轻量级代码编辑器，支持几乎所有主流的开发语言的语法高亮、智能代码补全、自定义热键、括号匹配、代码片段、代码对比 Diff、GIT 等特性，支持[插件扩展](https://code.visualstudio.com/docs/editor/extension-gallery)，并针对网页开发和云端应用开发做了优化。

### vscode 安装

使用`Homebrew`方式来安装:

```sh
brew cask install visual-studio-code
```

也可以通过[下载](https://code.visualstudio.com/Download)来安装。

Note: 建议在`程序坞`保留Visual Studio Code(和iterm一样)，右击Docker中的图标 **选项 > 在程序坞中保留**。

### vscode 配置

进入**Code > Preferences > Settings**(快捷键是 **Cmd + ,**)，然后在右上角点击`打开设置(json)`，粘贴以下配置信息(参考):

```json
{
    "files.autoSave": "afterDelay",
    "files.insertFinalNewline": true,
    "files.trimTrailingWhitespace": true,
    "editor.formatOnPaste": true,
    "editor.tabSize": 2,
    "editor.rulers": [
        80
    ],
    "workbench.editor.enablePreview": false
}
```

以上方式可以在你的新设备，快速配置vscode。日常修改配置时，你可以通过配置(ui)的搜索功能，快速定位配置项来做修改。

### 配置命令行中打开

如果你只想记住一个vscode的快捷键，那它会是`Cmd+Shift+P(⇧ ⌘ P)`，用来打开`命令面板`。

接着，马上使用下`命令面板`来安装插件，用来通过[`终端命令`快速打开VS Code](https://code.visualstudio.com/docs/setup/mac#_launching-from-the-command-line)。

`Cmd+Shift+P` > `Shell Command: Install 'code' command in PATH`。

这样，你可以在终端直接打开项目:

```sh
cd myproject/
code . ## 打开文件夹

code myfile.txt ## 打开文件
```

### vscode 插件安装

* Chinese (Simplified) Language Pack for Visual Studio Code(本地化)
* markdownlint(markdown格式检查器)
* atom one dark theme(ATOM 风格主题)
* one dark pro(主题)
* material theme(主题)
* vscode-icons(图标)
* Image preview(图片预览: 光标悬浮在图片路径上时显示)

#### vscode python 解释器选择

`Cmd+Shift+P(⇧ ⌘ P)` > `select interpreter`

#### python 编程

[Editing Python in Visual Studio Code](https://code.visualstudio.com/docs/python/editing)

## Vim

虽然VS Code将是我们的主要编辑器，但日常工作中还需掌握[Vim](https://www.vim.org/)的基本用法。

Vim是一个高度可配置的文本编辑器，用于高效地创建和更改任何类型的文本。

### Vim 安装

通过`homebrew`安装最新版:

```sh
brew install vim
```

### vimrc - The Ultimate vimrc

[The Ultimate vimrc](https://github.com/amix/vimrc) 是史上最强、最全的vimrc配置。

提供两个版本:

* The Basic 基础版本
* The Awesome

#### 安装 Awesome 版本

```sh
git clone --depth=1 https://github.com/amix/vimrc.git ~/.vim_runtime
sh ~/.vim_runtime/install_awesome_vimrc.sh
```

#### 安装 Basic 版本

```sh
git clone --depth=1 https://github.com/amix/vimrc.git ~/.vim_runtime
sh ~/.vim_runtime/install_basic_vimrc.sh
```

### 更新 amix/vimrc.git

```sh
cd ~/.vim_runtime
git pull --rebase
python update_plugins.py
```

## Sublime Text

[Sublime Text](http://www.sublimetext.com/) 是广泛使用到的编辑器，官方定义: a sophisticated text editor for code, markup and prose.

### 安装

与常规App安装一样，前往官网[下载](http://www.sublimetext.com/)，拖拽至`Applications`文件夹。

### 设置CLI方式打开文件

```sh
ln -s /Applications/Sublime\ Text.app/Contents/SharedSupport/bin/subl /usr/local/bin/subl
```

然后，你可以在终端快速打开文件 `subl myfile.py`，或者打开当前目录 `subl .`。

### Sublime Text 设置

偏好设置，这是一份基础开发配置(参考):

```json
{
    "auto_complete_delay": 5,
    "auto_complete_selector": "source, text",
    "color_scheme": "Packages/User/Monokai (SL).tmTheme",
    "create_window_at_startup": false,
    "folder_exclude_patterns":
    [
        ".svn",
        ".git",
        ".DS_Store",
        "__pycache__",
        "*.pyc",
        "*.pyo",
        "*.exe",
        "*.dll",
        "*.obj",
        "*.o",
        "*.a",
        "*.lib",
        "*.so",
        "*.dylib",
        "*.ncb",
        "*.sdf",
        "*.suo",
        "*.pdb",
        "*.idb",
        "*.psd"
    ],
    "font_face": "Source Code Pro",
    "font_size": 13,
    "ignored_packages":
    [
        "Markdown",
        "Vintage"
    ],
    "open_files_in_new_window": false,
    "rulers":
    [
        80
    ],
    "translate_tabs_to_spaces": true,
    "word_wrap": true
}
```

### 安装 Package Control

Package Control 可方便管理Sublime text的插件，最方便的安装方式是 如下:

* 打开`Console`: ctrl+\` 快捷键 或者通过菜单 `View > Show Console`打开
* 参考<https://packagecontrol.io/installation> 执行相关命令

推荐的插件有:

* [Git](https://github.com/kemayo/sublime-text-git): Plugin for some Git integration
* [SublimeLinter](https://sublimelinter.readthedocs.io/en/stable/): Interactive code linting framework for Sublime Text 3
* [IndentXML](https://github.com/alek-sys/sublimetext_indentxml): Plugin for re-indenting XML and JSON files

## Docker

[Docker](https://docs.docker.com/)是开发人员和系统管理员开发、发布和运行应用程序的平台。如果你也使用`Oh My Zsh`，推荐使用[Docker插件](https://github.com/ohmyzsh/ohmyzsh/wiki/Plugins#docker)。

### Docker 安装

官网: <https://docs.docker.com/docker-for-mac/install/>下载安装包。或者使用`Homebrew-Cask`方式 `brew cask install docker`。

启动你的第一个容器: `docker run hello-world`。

新人请阅读[快速入门教程](https://docs.docker.com/get-started/)。

Docker的命令参考[docker-cheat-sheet](https://github.com/wsargent/docker-cheat-sheet)。

#### 镜像加速器

参考阿里云的: <https://cr.console.aliyun.com/cn-hangzhou/instances/mirrors>

### Docker 安装2

安装yum-utils：

```sh
yum install -y yum-utils device-mapper-persistent-data lvm2
```

为yum源添加docker仓库位置：

```sh
yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
```

安装docker:

```sh
yum install docker-ce
```

启动docker:

```sh
systemctl start docker
```

Docker cheat-sheet: [](./docker-cheatsheet.md)

## Elasticsearch

[Elasticsearch](https://www.elastic.co/products/elasticsearch)是一个分布式搜索和分析引擎。

```sh
# 安装
brew install elasticsearch

# 运行
brew services start elasticsearch

# test
curl -XGET 'http://localhost:9200/'
```

文档: <https://www.elastic.co/guide/en/elasticsearch/reference/current/index.html> [Elasticsearch: The Definitive Guide](https://www.elastic.co/guide/en/elasticsearch/guide/master/index.html)

GUI: [dejavu](https://github.com/appbaseio/dejavu)

cheatsheet: [elasticsearch-cheatsheet](./elasticsearch-cheatsheet.md)

## 其他 - 软件

### 替代APP Store

通过 App Store 安装的应用可以通过 mas 来管理。

### 邮箱客户端

* [Foxmail](http://www.foxmail.com/mac/en) - Fast email client.
* [Airmail](http://airmailapp.com/) - Fast email client. For both Mac OS and iOS.

### 画流程图

* **StarUML** `brew cask install StarUML`
* [ProcessOn](https://www.processon.com/)
* **draw.io** <https://app.diagrams.net/>

#### 附1.StarUML破解

参考: <https://gist.github.com/trandaison/40b1d83618ae8e3d2da59df8c395093a>

上面提到了2.0版本 和 3.0版本的破解方案，本人使用的版本是3.2.2，使用修改源码方式 亲测可用。

### PDF阅读

* [PDF Expert](https://pdfexpert.com/) - PDF reader/editor
* Skim<https://skim-app.sourceforge.io/> - PDF reader and note-taker for OS X.

### API测试

* Insomnia: API接口测试。美观小巧大方，非常适合个人使用。
* PostMan

### Alfred

```sh
brew cask install alfred
```

Guides and Tutorials: <https://www.alfredapp.com/help/guides-and-tutorials/>

### Charles

抓包神器 / Mock工具

### PicGo

图床管理工具。

```sh
brew cask install picgo
```

### Dash

Mac专属的文档管理工具

### 时间管理

`Rescue Time` 日常行为管理。可以分析出日常使用电脑时间分配，细化到软件/网站层面，对于提升工作效率还是很有意义的。

```sh
brew cask install rescuetime
```

stretchly<https://github.com/hovancik/stretchly> - break time reminder app.

```sh
brew update && brew cask install stretchly
```

Focus is a distraction blocker that helps you improve your productivity(一个漂亮的番茄工作法为基础的时间管理工具。)

```sh
brew cask info focus
```

### 窗口管理

[Rectangle](https://github.com/rxhanson/Rectangle) is a window management app based on Spectacle, written in Swift.

`sizeup`: 窗口管理, 多/大显示器尤其实用

### IINA

多媒体播放，mpv内核,开源软件,快速迭代中,强推.

### The Unarchiver

解压缩神器

### HandShaker

情怀工匠精神锤出品，mac上管理安卓手机文件一把好手

### 下载工具 Motrix

[motrix](https://motrix.app/)是一款全能的下载工具，支持下载 HTTP、FTP、BT、磁力链、百度网盘等资源。

```sh
brew update && brew cask install motrix
```

### 壁纸应用 pap.er

```sh
brew cask install paper
```

### 更多

* Manico 是一个为 macOS 设计的快速启动和切换 App 的工具，使用简单没有学习成本。
* shuttle ：让我们更加方便地远程登录某台机器。
* XMind :思维导图
* Axure ：最强大的原型图制作工作，可以共享协作
* gif截图工具：Gifox。截图工具 ：Xnip（command+shift+4是mac自带的截图也很好用）
* 录屏工具: kap <https://getkap.co/>
* Mac APP 卸载： AppCleaner
* [NetNewsWire](https://ranchero.com/netnewswire/) 是一个可以在 Mac 及 iPhone 上使用的免费开源的 RSS 阅读器
* 压缩图片 用 Google 的 Squoosh<https://squoosh.app/>
* 剪切板增强管理工具 CopyQ `brew cask install copyq`
* OpenInTerminal<https://github.com/Ji4n1ng/OpenInTerminal> 可以实现在 Finder 目录中，立即打开终端
* [Mac keyboard shortcuts](https://support.apple.com/en-us/HT201236)

## 参考

* [awesome-mac](https://github.com/jaywcjlove/awesome-mac/blob/master/README-zh.md)
* [macOS Setup Guide](http://sourabhbajaj.com/mac-setup/)
* [mac-dev-setup](https://github.com/nicolashery/mac-dev-setup)
* [使用 pyenv 管理 Python 版本](http://einverne.github.io/post/2017/04/pyenv.html)
* [还在用 Win？教你从零把 Mac 打造成开发利器](https://mp.weixin.qq.com/s/qRzpNHZSL6hnZNwUnoaO1g)
* [MacBook Pro 初始设置记录](https://einverne.github.io/post/2020/07/macbook-pro-initial-setup.html)
* [强迫症的 Mac 设置指南](https://github.com/macdao/ocds-guide-to-setting-up-mac)
* [My wonderful world of macOS](https://github.com/nikitavoloboev/my-mac-os)
