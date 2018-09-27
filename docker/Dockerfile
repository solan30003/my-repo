FROM registry.cn-hangzhou.aliyuncs.com/solan-repo/alpine-jre-8u181:1.0
ENV LANG C.UTF-8
LABEL maintainer "solan"
ADD myapp-0.0.1-SNAPSHOT.jar /usr/local/app.jar
ENTRYPOINT ["java" ,"-jar","/usr/local/app.jar"]
