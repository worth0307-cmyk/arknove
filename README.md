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
└── og-image.png            # 社交分享图 / Open Graph image
```

## 网址规范 / URL convention

站点对外一律使用**无后缀**网址(`/privacy`、`/about.zh`),而非 `/privacy.html`。
canonical、hreflang、sitemap 和站内链接都必须使用这一形式。

跳转由 Cloudflare Pages 内置处理:`/privacy` 由磁盘上的 `privacy.html` 提供服务,
而 `/privacy.html` 会 **308** 单跳到 `/privacy`。Google 对 308 和 301 的处理完全
一致,无需干预。

本项目曾加过 `_redirects` 想把这些跳转显式声明为 301。它**确实生效**——状态码从内置
的 308 变为 301,加回和删除时可稳定复现。但 308 已经正确,改成 301 没有任何收益,而
`/_redirects` 本身返回 200(可被抓取),所以已移除。若日后要加,先想清楚要解决什么
问题:仅仅为了把 308 换成 301 是不值得的。

Canonical URLs are **extensionless** (`/privacy`, `/about.zh`). Every canonical
tag, hreflang annotation, sitemap entry, and internal link must use that form.

Redirects are handled by Cloudflare Pages itself: `/privacy` is served from
`privacy.html` on disk, and `/privacy.html` makes a single **308** hop to
`/privacy`. Google treats 308 and 301 identically, so nothing needs doing.

A `_redirects` file was tried here to declare those hops explicitly as 301s.
It **did take effect** — the status code went from the built-in 308 to 301,
reproducibly, on adding and removing it. But 308 was already correct, so the
change bought nothing, and `/_redirects` itself returned 200 (crawlable), so
it was removed. If you reach for one again, be clear what it is solving:
turning a 308 into a 301 is not worth it.

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
