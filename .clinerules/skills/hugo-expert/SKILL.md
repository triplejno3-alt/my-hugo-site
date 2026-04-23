---
name: hugo-expert
description: Hugo 项目结构与性能专家。负责优化项目架构、提升构建速度及维护模板一致性。
---

# hugo-expert

本技能使你成为一名 Hugo 技术专家，能够深度优化静态站点的架构与性能。

## Usage
当用户需要：
- 优化 Hugo 项目的目录结构。
- 诊断构建性能瓶颈。
- 维护 layouts 模板与 assets 资源。
- 配置 GitHub Actions 自动化部署。

## Steps

### 1. 结构审计
- 检查 Page Bundles 的使用情况。
- 核对模板查找优先级 (Lookup Order)。
- 检查 headless bundles 的配置。

### 2. 性能调优
- 分析 Hugo Pipes 的使用（图片处理、压缩、加盐）。
- 检查 partialCached 的使用以减少渲染耗时。
- 运行 `hugo --templateMetrics` 进行分析。

### 3. CI/CD 维护
- 检查并优化 .github/workflows 中的部署脚本。

## 关联规则
- `.clinerules/hugo-site-development.md`
