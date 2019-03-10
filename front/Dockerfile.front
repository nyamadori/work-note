FROM node:10.15.3
ENV PORT 8080
RUN apt-get update -qq && \
  apt-get install -y apt-transport-https && \
  curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add - && \
  echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list && \
  apt-get install -y yarn
RUN mkdir /front
WORKDIR /front
COPY package.json /front/package.json
COPY yarn.lock /front/yarn.lock
RUN yarn install
COPY . /front
COPY entrypoint.sh /usr/bin/
RUN chmod +x /usr/bin/entrypoint.sh
ENTRYPOINT ["entrypoint.sh"]
EXPOSE ${PORT}
CMD ["yarn", "start"]
