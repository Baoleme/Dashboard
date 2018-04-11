**用例图**
![](../img/use_case_img3.0.png)

**流程图**
 - 顾客使用流程图
    ![](../img/流程图-顾客.png)

 - 商家使用流程图
    ![](../img/流程图-商家.png) 

**基本用例：**
 -  注册登录：一个餐厅作为一个店铺用户注册并登录系统。
 -  管理菜色信息：餐厅上传餐厅信息（餐厅简介、广告语）、食品信息（价格、数量、介绍、图片），并允许实时改动菜色信息。
 -  生成每桌二维码：餐厅管理员用系统为每张餐桌生成二维码。
 -  查看账单：查询近期账单（各菜色的销量、收入）。
 -  接单并生成票据：餐厅收到点餐信息（桌号、餐饮类型与数量、备注），以及用户的付款，根据信息打印票据。
 -  点餐：顾客进入餐厅，用手机扫描桌上二维码，系统显示点餐菜单。顾客选择餐饮种类以及数量，添加备注，点击结算、支付。

**扩展用例：**
 - 呼叫服务员：顾客在点餐界面有个呼叫服务员按钮，一按餐厅端的服务员便收到信息（桌号、时间）。
 - 催单：点餐后过了好久都没上菜，顾客可以在点餐界面点击催单按钮，餐厅端收到催单信息（桌号、时间）。

**选做用例：**
 - 多人点单：同一桌的多个顾客同时用手机扫描二维码，系统显示点餐菜单，顾客可以同时点餐，并将点餐数据统一到一份点餐信息上，发送到餐厅端。

 - 多人支付：支持AA支付法，每个顾客支付各自的部分。

   |     用例名称     | 生成每桌二维码                                  |
   | :----------: | :--------------------------------------- |
   |      范围      | web应用                                    |
   |      级别      | 用户目标                                     |
   |    主要参与者     | 餐厅管理员                                    |
   |   涉众及其关注点    | 餐厅管理员：希望能准确、简便地为每张桌子生成对应的二维码。            |
   |     前置条件     | 餐厅里有多张桌子，且每张桌子有自己的编号。                    |
   | 成功保证（或后置条件）  | 为每张桌子生成特定的二维码。                           |
   | 主成功场景（或基本流程） | 1. 餐厅管理员输入要生成的二维码的个数。<br>2. 系统生成并显示相应个数的二维码，每个二维码有对应的编号（从1开始）。<br>3. 餐厅管理员打印出所有的二维码，每个二维码旁有相应的编号标志。 |
   |  扩展（或替代流程）   | 3a. 某个二维码打印效果不好：<br>    1. 餐厅管理员可以选择重打某个特定的二维码。<br>3b. 缺乏打印纸或者打印机坏了：<br>    1. 给出错误提示。<br>    2.餐厅管理员可以将二维码作为图片保存下来，去别的地方打印，或者直接通过手机提供给顾客扫码。 |
   |     特殊需求     | 1. 计算机要连接打印机。<br>2. 二维码旁边对应的编号要显而易见。     |
   |   技术和数据元表    | 1a. 关于二维码的个数，餐厅管理员可以通过键盘输入。<br>2a. 每个生成二维码旁边有对应的编号。 |
   |     发生频率     | 偶尔会发生。                                   |
   |     未决问题     | 未实现定期更新二维码功能，可能存在顾客远程插队点餐的情况。            |


|     用例名称     | 查看账单                                     |
| :----------: | :--------------------------------------- |
|      范围      | web应用                                    |
|      级别      | 用户目标                                     |
|    主要参与者     | 餐厅管理员                                    |
|   涉众及其关注点    | 餐厅管理员：希望能准确地看到某一时间段内、或者某个顾客、或者某个订单号、或者订单收入在一定区间范围内、或者某个餐桌的详细账单信息。 |
|     前置条件     | 每次成功订单的信息（订单号、交易时间、顾客、菜色信息、餐桌号、收费信息）都能被准确录入系统。 |
| 成功保证（或后置条件）  | 准确、清晰地显示对应时间的账单信息。                       |
| 主成功场景（或基本流程） | 1. 餐厅管理员可以通过查询某一时间段（输入起始日期和结束日期），或者通过输入顾客账号名或订单号或餐桌号来查询符合条件的账单，点击确定查询。<br>2. 系统显示满足输入条件的账单信息：每个订单的信息（订单号、交易时间、顾客、餐桌号、菜色信息、收费信息）、总收入。<br>3. 餐厅管理员改变查询信息，点击查询。<br>4. 系统显示满足新输入的条件的账单信息。<br>5. 重复3-4步骤。 |
|  扩展（或替代流程）   | 1a、3a. 餐厅管理员没有输入任何限制条件：<br>    1. 显示所有历史账单信息。<br>2a、4a. 符合查询条件的账单信息过多。<br>    1. 分页显示。<br>2b、4b. 查不到符合查询条件的账单信息：<br>    1.弹出窗口提示没有符合查询条件的账单信息。 |
|     特殊需求     | 账单信息的显示要能适应各种屏幕大小，清晰地显示。                 |
|   技术和数据元表    | 1a. 餐厅管理员通过选择时间框选择起始日期和结束日期。<br>1b. 餐厅管理员通过键盘输入顾客账号名或者订单号或者餐桌号。<br>2a. 从数据库中得到相应的信息，并以表格的形式显示在餐厅管理员的用户界面上。 |
|     发生频率     | 可能会经常发生。                                 |
|     未决问题     | 1. 税率问题。<br>2. 故障恢复修改问题。                 |
