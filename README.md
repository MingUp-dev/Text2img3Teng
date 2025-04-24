# 腾讯混元 AI 图像生成器

这是一个基于腾讯混元大模型的AI图像生成Web应用，通过纯静态网页方式实现，可轻松部署到GitHub Pages或腾讯云Web托管服务(Webify)。

## 项目特点

- 纯静态网页实现，无需服务器后端
- 简洁美观的用户界面
- 支持多种图片风格（日漫、动漫、油画、水墨、国风Q版）
- 前端直接调用腾讯云API生成图片

## 关于API密钥

本项目支持两种方式配置API密钥：

1. **默认方式**: 应用内置测试用API密钥，可直接使用（可能有使用限制）

2. **自定义方式**: 通过`.env-example`文件指定您自己的API密钥
   - 复制并修改`.env-example`文件，填入您的腾讯云SecretId和SecretKey
   - 应用会优先使用.env-example中的密钥，如果未找到则使用默认密钥

### 获取自己的API密钥

1. 登录[腾讯云控制台](https://console.cloud.tencent.com/)
2. 前往【访问管理】>【API密钥管理】
3. 创建或查看您的SecretId和SecretKey
4. 将获取到的密钥填入`.env-example`文件

## 在线体验

访问 [https://您的用户名.github.io/项目名称](https://您的用户名.github.io/项目名称) 立即体验

## 本地使用

本应用是纯静态网页，您可以直接在本地打开index.html使用：

1. 下载或克隆仓库到本地
2. 在浏览器中打开index.html文件
3. 输入提示词，选择风格和分辨率
4. 点击"生成图像"按钮

## 部署到GitHub Pages

1. 在GitHub上创建新仓库
2. 将本项目文件上传到仓库
3. 前往仓库设置 -> Pages
4. 在Source选项中选择"main"分支和"/(root)"文件夹
5. 点击Save，等待部署完成
6. 访问生成的GitHub Pages URL体验应用

## 部署到腾讯云Webify

### 前提条件

- 腾讯云账号（已实名认证）
- 已开通腾讯云Web应用托管服务（Webify）

### 部署步骤

1. 登录 [腾讯云Webify控制台](https://console.cloud.tencent.com/webify)
2. 选择"新建应用"
3. 选择GitHub仓库关联（需先将代码上传到GitHub）
4. 选择"静态网站"作为项目类型
5. 框架选择"自定义设置"
6. 设置以下选项：
   - 构建命令：留空
   - 输出目录：`.`（当前目录）
7. 点击"部署应用"
8. 应用部署完成后，您将获得一个可访问的URL

## CORS跨域问题解决方案

本应用使用多个可靠的CORS代理来解决浏览器的跨域限制：

1. 使用以下代理服务：
   - cors-anywhere.azm.workers.dev
   - api.allorigins.win
   - corsproxy.io
   - cors-proxy.fringe.zone

2. 如果在腾讯云Webify部署，可以考虑设置自定义响应头解决CORS问题，详见[CORS_README.md](./CORS_README.md)

## 技术实现

- 纯HTML/CSS/JavaScript实现
- 使用CryptoJS计算腾讯云API签名
- 遵循腾讯云API的TC3-HMAC-SHA256签名算法
- 使用异步任务轮询机制查询图像生成进度

## 注意事项

- 图像生成需要时间，通常为30秒至1分钟
- 使用API会产生费用，请确保腾讯云账户有足够余额
- 生成的图像可能有版权和使用限制，请遵守腾讯云服务条款

## 相关资源

- [腾讯混元大模型官方文档](https://cloud.tencent.com/document/product/1729)
- [混元生图API文档](https://cloud.tencent.com/document/product/1729/105969)
- [腾讯云Webify部署教程](https://cloud.tencent.com/document/product/1210)

## 开源协议

MIT License 