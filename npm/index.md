### 2020-2-26

#### 1.Npm 淘宝镜像切换

```
修改 npm 安装资源的源
npm config set registry https://registry.npm.taobao.org

测试有没有修改成功，如果返回的跟上面设置的一样则说明修改成功了
npm config get registry

再次使用该命令创建就会发现这次快很多了
create-react-app my-app

切换回 npmjs 源
npm config set registry=http://registry.npmjs.org
```

#### 2.使用 nvm 安装管理多个版本的 node.js

```
1. 安装 nvm 版本管理器
打开“终端”窗口，输入如下命令，在线安装 nvm 软件:
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.32.1/install.sh|bash
安装成功之后，在“终端”窗口，输入 nvm 命令，验证 nvm 是否安装成功

2 使用 nvm 安装 Node.js
安装指定版本的 Node.js
nvm install v6.9.1

3 指定当前使用的 Node.js 版本
nvm use v6.9.1

4 查看当前安装的 Node.js 版本列表
nvm ls
```

#### 3.Mac 系统的 nvm 软件切换镜像源

```
1.根据 nvm 官方提供的帮助文档，我们可以通过以下命令进行切换。
export NVM_NODEJS_ORG_MIRROR="http://npm.taobao.org/mirrors/node"
如果并不想每次打开“终端”，都需要重新设置 NVM_NODEJS_ORG_MIRROR 环境变量。

2.如果“终端”使用的是 bash Shell 的话(一般是 Mac 系统终端默认)向 ~/.bash_profile 文件(如果没有，会自动创建)增加以下内容:

export NVM_NODEJS_ORG_MIRROR="http://npm.taobao.org/mirrors/node"
source ~/.nvm/nvm.sh

3.如果“终端”使用的是 zsh Shell 的话(一般是 Mac 开发人员使用)向 ~/.zshrc 文件(如果没有，会自动创建)增加以下内容:

export NVM_NODEJS_ORG_MIRROR="http://npm.taobao.org/mirrors/node"
source ~/.nvm/nvm.sh
```
