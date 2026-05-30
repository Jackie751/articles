# 柒安的文章站 · 使用说明

## 仓库结构

```
Jackie751/articles/
  index.json              ← 自动生成，不要手动改
  .github/workflows/
    build-index.yml       ← 自动更新 index.json 的脚本
  Opinion/                ← 时事点评、分析报告
  Journal/                ← 电影书籍、地方分享、生活感悟
  Focus/                  ← 学习笔记、编程、会计
  Ideas/                  ← 碎碎念、人生观、奇思妙想
```

---

## 写文章流程

1. 在 Obsidian 里写 `.md` 文章
2. 文章顶部必须有 frontmatter（见下方格式）
3. 把文件放到对应文件夹，推到 GitHub
4. GitHub Actions 自动更新 `index.json`，网站自动显示

---

## Frontmatter 格式

每篇文章顶部必须有这段，否则不会显示在列表：

```
---
title: 文章标题
category: Journal
date: 2026-05-29
tags: 标签1, 标签2, 标签3
template: default
---
```

### 字段说明

| 字段 | 必填 | 说明 |
|------|------|------|
| title | ✅ | 文章标题，显示在卡片和详情页 |
| category | ✅ | 分类，填文件夹名（见下方） |
| date | ✅ | 日期，格式必须是 YYYY-MM-DD |
| tags | ❌ | 标签，用英文逗号分隔 |
| template | ❌ | 模板，不填默认暗棕色 |
| subtitle | ❌ | 副标题，显示在标题下方 |

### category 可选值

| 值       | 对应文件夹    | 颜色         |
| ------- | -------- | ---------- |
| Opinion | Opinion/ | 粉红 #ff6eb4 |
| Journal | Journal/ | 金黄 #ffd166 |
| Focus   | Focus/   | 青蓝 #00e5ff |
| Ideas   | Ideas/   | 紫色 #b47eff |

> ⚠️ category 必须和文件所在文件夹名一致，否则分类筛选会出错

---

## 模板选择

在 frontmatter 里填 `template` 字段切换模板：

### `template: default`（或不填）
- 风格：暗棕色，深色背景
- 字体：Noto Serif SC 600
- 适合：影评、深度分析、长篇文章

```
---
template: default
---
```

### `template: tegami`
- 风格：和风手账，奶油米色背景
- 字体：Shippori Mincho（日式明朝体）
- 适合：日记、随笔、生活感悟

```
---
template: tegami
---
```

---

## Markdown 语法支持

```markdown
## 二级标题（显示为 section label 样式）

# 一级标题（显示为大标题）

普通段落直接写就好。

**粗体文字**

*斜体文字*

`代码`

> 引用块，会有左边红线装饰

---（三个横线，显示为分割线）

![图片描述](图片链接)
```

> ⚠️ 图片用 Telegram 外链，格式：`![](https://你的telegram图床链接)`

---

## 图片使用

1. 把图片发到 Telegram
2. 用 Thunder 转换成外链
3. 在文章里用 `![](外链地址)` 插入

---

## 注意事项

- `index.json` 不要手动改，由 Actions 自动生成
- 文件名不要有空格，用 `-` 代替，例如 `my-article-2026.md`
- date 格式必须是 `YYYY-MM-DD`，例如 `2026-05-29`
- tags 用英文逗号分隔，不要用中文逗号
- 文章内容里不要用中文双引号 `""` 包裹 frontmatter 的值

---

## 前端仓库

`Jackie751/blogs` → Vercel 自动部署

修改前端代码推到 main 分支，Vercel 自动重新 build。

---

## 模板开发

新增模板步骤：
1. 在 `src/pages/` 新建 `ArticleXxx.jsx`
2. 在 `src/pages/Article.jsx` 里 import 并添加判断条件
3. 文章 frontmatter 填 `template: xxx` 即可使用

#情感 #人性 #恐怖片