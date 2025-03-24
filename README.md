# Shiroi Docker Builder

## 项目简介

Shiroi Docker Builder 是一个自动化工具，用于构建和发布 [Shiroi](https://github.com/innei-dev/shiroi) 项目的私有 Docker 镜像。该工具通过 GitHub Actions 工作流程自动监控源代码仓库的变更，并在需要时重新构建 Docker 镜像。

## 特性

- 自动检测源代码仓库的更新
- 基于 GitHub Actions 的自动化构建流程
- 支持多平台构建（目前配置为 linux/amd64）
- 自动发布到 GitHub Container Registry (GHCR)
- 使用哈希值跟踪构建状态，避免不必要的重复构建

## 工作原理

1. 工作流程定期（每天凌晨3点）或在主分支有新的提交时触发
2. 检查源代码仓库的最新提交哈希值，与上次构建的哈希值比较
3. 如果哈希值不同，则执行新的构建流程
4. 构建完成后，更新本地的哈希值记录
5. 私有 Docker 镜像会自动推送到 GHCR

## 使用方法

### Docker 镜像

您可以使用以下命令拉取最新的 Shiroi Docker 镜像：

```bash
docker login ghcr.io
docker pull ghcr.io/[username]/shiroi:latest
```

### 部署

1. 克隆此仓库
2. 配置 GitHub 个人访问令牌（PAT）(secrets.GH_PAT)
3. 激活 Workflow

## 许可证

此项目遵循 MIT 许可证发布。详情请参阅 LICENSE 文件。

## 相关链接

- [Shiroi 项目仓库](https://github.com/innei-dev/shiroi)
- [Docker 文档](https://docs.docker.com/)
- [GitHub Actions 文档](https://docs.github.com/en/actions) 