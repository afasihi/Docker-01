FROM debian
RUN apt-get update
RUN apt-get install wget bzip2 -y
RUN wget http://dl.4players.de/ts/releases/3.6.1/teamspeak3-server_linux_amd64-3.6.1.tar.bz2
RUN tar xfvj teamspeak3-server_linux_amd64-3.6.1.tar.bz2
WORKDIR teamspeak3-server_linux_amd64/.
EXPOSE 9987/udp 10011 30033
CMD ["./ts3server_minimal_runscript.sh", "license_accepted=1"]
#docker build -t new_teamserver .
#docker run -p 9987:9987/udp -p 10011:10011 -p 30033:30033 new_teamserver
