# 安装logstash同步mysql数据到elasticsearch
* 在mac上配置如下信息
~~~
mkdir ~/etc
vi ~/etc/timezone
在里面输入 America/New_York 保存退出
~~~
* 修改`docker/es-logstash-mysql/plugins/config/sync_table.cfg`中的jdbc,替换为要同步的mysql数据库信息和表信息
* 修改`elasticsearch`中es地址,同时修改logstash中es地址
* 查看logstash日志
~~~
docker logs -f --tail=200 logstash
~~~