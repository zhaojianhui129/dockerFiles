#
# Composer for PHP 5.5 Dockerfile
#
# https://github.com/phalcon/dockerfiles
#

# Pull base image
FROM phalconphp/php:5.5

MAINTAINER Serghei Iakovlev <serghei@phalconphp.com>

# Set environment variables
ENV COMPOSER_HOME /root/composer
ENV PATH $COMPOSER_HOME/vendor/bin:$PATH
ENV COMPOSER_ALLOW_SUPERUSER=1

# Install Composer
RUN sed -i "s|apc.enable_cli = 1|apc.enable_cli = 0|" /etc/php/5.5/mods-available/apcu.ini && \
    rm /etc/php/5.5/cli/conf.d/20-xdebug.ini && \
    curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer && \
    chmod +x /usr/local/bin/composer

# Display version information
RUN composer --ansi --version

# Set up the application directory
VOLUME ["/app"]

# Define working directory
WORKDIR /app

# Set up the command arguments
CMD ["-"]
ENTRYPOINT ["composer", "--ansi"]
