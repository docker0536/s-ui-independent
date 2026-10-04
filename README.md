# S-UI independent backup

这是 docker0536 保存的 S-UI 独立副本，源自 [alireza0/s-ui](https://github.com/alireza0/s-ui)。原项目作者、版权声明和 GPL-3.0 许可证保留。

## 安装 Linux 版本

```bash
curl -fL https://raw.githubusercontent.com/docker0536/s-ui-independent/main/install.sh -o install.sh
sudo bash install.sh v1.6.3
```

安装包来自本仓库的 [Releases](https://github.com/docker0536/s-ui-independent/releases/tag/v1.6.3)。下载后会检查 SHA256SUMS。Linux 安装包内的 s-ui.sh 已修改为使用本仓库安装和更新；可执行文件和内含库保留原发布版本。

Windows：从上述 Releases 下载对应的 ZIP，解压后按照包内说明安装。WinSW 等第三方依赖仍使用其官方来源。

## 保存和构建源码

```bash
git clone --recurse-submodules https://github.com/docker0536/s-ui-independent.git
cd s-ui-independent
```

frontend 子模块指向 [自己的前端仓库](https://github.com/docker0536/s-ui-frontend-independent)，保留主项目引用的提交。使用 main 分支中的配置；历史标签保留原始内容和地址。

如需 Docker，可从这份源码构建：

```bash
docker compose up -d --build
```

Dockerfile 仍需下载官方基础镜像、npm/Go 依赖和 SagerNet 的 libcronet。本次备份消除了安装和前端源码对原作者仓库的依赖，不是整个互联网依赖的离线镜像。未在你的服务器执行安装或验证 Docker 构建。

## 备份范围

- 主项目和前端的 Git 历史、分支和标签。
- v1.6.3 全部原发布平台安装包；Linux 管理脚本仅修改仓库地址后重新打包。
- UPSTREAM-SHA256SUMS-v1.6.3 保存原安装包校验值；Releases 的 SHA256SUMS 覆盖当前重打包文件。
- preserve-release.yml 是一次性备份工具，其下载原仓库的步骤只用于备份阶段；保存后的安装包下载与运行不需要原仓库。
- Go 的模块名称仍为 github.com/alireza0/s-ui，这是本地模块标识，构建当前源码不需要下载原作者主仓库。

已安装服务器的数据库、配置和证书需要另外备份。本仓库不包含这些私人数据。原项目文档可从提交历史查看。
