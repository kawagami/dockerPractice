FROM mysql:8.0.26

#####################################
# Set Timezone
#####################################

COPY my.cnf /etc/mysql/conf.d/my.cnf
RUN chmod 644 /etc/mysql/conf.d/my.cnf

ENV MYSQL_ROOT_PASSWORD=root

CMD ["mysqld"]

EXPOSE 3306
