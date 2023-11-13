ARG WORDPRESS_IMAGE_TAG

FROM wordpress:${WORDPRESS_IMAGE_TAG}

# install source guardian
# https://stackoverflow.com/questions/64043106/how-to-install-php-extensionson-sourceguardian-on-wordpress-docker-image
# https://www.appsloveworld.com/docker/100/29/how-to-install-php-extensionson-sourceguardian-on-wordpress-docker-image#google_vignette
RUN mkdir -p /tmp/sourceguardian && cd /tmp/sourceguardian && \
  curl -Os https://www.sourceguardian.com/loaders/download/loaders.linux-x86_64.tar.gz && \
  tar xzf loaders.linux-x86_64.tar.gz && \
  PHP_VERSION=$(php -v | head -n1 | cut -d' ' -f2 | cut -d. -f1-2) && \
  cp ixed.$PHP_VERSION.lin "$(php -i | grep '^extension_dir =' | cut -d' ' -f3)/sourceguardian.so" && \
  echo "extension=sourceguardian.so" > /usr/local/etc/php/conf.d/15-sourceguardian.ini && \
  rm -rf /tmp/sourceguardian
