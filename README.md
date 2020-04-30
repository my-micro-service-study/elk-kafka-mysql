# 安装logstash同步mysql数据到elasticsearch
* 在mac上配置如下信息
~~~
mkdir ~/etc
vi ~/etc/timezone
在里面输入 America/New_York 保存退出
~~~
* 修改`es-logstash-mysql/plugins/config/sync_table1.cfg`和`es-logstash-mysql/plugins/config/sync_table2.cfg`中的jdbc,替换为要同步的mysql数据库信息和表信息
* 修改`elasticsearch`中es地址,同时修改logstash中es地址
* 查看logstash日志
~~~
docker logs -f --tail=200 logstash
~~~
* 在elasticsearch安装ik分词器插件
~~~
// 进入容器es
docker exec -it elasticsearch /bin/bash
// 使用bin目录下的elasticsearch-plugin install安装ik插件
bin/elasticsearch-plugin install https://github.com/medcl/elasticsearch-analysis-ik/releases/download/v6.6.2/elasticsearch-analysis-ik-6.6.2.zip
//退出容器
exit
// 再重启下容器
docker restart elasticsearch
~~~