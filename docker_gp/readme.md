# 使用docker安装greenplum
## 制作docker镜像
### 1. 从官网下载对应平台的Greenplum安装包后，准备如下Dockerfile文件：

FROM lyasper/gphost
COPY greenplum-db-5.*-rhel7-x86_64.rpm /home/gpadmin/greenplum-db.rpm
RUN rpm -i /home/gpadmin/greenplum-db.rpm
RUN chown -R gpadmin /usr/local/greenplum-db*
RUN rm -f /home/gpadmin/greenplum-db.rpm

### 2.运行如下命令创建镜像
docker build . -t mygreenplum