FROM ruby:2.5.3
MAINTAINER Jarrod Folino <jdfolino@gmail.com>

RUN apt-get update && \
    apt-get install -y net-tools

# Install gems
ENV APP_HOME /app
ENV HOME /root
RUN mkdir $APP_HOME
RUN mkdir $APP_HOME/views
WORKDIR $APP_HOME
COPY Gemfile* $APP_HOME/
RUN bundle install

# Upload source
COPY . $APP_HOME

# Start server
ENV PORT 4567
ENV PRODUCT_SERVICE 'http://192.168.0.13:9494'
EXPOSE 4567
CMD ["ruby", "app.rb"]
