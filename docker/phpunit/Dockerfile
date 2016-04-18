FROM dankempster/spc:5.3-cli

MAINTAINER Dan Kempster <dank@sportsbikeshop.co.uk>

ARG GITHUB_TOKEN

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN mkdir -p /root/.composer/vendor/bin
ENV PATH=/root/.composer/vendor/bin:$PATH

RUN apt-get update \
    && apt-get install -y git zip unzip --no-install-recommends \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

RUN docker-php-ext-configure pdo_mysql --with-pdo-mysql=mysqlnd \
    && docker-php-ext-install pdo_mysql

ENTRYPOINT ["/project/vendor/phpunit/phpunit/phpunit"]
CMD ["--colors=always", "-v"]
