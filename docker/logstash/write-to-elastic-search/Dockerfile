FROM logstash:7.17.28

RUN rm -f /usr/share/logstash/config/logstash-sample.conf
RUN rm -f /usr/share/logstash/pipeline/logstash.conf

COPY spring.log /my-log/

COPY logstash.conf /usr/share/logstash/config/
COPY logstash.conf /usr/share/logstash/pipeline/

#http://localhost:9200/_search?pretty&size=1000