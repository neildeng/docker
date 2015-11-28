FROM neildeng/centos-jdk:7-8u66

MAINTAINER "NEILDENG" <"Neil.Deng.g@gmail.com">

ENV ES_VER 2.1.0

RUN wget --no-check-certificate https://download.elasticsearch.org/elasticsearch/release/org/elasticsearch/distribution/tar/elasticsearch/${ES_VER}/elasticsearch-${ES_VER}.tar.gz

RUN tar -xf elasticsearch-${ES_VER}.tar.gz \
    && rm elasticsearch-${ES_VER}.tar.gz \
    && mv elasticsearch-${ES_VER} elasticsearch \
    && adduser elasticsearch \
    && chown -R elasticsearch:elasticsearch elasticsearch 

#RUN elasticsearch/bin/plugin install license
#RUN elasticsearch/bin/plugin install marvel-agent
RUN elasticsearch/bin/plugin install mobz/elasticsearch-head
RUN elasticsearch/bin/plugin install lmenezes/elasticsearch-kopf
RUN elasticsearch/bin/plugin install jettro/elasticsearch-gui

EXPOSE 9200 9300

ENV CLUSTER_NAME ES
ENV UNICAST_HOSTS ''

#USER elasticsearch 

CMD su -c "elasticsearch/bin/elasticsearch -Des.network.host=0.0.0.0 -Des.cluster.name=${CLUSTER_NAME} -Des.node.name=\${HOSTNAME} -Des.discovery.zen.ping.multicast.enabled=false -Des.discovery.zen.ping.unicast.hosts=${UNICAST_HOSTS}" elasticsearch


