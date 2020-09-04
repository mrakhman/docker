# Developing environment to code in nodejs, using yarn 

FROM node:10

WORKDIR /tmp/node_yarn/

RUN apt-get update
RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add -
RUN echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list
RUN apt-get install -y yarn

COPY my_app /tmp/node_yarn

RUN yarn

EXPOSE 5000

CMD ["node", "app.js"]