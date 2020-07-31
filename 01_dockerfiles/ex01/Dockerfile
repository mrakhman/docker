FROM debian

RUN apt-get update && \
    apt-get upgrade && \
	apt-get install -y wget bzip2 && \
	wget https://files.teamspeak-services.com/releases/server/3.12.1/teamspeak3-server_linux_amd64-3.12.1.tar.bz2 && \ 
	tar xvf teamspeak3-server_linux_amd64-3.12.1.tar.bz2 && \
	rm teamspeak3-server_linux_amd64-3.12.1.tar.bz2 && \
	cd teamspeak3-server_linux_amd64 && \
	touch .ts3server_license_accepted 

WORKDIR teamspeak3-server_linux_amd64

ENTRYPOINT ["sh", "ts3server_startscript.sh"]
CMD ["start"]

not finished!
