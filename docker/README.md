# docker

<!--help-->

**docker** / **docker -- help**

**docker *command* --help**



**docker run ubuntu echo "hello world"**



**docker run -i -t ubuntu bash**

*-i 交互*

*-t 开启一个term*

*--name name*

*-P 将容器内部使用的网络端口随机映射到我们使用的主机上或者设置 -P 5000:5000*



**docker run -d ubuntu sh -c "while true; do echo hello world; sleep 1; done"**

*container id*



**docker ps**



**docker logs *container id***

*-f 类似tail -f*



**docker stop *container id***



**docker start *container id***

**docker restart *container id***



**docker rm -f *container id***



**docker container prune**



**docker pull ubuntu**

**docker pull ubuntu:15.10**



<!--进入容器-->

**docker attach *container id***

**docker exec -it *container id* bash**



**docker port *container id***



**docker top *container id***



<!--查看 Docker 的底层信息-->

**docker inspect *container id***



**images list**

docker images



**search image**

docker search httpd



**remove image**

docker rei *image_name*



**create docker network**

docker network create -d bridge test-net

*-d network type*

docker network ls--



**connect to docker network**

docker run -itd --name test1 --network test-net ubuntu bash

docker run -itd --name test2 --network test-net ubuntu bash. 



ping test2

*apt-get update / apt install iputils-ping*



docker login/logout



**dockerfile**

*FROM:定制的镜像都是基于 FROM 的镜像*<br>

*RUN:用于执行后面跟着的命令行命令*<br>

- *RUN <命令行命令>*

- *RUN ["可执行文件", "参数1", "参数2"]*

  *eg:RUN ["./test.php", "dev", "offline"] 等价于 RUN ./test.php dev offline*

*&&连接命令*--    

 

**build image ** 

docker build -t nginx:text .

