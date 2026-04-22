---
title: "Hugo 主题开发入门指南"
date: 2026-04-22T14:00:00+08:00
draft: false
categories:
  - 开发指南
tags:
  - hugo
  - 主题开发
---

想要让你的静态站点与众不同，最好的方法就是开发一个属于自己的 Hugo 主题。本文将带你了解 Hugo 主题的基础结构和开发流程。

## 1. 创建你的第一个主题

在项目根目录下，使用 Hugo 命令行工具可以快速生成主题的骨架模板：

```bash
hugo new theme my-custom-theme
```

这会在 `themes/my-custom-theme` 目录下生成一组基本文件，包括布局文件、静态资源目录和配置文件 `theme.toml`。

## 2. 理解布局 (Layouts) 的查找顺序

Hugo 使用一种非常灵活的布局查找机制。当你渲染一个页面时，Hugo 会按照特定的顺序在 `layouts/` 目录下寻找模板。

基本规则是：**根目录 `layouts/` 优先于主题 `themes/my-custom-theme/layouts/`**。

- `layouts/index.html`：首页模板
- `layouts/_default/single.html`：单篇文章的默认模板
- `layouts/_default/list.html`：列表页面（如分类、标签或博客文章列表）的默认模板

## 3. 基础页面结构

通常，我们可以通过 `baseof.html` 来定义整个网站的基础 HTML 结构，再结合 `blocks` 让其他页面继承它。

在 `layouts/_default/baseof.html` 中：

```html
<!DOCTYPE html>
<html lang="{{ .Site.LanguageCode }}">
<head>
    <meta charset="UTF-8">
    <title>{{ block "title" . }}{{ .Site.Title }}{{ end }}</title>
</head>
<body>
    {{ partial "header.html" . }}
    
    <main>
        {{ block "main" . }}{{ end }}
    </main>

    {{ partial "footer.html" . }}
</body>
</html>
```

然后在 `layouts/_default/single.html` 中继承并填充它：

```html
{{ define "main" }}
  <article>
      <h1>{{ .Title }}</h1>
      <div>{{ .Content }}</div>
  </article>
{{ end }}
```

## 4. 主题配置参数

在 `theme.toml` 中填写你的主题信息，同时你可以在主题的 `hugo.toml` 中预设一些参数（Params），供用户在自己的网站中开启或关闭某些功能。

```toml
[params]
  showAuthor = true
  footerText = "Copyright 2026"
```

在模板中读取参数：
```html
{{ if .Site.Params.showAuthor }}
  <p>作者：{{ .Params.author | default .Site.Params.author }}</p>
{{ end }}
```

通过这些简单的步骤，你就能开始构建出独一无二的 Hugo 主题了！