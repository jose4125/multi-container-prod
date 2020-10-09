FROM nginx:1.19
HEALTHCHECK --interval=5m --timeout=3s \
  CMD curl -f http://localhost/ || exit 1
COPY ./default.conf /etc/nginx/conf.d/default.conf
