sudo sysctl -w vm.max_map_count=262144
or
nano /etc/sysctl.conf
vm.max_map_count = 262144
sysctl -p

For development mode, you can use below settings as well -

    environment:
      - discovery.type=single-node
      
docker run --name mongo -d mongo:3
docker run --name elasticsearch \
    -e "http.host=0.0.0.0" \
    -e "ES_JAVA_OPTS=-Xms512m -Xmx512m" \
    -d docker.elastic.co/elasticsearch/elasticsearch-oss:6.6.1

docker run --name graylog --link mongo --link elasticsearch \
    -p 9000:9000 -p 514:514 \
    -e GRAYLOG_HTTP_EXTERNAL_URI="http://[ublic-ip:9000"/   \
    -e GRAYLOG_ROOT_PASSWORD_SHA2=8c6976e5b5410415bde908bd4dee15dfb167a9c873fc4bb8a81f6f2ab448a918 \
    -d graylog/graylog:3.0



nano /etc/rsyslog.conf

*.* @@graylog.company:514;RSYSLOG_SyslogProtocol23Format

