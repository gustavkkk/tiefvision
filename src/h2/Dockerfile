FROM openjdk:8-alpine

ENV H2_VERSION 1.4.192

COPY sudo cp create-tables.sql /root/create-tables.sql

RUN \
  sudo mkdir /opt && \
  sudo wget http://repo1.maven.org/maven2/com/h2database/h2/$H2_VERSION/h2-$H2_VERSION.jar -O /opt/h2.jar -q

EXPOSE 8082 9092

ENTRYPOINT \
  sudo java -cp /opt/h2.jar org.h2.tools.RunScript -url jdbc:h2:~/tiefvision -user sa -script /root/create-tables.sql && \
  sudo java -cp /opt/h2.jar org.h2.tools.Server -tcp -tcpAllowOthers -web -webAllowOthers
