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
