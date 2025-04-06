---
layout: default
title: 文档中心
description: 项目文档索引
nav_order: 1
permalink: /docs/
---

# 📚 文档中心

<div class="docs-search">
  <input type="text" id="docSearch" placeholder="输入项目名称搜索..." class="search-box">
</div>

<div class="docs-grid">
  {% assign sorted_docs = site.docs | sort: 'date' | reverse %}
  {% for doc in sorted_docs %}
    {% if doc.path contains '/index.md' and doc.url != '/docs/' %}
      <a href="{{ doc.url }}" class="doc-card">
        <div class="card-icon">{% if doc.icon %}<i class="{{ doc.icon }}"></i>{% else %}📄{% endif %}</div>
        <div class="card-content">
          <h3>{{ doc.title }}</h3>
          <p>{{ doc.description | default: '点击查看详细文档' }}</p>
          <div class="card-meta">
            {% if doc.version %}<span class="version">v{{ doc.version }}</span>{% endif %}
            {% if doc.update %}<span class="update">更新于 {{ doc.update }}</span>{% endif %}
          </div>
        </div>
      </a>
    {% endif %}
  {% endfor %}
</div>

<style>
.docs-search {
  margin: 2rem 0;
  text-align: center;
}

.search-box {
  padding: 12px 20px;
  width: 60%;
  border: 2px solid #eee;
  border-radius: 25px;
  font-size: 16px;
}

.docs-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 1.5rem;
  padding: 2rem 0;
}

.doc-card {
  border: 1px solid #eaecef;
  border-radius: 8px;
  padding: 1.5rem;
  transition: transform 0.2s;
  color: inherit;
  text-decoration: none;
}

.doc-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 4px 12px rgba(0,0,0,0.1);
}

.card-icon {
  font-size: 2.5rem;
  margin-bottom: 1rem;
}

.card-content h3 {
  margin: 0 0 0.5rem;
  color: #24292e;
}

.card-content p {
  color: #6a737d;
  margin: 0.5rem 0;
}

.card-meta {
  margin-top: 1rem;
  display: flex;
  justify-content: space-between;
  font-size: 0.9em;
  color: #586069;
}

.version {
  background: #f3f4f6;
  padding: 2px 8px;
  border-radius: 12px;
}
</style>

<script>
// 简单搜索功能
document.getElementById('docSearch').addEventListener('input', function(e) {
  const searchTerm = e.target.value.toLowerCase();
  document.querySelectorAll('.doc-card').forEach(card => {
    const title = card.querySelector('h3').textContent.toLowerCase();
    card.style.display = title.includes(searchTerm) ? 'block' : 'none';
  });
});
</script>