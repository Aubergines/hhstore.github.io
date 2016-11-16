title: "Golang 开发环境搭建"
date: 2016-09-1 22:12:10
categories: Tools
tags: [golang, mac]
---
本篇介绍如何搭建 Golang 的开发环境, 以及推荐一些 go 的项目资源.

<!-- more -->


## golang 简介:

- [golang 官网](https://golang.org/)
- [golang 中文官网](https://go-zh.org/)
- [go 官方中文安装指南](https://go-zh.org/doc/install)
    - 参考此中文文档,基本不需要多介绍,就可以搭建好环境.
- [go - github](https://github.com/golang/go)
- go 的一些安利:
    - go 是 C 语言他爸, 又一个儿子. C 他爸的设计水平,不用怀疑.
        - 这里多说一句, 语言发明人本身的背景, 其实很关键.
        - 很多语言设计上先天不足, 都跟语言发明人的背景有关.
        - 比如 PHP, 发明人是个业余开发者, 缺少科学训练, 导致 PHP 早期设计上有很多缺陷, 靠后天打补丁, 是无法改变本质的不足的.
        - 比如 Python 他爸是搞数学的, 数学系的思维, 通常喜欢简化, 追求极简的解题思路, 喜欢追求最优解. 所以, Python 追求极简, 追求单一最优解.
        - 对比 Ruby 他爸是日本人, 喜欢炫技(茴香豆的茴有16种写法,这种无聊的事,爱干) 这些小聪明, 消磨太多人的精力, 除了自娱自乐, 与他人无益.
        - c 语言, 自然不必多说, 工业级排第一位的应用, c++, java等都受其影响, 而 c 他爹是正经的科班博士, 贝尔实验室的大咖.由此可见.
        - go 是 c 他爸, 几十年后又一发明, 其他几位合作者, 都是大咖中的大咖, 背靠 Google 这个大树, 还要说啥?
    - go 有 google 干爹.
    - go 的 1.6 版本之后, 性能已优化到很好
    - go 的设计理念: 更偏向工程的务实, 而不是学院派炫技.
    - go 天然支持并发编程, 这方面 Python 先天缺陷
    - go 现在在云计算领域很火, docker 等项目,多用 go
    - 国内企业实践: 
        - 七牛大量使用
        - BAT 很多业务部门在用
- 围观 go 的过程:
    - 从2013年到今天(2016年), 围观了 go 多个版本, 以及国内很多公司的实践
    - 目前这个节点,切入 go,还是比较理想的.
    - 雨痕等菊苣, 多是2012年切入, 之所以现在切入, 差不少是精力投入成本最低的
    - 现在 go 的生态圈已比较完善, 各种中文资料也比较丰富, 开源的 go 项目也多
    - 在大量开发者使用 go 的过程中, 慢慢有了 go 的最佳实践,可供参考.
    - 所以, 吃瓜群众,决定入坑了.


## go 适合谁?
- python 等脚本语言开发者:
    - 崇尚简介, go 的实践理念跟 Python 一致
    - 不喜欢 c++ 的复杂
    - 讨厌 java 的冗长语法
    - 对 ruby 低性能, 又提不起兴致
    - 苦于 Python 的性能瓶颈
    - 所以, 学一门 go 防身, 是必要的
- web 后端开发者:
    - 未来 Python 更适合快速的原型创建
    - 性能瓶颈, 用 go 重写替代


## Mac 安装 golang:
- 推荐 homebrew 方式安装:
- 当前 golang 最新版本: 1.7.1
- 设置 shell 环境变量:
    - 本机是 zsh 环境.所以修改: ~/.zprofile 文件
    - 如果是 brew 方式安装, 不需要设置 GOROOT 环境变量值.
    - 添加GOPATH环境变量:
        - 此环境变量用途: 是个人的 go 开发目录(必须)
        - 用来存放个人开发代码, 以及下载的 go 第三方包等
        - 我个人的 go 开发目录: ~/iGit/iGoSpace
    
```bash

# 初次安装 go:
-> % brew install go

# 查看过期安装包:
-> % brew outdated
go (1.6.3) < 1.7.1

# 更新 go 版本:
-> % brew upgrade go

...
You may wish to add the GOROOT-based install location to your PATH:
  export PATH=$PATH:/usr/local/opt/go/libexec/bin
==> Summary
🍺  /usr/local/Cellar/go/1.7.1: 6,436 files, 250.6M

# 安装路径:如上

# 检查是否安装成功:
-> % go version
go version go1.7.1 darwin/amd64


#################################
# 配置环境变量:
#   - zsh: 修改 ~/.zprofile
#   - bash: 修改 ~/.bash_profile
#################################


# 添加 go 环境变量:
vim ~/.zprofile

#################################
# 如下添加到 ~/.zprofile
# Golang Config:
export GOPATH=${HOME}/iGit/iGoSpace

#################################


# 刷新环境变量:
source ~/.zprofile

# 查看环境变量是否生效:
-> % echo $GOPATH
/Users/hhstore/iGit/iGoSpace

# 看到上面的路径, 可知已生效.


```

## Windows 安装 golang:

- 参考: [go 官方中文安装指南](https://go-zh.org/doc/install)


## Go 开发 IDE 选择:

- jetbrains 家 IDE 全家桶 + go 插件
    - 我常用 pycharm + go 插件
    - IDEA, PhpStorm, RubyMine等都可用
- sublime text3 + go 插件
- [这有个IDE参考列表](https://github.com/golang/go/wiki/IDEsAndTextEditorPlugins)
- 雨痕菊苣, 建议多用 命令行来编写,调试 go.深以为然,应该多多练习一下.


## Go 学习资源:

- [官方中文文档](https://go-zh.org/doc/)
    - [Go 指南 - 必读](https://go-tour-zh.appspot.com/welcome/1)
        - 这个指南, 可以在线编辑,运行 go 代码, 必读
    - go 官方中文文档,很完善, 对用户很友好
- [build-web-application-with-golang](https://github.com/astaxie/build-web-application-with-golang)
    - 中文教程
- [go 笔记 - 雨痕](https://github.com/qyuhen/book)
    - 必读, 高质量


## Go 热门项目:

- 热门项目的价值:
    - 学习语言本身
    - 学习最佳实践
    - 学习各种技术: 数据库, 并发, 网络等
- [go-project-list](https://github.com/golang/go/wiki/Projects)
- [awesome-go](https://github.com/avelino/awesome-go)
    - 列举了大量 go 项目, 可以在这里扒拉各种.
- 感兴趣的项目:
    - [beego - github](https://github.com/astaxie/beego)
    - [beego - 官网](http://beego.me/)
        - 用途: go web 框架
        - 作者:国人
    - [docker - github](https://github.com/docker/docker)
        - 热门应用, 很喜欢用
    - [tango](https://github.com/lunny/tango)
        - 用途: web 框架
        - 作者: 国人
    - [xorm](https://github.com/go-xorm/xorm)
        - 用途: 数据库 ORM
        - 作者: 国人


