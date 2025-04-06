---
layout: default
title: 文档中心
nav_order: 1
permalink: /docs/
---

# 📂 项目文档索引

<div class="docs-container">
  <div class="docs-filter">
    <input type="text" id="searchInput" placeholder="输入项目名称过滤..." class="filter-input">
  </div>

  <div class="docs-grid">
    {% comment %} 确保正确遍历文档结构 {% endcomment %}
    {% for collection in site.collections %}
      {% if collection.label == 'docs' %}
        {% for doc in collection.docs %}
          {% if doc.path contains '/index.md' and doc.url != '/docs/' %}
            <div class="doc-item" data-title="{{ doc.title | downcase }}">
              <div class="doc-card">
                <h3>{{ doc.title }}</h3>
                <div class="doc-meta">
                  {% if doc.last_modified %}
                    <span class="update-time">
                      📅 {{ doc.last_modified | date: "%Y-%m-%d" }}
                    </span>
                  {% endif %}
                  {% if doc.repository %}
                    <a href="{{ doc.repository }}" 
                       class="repo-link"
                       target="_blank" 
                       rel="noopener noreferrer">
                      <svg class="github-icon" viewBox="0 0 16 16" width="16" height="16">
                        <path fill-rule="evenodd" d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/>
                      </svg>
                      查看仓库
                    </a>
                  {% endif %}
                </div>
                <div class="doc-excerpt">
                  {{ doc.description | default: "点击查看完整文档 →" }}
                </div>
                <a href="{{ doc.url }}" class="doc-link">查看文档</a>
              </div>
            </div>
          {% endif %}
        {% endfor %}
      {% endif %}
    {% endfor %}
  </div>

  <div id="noResults" class="no-results" style="display: none;">
    🕵️ 没有找到匹配的项目
  </div>
</div>

<style>
/* 基础样式 */
.docs-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 2rem 1rem;
}

.filter-input {
  width: 100%;
  padding: 12px 20px;
  margin-bottom: 2rem;
  border: 2px solid #eaecef;
  border-radius: 8px;
  font-size: 16px;
}

.docs-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  gap: 1.5rem;
}

.doc-card {
  border: 1px solid #eaecef;
  border-radius: 12px;
  padding: 1.5rem;
  transition: all 0.2s ease;
  height: 100%;
}

.doc-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 6px 20px rgba(0, 0, 0, 0.05);
}

h3 {
  margin: 0 0 1rem;
  color: #24292e;
}

.doc-meta {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 1rem;
  font-size: 0.9em;
}

.update-time {
  color: #6a737d;
}

.repo-link {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  color: #0969da;
  text-decoration: none;
}

.github-icon {
  fill: currentColor;
}

.doc-excerpt {
  color: #6a737d;
  margin: 1rem 0;
  min-height: 60px;
}

.doc-link {
  display: block;
  text-align: center;
  padding: 8px 16px;
  background: #f6f8fa;
  border-radius: 6px;
  color: #24292e;
  text-decoration: none;
  border: 1px solid #eaecef;
}

.no-results {
  text-align: center;
  padding: 2rem;
  font-size: 1.2rem;
  color: #6a737d;
}
</style>

<script>
// 安全搜索功能
document.addEventListener('DOMContentLoaded', function() {
  const searchInput = document.getElementById('searchInput');
  const docItems = document.querySelectorAll('.doc-item');
  const noResults = document.getElementById('noResults');

  function filterDocs() {
    const searchTerm = searchInput.value.trim().toLowerCase();
    let visibleCount = 0;

    docItems.forEach(item => {
      const title = item.dataset.title;
      if (title.includes(searchTerm)) {
        item.style.display = 'block';
        visibleCount++;
      } else {
        item.style.display = 'none';
      }
    });

    noResults.style.display = visibleCount > 0 ? 'none' : 'block';
  }

  searchInput.addEventListener('input', filterDocs);
});
</script>