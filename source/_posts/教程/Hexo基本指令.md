---
title: Hexo基本指令
tags: [Hexo, 博客]
categories:
  - 教程
date: 2026-05-21 22:05:00
---


## 自用来查表的...
**其中有AI辅助**
### new的使用方法
* **`hexo new "我的文章"`**: 创建一篇新文章。默认布局是 `post`，文件会生成在 `source/_posts` 目录下。
* **`hexo new page about`**: 创建一个新页面，会在 `source` 目录下新建一个 `about` 文件夹，并生成 `index.md` 文件。
* **`hexo new draft "草稿标题"`**: 创建一篇草稿，草稿不会在博客中显示。
* **`hexo publish "草稿标题"`**: 将草稿发布，并移至 `source/_posts` 目录。*(但是我做了文件分类，不能用这个)*

**利用文件的分类：**
**`hexo new -p \第一级\第二级\文章名 "文章名"`**: 会在`source/_posts/第一级/第二级`目录下生成`文章名.md`文件。
例如：`hexo new -p \比赛\AtCoder\ABC458 "ABC458" `

### 其他常用指令
* **`hexo g`**: 生成网页的静态文件，运行后会在hexo根目录生成`/public`文件夹，里面放着静态文件。
* **`hexo clean`**: 清除缓存文件 `db.json` 和已生成的 `public` 文件夹。当修改了配置或遇到奇怪的问题时，运行这个可以保证重新生成时环境是全新的。
* **`hexo s`**: 启动本地服务器，默认地址为 http://localhost:4000/ ，可以进行本地的预览。