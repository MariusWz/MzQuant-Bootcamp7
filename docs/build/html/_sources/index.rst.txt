.. MzQuant-Bootcamp7 documentation master file, created by
   sphinx-quickstart on Mon Aug 18 15:23:43 2025.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

MzQuant-Bootcamp7 量化交易系统搭建实战教程
========================================

**7-Day Intensive Quant-Trading Sprint Plan** - 手把手教你从零开始搭建完整的量化交易系统。

本项目通过7天的密集学习，带你掌握量化交易系统的核心架构，从数据基础设施、策略开发、回测框架到风险管理的全流程实战。

学习目标
--------

- 掌握量化交易系统的基础架构设计
- 学习数据获取、清洗和存储的最佳实践
- 实践技术指标计算和策略信号生成
- 构建完整的回测框架和绩效评估系统
- 理解风险管理和仓位管理的核心概念

学习进度
--------

已完成模块
~~~~~~~~~~

**Day 1 - 数据基础设施搭建** ✅

- 搭建本地量化开发环境
- 构建数据管道：批量获取SPY前10大成分股6年日线数据
- 实现数据存储：Parquet格式 + 路径管理优化
- 完成探索性数据分析：分布分析 + 交互式K线图

**Day 2 - 策略原型开发** ✅

- 实现双均线策略（SMA20/50）+ 波动率过滤（ATR14 + z-score）
- 构建向量化回测框架，实现100%信号覆盖率
- 完成策略绩效评估：年化收益、夏普比率、最大回撤
- 代码函数化重构，支持pytest单元测试

待完成模块
~~~~~~~~~~

- **Day 3**: 策略框架优化与多策略集成
- **Day 4**: 风险管理与仓位管理系统
- **Day 5**: 策略参数优化与机器学习集成
- **Day 6**: 实盘模拟与性能监控系统
- **Day 7**: 系统部署与运维自动化

系统架构
--------

.. code-block:: text

   MzQuant-Bootcamp7/
   ├── bootcamp7/           # 核心系统代码
   ├── docs/               # 系统文档
   ├── notebooks/          # 学习与开发笔记本
   ├── data/               # 数据存储目录
   │   ├── raw/           # 原始数据
   │   └── backtest_results/ # 回测结果
   ├── README.md           # 系统说明文档
   └── readthedocs.yaml    # 文档部署配置

技术栈
------

**核心语言**: Python 3.13+

**数据处理**: Pandas, NumPy, PyArrow

**技术分析**: TA-Lib, Pandas-TA

**可视化**: Matplotlib, Plotly

**开发环境**: Jupyter Notebook, pytest

**文档构建**: Sphinx

学习内容
--------

.. toctree::
   :maxdepth: 2
   :caption: 每日学习记录:

   day1
   day2
   # day3
   # day4
   # day5
   # day6
   # day7

相关链接
--------

- `项目GitHub仓库 <https://github.com/MariusWz/MzQuant-Bootcamp7>`_
- `完整README文档 <../README.md>`_

