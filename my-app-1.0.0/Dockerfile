FROM openjdk:8

RUN curl --location --remote-name https://www-us.apache.org/dist/maven/maven-3/3.6.0/binaries/apache-maven-3.6.0-bin.tar.gz && \
    tar -xzvf apache-maven-3.6.0-bin.tar.gz && \
    rm apache-maven-3.6.0-bin.tar.gz && \
    mv apache-maven-3.6.0 /opt

ENV PATH "/opt/apache-maven-3.6.0/bin:${PATH}"

RUN useradd --create-home maven
COPY "${PWD}" /home/maven
RUN chown --recursive maven:maven /home/maven

USER maven
WORKDIR /home/maven

EXPOSE 8080
RUN mvn clean package

ENTRYPOINT ["java", "-jar", "target/my-app-1.0.0.jar"]
