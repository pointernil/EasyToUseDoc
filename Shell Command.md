args# Shell 常用指令

## 1. 匹配文件内容
```bash
# 在.xml中，找到带有string的行
find ./*.xml | xargs grep -wn --color <string>
```

## 2. mysql

### 2.1 升级数据库
```bash
# 导出所有数据库
mysqldump -uroot -p --all-databases --default-character-set=utf8 > /home/databases.sql

# 升级数据库
systemctl stop mysqld
rpm -ivh *.rpm --force --nodeps

# 初始化数据库
mysqld --initialize --console

# 目录授权
chown -R mysql:mysql /var/lib/mysql

# 服务启动
systemctl start mysqld

# 修改密码
cat /var/log/mysqld.log | grep password
mysql -u root -p
ALTER USER 'root'@'localhost' IDENTIFIED BY '123456';
# 导入数据库
mysql -uroot -p < /home/databases.sql
```

```
cat 2023-08-0*/zlog.* | grep "proto type=" | awk -F "|=" '{for(i=1;i<=NF;i++){if($i~"proto type"){print $(i+1)}}}' > test.log
sort test.log | uniq -c > protonum.txt
```