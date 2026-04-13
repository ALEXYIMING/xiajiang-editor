# MMX 公众号排版器

本地 Markdown 编辑，实时预览，一键复制到微信公众号后台。

## 功能概要

- 双栏编辑与预览，多种成文样式主题（见 `styles.js`）
- 智能粘贴（富文本转 Markdown）、图片粘贴与本地压缩（IndexedDB）
- 历史记录（浏览器本地）、会话自动保存

## 本地运行

```bash
cd <本项目根目录>
python3 -m http.server 8080
```

浏览器访问 `http://localhost:8080`（若端口占用可换其他端口）。

部署参见 [DEPLOY.md](DEPLOY.md)。

## 技术栈

Vue 3、markdown-it、highlight.js、Turndown、IndexedDB、Canvas。

## 项目结构

```
├── index.html
├── app.js
├── styles.js
├── shell.css
├── start.sh
├── DEPLOY.md
├── Dockerfile
├── nginx.conf
└── LICENSE
```

## 协议

[MIT License](LICENSE)
