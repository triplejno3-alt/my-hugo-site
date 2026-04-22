# My Hugo Site

这是一个基于 [Hugo](https://gohugo.io/) 构建的静态网站项目。

## 项目结构

以下是当前项目的核心源码目录结构：

```text
.
├── .clinerules/          # Cline 专属指导规则
│   ├── hugo-site-development.md
│   └── sspai-article-writing.md
├── archetypes/           # 内容模板目录
│   └── default.md        # 默认前置元数据模板
├── assets/               # 需要经过 Hugo 资产管道处理的文件（空）
├── content/              # 网站内容目录
│   └── posts/            # 博客文章集合
│       ├── github-readme-guide.md
│       ├── hello-world.md
│       ├── hugo-advanced-tutorial.md
│       ├── hugo-deploy-github-pages.md
│       ├── hugo-quick-start-tutorial.md
│       ├── hugo-seo-performance.md
│       ├── hugo-theme-development.md
│       └── sspai-newcomer-introduction.md
├── data/                 # 存放数据文件（空）
├── i18n/                 # 国际化翻译字典文件（空）
├── layouts/              # 自定义模板目录
│   ├── index.html        # 首页模板
│   └── _default/
│       ├── baseof.html   # 基础页面结构
│       ├── list.html     # 列表页（导航页）模板
│       └── single.html   # 单篇文章模板
├── public/               # Hugo 编译后生成的静态站点文件（自动生成，勿手动修改）
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
- `layouts/`：控制网站的前台视觉展现，包含主页、列表页、文章详情等核心模板。
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