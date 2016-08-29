FROM ubuntu:16.04
MAINTAINER jiacheng du "cleverdove4@163.com"
ENV REFRESHED_AT 20160820
RUN apt-get -y update 
RUN apt-get install -y mysql-server

RUN /etc/init.d/mysql start \
    && mysql -uroot -e "grant all privileges on *.* to 'root'@'%' identified by '1';" \
    && mysql -uroot -e "grant all privileges on *.* to 'root'@'localhost' identified by '1';" 

RUN sed -Ei 's/^(bind-address|log)/#&/' /etc/mysql/my.cnf \
    && echo 'skip-host-cache\nskip-name-resolve' | awk '{ print } $1 == "[mysqld]" && c == 0 { c = 1; system("cat") }' /etc/mysql/my.cnf > /tmp/my.cnf \
    && mv /tmp/my.cnf /etc/mysql/my.cnf

EXPOSE 3306  
CMD ["/usr/bin/mysqld_safe"]


