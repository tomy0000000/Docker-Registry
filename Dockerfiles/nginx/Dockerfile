FROM nginx:1.23.3

LABEL tech.tomy.docker.nginx=""
LABEL maintainer="Tomy Hsieh @tomy0000000"

WORKDIR /etc/nginx
EXPOSE 80
EXPOSE 443
VOLUME ["/etc/nginx/conf.d", "/etc/nginx/ssl", "/usr/share/nginx/html"]

# Customize content directory
RUN mkdir /usr/share/nginx/html/default && \
    mv /usr/share/nginx/html/*.html /usr/share/nginx/html/default

# Install OpenSSL and generate dhparam
RUN apt update && apt-get install -y openssl && \
    openssl dhparam -out dhparam.pem 2048

# Copy custom configurations
COPY conf/* .
COPY conf.d conf.d
