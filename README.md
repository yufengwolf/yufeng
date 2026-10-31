# 御风 · 个人作品集

纯静态个人站，零构建，可直接部署到 Cloudflare Pages / GitHub Pages。主页由根目录 `index.html` 管理项目列表；每个内置工具放在自己的目录中，例如二维码工具位于 `qrcode/`。暗色主题并内置亮/暗切换。

## 页面结构

- 顶栏：品牌标识 + 导航 + 主题切换（记忆到 `localStorage`）
- Hero：个人主张 + 品牌光球 + 滚动进度条
- 统计条：状态 / 已收录数量 / 部署方式
- 作品区：分类筛选（全部 / 工具 / 作品 / 关于）+ 关键词搜索 + 卡片网格
- 关于区：自我介绍 + 标签 + 联系方式卡片
- 页脚：版权 + 回到顶部

## 新增一个作品（扩展方式）

打开 `index.html`，找到脚本顶部的 `PROJECTS` 数组，往里加一条对象即可：

```js
{
  title: "作品名称",
  category: "工具",          // 工具 / 作品 / 关于
  status: "online",          // online 在线 / pending 待上线
  url: "https://xxx.pages.dev/", // 外部链接或仓库内相对路径；留空则不跳转
  desc: "一句话简介。",
  tags: "搜索关键词 空格分隔",
  color: "#7C9CFF",          // 图标主题色
  icon: '<rect x="3.5" y="5" width="17" height="14" rx="2"></rect>' // 24x24 内联 SVG 路径
}
```

卡片会自动渲染、参与筛选与搜索，无需改任何 HTML 结构。有 `url` 的作品整张卡片可点击跳转（新标签页），无 `url` 的显示 `Soon` 且不可点击。仓库内的简单工具可用相对路径，例如 `qrcode/index.html`；复杂或独立部署的项目则填 Cloudflare Pages 完整网址。

二维码生成器位于 `qrcode/index.html`，相关脚本和许可证放在 `qrcode/vendor/`，无需依赖外部 CDN。建议二维码只存链接，内容上限为 500 UTF-8 字节（不是字符数）；支持设置前景色和背景色，低对比度或图案较密时会提示扫码风险。PNG 尺寸可调至 1,600px，但长内容仍会形成密集图案，优先使用短链接。

## 主题与配色

- 默认暗色；右上角按钮可切换亮色，选择会记住。
- 配色集中在 `:root` 与 `[data-theme="light"]` 的 CSS 变量里，改 `--accent` / `--grad` 即可换主色。

## 部署到 Cloudflare Pages

1. 把 `yufeng` 目录推送到 GitHub 仓库。
2. Cloudflare 控制台 → **Workers & Pages** → **Create application** → **Pages** → **Connect to Git**。
3. 选仓库；构建命令留空，构建输出目录填 `.`。
4. 部署。之后更新 `index.html` 并推送，Pages 自动重新部署。

主页无后端、数据库或环境变量依赖。
