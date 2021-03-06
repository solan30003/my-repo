## Docker部署v18.06.1-ce 

### 1.安装
[下载docker-ce-18.06.1.ce-3.el7.x86_64.rpm](https://download.docker.com/linux/centos/7/x86_64/stable/Packages/docker-ce-18.06.1.ce-3.el7.x86_64.rpm)
* rpm安装 安装过程会自动下载所需依赖
> sudo yum install /usr/install/docker-ce-18.06.1.ce-3.el7.x86_64.rpm

安装成功后会自动创建docker用户组，但是还无用户

### 2.使用非root用户
docker要求运行在root权限下，如果要使用非root用户，可将用户添加到docker用户组，例如：
> sudo gpasswd -a hadoop docker

添加后如果当前用户是 非root用户，则需要退出并重新登录。
### 3.启动、停止
```
sudo systemctl start docker.service
sudo systemctl status -l docker.service
sudo systemctl stop docker.service
```
### 3.常用命令
[docker命令大全](http://www.runoob.com/docker/docker-command-manual.html)
```
# 构建image ，Dockerfile与在*.jar在同一个目录，并且切换到当前目录下执行
sudo docker build -t config-server:0.0.6 .
# -t 命名； -f 指定Dockerfile路径

# 登录镜像仓库
sudo docker login --username=solan8000 XXXXXX.cn-hangzhou.aliyuncs.com
# 修改镜像名称
sudo docker tag [ImageId 或 image-name:<镜像版本号>] image-name:[镜像版本号]
# 推送镜像到仓库
sudo docker push XXXXXX.cn-hangzhou.aliyuncs.com/solan-repo/image-name:[镜像版本号]
# 从仓库拉取镜像
sudo docker pull XXXXXX.cn-hangzhou.aliyuncs.com/solan-repo/image-name:[镜像版本号]
# 列出image
sudo docker images

# 运行容器
sudo docker run -it -d -p 8762:8762 --name c14-eureka-8762 --hostname h14-eureka-8762 -e "eureka.instance.instance-id=192.168.1.14:8762" -e "server.port=8762" -e "spring.profiles.active=peer1" -e "eureka.instance.hostname=192.168.1.14" -e "eureka.instance.prefer-ip-address=true" -e "eureka.instance.ip-address=192.168.1.14" -e "eureka.client.service-url.defaultZone=http://192.168.1.15:8762/eureka/,http://192.168.1.16:8762/eureka/" 4645bc620788
sudo docker run -it -d -p 8762:8762 --name c15-eureka-8762 --hostname h15-eureka-8762 -e "eureka.instance.instance-id=192.168.1.15:8762" -e "server.port=8762" -e "spring.profiles.active=peer2" -e "eureka.instance.hostname=192.168.1.15" -e "eureka.instance.prefer-ip-address=true" -e "eureka.instance.ip-address=192.168.1.15" -e "eureka.client.service-url.defaultZone=http://192.168.1.14:8762/eureka/,http://192.168.1.16:8762/eureka/" 4645bc620788
sudo docker run -it -d -p 8762:8762 --name c16-eureka-8762 --hostname h16-eureka-8762 -e "eureka.instance.instance-id=192.168.1.16:8762" -e "server.port=8762" -e "spring.profiles.active=peer3" -e "eureka.instance.hostname=192.168.1.16" -e "eureka.instance.prefer-ip-address=true" -e "eureka.instance.ip-address=192.168.1.16" -e "eureka.client.service-url.defaultZone=http://192.168.1.14:8762/eureka/,http://192.168.1.15:8762/eureka/" 4645bc620788

sudo docker run -it -d -p 8090:8090 --name c15-a-8090 --hostname h15-a-8090 -e "spring.profiles.active=prod" -e "eureka.instance.hostname=192.168.1.15" -e "eureka.instance.ip-address=192.168.1.15" -e "spring.cloud.config.uri=http://user:user@192.168.1.15:7090/" -e "eureka.client.service-url.defaultZone=http://192.168.1.14:8762/eureka/,http://192.168.1.15:8762/eureka/,http://192.168.1.16:8762/eureka/" 26448b110638
sudo docker run -it -d -p 9090:9090 --name c16-b-9090 --hostname h16-b-9090 -e "spring.profiles.active=prod" -e "eureka.instance.hostname=192.168.1.16" -e "eureka.instance.ip-address=192.168.1.16" -e "spring.cloud.config.uri=http://user:user@192.168.1.15:7090/" -e "eureka.client.service-url.defaultZone=http://192.168.1.14:8762/eureka/,http://192.168.1.15:8762/eureka/,http://192.168.1.16:8762/eureka/" 9a81e626abf3

sudo docker run -it -d -p 7090:7090 --name c15-config-7090 --hostname h15-config-7090 -v /usr/install/config:/usr/install/config -e "spring.profiles.active=native"  -e "eureka.instance.hostname=192.168.1.15" -e "eureka.instance.ip-address=192.168.1.15" 11c9824feb45
sudo docker run -it -d -p 7090:7090 --name c15-config-7090 --hostname h15-config-7090 -v /usr/install/config:/usr/install/config -e "spring.profiles.active=prod"  -e "eureka.instance.hostname=192.168.1.15" -e "eureka.instance.ip-address=192.168.1.15" -e "eureka.client.service-url.defaultZone=http://192.168.1.14:8762/eureka/,http://192.168.1.15:8762/eureka/,http://192.168.1.16:8762/eureka/" ed8cc8f27c4e

# 停止容器
sudo docker stop c14-b-8090

# 删除镜像
sudo docker rmi dcd7b2404dbb
# 删除容器(要先停止)
sudo docker rm c14-b-8090
# 删除所有容器
sudo docker rm $(docker ps -a -q)

# 列出容器,docker ps 默认列表是正在启动的容器 -a是显示所有创建的容器
sudo docker ps -a

# 查看指定容器的日志
sudo docker logs -f c14-b-8090
```