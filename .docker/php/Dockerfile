FROM amazonlinux:2

# timezone設定
RUN ln -sf /usr/share/zoneinfo/Asia/Tokyo /etc/localtime

RUN yum update -y && amazon-linux-extras install php8.0 postgresql13 vim -y && \
    yum clean metadata && yum install -y \
    curl \
    gcc-c++ \
    git \
    less \
    make \
    php-bcmath \
    php-ctype \
    php-curl \
    php-dom \
    php-fileinfo \
    php-json \
    php-mbstring \
    php-openssl \
    php-pcre \
    php-pdo \
    php-pgsql \
    php-tokenizer \
    php-xml \
    php-zip \
    unzip && \
    yum clean all && \
    rm -rf /var/cache/yum

RUN curl -fsSL https://rpm.nodesource.com/setup_16.x | bash - && \
    yum install -y nodejs && \
    yum clean all && \
    rm -rf /var/cache/yum

# composer
COPY --from=composer:2 /usr/bin/composer /usr/bin/composer

EXPOSE 9000

COPY ./www.conf /etc/php-fpm.d/www.conf
COPY ./php.ini /usr/local/etc/php/php.ini

WORKDIR /var/www/html

ENTRYPOINT /usr/sbin/php-fpm -F
