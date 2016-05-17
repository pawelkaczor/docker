# JBoss 7 image

FROM debian:jessie

MAINTAINER Pawel Kaczor <newicom@gmail.com>

RUN apt-get update && apt-get install -y wget openjdk-7-jre-headless && apt-get autoremove && apt-get autoclean
RUN wget -O /tmp/jboss.tar.gz http://download.jboss.org/jbossas/7.1/jboss-as-7.1.1.Final/jboss-as-7.1.1.Final.tar.gz && \
	tar zxf /tmp/jboss.tar.gz -C /opt && \
	mv /opt/jboss-as-7.1.1.Final /opt/jboss7 && \
	/opt/jboss7/bin/add-user.sh --silent=true admin admin*123 && \
	ln -s /opt/jboss7/standalone/deployments/ autodeploy && \
	rm -rf  /tmp/*

EXPOSE 8080 9990 9999 8787

COPY standalone.xml /opt/jboss7/standalone/configuration/
COPY standalone.conf /opt/jboss7/bin/

CMD /opt/jboss7/bin/standalone.sh -Dorg.apache.deltaspike.ProjectStage=Development -b 0.0.0.0