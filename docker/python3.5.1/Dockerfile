FROM ubuntu:16.04
MAINTAINER jiacheng du "cleverdove4@163.com"
ENV REFRESHED_AT 20160820
RUN apt-get -y update && apt-get -y install vim
RUN apt-get -y install curl 
RUN apt-get -y install git-core

RUN git clone git://github.com/yyuu/pyenv.git ~/.pyenv
RUN echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc
RUN echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
RUN echo 'eval "$(pyenv init -)"' >> ~/.bashrc
RUN exec $SHELL 

RUN apt-get -y build-dep python2.7

RUN /root/.pyenv/bin/pyenv install 3.5.1
#RUN ln -sf /bin/bash /bin/sh

RUN /root/.pyenv/bin/pyenv global 3.5.1 

RUN /root/.pyenv/shims/pip install --upgrade pip
RUN /root/.pyenv/shims/pip install aiohttp 
RUN /root/.pyenv/shims/pip install jinja2 
RUN /root/.pyenv/shims/pip install aiomysql 

RUN apt-get install -y mysql-client
RUN apt-get install -y libmysqlclient-dev
ADD awesome /srv/awesome

RUN apt-get install -y nginx
#ADD nginx/nginx.conf  /etc/nginx/nginx.conf
ADD /static/awesome /etc/nginx/sites-available/
WORKDIR /etc/nginx/sites-enabled
RUN ln -s /etc/nginx/sites-available/awesome .
RUN mkdir /srv/awesome/log/

WORKDIR /srv/awesome/www


EXPOSE 9000 8080
