# I only kept docker-compose file.
# Codebase itself was deleted because all the dependencies were VERY outdated, a lot of vulnerabilities.
# No code to build here

FROM node:10-alpine
WORKDIR /app
COPY package.json yarn.lock ./
RUN yarn install
COPY . .
VOLUME /todo-db
CMD ["node", "/app/src/index.js"]

# Named volume:
# docker build -t todo_app .
# docker run -it --rm -p 3000:3000 -v todo-db:/etc/todos todo_app
