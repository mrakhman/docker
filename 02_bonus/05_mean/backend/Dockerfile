FROM node:12.8-alpine

WORKDIR /app

COPY my_app/package*.json /app

RUN npm install

COPY my_app /app

EXPOSE 5000

CMD ["node", "app.js"]

# docker build -t back .
# docker run -it --rm -p 5000:5000 back