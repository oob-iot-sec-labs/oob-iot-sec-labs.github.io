# 技术文章模板

本文档以当前 `CVE-2022-42475` 文章结构为基准，用于后续技术文章投稿。投稿文章在提交前必须完成规范化检查。

## Front Matter

```yaml
---
layout: default
title: "CVE-XXXX-XXXXX | Vendor Product 漏洞类型分析"
permalink: /vulnerabilities/CVE/CVE-XXXX-XXXXX/
category: vulnerability
tags:
  - IoT
  - CVE
  - firmware
vendor: Vendor
product: Product
author: GitHubUsername
date: YYYY-MM-DD
---
```

## 正文结构

```markdown
# CVE-XXXX-XXXXX — Vendor Product 漏洞类型简述

<p>
<img src="https://img.shields.io/badge/CVSS-X.X%20Critical-red" alt="CVSS X.X">
<img src="https://img.shields.io/badge/类型-漏洞类型-orange" alt="Type">
<img src="https://img.shields.io/badge/影响-影响版本-blue" alt="Affected">
</p>

---

## 摘要

简要说明漏洞影响、攻击条件、风险等级和本文覆盖的研究链路。

## 基本信息

| 项目 | 内容 |
| --- | --- |
| 漏洞编号 | CVE-XXXX-XXXXX |
| 厂商 | Vendor |
| 产品 | Product |
| 影响版本 | x.x.x |
| 漏洞类型 | RCE / Command Injection / Auth Bypass |
| 严重等级 | Critical / High / Medium / Low |
| CVSS | X.X |
| 攻击条件 | 未认证远程攻击 / 认证后攻击 / 本地攻击 |
| 影响结果 | RCE / 信息泄露 / 权限提升 |

## 影响范围

说明受影响组件、暴露面、受影响版本和触发入口。

## 研究环境与准备

说明固件来源、实验环境、调试环境、工具版本和必要前置步骤。

### 1. 环境搭建

### 2. 固件或系统准备

### 3. 调试与分析准备

## 漏洞分析

### 漏洞概述

### 漏洞成因

#### 触发点

#### 关键代码路径

#### 内存布局或数据流

## 利用思路与验证

### 整体利用流程

### 关键偏移或关键参数

### Payload 或 PoC 结构

### 验证结果

## 修复建议

- 升级至厂商已修复版本。
- 限制暴露面或访问来源。
- 检查异常日志、异常进程和异常网络连接。

## 参考资料

- 厂商公告
- NVD / CVE 页面
- 相关工具或研究资料

## 免责声明

> **免责声明**：本文仅用于安全研究与教育目的。请勿将上述技术用于未经授权的系统。
```

技术文章返回导航由全局布局自动生成，投稿文章不要手写返回按钮。

## 规范化检查清单

提交前必须确认：

- [ ] 文章只包含一个一级标题 `#`。
- [ ] 标题层级按 `# -> ## -> ### -> ####` 递进，不跳级。
- [ ] Front Matter 包含 `title`、`category`、`tags`、`vendor`、`product`、`author`、`date`。
- [ ] 摘要、基本信息、影响范围、研究环境、漏洞分析、利用验证、修复建议、参考资料、免责声明均已包含。
- [ ] 图片已放入 `assets/images/<厂商或分类>/<项目名>/`，并使用 `relative_url` 引用。
- [ ] 代码块围栏成对，语言标识尽量明确。
- [ ] 外部链接可访问，引用来源清晰。
- [ ] 不在文章中展开无必要的授权绕过、恶意利用或违法用途细节。
- [ ] 未手写返回按钮，技术文章返回导航由全局布局自动生成。
- [ ] 新增文章后已同步更新对应索引页。
