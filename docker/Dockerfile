FROM centos:8

RUN yum update -y && \
    yum install -y git wget which less vim zip unzip && \
    yum install -y java-11-openjdk-devel && \
    yum clean all

RUN wget https://services.gradle.org/distributions/gradle-6.7-bin.zip -P /tmp && \
    unzip -d /opt/gradle /tmp/gradle-*.zip && \
    rm -rf /tmp/gradle-*.zip

ADD ./gradle.sh /etc/profile.d/gradle.sh
RUN chmod 755 /etc/profile.d/gradle.sh

WORKDIR /root
RUN git clone https://github.com/Kakoen/valheim-save-tools.git && \
    cd valheim-save-tools && \
    source /etc/profile.d/gradle.sh && \
    gradle build
