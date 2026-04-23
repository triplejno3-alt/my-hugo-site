# Workflow: 自动化部署配置

本工作流指导 Cline 协助用户为 Hugo 站点配置或维护 GitHub Actions 自动化部署流程。

## 执行步骤 (Steps)

### 1. 现状评估
- **动作**：检查项目根目录是否存在 `.github/workflows/` 目录。
- **动作**：检查 `hugo.toml` 中的 `baseURL` 是否已配置。

### 2. 配置部署脚本
- **动作**：创建或更新 `.github/workflows/hugo.yml`。
- **规范**：
    - 触发条件：`push` 到 `master` 或 `main` 分支。
    - 步骤：Checkout -> Setup Hugo -> Build -> Deploy to GitHub Pages。

### 3. 验证与提交
- **动作**：运行 `hugo` 本地构建测试。
- **动作**：提交更改并提示用户检查 GitHub 仓库的 Actions 页面。

## 关联规则
- `.clinerules/hugo-site-development.md`
