FROM debian

RUN apt-get update && \
    apt-get upgrade -y && \
	apt-get install -y wget bzip2 && \
	wget https://files.teamspeak-services.com/releases/server/3.12.1/teamspeak3-server_linux_amd64-3.12.1.tar.bz2 && \ 
	tar xvf teamspeak3-server_linux_amd64-3.12.1.tar.bz2 && \
	rm teamspeak3-server_linux_amd64-3.12.1.tar.bz2 && \
	cd teamspeak3-server_linux_amd64 && \
	touch .ts3server_license_accepted 

WORKDIR teamspeak3-server_linux_amd64

EXPOSE 9987/udp 10011 30033

ENTRYPOINT sh ts3server_minimal_runscript.sh

# docker build -t ex01 .
# docker run -it --rm -p 9987:9987/udp -p 10011:10011 -p 30033:30033 -e TS3SERVER_LICENSE=accept ex01

# install TeamSpeak client on Mac + connect with `docker-machine ip Char`:9987 + Server password + server admin privilege key
