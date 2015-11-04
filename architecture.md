# 体系结构

Laravel通过命令行工具的交互，生成和管理Laravel项目环境

Artisan可以生成框架代码和数据库架构，处理从数据库架构迁移到资源和配置管理的一切事情

## 目录结构

```
├── app       # 包含Controller, Models, Views和 assets, 项目主要代码
│   ├── Console
│   ├── Events
│   ├── Exceptions
│   ├── Http
│   ├── Jobs
│   ├── Listeners
│   ├── Policies
│   ├── Providers
│   └── User.php
├── artisan
├── bootstrap # 系统启动所需文件
│   ├── app.php
│   ├── autoload.php
│   └── cache
├── composer.json
├── composer.lock
├── config   # 配置运行时规则: 数据库，session
│   ├── app.php # 时区，区域，调试模式
│   ├── auth.php #身份验证
│   ├── broadcasting.php
│   ├── cache.php # 缓存
│   ├── compile.php
│   ├── database.php # 数据库配置与连接信息
│   ├── filesystems.php
│   ├── mail.php # 邮件配置
│   ├── queue.php
│   ├── services.php
│   ├── session.php
│   └── view.php # 模版系统
├── database
│   ├── factories
│   ├── migrations
│   └── seeds
├── dir.tree
├── gulpfile.js
├── package.json
├── phpspec.yml
├── phpunit.xml
├── public   # 唯一外界可见的服务目录，存放静态文件
│   ├── css
│   ├── favicon.ico
│   ├── index.php
│   ├── info.php
│   ├── js
│   └── robots.txt
├── readme.md
├── resources
│   ├── assets
│   ├── lang
│   └── views
├── server.php
├── storage
│   ├── app
│   ├── framework
│   └── logs
├── tests
│   ├── ExampleTest.php
│   └── TestCase.php
└── vendor   # 所有第三方代码
```


[参考](http://www.cnblogs.com/huangbx/p/Laravel_2.html)