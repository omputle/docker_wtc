FROM ruby:2.7.0

RUN apt-get update -y 

RUN apt-get install -y build-essential libpq-dev nodejs sqlite3

RUN gem update

RUN gem install bundler rails

ONBUILD EXPOSE 3000

ONBUILD COPY HelloWorld /opt/app

ONBUILD WORKDIR /opt/app

ONBUILD RUN bundle update --bundler

ONBUILD RUN bundle install --without production

ONBUILD RUN bundle exec rake db:migrate

ONBUILD RUN bundle exec rake db:seed
