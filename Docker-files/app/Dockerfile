FROM openjdk:11 AS BUILD_IMAGE

LABEL "Project" = "Vprofile"
LABEL "Author"="Arfan"

RUN apt update && apt install -y maven
RUN git clone https://github.com/arfanxn/vprofile-project-devops.git 
RUN cd vprofile-project-desktop && git checkout docker && mvn install 

FROM tomcat:9-jre11 
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE /vprofile-project-desktop/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]



