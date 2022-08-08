# Pull the minimal Ubuntu image
FROM nginx

# Install Nginx
#RUN apt-get -y update && apt-get -y install nginx

# Copy the Nginx config
#COPY default /etc/nginx/sites-available/default
#ADD nginx.conf /etc/nginx/nginx.conf

COPY default.conf /etc/nginx/conf.d/
#COPY default.conf /etc/nginx/nginx.conf

# Expose the port for access
EXPOSE 8080/tcp
EXPOSE 80/tcp
# Run the Nginx server
CMD ["/usr/sbin/nginx", "-g", "daemon off;"]
