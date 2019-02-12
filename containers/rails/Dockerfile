FROM ruby:2.5.3

ENV APP_ROOT=/app \
    LC_ALL=C.UTF-8

RUN apt-get update -qq && gem update bundler
RUN apt-get install -y nodejs \
                       mysql-client \
                       --no-install-recommends && \
    rm -rf /var/lib/apt/lists/* /var/cache/apt/archives/* /tmp/* /var/tmp/*
WORKDIR ${APP_ROOT}

COPY .ruby-version ${APP_ROOT}
COPY Gemfile           ${APP_ROOT}
COPY Gemfile.lock      ${APP_ROOT}

RUN bundle install --clean && \
    rm -rf ~/.gem

EXPOSE 3000

CMD ["bundle", "exec", "rails", "s", "-b", "0.0.0.0"]

