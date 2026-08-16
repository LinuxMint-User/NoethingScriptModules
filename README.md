# NoethingScriptModules

NoethingScript 官方模块仓库，供模块管理器 `nsm` 安装模块使用（需解释器 2.8+）。GitHub 主仓库 + Gitee 镜像，按序回退。

## 安装

```bash
node dist/noethingScript-Interpreter.js nsm -- install <包名>
```

安装后脚本中 `use <包名> from main` 即可调用。镜像列表查看/生成：`nsm -- repos` / `nsm -- init`。

## 结构

- `catalog/`：仓库清单（`nsmp gen-catalog` 自动生成）
- `packages/`：模块压缩包 `{包}@{版本}-v{适配}.zip`

包列表、双镜像与维护流程见解释器仓库 [module-system/self-host-repo-guide.md](https://github.com/LinuxMint-User/NoethingScript/blob/main/module-system/self-host-repo-guide.md)。
