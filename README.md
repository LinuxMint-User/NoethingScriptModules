# NoethingScriptModules

NoethingScript 官方模块仓库，供 NoethingScript 的模块管理器 `nsm` 安装模块使用。GitHub 主仓库 + Gitee 镜像（[epix-xhan/NoethingScriptModules](https://gitee.com/epix-xhan/NoethingScriptModules)）按序回退，需 NoethingScript 解释器 **2.8+**。

## 包列表

| 包名 | 版本 | 适配 | 说明 |
|---|---|---|---|
| nsm | 0.1.1 | 2.8 | 模块管理器（install/update/upgrade/check/refresh/list/search/remove/repos/init，镜像回退，依赖递归安装） |
| nsmp | 0.1.0 | 2.8 | 模块打包工具（pack 自动生成 manifest 并打 zip，gen-catalog 汇总仓库清单） |
| queue | 0.1.0 | 2.8 | 队列容器（enqueue/dequeue/front/isEmpty/size） |
| set | 0.1.0 | 2.8 | 整数集合（add/remove/contains/size，元素不重复） |
| stack | 0.1.0 | 2.8 | 栈容器（push/pop/peek/isEmpty） |
| tools | 0.1.0 | 2.8 | 通用工具函数集合（依赖 stack） |

## 安装模块

```bash
# 从默认镜像安装（GitHub 主 + Gitee 镜像，按序回退）
node dist/noethingScript-Interpreter.js nsm -- install stack

# 查看当前生效镜像；一键生成镜像配置文件（避免手写 JSON）
node dist/noethingScript-Interpreter.js nsm -- repos
node dist/noethingScript-Interpreter.js nsm -- init

# 临时指定其他镜像（逗号分隔多镜像按序回退）
node dist/noethingScript-Interpreter.js nsm -- install stack --repo https://你的仓库地址
```

安装后即可在脚本中 `use` 声明并调用（如 `use stack from main`）。

## 仓库结构

```
catalog/main.manifest.json          # 仓库清单（nsmp gen-catalog 自动生成）
packages/{包}@{版本}-v{适配}.zip    # 压缩包（zip 内顶层 = 包目录，含 manifest）
```

## 维护

新增/升级包：用 nsmp 打包放入 `packages/`，重跑 `gen-catalog` 更新清单后推送。详细流程见解释器仓库的 [module-system/self-host-repo-guide.md](https://github.com/LinuxMint-User/NoethingScript/blob/main/module-system/self-host-repo-guide.md)。
