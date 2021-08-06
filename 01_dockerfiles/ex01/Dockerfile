FROM debian

ENV	TS3SERVER_LICENSE=accept

EXPOSE 9987/udp 10011 30033

RUN apt-get update -y && \
	apt-get upgrade -y

RUN	apt-get install -y wget bzip2

RUN wget http://dl.4players.de/ts/releases/3.12.1/teamspeak3-server_linux_amd64-3.12.1.tar.bz2 

RUN tar xvf teamspeak3-server_linux_amd64-3.12.1.tar.bz2

WORKDIR teamspeak3-server_linux_amd64

ENTRYPOINT sh ts3server_minimal_runscript.sh

#docker build -t ex01 ex01
#docker run --rm -d -p 9987:9987/udp -p 10011:10011 -p 30033:30033 ex01
#$(docker-machine ip Char):9987
