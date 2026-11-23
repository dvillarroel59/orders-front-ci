FROM jenkins/jenkins:2.541.3-jdk17

ARG JENKINS_VERSION=2.541.3
ENV CASC_JENKINS_CONFIG=/var/jenkins_casc/jenkins.yaml \
    JAVA_OPTS=-Djenkins.install.runSetupWizard=false

COPY plugins.txt /usr/share/jenkins/ref/plugins.txt
RUN jenkins-plugin-cli --plugin-file /usr/share/jenkins/ref/plugins.txt --jenkins-version ${JENKINS_VERSION}

COPY jenkins.yaml /var/jenkins_casc/jenkins.yaml

USER jenkins
