# docker

## docker

**docker** / **docker -- help**

**docker *command* --help**

**docker run ubuntu echo "hello world"**

**docker run -i -t ubuntu bash**

- *-i 交互*
- *-t 开启一个term*
- *--name name*

- *-P 将容器内部使用的网络端口随机映射到我们使用的主机上或者设置 -P 5000:5000*

**docker run -d ubuntu sh -c "while true; do echo hello world; sleep 1; done"**

- *container id*

**docker ps**

**docker logs *container id***

- *-f 类似tail -f*

**docker stop *container id***

**docker start *container id***

**docker restart *container id***

**docker rm -f *container id***

**docker container prune**

**docker pull ubuntu**

**docker pull ubuntu:15.10**

**docker attach *container id***

**docker exec -it *container id* bash**

**docker port *container id***

**docker top *container id***

**docker inspect *container id***

**docker images**

**docker search httpd**

**docker rei *image_name***

**docker network create -d bridge test-net**

- *-d network type*
- *docker network ls*

**docker run -itd --name test1 --network test-net ubuntu bash**

**docker run -itd --name test2 --network test-net ubuntu bash**

**ping test2**

- *apt-get update / apt install iputils-ping*

**docker login/logout**

## dockerfile

*FROM:定制的镜像都是基于 FROM 的镜像*

*RUN:用于执行后面跟着的命令行命令*

- *RUN <命令行命令>*

- *RUN ["可执行文件", "参数1", "参数2"]*

  *eg:RUN ["./test.php", "dev", "offline"] 等价于 RUN ./test.php dev offline*

*&&连接命令*

**docker build -t nginx:text .**

## docker-machine

**docker-machine ls**

**docker-machine create --driver virtualbox test**

**docker-machine ip test**

**docker-machine stop test**

**docker-machine start test**

**docker-machine ssh test**

**docker swarm init --advertise-addr *ip***

**docker info**

**docker service create --replicas 1 --name helloworld alpine ping docker.com**

**docker service ps helloworld**

**docker service inspect --pretty helloworld**

**docker service scale helloworld=2**

**docker service rm helloworld**

**docker service create --replicas 1 --name redis --update-delay 10s redis:3.0.6**

**docker service update --image redis:3.0.7 redis**

**docker node ls**

**docker node update --availability drain swarm-work1**

