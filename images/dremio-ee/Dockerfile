ARG VER

FROM dremio/dremio-ee:4.1.4

USER root

COPY crt-* ./

RUN bash -c 'for i in $(ls crt-*); do keytool -noprompt -import -v -trustcacerts -alias $i -file $(pwd)/$i -keystore $JAVA_HOME/jre/lib/security/cacerts -keypass changeit -storepass changeit; done'

# https://www.vertica.com/client_drivers/9.3.x/9.3.0-0/vertica-jdbc-9.3.0-0.jar
COPY 3rdparty/vertica-jdbc-9.3.0-0.jar jars/3rdparty/

# https://github.com/luciodaza/dremio-vertica-connector.git
COPY dremio-vertica-connector/dremio-verticaarp-plugin.jar jars/

USER dremio

