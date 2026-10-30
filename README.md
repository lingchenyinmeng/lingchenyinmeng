# 聆尘吟梦

基于 [Hugo](https://gohugo.io/) + [PaperMod](https://github.com/adityatelange/hugo-PaperMod) 的静态博客，部署在 Cloudflare Workers（静态资源）。

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

推送到 GitHub 后，Cloudflare 会自动构建部署（约 1~3 分钟）。

## 部署配置（Cloudflare Workers Builds）

在 Worker 项目的 **Settings → Build** 里设置：

| 项 | 值 |
|---|---|
| Build command | `git submodule update --init --recursive && hugo --gc --minify` |
| Deploy command | `npx wrangler deploy` |
| Build variable `HUGO_VERSION` | `0.169.0` |

项目根目录的 `wrangler.jsonc` 已声明静态资源目录为 `./public`，
构建产物不需要提交到 Git（已加入 `.gitignore`）。

> 说明：Cloudflare 构建镜像自带 Hugo extended 0.147.7，但本项目的配置
> 使用了 0.158+ 才支持的 `locale` 写法，所以必须用 `HUGO_VERSION`
> 固定到 0.169.0。

## 待办

- [x] 站点标题、作者、首页文案
- [x] `baseURL` 指向 `https://lingchenyinmeng.com/`
- [ ] 域名实名认证通过后，绑定自定义域名
- [ ] 放一张 `static/favicon.ico`（可选）
