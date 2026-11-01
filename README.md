# App 隐私与支持网站

多个 App 共用一个 Git 仓库。纯静态 HTML/CSS，无依赖、无分析脚本。

## 目录

- `public/index.html`：应用目录。
- `public/audio-mixer/privacy.html`、`support.html`：调音台中英文隐私政策、技术支持。
- `public/lipfit/`：从现有 lipfit-privacy 复制的原文，旧仓库和旧线上链接不改动。
- `public/assets/site.css`：新页面共享样式。
- `.github/workflows/pages.yml`：只部署 public，文档和脚本不公开到网站。

## 本地预览

```sh
python3 -m http.server 8080 --directory public
```

## 部署

将仓库推送到 GitHub 后，在 Settings → Pages 中选择 GitHub Actions。
如果使用 butoften/app-privacy，则上线后的路径为：

- https://butoften.github.io/app-privacy/audio-mixer/privacy.html
- https://butoften.github.io/app-privacy/audio-mixer/support.html

以上为部署目标，只有 Pages 部署成功后才可填写到 App Store Connect。

## 新增 App

1. 在 public 下创建稳定英文 slug（如 my-app）。
2. 添加 privacy.html 和 support.html，按真实功能说明数据处理、权限、存储、删除和联系方式，不直接套用“不收集数据”。
3. 使用 ../assets/site.css；内部链接保持相对路径。
4. 更新 public/index.html，检查中英文、日期、邮箱与移动端布局。
5. 推送 main，待 Pages 工作流成功，确认两个线上 URL 可访问后填入 App Store Connect。
6. 发布后保持 slug 和文件名稳定；迁移旧站点时先保留旧网址，避免商店链接失效。

当前调音台隐私内容基于本地源码核对：素材本地处理、局域网配对、续传缓存；TestFlight 数据处理独立说明。后续新增统计、广告、账号或云服务时需同步更新。
