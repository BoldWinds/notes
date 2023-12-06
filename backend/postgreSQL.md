# postgreSQL配置

## 1. 获取docker镜像

```bash
docker pull postgres
```



## 2.运行容器并初始化密码

```bash
docker run --name mypostgres -e POSTGRES_PASSWORD=lbw@Aft1199 -p 5432:5432 -d postgres:16.0-alpine
```

这里不知道为什么，直接拉postgres后面启动时会报错，而加了alpine的tag之后就没有问题了

## 3. 进入容器并设置

```bash
docker exec -it mypostgres bash
```

进入Postgres命令行:
```bash
psql -U postgres
```

创建用户

```sql
CREATE USER myuser WITH PASSWORD 'mypassword';
```

创建数据库并分配权限

```sql
CREATE DATABASE mydb;
ALTER DATABASE mydb OWNER TO myuser;
```

输入`\q`退出命令行，然后设置连接权限。因为docker安装的postgresql，它默认是listen所有地址的，如果想限制监听的地址，可以进行修改

## 4. 重启容器应用配置更改

```bash
docker restart mypostgres
```

