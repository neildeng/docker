FROM centos:7

MAINTAINER Neil Deng <neil.deng.g@gmail.com>

ENV MAIN_VER 8
ENV CPU_VER 66

ENV STD_EDITION ${MAIN_VER}u${CPU_VER}
ENV JDK jdk1.${MAIN_VER}.0_${CPU_VER}


#install required pkgs
RUN yum install -y wget tar.x86_64 \
    && yum -y clean all


#download and install jdk
RUN wget -P /opt/ --no-cookies --no-check-certificate --header "Cookie: gpw_e24=http%3A%2F%2Fwww.oracle.com%2F; oraclelicense=accept-securebackup-cookie" http://download.oracle.com/otn-pub/java/jdk/${STD_EDITION}-b17/server-jre-${STD_EDITION}-linux-x64.tar.gz \
    && tar xzf /opt/server-jre-${STD_EDITION}-linux-x64.tar.gz -C /opt \
    && rm /opt/server-jre-${STD_EDITION}-linux-x64.tar.gz

#
RUN alternatives --install /usr/bin/java java /opt/${JDK}/bin/java 2 \
    && alternatives --install /usr/bin/javac javac /opt/${JDK}/bin/javac 2\
    && alternatives --install /usr/bin/jar jar /opt/${JDK}/bin/jar 2 \
    && alternatives --set jar /opt/${JDK}/bin/jar

#
ENV JAVA_HOME /opt/${JDK}
ENV JRE_HOME /opt/${JDK}/jre 
ENV PATH $PATH:/opt/${JDK}/bin:/opt/${JDK}/jre/bin

