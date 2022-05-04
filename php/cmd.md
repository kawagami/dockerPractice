## 起 mysql 的 docker 指令
docker run -d -p 3306:3306 --privileged=true
-v C:\kawa\docker\mysql\log:/var/log/mysql
-v C:\kawa\docker\mysql\data:/var/lib/mysql
-v C:\kawa\docker\mysql\conf:/etc/mysql/conf.d
-e MYSQL_ROOT_PASSWORD=root
--name=mymysql
mysql
--default_character_set=utf8mb4
--collation_server=utf8mb4_unicode_ci
--character_set_server=utf8mb4
* --default_character_set=utf8mb4 直接輸入似乎無效
* 改成創建 my.cnf 並在內輸入 key value
* 後遇到在 windows 創建的檔案在 linux 的權限是 777 mysql 認為此檔案很危險而被忽略
* 使用 chmod 644 後可正常讀取

## 在公司環境下起 mysql 的指令
docker run -d -p 3306:3306 --privileged=true -v C:\kawa\docker\mysql\log:/var/log/mysql -v C:\kawa\docker\mysql\data:/var/lib/mysql -v C:\kawa\docker\mysql\conf:/etc/mysql/conf.d -e MYSQL_ROOT_PASSWORD=root --name=mymysql mysql

## 進入 mysql container 交互模式
docker exec -it mymysql /bin/bash

## 顯示設定
show VARIABLES like 'character%';
