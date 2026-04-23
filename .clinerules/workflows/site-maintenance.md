# Workflow: 站点日常维护

本工作流用于指导 Cline 协助用户进行 Hugo 站点的日常技术维护、性能优化和结构更新。

## 执行步骤 (Steps)

### 1. 状态评估
- **动作**：使用 `ask_followup_question` 询问需要进行的维护类型。
- **优化**：提供 `options` 供用户快速选择（如：性能优化、SEO 检查、同步目录树）。
- **动作**：运行 `hugo` 构建检查当前是否有报错或警告。

### 2. 结构与文档同步
- **动作**：更新 `README.md` 中的项目结构树。
- **规范**：保持树形目录具体到每一个文件。

### 3. SEO 与元数据检查
- **动作**：扫描 `content/` 目录，检查文章是否缺失必要的 Front Matter。

### 4. 验证与提交
- **动作**：运行构建并提交。
- **规范**：使用 Conventional Commits 格式。

## 关联规则
- `.clinerules/hugo-site-development.md`
