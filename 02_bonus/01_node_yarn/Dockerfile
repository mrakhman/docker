# Developing environment to code in nodejs, using yarn 

FROM node:10

WORKDIR /tmp/node_yarn/

RUN apt-get update && \
	curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add - && \
	echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list && \
	apt-get install -y yarn

COPY my_app/package*.json /tmp/node_yarn

RUN yarn

COPY my_app /tmp/node_yarn

EXPOSE 5000

CMD ["node", "app.js"]

# docker build -t node_yarn . (if it fails - just run again)
# docker run -it --rm -p 5000:5000 node_yarn