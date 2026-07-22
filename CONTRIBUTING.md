# 贡献指南

感谢你对 OOB IoT Sec Labs 的关注。本站采用“Owner 维护整体框架，成员通过 Pull Request 贡献子模块内容”的协作方式。

技术细节、页面模板和站点上下文请参阅 [`docs/site-context.md`](docs/site-context.md)。

---

## 维护权限边界

仓库 Owner：[@ChinaGreat-IoTSec](https://github.com/ChinaGreat-IoTSec)

Owner 负责：

- 站点整体框架、目录结构与导航
- GitHub Pages / Jekyll 配置
- 页面布局、主题样式、Logo、favicon
- 贡献规范、Issue / PR 模板、CODEOWNERS
- PR 最终审核与合并

其他成员主要贡献子模块内容：

| 模块 | 允许贡献目录 |
| --- | --- |
| 漏洞研究 | `vulnerabilities/` |
| 安全工具 | `tools/` |
| 学习资料 | `resources/` |
| 实战记录 | `writeups/` |
| 文章配图 | `assets/images/<分类或厂商>/` |

未经 Owner 确认，请不要在内容 PR 中修改：

- `_config.yml`
- `_layouts/`
- `_includes/`
- `assets/css/`
- `.github/`
- `README.md`
- `CONTRIBUTING.md`
- `docs/site-context.md`
- `favicon.ico`
- 站点 Logo、首页结构、全局视觉风格

如果确实需要修改上述文件，请在 PR 描述中单独说明原因、影响范围和验证方式。

---

## 权限控制方式

建议仓库开启 `main` 分支保护：

- 禁止直接 push 到 `main`
- 所有修改通过 Pull Request 合并
- 至少需要 1 个 approval
- 开启 Require review from Code Owners
- 开启 Dismiss stale pull request approvals when new commits are pushed
- 开启 Require conversation resolution before merging
- 禁止 force push
- 禁止删除 `main`

本仓库使用 [`.github/CODEOWNERS`](.github/CODEOWNERS) 指定代码负责人。当前所有模块均由 `@ChinaGreat-IoTSec` 审核；后续成员稳定后，可将子模块负责人拆分为 GitHub Team。

---

## 贡献流程

推荐流程：

```bash
# 1. 从 main 创建功能分支
git checkout main
git pull origin main
git checkout -b vuln/CVE-2024-XXXXX

# 2. 修改内容
git add .
git commit -m "feat: add CVE-2024-XXXXX FortiOS 堆溢出分析"

# 3. 推送分支并发起 Pull Request
git push origin vuln/CVE-2024-XXXXX
```

如果你没有仓库写权限，请先 Fork 本仓库，然后从 Fork 发起 Pull Request。

---

## 分支命名规范

| 类型 | 格式 | 示例 |
| --- | --- | --- |
| 漏洞文章 | `vuln/CVE-XXXX-XXXXX` | `vuln/CVE-2024-12345` |
| 工具收录 | `tools/add-工具名` | `tools/add-binwalk` |
| 学习资料 | `resources/add-简述` | `resources/add-iot-books` |
| 实战记录 | `writeups/设备名` | `writeups/tplink-archer` |
| 修复 | `fix/问题简述` | `fix/cve-index-link` |
| 文档 | `docs/内容简述` | `docs/update-contributing` |

---

## Commit 规范

```text
feat:  新增内容，例如文章、工具、资料
fix:   修复错误
style: 样式调整
docs:  文档更新
chore: 维护类修改
```

示例：

```text
feat: add CVE-2024-XXXXX router overflow analysis
docs: add firmware analysis resources
fix: correct CVE index link
```

---

## 内容目录规范

| 内容类型 | 路径 |
| --- | --- |
| CVE 分析 | `vulnerabilities/CVE/CVE-XXXX-XXXX/index.md` |
| 原创研究 | `vulnerabilities/research/<名称>/index.md` |
| 工具收录 | `tools/<分类>/index.md` |
| 学习资料 | `resources/<分类>/index.md` |
| Writeup | `writeups/<设备名-日期>/index.md` |
| 相关图片 | `assets/images/<厂商或分类>/<项目名>/` |

---

## 页面编写要求

- 页面必须包含 Jekyll Front Matter
- 链接优先使用 `{{ '/path/' | relative_url }}`
- 返回按钮使用文字，例如“返回首页”“返回漏洞研究”
- 标题不使用装饰性 emoji
- 图片放入 `assets/images/` 对应目录，不依赖外部图床
- 新增文章后同步更新对应索引页
- 内容必须用于安全研究与教育目的

技术文章投稿必须参考 [`docs/technical-article-template.md`](docs/technical-article-template.md)。维护者会先进行文章规范化检查，确认结构、元数据、图片、引用和安全边界符合要求后，再提交或合并。

---

## 添加漏洞文章后的必要更新

新增 CVE 文章后至少同步更新：

1. `vulnerabilities/CVE/index.md`：统计表与漏洞列表
2. `vulnerabilities/index.md`：最新收录卡片

详细模板见 [`docs/site-context.md`](docs/site-context.md#漏洞文章模板)。

---

## PR 合并检查清单

- [ ] 修改范围符合权限边界
- [ ] 内容准确，术语和格式一致
- [ ] 技术文章已通过 [`docs/technical-article-template.md`](docs/technical-article-template.md) 中的规范化检查清单
- [ ] 未混入无关样式、配置或框架修改
- [ ] 图片已放入 `assets/images/` 对应目录
- [ ] 链接格式正确
- [ ] 返回按钮使用文字
- [ ] 新增内容已同步更新相关索引页
- [ ] 不包含未授权攻击、恶意利用或违法用途内容

---

## 使用 AI 辅助维护

本项目允许使用 AI 工具辅助编写、整理和审校内容。使用 AI 生成内容时，贡献者仍需自行验证技术准确性。

每次开启新会话时，可以将以下提示语发给 AI：

> 请先读取 `docs/site-context.md`，了解项目背景后继续协助我维护这个网站。
