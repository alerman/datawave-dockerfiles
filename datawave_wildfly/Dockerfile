FROM alerman/datawave-base-jdk:8

LABEL pull="docker pull alerman/datawave-wildfly" \
      run="docker run -it alerman/datawave-wildfly" \
      description="Wildfly app server image, with DATAWAVE customizations" \
      name="Wildfly App Server Image with DATAWAVE customizations" \
      maintainer="Adam Lerman" \
      version="17.0.1-Final"

USER root

ENV WILDFLY_VERSION 17.0.1.Final \
    JBOSS_HOME /opt/jboss/wildfly \
    LAUNCH_JOBS_IN_BACKGROUND true

COPY --from=jboss/wildfly:17.0.1.Final /opt/jboss/wildfly /opt/jboss/wildfly
EXPOSE 8080

CMD ["/opt/jboss/wildfly/bin/standalone.sh","-b","0.0.0.0"]

RUN chown -R datawave:hadoop /opt/jboss && \
    chmod -R ug+rX,o-rx /opt/jboss

WORKDIR /opt/jboss/wildfly
USER datawave