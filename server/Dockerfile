FROM nginx

RUN apt-get update &&\
    apt-get install -y software-properties-common &&\
    sed -i "/^# deb.*universe/ s/^# //" /etc/apt/sources.list &&\
    sed -i "/^# deb.*ppa:certbot/certbot/ s/^# //" /etc/apt/sources.list &&\
    apt-get update &&\
    apt-get install -y certbot python3-certbot-nginx &&\
    apt-get install -y cron &&\
    apt-get install -y nano

COPY encryptRenewCron /etc/cron.d/encryptRenewCron

RUN chmod 0644 /etc/cron.d/encryptRenewCron &&\
    crontab /etc/cron.d/encryptRenewCron &&\
    touch /var/log/cron.log &&\
    touch /var/log/nginx/access_host.log &&\
    touch /var/log/nginx/error_host.log