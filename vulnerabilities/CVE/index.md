---
layout: default
title: CVE 漏洞分析
permalink: /vulnerabilities/CVE/
---


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

<h2>📤 提交知识帖</h2>
<p>有知识帖想分享？漏洞复现、学习笔记、技术分享、疑问求助……。欢迎发送至 <a href="https://github.com/ChinaGreat-Sec/ChinaGreat-Sec/issues/new?template=vulnerability.yml">chinagreatsec@outlook.com</a> 提交。</p>

<a href="{{ '/vulnerabilities/' | relative_url }}" class="back-home" title="返回漏洞研究 / Back">🔙</a>
