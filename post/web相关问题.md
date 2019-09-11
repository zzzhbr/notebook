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
MySQL---MHA高可用
MongoDB
（keepalived主要搭配lvs，一般用作没有数据的服务进行高可用）
2） 存储
NFS
a. nfs+rsync+sersync
b. 

3） 缓存
redis/memcached
a.缓存数据库内容
b.做session会话共享

4.运维
1）连接系统的通道：OpenVPN/PPTP
2）跳板机：jumpserver
3）批量管理工具
密钥认证+pssh/ansible/saltstack


**面试基础套路：**
自我介绍
无论问到什么问题，就可以把这个带入
1.用户在浏览器中输入网址：www.baidu.com到显示页面的过程
a. DNS解析
b. 三次握手-建立连接
c. http请求报文
访问网站流程。。。
遇到的故障案例。。。
	搭建多个虚拟机主机nginx反向代理配置故障
		i: proxy_set_header(搭建多个只能用一个)
	磁盘空间不足
		i: inode
 		ii: block
定时任务运行脚本失败（java（Tomcat）网站环境）
swap不足	

d. htp响应报文
e. 四次挥手-断开连接

# 问题1：
反向代理与负载均衡区别？

