# 使用docker搭建本地mysql
把当前文件放到任意一个文件
# 运行开启
```
docker-compose up -d
```
# 关闭
```
docker-compose down
```
# mysql 进入mysql 创建一个test的远程连接账号 （本地不需要）
```
CREATE USER 'test'@'%' IDENTIFIED WITH mysql_native_password BY '123456';
GRANT ALL PRIVILEGES ON *.* TO 'test'@'%';
FLUSH PRIVILEGES;
```
# mysql 远程连接(进入容器创建账号)
```
地址 127.0.0.1
端口 3306
账号 test
密码 123456
```
# 数据库导入问题

###### 导入遇到 数据库字段类型【timestamp】默认值 CURRENT_TIMESTAMP datetime value: '0000-00-00 00:00:00'
1. 查询
```
SHOW VARIABLES LIKE 'sql_mode%';
```
2. 先复制出一份
```
删除里面的 NO_ZERO_IN_DATE,NO_ZERO_DATE（每个人的sql_mode 不一样 先查询自己的在替换）
```
3. 结果  mysql 配置文件自行修改【mysqld.cnf】
```
[mysqld]
sql_mode="ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,ERROR_FOR_DIVISION_BY_ZERO,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION"
#sql_mode="ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION"
```
