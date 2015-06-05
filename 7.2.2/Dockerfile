FROM php:5.6-fpm

# SuiteCRM 7.22 MAX
ENV SUITE_GIT_BASE_URL https://github.com/salesagility/SuiteCRM/archive
ENV SUITE_GIT_ARCHIVE v7.2.2.tar.gz
ENV SUITE_GIT_REPO ${SUITE_GIT_BASE_URL}/${SUITE_GIT_ARCHIVE}
ENV SUITE_APP_DIR /app/suitecrm

RUN apt-get update && \
    apt-get install -y  libcurl4-gnutls-dev libpng-dev libssl-dev libc-client2007e-dev libkrb5-dev \
                        unzip \
                        cron \
                        supervisor \
                        tar \
                        wget \
                        nginx \
                        nano \
    && docker-php-ext-configure imap --with-imap-ssl --with-kerberos \
    && docker-php-ext-install mysql curl gd zip mbstring imap \
    && rm -rf /var/lib/apt/lists/*

RUN mkdir -p ${SUITE_APP_DIR} && wget ${SUITE_GIT_REPO} && tar xzf ${SUITE_GIT_ARCHIVE} -C ${SUITE_APP_DIR} --strip-components 1

COPY init.sh /usr/local/bin/init.sh
RUN chmod u+x /usr/local/bin/init.sh
COPY nginx.conf /etc/nginx/conf.d/default.conf 
RUN rm /etc/nginx/sites-enabled/* && rm /etc/nginx/sites-available/*

EXPOSE 80

ENTRYPOINT ["/usr/local/bin/init.sh"]

