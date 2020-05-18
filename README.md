# macPostgreSql
1、下载

https://ftp.postgresql.org/pub/source/v10.7/postgresql-10.7.tar.gz
文档
http://www.postgres.cn/docs/10/index.html

2、make

3、sudo make install

4、创建用户，不能用root权限创建 pgsql 数据库

创建用户

sudo dscl . -create /Users/pgsql
sudo dscl . -create /Users/pgsql UserShell /bin/bash
sudo dscl . -create /Users/pgsql RealName “pgsql. User”

注意 UniqueID必须唯一

sudo dscl . -create /Users/pgsql UniqueID “1002”
sudo dscl . -create /Users/pgsql PrimaryGroupID 80
sudo dscl . -create /Users/pgsql NFSHomeDirectory /Users/pgsql

修改密码

sudo dscl . -passwd /Users/pgsql pgsql

5、创建目录并给权限

mkdir /usr/local/pgsql/data
sudo chown pgsql /usr/local/pgsql/data

6、切换用户（密码是 pgsql）

su pgsql

7、初始化并创建数据库

/usr/local/pgsql/bin/initdb -D /usr/local/pgsql/data
/usr/local/pgsql/bin/postgres -D /usr/local/pgsql/data >logfile 2>&1 &
/usr/local/pgsql/bin/createdb test
/usr/local/pgsql/bin/psql test
