---
layout: default
title: CVE 漏洞分析 | CVE Analysis
permalink: /vulnerabilities/CVE/
---

<div data-lang="zh">

<h1>🗂️ CVE 漏洞分析库</h1>
<p>收录已公开 CVE 编号的 IOT / 网络设备漏洞分析报告，包含漏洞原理、复现步骤及利用过程。</p>

<h2>📊 收录统计</h2>

| 厂商 | CVE 编号 | 类型 | 危险等级 |
|------|----------|------|----------|
| Fortinet FortiOS | CVE-2022-42475 | 堆缓冲区溢出 | 🔴 Critical 9.8 |

<h2>📋 漏洞列表</h2>

<div style="display:flex; flex-direction:column; gap:12px; margin:16px 0;">

  <div style="border:1px solid #444; border-radius:8px; padding:16px 20px; background:#111;">
    <h3 style="margin:0 0 8px;">🔴 CVE-2022-42475 <span style="font-size:0.75em; font-weight:normal; color:#aaa;">CVSS 9.8 · Critical</span></h3>
    <p style="margin:4px 0;"><strong>设备：</strong>Fortinet FortiOS（SSL-VPN sslvpnd 守护进程）</p>
    <p style="margin:4px 0;"><strong>类型：</strong>堆缓冲区溢出 → Pre-auth RCE</p>
    <p style="margin:4px 0;"><strong>影响版本：</strong>FortiOS 6.0 ~ 7.2.2</p>
    <p style="margin:4px 0;"><strong>内容：</strong>EVE-NG 环境搭建 · 固件定制 · 内核调试 · ROP 链 · Shellcode · Exploit</p>
    <a href="{{ '/vulnerabilities/CVE/CVE-2022-42475/' | relative_url }}">→ 查看详细分析</a>
  </div>

</div>

<h2>📤 提交新漏洞</h2>
<p>发现新的 CVE？欢迎通过 <a href="https://github.com/ChinaGreat-Sec/ChinaGreat-Sec/issues/new?template=vulnerability.yml">Issue 模板</a> 提交。</p>

<a href="{{ '/vulnerabilities/' | relative_url }}" class="back-home" title="返回漏洞研究 / Back">🔙</a>

</div>

<div data-lang="en">

<h1>🗂️ CVE Analysis Library</h1>
<p>IoT and network device vulnerability reports with public CVE IDs, covering root cause, reproduction, and exploitation.</p>

<h2>📊 Statistics</h2>

| Vendor | CVE | Type | Severity |
|--------|-----|------|----------|
| Fortinet FortiOS | CVE-2022-42475 | Heap Buffer Overflow | 🔴 Critical 9.8 |

<h2>📋 Vulnerability List</h2>

<div style="display:flex; flex-direction:column; gap:12px; margin:16px 0;">

  <div style="border:1px solid #444; border-radius:8px; padding:16px 20px; background:#111;">
    <h3 style="margin:0 0 8px;">🔴 CVE-2022-42475 <span style="font-size:0.75em; font-weight:normal; color:#aaa;">CVSS 9.8 · Critical</span></h3>
    <p style="margin:4px 0;"><strong>Device:</strong> Fortinet FortiOS (SSL-VPN sslvpnd daemon)</p>
    <p style="margin:4px 0;"><strong>Type:</strong> Heap Buffer Overflow → Pre-auth RCE</p>
    <p style="margin:4px 0;"><strong>Affected:</strong> FortiOS 6.0 ~ 7.2.2</p>
    <p style="margin:4px 0;"><strong>Covers:</strong> EVE-NG setup · Firmware customization · Kernel debugging · ROP chain · Shellcode · Full exploit</p>
    <a href="{{ '/vulnerabilities/CVE/CVE-2022-42475/' | relative_url }}">→ Read Full Analysis</a>
  </div>

</div>

<h2>📤 Submit a CVE</h2>
<p>Found a new IoT CVE? Submit via the <a href="https://github.com/ChinaGreat-Sec/ChinaGreat-Sec/issues/new?template=vulnerability.yml">Issue template</a>.</p>

<a href="{{ '/vulnerabilities/' | relative_url }}" class="back-home" title="返回漏洞研究 / Back">🔙</a>

</div>

{% include lang-switcher.html %}
