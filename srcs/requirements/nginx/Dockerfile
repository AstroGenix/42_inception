# NGINX Dockerfile

# Penultimate stable version of Debian | 'Slim' to reduce image size
FROM debian:bullseye-slim

# - Updates package list and upgrades installed packages
# - Installs NGINX and OpenSSL
# - Cleans package list to reduce image size
# - Creates directory for SSL certificates
# - Generates a self-signed SSL certificate
RUN apt update && \
    apt upgrade -y && \
    apt install nginx openssl -y && \
    apt clean && \
    mkdir -p /etc/nginx/ssl && \
    openssl req -x509 -nodes -days 365    \
    -keyout /etc/nginx/ssl/inception.key  \
    -out /etc/nginx/ssl/inception.crt     \
    -subj "/C=PT/ST=Porto/L=Aliados/O=42/OU=42Porto/CN=dberehov.42.fr/UID=dberehov"

# Copy custom NGINX config
COPY conf/nginx.conf /etc/nginx/conf.d/default.conf

# Ensure NGINX runs in foreground
CMD ["nginx", "-g", "daemon off;"]