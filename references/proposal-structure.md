# HTML 提案结构手册

叙事主线：**货架已经摆好，舞台还没点亮**（先立客户优势，再点出内容空白）。5 个 section，缺一不可。

## Section 结构与图表选型

| # | Section | 内容 | 图表 |
|---|---|---|---|
| Hero | 封面 | 主张 + 4 个钩子数字（市场规模/达人信任度/达人规模/渠道空白比） | 无 |
| 01 | 客户画像 | 公司实力 3 卡片（工厂 SKU/品牌矩阵/全球布局）+ **渠道盘点表**（7 渠道亮灯图）+ 诊断结论框 | 无 |
| 02 | 市场大盘 | 4 个规模数字 + 市场结构洞察 3 卡片 | 类目 Top10 横向条形图（客户所在类目高亮）；市场规模增长柱状图 |
| 03 | 达人生态 | "小达人大转化"论点 + 论据卡片 | 达人分层双轴图（互动率柱 × 成本线，体现粉丝越少互动越真） |
| 04 | 竞品拆解 | 2-3 个竞品卡片（GMV/达人打法/本地化动作）+ 四步起量公式 | 竞品单月 GMV 对标柱状图（客户目标位置标注在图上） |
| 05 | 合作方案 | 90 天三阶段（P1 基建/P2 引爆/P3 大促冲刺，各带 KPI）+ Why Us + 风险前置管理 + 收尾 CTA | 无 |

## 必埋的三个谈单钩子

1. **路径已验证**：同供应链画像的竞品已做到 X 千万 GMV——降低客户决策风险
2. **合规救火**：平台认证/税费新政的大限期——体现专业度，制造 urgency
3. **前车之鉴**：同品类被盗版/抢注的案例——商标确权紧迫性

## 数据规范

- 每个数字标出处（时间+口径），footer 汇总数据源清单 + "仅供提案讨论"
- 不确定的数据标注"约/量级"，禁止编造精确数字
- KPI 目标写成区间（如"单月 GMV $5–10 万"）

## 风格与代码

- 视觉：Neon Noir（深午夜蓝紫 #0B0A1A 底，霓虹粉 #FF2E63 / 青 #08D9D6 / 金 #F9C80E），Unbounded + Noto Sans SC + JetBrains Mono 字体
- 技术栈与动效规范遵循 `html-report` skill（GSAP ScrollTrigger reveal、ECharts SVG、自定义 tooltip）
- 骨架代码：复制 `assets/proposal-template.html`，替换标题文案、卡片数据、4 个图表的 data 数组即可。图表 JS 集中在文件末尾 `make('chartXxx', {...})` 调用中，注释清晰可定位
- 图表动画触发：模板已含"滚动到视口重放 option"逻辑，改数据时勿删 `charts.forEach` 段落

## 验证清单（交付前）

```bash
# 1. 结构自检（无残留占位符、5 section、4 chart div）
# 2. 渲染验证（file:// 会被 playwright-cli 拦截，必须走本地 http）
cd output && nohup python3 -m http.server 3000 &
playwright-cli open http://localhost:3000/index.html
playwright-cli eval "document.querySelectorAll('.chart-box svg').length"  # 应为 4
playwright-cli console error  # 应为空
playwright-cli session-stop
```
