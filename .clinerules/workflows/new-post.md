# Workflow: 创作少数派风格新文章

本工作流旨在引导 Cline 协助用户按照“少数派 (sspai) 风格”创作并发布高质量的 Hugo 博客文章。

## 触发条件 (Triggers)
- 用户表达想要写新文章的意图。
- 用户提供了一个文章标题或草稿。

## 执行步骤 (Steps)

### 1. 初始化与选题确认
- **动作**：使用 `ask_followup_question` 询问核心主题。
- **优化**：提供 `options` 供用户快速选择方向（如：效率工具、技术分享、深度评测、生活记录）。
- **目标**：确保符合 `.clinerules/sspai-article-writing.md` 中的“拒绝冗余”原则。

### 2. 生成文章结构建议
- **动作**：根据主题生成一份包含 H2 和 H3 标题的提纲。
- **规范**：遵循 `.clinerules/sspai-article-writing.md` 中的“层次分明”要求。
- **输出**：向用户展示提纲并等待确认。

### 3. 创建文件与配置元数据 (Front Matter)
- **动作**：确认提纲后，使用 `hugo new posts/<filename>.md` 创建文件。
- **交互**：在填写 `categories` 前，使用 `ask_followup_question` 并带上 `options` 展示项目中已有的分类供用户点选。
- **规范**：
    - 文件名使用连字符分隔。
    - 完善 Front Matter：填写 `title`, `description`, `categories`, `tags`。
    - `date` 自动生成。

### 4. 内容填充引导
- **动作**：根据提纲，逐段引导用户提供内容或由 Cline 根据用户提示撰写草稿。
- **规范**：
    - 检查中英文混排空格。
    - 检查全角标点符号。
    - 检查代码块高亮。
    - 确保语气“专业与亲和并重”。

### 5. 质量检查与预览
- **动作**：
    - 运行 `hugo` 命令检查构建是否报错。
    - 扫描全文，检查是否符合 `.clinerules/sspai-article-writing.md` 的硬性规范。

### 6. 自动提交与部署
- **动作**：确认内容无误后，询问用户是否提交到 Git。
- **规范**：使用 Conventional Commits 格式。

## 关联规则
- `.clinerules/sspai-article-writing.md`
- `.clinerules/hugo-site-development.md`
