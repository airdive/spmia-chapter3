FROM openjdk:8-jdk-alpine
RUN  apk update && apk upgrade && apk add netcat-openbsd && apk add curl && apk add unzip
RUN mkdir -p /usr/local/configserver
RUN echo $JAVA_HOME
RUN cd /tmp/ && \
    curl -q -L -C - -b "oraclelicense=accept-securebackup-cookie" -o jce_policy-8.zip -O http://download.oracle.com/otn-pub/java/jce/8/jce_policy-8.zip && \
    unzip jce_policy-8.zip && \
    rm -f jce_policy-8.zip && \
    yes |cp -v /tmp/UnlimitedJCEPolicyJDK8/*.jar /usr/lib/jvm/java-1.8-openjdk/jre/lib/security/
ADD  @project.build.finalName@.jar /usr/local/configserver/
ADD run.sh run.sh
RUN chmod +x run.sh
CMD ./run.sh
