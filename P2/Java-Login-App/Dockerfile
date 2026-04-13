FROM tomcat:9.0-jdk11

# remove default apps
RUN rm -rf /usr/local/tomcat/webapps/*

# copy WAR
COPY target/dptweb-1.0.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
