# Retrieve Nginx version: 1.26.1
FROM nginx:stable

RUN su

#  Copy config file
COPY ./nginx.conf /etc/nginx/

# Copy default config file
COPY ./default.conf /etc/nginx/conf.d/


