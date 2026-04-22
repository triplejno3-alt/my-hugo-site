# My Hugo Site

这是一个基于 [Hugo](https://gohugo.io/) 构建的静态网站项目。

## 项目结构

以下是当前项目的完整目录结构：

```text
.
├── archetypes/           # 内容模板目录
│   └── default.md        # 默认前置元数据模板
├── assets/               # 需要经过 Hugo 资产管道处理的文件（空）
├── content/              # 网站内容目录
│   └── posts/            # 博客文章集合
│       ├── hello-world.md
│       ├── hugo-advanced-tutorial.md
│       ├── hugo-deploy-github-pages.md
│       ├── hugo-quick-start-tutorial.md
│       ├── hugo-seo-performance.md
│       └── hugo-theme-development.md
├── data/                 # 存放数据文件（空）
├── i18n/                 # 国际化翻译字典文件（空）
├── layouts/              # 自定义模板目录（空）
├── public/               # Hugo 编译后生成的静态站点文件输出目录
│   ├── 404.html
│   ├── index.html
│   ├── index.xml
│   ├── sitemap.xml
│   ├── assets/
│   │   └── css/
│   │       └── stylesheet.4b72e7725c68fccaac08b7b94b4bf3724ac8531837c6717dbd3e55b5a23b0117.css
│   ├── categories/
│   │   ├── index.html
│   │   ├── index.xml
│   │   └── 开发指南/
│   │       └── index.xml
│   ├── images/
│   │   └── gohugo-default-sample-hero-image.jpg
│   ├── page/
│   │   └── 1/
│   │       └── index.html
│   ├── posts/
│   │   ├── index.html
│   │   ├── index.xml
│   │   ├── hello-world/
│   │   │   └── index.html
│   │   └── page/
│   │       └── 1/
│   │           └── index.html
│   └── tags/
│       ├── index.html
│       ├── index.xml
│       ├── hugo/
│       │   └── index.xml
│       ├── 教程/
│       │   └── index.xml
│       └── 静态站点/
│           └── index.xml
├── static/               # 静态资源目录（空）
├── themes/               # 主题目录（空）
├── README.md             # 项目说明文件
├── hugo.toml             # 主配置文件
├── hugo.log              # Hugo 运行日志
├── .hugo_build.lock      # Hugo 构建锁文件
└── .gitmodules           # Git 子模块配置
```

### 目录作用说明

- `archetypes/`：内容模板目录。使用 `hugo new` 命令时会使用此目录下的模板生成文件。
- `content/`：网站的内容目录。所有 Markdown 格式的文章和页面都放在这里。
- `public/`：Hugo 编译后生成的静态站点文件默认存放在这里。**注意：此目录下的文件由 Hugo 自动生成，请勿手动修改。**
- `static/`：静态资源目录。构建时会原封不动地复制到 `public/` 目录中。
- `hugo.toml`：Hugo 项目的主配置文件。

## 常用命令

以下是开发和部署时常用的 Hugo 命令：

### 启动本地开发服务器

```bash
hugo server -D
```
启动本地服务器并包含标记为草稿（`draft: true`）的文章。默认访问地址为 `http://localhost:1313/`。

### 创建新文章

```bash
hugo new posts/my-new-post.md
```
在 `content/posts/` 目录下创建新文章。

### 构建静态站点

```bash
hugo --minify
```
生成最终的静态站点文件并进行压缩优化，输出到 `public/` 目录。