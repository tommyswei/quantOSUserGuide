# quantOS数据规范

作者：PKUJohnson, symbol, vanvency

为了让quantOS各系统和谐工作，我们制定了必不可少的数据规范。在深入到系统细节之前，本章给您介绍以下在quantOS上使用的数据规范。

## 数据字典规范

## 市场代码（marketcode）

| 市场名称 | 市场代码 |
| :--- | :--- |
| 深交所 | SZ |
| 上交所 | SH |
| 中金所 | CFE |
| 郑商所 | CZC |
| 大商所 | DCE |
| 上期所 | SHF |
| 上金所 | SGE |
| 中证指数 | CSI |
| 港交所 | HK |

### 标的代码（symbol）

symbol由标的原始代码加市场代码组合而成，中间以'.'隔开，如'000001.SH'。

多标的输入时以逗号 \(','\) 隔开如：'000001.SH, cu1709.SHF'

### Bar类型（freq）

| Bar类型 | 说明 |
| :--- | :--- |
| 15S | 15秒线 |
| 30S | 30秒线 |
| 1M | 1分钟线 |
| 5M | 5分钟线 |
| 15M | 15分钟线 |
| 1d | 日线 |
| 1w | 周线 |
| 1m | 月线 |

### 证券类型定义 \(insttype\)

| 证券类型 | inst\_type |
| :--- | :--- |
| 股票 | 1 |
| 封闭式基金 | 2 |
| LOF基金 | 3 |
| ETF基金 | 4 |
| 分级基金 | 5 |
| 国债商品 | 6 |
| 商品 | 7 |
| 可转债 | 8 |
| 回购 | 10 |
| 国债 | 11 |
| 地方政府债 | 12 |
| 金融债 | 13 |
| 企业债 | 14 |
| 公司债 | 15 |
| 资产支持证券 | 16 |
| 可交换债 | 17 |
| 可分离转债存债 | 18 |
| 政府支持机构债 | 19 |
| 转股换股 | 20 |
| 指数 | 100 |
| 股指期货 | 101 |
| 国债期货 | 102 |
| 商品期货 | 103 |
| 股指ETF期权 | 201 |
| 股指期货期权 | 202 |
| 商品期货期权 | 203 |

### 交易行为（action）

| 交易行为 | 含义 |
| :--- | :--- |
| Buy | 买入（多头开仓） |
| Sell | 卖出（多头平仓） |
| Short | 空头开仓 |
| Cover | 空头平仓 |
| CoverYesterday | 空头平昨仓 |
| CoverToday | 空头平今仓 |
| SellYesterday | 多头平昨仓 |
| SellToday | 多头平今仓 |

### 订单状态（order\_status）

| 订单状态 | 含义 |
| :--- | :--- |
| New | 订单生成 |
| Accepted | 订单已被接受 |
| Rejected | 订单已被拒绝 |
| Filled | 订单已完全成交 |
| Cancelled | 订单已取消（可能有部分成交） |

## 基础数据规范

重要基础数据我们进行了统一的规范，主要包括：

### 证券信息（instrument）

| instcode | jzcode | market | buylot | pricetick | multiplier | insttype | symbol |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 000300 | 4 | 2 | 100 | 0.01 | 1 | 100 | 000300.SH |
| 000905 | 5 | 2 | 100 | 0.01 | 1 | 100 | 000905.SH |
| 000016 | 6 | 2 | 100 | 0.01 | 1 | 100 | 000016.SH |

其中的jzcode由我们统一编码，其他字段包括最小交易单位，最小价格，合约乘数，证券类型等。

### 交易日历（calendar）

| date |
| :--- |
| 20041022 |
| 20041025 |
| 20041026 |
| 20041027 |

calendar只列出了所有的A股交易日。

### 市场信息（market）

| market | marketcode | auctbeg1 | auctend1 | auctbeg2 | auctend2 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | SZ | 930 | 1130 | 1300 | 1500 |
| 2 | SH | 930 | 1130 | 1300 | 1500 |
| 3 | CFE | 915 | 1130 | 1300 | 1515 |
| 4 | CZC | 900 | 1015 | 1030 | 1130 |

市场信息中，最重要的是市场代码\(marketcode\)，还有该市场的交易时间段定义。

**基础数据是其他项目的依赖，请从**[**http://www.quantos.org/downloads/basedata/**](http://www.quantos.org/downloads/basedata/)**下载最新的基础数据。**

