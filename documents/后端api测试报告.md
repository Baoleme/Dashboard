# 测试报告

| 版本|作者|日期|描述|
| -- | -- | -- | :----- |
|0.1|humanlee1011|2018.6.28| 添加 Restaurant Account，Customer Account，Customer Order， System部分的测试报告 |
|0.2|yxlshk|2018.6.30| 添加Add table，Delete table，Create category，Handle order部分的测试报告 |
|0.3|CrystalZYP|2018.6.30| 添加Restaurant Management的部分测试报告 |

## 测试环境
 - mocha 5.1.1
 - node 8.11.2

## [API文档](https://baoleme.github.io/API-document/)
详细的API功能描述及其参数

## 测试简介
测试对象是服务器后端，采用白盒测试，以达到高代码覆盖率。

## 测试用例
### 1.  Restaurant Account

#### 1a. POST(/restaurant) 餐厅注册
| 测试内容|通过(Y/N)|
| ---- | --- |
| 字段缺少检查 | Y |
| Email格式检查 | Y |
| Email重复 | Y |
| Name格式检查 | Y |

#### 1b. POST(/restaurant/emailConfirm) 发送邮箱激活邮件
| 测试内容 | 通过 (Y/N) |
| ---- | --- |
| 登录前发送邮件 | Y |
| 登录后发送邮件 | Y |

#### 1c. GET(/restaurant/emailConfirm) 餐厅注册邮箱激活
| 测试内容 | 通过 (Y/N) |
| ---- | --- |
| 字段缺少检查 | Y |
| 验证码错误 | Y |
| 验证码正确 | Y |
| 重复激活 | Y |

#### 1d. POST(/restaurant/session) 登录
| 测试内容 | 通过 (Y/N) |
| ---- | --- |
| 字段缺少检查 | Y |
| Email格式检查 | Y |
| Password格式检查 | Y |

#### 1e. DELEET(/restaurant/session) 退出登录
| 测试内容 | 通过 (Y/N) |
| ---- | --- |
| 登录后登出 | Y |
| 登录前登出 | Y |

#### 1f. GET(/restaurant/self) 获取餐厅自身信息
| 测试内容 | 通过 (Y/N) |
| ---- | --- |
| 字段缺少检查 | Y |
| Email格式检查 | Y |
| Password格式检查 | Y |

#### 1g. PUT(/restaurant/self) 修改餐厅信息
| 测试内容 |通过(Y/N) |
| ---- | --- |
| Password格式检查 | Y |
| Name格式检查 | Y |
| Logo url格式检查 | Y |
| Description格式检查 | Y |
| Phone格式检查 | Y |
| Address格式检查 | Y |


### 2. Customer Account
#### 2a. GET(/customer/self) 获取用户自身信息
| 测试内容 |通过(Y/N) |
| ---- | --- |
| 登录前获取 | Y |
| 登录后获取 | Y |

#### 2b. POST(/customer/session) 登录，若未注册则会自动注册
| 测试内容 |通过(Y/N) |
| ---- | --- |
| 字段缺失检查 | Y |
| code验证 | Y |

#### 2c. DELETE(/customer/session) 退出登录
| 测试内容 | 通过 (Y/N) |
| ---- | --- |
| 登录后登出 | Y |
| 登录前登出 | Y |

### 3. Customer Order 用户点餐
#### Before
 - 注册商家账号
 - 登录商家账号
 - 新建分类
 - 新建菜品
 - 新建二维码
 - 退出商家账号
 - 登录顾客账号

#### 3a. GET(/restaurant/{id}) 获取餐厅信息
| 测试内容 | 通过 (Y/N) |
| ---- | --- |
| restaurant id格式检查 | Y |
| information和dish值正确 | Y |

#### 3b. POST(/order) 下单
| 测试内容 | 通过 (Y/N) |
| ---- | --- |
| 字段缺少检查 | Y |
| restaurant id格式检查 | Y |
| restaurant id存在 | Y |
| table格式检查 | Y |
| table存在 | Y |
| price格式检查 | Y |
| remark格式检查 | Y |
| dish格式检查 | Y |
| dish存在 | Y |
| dish属于该餐厅 | Y |
| price计算正确 | Y |

#### 3c. GET(/order) 获取全部订单
| 测试内容 | 通过 (Y/N) |
| ---- | --- |
| page格式检查 | Y |
| number存在 | Y |
| order list值正确 | Y |

#### 3d. POST(/order/{id}/payment) 支付订单
| 测试内容 | 通过 (Y/N) |
| ---- | --- |
| order id格式检查 | Y |
| order id存在 | Y |
| 支付 | Y |

### 4. Restaurant Management

#### Before

- 注册商家账号
- 登录商家账号
- 新建菜品分类
- 新建菜品

#### 4a. GET(/restaurant/self/order/count)获取今日订单数量

| 测试内容                         | 通过（Y/N） |
| -------------------------------- | ----------- |
| 获取的五种类型订单的数量是否正确 | Y           |

#### 4b. PUT(/category) 修改分类顺序

| 测试内容                                               | 通过（Y/N) |
| ------------------------------------------------------ | ---------- |
| 检查分类id格式的正确性                                 | Y          |
| 检查修改后的分类id的数量是否等于修改前的分类id的数量 | Y          |
| 检查是否包含不属于当前餐厅的分类id                   | Y          |
| 检查输入的字段合法时，能否正确修改分类顺序             | Y          |

#### 4c. PUT(/category/{id}) 修改分类名

| 测试内容                 | 通过（Y/N） |
| ------------------------ | ----------- |
| 检查分类id格式的正确性   | Y           |
| 检查分类id是否存在 | Y           |
| 检查分类name格式的正确性 | Y           |

#### 4d. DELETE(/category/{id}) 删除分类

| 测试内容               | 通过（Y/N） |
| ---------------------- | ----------- |
| 检查分类id格式的正确性 | Y           |
| 检查分类dump的目标id格式的正确性 | Y           |
| 检查分类id是否存在   | Y           |
| 检查分类dump的目标id是否存在   | Y           |
| 检查输入的所有字段合法时，能否正确删除分类 | Y           |

#### 4e. GET(/dish) 获取分类与菜品列表

| 测试内容                               | 通过（Y/N) |
| -------------------------------------- | ---------- |
| 获取的当前餐厅的分类和菜品列表是否正确 | Y          |

#### 4f. POST(/dish) 新增菜品

| 测试内容                                   | 通过（Y/N) |
| ------------------------------------------ | ---------- |
| 检查是否缺少字段                           | Y          |
| 检查菜品所属分类id格式的正确性             | Y          |
| 检查菜品name格式的正确性                   | Y          |
| 检查菜品price格式的正确性                  | Y          |
| 检查菜品spicy格式的正确性                  | Y          |
| 检查菜品图片url格式的正确性                | Y          |
| 检查菜品description格式的正确性            | Y          |
| 检查菜品tag格式的正确性                    | Y          |
| 检查菜品specifications格式的正确性         | Y          |
| 检查菜品所属分类id是否存在               | Y          |
| 检查当前餐厅是否存在菜品所属分类id       | Y          |
| 检查输入的所有字段合法时，能否正确添加菜品 | Y          |

#### 4g. PUT(/dish/{id}) 修改菜品

| 测试内容                                   | 通过（Y/N） |
| ------------------------------------------ | ----------- |
| 检查菜品id格式的正确性                     | Y           |
| 检查菜品所属分类id格式的正确性             | Y           |
| 检查菜品name格式的正确性                   | Y           |
| 检查菜品price格式的正确性                  | Y           |
| 检查菜品selling格式的正确性                | Y           |
| 检查菜品spicy格式的正确性                  | Y           |
| 检查菜品图片url格式的正确性                | Y           |
| 检查菜品description格式的正确性            | Y           |
| 检查菜品tag格式的正确性                    | Y           |
| 检查菜品specifications格式的正确性         | Y           |
| 检查菜品id是否存在        | Y           |
| 检查菜品所属分类id是否存在               | Y          |
| 检查当前餐厅是否存在菜品所属分类id       | Y          |
| 检查输入的所有字段合法时，能否正确修改菜品 | Y           |

#### 4h. DELETE(/dish/{id}) 删除菜品

| 测试内容                             | 通过（Y/N） |
| ------------------------------------ | ----------- |
| 检查菜品id格式的正确性               | Y           |
| 检查当前餐厅是否存在菜品id               | Y           |
| 检查输入的id合法时，能够正确修改菜品 | Y           |

### 5. System
#### POST(/image)
| 测试内容|通过|
| ---- | --- |
|JPEG格式文件|  Y|
|JPG格式文件|  Y|
|PNG格式文件|  Y|
|BMP格式文件|  Y|

## 6. Add table

| 测试内容              | 通过(Y/N) |
| --------------------- | --------- |
| 正确格式              | Y         |
| 传入格式检查（0）     | Y         |
| 传入格式检查（‘saa'） | Y         |
| 传入格式检查（“”）    | Y         |

## 7. Delete table

| 测试内容               | 通过(Y/N) |
| ---------------------- | :-------- |
| 传入无效编号（1）      | Y         |
| 传入非法编号（-1）     | Y         |
| 传入字符串（‘hahaha’） | Y         |

## 8. Create category

| 测试内容       | 通过(Y/N) |
| -------------- | --------- |
| 正确格式       | Y         |
| 非法格式（“”） | Y         |
| 非法格式（0）  | Y         |
| 非法格式（-1） | Y         |

##9. Handle order

| 测试内容                  | 通过(Y/N) |
| ------------------------- | --------- |
| 非法state格式（1）        | Y         |
| 非法state格式（‘dasdas’） | Y         |
| 非法id格式（‘sadfa’）     | Y         |

