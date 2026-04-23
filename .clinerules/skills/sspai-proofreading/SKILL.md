---
name: sspai-proofreading
description: 少数派 (sspai) 风格深度校对专家。专注于细节排版纠错、标点核对与结构化改进。
---

# sspai-proofreading

本技能专注于对 Markdown 文档进行“像素级”的排版校对。

## Usage
当用户需要：
- 自动识别并纠正文档中的细微排版错误。
- 确保中英文混排达到“出版级”质量。

## Steps

### 1. 像素级扫描
- 正则校验：确保中英文/数字间有空格。
- 标点校验：纠正误用的半角标点。
- 链接校验：检查行内链接前后的空格处理。

### 2. 结构化改进
- 检查 H2/H3 标题的逻辑层次。
- 验证加粗是否仅用于核心术语和按键。

## 关联规则
- `.clinerules/sspai-article-writing.md`
