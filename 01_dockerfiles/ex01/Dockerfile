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

EXPOSE 9987/udp 10011 30033

ENTRYPOINT ["sh", "ts3server_startscript.sh"]

CMD ["start"]

# docker build -t ex01 .
# docker run -it -p 9987:9987/udp -p 10011:10011 -p 30033:30033 ex01

# install TeamSpeak client on Mac, connect with opened port ????
