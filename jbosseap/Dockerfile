FROM shona/centos-jdk:7-8u65

#ENV EAP_VER 7.0.0
#ENV EAP_BUILD Alpha

RUN yum install -y unzip

ADD files/jboss-eap-7.0.0.Alpha.zip /tmp/
RUN unzip /tmp/jboss-eap-7.0.0.Alpha.zip -d /opt/jboss
RUN rm -rf *.zip

ENV EAP_HOME /opt/jboss/jboss-eap-7.0

RUN ${EAP_HOME}/bin/add-user.sh admin 1qaz@WSX --silent

RUN echo "JAVA_OPTS=\"\$JAVA_OPTS -Djboss.bind.address=0.0.0.0 -Djboss.bind.address.management=0.0.0.0\"" >> ${EAP_HOME}/bin/standalone.conf

EXPOSE 9990 9999 8080 8787

ENTRYPOINT ["/opt/jboss/jboss-eap-7.0/bin/standalone.sh"]
CMD []


