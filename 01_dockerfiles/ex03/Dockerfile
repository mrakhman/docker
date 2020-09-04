FROM ubuntu

RUN apt-get update && \
	apt-get install -y curl openssh-server ca-certificates postfix
	
RUN curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | bash

RUN apt-get update && \
	apt-get install -y gitlab-ce

# RUN EXTERNAL_URL="http://192.168.99.100" # change to HTTPS!!!!!!!!!!!! не работает все равно
 
EXPOSE 443 80 22

# HTTPS for localhost: (new lines added 15 - 27)

RUN mkdir -p /etc/gitlab/ssl
RUN chmod 700 /etc/gitlab/ssl
RUN openssl req -x509 -nodes -days 365 -newkey rsa:4096 \
	-subj /C=FR/ST=75/L=Paris/O=rs1/OU=rs1/CN=192.168.99.100/emailAddress=mrakhman@student.42.fr \
	-keyout /etc/gitlab/ssl/selfsigned.key -out /etc/gitlab/ssl/selfsigned.crt

RUN echo "external_url \"https://192.168.99.100\"" >> /etc/gitlab/gitlab.rb
RUN echo "nginx['redirect_http_to_https'] = true" >> /etc/gitlab/gitlab.rb
RUN echo "nginx['ssl_certificate'] = \"/etc/gitlab/ssl/selfsigned.crt\"" >> /etc/gitlab/gitlab.rb
RUN echo "nginx['ssl_certificate_key'] = \"/etc/gitlab/ssl/selfsigned.key\"" >> /etc/gitlab/gitlab.rb
RUN echo "gitlab_rails['gitlab_shell_ssh_port'] = 8022" >> /etc/gitlab/gitlab.rb

ENTRYPOINT (/opt/gitlab/embedded/bin/runsvdir-start &) && gitlab-ctl reconfigure && tail -f /dev/null

# Возможно, придется переместить --privileged и порты в build, потому что он начал открывать сервер во время билда
# docker build -t ex03 .
# docker run -it --rm -p 8080:80 -p 8022:22 -p 8443:443 --privileged ex03

# Why we shouldn't run SSH in Docker container: https://jpetazzo.github.io/2014/06/23/docker-ssh-considered-evil/

# In VirtualBox > Char > Settings > System increase Base memory and Processors N of CPUs (docker-machine stop Char before it)

# root Robinbad!312

# GIT_SSH_COMMAND="ssh -oPort=8022" \
# git clone git@192.168.99.100:8080/root/test_docker_gitlab.git