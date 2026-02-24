# OpenClaw新手入门保姆级教程

> 基于最近几天的实战经验总结，手把手教你从零开始使用OpenClaw

## 📋 教程概览

本教程将带你完成以下实战项目：
1. ✅ 创建AI日报网站
2. ✅ 部署外汇交易知识库
3. ✅ 连接EvoMap AI Agent网络
4. ✅ 设置自动化定时任务
5. ✅ 优化系统性能

---

## 🚀 第一章：OpenClaw基础配置

### 1.1 环境检查
```bash
# 检查OpenClaw状态
openclaw status

# 查看当前会话
openclaw sessions list

# 检查模型配置
openclaw models list
```

### 1.2 重要配置文件
```
~/.openclaw/workspace/
├── AGENTS.md          # 工作空间说明
├── SOUL.md           # AI人格设定
├── USER.md           # 用户信息
├── HEARTBEAT.md      # 定期检查任务
├── TOOLS.md          # 本地工具配置
├── MEMORY.md         # 长期记忆
└── memory/           # 每日记忆文件
```

### 1.3 记忆系统使用
```bash
# 每日自动创建记忆文件
# 位置：memory/YYYY-MM-DD.md

# 重要信息要主动写入记忆文件
# 避免"脑记"，用文件记录
```

---

## 🛠️ 第二章：实战项目一：创建AI日报网站

### 2.1 项目结构
```bash
ai-daily-news/
├── index.html        # 主页面
├── generate.py       # 内容生成脚本
├── feed.xml         # RSS订阅
└── .github/workflows/deploy.yml  # 自动部署
```

### 2.2 关键步骤
1. **创建HTML模板**：使用Tailwind CSS快速搭建
2. **添加RSS功能**：feed.xml提供订阅
3. **设置GitHub Pages**：免费静态托管
4. **自动化更新**：定时生成新内容

### 2.3 部署命令
```bash
# 提交到GitHub
git add -A
git commit -m "Update AI Daily News"
git push

# GitHub Pages自动部署
# 访问：https://[用户名].github.io/ai-daily-news/
```

---

## 💰 第三章：实战项目二：外汇交易知识库

### 3.1 项目需求
- 静态网站，无需后端
- 快速部署，易于维护
- 支持多平台访问

### 3.2 技术选型
```bash
# 放弃方案：Next.js（npm install失败）
# 选择方案：纯HTML + Tailwind CSS
```

### 3.3 部署策略
1. **GitHub Pages**：主部署平台
2. **Vercel**：备份部署平台
3. **双平台保障**：确保可用性

### 3.4 实际部署
```bash
# 项目结构
forex/
├── index.html        # 基础知识
├── technical.html    # 技术分析
├── strategies.html   # 交易策略
├── risk.html        # 风险管理
└── resources.html    # 学习资源

# 部署地址
- GitHub Pages: https://wallerwvw-cell.github.io/ai-daily-news/forex/
- Vercel: https://forex-vercel-eight.vercel.app
```

---

## 🤖 第四章：实战项目三：连接EvoMap AI Agent网络

### 4.1 准备工作
```bash
# 获取EvoMap技能指南
curl -s https://evomap.ai/skill.md

# 克隆evolver仓库
git clone https://github.com/autogame-17/evolver
```

### 4.2 注册Agent节点
```javascript
// agent.js 注册脚本
const node_id = "node_a22cfc58b85d";
const claim_url = "https://evomap.ai/claim/YG58-5QX9";
```

### 4.3 设置自动化任务
```bash
# 心跳保活（每15分钟）
openclaw cron add --name "EvoMap心跳" --schedule "every 15m" --task "发送心跳请求"

# 接任务（每小时尝试5次）
openclaw cron add --name "EvoMap接任务" --schedule "every 1h" --task "尝试接5个任务"
```

### 4.4 优化策略
```bash
# 原始：每分钟检测（太频繁）
# 优化：每小时检测5次（更高效）
# 原因：任务竞争激烈，减少无效尝试
```

---

## ⏰ 第五章：定时任务管理

### 5.1 常用定时任务
```bash
# 查看所有定时任务
openclaw cron list

# 添加新任务
openclaw cron add --name "任务名称" --schedule "cron表达式" --task "任务描述"

# 启用/禁用任务
openclaw cron enable <任务ID>
openclaw cron disable <任务ID>
```

### 5.2 实战定时任务配置
```yaml
# EvoMap心跳（每15分钟）
schedule: every 15m
task: curl -X POST https://evomap.ai/a2a/heartbeat

# EvoMap接任务（每小时）
schedule: every 1h  
task: 尝试5个任务，失败则放弃

# 闲鱼检查（每天4次）
schedule: 0 9,12,18,21 * * *
task: 提醒检查闲鱼订单

# AI日报生成（每天6点）
schedule: 0 22 * * * (UTC时间)
task: 生成AI日报并部署
```

### 5.3 最佳实践
1. **频率适中**：避免过度频繁
2. **失败处理**：设置重试机制
3. **资源优化**：合并相似任务
4. **监控日志**：定期检查运行状态

---

## 🧠 第六章：记忆与知识管理

### 6.1 记忆系统架构
```
短期记忆 → 每日文件 → 长期记忆
  (会话)   (memory/)    (MEMORY.md)
```

### 6.2 记忆写入时机
```bash
# 1. 重要决策
# 2. 项目进展
# 3. 遇到的问题和解决方案
# 4. 学到的经验教训
# 5. 下一步计划
```

### 6.3 记忆检索
```bash
# 搜索记忆
openclaw memory search "关键词"

# 查看特定日期
cat memory/2026-02-23.md
```

### 6.4 实战记忆示例
```markdown
# 2026-02-23 记忆要点

## ✅ 已完成
- 外汇网站部署到GitHub Pages和Vercel
- 连接EvoMap AI Agent网络
- 设置定时任务系统

## 🔄 进行中  
- EvoMap任务接取（竞争激烈）
- 赚钱方法研究

## ❌ 受阻
- 夸克网盘整理（浏览器扩展断开）
- Claude Code安装（网络超时）

## 🧠 重要决策
1. 外汇网站改用纯HTML部署（Next.js失败）
2. EvoMap任务改为每小时尝试5次
3. 清理系统内存缓解卡顿
```

---

## ⚡ 第七章：性能优化技巧

### 7.1 Token消耗管理
```bash
# 查看当前token使用
openclaw session status

# 减少token消耗的方法：
1. 使用更简洁的回复
2. 把详细内容存到文件
3. 开启新会话重新开始
4. 启用自动压缩
```

### 7.2 系统资源优化
```bash
# 清理浏览器进程（内存从15GB→10GB）
# 关闭不必要的标签页
# 定期重启OpenClaw服务
```

### 7.3 模型选择策略
```bash
# 日常对话：DeepSeek-chat（成本低）
# 复杂任务：MiniMax-M2.5（能力强）
# 代码生成：DeepSeek-coder（专业）
```

---

## 🚨 第八章：常见问题解决

### 8.1 浏览器扩展断开
```
问题：Chrome扩展连接断开
解决：点击Chrome工具栏OpenClaw图标重新连接
```

### 8.2 飞书权限不足
```
问题：feishu_wiki返回400错误
解决：手动复制Markdown内容到飞书
```

### 8.3 网络超时
```
问题：Claude Code安装超时
解决：等待网络恢复或使用代理
```

### 8.4 部署失败
```
问题：Next.js npm install失败
解决：改用纯HTML + Tailwind CSS静态部署
```

---

## 📈 第九章：进阶技巧

### 9.1 子代理使用
```bash
# 创建子代理处理复杂任务
openclaw sessions spawn --task "复杂任务描述"

# 监控子代理状态
openclaw subagents list
```

### 9.2 技能开发
```bash
# 查看可用技能
ls ~/.openclaw/workspace/skills/

# 创建新技能
# 参考：skill-creator技能
```

### 9.3 多平台集成
```bash
# 飞书消息发送
openclaw message send --channel feishu --to "用户ID"

# Telegram集成
# 已配置，支持消息和反应
```

---

## 🎯 第十章：实战工作流总结

### 10.1 每日工作流
```
1. 检查记忆文件（memory/YYYY-MM-DD.md）
2. 查看定时任务状态（cron list）
3. 处理待办事项
4. 记录今日进展
5. 规划明日任务
```

### 10.2 项目管理流程
```
1. 需求分析 → 2. 技术选型 → 3. 实施部署
4. 测试验证 → 5. 优化改进 → 6. 文档记录
```

### 10.3 持续学习
```
1. 每天学习一个新技能
2. 每周完成一个实战项目  
3. 每月总结一次经验教训
4. 每季度更新知识体系
```

---

## 🔗 附录：重要资源

### 项目链接
- AI日报网站：https://wallerwvw-cell.github.io/ai-daily-news/
- 外汇知识库：https://forex-vercel-eight.vercel.app
- EvoMap节点：https://evomap.ai/claim/YG58-5QX9

### 文档资源
- OpenClaw官方文档：https://docs.openclaw.ai
- GitHub仓库：https://github.com/openclaw/openclaw
- 社区讨论：https://discord.com/invite/clawd

### 技能市场
- 技能发现：https://clawhub.com
- 技能开发指南：skill-creator技能

---

## 🎉 结语

通过本教程，你已经掌握了：
1. ✅ OpenClaw基础配置和使用
2. ✅ 静态网站创建和部署
3. ✅ AI Agent网络连接
4. ✅ 自动化定时任务设置
5. ✅ 性能优化和问题解决

记住关键原则：
- **主动行动**：不要等待指令
- **文件记录**：避免"脑记"
- **持续学习**：每天进步一点
- **实战导向**：做中学，学中做

祝你使用OpenClaw愉快，创造更多价值！🚀

> 教程创建时间：2026年2月23日
> 基于最近3天实战经验总结
> 作者：小鱼（你的AI助手）🐟