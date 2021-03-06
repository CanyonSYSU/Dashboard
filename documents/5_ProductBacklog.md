# 产品特性

| 版本 | 日期 | 描述 | 作者 |
| --- | --- | --- | --- |
| 初始草案V1.0 | 2018.3.29 | 第一草案，在细化阶段精化 | 何子龙 |

* **Imp** 产品负责人评出一个数值，指示这个故事有多重要。这里最高为10分。
* **Est** 团队的初步估算，表示与其他故事相比，完成该故事所需的工作量。最小的单位是故事点，一般大致相当于一个“理想的人天”。

## 扫码点餐系统BACKLOG 

| ID | Name | Imp | Est | How to demo | Notes |
| --- | --- | --- | --- | --- | --- |
| 0 | （客户）扫码 | 8 | 6 | 可通过扫描二维码进入点餐界面，同时确定就餐桌号 |  需要二维码相关技术 |
| 1 | （客户）选餐菜单 | 10 | 12 | 提供菜品分类，名称，价格，可以根据以上菜单内容作出初步选择 | 用户可根据需求初步选择具体菜品 |
| 2 | （客户）菜品详情 | 6 | 8 | 页面包括菜品的名称，价格，介绍，图片以及可能提供的吃客评价 | 用户可获取菜品的更详细介绍，以作出进一步选择 |
| 3 | （客户）点菜按钮 | 10 | 7 | 在选餐菜单与菜品详情界面均可进行点餐，点菜后记录到订单，并进行账单计算 | 会记录用户点餐选择，以通知厨房并进行账单计算 |
| 4 | （客户）订单查看 | 9 | 9 | 客户可观看已经点了的菜品 | 可在订单对菜品进行取消（如果没有付款），或者选择再点一份 |
| 5 | （客户）支付按钮 | 10 | 8 | 客户进行结账，支付 | 需要微信提供的支付api进行在线支付，或者可采取其他收款手段（需经商家确认收款） |
| 6 | （商家）添加食物 | 10 | 9 | 商家为菜单录入菜品信息，从而可以显示给客户看，供客户选择 | 需要将商家提供食物信息存入服务端 |
| 7 | （商家）修改或删除食物 | 8 | 9 | 可以根据实际情况修改或删除食物信息 | 动态修改，无需重新构造整个菜单 |
| 8 | （商家）接收订单 | 10 | 8 | 接收客户点餐信息，从而安排厨房工作 | 需要实现用户客户端与商家客户端的交互 |
| 9 | （商家）收款 | 10 | 6 | 商家根据点餐情况，折扣情况进行收款 | 需要微信提供的支付api进行在线收款，或者可采取其他收款手段（需经商家确认收款） |
| 10 | （商家）实时信息 | 7 | 8 | 商家可实时了解座位情况，点餐情况 | 客户催单时，等位时可以商家可以根据此信息作出回应 |
| 11 | （商家）统计 | 6 | 8 | 统计每日营业额，各菜品受欢迎程度 | 需记录一天的每次点餐情况，方便进行审计  |
| 12 | （客户）线上点餐 | 4 | 8 | 预约叫号点餐 | 客户可以选择外带或堂吃，堂吃看店铺情况座位情况给号 |
| 13 | （客户）点评 | 5 | 8 | 用户可评价每次的就餐体验，可为点的每个菜品附上评语 | 评语经商家选择显示在菜品详情中 |
| 14 | （客户）登录 | 3 | 10 | 可统计客户历史数据，为客户提供个性化点餐 | 在登录界面包含注册按钮，账户可与社交账号绑定或绑定邮箱，手机|
| 15 | （客户）我的主页 | 5 | 10 | 若登陆成功后，可查看历史点餐数据，可保存偏好点餐组合，可与商家联动根据就餐次数提供适当优惠；不登陆亦可选择餐馆 | 其实就是客户不通过扫码而也能进入该小程序的入口 |
| 16 | （客户）智能点餐 | 2 | 16 | 根据客户历史点餐数据以及可选择的额外输入的点餐偏好信息（如口味，人数）进行推荐 | 需要使用AI算法  |
