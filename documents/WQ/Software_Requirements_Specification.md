# 随心点餐宝软件需求文档
## 1. 引言

### 1.1 目的

编写此文档的目的是进一步定制软件开发的细节问题,希望能使本软件开发工作更具体。是为使用户、软件开发者及分析人员对该软件的初始规定有一个共同的理解，它说明了本产品的各项功能需求、性能需求和数据要求，明确标识各功能的实现过程，阐述实用背景及范围，提供客户解决问题或达到目标所需的条件或权能，提供一个度量和遵循的基准

### 1.2 项目背景
目前国内市场上的餐馆点餐系统还处于发展初期，目前还只有少量的餐馆使用点餐系统，有巨大的市场空间。消费者对于尝试和使用点餐系统有很大的兴趣，点餐小程序使消费者点餐和支付更加方便，提前查看餐馆空位和预约点餐可以很大程度的方便消费者，优惠卷和相关优惠活动可以大幅度提高客户粘性，长远来看这有很大的商业机遇。而现有的点餐系统绝大部分为店内点餐系统，并且不支持支付，评论等功能，这对于点餐的优化很有限，小程序的实现方式可以使消费者更加方便的安装使用，也提供了远程预约，查看空位，评论，查看菜品详情，支付等功能的实现，而优惠卷，优惠信息的推送可以店家更方便等开展活动并使活动可以推送给目标客户群体。

### 1.3 软件定位
这是一款基于微信小程序的点餐系统，提供点餐，支付，查看菜品详情，评论等功能，极大地方便客户点餐和支付，减少餐馆的工作负担，此外提供提前查看餐馆空位和预约点餐，优惠卷和相关优惠活动，可以很大程度的方便消费者和商家。

### 1.4 参考资料
[1]潘茂林 《系统设计分析与设计课程内容》
[2]go web指南 https://github.com/astaxie/build-web-application-with-golang/blob/master/zh/preface.md

## 2. 任务概述

### 2.1 目标

项目需求细化。

对于顾客端：

实现餐馆菜单界面: 实现所有菜品分类与列表显示，单个菜品概要介绍与选择按钮，以及购物车按钮，支付按钮，评价按钮与商家按钮。

实现菜品详细介绍页面: 通过点击菜品概要介绍部分，可弹出菜品详细介绍页面，可从页面中获取菜品大图，详细介绍等信息。

实现购物车页面: 通过点击购物车按钮，可进入购物车页面管理购物车，查看，增加或减少已点菜品。

实现订单支付页面: 点击去结账按钮，会跳转到订单详情页面，可检查后确定结账并支付。

实现顾客评价页面：通过点击餐馆菜单首页的评价按钮，可进入评价页面查看评价以及进行评价。

实现商家按钮：通过点击商家按钮，可查看商家的商家地址、联系电话、食品安全档案（许可证、营业执照）、营业时间、本店优惠活动等信息。

对于商家端：

实现登录，注册，修改商家个人信息等功能。

登录后主界面实现数据查看与数据增删选项。

点击数据查看选项，可查看食品列表与订单列表，可从订单列表获得实时订单信息与历史订单信息，方便店家进行管理。

点击数据增删选项，店家可编辑增删菜品，根据实际情况编写餐馆菜单。


### 2.2 运行环境

 软件平台：

 顾客端；安装了微信的ios或Android系统；

 系统后台：配置好go、mysql的Ubuntu系统。

### 2.3 条件和限制

 环境约束：运行该软件需在Linux系统下配置安装环境.

 技术约束：实现功能并不完善.

## 3. 功能需求

### 3.1 Use Case 图
顾客端用例图：

![顾客端usecase图](https://github.com/QAZASDEDC/photo/raw/master/customer_usecase.png)

商家端用例图：

![商家端usecase图](https://github.com/QAZASDEDC/photo/raw/master/seller_usecase.png)

### 3.2 功能模型

#### 顾客端用例主场景：顾客点菜下单支付
![function_model](https://github.com/QAZASDEDC/photo/raw/master/customer_sequence.png)

##### 子用例：点菜
![addFood](https://github.com/QAZASDEDC/photo/raw/master/OrderFood_sequence1.png)

##### 子用例：下单
![submitOrder](https://github.com/QAZASDEDC/photo/raw/master/SubmitOrder_sequence.png)

##### 子用例： 支付
![pay](https://github.com/QAZASDEDC/photo/raw/master/ManageOrder_sequence.png)

#### 商家端用例主场景一：商家注册
![register](https://github.com/QAZASDEDC/photo/raw/master/registerS.png)

#### 商家端用例主场景二：商家登录
![login](https://github.com/QAZASDEDC/photo/raw/master/loginS.png)

#### 商家端用例主场景三：商家查看订单
![orders](https://github.com/QAZASDEDC/photo/raw/master/orderS.png)

#### 商家端用例主场景四：商家查看菜品列表
![dishs](https://github.com/QAZASDEDC/photo/raw/master/dishS.png)

#### 商家端用例主场景五：商家增加菜品
![addfoods](https://github.com/QAZASDEDC/photo/raw/master/addFoodS.png)

#### 商家端用例主场景六：商家删减菜品
![reducefoods](https://github.com/QAZASDEDC/photo/raw/master/reduceFoodS.png)

### 3.3 状态模型

#### 订单状态模型
![order_state](https://github.com/QAZASDEDC/photo/raw/master/6.4_State_Model.png)

## 4. 数据描述

### 4.1 静态数据
餐馆信息表
```
CREATE TABLE IF NOT EXISTS `canyonsysu`.`restaurant` (
  `id` INT NOT NULL AUTO_INCREMENT,
  `name` VARCHAR(45) NOT NULL,
  `address` VARCHAR(45) NOT NULL,
  PRIMARY KEY (`id`))
ENGINE = InnoDB;
```

订单信息表
```
CREATE TABLE IF NOT EXISTS `canyonsysu`.`order` (
  `id` INT NOT NULL AUTO_INCREMENT,
  `orderin` DATE NOT NULL COMMENT '点菜时间',
  `orderout` DATE NOT NULL COMMENT '上菜时间',
  `restaurant_id` INT NOT NULL,
  PRIMARY KEY (`id`, `restaurant_id`),
  INDEX `fk_order_restaurant1_idx` (`restaurant_id` ASC),
  CONSTRAINT `fk_order_restaurant1`
    FOREIGN KEY (`restaurant_id`)
    REFERENCES `canyonsysu`.`restaurant` (`id`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB;

```
顾客信息表
```
CREATE TABLE IF NOT EXISTS `canyonsysu`.`customer` (
  `id` INT NOT NULL AUTO_INCREMENT,
  `name` VARCHAR(45) NOT NULL,
  `phone` VARCHAR(45) NOT NULL,
  `order_id` INT NOT NULL,
  `order_restaurant_id` INT NOT NULL,
  PRIMARY KEY (`id`, `order_id`, `order_restaurant_id`),
  INDEX `fk_customer_order1_idx` (`order_id` ASC, `order_restaurant_id` ASC),
  CONSTRAINT `fk_customer_order1`
    FOREIGN KEY (`order_id` , `order_restaurant_id`)
    REFERENCES `canyonsysu`.`order` (`id` , `restaurant_id`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB;
```
菜单信息表
```
CREATE TABLE IF NOT EXISTS `canyonsysu`.`menu` (
  `id` INT NOT NULL AUTO_INCREMENT,
  `restaurant_id` INT NOT NULL,
  PRIMARY KEY (`id`, `restaurant_id`),
  INDEX `fk_menu_restaurant_idx` (`restaurant_id` ASC),
  CONSTRAINT `fk_menu_restaurant`
    FOREIGN KEY (`restaurant_id`)
    REFERENCES `canyonsysu`.`restaurant` (`id`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB;
```
支付信息表
```
CREATE TABLE IF NOT EXISTS `canyonsysu`.`payment` (
  `id` INT NOT NULL AUTO_INCREMENT,
  `payment_way` VARCHAR(45) NOT NULL COMMENT 'wechat or cash',
  `order_id` INT NOT NULL,
  `order_restaurant_id` INT NOT NULL,
  PRIMARY KEY (`id`, `order_id`, `order_restaurant_id`),
  INDEX `fk_payment_order1_idx` (`order_id` ASC, `order_restaurant_id` ASC),
  CONSTRAINT `fk_payment_order1`
    FOREIGN KEY (`order_id` , `order_restaurant_id`)
    REFERENCES `canyonsysu`.`order` (`id` , `restaurant_id`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB;
```
菜单菜品信息表
```
CREATE TABLE IF NOT EXISTS `canyonsysu`.`menu_food` (
  `id` INT NOT NULL AUTO_INCREMENT,
  `type` VARCHAR(45) NOT NULL,
  `price` REAL NOT NULL,
  `menu_id` INT NOT NULL,
  `menu_restaurant_id` INT NOT NULL,
  PRIMARY KEY (`id`, `menu_id`, `menu_restaurant_id`),
  INDEX `fk_menu_food_menu1_idx` (`menu_id` ASC, `menu_restaurant_id` ASC),
  CONSTRAINT `fk_menu_food_menu1`
    FOREIGN KEY (`menu_id` , `menu_restaurant_id`)
    REFERENCES `canyonsysu`.`menu` (`id` , `restaurant_id`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB;
```
订单菜品信息表
```
CREATE TABLE IF NOT EXISTS `canyonsysu`.`order_food` (
  `id` INT NOT NULL AUTO_INCREMENT,
  `type` VARCHAR(45) NOT NULL,
  `number` INT NOT NULL DEFAULT 1,
  `prices` REAL NOT NULL COMMENT 'prices = number*menu_food.price',
  `order_id` INT NOT NULL,
  `order_restaurant_id` INT NOT NULL,
  PRIMARY KEY (`id`, `order_id`, `order_restaurant_id`),
  INDEX `fk_order_food_order1_idx` (`order_id` ASC, `order_restaurant_id` ASC),
  CONSTRAINT `fk_order_food_order1`
    FOREIGN KEY (`order_id` , `order_restaurant_id`)
    REFERENCES `canyonsysu`.`order` (`id` , `restaurant_id`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB;
```

### 4.2 数据库领域模型

#### 领域模型
![domain](https://github.com/QAZASDEDC/photo/raw/master/Domian_Model.png)

#### 数据库设计
![database](https://github.com/QAZASDEDC/photo/raw/master/sql.png)

## 5. 性能及运行需求

### 5.1 时间特性
一般操作的响应时间应在1－2秒内。

### 5.2 适应性
满足运行环境在允许操作系统之间的安全转换和与其它应用软件的独立运行要求。

### 6.1 用户界面
商家端采用网页显示方式。

顾客端使用微信小程序页面显示方式。

### 6.4 故障处理
正常使用时不应出错，对于用户的输入错误应给出适当的改正提示。若运行时遇到不可 恢复的系统错误，也必须保证数据库完好无损。