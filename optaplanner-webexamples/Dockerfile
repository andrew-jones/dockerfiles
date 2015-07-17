FROM tomcat:8
MAINTAINER Andrew Jones <andrewj@softint.com.au>

ENV OPTAPLANNER_VERSION 6.2.0.Final

    # Fetch the optaplanner package
RUN wget --no-verbose --output-document /opt/optaplanner.zip \
        http://download.jboss.org/optaplanner/release/$OPTAPLANNER_VERSION/optaplanner-distribution-$OPTAPLANNER_VERSION.zip && \
    # unzip optaplanner
    unzip /opt/optaplanner.zip -d /opt && \
    # Remove default Tomcat web apps
    rm -fr /usr/local/tomcat/webapps/* && \
    # Recreate ROOT dir
    mkdir /usr/local/tomcat/webapps/ROOT && \
    # mv war into Tomcat root
    mv /opt/optaplanner-distribution-$OPTAPLANNER_VERSION/webexamples/binaries/optaplanner-webexamples-$OPTAPLANNER_VERSION.war \
        /usr/local/tomcat/webapps/ROOT/optaplanner.war && \
    # Unzip war
    cd /usr/local/tomcat/webapps/ROOT && unzip optaplanner.war && \
    # Clean up optaplanner and war
    rm -fr /opt/optaplanner* && \
    rm -f /usr/local/tomcat/webapps/ROOT/optaplanner-webexamples-$OPTAPLANNER_VERSION.war
