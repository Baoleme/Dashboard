# 1.逻辑架构
逻辑架构由三层模型（表示层、业务层、持久化层）构成

## 1.1.表示层
- 顾客端使用微信小程序作为表示层，提供用户点餐子系统、用户订单子系统
- 餐厅端使用 Web 作为表示层，提供餐厅信息管理子系统、菜品管理系统、二维码管理系统、订单管理子系统、审计子系统

## 1.2.业务层
服务器充当业务层的角色，为表示层的各个子系统提供相应的服务模块

## 1.3.持久化层
- MySQL 提供了数据的持久化服务
- Redis 提供了会话的持久化服务

# 2.框架目录设计
## 2.1. 小程序
```
.
├── app.wpy
├── assets
│   └── ...
├── components
│   ├── cart
│   │   ├── CartItem.wpy
│   │   └── Cart.wpy
│   ├── Detail.wpy
│   ├── Header.wpy
│   ├── menu
│   │   ├── Category.wpy
│   │   ├── DishCounter.wpy
│   │   ├── DishItem.wpy
│   │   ├── MenuList.wpy
│   │   └── Menu.wpy              # 获取商家菜品
│   ├── OrderContent.wpy
│   ├── OrderList.wpy             # 获取订单信息
│   ├── RestaurantInfo.wpy        # 获取商家信息
│   └── SpecSelect.wpy
├── index.template.html
├── lib
│   ├── cookieJar.js
│   ├── iconfont.scss
│   ├── request.js
│   └── var.scss
├── mixins
│   ├── request.js
│   └── test.js
├── pages
│   ├── confirmOrder.wpy          # 创建订单、支付
│   ├── index.wpy                 # 登录、扫码
│   └── orderDetail.wpy           # 获取订单详情
├── store
│   ├── actions
│   │   ├── index.js
│   │   ├── menu.js
│   │   ├── order.js
│   │   ├── restaurant.js
│   │   └── user.js
│   ├── index.js
│   ├── lib.js
│   ├── reducers
│   │   ├── index.js
│   │   ├── menu.js
│   │   ├── order.js
│   │   ├── restaurant.js
│   │   └── user.js
│   └── types
│       ├── index.js
│       ├── menu.js
│       ├── order.js
│       ├── restaurant.js
│       └── user.js
└── tree.txt
```

## 2.2.后端
```
.
├── app
│   ├── controller              # 处理 http 请求
│   ├── model                   # 与数据库交互
│   ├── router                  # 与前端接口
│   └── service                 # 承载业务逻辑
├── config
├── files
├── lib
│   ├── assert.js
│   └── ...
├── logs
├── node_modules
├── script
│   ├── createDB.sql
│   └── deploy.sh
├── test
│   ├── restaurant.test.js
│   └── ....
├── Code Style.md
├── deploy_rsa.enc
├── index.js
├── nodemon.json
├── package.json
├── package-lock.json
└── README.md
```

# 3.与 ECB 关系
ECB中：
- Entity：代表系统数据，如：订单、餐厅、菜品等
- Boundary：与用户的接口，如：界面、网关、代理等
- Controller：在 Boundary 和 Entity 中衔接的媒介，编排来自 Boundary 的命令的执行

在本系统中，Boundary有三个部分：
- 顾客端小程序用户界面
- 餐厅端 Web 程序用户界面
- 服务端 Nginx 反向代理服务器

Controller 包含：
- 服务器框架目录设计中，`controller` 目录下定义了所有的相关内容，它们接收来自上述 Boundary 的命令，并编排 `service` 的执行
- 服务器框架目录设计中，`service` 目录下定义了部分相关内容，它们接收也会对来自 Boundary 的命令进行相应的编排

Entity 包含：
- 服务器框架目录设计中，`model` 目录下定义了所有服务器与 MySQL 相关的实体，承载系统数据
- 服务器在会话管理中，与 Redis 通讯的相关部分