# LJH938527 的文档站

[![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-Online-brightgreen)](https://ljh938527.github.io/)
[![Jekyll](https://img.shields.io/badge/Powered_by-Jekyll-red)](https://jekyllrb.com/)

一个基于 GitHub Pages + Jekyll 构建的技术文档中心，支持多项目文档托管。

🌐 在线访问: [https://ljh938527.github.io/](https://ljh938527.github.io/)

## 🚀 功能特性

- 📚 结构化文档管理：通过 `/docs/项目名/` 路径访问不同项目文档
- 🎨 响应式设计：适配电脑/平板/手机浏览
- 🔍 SEO 优化：自动生成页面元数据
- 🖥️ 本地预览：支持实时热更新开发
- 📦 自动部署：GitHub Pages 无缝集成

## 📦 快速开始

### 本地运行

1. 克隆仓库：
   ```bash
   git clone https://github.com/ljh938527/ljh938527.github.io.git
   cd ljh938527.github.io
   ```

2. 安装依赖：
   ```bash
   bundle install
   ```

3. 启动服务：
   ```bash
   bundle exec jekyll serve --livereload
   ```
   访问 `http://localhost:4000`

### 添加新文档

1. 在 `docs` 目录下创建项目文件夹：
   ```bash
   mkdir docs/new-project
   ```

2. 编写文档（Markdown 格式）：
   ```bash
   # docs/new-project/index.md
   ---
   title: 新项目文档
   ---
   # 这里是新项目的文档内容...
   ```

3. 更新主页链接：
   编辑 `index.md` 添加导航链接：
   ```markdown
   - [新项目文档](/docs/new-project/)
   ```

## ⚙️ 配置指南

修改 `_config.yml` 自定义站点：
```yaml
# 基础配置
title: "我的知识库"
description: "技术文档与经验分享"
url: "https://ljh938527.github.io"

# 主题设置
theme: minima
plugins:
  - jekyll-feed
  - jekyll-seo-tag

# 自定义页脚
custom_footer: "© 2025 ljh938527 | 基于 Jekyll 构建"
```

## 🌍 部署说明

推送代码到 `main` 分支后，GitHub 会自动构建并发布到：
- 主页：`https://ljh938527.github.io/`
- 文档示例：`https://ljh938527.github.io/docs/project1/`

💡 提示：可在仓库 Settings → Pages 查看构建状态

## 🛠️ 开发建议

### 目录结构
```
.
├── _config.yml       # 全局配置
├── index.md          # 主页内容
├── docs/             # 文档中心
│   ├── project1/     # 项目1文档
│   └── project2/     # 项目2文档
├── _includes/        # 自定义组件
└── _sass/            # 自定义样式
```

### 扩展功能
- 添加评论系统（在 `_config.yml` 中配置 Utterances/Giscus）
- 集成 Google Analytics（配置跟踪 ID）
- 自定义域名（创建 `CNAME` 文件）

## 🤝 参与贡献
1. Fork 本仓库
2. 创建分支 (`git checkout -b feature/your-feature`)
3. 提交修改 (`git commit -am 'Add some feature'`)
4. 推送分支 (`git push origin feature/your-feature`)
5. 创建 Pull Request

## 📄 许可证
[MIT License](LICENSE) © 2025 ljh938527