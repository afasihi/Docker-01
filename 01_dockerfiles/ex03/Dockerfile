FROM ubuntu:16.04

RUN apt-get update && apt-get upgrade -y
RUN apt-get install -y curl openssh-server ca-certificates
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y postfix
RUN curl https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh |  bash 
RUN apt-get install tzdata -y
RUN apt-get install gitlab-ce
EXPOSE 433 666 80
WORKDIR /etc/gitlab
RUN sed -i '13s/http:\/\/gitlab.example.com/https:\/\/192.168.99.100/' gitlab.rb
RUN echo "gitlab_rails['gitlab_shell_ssh_port'] = 666" >> gitlab.rb
RUN echo "Port 666" >> /etc/ssh/ssh_config
RUN sed -i '953s/# //' gitlab.rb
RUN sed -i '953s/false/true/' gitlab.rb
RUN sed -i '954s/# //' gitlab.rb
RUN echo "/opt/gitlab/embedded/bin/runsvdir-start& gitlab-ctl reconfigure" > script.sh
RUN echo "service ssh restart" >> script.sh
RUN echo "tail -f /dev/null" >> script.sh
RUN chmod 777 script.sh
CMD ["sh", "script.sh"]
# docker build -t my_gitlab .
# docker run --name git -p 80:80 -p 443:443 -p 666:22 -it my_gitlab
# -p 10.11.13.1:22:22
