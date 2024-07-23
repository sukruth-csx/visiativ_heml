# Use Ubuntu 22.04 as the base image
FROM ubuntu:22.04

# Create the workspace directory
RUN mkdir -p /workspace

COPY install-process-2024.0.0-linux-x64.run /workspace/install-process-2024.0.0-linux-x64.run
RUN chmod +x /workspace/install-process-2024.0.0-linux-x64.run

# Run the installer in unattended mode
RUN /workspace/install-process-2024.0.0-linux-x64.run --installer-language en --mode unattended


# Create directories
RUN mkdir -p /opt/VisiativProcess/wildfly/modules/org/mysql/main
RUN mkdir -p /opt/VisiativProcess/configurator/lib

# Copy the necessary files
COPY mysql-connector-java-5.1.48.jar /opt/VisiativProcess/wildfly/modules/org/mysql/main/mysql-connector-java-5.1.48.jar
COPY module.xml /opt/VisiativProcess/wildfly/modules/org/mysql/main/module.xml
COPY mysql-connector-java-5.1.48.jar /opt/VisiativProcess/configurator/lib/mysql-connector-java-5.1.48.jar

COPY config.properties /opt/VisiativProcess/config.properties


# Expose any necessary ports (example port)
EXPOSE 8080


# Set the entrypoint to run both scripts
CMD ["/bin/bash", "-c", "/opt/VisiativProcess/applyconfig.sh && /opt/VisiativProcess/start.sh"]
# ENTRYPOINT ["some-command"]
