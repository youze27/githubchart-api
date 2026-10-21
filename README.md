# GitHub Chart API

> 将任意 GitHub 用户的贡献热力图渲染为 SVG 图像，通过 URL 直接访问，可嵌入任意网页。

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)
[![Ruby](https://img.shields.io/badge/Ruby-3.x-red.svg)](https://www.ruby-lang.org/)

## 项目简介

**GitHub Chart API** 是一个轻量级 HTTP 服务，接收 GitHub 用户名并返回该用户过去一年的贡献热力图（Contribution Graph）SVG 图像。由于输出为标准 SVG，你可以像使用普通图片一样，将它嵌入个人网站、博客、Markdown 文档或任何支持 `<img>` 标签的环境。

本项目 Fork 自 [2016rshah/githubchart-api](https://github.com/2016rshah/githubchart-api)，并在此基础上维护。

- 仓库地址：<https://github.com/youze27/githubchart-api>
- 公共实例：<https://ghchart.rshah.org>
- 示例热力图：<https://ghchart.rshah.org/youze27>

## 功能特性

- **零依赖嵌入**：返回纯 SVG，无需 JavaScript、无需认证。
- **按用户名生成**：只需替换 URL 中的用户名即可获取对应热力图。
- **自定义配色**：支持传入十六进制基色，自动生成深浅色阶。
- **轻量部署**：基于 Ruby / Sinatra，可部署至 Heroku、Railway、Render、Fly.io 或任意支持 Ruby 的平台。
- **遵循 GitHub 公开数据**：仅统计公开贡献，与 GitHub 个人主页展示规则一致。

## 快速开始

### 基本用法

将下面的 `{username}` 替换为你的 GitHub 用户名：

```html
<img src="https://ghchart.rshah.org/{username}" alt="{username} 的 GitHub 贡献图" />
```

例如，显示 `youze27` 的热力图：

```html
<img src="https://ghchart.rshah.org/youze27" alt="youze27 的 GitHub 贡献图" />
```

Markdown 中直接使用：

```markdown
![youze27 的 GitHub 贡献图](https://ghchart.rshah.org/youze27)
```

渲染效果：

![youze27 的 GitHub 贡献图](https://ghchart.rshah.org/youze27)

### 自定义颜色

在用户名前追加**不带 `#` 的十六进制颜色码**，服务会以该基色生成配色方案：

```html
<img src="https://ghchart.rshah.org/409ba5/youze27" alt="youze27 的蓝色 GitHub 贡献图" />
```

Markdown 中直接使用：

```markdown
![youze27 的蓝色 GitHub 贡献图](https://ghchart.rshah.org/409ba5/youze27)
```

渲染效果：

![youze27 的蓝色 GitHub 贡献图](https://ghchart.rshah.org/409ba5/youze27)

路由规则：

| 路由 | 说明 |
| --- | --- |
| `https://ghchart.rshah.org/{username}` | 使用默认绿色主题 |
| `https://ghchart.rshah.org/{hex-color}/{username}` | 使用指定基色生成主题（`hex-color` 不含 `#`） |

## 嵌入示例

### Markdown

```markdown
![GitHub 贡献图](https://ghchart.rshah.org/youze27)
```
![GitHub 贡献图](https://ghchart.rshah.org/youze27)

### VuePress / VitePress

```markdown
<img src="https://ghchart.rshah.org/youze27" alt="GitHub 贡献图" style="max-width: 100%;" />
```

### 个人网站（HTML）

```html
<figure>
  <img src="https://ghchart.rshah.org/409ba5/youze27" alt="GitHub 贡献图" />
  <figcaption>我的 GitHub 贡献热力图</figcaption>
</figure>
```



### 其他平台

项目为标准的 Ruby Web 应用，可直接部署至任何支持 Ruby 构建的环境（如 Railway、Render、Fly.io）。请确保平台能够执行 `bundle install`，并以 `ruby app.rb` 或对应的 Rack 方式启动。

部署完成后，将示例中的 `https://ghchart.rshah.org` 替换为你的实际域名即可。

## 贡献指南

欢迎提交 Issue 与 Pull Request。

1. Fork 本仓库并创建特性分支：`git checkout -b feature/your-feature`
2. 提交改动：`git commit -m "feat: describe your change"`
3. 推送分支：`git push origin feature/your-feature`
4. 在 [Pull Requests](https://github.com/youze27/githubchart-api/pulls) 页面发起合并请求

提交前请确保本地 `ruby app.rb` 可正常启动，并自测涉及的接口路由。

- 问题反馈：<https://github.com/youze27/githubchart-api/issues>
- 功能建议：<https://github.com/youze27/githubchart-api/issues>

## 许可证

本项目基于 [MIT License](./LICENSE) 发布。

## 致谢

- 原始项目：[2016rshah/githubchart-api](https://github.com/2016rshah/githubchart-api)
- 热力图渲染：[akerl/githubchart](https://github.com/akerl/githubchart)
- 数据来源：GitHub 公开贡献数据
