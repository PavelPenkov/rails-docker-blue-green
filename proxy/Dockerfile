FROM nginx
COPY etc/nginx/* /etc/nginx/
RUN cp /etc/nginx/blue.conf /etc/nginx/proxy_pass.conf
COPY switch /usr/bin/
EXPOSE 80 443
HEALTHCHECK CMD curl -f -k https://localhost
