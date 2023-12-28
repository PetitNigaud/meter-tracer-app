FROM nginx:latest

# Add self signed SSL certificate for local development / deployment (required fo webcam access when client is not localhost)
# https://codingwithmanny.medium.com/configure-self-signed-ssl-for-nginx-docker-from-a-scratch-7c2bcd5478c6
RUN apt-get update && apt-get install -y openssl

RUN openssl req -x509 -nodes \
   -days 365 \
   -subj "/C=CA/ST=QC/O=Company, Inc./CN=mydomain.com" \
   -addext "subjectAltName=DNS:mydomain.com" \
   -newkey rsa:2048 \
   -keyout /etc/ssl/private/nginx-selfsigned.key \
   -out /etc/ssl/certs/nginx-selfsigned.crt;

COPY ./conf/default.conf /etc/nginx/conf.d/default.conf
COPY ./conf/self_signed_ssl.conf /etc/nginx/self_signed_ssl.conf

# add line into default.conf to include new conf file
#RUN sed -i "15i\    include /etc/nginx/self_signed_ssl.conf;" /etc/nginx/conf.d/default.conf

