# Yufeng 个人站点导航

这是一个纯静态个人主页，只有 `index.html`，不需要安装依赖、构建或运行服务。

## 添加站点

打开 `index.html`，在 `id="site-grid"` 的站点卡片区域复制一个 `<article class="site-card">...</article>`，然后修改：

- 标题和简介
- `data-category`：使用 `工具`、`作品` 或 `关于`
- `data-search`：填写便于搜索的关键词
- 标题链接：`<h3><a href="https://你的站点.pages.dev/" target="_blank" rel="noopener noreferrer">站点名称</a></h3>`
- 顶部状态：把 `待添加链接` 改成 `<span class="status online">在线</span>`

不需要的卡片可以直接删除。链接建议使用完整的 `https://` 地址。

## 部署到 Cloudflare Pages

1. 将 `yufeng` 目录推送到 GitHub 仓库。
2. 在 Cloudflare 控制台进入 **Workers & Pages**，选择 **Create application** → **Pages** → **Connect to Git**。
3. 选择仓库；若仓库根目录就是本项目，构建命令留空，构建输出目录填写 `.`。
4. 点击部署。后续更新 `index.html` 并推送，Pages 会自动重新部署。

也可以在 Pages 项目中上传本目录的静态文件。主页无需后端、数据库或环境变量。
