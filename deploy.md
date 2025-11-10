安装 GoReleaser：

```shell
brew install goreleaser/tap/goreleaser
go install github.com/goreleaser/goreleaser@latest
```



基本命令：

```shell
# 1. 检查配置文件是否正确
goreleaser check

# 2. 本地测试构建（不发布）
goreleaser release --snapshot --clean

# 3. 本地测试构建（保留之前的构建产物）
goreleaser release --snapshot

# 4. 正式发布（需要 git tag）
goreleaser release --clean

# 5. 正式发布（保留之前的构建产物）
goreleaser release
```

完整发布流程：

```shell
# 1. 确保代码已提交
git add .
git commit -m "Release v1.0.0"

# 2. 创建并推送 tag
git tag -a v1.0.0 -m "Release version 1.0.0"
git push origin v1.0.0

# 3. 运行 GoReleaser 发布
goreleaser release --clean

本地测试构建（推荐用于开发）：
# 构建所有平台的二进制文件到 dist/ 目录
goreleaser build --snapshot --clean

# 只构建当前平台
goreleaser build --single-target --snapshot --clean
```

其他有用命令：

```shell
# 查看 GoReleaser 版本
goreleaser --version

# 查看帮助
goreleaser --help
goreleaser release --help

# 初始化配置文件（如果没有）
goreleaser init

# 生成补全脚本
goreleaser completion bash
goreleaser completion zsh
```


环境变量：

```shell
# GitHub Token（用于发布到 GitHub Releases）
export GITHUB_TOKEN="your_github_token"

# 或者在发布时指定
GITHUB_TOKEN="your_token" goreleaser release --clean
```

