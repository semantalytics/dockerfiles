FROM centos:7

ENV STARDOG_HOME=/stardog-data STARDOG_SERVER_JAVA_ARGS="-Xmx8g -Xms8g -XX:MaxDirectMemorySize=2g"

# Install stardog from its repo
RUN curl http://packages.stardog.com/rpms/stardog.repo > /etc/yum.repos.d/stardog.repo && \
    yum install -y stardog

# User data directory for $STARDOG_HOME
VOLUME ["/stardog-data"]
# Potential volume for license key to be lifted at runtime
VOLUME ["/stardog-license"]

COPY resources/stardog-license-key.bin /stardog-license/stardog-license-key.bin

EXPOSE 5820

# remove locks, always replace license key if present, start stardog
CMD rm -f $STARDOG_HOME/system.lock || true && \
    cp -f /stardog-license/stardog-license-key.bin $STARDOG_HOME 2>/dev/null || true && \
/opt/stardog/bin/stardog-admin server start --foreground
