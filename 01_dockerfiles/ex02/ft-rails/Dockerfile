FROM ruby:2.5.1

RUN apt-get update && \
	apt-get install -y nodejs sqlite3

RUN mkdir /opt/app
ONBUILD WORKDIR /opt/app
ONBUILD COPY app /opt/app

ONBUILD RUN bundle install
ONBUILD RUN rake db:migrate
ONBUILD RUN rake db:seed

# From ft-rails:
# docker build -t ft-rails:on-build .
# Not necessary to run: docker run -it --rm ft-rails:on-build

# From ex02:
# docker build -t ex02 .
# docker run -it --rm -p 3000:3000 ex02

# Open http://192.168.99.100:3000

# git repo for Ruby app: https://github.com/RailsApps/rails-signup-thankyou
