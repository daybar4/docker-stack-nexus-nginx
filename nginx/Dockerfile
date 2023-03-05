FROM nginx:1.23

## For passwd file
RUN apt-get update; apt-get install -y \
    apache2-utils

## For localhost testing pruposes, uncomment in localhost
RUN apt-get install -y openssl
RUN mkdir -p /etc/nginx/external; \
    openssl req -x509 -newkey rsa:4096 \
    -subj "/C=ES/ST=SPAIN/L=BARCELONA/O=VIDNEO/CN=localhost" \
    -keyout "/etc/nginx/external/key.pem" \
    -out "/etc/nginx/external/cert.pem" \
    -days 365 -nodes -sha256

# Configuration
ADD nginx.conf /etc/nginx/nginx.conf
ADD .htpasswd /etc/apache2/.htpasswd