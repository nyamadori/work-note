FROM ruby:2.5
ENV PORT 3000
RUN apt-get update -qq && apt-get install -y postgresql-client
RUN mkdir /api
WORKDIR /api
COPY Gemfile /api/Gemfile
COPY Gemfile.lock /api/Gemfile.lock
RUN bundle install
COPY . /api
COPY entrypoint.sh /usr/bin/
RUN chmod +x /usr/bin/entrypoint.sh
ENTRYPOINT ["entrypoint.sh"]
EXPOSE ${PORT}
CMD ["rails", "server", "-b", "0.0.0.0"]
