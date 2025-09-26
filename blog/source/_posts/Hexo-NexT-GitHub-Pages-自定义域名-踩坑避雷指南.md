---
title: Hexo + NexT + GitHub Pages + 自定义域名 踩坑避雷指南
date: 2025-09-26 16:37:41
tags: Hexo
categories：避坑指南系列
---

------

# Hexo + NexT + GitHub Pages + 自定义域名 踩坑避雷指南

> 三天的踩坑记录，写下来分享给后来人，也给未来的自己留个备份。

------

<!--more-->

## 1. 部署初体验：为什么本地好好的，上线就崩？

- **现象**：`hexo s` 本地一切正常，`hexo g` 推上去 GitHub Pages 就报错或者啥也没有。
- **原因**：没分清两个分支的职责。
    - `main` → 存源码（文章、主题、配置）
    - `gh-pages` → 存生成后的 `public/` 静态文件
- **解决**：
    - 生成 `public/` 后单独推送到 `gh-pages` 分支
    - 不要把 `public/` 放到 `main`，会乱套

------

## 2. 样式丢失：页面只剩纯文字

- **现象**：上线后页面乱七八糟，CSS、图片全没了。

- **原因**：Hexo 用 `_config.yml` 里的 `url` 和 `root` 拼路径，写错了。

- **修复**：

    ```yaml
    url: https://blog.jotang.uestcgal.top
    root: /
    ```

- **经验**：路径错误 = 样式全丢，第一时间检查这两个配置。

------

## 3. 仓库管理：到底哪些文件要提交？

- **现象**：一堆文件，不知道哪些该进 GitHub。

- **解决**：

    - **提交到 main 的内容**

        - `_config.yml`
        - `source/`（文章）
        - `themes/`（主题）
        - `package.json` & `package-lock.json`

    - **忽略掉的内容**

        ```gitignore
        node_modules/
        public/
        db.json
        .deploy*/
        ```

    - **`gh-pages`** 专门存放 `public/`

- **收获**：这样既能在线部署，也能随时备份源码。

------

## 4. 自动化：从手动到一键部署

- **痛点**：每次都要手动三步：提交源码 → 生成 → 推送 `public/`。
- **解决**：写一个脚本（Linux/Mac/Windows 都可以）：

```bash
# 部分示例 (Linux/Mac)
commit_msg="update blog source on $(date '+%Y-%m-%d %H:%M:%S')"
git add .
git commit -m "$commit_msg"
git push origin main
hexo clean && hexo generate
git subtree push --prefix=public origin gh-pages
```

- **效果**：只需要敲一个命令（或双击脚本），源码和部署一键搞定。

------

## 5. 成果 🎉

- 本地开发顺畅 (`hexo s`)
- 部署分支清晰 (`main` vs `gh-pages`)
- 样式不再丢失（配置正确）
- 自动化脚本节省时间
- 自定义域名生效 → `blog.jotang.uestcgal.top`

------

## 结语

这三天基本把新手最容易踩的坑都踩了一遍，回头看还挺有意思。
 如果你刚好也在折腾 Hexo + NexT + GitHub Pages，希望这份记录能帮你少掉几次坑，多花时间写文章而不是调 bug。

------

