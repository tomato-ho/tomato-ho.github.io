---
title: "关于我"
date: 2026-05-22
layout: "about"
url: "/about/"
summary: "我的一些经历与成长"
---

## 👋 你好，我是散漫成长技的作者

高级运维工程师出身，但这两年干的事情早就不只是运维了。

从零搭建大数据平台、自研数据网关、写 C++/Go/Python、部署 AI 模型……基本上公司缺什么我就做什么。比起"运维工程师"，我更愿意把自己定义为**基础设施 + 数据工程 + AI 工程化**的复合型工程师。

---

## 🔧 技术栈

| 方向 | 技术 |
|------|------|
| 大数据 | Hadoop / Spark / Hive / StarRocks / DolphinScheduler |
| 数据传输 | Apache Arrow / Arrow Flight / Flight SQL |
| 后端开发 | C++ / Golang / Python / Java / SpringBoot |
| AI 工程化 | LlamaCPP / Dify / LlamaFactory / LoRA 微调 |
| 存储 | HDFS / S3 / MySQL / Redis / Elasticsearch |
| 监控运维 | Prometheus / Grafana / ELK / GitLab / LDAP |
| 权限管理 | Casbin |
| 前端/桌面 | C++ Qt |

---

## 🚀 代表性项目

### 大数据平台从零搭建
从无到有独立搭建公司大数据基础设施，包含 Hadoop / Spark / Hive / DolphinScheduler / StarRocks 全套集群。

在此基础上完成了数据分析代码的整体迁移重构：
- 原有单机 Python Spark 代码 → 迁移至 Spark 集群
- 数据存储从本地文件 → HDFS + Hive 表映射
- 查询加速层引入 StarRocks
- **计算耗时从 1 天压缩到 20~30 分钟**
- 从经常崩溃的命令行脚本，重构为网页点击即可运行的稳定服务

---

### 数据读取性能优化
另一个数据分析项目原使用 Pandas 读取本地数据，经重构后：
- 使用 **C++ Arrow Flight** 将数据迁移至 HDFS
- 实现 Hive 数据库映射，StarRocks 查询加速
- 统一了多个项目的数据使用方式
- **数据读取性能提升 50% 以上**
- **程序运行时长从 24 小时缩短至 3 小时**

---

### 自研数据网关（核心项目）
公司内部 Python / Java / R 各自使用不同的库访问 HDFS / S3，权限混乱、标准不统一、无审计。

为解决这个问题，**独立使用 libpgquery + C++ Arrow + Casbin 实现了 Flight SQL 协议的数据网关**：
- 统一权限管理，所有数据读写经由网关鉴权
- 统一数据传输标准，避免各语言重复造轮子
- 内置审计功能，完整记录数据读写行为
- 提供 Python / Java / R 多语言 SDK 供业务方直接使用

---

### HDFS 文件管理桌面工具
数据统一迁移到 HDFS 后，数据分析人员无法直接操作文件。

使用 **C++ Qt** 开发了类似 WinSCP 的桌面客户端，支持本地文件与 HDFS 文件之间的拖拽上传和下载，解决了数据分析人员的日常使用痛点。

---

### 监控告警体系建设
搭建完整的监控基础设施：Prometheus / Grafana / ELK（Elasticsearch + Kibana + Filebeat）/ GitLab / LDAP。

在此基础上用 **Golang** 做了两个扩展：
- **飞书告警集成**：接收 Alertmanager 告警并实时推送到飞书群，业务和运维第一时间响应
- **外部心跳监控**：解决内网 Prometheus 单点故障问题。各监控主机定时上报心跳，外部系统分析心跳状态，长时间无心跳则通过**阿里云短信**发送告警，确保即使内网监控系统本身故障也不会漏报

---

### SSL 证书自动化
公司两个公网网站每年手动购买和更新证书，使用 **lego** 实现自动签发与续签，部署后完全无需人工介入，**每年节省证书费用约 XXX 元**。

---

### 内网 AI 模型部署
独立搭建 **LlamaCPP + Dify**，在公司 GPU 服务器上实现各主流大语言模型的内网私有化部署，数据不出内网。

目前也在研究模型微调方向（Qwen3 LoRA SFT），探索 AI 工程化落地。

---

### 遗留系统现代化重构
使用 AI 辅助工具（OpenCode / OpenClaw）将一个老旧 PHP 项目完整重写，新架构为 **SpringBoot + Elasticsearch + MySQL + Redis**。

---

### 数据驱动 PPT 生成
在建项目，架构为 **FastAPI + python-pptx**，目标是通过数据自动生成结构化 PPT，减少重复性手工制作。

---

## 📝 关于这个博客

这里记录我在**大数据、数据工程、AI 工程化、系统开发、运维**等方向的实践经验和踩坑记录。

不追热点，只写自己真正做过的东西。

## 🌱 正在探索

- **模型微调**：研究 Qwen3 LoRA SFT，探索小模型在垂直场景的落地
- **AI 工程化**：RAG / Agent 部署与生产化

---

## 📬 联系我

- GitHub：[tomato-ho](https://github.com/tomato-ho)
- 邮箱: mail_maomao@163.com
