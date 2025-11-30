# 🌟 AA’s · AI Projects Portfolio

---

本作品集目前收录了 2 个核心项目：

- **Job Daily Agent（求职岗位自动筛选Agent）** --- 帮助每日实现我求职季岗位自动筛选/排序
- **Labor Law RAG（劳动合同法复习资料检索助手）** --- 帮我准确期末复习劳动法，避免大模型的编造法条和案例的情况

---

## 📌 项目总览

| 项目名称 | 类型 | 技术栈 | 简述 |
|---------|------|--------|------|
| **Job Daily Agent** | 自动化系统 | Coze Workflow, LLM, GitHub Actions | 每晚自动读取平台推送的岗位邮件 → 解析 → 匹配 → 打分并提出简历修改建议 → 生成“求职日报邮件”并发送到邮箱 |
| **Labor Law RAG** | 检索增强生成（RAG） | Python, Embeddings, Vector Store, Prompt Engineering | 面向劳动法课程的精确检索助手，返回结论 / 法条 / 老师PPT中的类案检索结果，适合备考与复习 |

---

## 🚀 1. Job Daily Agent  
**自动化求职岗位筛选系统（All-in-One Job Application Assistant）**

> 自动把今日推送到邮箱的招聘平台邮件筛选后
> 打分 + 增加简历修改建议，
> 生成岗位推荐邮件 + 每日9 p.m. 发送至邮箱。

🔗 **项目仓库**：`https://github.com/AAholdingACES-zhou/job-daily-agent-cron`  
🔗 **Workflow**：`Job_Daily_Agent-Job_Daily_Agent`

### ⭐ 项目简介  

Job Daily Agent 是一个全自动求职助手，会在每天固定时间：

1. 从邮箱中抓取最近 24 小时的岗位推荐邮件（如智联、前程无忧等）
2. 用 LLM 解析邮件 HTML 文本，抽取结构化岗位信息(如岗位内容、地点、薪酬等）
3. 结合个人画像为每个岗位评估匹配度并打分
4. 生成一封包含「岗位列表 + 匹配度 + 推荐理由 + 简历修改建议」的日报邮件
5. 每日晚9点通过 SMTP 自动发送到我的个人邮箱

### 🔧 Workflow 重要结束节点

- **Coze Workflow**
  - 邮件抓取节点（IMAP）
  - 内容解析与清洗节点（代码块）
  - 岗位识别与结构化抽取（LLM）
  - 岗位匹配与打分（LLM + 规则）
  - 文本生成与邮件发送
    
- **GitHub Actions 定时触发**
  - 使用 `cron` 表达式实现每天定时调用 Coze Workflow
  - Action 日志与运行状态通过徽章展示

### 📈 流程图


- `docs/job_daily_agent_flow_chart.png`
- `docs/email_to_report_pipeline.png`

---

## 📘 2. Labor Law RAG  
**劳动法课程检索助手（RAG for Exam Review）**

🔗 **项目仓库**：`（预留，将来填上 repo 链接）`

### ⭐ 项目简介  

在复习劳动法时，我发现通用 LLM 容易：

- 只返回「劳动合同法第 X 条」而不给具体内容  
- 或者张冠李戴，把法条和案例对错号  

于是我做了一个轻量级的 **Labor Law RAG**：

- 语料：课程 PPT、案例、教师讲义等
- 输入：自然语言问题，例如“试用期解除劳动合同需要满足什么条件？”
- 输出：相关法条 / 案例 + PPT 页码 + 简短解释
- 目标：**不替代老师，只负责“查找和定位”**，提高复习效率且可溯源

### 🔧 核心技术要点

- 文档切片与向量化检索（Embeddings + 向量数据库）
- 检索结果重排序与去重
- Prompt 设计：将「问题 + 上下文 + 页码」一起送入 LLM，要求模型引用原文并显式标出来源
- 以「可追踪」为第一优先级，减少幻觉

---

## 🌱 这些项目是怎么长出来的？

- 求职期间，每天邮箱里都是岗位推送，很难快速判断有没有值得投递的。于是我做了 **Job Daily Agent** 来帮我先看一遍。
- 备考劳动法时，我不太放心直接用通用 LLM 查法条，于是做了 **Labor Law RAG**，把课堂资料变成“更听话的检索助手”。

对我来说，它们不是“练习项目”，而是我日常生活中的两件小事：  
**少一点机械劳动，多一点思考和选择。**

---

## 🧑‍💻 关于我

- 复旦大学 · 法学硕士  
- 对外经济贸易大学 · 管理学学士  
- 对 **AI × 法律 / 合规 × 自动化** 有持续兴趣  
- 喜欢做真正能落地的小工具，而不仅仅是 Demo  

---

## 📬 联系方式

- 📧 Email：`你的邮箱`
- 🌐 GitHub：`https://github.com/AAholdingACES-zhou`

---

## 📊 动态效果（GitHub 统计卡片，可选）

> 如果你不想展示，可以把下面这一段删掉。

<p align="center">
  <a href="https://github.com/AAholdingACES-zhou">
    <img src="https://github-readme-stats.vercel.app/api?username=AAholdingACES-zhou&show_icons=true&theme=tokyonight&hide_border=true" alt="GitHub stats" />
  </a>
</p>

<p align="center">
  <a href="https://github.com/AAholdingACES-zhou">
    <img src="https://github-readme-streak-stats.herokuapp.com?user=AAholdingACES-zhou&theme=tokyonight&hide_border=true" alt="GitHub Streak" />
  </a>
</p>

---

_最后更新：2025-11_
