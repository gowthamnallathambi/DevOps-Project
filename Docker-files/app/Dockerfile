FROM openjdk:11 AS BUILD_IMAGE
LABEL "Project"="Vprofile"
LABEL "Author"="Gowtham_Nallathambi"
RUN apt update && apt install maven -y
RUN git clone https://github.com/gowthamnallathambi/DevOps-Project.git
RUN cd DevOps-Project && git checkout docker && mvn install

FROM tomcat:9-jre11

RUN rm -rf /usr/local/tomcat/webapps/*

COPY --from=BUILD_IMAGE DevOps-Project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]