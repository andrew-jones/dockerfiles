FROM ubuntu:14.04
MAINTAINER Andrew Jones <andrewj@softint.com.au>

ENV OPENJDK_VERSION 1.7.0
ENV OPTAPLANNER_VERSION 6.2.0.Final

# Update list of packages
RUN apt-get update && apt-get upgrade -y && \
    apt-get install -y wget unzip openjdk-7-jre && \
    apt-get clean

    # Fetch the wso2is package
RUN wget --output-document /opt/optaplanner.zip \
        http://download.jboss.org/optaplanner/release/$OPTAPLANNER_VERSION/optaplanner-distribution-$OPTAPLANNER_VERSION.zip && \
    # Install binary
    unzip /opt/optaplanner.zip -d /opt && \
    # symlink
    mv /opt/optaplanner-distribution-$OPTAPLANNER_VERSION /opt/optaplanner && \
    # Clean wso2am
    rm -f /opt/optaplanner.zip

RUN export uid=1000 gid=1000 && \
    mkdir -p /home/developer && \
    echo "developer:x:${uid}:${gid}:Developer,,,:/home/developer:/bin/bash" >> /etc/passwd && \
    echo "developer:x:${uid}:" >> /etc/group && \
    echo "developer ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/developer && \
    chmod 0440 /etc/sudoers.d/developer && \
    chown ${uid}:${gid} -R /home/developer

USER developer
ENV HOME /home/developer

WORKDIR /opt/optaplanner

# Setup environment
ENV JAVA_HOME /usr/lib/jvm/jre-$OPENJDK_VERSION-openjdk.x86_64

CMD ["/opt/optaplanner/examples/runExamples.sh"]
