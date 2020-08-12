FROM ubuntu

RUN apt-get update && \
	apt-get install -y curl openssh-server ca-certificates postfix
	
RUN curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | bash

RUN apt-get update && \
	apt-get install -y gitlab-ce

RUN EXTERNAL_URL="https://192.168.99.100"
 
EXPOSE 443 80 22

# PAY ATTENTION to this command - I only tested it in bash !!!!!!!!!!!!!
ENTRYPOINT (/opt/gitlab/embedded/bin/runsvdir-start &) && gitlab-ctl reconfigure && tail -f /dev/null

# Возможно, придется переместить --privileged и порты в build, потому что он начал открывать сервер во время билда
# docker build -t ex03 .
# docker run -it --rm -p 8080:80 -p 8022:22 -p 8443:443 --privileged ex03

# Why we shouldn't run SSH in Docker container: https://jpetazzo.github.io/2014/06/23/docker-ssh-considered-evil/
# In VirtualBox > Char > Settings > System increase Base memory and Processors N of CPUs (docker-machine stop Char before it)
# root Robinbad!312
