# 人大金仓数据库管理系统（KingbaseES V8 R3) Docker 镜像
本项目 fork from [kingbase-es-v8-r3-docker](https://github.com/renfei/kingbase-es-v8-r3-docker) 

由于在linux环境直接使用原作者镜像出现权限问题，无法启动，所以基于原项目，修改为工作用户为root，同时增加环境变量控制数据库初始化时是否大小写敏感，数据库默认用户和密码为SYSTEM

使用的人大金仓版本号：V008R003C002B0320

原作者教程文章：[在苹果 MacOS 上基于 Docker 容器运行人大金仓（Kingbase）V8 R3 数据库的教程](https://www.renfei.net/posts/1003506)

## 拉取镜像

镜像已经上传到 Docker Hub：

### Docker Hub

[https://hub.docker.com/r/dockerarbor/kingbase](https://github.com/renfei/kingbase-es-v8-r3-docker/pkgs/container/kingbase)

## 构建镜像

如果您想自己构建镜像可参照以下操作：

```bash
git clone https://github.com/CodingArbor/kingbase-es-v8-r3-docker.git
cd kingbase-es-v8-r3-docker
docker build -t kingbase:v8r3 .
```

## 运行

```bash
docker run -d --name kingbase -p 54321:54321 -e SYSTEM_PWD=SYSTEM CASE_INSENSITIVE=true -v /opt/kingbase/data:/opt/kingbase/data -v /opt/kingbase/license.dat:/opt/kingbase/Server/bin/license.dat kingbase:v8r3
```

- --name: 容器名称
- -p: 端口映射
- -e: 默认用户SYSTEM，密码为SYSTEM；CASE_INSENSITIVE为true则大小写不敏感，不加此参数则默认大小写敏感
- -v: 挂载宿主机的一个目录，这里挂载了数据目录和license文件
