# Usa a imagem base PHP 8.3 com Alpine 3.20
FROM php:8.3-fpm-alpine3.20

# Mantenedor da imagem
LABEL maintainer="Paulo Coelho"

# Define o diretório de trabalho
WORKDIR /var/www

# Instala dependências do sistema e extensões PHP
RUN apk add --no-cache \
    bash \
    curl \
    libpng-dev \
    libzip-dev \
    zlib-dev \
    nodejs \
    npm \
    autoconf \
    build-base \
    && docker-php-ext-install \
    gd \
    zip \
    pdo \
    pdo_mysql \
    && pecl install redis \
    && docker-php-ext-enable redis \
    && rm -rf /var/cache/apk/*

# Instala o Composer mais recente
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# Copia os arquivos da aplicação para o diretório de trabalho
COPY . /var/www

# Instala as dependências do Node.js usando o npm
RUN npm install

# Expõe a porta do PHP-FPM para o host
EXPOSE 9000

# Comando padrão para iniciar o PHP-FPM
CMD ["php-fpm"]
