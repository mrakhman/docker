FROM ubuntu:20.04

RUN apt-get update && \
	apt-get install -y curl openssh-server ca-certificates postfix

RUN curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | bash

RUN apt-get update && \
	apt-get install -y gitlab-ce

EXPOSE 443 80 22

# HTTPS:
RUN mkdir -p /etc/gitlab/ssl \
&& chmod 700 /etc/gitlab/ssl \

&& openssl req -x509 -nodes -days 365 -newkey rsa:4096 \
	-subj /C=FR/ST=75/L=Paris/O=42/OU=/CN=192.168.99.100/emailAddress=mrakhman@student.42.fr \
 	-keyout /etc/gitlab/ssl/selfsigned.key -out /etc/gitlab/ssl/selfsigned.crt \

&& echo "external_url \"https://192.168.99.100\"" >> /etc/gitlab/gitlab.rb \
&& echo "nginx['redirect_http_to_https'] = true" >> /etc/gitlab/gitlab.rb \
&& echo "nginx['ssl_certificate'] = \"/etc/gitlab/ssl/selfsigned.crt\"" >> /etc/gitlab/gitlab.rb \
&& echo "nginx['ssl_certificate_key'] = \"/etc/gitlab/ssl/selfsigned.key\"" >> /etc/gitlab/gitlab.rb

ENTRYPOINT service ssh start && (/opt/gitlab/embedded/bin/runsvdir-start &) && gitlab-ctl reconfigure && tail -f /dev/null



# In VirtualBox > Char > Settings > System increase Base memory and Processors N of CPUs (docker-machine stop Char before it)

# docker build -t ex03 .
# docker run -it --rm -p 8080:80 -p 8022:22 -p 8443:443 --privileged ex03

# Open:
# HTTPS: https://192.168.99.100:8443/

# clone / push with HTTPS:
# GIT_SSL_NO_VERIFY=true git clone https://192.168.99.100:8443/root/test_docker_gitlab.git
# GIT_SSL_NO_VERIFY=true git push + root with password

# clone / push with SSH:
# GIT_SSH_COMMAND="ssh -oPort=8022" git clone git@192.168.99.100:root/test_docker_gitlab.git
# GIT_SSH_COMMAND="ssh -oPort=8022" git push

# If "WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!" error then open ~/.ssh/known_hosts and delete the line it screams about
# For ex: "Offending ECDSA key in /Users/mrakhman/.ssh/known_hosts:10" del line 10

# Why we shouldn't run SSH in Docker container: https://jpetazzo.github.io/2014/06/23/docker-ssh-considered-evil/