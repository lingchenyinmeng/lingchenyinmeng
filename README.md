# 我的博客

基于 [Hugo](https://gohugo.io/) + [PaperMod](https://github.com/adityatelange/hugo-PaperMod) 的静态博客，部署在 Cloudflare Pages。

## 本地写作

```powershell
hugo new posts/文章标题.md     # 新建文章
hugo server -D                 # 本地预览 http://localhost:1313
```

## 发布

```powershell
git add .
git commit -m "新文章：xxx"
git push
```

推送到 GitHub 后，Cloudflare Pages 会自动构建部署（约 1~2 分钟）。

## 部署配置（Cloudflare Pages）

| 项 | 值 |
|---|---|
| Framework preset | Hugo |
| Build command | `git submodule update --init --recursive && hugo --gc --minify` |
| Build output directory | `public` |
| 环境变量 `HUGO_VERSION` | `0.169.0` |

## 待办

- [ ] 把 `hugo.toml` 里的 `baseURL` 改成真实域名（结尾要带 `/`）
- [ ] 修改 `hugo.toml` 里的 `title`、`author`、`homeInfoParams`、GitHub 链接
- [ ] 放一张 `static/favicon.ico`（可选）
