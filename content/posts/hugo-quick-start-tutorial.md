+++
title = 'Hugo 快速入门教程'
date = 2026-04-22T12:01:00+08:00
draft = false
tags = ["Hugo", "静态站点", "教程"]
categories = ["开发指南"]
description = "从零开始学习使用 Hugo 构建现代化静态网站的完整教程"
+++

# Hugo 快速入门教程

Hugo 是目前最快的静态网站生成器之一，使用 Go 语言编写，具有极快的构建速度和强大的功能特性。

## 🚀 安装 Hugo

### 系统要求
- 任意现代操作系统（Linux / macOS / Windows）
- Git 版本控制工具

### 安装命令

**Linux / macOS**
```bash
brew install hugo
```

**Debian / Ubuntu**
```bash
sudo apt install hugo
```

安装完成后验证版本：
```bash
hugo version
```

## 📦 创建第一个站点

1. 新建项目：
```bash
hugo new site my-hugo-site
cd my-hugo-site
```

2. 初始化 Git 仓库：
```bash
git init
```

3. 安装主题（以 PaperMod 为例）：
```bash
git submodule add https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod
```

## ✍️ 创建文章

使用 Hugo 命令创建新文章：
```bash
hugo new posts/your-first-post.md
```

文章默认使用 Markdown 格式，支持完整的 Front Matter 元数据：
```toml
+++
title = "文章标题"
date = 2026-04-22T12:00:00+08:00
draft = true
tags = ["标签1", "标签2"]
categories = ["分类"]
+++

这里是你的文章内容...
```

## 🔧 本地开发

启动开发服务器：
```bash
hugo server -D
```

访问地址：`http://localhost:1313`

特性：
- ✅ 实时热重载
- ✅ 草稿文章预览
- ✅ 自动浏览器刷新
- ✅ 构建速度极快

## 🚀 构建发布

生成生产环境静态文件：
```bash
hugo --minify
```

所有生成的静态文件将输出到 `public/` 目录，可以直接部署到任意静态文件托管服务：
- GitHub Pages
- Vercel
- Netlify
- Cloudflare Pages
- 传统 Web 服务器

## 💡 最佳实践

1. **始终使用 archetypes 模板** 统一文章格式
2. **合理使用标签和分类** 组织内容
3. **图片资源放在 static 目录** 下管理
4. **定期更新主题** 保持安全和功能更新
5. **配置 .gitignore** 排除临时文件

## 📚 相关资源

- 官方文档：https://gohugo.io/documentation/
- 主题市场：https://themes.gohugo.io/
- 社区论坛：https://discourse.gohugo.io/

---

> 本教程持续更新中，欢迎提出改进建议。