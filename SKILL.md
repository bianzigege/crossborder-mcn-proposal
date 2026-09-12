---
name: crossborder-mcn-proposal
description: 跨境电商 MCN 客户提案工作流：对跨境电商品牌客户（重点东南亚/泰国市场）做尽职调查与提案。四步流程：(1) 客户基础信息核查（品牌归属、社媒/电商平台布局现状、招聘动向、公司地址、主营业务），(2) 客户数据页面分析，(3) 同行与品类大盘数据抓取（TikTok Shop/Shopee/Lazada 竞品 GMV、达人生态、平台规则），(4) 生成可直接给客户演示的单文件 HTML 提案。Use when 用户提到 MCN 提案、客户提案、跨境品牌尽调、达人营销提案、内容电商提案、给某品牌做 TikTok/东南亚市场分析或增长方案。
metadata:
  displayName: 跨境 MCN 客户提案
  displayNameEn: Cross-border MCN Client Proposal
  version: 1.0.0
  author: 辫子哥哥
  category: 跨境电商
  scene: 客户尽调 + 数据分析 + HTML 提案生成
---

# 跨境电商 MCN 客户提案工作流

为跨境电商品牌客户产出"尽调 + 数据分析 + 演示级 HTML 提案"的完整交付。核心叙事逻辑：**先证明客户有货没内容（痛点），再证明同赛道有人跑通了（机会），最后给出 90 天落地方案（行动）**。

## 工作流程

### Step 0：收集客户输入

向用户确认（缺啥问啥，不要全问一遍）：
1. 客户品牌名（中英文）
2. 品类（美妆/3C/小家电/家居…）
3. 已知链接/账号（可选）
4. 目标市场（默认东南亚，泰国最常见）

### Step 1：客户基础信息核查（搜索 8-12 次）

按 [references/search-playbook.md](references/search-playbook.md) 的查询模板执行，必须回答四个问题：

- **(a) 有没有做？做得怎么样？** —— 品牌归属公司（百度百科/天眼查类信息）、Shopee/Lazada/TikTok Shop 店铺、TikTok/IG/YT/FB 官方账号是否存在
- **(b) 最近招聘信息** —— 智联/BOSS/猎聘，判断团队扩张方向（电商运营？直播？海外岗？）
- **(c) 公司地址** —— 总部、关联公司、海外分公司（关联公司介绍页常含海外布局清单，是金矿）
- **(d) 主营业务** —— 品牌矩阵、SKU 规模、工厂/贴牌情况

关键产出：**渠道盘点表**——把目标市场所有主渠道（Shopee/Lazada/TikTok Shop/TikTok 账号/IG/FB/LINE/YT）逐个标注"已布局 ✓ / 空白 ✗"。空白渠道数 = 提案的切入点。

### Step 2：客户数据页面分析

基于 Step 1 发现的账号/店铺深入：
- 店铺在营状态、商品结构、价格带（webfetch 店铺页）
- 内容账号的更新频率、粉丝量、互动情况
- 注意：品牌方内容账号常查不到——这本身就是最重要的发现，直接写进提案

### Step 3：同行与品类大盘抓取

搜索目标市场的（详见 search-playbook.md 数据源清单）：
- **大盘**：平台 GMV、增速、类目 Top10 结构
- **竞品**：找 2-3 个与客户供应链画像相似的已跑通品牌，抓单月 GMV、达人数量、内容打法、直播占比
- **达人生态**：各层级达人互动率、成本、消费者达人信任度
- **平台规则与合规**：佣金费率、认证要求（如泰国 TISI）、税费新政、商标风险

### Step 4：生成 HTML 提案

结构、叙事钩子、图表选型按 [references/proposal-structure.md](references/proposal-structure.md) 执行；视觉与代码规范用 `html-report` skill。

模板骨架（Neon Noir 深色风格，含 GSAP 滚动动效 + 4 个 ECharts 图表位）在 [assets/proposal-template.html](assets/proposal-template.html)，复制后替换数据即可，省去从零搭建。

## 交付标准

- 单文件 `output/index.html`，5 个 section + ≥4 个数据图表
- 每个数字有出处（页面 footer 列数据源）
- 必含三要素：渠道盘点表（痛点）、竞品对标图（机会）、90 天三阶段方案（行动）
- 渲染验证：ECharts 图表全部出现 SVG、无 console 报错（用 playwright-cli + 本地 http.server 验证，file:// 协议会被 playwright-cli 拦截）
