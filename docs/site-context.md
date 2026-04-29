# ChinaGreat-Sec 站点技术上下文

> **用途**：每次开启新会话时，先让 AI 读取本文件以快速恢复上下文。  
> **维护**：每次做出重要技术决策后更新本文件。

---

## 🌐 站点基本信息

| 字段 | 值 |
|------|----|
| 网址 | https://chinagreat-sec.github.io/ |
| 仓库 | https://github.com/ChinaGreat-Sec/chinagreat-sec.github.io |
| 本地路径 | `C:\github\ChinaGreat-Sec\` |
| 技术栈 | Jekyll + jekyll-theme-hacker |
| 语言 | 纯中文（已移除双语功能） |
| 部署 | GitHub Pages（main 分支自动构建） |

---

## ⚙️ Jekyll 配置（`_config.yml`）

```yaml
title: "ChinaGreat-Sec"
description: "IOT 网络安全社区"
url: "https://chinagreat-sec.github.io"
baseurl: ""          # 组织 Pages，baseurl 为空
theme: jekyll-theme-hacker
markdown: kramdown
```

**关键注意事项**：
- `baseurl` 为空，所有链接必须使用 `{{ '/path/' | relative_url }}` 而不是相对路径 `./path/`
- 不能直接写 `href="/vulnerabilities/"` 需写 `href="{{ '/vulnerabilities/' | relative_url }}"`

---

## 🎨 主题与样式（`assets/css/style.scss`）

### 颜色变量
```scss
--accent:     #a855f7   /* 主色：蓝紫色 */
--accent-dim: #7c3aed   /* 暗色版 */
--accent-glow: rgba(168, 85, 247, 0.18)
--bg:         #0a070f   /* 背景 */
--bg-card:    #100d1a   /* 卡片背景 */
--border:     #a855f733 /* 边框 */
```

### 已知 hacker 主题 quirk（坑）
1. **`header h1::before`** 会自动插入 `"./ "` 前缀 → 已用 `content: "" !important` 覆盖
2. **`h4/h5/h6` 颜色** 主题默认绿色，不随 h1/h2/h3 继承 → 已单独添加 `color: var(--accent) !important`
3. **`header h2`（副标题）** 默认不可见 → 已单独设置颜色和字号
4. **lang-switcher.html** 的 `<style>` 块是内联样式，不继承 CSS 变量 → 已清空（移除双语后不再需要）

### 组件规范
```scss
/* 返回按钮 */
.back-home   /* 子页面用 🔙，首页直接子模块用 🏠 */

/* 卡片样式（用 inline style 触发 CSS 选择器） */
style="border:1px solid #444"  /* → SCSS 会自动添加发光效果 */
```

---

## 📁 目录结构

```
chinagreat-sec.github.io/
├── _config.yml
├── _includes/
│   └── lang-switcher.html    # 已清空，保留文件避免 Jekyll 报错
├── assets/
│   ├── css/style.scss        # 所有自定义样式
│   └── images/
│       └── Forti/CVE-2022-42475/   # 7 张 PNG 截图
├── index.md                  # 首页
├── vulnerabilities/
│   ├── index.md              # 漏洞研究模块首页
│   ├── CVE/
│   │   ├── index.md          # CVE 列表页
│   │   └── CVE-2022-42475/
│   │       └── index.md      # 完整漏洞分析文章
│   └── research/
│       └── index.md          # 原创研究（占位）
├── tools/index.md
├── resources/index.md
├── writeups/index.md
├── CONTRIBUTING.md
├── README.md
└── docs/
    └── site-context.md       # 本文件
```

---

## 📄 页面编写规范

### Front Matter 模板
```yaml
---
layout: default
title: "页面标题"
permalink: /path/to/page/
---
```

### 页面结构模板
```html
# 页面标题

<p>页面简介</p>

<!-- 正文内容 -->

<a href="{{ '/parent/' | relative_url }}" class="back-home" title="返回上一页">🔙</a>
```

### 返回按钮规则
- 返回**首页**：用 🏠，链接 `{{ '/' | relative_url }}`
- 返回**上一级**：用 🔙，链接 `{{ '/parent-path/' | relative_url }}`

### 图片引用
```markdown
![图片描述]({{ '/assets/images/分类/文件名.png' | relative_url }})
```
图片存放路径：`assets/images/<厂商或分类>/<CVE编号或项目名>/`

---

## 📝 漏洞文章模板

新建漏洞文章路径：`vulnerabilities/CVE/CVE-XXXX-XXXXX/index.md`

```markdown
---
layout: default
title: "CVE-XXXX-XXXXX | 设备名 漏洞类型简述"
permalink: /vulnerabilities/CVE/CVE-XXXX-XXXXX/
---

# CVE-XXXX-XXXXX — 设备名 漏洞类型 Pre-auth RCE

<p>
<img src="https://img.shields.io/badge/CVSS-X.X%20Critical-red" alt="CVSS">
<img src="https://img.shields.io/badge/类型-漏洞类型-orange" alt="Type">
<img src="https://img.shields.io/badge/影响-设备版本-blue" alt="Affected">
</p>

---

## 漏洞概述
...

## 环境搭建
...

## 漏洞分析
...

## 利用过程
...

> ⚠️ **免责声明**：本文仅用于安全研究与教育目的。请勿将上述技术用于未经授权的系统。

<a href="{{ '/vulnerabilities/CVE/' | relative_url }}" class="back-home" title="返回 CVE 列表">🔙</a>
```

**添加完文章后记得更新：**
1. `vulnerabilities/CVE/index.md` — 在统计表和列表中添加新条目
2. `vulnerabilities/index.md` — 更新"最新收录"卡片

---

## 🤝 协作工作流

### 分支命名规范
```
vuln/CVE-XXXX-XXXXX     漏洞文章
tools/add-工具名         工具收录
resources/add-内容简述   学习资料
writeups/设备名-日期     实战记录
fix/问题简述             样式或错误修复
```

### 每次提交流程
```bash
# 1. 同步最新 main
git checkout main && git pull origin main

# 2. 创建功能分支
git checkout -b vuln/CVE-2024-XXXXX

# 3. 写内容，提交
git add .
git commit -m "feat: add CVE-2024-XXXXX [厂商] 漏洞类型简述"

# 4. 推送，发起 PR
git push origin vuln/CVE-2024-XXXXX
```

### commit message 规范
```
feat: add CVE-2024-XXXXX FortiOS 堆溢出分析
fix:  修复首页链接错误
style: 更新卡片样式
docs: 更新 CONTRIBUTING.md
```

### 责任分工建议
| 成员 | 负责目录 | 不要随意修改 |
|------|----------|-------------|
| 漏洞研究 | `vulnerabilities/` `assets/images/` | `assets/css/style.scss` |
| 安全工具 | `tools/` | `_config.yml` |
| 学习资料 | `resources/` | `_includes/` |
| 样式/架构 | `assets/css/` `_config.yml` `_includes/` | — |

> `assets/css/style.scss` 和 `_config.yml` 是全局文件，修改前请在 PR 中说明原因。

---

## 🔄 会话恢复提示词

每次新开会话，告诉 AI：
> "请先读取 `C:\github\ChinaGreat-Sec\docs\site-context.md`，了解项目背景后继续协助我维护这个网站。"
