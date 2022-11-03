FROM ruby:3.1.2

ENV BUNDLE_VERSION 2.2.11
ENV APP /usr/src/app

RUN mkdir $APP
WORKDIR $APP
COPY Gemfile* $APP/

RUN gem update --system
RUN bundle update --bundler

RUN bundle install
COPY . $APP/

COPY entrypoint.sh /usr/bin/
RUN chmod +x /usr/bin/entrypoint.sh
ENTRYPOINT ["entrypoint.sh"]
EXPOSE 8080

CMD ["rails", "server", "-b", "0.0.0.0"]