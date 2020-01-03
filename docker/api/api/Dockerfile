FROM ruby:2.5.0
RUN apt-get update -qq && apt-get install -y build-essential libpq-dev nodejs
RUN mkdir /myApi
WORKDIR /myApi

COPY Gemfile /myApi/Gemfile
COPY Gemfile.lock /myApi/Gemfile.lock
RUN bundle install

COPY . /myApi

EXPOSE 3000

CMD rm -f tmp/pids/server.pid && rails server -b '0.0.0.0'