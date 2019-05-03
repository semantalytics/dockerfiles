FROM centos:7

ENV STARDOG_HOME=/stardog
ENV STARDOG_SERVER_JAVA_ARGS="-Xmx8g -Xms8g -XX:MaxDirectMemorySize=2g"
ENV STARDOG_VERSION=6.1.1

RUN curl http://packages.stardog.com/rpms/stardog.repo > /etc/yum.repos.d/stardog.repo && \
    yum install -y stardog-6.1.1

VOLUME ["/stardog"]

RUN chcon -Rt svirt_sandbox_file_t /stardog

EXPOSE 5820

WORKDIR /opt/stardog/bin

ENTRYPOINT ["./stardog-admin", "server", "start"]

CMD ["--foreground"] 
