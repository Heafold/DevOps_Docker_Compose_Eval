FROM node:16 as build

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

RUN npm run build

FROM node:16 as serve

WORKDIR /app

RUN npm install -g http-server

COPY --from=build /app/build /app/build

EXPOSE 80

CMD ["http-server", "/app/build", "-p", "80"]
