FROM ubuntu:16.04
MAINTAINER jiacheng du "cleverdove4@163.com"
ENV REFRESHED_AT 20160820
RUN apt-get -y update && apt-get -y install vim

RUN apt-get -y install nginx

ADD awesome /etc/nginx/sites-available/


WORKDIR /etc/nginx/sites-enabled
RUN ln -s /etc/nginx/sites-available/awesome .

ADD static/awesome /srv/awesome
ADD nginx/nginx.conf  /etc/nginx/nginx.conf
RUN mkdir /srv/awesome/log/


EXPOSE 80

