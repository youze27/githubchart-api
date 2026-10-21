# GitHub Chart API

> 将任意 GitHub 用户的贡献热力图渲染为 SVG 图像，通过 URL 直接访问，可嵌入任意网页。

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)
[![Ruby](https://img.shields.io/badge/Ruby-3.x-red.svg)](https://www.ruby-lang.org/)

## 项目简介

**GitHub Chart API** 是一个轻量级的 HTTP 服务，接收 GitHub 用户名并返回该用户过去一年的贡献热力图（Contribution Graph）SVG 图像。由于输出为标准 SVG，你可以像使用普通图片一样，将它嵌入个人网站、博客、Markdown 文档或任何支持 `<img>` 标签的环境。

本项目 Fork 自 [2016rshah/githubchart-api](https://github.com/2016rshah/githubchart-api)，并在此基础上维护。

- 仓库地址：<https://github.com/youze27/githubchart-api>
- 在线服务：`<YOUR_DEPLOY_URL>`（部署后替换为你的实际域名）

## 功能特性

- **零依赖嵌入**：返回纯 SVG，无需 JavaScript、无需认证。
- **按用户名生成**：只需替换 URL 中的用户名即可获取对应热力图。
- **自定义配色**：支持传入十六进制基色，自动生成深浅色阶。
- **轻量部署**：基于 Ruby / Sinatra，可部署至 Heroku、Vercel、Railway 或任意支持 Ruby 的平台。
- **遵循 GitHub 公开数据**：仅统计公开贡献（与 GitHub 个人主页展示规则一致）。

## 快速开始

### 基本用法

将下面的 `{username}` 替换为你的 GitHub 用户名：

```html
<img src="https://<YOUR_DEPLOY_URL>/{username}" alt="{username} 的 GitHub 贡献图" />
