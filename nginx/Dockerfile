FROM nginx:latest

# Nginx will listen on this port
EXPOSE 80

# Remove the default config file that
# /etc/nginx/nginx.conf includes
RUN rm /etc/nginx/conf.d/default.conf

# We copy the requirements file in order to install
# Python dependencies
COPY selfie.conf /etc/nginx/conf.d
