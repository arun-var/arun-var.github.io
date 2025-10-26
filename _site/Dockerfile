FROM ruby:3.1
RUN apt-get update && apt-get install -y libmagickwand-dev imagemagick
COPY Gemfile* /usr/src/myapp/
WORKDIR /usr/src/myapp
RUN gem install bundler:2.2.32 && bundle install
COPY . /usr/src/myapp
EXPOSE 4000
CMD bundle exec jekyll serve --host=0.0.0.0