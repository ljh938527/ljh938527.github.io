---
layout: page
title: 更新日志
permalink: /changelog/
---

{% raw %}
## 📆 近期更新

<div class="changelog">
  <!-- 此处内容会自动填充 -->
  {% for entry in site.changelog reversed %}
    <div class="entry">
      <h3>{{ entry.date | date: "%Y-%m-%d" }} | {{ entry.title }}</h3>
      <div class="content">
        {{ entry.content | markdownify }}
      </div>
    </div>
  {% else %}
    <p>暂无更新记录，请稍后再来查看~</p>
  {% endfor %}
</div>

<p class="tip">🔍 查看 <a href="/changelog/archive/">历史归档</a></p>
{% endraw %}