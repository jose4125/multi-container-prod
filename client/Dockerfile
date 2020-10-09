FROM node:alpine as builder
WORKDIR /usr/app
ENV NODE_ENV=development
ENV PATH /app/node_modules/.bin:$PATH
COPY package*.json ./
RUN npm install
COPY . .
USER node
RUN npm run build

FROM nginx
EXPOSE 3000
HEALTHCHECK --interval=5m --timeout=3s \
  CMD curl -f http://localhost/ || exit 1
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /usr/app/build /usr/share/nginx/html
