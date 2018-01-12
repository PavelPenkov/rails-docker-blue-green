FROM ruby:2.5.0
RUN apt-get update
RUN apt-get install -y libsqlite3-dev
ENV APP_DIR=/app
RUN mkdir -p $APP_DIR
WORKDIR $APP_DIR
COPY Gemfile Gemfile.lock $APP_DIR/
RUN bundle install --jobs=4 --without development test
COPY . $APP_DIR
ENV RAILS_ENV=production PORT=3000 RAILS_MAX_THREADS=5 RAILS_LOG_TO_STDOUT=1
RUN bundle exec rake assets:precompile
EXPOSE $PORT
HEALTHCHECK CMD curl -f http://localhost:$PORT
CMD bundle exec puma -C config/puma.rb
