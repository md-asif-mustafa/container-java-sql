FROM openjdk:11 AS BUILD_IMAGE
LABEL "Project"="Aprofile"
LABEL "Author"="Asif"
RUN apt update && apt install maven -y
RUN git clone https://github.com/md-asif-mustafa/container-java-sql.git
#ADD ../.. vprofile-project
RUN cd container-java-sql && mvn install
#RUN cd vprofile-project && mvn install


FROM tomcat:9-jre11
LABEL "Project"="Aprofile"
LABEL "Author"="Asif"
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE vprofile_project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]