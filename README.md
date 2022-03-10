# 安装
## 把当前文件放到任意一个文件
## $PWD 是当前目录的路径
# 运行开启
```

docker-compose up -d

```
# 关闭
```

docker-compose down

```

# mysql 配置文件自行修改【mysqld.cnf】

# mysql 连接
```
地址 127.0.0.1
端口 3306
账号 root
密码 123456
```
# mysql 远程连接(进入容器创建账号)
```
CREATE USER 'test'@'%' IDENTIFIED WITH mysql_native_password BY '123456';
GRANT ALL PRIVILEGES ON *.* TO 'test'@'%';
FLUSH PRIVILEGES;
地址 127.0.0.1
端口 3306
账号 test
密码 123456
```



### 如果服务器部署在线上服务器
#### 地址换成线上 ip 地址
#### 服务器记得开启 3306的限制
#### root 密码在 docker-compose.yml 文件中 可以自行修改
#### 3006端口也在 docker-compose.yml（对外端口现在是3307）
```
3307:3306
```
