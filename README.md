# Pulse · Live Salary Calculator

[arknove.com](https://arknove.com/) — 一个免费的实时薪资计算器。输入月薪、每日工时和每月工作天数,即可看到收入按秒实时跳动。支持人民币 / 美元、中文 / 英文。

A free live salary calculator that watches your earnings tick up second by second in real time. Supports USD/CNY and English/Chinese.

## 项目结构 / Structure

```
.
├── index.html              # 主页 / Main calculator (EN)
├── about.html / .zh.html   # 关于 / About
├── contact.html / .zh.html # 联系 / Contact
├── privacy.html / .zh.html # 隐私政策 / Privacy
├── terms.html / .zh.html   # 服务条款 / Terms
├── blog/                   # 博客文章 / Blog posts
├── ads.txt                 # Google AdSense
├── robots.txt
├── sitemap.xml
├── _redirects              # 已合并文章的 301 / 301s for merged-away posts
└── og-image.png            # 社交分享图 / Open Graph image
```

## 网址规范 / URL convention

站点对外一律使用**无后缀**网址(`/privacy`、`/about.zh`),而非 `/privacy.html`。
canonical、hreflang、sitemap 和站内链接都必须使用这一形式。

跳转由 Cloudflare Pages 内置处理:`/privacy` 由磁盘上的 `privacy.html` 提供服务,
而 `/privacy.html` 会 **308** 单跳到 `/privacy`。Google 对 308 和 301 的处理完全
一致,无需干预。

`_redirects` **只用于内置行为覆盖不到的跳转**,也就是页面被删除或合并、URL 不再对应
任何文件的情况——内置跳转只负责 `.html` 去后缀,删掉的页面会直接 404 并丢掉已累积的
索引信号。当前它承载的是三篇被合并文章的 301。

不要用它去重写内置跳转已经处理好的路径。此前试过一次,规则**确实生效**(状态码从内置
的 308 变为 301,增删可稳定复现),但 Google 对 308 和 301 处理一致,等于只换了个状态码,
毫无收益,后来删掉了。

Canonical URLs are **extensionless** (`/privacy`, `/about.zh`). Every canonical
tag, hreflang annotation, sitemap entry, and internal link must use that form.

Redirects are handled by Cloudflare Pages itself: `/privacy` is served from
`privacy.html` on disk, and `/privacy.html` makes a single **308** hop to
`/privacy`. Google treats 308 and 301 identically, so nothing needs doing.

`_redirects` is **only for hops the built-in behavior cannot make** — pages that
were deleted or merged away, whose URLs no longer map to any file. The built-in
redirect only strips `.html`; a removed page just 404s and throws away whatever
index signal it had earned. It currently carries the 301s for three merged posts.

Do not use it to restate hops the built-in behavior already handles. That was
tried once and the rules **did take effect** (the status code went from the
built-in 308 to 301, reproducibly, on adding and removing the file), but Google
treats 308 and 301 identically, so it changed a status code and nothing else.
It was removed again.

## 部署 / Deployment

纯静态站点,通过 **Cloudflare Pages** 托管:

- 生产分支 / Production branch: `main`
- 框架预设 / Framework preset: None
- 构建命令 / Build command: 无 (none)
- 构建输出目录 / Build output directory: `/` (root)

每次推送到 `main` 分支,Cloudflare Pages 会自动重新部署。自定义域名 `arknove.com` 在 Cloudflare 控制台管理。

Static site hosted on **Cloudflare Pages**. Pushing to `main` triggers an automatic redeploy. The custom domain is managed in the Cloudflare dashboard.

## 本地预览 / Local preview

```bash
python3 -m http.server 8000
# 然后打开 / then open http://localhost:8000
```
