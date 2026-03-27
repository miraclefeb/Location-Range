# 地理范围圈选（高德）

运营在浏览器中圈选地理范围、导出坐标串（CSV）的静态页面，可部署在 **GitHub Pages** 或任意静态托管，便于外网访问。

## 使用

1. 打开页面根路径下的 `index.html`（部署后一般为 `https://你的域名/仓库名/`）。
2. 在「Web 端 Key」中填入高德 **Web 端（JS API）** Key，点击「初始化地图」或「定位到此处」。
3. Key 会保存在本机浏览器 `localStorage`，换电脑需重新填写。
4. 在高德控制台为该 Key 配置 **Referer 白名单**（见下文）。

## 部署到 GitHub Pages

1. 将本仓库推送到 GitHub。
2. 仓库 **Settings → Pages**：Source 选 **Deploy from a branch**，Branch 选 **main** / **（root）**，保存。
3. 等待几分钟后访问：`https://<用户名>.github.io/<仓库名>/`。

## 高德 Key 与安全

- 不要在代码仓库中提交真实 Key；页面内默认 Key 为空。
- [控制台](https://console.amap.com/dev/key/app) → 选择 Key → **安全设置** → **HTTP Referer** 白名单增加例如：
  - `https://你的用户名.github.io/*`
  - 若使用自定义域名，增加对应 `https://你的域名/*`
- 需开通：**Web 端（JS API）**；地址搜索需地理编码相关服务按控制台说明开启。

## 本地预览

将 `index.html` 与 `pin-marker-icon.png` 放在同一目录，用本地静态服务器打开（避免 `file://` 下部分环境加载异常），例如：

```bash
python3 -m http.server 8080
```

浏览器访问 `http://127.0.0.1:8080/`。

## 仓库文件

| 文件 | 说明 |
|------|------|
| `index.html` | 主页面 |
| `pin-marker-icon.png` | 大头针图标 |
| `.nojekyll` | 禁用 Jekyll，避免 GitHub Pages 误处理 |
