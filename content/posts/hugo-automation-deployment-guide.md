---
title: "从手动到全自动：Hugo 站点的 GitHub Actions 部署实战"
date: 2026-04-23T09:33:14+08:00
draft: false
description: "本文将手把手教你如何利用 GitHub Actions 为你的 Hugo 站点搭建一套完整的 CI/CD 流程，实现代码一键推送、站点自动构建与发布。"
categories: ["开发指南"]
tags: ["Hugo", "GitHub Actions", "CI/CD", "自动化部署"]
---

## 引言

静态站点的魅力在于其极致的访问速度和简单的架构，但如果你仍然在本地手动运行 `hugo` 命令，然后再通过 FTP 或 Git 手动上传 `public` 目录，那么部署过程很快就会成为创作的累赘。真正的现代化工作流应该是：**你只管写字，剩下的交给自动化。**

## 准备工作：环境与权限

在开始之前，请确保你的 Hugo 项目已经托管在 GitHub 仓库中。

### 为什么选择 GitHub Actions？

作为 GitHub 原生的自动化工具，Actions 无需配置额外的 Webhooks，且对开源项目完全免费。它能直接读取你的源码，在云端虚拟机中完成构建，并安全地将产物推送到 GitHub Pages 或其他托管平台。

## 核心配置：编写部署工作流

在项目根目录下创建 `.github/workflows/deploy.yml` 文件。以下是一个经过优化的配置示例：

```yaml
name: Deploy Hugo Site
on:
  push:
    branches:
      - main  # 或者是你的主分支名

jobs:
  build-deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4
        with:
          submodules: recursive
          fetch-depth: 0

      - name: Setup Hugo
        uses: peaceiris/actions-hugo@v3
        with:
          hugo-version: 'latest'
          extended: true

      - name: Build
        run: hugo --minify

      - name: Deploy
        uses: peaceiris/actions-gh-pages@v4
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./public
```

### 关键步骤解析：
- **Submodules**: 如果你的主题是通过 Git Submodule 引入的，必须开启 `submodules: recursive`。
- **Extended Version**: 许多现代 Hugo 主题需要 `extended` 版本来处理 SCSS。
- **GITHUB_TOKEN**: 这是系统自动生成的，无需手动配置 Secrets，非常方便。

## 进阶：优化构建速度与自定义域名

### 使用缓存加速

如果你的站点文章非常多，构建时间会变长。你可以通过缓存 Hugo 的资源目录来提速。

### 自定义域名处理

如果你使用了自定义域名，请确保在 `static/` 目录下放置一个 `CNAME` 文件，或者在部署步骤中指定 `cname: yourdomain.com`，否则每次部署后 GitHub Pages 的域名设置可能会被重置。

## 结语

一次配置，终身受益。当你看到 GitHub 仓库上那个绿色的小勾缓缓亮起，而你的修改已经秒级同步到线上时，那种掌控感会让你更专注于内容创作本身。

---
*提示：建议在此处插入一张 GitHub Actions 执行成功的界面截图，展示流水线的各个环节。*
