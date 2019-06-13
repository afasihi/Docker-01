FROM debian

RUN apt-get update
RUN apt-get -y install openjdk-8-jre-headless screen
RUN apt-get install -y wget
RUN wget https://launcher.mojang.com/v1/objects/3737db93722a9e39eeada7c27e7aca28b144ffa7/server.jar -O minecraft_server.1.13.jar
RUN echo "#!/bin/sh" > run.sh
RUN echo "java -Xms1024M -Xmx1536M -jar minecraft_server.1.13.jar -o true" >> run.sh
RUN chmod +x run.sh
RUN ./run.sh
RUN sed -i '3s/false/true/' eula.txt
CMD ./run.sh
