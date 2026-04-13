# 部署说明（纯静态）

本项目为 **纯静态文件**（HTML / JS / CSS），无后端进程。任选一种方式发布即可。

## 1. Docker + Nginx（自建服务器 / K8s）

在项目根目录（含 `index.html` 的目录）执行：

```bash
docker build -t mmx-wechat-editor .
docker run -p 8080:80 mmx-wechat-editor
```

浏览器访问 `http://localhost:8080`。生产环境请在前面加 **HTTPS** 反向代理（如 Caddy、Traefik、云负载均衡）。

## 2. 对象存储 + CDN（阿里云 OSS / 腾讯云 COS / AWS S3）

1. 将本目录内所有文件上传到 bucket 根目录（保持 `index.html` 在根路径）。
2. 开启静态网站托管，或绑定 CDN 域名。
3. 建议：对 `index.html` 设置较短 `Cache-Control`（no-cache 或 60s），对 `*.js` / `*.css` 使用长缓存（见 [nginx.conf](nginx.conf) 中的策略）。

## 3. GitHub Pages / Cloudflare Pages / Vercel Static

- **构建命令**：无（根目录即为站点根）。
- **输出目录**：静态站点所在目录（或整仓根目录，视你如何托管而定）。
- 绑定自定义域名后，平台自动提供 HTTPS。

## 本地预览

```bash
cd <项目根目录>
python3 -m http.server 8080
# 打开 http://127.0.0.1:8080
```

## 数据说明

用户数据（正文、样式、历史）保存在浏览器 **localStorage**；图片在 **IndexedDB**。不经过服务器，部署时无需数据库。
