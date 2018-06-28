# 测试报告

| 版本|作者|日期|描述|
| -- | -- | -- | ------ |
|0.1|humanlee1011|2018.6.28| 添加 Restaurant Account，Customer Account，Customer Order， System部分的测试报告 |

## 测试环境
 - mocha ^5.1.1
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

### 5. System
#### POST(/image)
| 测试内容|通过|
| ---- | --- |
|JPEG格式文件|  Y|
|JPG格式文件|  Y|
|PNG格式文件|  Y|
|BMP格式文件|  Y|
