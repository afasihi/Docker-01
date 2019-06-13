FROM ubuntu:14.04
RUN apt-get update
RUN apt-get -y install apache2
ENTRYPOINT service apache2 start && tail -f /dev/null
