FROM nginx:latest
COPY default.conf /etc/nginx/conf.d/default.conf
COPY ./index.html /app/index.html
COPY ./index.html /app/homework.html
WORKDIR /app
RUN usermod -u 1001 nginx \
  && groupmod -g 1001 nginx
RUN chown -R nginx:nginx /app
EXPOSE 8000
CMD ["nginx", "-g", "daemon off;"]
