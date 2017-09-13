FROM openshift/jenkins-slave-base-centos7

MAINTAINER Joao Soares <joao.soares@avantsoft.com.br>

ENV BASH_ENV=/usr/local/bin/scl_enable \
    ENV=/usr/local/bin/scl_enable \
    PROMPT_COMMAND=". /usr/local/bin/scl_enable"

COPY contrib/bin/scl_enable /usr/local/bin/scl_enable

# Install Docker
RUN yum install -y centos-release-scl-rh && \
    INSTALL_PKGS="docker" && \
    yum install -y --setopt=tsflags=nodocs $INSTALL_PKGS && \
    rpm -V $INSTALL_PKGS && \
    yum clean all -y

RUN chown -R 1001:0 $HOME && \
    chmod -R g+rw $HOME

RUN systemctl start docker && usermod -aG docker 1001

USER 1001
