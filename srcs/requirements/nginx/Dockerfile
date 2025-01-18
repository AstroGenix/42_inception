# NGINX Dockerfile

# Penultimate stable version of Debian
FROM debian:buster

# Update and Upgrade
RUN apt update && apt upgrade -y

# Install nginx and openssl
RUN apt install nginx openssl -y

# Clear apt cache to reduce image size
RUN apt clean

# Create ssl directory for certificates
RUN mkdir -p /etc/nginx/ssl

# Generate self-signed SSL cerificate
RUN openssl req -x509 -nodes -days 365    \
    -keyout /etc/nginx/ssl/inception.key  \
    -out /etc/nginx/ssl/inception.crt     \
    -subj "/C=PT/ST=Porto/L=Aliados/O=42/OU=42Porto/CN=dberehov.42.fr/UID=dberehov"
