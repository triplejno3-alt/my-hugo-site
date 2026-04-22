---
title: "将 Hugo 站点自动化部署到 GitHub Pages"
date: 2026-04-22T14:10:00+08:00
draft: false
categories:
  - 运维部署
tags:
  - hugo
  - github actions
  - CI/CD
---

GitHub Pages 是托管静态站点的绝佳免费平台，结合 GitHub Actions，我们可以实现“只要提交代码（Git Push），网站就自动构建并上线”的自动化部署工作流。

## 1. 准备工作

首先，确保你已经将你的 Hugo 项目推送到 GitHub 仓库。如果是个人博客，通常建议仓库名称设为 `<username>.github.io`，这样访问链接会更短更优雅。

在 `hugo.toml` 中，确保你的 `baseURL` 配置正确：

```toml
baseURL = "https://<你的用户名>.github.io/"
```

## 2. 编写 GitHub Actions 工作流文件

在项目根目录下创建一个特殊的目录和文件：`.github/workflows/hugo.yaml`，并写入以下配置：

```yaml
name: Deploy Hugo site to Pages

on:
  push:
    branches:
      - main # 或者 master，视你的默认分支而定

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4
        with:
          submodules: true  # 如果你使用 Git Submodules 引入主题，请确保开启此项
          fetch-depth: 0    # 抓取完整历史记录，以便 Hugo 能正确计算 .GitInfo 等时间

      - name: Setup Hugo
        uses: peaceiris/actions-hugo@v3
        with:
          hugo-version: 'latest'
          extended: true    # 如果你的主题使用了 SCSS，需开启扩展版本

      - name: Build
        run: hugo --minify

      - name: Deploy
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./public
```

## 3. 推送并观察构建

将上面的文件提交并 Push 到 GitHub 后，点击仓库页面的 **Actions** 标签页，你会看到一个名为 `Deploy Hugo site to Pages` 的任务正在运行。

这个任务会自动执行：
1. 拉取你的源码
2. 安装最新的 Hugo 环境
3. 运行 `hugo --minify` 将静态文件生成至 `public` 目录
4. 将 `public` 目录的内容推送到名为 `gh-pages` 的特殊分支中。

## 4. 开启 GitHub Pages

任务成功后，进入仓库的 **Settings** -> **Pages**。

在 "Build and deployment" 的 "Source" 中，选择 **Deploy from a branch**。在下方的 Branch 选择下拉框中，选择刚刚构建产生的 `gh-pages` 分支，保存。

稍等片刻，访问 `https://<你的用户名>.github.io/`，你的网站就成功上线了！以后每次写完新文章只需执行 `git push`，剩下的就交给 GitHub 自动完成吧。