FROM openjdk:11-jre 
# we pull jre(java run time environment because since the code alread been compiled I didn't need jdk to be cost effective)
ARG DOCKERIZE_VERSION=v0.6.1
# docker build --build-arg VERSION=2   -t arg4 . => if we wanna change we can use this command in cli.
ARG EXPOSED_PORT=9090
# we use ARG because those values are not permanent it may change and it would take a lot of time for us to update all of them.
ENV SPRING_PROFILES_ACTIVE docker,mysql
# 
ADD https://github.com/jwilder/dockerize/releases/download/${DOCKERIZE_VERSION}/dockerize-alpine-linux-amd64-${DOCKERIZE_VERSION}.tar.gz dockerize.tar.gz
# works like a wget
RUN tar -xzf dockerize.tar.gz
# take tar file and open the zipped folder
RUN chmod +x dockerize
# make it executable
ADD ./target/*.jar /app.jar
# copy jar files under target folder to the container as /app.jar
EXPOSE ${EXPOSED_PORT}
ENTRYPOINT ["java", "-Djava.security.egd=file:/dev/./urandom","-jar","/app.jar"]
# Entrypoint = sabit / can not overridden
# CMD = degisken / overridden