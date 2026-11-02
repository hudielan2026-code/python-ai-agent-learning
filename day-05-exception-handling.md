# Day 5：Python 异常处理（Exception Handling）

## 一、什么是异常？

异常是程序运行过程中发生的一类问题。

例如：
- 股票价格为 0，计算涨跌幅时发生除以零异常。
- 网络中断，行情接口连接失败。
- 股票价格数据格式不正确。
- 返回的数据缺少需要的字段。

异常处理的目的：让程序能够发现、记录并合理处理问题，而不是遇到问题就直接停止运行。

## 二、try 和 except

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

## 三、股票项目中的异常处理

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

## 四、常见异常类型

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

## 五、else 和 finally

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

## 六、异常处理的完整知识表

| 关键字 | 作用 |
|---|---|
| try | 尝试执行代码 |
| except | 捕获并处理异常 |
| raise | 主动抛出异常 |
| else | 没有异常时执行 |
| finally | 最后执行收尾工作 |
| as error | 获取异常对象，查看错误信息 |

## 七、工程实践中的重要原则

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

## 八、今天学到了什么？

1. 理解异常和异常处理。
2. 学会使用 try 和 except。
3. 认识 raise 和常见异常类型。
4. 理解 else 和 finally。
5. 理解为什么不能随意忽略错误。

**本日核心：程序健壮不是没有错误，而是发生错误时能够发现、记录并合理处理。**
