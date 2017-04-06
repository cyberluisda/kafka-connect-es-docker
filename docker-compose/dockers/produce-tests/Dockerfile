FROM cyberluisda/kafka-ctrl:0.10.1.1

MAINTAINER Luis David Barrios Alfonso (luisdavid.barrios@agsnasoft.com)

# ADD iVi agents configurations
RUN mkdir -p /var/data/producer
COPY files/* /var/data/producer/
CMD [ \
  "produce", \
  "tests_json", \
  "--file",  "/var/data/producer/doc-with-key.csv", \
  "--property", "parse.key=true", \
  "--property", "key.separator=," \
]
