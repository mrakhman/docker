FROM ubuntu:20.04

RUN apt-get update && \
	apt-get install -y openjdk-8-jdk wget

WORKDIR /minecraft

RUN wget -O minecraft_server.jar \
	https://launcher.mojang.com/v1/objects/c5f6fb23c3876461d46ec380421e42b289789530/server.jar

RUN echo "eula=true" > eula.txt && \
	java -jar minecraft_server.jar --initSettings && \
	sed -i 's/online-mode=true/online-mode=false/g' server.properties

CMD java -Xmx1024M -Xms1024M -jar minecraft_server.jar nogui

EXPOSE 25565

# docker build -t minecraft .
# docker run -it --rm -p 25565:25565 minecraft

# How to connect to Client here: https://developer.ibm.com/technologies/containers/tutorials/minecraft-and-ibm-cloud-part-1/
