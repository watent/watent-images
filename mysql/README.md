## MySQL 主从
    
### 构建主从镜像
    
    1.分别在主从Dockerfile目录执行
        sudo docker build -t watent/mysql_master:5.7 .
        sudo docker build -t watent/mysql_slave:5.7 .
    
    2.分别运行主从容器
    
    sudo docker run \
    --name mysql-master \
    --privileged=true \
    -v /home/mysql/etc/master:/etc/mysql/conf.d \
    -v /home/mysql/master-data:/var/lib/mysql \
    -p 3306:3306 \
    -e MYSQL_ROOT_PASSWORD=root \
    -d watent/mysql-master:5.7
    
    sudo docker run \
    --name mysql-slave \
    --privileged=true \
    -v /home/mysql/etc/slave:/etc/mysql/conf.d \
    -v /home/mysql/slave-data:/var/lib/mysql \
    -p 3307:3306 --link mysql-master:master \
    -e MYSQL_ROOT_PASSWORD=root \
    -d watent/mysql-slave:5.7