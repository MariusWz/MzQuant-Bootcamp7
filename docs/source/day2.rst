Day 2 - 策略原型开发
====================

概述
----

Day2是量化交易系统搭建的关键一步，主要目标是开发第一个可运行的交易策略原型，包括技术指标计算、策略逻辑实现、回测框架构建和绩效评估系统。

完成状态: ✅ 已完成

核心成就
--------

- ✅ 实现双均线策略（SMA20/50）+ 波动率过滤（ATR14 + z-score）
- ✅ 构建向量化回测框架，实现100%信号覆盖率
- ✅ 完成策略绩效评估：年化收益、夏普比率、最大回撤
- ✅ 代码函数化重构，支持pytest单元测试

技术架构详解
------------

技术指标层
~~~~~~~~~

**1.1 SMA双均线系统**

使用Pandas-TA库计算20日和50日简单移动平均线：

.. code-block:: python

   df['SMA_20'] = SMAIndicator(close=df.Close, window=20).sma_indicator()
   df['SMA_50'] = SMAIndicator(close=df.Close, window=50).sma_indicator()

**1.2 ATR波动率指标**

计算14日平均真实波幅，衡量市场波动率：

.. code-block:: python

   df['ATR_14'] = AverageTrueRange(
       high=df.High,
       low=df.Low,
       close=df.Close,
       window=14
   ).average_true_range()

**1.3 波动率过滤z-score**

用ATR的252日滚动均值与标准差计算z-score，识别异常波动时期：

.. code-block:: python

   df['zscore'] = (df['ATR_14'] - df['ATR_14'].rolling(252).mean()) / df['ATR_14'].rolling(252).std()

策略逻辑层
~~~~~~~~~

**2.1 双均线交叉信号**

当SMA20 > SMA50时产生买入信号，否则为空仓：

.. code-block:: python

   df['Signal'] = np.where(df['SMA_20'] > df['SMA_50'], 1, 0)

**2.2 波动率过滤**

当ATR z-score < 1（即波动率较低）时才允许开仓：

.. code-block:: python

   df['Vol_filter'] = df['zscore'] < 1

持仓矩阵层
~~~~~~~~~

**3.1 滞后处理**

持仓信号需要滞后1天，避免"未来函数"：

.. code-block:: python

   df['Position'] = (
       (df['Signal'].astype(bool) & df['Vol_filter'])
       .shift(1)
       .astype('boolean')   
       .ffill()
       .fillna(False)
       .astype(int) 
   )

回测框架层
~~~~~~~~~

**4.1 收益率计算**

标的每日收益率和策略收益：

.. code-block:: python

   df['Return'] = df['Close'].pct_change()
   df['Strategy_Return'] = df['Position'] * df['Return']

**4.2 净值曲线**

用累计乘积计算策略净值曲线：

.. code-block:: python

   df['Equity_Curve'] = (1 + df['Strategy_Return']).cumprod()

绩效评估系统
-----------

核心指标计算
~~~~~~~~~~~

**年化复合收益率 (CAGR)**

.. math::

   CAGR = \left(\frac{Equity_{end}}{Equity_{start}}\right)^{\frac{252}{n}} - 1

**夏普比率 (Sharpe Ratio)**

.. math::

   Sharpe = \frac{E[daily\_return]}{Std[daily\_return]} \times \sqrt{252}

**最大回撤 (Max Drawdown)**

基于equity_curve的滚动高点计算：

.. code-block:: python

   roll_max = er.cummax()
   dd = er / roll_max - 1
   mdd = dd.min()

评估结果示例
~~~~~~~~~~~

以AAPL为例的策略绩效：

- **CAGR**: 1.73%
- **年化收益率**: 2.76%
- **年化波动率**: 14.45%
- **夏普比率**: 0.19
- **最大回撤**: -32.21%
- **信号覆盖率**: 100.00%

代码架构设计
-----------

函数化设计
~~~~~~~~~

1. **calculate_indicators(df)**: 技术指标计算
2. **strategy_logic(df)**: 策略逻辑实现
3. **position_matrix(df)**: 持仓矩阵生成
4. **calculate_returns(df)**: 收益率计算
5. **evaluate_strategy(df)**: 策略评估

数据存储优化
~~~~~~~~~~~

- 使用Parquet格式存储回测结果
- 自动创建数据目录结构
- 支持跨平台路径管理

测试框架
~~~~~~~~~

- 支持pytest单元测试
- 函数接口标准化
- 错误处理机制完善

学习成果
--------

通过Day2的学习和实践，掌握了：

1. **技术指标计算技术**
   - Pandas-TA库的使用
   - 向量化计算的优势
   - 滚动窗口操作

2. **策略开发流程**
   - 信号生成逻辑
   - 波动率过滤机制
   - 持仓管理策略

3. **回测系统构建**
   - 向量化回测框架
   - 收益率计算方法
   - 绩效指标计算

4. **代码工程实践**
   - 函数化重构
   - 模块化设计
   - 测试驱动开发

下一步计划
----------

Day3将重点学习：

- 策略框架优化
- 多策略集成
- 参数优化方法
- 风险管理框架

相关资源
--------

- `Day2 Jupyter Notebook <../notebooks/day2.ipynb>`_
- `项目GitHub仓库 <https://github.com/MariusWz/MzQuant-Bootcamp7>`_
- `完整README文档 <../README.md>`_
