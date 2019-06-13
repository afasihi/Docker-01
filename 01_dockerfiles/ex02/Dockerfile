FROM ruby
RUN apt-get update -qq && apt-get install -y nodejs && gem install rails bundler
ONBUILD WORKDIR /opt
COPY ./myapp1 .
ONBUILD RUN bundle install
ONBUILD RUN rails generate migration Products name:string
ONBUILD RUN rake db:migrate

#first build
#docker build -t ft-rails:on-build .

#second build
#docker build -t rubyrails .

#to run it
#docker run --rm -it --name ex02 -p $(docker-machine ip Char):3000:3000 rubyrails
