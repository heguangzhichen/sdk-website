# VoiceSDK 下载站

> 企业级离线语音识别及合成 SDK 官方下载网站 + 后台管理平台

## 📁 项目结构

```
sdk-website/
├── index.html              ← 前台下载网站
├── admin/
│   ├── index.html          ← 后台管理平台
│   └── login.html          ← 后台登录页
├── .github/
│   └── workflows/
│       └── deploy.yml      ← GitHub Actions 自动部署配置
├── .gitignore
├── README.md               ← 你在看的这个
└── SDK上传指南.md           ← 如何上传 SDK 文件到 GitHub Releases
```

## 🚀 快速部署（3步完成）

### 第1步：上传代码到 GitHub

```bash
# 1. 在 GitHub 上新建一个空白仓库，名字比如：sdk-website
# 2. 克隆到本地
git clone https://github.com/你的用户名/sdk-website.git
cd sdk-website

# 3. 把本项目所有文件复制进去，然后：
git add .
git commit -m "Initial commit"
git push origin main
```

### 第2步：开启 GitHub Pages

1. 进入你的 GitHub 仓库 → **Settings** → **Pages**
2. **Source** 选择：**GitHub Actions**
3. 保存即可（无需其他配置）

> 部署会自动进行，等待 1~2 分钟后，网站就会上线：
> `https://你的用户名.github.io/sdk-website/`

### 第3步：上传 SDK 文件并配置下载链接

参考 👉 `SDK上传指南.md`，把真实的 SDK 文件上传到 GitHub Releases，然后在后台管理平台填入对应的下载链接。

---

## 🔧 后台管理

- **访问地址**：`你的网站地址/admin/login.html`
- **默认账号**：`admin`
- **默认密码**：`admin123`

登录后可管理：
- SDK 版本信息（版本号、更新时间、包大小）
- 下载链接（指向 GitHub Releases）
- 网站文字内容
- 下载统计

---

## 📦 更新网站代码

修改代码后 `git push`，GitHub Actions 会自动重新部署，等待约 1~2 分钟生效。

---

## 💡 后续扩展建议

| 需求 | 建议 |
|------|------|
| 想要自定义域名 | 在 GitHub Pages Settings 绑定域名（需 DNS 配置） |
| SDK 文件太大 | 压缩成 zip/rar，或分卷压缩 |
| 想国内访问更快 | 后续可迁移到腾讯云 COS 香港节点 + Cloudflare |
| 需要多管理员 | 后续可接入 GitHub OAuth 登录 |
