FROM adoptopenjdk/openjdk11:alpine-slim

ADD eis-vocab-*.jar eis-vocab.jar
ADD run.sh run.sh

RUN sh -c 'touch /eis-vocab.jar'
RUN sh -c 'chmod +x /run.sh'

ADD daps.crt $JAVA_HOME/lib/security

RUN keytool -keystore $JAVA_HOME/lib/security/cacerts -storepass changeit -noprompt -trustcacerts -importcert -alias aisec_daps -file $JAVA_HOME/lib/security/daps.crt

ENTRYPOINT ["/run.sh"]
