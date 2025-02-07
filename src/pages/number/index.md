# 前端精度数值计算规范

## 规则①：

前后端传递数值使用 string，尤其金额必须 string

前端能够接收的最大安全整数 Number.MAX_SAFE_INTEGER === 9007199254740991

## 规则②：

精度计算库的选择：从前到后，包的大小依次增加

### [big.js](https://github.com/MikeMcl/big.js)(首选)：最小最轻的库 6kb

- 支持十进制
- toExponential（科学计数法）, toFixed（定点计数法） 和 toPrecision（有效位数）

```javascript
Big.strict = true // 必须开启，禁止传入 number 类型的值
Big.DP = 7 // 设置小数位数
Big.RM = 4 // 四舍五入边界
const x = new Big('5')
x.div(3).toString() // '1.6666667'
```

### [bignumber.js](https://github.com/MikeMcl/bignumber.js)：

在 big.js 的基础上

- 支持二进制、六进制、八进制
- 精度是以小数位数决定，所有的计算都是四舍五入到这个精度再进行计算
- 更适用于极其精确的计算，用户不需担心失去精度
- bignumber.js 会尝试完全精确地执行操作，这可能会使操作所花费的时间变得漫长

### [decimal.js](https://github.com/MikeMcl/decimal.js)：

在 bignumber.js 的基础上

- 精度是以有效位数决定，所有的计算都是四舍五入到这个精度再进行计算
- 增加了非整数幂，并添加了三角函数、 exp、 ln 和 log 方法

#### bignumber.js 与 decimal.js 的计算精确度差异：

```javascript
Bignumber.config({ DECIMAL_PLACES: 3, ROUNDING_MODE: 1 })
const x = new BigNumber('123.456789')
x.plus(1).toString() // '124.456789'

Decimal.set({ precision: 7, rounding: 4 })
const y = new Decimal('123.456789')
y.plus(1).toString() // '124.4568'
```

## 参考：

- https://github.com/MikeMcl/big.js/wiki
- 20230605-前端技术方案-前端计算使用优惠券后订单金额
