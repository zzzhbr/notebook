1.负载均衡
反向代理：nginx
负载均衡：lvs；haproxy

2.web服务器（架构）：
nginx+php（php）
nginx+uwsgi（python）
nginx+TOMCAT（java）
nginx+自己写

3后端
1） 数据库
MySQL
MongoDB
2） 存储
NFS
3） 缓存
redis/memcached
a.缓存数据库内容
b.做session会话共享

4.运维
1）连接系统的通道：OpenVPN/PPTP
2）跳板机：jumpserver
3）批量管理工具
密钥认证+pssh/ansible/saltstack


面试基础套路：
自我介绍
1.用户在浏览器中输入网址：

# 问题1：

反向代理与负载均衡区别？

