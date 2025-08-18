# MzQuant-Bootcamp7

## 📚 项目简介

**7-Day Intensive Quant-Trading Sprint Plan** - 一个为期7天的量化交易强化训练营项目。

本项目旨在通过7天的密集学习，掌握量化交易的核心技能，从数据获取、分析到策略回测的完整流程。

## 🎯 项目目标

- 掌握量化交易基础框架
- 学习数据获取和处理技术
- 实践技术分析和策略开发
- 完成完整的量化交易项目

## 📅 学习进度

### Day 1 - 框架 & 数据 ✅ 已完成

#### 🎯 里程碑
- [x] 本地环境可用
- [x] 一次性拉取 10 只股票最近 6 年日线
- [x] 完成一次快速 EDA（分布 + 交互式 K 线）
- [x] README 记录并推送 GitHub

#### 📊 主要任务完成情况
1. **环境搭建** ✅
   - 本地开发环境配置完成
   - 依赖包安装和配置

2. **数据获取** ✅
   - 成功获取SPY前10大成分股数据
   - 包含最近6年的日线数据
   - 数据质量验证通过

3. **数据分析** ✅
   - 完成快速EDA（探索性数据分析）
   - 日收益率计算与可视化（Pairplot）
   - 交互式K线图（Candlestick）展示

4. **文档记录** ✅
   - 完成README文档编写
   - 代码注释和说明完善
   - 项目结构清晰化

### Day 2-7 - 待完成
- [ ] Day 2: 技术指标与信号生成
- [ ] Day 3: 策略开发与回测框架
- [ ] Day 4: 风险管理与仓位管理
- [ ] Day 5: 策略优化与参数调优
- [ ] Day 6: 实盘模拟与性能评估
- [ ] Day 7: 项目总结与部署

## 🏗️ 项目结构

```
MzQuant-Bootcamp7/
├── bootcamp7/           # 核心代码目录
│   └── src/            # 源代码
├── docs/               # 文档目录
│   ├── source/         # Sphinx文档源文件
│   ├── build/          # 构建输出
│   ├── Makefile        # 构建脚本
│   └── make.bat        # Windows构建脚本
├── notebooks/          # Jupyter笔记本
│   └── day1.ipynb     # Day1学习内容
├── README.md           # 项目说明文档
└── readthedocs.yaml    # ReadTheDocs配置
```

## 🚀 快速开始

### 环境要求
- Python 3.13+
- Jupyter Notebook
- 相关量化交易库

### 安装步骤
1. 克隆项目
```bash
git clone <repository-url>
cd MzQuant-Bootcamp7
```

2. 安装依赖
```bash
pip install -r requirements.txt
```

3. 启动Jupyter Notebook
```bash
jupyter notebook
```

## 📖 学习资源

- **Day1**: 框架搭建与数据获取
- **技术栈**: Python, Pandas, NumPy, Matplotlib, Plotly
- **数据源**: 股票市场数据API
- **分析方法**: EDA, 技术分析, 可视化

## 🤝 贡献指南

欢迎提交Issue和Pull Request来改进项目！

## 📄 许可证

本项目采用MIT许可证。

## 👨‍💻 作者

**MariusWz** - 量化交易学习项目

---

*最后更新: 2025年8月*
