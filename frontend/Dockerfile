FROM node:20

WORKDIR /app

COPY package*.json ./
RUN npm ci

COPY . .
RUN npm run build
RUN npm install --global serve

EXPOSE 80

CMD ["serve", "-s", "dist", "-l", "80"]
