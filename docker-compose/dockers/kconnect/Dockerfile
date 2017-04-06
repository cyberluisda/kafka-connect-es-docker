# We use dafault image builded by docker-compose
FROM dockercompose_kafka-connect-es

MAINTAINER Luis David Barrios Alfonso (luisdavid.barrios@agsnasoft.com)

# ADD iVi agents configurations
RUN mkdir -p /etc/kafka-connect
COPY files/config/* /etc/kafka-connect/
CMD [ "name", "tests" ]
