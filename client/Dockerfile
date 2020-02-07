FROM node:alpine as multi-client
WORKDIR '/app'
COPY ./package.json ./
RUN npm install
COPY . .
RUN  npm run build

FROM nginx
EXPOSE 3000
COPY ./nginx/prod.conf /etc/nginx/conf.d/default.conf
COPY --from=multi-client /app/build /usr/share/nginx.html
