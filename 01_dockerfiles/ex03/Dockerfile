FROM ubuntu

RUN apt-get update && \
	apt-get install -y curl openssh-server ca-certificates postfix
	
RUN curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | bash

RUN apt-get update && \
	install gitlab-ce

EXPOSE 443 80 22

# PAY ATTENTION to this command - I only tested it in bash !!!!!!!!!!!!!
RUN /opt/gitlab/embedded/bin/runsvdir-start & \
	gitlab-ctl reconfigure && \
	tail -f /dev/null

# docker build -t ex03 .
# docker run -it --rm -p 8080:80 -p 8022:22 -p 8443:443 --privileged ex03

# root Robinbad!312