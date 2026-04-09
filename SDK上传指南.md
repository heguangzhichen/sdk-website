# VoiceSDK 下载站 - SDK 文件上传指南

> 本指南说明如何将真实的 SDK 文件上传到 GitHub Releases，并配置下载链接。

---

## 📋 上传流程概览

```
上传 SDK 文件到 GitHub Releases
        ↓
GitHub 自动生成下载 URL
        ↓
在后台管理平台填入下载链接
        ↓
前台网站立即生效
```

---

## 第一步：准备 SDK 文件

将每个平台的 SDK 文件整理好，建议命名格式：

```
VoiceSDK_Windows_v2.3.1.zip
VoiceSDK_Kylin_ARM_v2.3.1.zip
VoiceSDK_UnionTech_X86_v2.3.1.zip
VoiceSDK_Android_v2.3.1.zip
```

> 建议压缩成 `.zip` 格式，减少文件体积。

---

## 第二步：创建 GitHub Release

### 方法 A：网页操作（推荐新手）

1. 打开你的 GitHub 仓库页面
2. 点击 **Releases** → **Create a new release**

   ![Releases 位置示意]

3. 填写信息：
   - **Tag version**：`v2.3.1`（版本号）
   - **Release title**：`VoiceSDK v2.3.1 正式版`
   - **Description：更新说明（可选）

4. **拖拽上传**你的 SDK 文件到上传区域

   ```
   ✅ VoiceSDK_Windows_v2.3.1.zip
   ✅ VoiceSDK_Kylin_ARM_v2.3.1.zip
   ✅ VoiceSDK_UnionTech_X86_v2.3.1.zip
   ✅ VoiceSDK_Android_v2.3.1.zip
   ```

5. 点击 **Publish release**

### 方法 B：GitHub CLI（适合有命令行经验）

```bash
# 安装 GitHub CLI（如果没有）
winget install GitHubCLI

# 登录
gh auth login

# 创建 release 并上传文件
gh release create v2.3.1 \
  --title "VoiceSDK v2.3.1 正式版" \
  --notes "离线语音识别及合成 SDK" \
  ./VoiceSDK_Windows_v2.3.1.zip \
  ./VoiceSDK_Kylin_ARM_v2.3.1.zip \
  ./VoiceSDK_UnionTech_X86_v2.3.1.zip \
  ./VoiceSDK_Android_v2.3.1.zip
```

---

## 第三步：获取下载链接

Release 发布后，GitHub 会自动生成下载链接。格式如下：

```
https://github.com/{用户名}/{仓库名}/releases/download/{版本号}/{文件名}
```

**示例**（假设用户名是 `mycompany`，仓库是 `sdk-website`，版本是 `v2.3.1`）：

| 平台 | 下载链接 |
|------|---------|
| Windows | `https://github.com/mycompany/sdk-website/releases/download/v2.3.1/VoiceSDK_Windows_v2.3.1.zip` |
| 麒麟 ARM | `https://github.com/mycompany/sdk-website/releases/download/v2.3.1/VoiceSDK_Kylin_ARM_v2.3.1.zip` |
| 统信 X86 | `https://github.com/mycompany/sdk-website/releases/download/v2.3.1/VoiceSDK_UnionTech_X86_v2.3.1.zip` |
| 安卓 | `https://github.com/mycompany/sdk-website/releases/download/v2.3.1/VoiceSDK_Android_v2.3.1.zip` |

> ⚠️ 记得把上面链接中的 `mycompany`、`sdk-website`、`v2.3.1` 换成你实际的值！

---

## 第四步：在后台填入下载链接

1. 打开后台管理平台 → **SDK 版本管理**
2. 点击每个平台卡片的「编辑」按钮
3. 将对应的 GitHub 下载链接粘贴到「下载链接」输入框

   ```
   例：https://github.com/mycompany/sdk-website/releases/download/v2.3.1/VoiceSDK_Windows_v2.3.1.zip
   ```

4. 点击「保存」

---

## 第五步：验证前台效果

打开前台网站 `index.html`，点击「立即下载」，确认：
- ✅ 文件可以正常下载
- ✅ 下载统计数字增加
- ✅ 版本号、更新时间显示正确

---

## 🔄 更新 SDK 版本（重复操作）

1. 上传新版本文件到同一个 Release（追加文件），**或**新建一个 Release（推荐）
2. 在后台管理平台 → **SDK 版本管理** → 编辑对应平台 → 修改版本号和下载链接
3. 保存后前台自动更新

---

## ❓ 常见问题

**Q: GitHub 在国内下载速度慢怎么办？**

A: 可以使用以下镜像加速服务，将 `github.com` 替换为：
- `ghproxy.com`（国内代理）
- `mirror.ghproxy.com`
- `download.fastgit.org`

例如：`https://ghproxy.com/https://github.com/mycompany/sdk-website/releases/download/v2.3.1/VoiceSDK_Windows_v2.3.1.zip`

**Q: 一个 Release 可以放多少文件？**

A: GitHub 单个 Release 总大小限制为 **2GB**，建议每个 SDK 包控制在 500MB 以内。

**Q: 如何删除旧版本的 SDK 文件？**

A: 在 GitHub 仓库 → Releases → 点击具体 Release → 可以删除整个 Release 或其中的单个文件。
