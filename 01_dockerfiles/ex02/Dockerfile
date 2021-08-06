FROM ruby:2.5.1

RUN apt-get update -y && \
    apt-get upgrade -y
RUN apt-get install build-essential nodejs sqlite -y && \
    gem install bundler rails && \
	gem install rake 

RUN mkdir -p opt/app
COPY ./app /opt/app

ONBUILD WORKDIR /opt/app
ONBUILD EXPOSE 3000
ONBUILD RUN gem install bundler:1.16.2
ONBUILD RUN bundle install
ONBUILD RUN rake db:migrate
ONBUILD RUN rake db:seed

#cd ex02
#git clone https://github.com/JetBrains/sample_rails_app ft-rails/app
#mv Dockerfile ft-rails
#cd ft-rails
#docker build -t ft-rails:on-build .
#cd ..
#echo 	"FROM ft-rails:on-build
#EXPOSE 3000
#CMD [\"rails\", \"s\", \"-b\", \"0.0.0.0\", \"-p\", \"3000\"]" > Dockerfile				
#docker build -t ex02 .
#open http://$(docker-machine ip Char):3000
#docker run -it --rm -p 3000:3000 ex02
#mv ft-rails/Dockerfile .
#rm -rf ft-rails
