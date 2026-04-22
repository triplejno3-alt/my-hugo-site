# My Hugo Site

这是一个基于 [Hugo](https://gohugo.io/) 构建的静态网站项目。

## 项目结构说明

当前项目的目录结构及其作用如下：

- `archetypes/`：内容模板目录。当您使用 `hugo new` 命令创建新内容时，Hugo 会使用此目录下的模板（如 `default.md`）生成带有默认前置元数据（Front Matter）的文件。
- `assets/`：用于存放需要经过 Hugo 资产管道（Asset Pipeline）处理的文件，如 Sass/SCSS、JavaScript 或需要压缩、指纹处理的图片。
- `content/`：网站的内容目录。所有 Markdown 格式的文章和页面都放在这里。例如 `content/posts/` 存放博客文章。
- `data/`：用于存放数据文件（如 JSON, YAML, TOML 格式）。Hugo 可以在生成页面时读取这些数据。
- `i18n/`：国际化（i18n）配置目录。存放多语言翻译字典文件。
- `layouts/`：自定义模板目录。存放在此处的模板会覆盖主题（Theme）中的同名模板。可以用来定制网站布局。
- `public/`：Hugo 编译后生成的静态站点文件默认存放在这里。**注意：此目录下的文件由 Hugo 自动生成，请勿手动修改。**
- `static/`：静态资源目录。存放在这里的所有文件或目录在构建时会原封不动地复制到 `public/` 目录的根节点下。适合存放不需要处理的图片、CSS、JS、favicon 等。
- `themes/`：主题目录。下载或添加的 Hugo 主题均存放在此。
- `hugo.toml`：Hugo 项目的主配置文件，用于配置网站基础信息、菜单、参数以及指定主题等。

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
在 `content/posts/` 目录下创建一篇名为 `my-new-post.md` 的新文章。

### 构建静态站点

```bash
hugo
```
生成最终的静态站点文件，输出到 `public/` 目录。可以配合 `--minify` 参数压缩 HTML/CSS/JS 等资源：

```bash
hugo --minify
```
