FROM oraclelinux:7-slim

ARG MYSQL_SERVER_PACKAGE=mysql-community-server-minimal-8.0.23
ARG MYSQL_SHELL_PACKAGE=mysql-shell-8.0.22

# Install server
RUN yum install -y https://repo.mysql.com/mysql-community-minimal-release-el7.rpm \
      https://repo.mysql.com/mysql-community-release-el7.rpm \
  && yum-config-manager --enable mysql80-server-minimal \
  && yum install -y wget \
  && yum install -y \
      $MYSQL_SERVER_PACKAGE \
      $MYSQL_SHELL_PACKAGE \
      libpwquality \
  && yum clean all \
  && mkdir /docker-entrypoint-initdb.d

VOLUME /var/lib/mysql

# download entrypoint and healthcheck
RUN wget https://raw.githubusercontent.com/SmartGuyy/p13_oc_pods/master/oraclelinux_MySQL-server/docker-entrypoint.sh
RUN wget https://raw.githubusercontent.com/SmartGuyy/p13_oc_pods/master/oraclelinux_MySQL-server/healthcheck.sh

# give permission to execute
RUN chmod +x start.sh
RUN chmod +x healthcheck.sh

ENTRYPOINT ["/entrypoint.sh"]
HEALTHCHECK CMD /healthcheck.sh
EXPOSE 3306 33060 33061
CMD ["mysqld"]

