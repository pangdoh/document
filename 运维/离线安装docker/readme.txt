rpm -ivh libcgroup-*
rpm -ivh docker-engine-1.7.1-1.el7.centos.x86_64.rpm
启动docker
service docker start
docker -v

打包系统：
tar -cvpf /tmp/system.tar --directory=/ --exclude=proc --exclude=sys --exclude=dev --exclude=run --exclude=boot .
导入系统：
cat system.tar | docker import - ubuntu:16.4.1
1.
cat system.tar | docker import - centos:7.1
2.
docker import system.tar centos2:7.1

导入成功后，接下去就可以运行容器了
docker run -t -i ubuntu:16.4.1 /bin/bash

映射端口启动
docker run -t -i -p 2222:22 ubuntu:16.4.1 /bin/bash
docker run -t -i -p 2222:22 -p 2121:21 ubuntu:16.4.1 /bin/bash

将容器a404c6c174a2 保存为新的镜像,并添加提交人信息和说明信息。
docker commit -a "pdh" -m "ubuntu" a404c6c174a2  ubuntu:16.4.1

退出容器：
exit
或者
Ctrl+P+Q

查看容器：docker ps -a

查看运行的容器：docker ps

重启容器：docker restart 容器ID

查看本地的镜像
docker images

删除镜像
docker rmi <image id>