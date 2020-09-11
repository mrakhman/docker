FROM node:12.8-alpine

WORKDIR /app

COPY package*.json /app

RUN npm install

COPY . /app

EXPOSE 3000

CMD ["npm", "start"]

# docker build -t front .
# docker run -it --rm -p 3000:3000 front