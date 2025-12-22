Docker离线安装

https://blog.csdn.net/weixin_42571882/article/details/134015815



Docker作为一个开源容器化平台，允许用户在隔离的环境中打包、分发和管理应用。Docker 的命令行工具docker CLI 提供了一套广泛的命令，适用于处理不同的任务，比如镜像管理、容器生命周期管理、网络配置等

**基础命令**

- `docker --version`: 显示 Docker 的版本信息。
- `docker info`: 显示 Docker 的系统信息，包括容器和镜像的数量。
- `docker login [Server]`: 用于登录到 Docker 仓库服务器。
- `docker help`: 查看更多的 Docker 命令说明或特定命令的帮助信息。

**镜像命令**

- `docker images`: 列出本地主机上的所有镜像。
- `docker pull [Image]`: 从镜像仓库拉取指定的镜像。
- `docker push [Image]`: 将本地镜像推送到镜像仓库。
- `docker build -t [Tag] .`: 根据当前目录下的 Dockerfile 创建镜像。
- `docker rmi [Image]`: 删除一个或多个镜像。
- `docker history [Image]`: 查看镜像的历史变更。

**容器命令**

- `docker ps`: 列出当前正在运行的容器。
- `docker ps -a`: 列出所有容器，包括未运行的。
- `docker run [Options] [Image]`: 创建一个新的容器并运行一个命令。
  - `[Options]`可能包括 `-d` (后台运行), `-p` (端口映射), `-e` (设置环境变量), 等等。
- `docker start [Container]`: 启动一个或多个已经停止的容器。
- `docker stop [Container]`: 停止一个运行中的容器。
- `docker restart [Container]`: 重启容器。
- `docker rm [Container]`: 删除一个或多个容器。
- `docker exec -it [Container] /bin/bash`: 进入运行中的容器并启动 Bash（对于基于 Linux 的容器）。
- `docker logs [Container]`: 查看容器的日志。

**数据卷（Volumes）命令**

- `docker volume create [Options] [Name]`: 创建一个新的卷。
- `docker volume ls`: 列出所有的卷。
- `docker volume inspect [Name]`: 显示指定卷的详细信息。
- `docker volume rm [Name]`: 删除一个或多个卷。
- `docker run -v [HostDir]:[ContainerDir]`: 运行容器时，将宿主机的目录挂载到容器的指定目录。

**网络命令**

- `docker network ls`: 列出所有网络。
- `docker network create [Options] [Name]`: 创建新的网络。
- `docker network rm [Network]`: 删除一个或多个网络。
- `docker network inspect [Network]`: 查看特定网络的详细信息。
- `docker run --network=[Network]`: 连接容器到一个特定的网络。

**系统磁盘命令**

- `docker system df`: 显示 Docker 使用的磁盘空间。
- `docker system prune`: 清理未使用的数据。