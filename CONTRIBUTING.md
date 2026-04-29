# 贡献指南

感谢你对 ChinaGreat-Sec 的关注！本文档说明如何参与维护本站。

> 技术细节（Jekyll 配置、样式规范、已知坑）请参阅 [`docs/site-context.md`](docs/site-context.md)。

---

## 🤝 协作分工

| 模块 | 负责目录 |
|------|----------|
| 漏洞研究 | `vulnerabilities/`、`assets/images/` |
| 安全工具 | `tools/` |
| 学习资料 | `resources/` |
| 实战记录 | `writeups/` |
| 样式/架构 | `assets/css/style.scss`、`_config.yml`、`_includes/` |

> ⚠️ `assets/css/style.scss` 和 `_config.yml` 是全局文件，修改前请在 PR 中说明原因。

---

## 📋 提交流程

```bash
# 1. 同步最新 main
git checkout main && git pull origin main

# 2. 创建功能分支
git checkout -b vuln/CVE-2024-XXXXX

# 3. 写内容并提交
git add .
git commit -m "feat: add CVE-2024-XXXXX FortiOS 堆溢出分析"

# 4. 推送并发起 Pull Request
git push origin vuln/CVE-2024-XXXXX
```

### 分支命名规范

| 类型 | 格式 | 示例 |
|------|------|------|
| 漏洞文章 | `vuln/CVE-XXXX-XXXXX` | `vuln/CVE-2024-12345` |
| 工具收录 | `tools/add-工具名` | `tools/add-binwalk` |
| 学习资料 | `resources/add-简述` | `resources/add-iot-books` |
| 实战记录 | `writeups/设备名` | `writeups/tplink-archer` |
| 修复 | `fix/问题简述` | `fix/cve-index-link` |

### Commit 规范

```
feat:  新增内容（文章、工具、资料）
fix:   修复错误
style: 样式调整
docs:  文档更新
```

---

## 📁 目录规范

| 内容类型 | 路径 |
|---------|------|
| CVE 分析 | `vulnerabilities/CVE/CVE-XXXX-XXXX/index.md` |
| 原创研究 | `vulnerabilities/research/<名称>/index.md` |
| 相关图片 | `assets/images/<厂商>/<CVE编号>/` |
| 工具收录 | `tools/<分类>/index.md` |
| 学习资料 | `resources/<分类>/index.md` |
| Writeup  | `writeups/<设备名-日期>/index.md` |

---

## 📝 添加漏洞文章后的必要更新

1. **`vulnerabilities/CVE/index.md`** — 统计表 + 漏洞列表新增条目
2. **`vulnerabilities/index.md`** — 更新"最新收录"卡片

详细模板见 [`docs/site-context.md`](docs/site-context.md#-漏洞文章模板)。

---

## ✅ PR 合并条件

- [ ] 内容准确，图片已放入 `assets/images/` 对应目录
- [ ] 链接使用 `{{ '/path/' | relative_url }}` 格式
- [ ] 返回按钮正确（🔙 返回上级，🏠 返回首页）
- [ ] 相关索引页已同步更新

---

## 🤖 使用 AI 辅助维护

本项目支持使用 GitHub Copilot CLI 或其他 AI 工具协助编写内容。  
每次开启新会话时，请将以下提示语发给 AI，以快速恢复上下文：

> 请先读取 `docs/site-context.md`，了解项目背景后继续协助我维护这个网站。
