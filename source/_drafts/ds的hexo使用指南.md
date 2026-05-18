---
title: ds的hexo使用指南
tags:
---
了解 Hexo 的基本指令，是高效管理博客的基础。我把最常用的几个都整理在了下面，可以把它当作一个快速参考手册来用。

### 📝 新建内容 (`new`)

这个命令用于创建新的文章、页面或草稿。

```bash
hexo new [layout] <title>
```
*   **`hexo new "我的文章"`**: 创建一篇新文章。默认布局是 `post`，文件会生成在 `source/_posts` 目录下。
*   **`hexo new page about`**: 创建一个新页面，常用于“关于”或“友链”等独立页面。会在 `source` 目录下新建一个 `about` 文件夹，并生成 `index.md` 文件。
*   **`hexo new draft "草稿标题"`**: 创建一篇草稿，草稿默认不会在博客中显示。
*   **`hexo publish "草稿标题"`**: 将草稿发布，并移至 `source/_posts` 目录。

#### 📌 `new` 命令的常用选项

| 选项 | 说明 | 示例 |
| :--- | :--- | :--- |
| `-p, --path` | 自定义新文章的路径，而非使用默认的 `:title.md`。 | `hexo new page -p about/me "关于我"` |
| `-r, --replace` | 如果存在同名文章，将其替换。 | `hexo new -r "已有文章"` |
| `-s, --slug` | 自定义文章的URL别名。 | `hexo new -s my-post "我的文章"` |

### 🚀 生成与预览 (`generate`, `server`)

这两个命令是本地开发和调试的核心，`g` 负责构建，`s` 负责展示。

**生成静态文件 (`generate`)**
这个命令会把你的 Markdown 文件和主题样式编译成浏览器能直接识别的 HTML、CSS 和 JS 文件。
```bash
hexo generate   # 基本用法
hexo g          # 简写形式
```

**选项**：
- `-d, --deploy`: 文件生成后立即部署网站。
- `-w, --watch`: 监视文件变动，一旦有修改就自动重新生成。
- `-f, --force`: 强制完全重新生成文件，而不是使用缓存进行增量生成。

**启动本地服务器 (`server`)**
这个命令会在本地启动一个服务器，生成一个和线上完全一样的预览环境，可以在这里实时查看文章的效果。
```bash
hexo server     # 基本用法，启动本地服务器，默认地址 http://localhost:4000/
hexo s          # 简写形式 
```

**选项**：
- `-p, --port`: 指定端口，用于解决端口被占用的问题。
- `-s, --static`: 仅使用 `public` 目录中的静态文件提供服务，不重新生成。
- `-l, --log`: 启用日志输出，方便调试。

### ☁️ 部署与清理 (`deploy`, `clean`)

这是让博客真正上线或维护环境干净的关键指令。

*   **部署** (`deploy`): 将生成的网站文件推送到 GitHub Pages 等代码托管平台，这样别人就能通过网址访问你的博客了。
    ```bash
    hexo deploy   # 将本地博客部署到远程仓库
    hexo d        # 简写形式
    hexo d -g     # 等价于先执行 hexo generate，再执行 hexo deploy，是更新博客最常用的命令之一
    ```

*   **清理** (`clean`): 清除缓存文件 `db.json` 和已生成的 `public` 文件夹。当修改了配置或遇到奇怪的问题时，运行这个可以保证重新生成时环境是全新的。
    ```bash
    hexo clean    # 清除缓存
    ```

### 📄 管理配置与信息 (`config`, `list`, `version`)

这几个指令主要负责查看和管理博客的基本信息。

*   **查看配置** (`config`): 查看或修改根目录下的 `_config.yml` 配置文件。
    ```bash
    hexo config           # 列出所有站点配置
    hexo config title     # 查看站点标题
    hexo config title "我的博客"  # 修改站点标题为“我的博客”
    ```

*   **查看信息** (`list`, `version`): 查看网站路由和 Hexo 版本信息。
    ```bash
    hexo list route       # 列出所有路由（即所有生成的页面路径）
    hexo version          # 查看 Hexo 及其依赖的版本号
    ```

### 💡 其他实用指令

除了上面介绍的，还有一些可能用到的高级功能或指令：

*   **初始化** (`init`): 这是创建一个全新 Hexo 站点的起点，会生成所有必须的文件和文件夹结构。
    ```bash
    hexo init [folder]    # [folder] 是可选参数，用于指定新建博客文件夹的名称
    ```
*   **渲染** (`render`): 手动渲染指定的 Markdown 或其他格式的文件，并输出到指定位置。
*   **迁移** (`migrate`): 用于从其他博客平台（如 WordPress、Jekyll）迁移内容到 Hexo。
*   **安全模式** (`--safe`): 在启动时禁用加载所有插件和脚本，用于排查是否由某个插件引发的问题。
    ```bash
    hexo --safe           # 以安全模式运行 Hexo 命令
    ```

希望这份指南能帮助你更顺畅地管理博客～