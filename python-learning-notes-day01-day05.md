# Python、AI Agent 与 Harness Engineering 学习笔记

# 第一部分：Python 基础学习

## Day 1：计算机基础与编程入门

### 1. 什么是计算机程序？

计算机本身不会主动理解我们的想法，需要我们通过程序告诉它应该做什么。

程序就是一组按照一定规则编写、可以由计算机执行的指令。

### 2. 什么是代码？

代码是我们使用编程语言编写的指令。

例如：

```python
print("Hello World")
```

这段代码告诉 Python 在屏幕上显示 Hello World。

### 3. 什么是算法？

算法就是解决某个问题的一系列步骤。

例如，计算股票涨跌幅：

1. 获取昨日收盘价。
2. 获取今日价格。
3. 用今日价格减去昨日价格。
4. 除以昨日价格。
5. 乘以 100，得到涨跌幅百分比。

公式：

涨跌幅 =（今日价格 - 昨日价格）/ 昨日价格 × 100%

### 4. 什么是 Python？

Python 是一种编程语言，可以用来开发软件、处理数据、自动化任务和构建 AI 应用。

未来我们的美股波段盯盘器也会使用 Python 开发。

### 5. 核心概念总结

| 概念 | 含义 |
|---|---|
| 计算机 | 执行指令的设备 |
| 程序 | 一组可以执行的指令 |
| 代码 | 使用编程语言写出的指令 |
| 算法 | 解决问题的一系列步骤 |
| 编程语言 | 人与计算机沟通、编写程序的工具 |
| Python | 一种常用的编程语言 |

---

## Day 2：Python 变量、数据类型与运算

### 1. 什么是变量？

变量可以理解为一个用来保存数据的名称。

例如：

```python
stock_price = 250
stock_name = "AAPL"
```

这里：

- `stock_price` 保存股票价格。
- `stock_name` 保存股票代码。

### 2. 常见数据类型

| 数据类型 | Python 写法 | 含义 | 股票项目示例 |
|---|---|---|---|
| 整数 | `int` | 没有小数的数字 | 股票数量 100 |
| 浮点数 | `float` | 带小数的数字 | 股票价格 250.5 |
| 字符串 | `str` | 文本 | 股票代码 "AAPL" |
| 布尔值 | `bool` | 真或假 | 是否满足上涨条件 |

示例：

```python
stock_name = "AAPL"
stock_price = 250.5
shares = 100
is_rising = True
```

### 3. 常见运算符

| 运算符 | 含义 | 示例 |
|---|---|---|
| `+` | 加法 | `10 + 5` |
| `-` | 减法 | `10 - 5` |
| `*` | 乘法 | `10 * 5` |
| `/` | 除法 | `10 / 5` |
| `>` | 大于 | `10 > 5` |
| `<` | 小于 | `10 < 5` |
| `==` | 等于 | `10 == 10` |
| `!=` | 不等于 | `10 != 5` |

### 4. input()：获取用户输入

`input()` 可以让程序接收用户输入的信息。

```python
stock_name = input("请输入股票代码：")

print(stock_name)
```

注意：`input()` 获取的内容默认是字符串。如果需要数字，通常要进行类型转换。

例如：

```python
price = float(input("请输入股票价格："))
```

### 5. 股票项目中的应用

```python
yesterday_price = 100
today_price = 105

change = (today_price - yesterday_price) / yesterday_price * 100

print("涨跌幅：", change, "%")
```

运行结果：

```text
涨跌幅：5.0 %
```

### 6. 核心概念总结

| 概念 | 含义 |
|---|---|
| 变量 | 保存数据 |
| 数据类型 | 决定数据的类别 |
| 运算符 | 对数据进行计算或比较 |
| input() | 接收用户输入 |
| print() | 显示内容 |
| 类型转换 | 将数据转换成另一种类型 |

---

## Day 3：条件判断与程序逻辑

### 1. 什么是条件判断？

条件判断就是让程序根据某个条件，决定下一步应该执行什么操作。

例如：

如果股票涨幅超过 5%，就显示上涨提醒。

### 2. if 语句

```python
change = 5.5

if change > 5:
    print("股票涨幅超过5%，需要关注")
```

这里：

- `if` 表示如果。
- `change > 5` 是判断条件。
- 条件成立时，执行下面缩进的代码。

### 3. if 和 else

如果条件不成立，就可以执行另一段代码。

```python
change = 3

if change > 5:
    print("涨幅较大")
else:
    print("涨幅未超过5%")
```

### 4. if、elif 和 else

当需要判断多种情况时，可以使用 `elif`。

```python
change = 6

if change > 5:
    print("明显上涨")

elif change > 0:
    print("小幅上涨")

elif change == 0:
    print("价格没有变化")

else:
    print("股票下跌")
```

### 5. 逻辑判断

| 运算符 | 含义 |
|---|---|
| `and` | 并且，两个条件都成立 |
| `or` | 或者，至少一个条件成立 |
| `not` | 取反 |

例如：

```python
price = 105
moving_average = 100

if price > moving_average and price > 100:
    print("满足上涨观察条件")
```

这里要求两个条件同时成立。

### 6. 股票项目中的应用

未来我们可以用条件判断编写简单的趋势规则：

- 价格高于某条均线。
- 均线向上。
- 最近的波段高点逐步抬高。
- 最近的波段低点逐步抬高。

满足多个条件时，可以把股票标记为上涨趋势候选。

注意：这些只是规则示例，不能单独作为真实交易结论。

### 7. 核心概念总结

| 概念 | 含义 |
|---|---|
| `if` | 如果条件成立 |
| `elif` | 如果前面的条件不成立，再判断其他条件 |
| `else` | 以上条件都不成立时执行 |
| `and` | 多个条件必须同时成立 |
| `or` | 多个条件至少一个成立 |
| `not` | 对条件结果取反 |
| 缩进 | 表示代码属于哪个代码块 |

---

## Day 4：函数、模块、包与项目结构

### 1. 什么是函数？

函数就是把一项具体任务封装成一个可以重复调用的代码单元。

例如：

```python
def calculate_change(yesterday, today):
    change = (today - yesterday) / yesterday * 100
    return change

result = calculate_change(100, 105)

print(result)
```

输出：

```text
5.0
```

### 2. 函数的组成

| 知识点 | 含义 | 作用 |
|---|---|---|
| `def` | 定义函数的关键字 | 创建函数 |
| 函数名 | 函数的名称 | 用来调用函数 |
| 参数 | 函数的输入 | 接收外部数据 |
| `return` | 返回结果 | 把结果交给调用者 |
| 函数调用 | 使用函数 | 让函数真正执行 |
| `print()` | 打印内容 | 在屏幕上显示信息 |

### 3. 参数和返回值

参数和返回值是两个重要概念。

| 对比 | 参数 | 返回值 |
|---|---|---|
| 作用 | 输入信息 | 输出结果 |
| 方向 | 外部传入函数 | 函数返回给外部 |
| 是否必须 | 不一定需要 | 不一定需要 |
| 股票例子 | 昨日价格、今日价格 | 涨跌幅 |

记忆：

参数负责输入，返回值负责输出。

### 4. print() 和 return 的区别

- `print()`：把信息显示出来。
- `return`：把计算结果交给调用者，方便其他代码继续使用。

### 5. 什么是模块（Module）？

模块通常就是一个 Python 文件，以 `.py` 结尾。

一个模块可以包含函数、变量和类等内容。

例如：

market_data.py：

```python
def get_stock_data():
    print("正在获取 AAPL 股票行情")
```

main.py：

```python
import market_data

market_data.get_stock_data()
```

这里：

- `market_data.py` 是模块。
- `get_stock_data()` 是函数。
- `import market_data` 是导入模块。
- `market_data.get_stock_data()` 是调用模块中的函数。

### 6. 什么是包（Package）？

包是用来组织多个模块的目录。

例如：

```text
strategy/
    __init__.py
    trend.py
    pattern.py
```

其中：

- `strategy/` 是包。
- `trend.py` 是模块。
- `pattern.py` 是模块。
- `__init__.py` 通常用于包的初始化和结构组织，但现代 Python 并非所有包都必须有它。

导入示例：

```python
from strategy.trend import identify_trend
```

### 7. 什么是项目结构？

项目结构就是按照不同职责组织项目中的文件和目录。

我们的美股波段盯盘器可以采用这样的初步结构：

```text
stock-agent/
│
├── main.py
│
├── market_data/
│   ├── __init__.py
│   ├── stock.py
│   └── daily.py
│
├── strategy/
│   ├── __init__.py
│   ├── trend.py
│   └── pattern.py
│
├── agent/
│   ├── __init__.py
│   └── assistant.py
│
├── harness/
│   └── runner.py
│
├── tests/
│
└── logs/
```

各部分职责：

| 文件或目录 | 主要职责 |
|---|---|
| main.py | 程序入口和协调 |
| market_data/ | 获取行情数据 |
| strategy/ | 趋势、形态和策略规则 |
| agent/ | AI Agent 相关功能 |
| harness/ | 管理 Agent 的执行流程 |
| tests/ | 测试程序 |
| logs/ | 记录运行日志 |

### 8. main.py 的作用

`main.py` 通常负责组织和协调不同模块，让整个程序按照指定流程运行。

例如：

```python
def get_stock_data():
    print("获取股票数据")

def analyze_stock():
    print("分析股票趋势")

def send_alert():
    print("发送股票提醒")

def main():
    get_stock_data()
    analyze_stock()
    send_alert()

main()
```

执行顺序：

1. 获取股票数据。
2. 分析股票趋势。
3. 发送股票提醒。

注意：`main.py` 不是 Python 强制要求的特殊文件，只是一种常见的项目组织方式。

### 9. Python 程序执行流程

| 知识点 | 规则 |
|---|---|
| 顺序执行 | 通常从上往下执行 |
| 定义函数 | 创建函数，不会立即执行函数体 |
| 调用函数 | 真正执行函数体 |
| 参数传递 | 把数据传入函数 |
| 返回结果 | 把结果交给调用者 |
| 模块导入 | 使用其他文件中的代码 |
| main() | 组织和协调各部分执行 |

示例：

```python
def A():
    print("苹果")

def B():
    print("微软")

def main():
    B()
    A()

main()
```

输出：

```text
微软
苹果
```

核心理解：

函数定义的先后顺序，不一定决定函数执行的先后顺序；真正的执行顺序取决于函数调用关系。

---

# 第二部分：Python 程序健壮性

## Day 5：异常处理（Exception Handling）

### 1. 什么是异常？

异常是程序运行过程中发生的一类问题。

例如：

- 股票价格为 0，计算涨跌幅时发生除以零异常。
- 网络中断，行情接口连接失败。
- 股票价格数据格式不正确。
- 返回的数据缺少需要的字段。

异常处理的目的：让程序能够发现、记录并合理处理问题，而不是遇到问题就直接停止运行。

### 2. try 和 except

- `try`：尝试执行可能发生异常的代码。
- `except`：发生指定异常时，执行对应的处理代码。

示例：

```python
price = 100
yesterday_price = 0

try:
    change = (price - yesterday_price) / yesterday_price
    print(change)

except ZeroDivisionError:
    print("无法计算涨跌幅：昨日价格不能为零")
```

### 3. 股票项目中的异常处理

模拟行情接口连接失败：

```python
def get_stock_price():
    raise ConnectionError("行情接口连接失败")

try:
    price = get_stock_price()
    print("苹果当前价格：", price)

except ConnectionError:
    print("无法获取苹果股票价格，请稍后重试")
```

`raise` 的作用是主动抛出异常。

### 4. 常见异常类型

| 异常 | 可能发生的情况 |
|---|---|
| ZeroDivisionError | 除以零 |
| ConnectionError | 网络或接口连接失败 |
| ValueError | 数据无法转换成预期的数字 |
| KeyError | 数据中缺少需要的字段 |

可以针对不同异常设置不同的处理方式：

```python
try:
    price = float("abc")

except ValueError:
    print("股票价格数据格式错误")

except ZeroDivisionError:
    print("股票价格不能为零")

except ConnectionError:
    print("行情接口连接失败")
```

### 5. else 和 finally

- `else`：try 中没有发生异常时执行。
- `finally`：无论是否发生异常，最后都会执行。

```python
try:
    price = float("250")

except ValueError:
    print("股票价格格式错误")

else:
    print("股票价格获取成功：", price)

finally:
    print("本次行情检查结束")
```

### 6. 异常处理的完整知识表

| 关键字 | 作用 |
|---|---|
| try | 尝试执行代码 |
| except | 捕获并处理异常 |
| raise | 主动抛出异常 |
| else | 没有异常时执行 |
| finally | 最后执行收尾工作 |
| as error | 获取异常对象，查看错误信息 |

### 7. 工程实践中的重要原则

不要随意忽略异常。

例如：

```python
try:
    price = get_stock_price()

except Exception:
    pass
```

这种做法可能隐藏错误，让我们不知道行情获取已经失败。

更合理的方式是记录错误、判断是否可以重试，并避免错误数据进入后续分析。

对于未来的美股波段盯盘器，异常处理可以帮助我们应对网络中断、行情缺失和数据格式错误等问题。

### 8. 今天学到了什么？

1. 理解异常和异常处理。
2. 学会使用 try 和 except。
3. 认识 raise 和常见异常类型。
4. 理解 else 和 finally。
5. 理解为什么不能随意忽略错误。

**本日核心：程序健壮不是没有错误，而是发生错误时能够发现、记录并合理处理。**

---

# 第三部分：我们的长期实战项目

## 美股波段盯盘器

我们的学习最终会落到一个实际项目上：开发一个能够监控自选美股、识别上涨趋势并发出提醒的工具。

### 项目目标

- 交易周期：1–4 周波段。
- 监控范围：个人自选股。
- 检查频率：美股交易时段每小时。
- 第一版只分析和提醒，不自动下单。

### 计划实现的功能

1. 获取股票行情数据。
2. 计算技术指标和识别市场结构。
3. 判断上涨、震荡和下跌趋势。
4. 识别趋势形态及趋势转换。
5. 每小时扫描自选股并发送提醒。
6. 引入 AI Agent，辅助解释分析结果。
7. 使用历史数据进行回测和评估。
8. 使用 Harness Engineering 提高程序长期运行的可靠性。

### 当前的学习路线

Python 基础
→ 函数和模块
→ 程序结构
→ 异常处理
→ 循环和数据处理
→ API 和行情获取
→ 技术指标与策略规则
→ AI Agent
→ Harness Engineering
→ 完整项目。

**学习原则：先理解，再动手；先做出能运行的基础程序，再逐步增加复杂功能。**
