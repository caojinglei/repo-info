## `nextcloud:latest`

```console
$ docker pull nextcloud@sha256:7ead4dc8e8a2d9966d74ae42685a905f5afbbfe794a2f77430d63c0693e0410e
```

-	Manifest MIME: `application/vnd.docker.distribution.manifest.list.v2+json`
-	Platforms:
	-	linux; amd64
	-	linux; arm variant v5
	-	linux; arm variant v7
	-	linux; arm64 variant v8
	-	linux; 386
	-	linux; ppc64le
	-	linux; s390x

### `nextcloud:latest` - linux; amd64

```console
$ docker pull nextcloud@sha256:8224ed87bf29e1d178858fd1d58970400ba9dbfa8f28debbcfc9c2a81c28d1ac
```

-	Docker Version: 17.06.2-ce
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **250.5 MB (250472949 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:72b1b0bc80e25a266fa9f3ea0e3be62c5e3ef51d1581317a9174653722ea8397`
-	Entrypoint: `["\/entrypoint.sh"]`
-	Default Command: `["apache2-foreground"]`

```dockerfile
# Sat, 04 Nov 2017 05:21:35 GMT
ADD file:55b071e2cfc3ea2f4bbf048d7d676e3c06a77a9a98d63f7af291f3decb495ec8 in / 
# Sat, 04 Nov 2017 05:21:36 GMT
CMD ["bash"]
# Sat, 04 Nov 2017 10:11:29 GMT
ENV PHPIZE_DEPS=autoconf 		dpkg-dev 		file 		g++ 		gcc 		libc-dev 		libpcre3-dev 		make 		pkg-config 		re2c
# Sat, 04 Nov 2017 10:12:05 GMT
RUN apt-get update && apt-get install -y 		$PHPIZE_DEPS 		ca-certificates 		curl 		libedit2 		libsqlite3-0 		libxml2 		xz-utils 	--no-install-recommends && rm -r /var/lib/apt/lists/*
# Sat, 04 Nov 2017 10:12:06 GMT
ENV PHP_INI_DIR=/usr/local/etc/php
# Sat, 04 Nov 2017 10:12:07 GMT
RUN mkdir -p $PHP_INI_DIR/conf.d
# Sat, 04 Nov 2017 10:17:18 GMT
RUN apt-get update 	&& apt-get install -y --no-install-recommends 		apache2 	&& rm -rf /var/lib/apt/lists/*
# Sat, 04 Nov 2017 10:17:18 GMT
ENV APACHE_CONFDIR=/etc/apache2
# Sat, 04 Nov 2017 10:17:18 GMT
ENV APACHE_ENVVARS=/etc/apache2/envvars
# Sat, 04 Nov 2017 10:17:19 GMT
RUN set -ex 		&& sed -ri 's/^export ([^=]+)=(.*)$/: ${\1:=\2}\nexport \1/' "$APACHE_ENVVARS" 		&& . "$APACHE_ENVVARS" 	&& for dir in 		"$APACHE_LOCK_DIR" 		"$APACHE_RUN_DIR" 		"$APACHE_LOG_DIR" 		/var/www/html 	; do 		rm -rvf "$dir" 		&& mkdir -p "$dir" 		&& chown -R "$APACHE_RUN_USER:$APACHE_RUN_GROUP" "$dir"; 	done
# Sat, 04 Nov 2017 10:17:20 GMT
RUN a2dismod mpm_event && a2enmod mpm_prefork
# Sat, 04 Nov 2017 10:17:20 GMT
RUN set -ex 	&& . "$APACHE_ENVVARS" 	&& ln -sfT /dev/stderr "$APACHE_LOG_DIR/error.log" 	&& ln -sfT /dev/stdout "$APACHE_LOG_DIR/access.log" 	&& ln -sfT /dev/stdout "$APACHE_LOG_DIR/other_vhosts_access.log"
# Sat, 04 Nov 2017 10:17:21 GMT
RUN { 		echo '<FilesMatch \.php$>'; 		echo '\tSetHandler application/x-httpd-php'; 		echo '</FilesMatch>'; 		echo; 		echo 'DirectoryIndex disabled'; 		echo 'DirectoryIndex index.php index.html'; 		echo; 		echo '<Directory /var/www/>'; 		echo '\tOptions -Indexes'; 		echo '\tAllowOverride All'; 		echo '</Directory>'; 	} | tee "$APACHE_CONFDIR/conf-available/docker-php.conf" 	&& a2enconf docker-php
# Sat, 04 Nov 2017 10:17:21 GMT
ENV PHP_EXTRA_BUILD_DEPS=apache2-dev
# Sat, 04 Nov 2017 10:17:21 GMT
ENV PHP_EXTRA_CONFIGURE_ARGS=--with-apxs2
# Sat, 04 Nov 2017 10:17:22 GMT
ENV PHP_CFLAGS=-fstack-protector-strong -fpic -fpie -O2
# Sat, 04 Nov 2017 10:17:22 GMT
ENV PHP_CPPFLAGS=-fstack-protector-strong -fpic -fpie -O2
# Sat, 04 Nov 2017 10:17:22 GMT
ENV PHP_LDFLAGS=-Wl,-O1 -Wl,--hash-style=both -pie
# Sat, 04 Nov 2017 10:17:22 GMT
ENV GPG_KEYS=A917B1ECDA84AEC2B568FED6F50ABC807BD5DCD0 528995BFEDFBA7191D46839EF9BA0ADA31CBD89E
# Tue, 28 Nov 2017 00:04:07 GMT
ENV PHP_VERSION=7.1.12
# Tue, 28 Nov 2017 00:04:08 GMT
ENV PHP_URL=https://secure.php.net/get/php-7.1.12.tar.xz/from/this/mirror PHP_ASC_URL=https://secure.php.net/get/php-7.1.12.tar.xz.asc/from/this/mirror
# Tue, 28 Nov 2017 00:04:08 GMT
ENV PHP_SHA256=a0118850774571b1f2d4e30b4fe7a4b958ca66f07d07d65ebdc789c54ba6eeb3 PHP_MD5=
# Tue, 28 Nov 2017 00:04:23 GMT
RUN set -xe; 		fetchDeps=' 		wget 	'; 	if ! command -v gpg > /dev/null; then 		fetchDeps="$fetchDeps 			dirmngr 			gnupg 		"; 	fi; 	apt-get update; 	apt-get install -y --no-install-recommends $fetchDeps; 	rm -rf /var/lib/apt/lists/*; 		mkdir -p /usr/src; 	cd /usr/src; 		wget -O php.tar.xz "$PHP_URL"; 		if [ -n "$PHP_SHA256" ]; then 		echo "$PHP_SHA256 *php.tar.xz" | sha256sum -c -; 	fi; 	if [ -n "$PHP_MD5" ]; then 		echo "$PHP_MD5 *php.tar.xz" | md5sum -c -; 	fi; 		if [ -n "$PHP_ASC_URL" ]; then 		wget -O php.tar.xz.asc "$PHP_ASC_URL"; 		export GNUPGHOME="$(mktemp -d)"; 		for key in $GPG_KEYS; do 			gpg --keyserver ha.pool.sks-keyservers.net --recv-keys "$key"; 		done; 		gpg --batch --verify php.tar.xz.asc php.tar.xz; 		rm -rf "$GNUPGHOME"; 	fi; 		apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false $fetchDeps
# Tue, 28 Nov 2017 00:04:23 GMT
COPY file:207c686e3fed4f71f8a7b245d8dcae9c9048d276a326d82b553c12a90af0c0ca in /usr/local/bin/ 
# Tue, 28 Nov 2017 00:06:56 GMT
RUN set -xe 	&& buildDeps=" 		$PHP_EXTRA_BUILD_DEPS 		libcurl4-openssl-dev 		libedit-dev 		libsqlite3-dev 		libssl-dev 		libxml2-dev 		zlib1g-dev 	" 	&& apt-get update && apt-get install -y $buildDeps --no-install-recommends && rm -rf /var/lib/apt/lists/* 		&& export CFLAGS="$PHP_CFLAGS" 		CPPFLAGS="$PHP_CPPFLAGS" 		LDFLAGS="$PHP_LDFLAGS" 	&& docker-php-source extract 	&& cd /usr/src/php 	&& gnuArch="$(dpkg-architecture --query DEB_BUILD_GNU_TYPE)" 	&& debMultiarch="$(dpkg-architecture --query DEB_BUILD_MULTIARCH)" 	&& if [ ! -d /usr/include/curl ]; then 		ln -sT "/usr/include/$debMultiarch/curl" /usr/local/include/curl; 	fi 	&& ./configure 		--build="$gnuArch" 		--with-config-file-path="$PHP_INI_DIR" 		--with-config-file-scan-dir="$PHP_INI_DIR/conf.d" 				--disable-cgi 				--enable-ftp 		--enable-mbstring 		--enable-mysqlnd 				--with-curl 		--with-libedit 		--with-openssl 		--with-zlib 				--with-pcre-regex=/usr 		--with-libdir="lib/$debMultiarch" 				$PHP_EXTRA_CONFIGURE_ARGS 	&& make -j "$(nproc)" 	&& make install 	&& { find /usr/local/bin /usr/local/sbin -type f -executable -exec strip --strip-all '{}' + || true; } 	&& make clean 	&& cd / 	&& docker-php-source delete 		&& apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false $buildDeps 		&& pecl update-channels 	&& rm -rf /tmp/pear ~/.pearrc
# Tue, 28 Nov 2017 00:07:09 GMT
COPY multi:dbabcc0b81566a75f49e7faa9ca5f96cd22a515b80ee7ea1e34fceceee3f9c2a in /usr/local/bin/ 
# Tue, 28 Nov 2017 00:07:09 GMT
ENTRYPOINT ["docker-php-entrypoint"]
# Tue, 28 Nov 2017 00:07:09 GMT
COPY file:24613ecbb1ce6a09f683b0753da9c26a1af07547326e8a02f6eec80ad6f2774a in /usr/local/bin/ 
# Tue, 28 Nov 2017 00:07:09 GMT
WORKDIR /var/www/html
# Tue, 28 Nov 2017 00:07:10 GMT
EXPOSE 80/tcp
# Tue, 28 Nov 2017 00:07:10 GMT
CMD ["apache2-foreground"]
# Tue, 28 Nov 2017 02:32:13 GMT
RUN apt-get update && apt-get install -y   rsync   bzip2   libcurl4-openssl-dev   libfreetype6-dev   libicu-dev   libjpeg-dev   libldap2-dev   libmcrypt-dev   libmemcached-dev   libpng12-dev   libpq-dev   libxml2-dev   && rm -rf /var/lib/apt/lists/*
# Tue, 28 Nov 2017 02:34:22 GMT
RUN debMultiarch="$(dpkg-architecture --query DEB_BUILD_MULTIARCH)"   && docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr   && docker-php-ext-configure ldap --with-libdir="lib/$debMultiarch"   && docker-php-ext-install gd exif intl mbstring mcrypt ldap mysqli opcache pdo_mysql pdo_pgsql pgsql zip pcntl
# Tue, 28 Nov 2017 02:36:22 GMT
RUN {   echo 'opcache.enable=1';   echo 'opcache.enable_cli=1';   echo 'opcache.interned_strings_buffer=8';   echo 'opcache.max_accelerated_files=10000';   echo 'opcache.memory_consumption=128';   echo 'opcache.save_comments=1';   echo 'opcache.revalidate_freq=1';   } > /usr/local/etc/php/conf.d/opcache-recommended.ini
# Tue, 28 Nov 2017 02:36:23 GMT
RUN a2enmod rewrite
# Tue, 28 Nov 2017 02:36:53 GMT
RUN set -ex  && pecl install APCu-5.1.8  && pecl install memcached-3.0.4  && pecl install redis-3.1.4  && docker-php-ext-enable apcu redis memcached
# Tue, 28 Nov 2017 02:36:54 GMT
RUN a2enmod rewrite
# Tue, 28 Nov 2017 02:44:36 GMT
ENV NEXTCLOUD_VERSION=12.0.3
# Tue, 28 Nov 2017 02:44:37 GMT
RUN chown -R www-data:root /var/www/html &&     chmod -R g=u /var/www/html
# Tue, 28 Nov 2017 02:44:37 GMT
VOLUME [/var/www/html]
# Tue, 28 Nov 2017 02:44:51 GMT
RUN curl -fsSL -o nextcloud.tar.bz2     "https://download.nextcloud.com/server/releases/nextcloud-${NEXTCLOUD_VERSION}.tar.bz2"  && curl -fsSL -o nextcloud.tar.bz2.asc     "https://download.nextcloud.com/server/releases/nextcloud-${NEXTCLOUD_VERSION}.tar.bz2.asc"  && export GNUPGHOME="$(mktemp -d)"  && gpg --keyserver ha.pool.sks-keyservers.net --recv-keys 28806A878AE423A28372792ED75899B9A724937A  && gpg --batch --verify nextcloud.tar.bz2.asc nextcloud.tar.bz2  && rm -r "$GNUPGHOME" nextcloud.tar.bz2.asc  && tar -xjf nextcloud.tar.bz2 -C /usr/src/  && rm nextcloud.tar.bz2  && rm -rf /usr/src/nextcloud/updater  && mkdir -p /usr/src/nextcloud/data  && mkdir -p /usr/src/nextcloud/custom_apps  && chmod +x /usr/src/nextcloud/occ
# Tue, 28 Nov 2017 02:44:52 GMT
COPY file:3fa42fa6664f03c90280a265050a78ef70bf32cd31864db727f5ee7e94828722 in /entrypoint.sh 
# Tue, 28 Nov 2017 02:44:52 GMT
COPY multi:a4ce16f733fa0a4cb4b62b3fe3229e71f5a6b970a03b912772780cdb452098f4 in /usr/src/nextcloud/config/ 
# Tue, 28 Nov 2017 02:44:53 GMT
ENTRYPOINT ["/entrypoint.sh"]
# Tue, 28 Nov 2017 02:44:53 GMT
CMD ["apache2-foreground"]
```

-	Layers:
	-	`sha256:85b1f47fba49da65256f07c8790542a3880e9216f9c491965040f35ce2c6ca7a`  
		Last Modified: Mon, 09 Oct 2017 21:36:40 GMT  
		Size: 52.6 MB (52595124 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:d8204bc927258ee7d613ed166e9ee95041987ddbfddaf39594e54b403d55dc09`  
		Last Modified: Sat, 04 Nov 2017 11:53:46 GMT  
		Size: 82.5 MB (82497571 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:92fc16bb18e4e7f7c6975e0cbef8949d968f35f0672b4ebd5006afb10c20ca10`  
		Last Modified: Sat, 04 Nov 2017 11:53:17 GMT  
		Size: 183.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:31098e61b2ae5029460c46c69ecf26335ffdf5ba5a7e492a104018df593735c9`  
		Last Modified: Sat, 04 Nov 2017 11:55:30 GMT  
		Size: 3.0 MB (3012952 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:f6ae64bfd33d38ba595480aead27756418fa63d2e22da09dc0f2673d863eb051`  
		Last Modified: Sat, 04 Nov 2017 11:55:29 GMT  
		Size: 1.3 KB (1253 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:003c1818b354888cc37d66173a56d44d1ff2b838f4b0cc3fffd403569686974c`  
		Last Modified: Sat, 04 Nov 2017 11:55:26 GMT  
		Size: 427.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:a6fd4aeb32ad8234ae032a6ddbd2429dd6f1de2cc734319c8bfd7039b311fa9e`  
		Last Modified: Sat, 04 Nov 2017 11:55:26 GMT  
		Size: 230.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:a094df7cedc1113abd270d4413af16b24013ba274fe2420cbbdf90f6c65e4efc`  
		Last Modified: Sat, 04 Nov 2017 11:55:26 GMT  
		Size: 486.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:91278dc5a9ce25a3512591489cd5e3e1e02aa996e0b53b45913c132f95892776`  
		Last Modified: Tue, 28 Nov 2017 01:24:12 GMT  
		Size: 12.5 MB (12549297 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:9538f34af1321d4ee0dc1bc8185d950e31829d6438f3a59f58d99ba10cd85201`  
		Last Modified: Tue, 28 Nov 2017 01:24:10 GMT  
		Size: 502.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:733e3c4f8018fa21aa31cb5717a2908846f945ae98329179649f935af052fc76`  
		Last Modified: Tue, 28 Nov 2017 01:24:15 GMT  
		Size: 13.5 MB (13501152 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:995b9d08453eb5221eb8f80433ddb5163a2c3cd37eed610ab59217a4f0985339`  
		Last Modified: Tue, 28 Nov 2017 01:24:12 GMT  
		Size: 2.2 KB (2184 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:61bf14ff73e36324847c1a8d7674669ecf801c05eb0b73599732658780d4abde`  
		Last Modified: Tue, 28 Nov 2017 01:24:10 GMT  
		Size: 906.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:c7a1bd795714ebe107444f19fd2deb7e46d20819343d21301112bc65dc4be878`  
		Last Modified: Tue, 28 Nov 2017 02:46:00 GMT  
		Size: 36.1 MB (36114639 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:325d4d05e8d39bca365f600e7a0299bb2800ba81baf6ef996f6e95d76496da4f`  
		Last Modified: Tue, 28 Nov 2017 02:45:51 GMT  
		Size: 1.9 MB (1920005 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:436a02f8e57db5ad8151ad01dbeafd97b468489eb76946a9e82214d60e940e87`  
		Last Modified: Tue, 28 Nov 2017 02:45:50 GMT  
		Size: 354.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:7b23f55fa6a29828d2f9f4f6e3fde8470d2180671577f69e8d2f588c96def44e`  
		Last Modified: Tue, 28 Nov 2017 02:45:48 GMT  
		Size: 312.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:528c9db2268e64f05fb4c64fc6142a1e7cb854d12a356899d9663cb1b6c9cba8`  
		Last Modified: Tue, 28 Nov 2017 02:45:48 GMT  
		Size: 1.3 MB (1303126 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:0ad129e522c191ea6f2f9925bbf03139d463804991dd5e4a2022783c3abd194e`  
		Last Modified: Sat, 04 Nov 2017 20:53:31 GMT  
		Size: 138.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:a781e49060e945d2a1eefc41b0491aee350dcd6c9c2acee16182fdae24a1a396`  
		Last Modified: Tue, 28 Nov 2017 02:52:25 GMT  
		Size: 47.0 MB (46970316 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:1327416c668db56840995aaa6ded7f90fc97a9929c72275dca86c002cbde6628`  
		Last Modified: Tue, 28 Nov 2017 02:51:51 GMT  
		Size: 941.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:5b20b0257dabcff3c8a8471e468992b9775b27a8c08ddf40c7a6770c8b8f8164`  
		Last Modified: Tue, 28 Nov 2017 02:51:50 GMT  
		Size: 851.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip

### `nextcloud:latest` - linux; arm variant v5

```console
$ docker pull nextcloud@sha256:ecc14ec05b1e7a27bd2f6771b1fcff4319ddea7bdd4b02e19187672a40e83b3a
```

-	Docker Version: 17.06.0-ce
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **230.5 MB (230478278 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:57675f507483b3e2de7e8c9dbd332fd7841bf5af1d27ac6d10d0f087d77f5354`
-	Entrypoint: `["\/entrypoint.sh"]`
-	Default Command: `["apache2-foreground"]`

```dockerfile
# Mon, 09 Oct 2017 21:42:07 GMT
ADD file:cfee2e008c8ea154a9e6408e017dd40cc1b53f7c31932cec7fa8e1dc14649764 in / 
# Mon, 09 Oct 2017 21:42:07 GMT
CMD ["bash"]
# Mon, 09 Oct 2017 22:44:50 GMT
ENV PHPIZE_DEPS=autoconf 		dpkg-dev 		file 		g++ 		gcc 		libc-dev 		libpcre3-dev 		make 		pkg-config 		re2c
# Mon, 09 Oct 2017 22:45:58 GMT
RUN apt-get update && apt-get install -y 		$PHPIZE_DEPS 		ca-certificates 		curl 		libedit2 		libsqlite3-0 		libxml2 		xz-utils 	--no-install-recommends && rm -r /var/lib/apt/lists/*
# Mon, 09 Oct 2017 22:45:58 GMT
ENV PHP_INI_DIR=/usr/local/etc/php
# Mon, 09 Oct 2017 22:46:00 GMT
RUN mkdir -p $PHP_INI_DIR/conf.d
# Mon, 09 Oct 2017 22:51:00 GMT
RUN apt-get update 	&& apt-get install -y --no-install-recommends 		apache2 	&& rm -rf /var/lib/apt/lists/*
# Mon, 09 Oct 2017 22:51:01 GMT
ENV APACHE_CONFDIR=/etc/apache2
# Mon, 09 Oct 2017 22:51:01 GMT
ENV APACHE_ENVVARS=/etc/apache2/envvars
# Mon, 09 Oct 2017 22:51:02 GMT
RUN set -ex 		&& sed -ri 's/^export ([^=]+)=(.*)$/: ${\1:=\2}\nexport \1/' "$APACHE_ENVVARS" 		&& . "$APACHE_ENVVARS" 	&& for dir in 		"$APACHE_LOCK_DIR" 		"$APACHE_RUN_DIR" 		"$APACHE_LOG_DIR" 		/var/www/html 	; do 		rm -rvf "$dir" 		&& mkdir -p "$dir" 		&& chown -R "$APACHE_RUN_USER:$APACHE_RUN_GROUP" "$dir"; 	done
# Mon, 09 Oct 2017 22:51:03 GMT
RUN a2dismod mpm_event && a2enmod mpm_prefork
# Mon, 09 Oct 2017 22:51:04 GMT
RUN set -ex 	&& . "$APACHE_ENVVARS" 	&& ln -sfT /dev/stderr "$APACHE_LOG_DIR/error.log" 	&& ln -sfT /dev/stdout "$APACHE_LOG_DIR/access.log" 	&& ln -sfT /dev/stdout "$APACHE_LOG_DIR/other_vhosts_access.log"
# Mon, 09 Oct 2017 22:51:05 GMT
RUN { 		echo '<FilesMatch \.php$>'; 		echo '\tSetHandler application/x-httpd-php'; 		echo '</FilesMatch>'; 		echo; 		echo 'DirectoryIndex disabled'; 		echo 'DirectoryIndex index.php index.html'; 		echo; 		echo '<Directory /var/www/>'; 		echo '\tOptions -Indexes'; 		echo '\tAllowOverride All'; 		echo '</Directory>'; 	} | tee "$APACHE_CONFDIR/conf-available/docker-php.conf" 	&& a2enconf docker-php
# Mon, 09 Oct 2017 22:51:05 GMT
ENV PHP_EXTRA_BUILD_DEPS=apache2-dev
# Mon, 09 Oct 2017 22:51:05 GMT
ENV PHP_EXTRA_CONFIGURE_ARGS=--with-apxs2
# Mon, 09 Oct 2017 22:51:06 GMT
ENV PHP_CFLAGS=-fstack-protector-strong -fpic -fpie -O2
# Mon, 09 Oct 2017 22:51:06 GMT
ENV PHP_CPPFLAGS=-fstack-protector-strong -fpic -fpie -O2
# Mon, 09 Oct 2017 22:51:06 GMT
ENV PHP_LDFLAGS=-Wl,-O1 -Wl,--hash-style=both -pie
# Mon, 09 Oct 2017 22:51:06 GMT
ENV GPG_KEYS=A917B1ECDA84AEC2B568FED6F50ABC807BD5DCD0 528995BFEDFBA7191D46839EF9BA0ADA31CBD89E
# Tue, 28 Nov 2017 14:42:16 GMT
ENV PHP_VERSION=7.1.12
# Tue, 28 Nov 2017 14:42:16 GMT
ENV PHP_URL=https://secure.php.net/get/php-7.1.12.tar.xz/from/this/mirror PHP_ASC_URL=https://secure.php.net/get/php-7.1.12.tar.xz.asc/from/this/mirror
# Tue, 28 Nov 2017 14:42:17 GMT
ENV PHP_SHA256=a0118850774571b1f2d4e30b4fe7a4b958ca66f07d07d65ebdc789c54ba6eeb3 PHP_MD5=
# Tue, 28 Nov 2017 14:42:57 GMT
RUN set -xe; 		fetchDeps=' 		wget 	'; 	if ! command -v gpg > /dev/null; then 		fetchDeps="$fetchDeps 			dirmngr 			gnupg 		"; 	fi; 	apt-get update; 	apt-get install -y --no-install-recommends $fetchDeps; 	rm -rf /var/lib/apt/lists/*; 		mkdir -p /usr/src; 	cd /usr/src; 		wget -O php.tar.xz "$PHP_URL"; 		if [ -n "$PHP_SHA256" ]; then 		echo "$PHP_SHA256 *php.tar.xz" | sha256sum -c -; 	fi; 	if [ -n "$PHP_MD5" ]; then 		echo "$PHP_MD5 *php.tar.xz" | md5sum -c -; 	fi; 		if [ -n "$PHP_ASC_URL" ]; then 		wget -O php.tar.xz.asc "$PHP_ASC_URL"; 		export GNUPGHOME="$(mktemp -d)"; 		for key in $GPG_KEYS; do 			gpg --keyserver ha.pool.sks-keyservers.net --recv-keys "$key"; 		done; 		gpg --batch --verify php.tar.xz.asc php.tar.xz; 		rm -rf "$GNUPGHOME"; 	fi; 		apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false $fetchDeps
# Tue, 28 Nov 2017 14:42:57 GMT
COPY file:207c686e3fed4f71f8a7b245d8dcae9c9048d276a326d82b553c12a90af0c0ca in /usr/local/bin/ 
# Tue, 28 Nov 2017 14:45:48 GMT
RUN set -xe 	&& buildDeps=" 		$PHP_EXTRA_BUILD_DEPS 		libcurl4-openssl-dev 		libedit-dev 		libsqlite3-dev 		libssl-dev 		libxml2-dev 		zlib1g-dev 	" 	&& apt-get update && apt-get install -y $buildDeps --no-install-recommends && rm -rf /var/lib/apt/lists/* 		&& export CFLAGS="$PHP_CFLAGS" 		CPPFLAGS="$PHP_CPPFLAGS" 		LDFLAGS="$PHP_LDFLAGS" 	&& docker-php-source extract 	&& cd /usr/src/php 	&& gnuArch="$(dpkg-architecture --query DEB_BUILD_GNU_TYPE)" 	&& debMultiarch="$(dpkg-architecture --query DEB_BUILD_MULTIARCH)" 	&& if [ ! -d /usr/include/curl ]; then 		ln -sT "/usr/include/$debMultiarch/curl" /usr/local/include/curl; 	fi 	&& ./configure 		--build="$gnuArch" 		--with-config-file-path="$PHP_INI_DIR" 		--with-config-file-scan-dir="$PHP_INI_DIR/conf.d" 				--disable-cgi 				--enable-ftp 		--enable-mbstring 		--enable-mysqlnd 				--with-curl 		--with-libedit 		--with-openssl 		--with-zlib 				--with-pcre-regex=/usr 		--with-libdir="lib/$debMultiarch" 				$PHP_EXTRA_CONFIGURE_ARGS 	&& make -j "$(nproc)" 	&& make install 	&& { find /usr/local/bin /usr/local/sbin -type f -executable -exec strip --strip-all '{}' + || true; } 	&& make clean 	&& cd / 	&& docker-php-source delete 		&& apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false $buildDeps 		&& pecl update-channels 	&& rm -rf /tmp/pear ~/.pearrc
# Tue, 28 Nov 2017 14:45:49 GMT
COPY multi:dbabcc0b81566a75f49e7faa9ca5f96cd22a515b80ee7ea1e34fceceee3f9c2a in /usr/local/bin/ 
# Tue, 28 Nov 2017 14:45:49 GMT
ENTRYPOINT ["docker-php-entrypoint"]
# Tue, 28 Nov 2017 14:45:50 GMT
COPY file:24613ecbb1ce6a09f683b0753da9c26a1af07547326e8a02f6eec80ad6f2774a in /usr/local/bin/ 
# Tue, 28 Nov 2017 14:45:50 GMT
WORKDIR /var/www/html
# Tue, 28 Nov 2017 14:45:50 GMT
EXPOSE 80/tcp
# Tue, 28 Nov 2017 14:45:51 GMT
CMD ["apache2-foreground"]
# Tue, 28 Nov 2017 15:36:11 GMT
RUN apt-get update && apt-get install -y   rsync   bzip2   libcurl4-openssl-dev   libfreetype6-dev   libicu-dev   libjpeg-dev   libldap2-dev   libmcrypt-dev   libmemcached-dev   libpng12-dev   libpq-dev   libxml2-dev   && rm -rf /var/lib/apt/lists/*
# Tue, 28 Nov 2017 15:40:54 GMT
RUN debMultiarch="$(dpkg-architecture --query DEB_BUILD_MULTIARCH)"   && docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr   && docker-php-ext-configure ldap --with-libdir="lib/$debMultiarch"   && docker-php-ext-install gd exif intl mbstring mcrypt ldap mysqli opcache pdo_mysql pdo_pgsql pgsql zip pcntl
# Tue, 28 Nov 2017 15:40:55 GMT
RUN {   echo 'opcache.enable=1';   echo 'opcache.enable_cli=1';   echo 'opcache.interned_strings_buffer=8';   echo 'opcache.max_accelerated_files=10000';   echo 'opcache.memory_consumption=128';   echo 'opcache.save_comments=1';   echo 'opcache.revalidate_freq=1';   } > /usr/local/etc/php/conf.d/opcache-recommended.ini
# Tue, 28 Nov 2017 15:40:56 GMT
RUN a2enmod rewrite
# Tue, 28 Nov 2017 15:41:46 GMT
RUN set -ex  && pecl install APCu-5.1.8  && pecl install memcached-3.0.4  && pecl install redis-3.1.4  && docker-php-ext-enable apcu redis memcached
# Tue, 28 Nov 2017 15:41:47 GMT
RUN a2enmod rewrite
# Tue, 28 Nov 2017 15:49:26 GMT
ENV NEXTCLOUD_VERSION=12.0.3
# Tue, 28 Nov 2017 15:49:27 GMT
RUN chown -R www-data:root /var/www/html &&     chmod -R g=u /var/www/html
# Tue, 28 Nov 2017 15:49:27 GMT
VOLUME [/var/www/html]
# Tue, 28 Nov 2017 15:49:53 GMT
RUN curl -fsSL -o nextcloud.tar.bz2     "https://download.nextcloud.com/server/releases/nextcloud-${NEXTCLOUD_VERSION}.tar.bz2"  && curl -fsSL -o nextcloud.tar.bz2.asc     "https://download.nextcloud.com/server/releases/nextcloud-${NEXTCLOUD_VERSION}.tar.bz2.asc"  && export GNUPGHOME="$(mktemp -d)"  && gpg --keyserver ha.pool.sks-keyservers.net --recv-keys 28806A878AE423A28372792ED75899B9A724937A  && gpg --batch --verify nextcloud.tar.bz2.asc nextcloud.tar.bz2  && rm -r "$GNUPGHOME" nextcloud.tar.bz2.asc  && tar -xjf nextcloud.tar.bz2 -C /usr/src/  && rm nextcloud.tar.bz2  && rm -rf /usr/src/nextcloud/updater  && mkdir -p /usr/src/nextcloud/data  && mkdir -p /usr/src/nextcloud/custom_apps  && chmod +x /usr/src/nextcloud/occ
# Tue, 28 Nov 2017 15:49:54 GMT
COPY file:3fa42fa6664f03c90280a265050a78ef70bf32cd31864db727f5ee7e94828722 in /entrypoint.sh 
# Tue, 28 Nov 2017 15:49:55 GMT
COPY multi:a4ce16f733fa0a4cb4b62b3fe3229e71f5a6b970a03b912772780cdb452098f4 in /usr/src/nextcloud/config/ 
# Tue, 28 Nov 2017 15:50:01 GMT
ENTRYPOINT ["/entrypoint.sh"]
# Tue, 28 Nov 2017 15:50:01 GMT
CMD ["apache2-foreground"]
```

-	Layers:
	-	`sha256:29dee24d6376416a80f3fdb145082e8dd352694bfdcf639e49e26ddbf8d8cb52`  
		Last Modified: Mon, 09 Oct 2017 21:47:16 GMT  
		Size: 50.9 MB (50879894 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:cad1ba133bf708efd9b75cf971201a4ed647286864942a66d5c9d86b126f9b92`  
		Last Modified: Mon, 09 Oct 2017 23:39:58 GMT  
		Size: 63.5 MB (63526955 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:fa24f60e9c2ee1e5256863f0b528469123443a094ca2c8a19dfe9890a89b664a`  
		Last Modified: Mon, 09 Oct 2017 23:39:37 GMT  
		Size: 211.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:6d2226c6d34b25989365cc4d9036799ca2fefec786911c54f67ef906f4b9bb76`  
		Last Modified: Mon, 09 Oct 2017 23:40:30 GMT  
		Size: 2.8 MB (2824242 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:589b717d3a226bfcde3047ef4cf6d796173d1f4a1ece0bc788271c06f29bba47`  
		Last Modified: Mon, 09 Oct 2017 23:40:29 GMT  
		Size: 1.3 KB (1279 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:ae277f94e125f9b12232fd0cb072c63090cad8a41f1c77e71b4c5374e5656946`  
		Last Modified: Mon, 09 Oct 2017 23:40:28 GMT  
		Size: 470.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:11585a82e3a977c923548ce1364988534f529c5cb4b2555e3698a2f16cfd978f`  
		Last Modified: Mon, 09 Oct 2017 23:40:29 GMT  
		Size: 230.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:e034a32b45a003b5387a7745c9c1e5ccc4fd3dc902b42894564087c846344889`  
		Last Modified: Mon, 09 Oct 2017 23:40:28 GMT  
		Size: 511.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:d63298587e7e53163b4784d54649556e67f1e933e0c6aac7687b20eca97e94ec`  
		Last Modified: Tue, 28 Nov 2017 15:13:59 GMT  
		Size: 12.5 MB (12547942 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:e2739f59616b240fc13280f8f94f8a2fec1ad9f1a76fde9ff8db923d17f2d588`  
		Last Modified: Tue, 28 Nov 2017 15:13:57 GMT  
		Size: 500.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:d737f1ea9dd54eab7e47945dca5416d6b03502e4e016f1fe0f98328ede8f9e54`  
		Last Modified: Tue, 28 Nov 2017 15:14:03 GMT  
		Size: 14.5 MB (14480346 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:3df21a92e6a19fb4449e472657c3ff0458eb2f9c3fe93728298aac40fb5fa4a2`  
		Last Modified: Tue, 28 Nov 2017 15:13:57 GMT  
		Size: 2.2 KB (2180 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:1e8aa7ae723f6d563edaebc697d35b404c5c16120206ca2fd36a16cff63ddb55`  
		Last Modified: Tue, 28 Nov 2017 15:13:58 GMT  
		Size: 902.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:7ed10db0bdfb320f1f8c85fd14157a6609ad9da198b07f92165ca36bfcb1737b`  
		Last Modified: Tue, 28 Nov 2017 15:51:10 GMT  
		Size: 36.0 MB (36042818 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:ab7cadb434891070ef1f2099a99e949734557731d10bb32ecb9b47745c22b3ee`  
		Last Modified: Tue, 28 Nov 2017 15:50:58 GMT  
		Size: 1.8 MB (1847323 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:2f7011142c287b2b8f28510065594a4be0a862d3f7f55c169f98c33b6448c746`  
		Last Modified: Tue, 28 Nov 2017 15:50:58 GMT  
		Size: 354.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:2865db74e29e37378cf0052edd89e73b065e752df35231122db5192c7bf9610f`  
		Last Modified: Tue, 28 Nov 2017 15:50:57 GMT  
		Size: 313.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:71060aaebdfc8696d92ed91d90cd8a0d007772483d075464cef4aab5c82dda63`  
		Last Modified: Tue, 28 Nov 2017 15:50:57 GMT  
		Size: 1.3 MB (1349509 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:b9d00aa867d4da74d1b6211f594a244015db32d672db4cb9931fc19f87e5dccc`  
		Last Modified: Tue, 10 Oct 2017 02:17:44 GMT  
		Size: 137.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:ced60a213f5dc0b1b3dc8700a8ac901dd854b2aa95a726bb04614800ddf82cfb`  
		Last Modified: Tue, 28 Nov 2017 15:53:33 GMT  
		Size: 47.0 MB (46970372 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:8cb620d945d3550d14c0e8b0aed071d696eb334a5e75357c378be1409dc34d0a`  
		Last Modified: Tue, 28 Nov 2017 15:53:17 GMT  
		Size: 939.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:2c436bfa7cb6d69bba45f086d0a18437667d7502c1268e0463a698b93bca3b3a`  
		Last Modified: Tue, 28 Nov 2017 15:53:17 GMT  
		Size: 851.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip

### `nextcloud:latest` - linux; arm variant v7

```console
$ docker pull nextcloud@sha256:5ffd9b7acecc842e281ea14ede8245c988da581a5d288b92ba225967da9a6a9b
```

-	Docker Version: 17.06.0-ce
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **225.9 MB (225936365 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:aaf3ddaee9a91cdadbcff7df6565c00ecc916ac5bb95d7f2c1a49627996d148d`
-	Entrypoint: `["\/entrypoint.sh"]`
-	Default Command: `["apache2-foreground"]`

```dockerfile
# Mon, 09 Oct 2017 21:42:19 GMT
ADD file:68eabcdf7d9c5518c34f691d547b77534be3929ad958c8835c5d4a54114c7ee4 in / 
# Mon, 09 Oct 2017 21:42:20 GMT
CMD ["bash"]
# Mon, 09 Oct 2017 23:08:59 GMT
ENV PHPIZE_DEPS=autoconf 		dpkg-dev 		file 		g++ 		gcc 		libc-dev 		libpcre3-dev 		make 		pkg-config 		re2c
# Mon, 09 Oct 2017 23:10:02 GMT
RUN apt-get update && apt-get install -y 		$PHPIZE_DEPS 		ca-certificates 		curl 		libedit2 		libsqlite3-0 		libxml2 		xz-utils 	--no-install-recommends && rm -r /var/lib/apt/lists/*
# Mon, 09 Oct 2017 23:10:03 GMT
ENV PHP_INI_DIR=/usr/local/etc/php
# Mon, 09 Oct 2017 23:10:04 GMT
RUN mkdir -p $PHP_INI_DIR/conf.d
# Mon, 09 Oct 2017 23:15:10 GMT
RUN apt-get update 	&& apt-get install -y --no-install-recommends 		apache2 	&& rm -rf /var/lib/apt/lists/*
# Mon, 09 Oct 2017 23:15:10 GMT
ENV APACHE_CONFDIR=/etc/apache2
# Mon, 09 Oct 2017 23:15:14 GMT
ENV APACHE_ENVVARS=/etc/apache2/envvars
# Mon, 09 Oct 2017 23:15:16 GMT
RUN set -ex 		&& sed -ri 's/^export ([^=]+)=(.*)$/: ${\1:=\2}\nexport \1/' "$APACHE_ENVVARS" 		&& . "$APACHE_ENVVARS" 	&& for dir in 		"$APACHE_LOCK_DIR" 		"$APACHE_RUN_DIR" 		"$APACHE_LOG_DIR" 		/var/www/html 	; do 		rm -rvf "$dir" 		&& mkdir -p "$dir" 		&& chown -R "$APACHE_RUN_USER:$APACHE_RUN_GROUP" "$dir"; 	done
# Mon, 09 Oct 2017 23:15:17 GMT
RUN a2dismod mpm_event && a2enmod mpm_prefork
# Mon, 09 Oct 2017 23:15:19 GMT
RUN set -ex 	&& . "$APACHE_ENVVARS" 	&& ln -sfT /dev/stderr "$APACHE_LOG_DIR/error.log" 	&& ln -sfT /dev/stdout "$APACHE_LOG_DIR/access.log" 	&& ln -sfT /dev/stdout "$APACHE_LOG_DIR/other_vhosts_access.log"
# Mon, 09 Oct 2017 23:15:23 GMT
RUN { 		echo '<FilesMatch \.php$>'; 		echo '\tSetHandler application/x-httpd-php'; 		echo '</FilesMatch>'; 		echo; 		echo 'DirectoryIndex disabled'; 		echo 'DirectoryIndex index.php index.html'; 		echo; 		echo '<Directory /var/www/>'; 		echo '\tOptions -Indexes'; 		echo '\tAllowOverride All'; 		echo '</Directory>'; 	} | tee "$APACHE_CONFDIR/conf-available/docker-php.conf" 	&& a2enconf docker-php
# Mon, 09 Oct 2017 23:15:27 GMT
ENV PHP_EXTRA_BUILD_DEPS=apache2-dev
# Mon, 09 Oct 2017 23:15:27 GMT
ENV PHP_EXTRA_CONFIGURE_ARGS=--with-apxs2
# Mon, 09 Oct 2017 23:15:27 GMT
ENV PHP_CFLAGS=-fstack-protector-strong -fpic -fpie -O2
# Mon, 09 Oct 2017 23:15:31 GMT
ENV PHP_CPPFLAGS=-fstack-protector-strong -fpic -fpie -O2
# Mon, 09 Oct 2017 23:15:31 GMT
ENV PHP_LDFLAGS=-Wl,-O1 -Wl,--hash-style=both -pie
# Mon, 09 Oct 2017 23:15:31 GMT
ENV GPG_KEYS=A917B1ECDA84AEC2B568FED6F50ABC807BD5DCD0 528995BFEDFBA7191D46839EF9BA0ADA31CBD89E
# Tue, 28 Nov 2017 12:53:13 GMT
ENV PHP_VERSION=7.1.12
# Tue, 28 Nov 2017 12:53:13 GMT
ENV PHP_URL=https://secure.php.net/get/php-7.1.12.tar.xz/from/this/mirror PHP_ASC_URL=https://secure.php.net/get/php-7.1.12.tar.xz.asc/from/this/mirror
# Tue, 28 Nov 2017 12:53:13 GMT
ENV PHP_SHA256=a0118850774571b1f2d4e30b4fe7a4b958ca66f07d07d65ebdc789c54ba6eeb3 PHP_MD5=
# Tue, 28 Nov 2017 12:53:52 GMT
RUN set -xe; 		fetchDeps=' 		wget 	'; 	if ! command -v gpg > /dev/null; then 		fetchDeps="$fetchDeps 			dirmngr 			gnupg 		"; 	fi; 	apt-get update; 	apt-get install -y --no-install-recommends $fetchDeps; 	rm -rf /var/lib/apt/lists/*; 		mkdir -p /usr/src; 	cd /usr/src; 		wget -O php.tar.xz "$PHP_URL"; 		if [ -n "$PHP_SHA256" ]; then 		echo "$PHP_SHA256 *php.tar.xz" | sha256sum -c -; 	fi; 	if [ -n "$PHP_MD5" ]; then 		echo "$PHP_MD5 *php.tar.xz" | md5sum -c -; 	fi; 		if [ -n "$PHP_ASC_URL" ]; then 		wget -O php.tar.xz.asc "$PHP_ASC_URL"; 		export GNUPGHOME="$(mktemp -d)"; 		for key in $GPG_KEYS; do 			gpg --keyserver ha.pool.sks-keyservers.net --recv-keys "$key"; 		done; 		gpg --batch --verify php.tar.xz.asc php.tar.xz; 		rm -rf "$GNUPGHOME"; 	fi; 		apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false $fetchDeps
# Tue, 28 Nov 2017 12:53:52 GMT
COPY file:207c686e3fed4f71f8a7b245d8dcae9c9048d276a326d82b553c12a90af0c0ca in /usr/local/bin/ 
# Tue, 28 Nov 2017 12:56:31 GMT
RUN set -xe 	&& buildDeps=" 		$PHP_EXTRA_BUILD_DEPS 		libcurl4-openssl-dev 		libedit-dev 		libsqlite3-dev 		libssl-dev 		libxml2-dev 		zlib1g-dev 	" 	&& apt-get update && apt-get install -y $buildDeps --no-install-recommends && rm -rf /var/lib/apt/lists/* 		&& export CFLAGS="$PHP_CFLAGS" 		CPPFLAGS="$PHP_CPPFLAGS" 		LDFLAGS="$PHP_LDFLAGS" 	&& docker-php-source extract 	&& cd /usr/src/php 	&& gnuArch="$(dpkg-architecture --query DEB_BUILD_GNU_TYPE)" 	&& debMultiarch="$(dpkg-architecture --query DEB_BUILD_MULTIARCH)" 	&& if [ ! -d /usr/include/curl ]; then 		ln -sT "/usr/include/$debMultiarch/curl" /usr/local/include/curl; 	fi 	&& ./configure 		--build="$gnuArch" 		--with-config-file-path="$PHP_INI_DIR" 		--with-config-file-scan-dir="$PHP_INI_DIR/conf.d" 				--disable-cgi 				--enable-ftp 		--enable-mbstring 		--enable-mysqlnd 				--with-curl 		--with-libedit 		--with-openssl 		--with-zlib 				--with-pcre-regex=/usr 		--with-libdir="lib/$debMultiarch" 				$PHP_EXTRA_CONFIGURE_ARGS 	&& make -j "$(nproc)" 	&& make install 	&& { find /usr/local/bin /usr/local/sbin -type f -executable -exec strip --strip-all '{}' + || true; } 	&& make clean 	&& cd / 	&& docker-php-source delete 		&& apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false $buildDeps 		&& pecl update-channels 	&& rm -rf /tmp/pear ~/.pearrc
# Tue, 28 Nov 2017 12:56:32 GMT
COPY multi:dbabcc0b81566a75f49e7faa9ca5f96cd22a515b80ee7ea1e34fceceee3f9c2a in /usr/local/bin/ 
# Tue, 28 Nov 2017 12:56:32 GMT
ENTRYPOINT ["docker-php-entrypoint"]
# Tue, 28 Nov 2017 12:56:32 GMT
COPY file:24613ecbb1ce6a09f683b0753da9c26a1af07547326e8a02f6eec80ad6f2774a in /usr/local/bin/ 
# Tue, 28 Nov 2017 12:56:33 GMT
WORKDIR /var/www/html
# Tue, 28 Nov 2017 12:56:33 GMT
EXPOSE 80/tcp
# Tue, 28 Nov 2017 12:56:33 GMT
CMD ["apache2-foreground"]
# Tue, 28 Nov 2017 13:49:38 GMT
RUN apt-get update && apt-get install -y   rsync   bzip2   libcurl4-openssl-dev   libfreetype6-dev   libicu-dev   libjpeg-dev   libldap2-dev   libmcrypt-dev   libmemcached-dev   libpng12-dev   libpq-dev   libxml2-dev   && rm -rf /var/lib/apt/lists/*
# Tue, 28 Nov 2017 13:53:54 GMT
RUN debMultiarch="$(dpkg-architecture --query DEB_BUILD_MULTIARCH)"   && docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr   && docker-php-ext-configure ldap --with-libdir="lib/$debMultiarch"   && docker-php-ext-install gd exif intl mbstring mcrypt ldap mysqli opcache pdo_mysql pdo_pgsql pgsql zip pcntl
# Tue, 28 Nov 2017 13:53:55 GMT
RUN {   echo 'opcache.enable=1';   echo 'opcache.enable_cli=1';   echo 'opcache.interned_strings_buffer=8';   echo 'opcache.max_accelerated_files=10000';   echo 'opcache.memory_consumption=128';   echo 'opcache.save_comments=1';   echo 'opcache.revalidate_freq=1';   } > /usr/local/etc/php/conf.d/opcache-recommended.ini
# Tue, 28 Nov 2017 13:53:56 GMT
RUN a2enmod rewrite
# Tue, 28 Nov 2017 13:54:42 GMT
RUN set -ex  && pecl install APCu-5.1.8  && pecl install memcached-3.0.4  && pecl install redis-3.1.4  && docker-php-ext-enable apcu redis memcached
# Tue, 28 Nov 2017 13:54:43 GMT
RUN a2enmod rewrite
# Tue, 28 Nov 2017 14:02:31 GMT
ENV NEXTCLOUD_VERSION=12.0.3
# Tue, 28 Nov 2017 14:02:32 GMT
RUN chown -R www-data:root /var/www/html &&     chmod -R g=u /var/www/html
# Tue, 28 Nov 2017 14:02:41 GMT
VOLUME [/var/www/html]
# Tue, 28 Nov 2017 14:03:00 GMT
RUN curl -fsSL -o nextcloud.tar.bz2     "https://download.nextcloud.com/server/releases/nextcloud-${NEXTCLOUD_VERSION}.tar.bz2"  && curl -fsSL -o nextcloud.tar.bz2.asc     "https://download.nextcloud.com/server/releases/nextcloud-${NEXTCLOUD_VERSION}.tar.bz2.asc"  && export GNUPGHOME="$(mktemp -d)"  && gpg --keyserver ha.pool.sks-keyservers.net --recv-keys 28806A878AE423A28372792ED75899B9A724937A  && gpg --batch --verify nextcloud.tar.bz2.asc nextcloud.tar.bz2  && rm -r "$GNUPGHOME" nextcloud.tar.bz2.asc  && tar -xjf nextcloud.tar.bz2 -C /usr/src/  && rm nextcloud.tar.bz2  && rm -rf /usr/src/nextcloud/updater  && mkdir -p /usr/src/nextcloud/data  && mkdir -p /usr/src/nextcloud/custom_apps  && chmod +x /usr/src/nextcloud/occ
# Tue, 28 Nov 2017 14:03:02 GMT
COPY file:3fa42fa6664f03c90280a265050a78ef70bf32cd31864db727f5ee7e94828722 in /entrypoint.sh 
# Tue, 28 Nov 2017 14:03:03 GMT
COPY multi:a4ce16f733fa0a4cb4b62b3fe3229e71f5a6b970a03b912772780cdb452098f4 in /usr/src/nextcloud/config/ 
# Tue, 28 Nov 2017 14:03:03 GMT
ENTRYPOINT ["/entrypoint.sh"]
# Tue, 28 Nov 2017 14:03:03 GMT
CMD ["apache2-foreground"]
```

-	Layers:
	-	`sha256:e52c47bf5ccb0baf5e58ae2e958abbb260f942d8743078a07a367079102e162f`  
		Last Modified: Mon, 09 Oct 2017 21:48:44 GMT  
		Size: 48.7 MB (48686311 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:be530d54777d3b6901a69cebe98eb5b0bde4c6c3d6ab1447b9c76a1b7c86069d`  
		Last Modified: Tue, 10 Oct 2017 00:03:17 GMT  
		Size: 63.8 MB (63794787 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:c4780c6a3912aa6ac660ed0fc0c12bba611f9ef448dfa9a5ba381e9f64e6c5e9`  
		Last Modified: Tue, 10 Oct 2017 00:02:59 GMT  
		Size: 213.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:fc2b072a68b1ce966d087589a733ae3bcdae5bae86a87514685551381cba07f7`  
		Last Modified: Tue, 10 Oct 2017 00:03:59 GMT  
		Size: 2.7 MB (2679426 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:58b5aa77f567a1f48fd4330791ccad8dfd3fc253242827b0bdb542f09ce6ea24`  
		Last Modified: Tue, 10 Oct 2017 00:03:59 GMT  
		Size: 1.3 KB (1284 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:6631b21dd7133ce0dee7db390449eb7531c9172eec2f5013dd1a3932d54f885b`  
		Last Modified: Tue, 10 Oct 2017 00:03:58 GMT  
		Size: 471.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:6ee4dfbed472dc58e234d5bdb206374277f6c6b3e3e684c15dd7ec6afd46e88e`  
		Last Modified: Tue, 10 Oct 2017 00:03:58 GMT  
		Size: 231.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:6d81fa28c2f426fba5560a1cda751278130e9becbcbcf17f06bc3a3832f45366`  
		Last Modified: Tue, 10 Oct 2017 00:03:58 GMT  
		Size: 511.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:2defc639c5f875919cee1be721360bc03e2a1be1675c030ea39c782bdaae5b6f`  
		Last Modified: Tue, 28 Nov 2017 13:24:40 GMT  
		Size: 12.5 MB (12547906 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:a3012d6eb6aecbcdf458103f678a9c390ae38e506bafb0e5d0319b0d566bacf1`  
		Last Modified: Tue, 28 Nov 2017 13:24:38 GMT  
		Size: 500.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:587c5d261c4034a59f987fcd0b1c119f297ac1dc300e52effa1eb94af597051c`  
		Last Modified: Tue, 28 Nov 2017 13:24:42 GMT  
		Size: 13.7 MB (13723864 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:976f84c98446d68ad6a55e0946a7b68e502abef467cb4d6eabeec0a12d1ec1bd`  
		Last Modified: Tue, 28 Nov 2017 13:24:39 GMT  
		Size: 2.2 KB (2182 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:5dbc4710393755f664625a2ff98e620d8e449c9a3d85cab8b64c8542f8f91c1e`  
		Last Modified: Tue, 28 Nov 2017 13:24:39 GMT  
		Size: 904.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:2240e017f52840d498de5c816805d953e61ec5727d7ad6d09edf948346c17847`  
		Last Modified: Tue, 28 Nov 2017 14:04:22 GMT  
		Size: 34.4 MB (34425257 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:ca58706ed439f7fd381f42974ff5599caef386ad4f3441b1448eea6f5d559d95`  
		Last Modified: Tue, 28 Nov 2017 14:04:12 GMT  
		Size: 1.8 MB (1770131 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:7453477ed7f836661a475c3032abe50374a8e79bbafe8bcf853ae231ffd00cd6`  
		Last Modified: Tue, 28 Nov 2017 14:04:11 GMT  
		Size: 354.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:95b6e44eeeb14c2eb81b401e44b236100944e5b022e92d7a2d56a66a76f4ad04`  
		Last Modified: Tue, 28 Nov 2017 14:04:10 GMT  
		Size: 314.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:6a6be31c9e2e84d365f5ff47157f18e7f0457175a8a3dee60e7f15326552888e`  
		Last Modified: Tue, 28 Nov 2017 14:04:10 GMT  
		Size: 1.3 MB (1329426 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:26ae2cb9ffc420124ef68128795a9e164918d9db74dbe328b25d4e40afc20b00`  
		Last Modified: Tue, 10 Oct 2017 02:04:26 GMT  
		Size: 137.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:a4247f4c2751d66ac6e554569a4128f120bb943784e9c093069542e0f7408fef`  
		Last Modified: Tue, 28 Nov 2017 14:06:38 GMT  
		Size: 47.0 MB (46970366 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:1117b9a99bcc4dfefebce6868b7a85b1f56d0282b8080759ad4f2be33427ebcb`  
		Last Modified: Tue, 28 Nov 2017 14:06:23 GMT  
		Size: 940.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:8e3a2b65ddc6acee785922de466430282442902f2f8a47a10dd02c9e2478ec75`  
		Last Modified: Tue, 28 Nov 2017 14:06:23 GMT  
		Size: 850.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip

### `nextcloud:latest` - linux; arm64 variant v8

```console
$ docker pull nextcloud@sha256:a0dbe726af165582ebb76a14d8ddf03288e271349ce8d0725fbf230fab97e1e9
```

-	Docker Version: 17.06.2-ce
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **230.1 MB (230060326 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:f99fe3e8b07d7d8cfa2052da4732cc89ca86967ca5ef6341de7a8e2ba9ffa613`
-	Entrypoint: `["\/entrypoint.sh"]`
-	Default Command: `["apache2-foreground"]`

```dockerfile
# Mon, 09 Oct 2017 21:43:13 GMT
ADD file:1661271485aa5a1ca074498b8ca025f41e547bf2b33335b108d9aaa06717b2a5 in / 
# Mon, 09 Oct 2017 21:43:14 GMT
CMD ["bash"]
# Tue, 10 Oct 2017 03:01:07 GMT
ENV PHPIZE_DEPS=autoconf 		dpkg-dev 		file 		g++ 		gcc 		libc-dev 		libpcre3-dev 		make 		pkg-config 		re2c
# Tue, 10 Oct 2017 03:02:43 GMT
RUN apt-get update && apt-get install -y 		$PHPIZE_DEPS 		ca-certificates 		curl 		libedit2 		libsqlite3-0 		libxml2 		xz-utils 	--no-install-recommends && rm -r /var/lib/apt/lists/*
# Tue, 10 Oct 2017 03:02:45 GMT
ENV PHP_INI_DIR=/usr/local/etc/php
# Tue, 10 Oct 2017 03:02:47 GMT
RUN mkdir -p $PHP_INI_DIR/conf.d
# Tue, 10 Oct 2017 03:12:18 GMT
RUN apt-get update 	&& apt-get install -y --no-install-recommends 		apache2 	&& rm -rf /var/lib/apt/lists/*
# Tue, 10 Oct 2017 03:12:19 GMT
ENV APACHE_CONFDIR=/etc/apache2
# Tue, 10 Oct 2017 03:12:20 GMT
ENV APACHE_ENVVARS=/etc/apache2/envvars
# Tue, 10 Oct 2017 03:12:21 GMT
RUN set -ex 		&& sed -ri 's/^export ([^=]+)=(.*)$/: ${\1:=\2}\nexport \1/' "$APACHE_ENVVARS" 		&& . "$APACHE_ENVVARS" 	&& for dir in 		"$APACHE_LOCK_DIR" 		"$APACHE_RUN_DIR" 		"$APACHE_LOG_DIR" 		/var/www/html 	; do 		rm -rvf "$dir" 		&& mkdir -p "$dir" 		&& chown -R "$APACHE_RUN_USER:$APACHE_RUN_GROUP" "$dir"; 	done
# Tue, 10 Oct 2017 03:12:23 GMT
RUN a2dismod mpm_event && a2enmod mpm_prefork
# Tue, 10 Oct 2017 03:12:25 GMT
RUN set -ex 	&& . "$APACHE_ENVVARS" 	&& ln -sfT /dev/stderr "$APACHE_LOG_DIR/error.log" 	&& ln -sfT /dev/stdout "$APACHE_LOG_DIR/access.log" 	&& ln -sfT /dev/stdout "$APACHE_LOG_DIR/other_vhosts_access.log"
# Tue, 10 Oct 2017 03:12:27 GMT
RUN { 		echo '<FilesMatch \.php$>'; 		echo '\tSetHandler application/x-httpd-php'; 		echo '</FilesMatch>'; 		echo; 		echo 'DirectoryIndex disabled'; 		echo 'DirectoryIndex index.php index.html'; 		echo; 		echo '<Directory /var/www/>'; 		echo '\tOptions -Indexes'; 		echo '\tAllowOverride All'; 		echo '</Directory>'; 	} | tee "$APACHE_CONFDIR/conf-available/docker-php.conf" 	&& a2enconf docker-php
# Tue, 10 Oct 2017 03:12:27 GMT
ENV PHP_EXTRA_BUILD_DEPS=apache2-dev
# Tue, 10 Oct 2017 03:12:28 GMT
ENV PHP_EXTRA_CONFIGURE_ARGS=--with-apxs2
# Tue, 10 Oct 2017 03:12:29 GMT
ENV PHP_CFLAGS=-fstack-protector-strong -fpic -fpie -O2
# Tue, 10 Oct 2017 03:12:30 GMT
ENV PHP_CPPFLAGS=-fstack-protector-strong -fpic -fpie -O2
# Tue, 10 Oct 2017 03:12:31 GMT
ENV PHP_LDFLAGS=-Wl,-O1 -Wl,--hash-style=both -pie
# Tue, 10 Oct 2017 03:12:31 GMT
ENV GPG_KEYS=A917B1ECDA84AEC2B568FED6F50ABC807BD5DCD0 528995BFEDFBA7191D46839EF9BA0ADA31CBD89E
# Tue, 28 Nov 2017 03:05:11 GMT
ENV PHP_VERSION=7.1.12
# Tue, 28 Nov 2017 03:05:11 GMT
ENV PHP_URL=https://secure.php.net/get/php-7.1.12.tar.xz/from/this/mirror PHP_ASC_URL=https://secure.php.net/get/php-7.1.12.tar.xz.asc/from/this/mirror
# Tue, 28 Nov 2017 03:05:12 GMT
ENV PHP_SHA256=a0118850774571b1f2d4e30b4fe7a4b958ca66f07d07d65ebdc789c54ba6eeb3 PHP_MD5=
# Tue, 28 Nov 2017 03:05:46 GMT
RUN set -xe; 		fetchDeps=' 		wget 	'; 	if ! command -v gpg > /dev/null; then 		fetchDeps="$fetchDeps 			dirmngr 			gnupg 		"; 	fi; 	apt-get update; 	apt-get install -y --no-install-recommends $fetchDeps; 	rm -rf /var/lib/apt/lists/*; 		mkdir -p /usr/src; 	cd /usr/src; 		wget -O php.tar.xz "$PHP_URL"; 		if [ -n "$PHP_SHA256" ]; then 		echo "$PHP_SHA256 *php.tar.xz" | sha256sum -c -; 	fi; 	if [ -n "$PHP_MD5" ]; then 		echo "$PHP_MD5 *php.tar.xz" | md5sum -c -; 	fi; 		if [ -n "$PHP_ASC_URL" ]; then 		wget -O php.tar.xz.asc "$PHP_ASC_URL"; 		export GNUPGHOME="$(mktemp -d)"; 		for key in $GPG_KEYS; do 			gpg --keyserver ha.pool.sks-keyservers.net --recv-keys "$key"; 		done; 		gpg --batch --verify php.tar.xz.asc php.tar.xz; 		rm -rf "$GNUPGHOME"; 	fi; 		apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false $fetchDeps
# Tue, 28 Nov 2017 03:05:47 GMT
COPY file:207c686e3fed4f71f8a7b245d8dcae9c9048d276a326d82b553c12a90af0c0ca in /usr/local/bin/ 
# Tue, 28 Nov 2017 03:10:48 GMT
RUN set -xe 	&& buildDeps=" 		$PHP_EXTRA_BUILD_DEPS 		libcurl4-openssl-dev 		libedit-dev 		libsqlite3-dev 		libssl-dev 		libxml2-dev 		zlib1g-dev 	" 	&& apt-get update && apt-get install -y $buildDeps --no-install-recommends && rm -rf /var/lib/apt/lists/* 		&& export CFLAGS="$PHP_CFLAGS" 		CPPFLAGS="$PHP_CPPFLAGS" 		LDFLAGS="$PHP_LDFLAGS" 	&& docker-php-source extract 	&& cd /usr/src/php 	&& gnuArch="$(dpkg-architecture --query DEB_BUILD_GNU_TYPE)" 	&& debMultiarch="$(dpkg-architecture --query DEB_BUILD_MULTIARCH)" 	&& if [ ! -d /usr/include/curl ]; then 		ln -sT "/usr/include/$debMultiarch/curl" /usr/local/include/curl; 	fi 	&& ./configure 		--build="$gnuArch" 		--with-config-file-path="$PHP_INI_DIR" 		--with-config-file-scan-dir="$PHP_INI_DIR/conf.d" 				--disable-cgi 				--enable-ftp 		--enable-mbstring 		--enable-mysqlnd 				--with-curl 		--with-libedit 		--with-openssl 		--with-zlib 				--with-pcre-regex=/usr 		--with-libdir="lib/$debMultiarch" 				$PHP_EXTRA_CONFIGURE_ARGS 	&& make -j "$(nproc)" 	&& make install 	&& { find /usr/local/bin /usr/local/sbin -type f -executable -exec strip --strip-all '{}' + || true; } 	&& make clean 	&& cd / 	&& docker-php-source delete 		&& apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false $buildDeps 		&& pecl update-channels 	&& rm -rf /tmp/pear ~/.pearrc
# Tue, 28 Nov 2017 03:10:49 GMT
COPY multi:dbabcc0b81566a75f49e7faa9ca5f96cd22a515b80ee7ea1e34fceceee3f9c2a in /usr/local/bin/ 
# Tue, 28 Nov 2017 03:10:50 GMT
ENTRYPOINT ["docker-php-entrypoint"]
# Tue, 28 Nov 2017 03:10:50 GMT
COPY file:24613ecbb1ce6a09f683b0753da9c26a1af07547326e8a02f6eec80ad6f2774a in /usr/local/bin/ 
# Tue, 28 Nov 2017 03:10:51 GMT
WORKDIR /var/www/html
# Tue, 28 Nov 2017 03:10:51 GMT
EXPOSE 80/tcp
# Tue, 28 Nov 2017 03:10:52 GMT
CMD ["apache2-foreground"]
# Tue, 28 Nov 2017 04:55:28 GMT
RUN apt-get update && apt-get install -y   rsync   bzip2   libcurl4-openssl-dev   libfreetype6-dev   libicu-dev   libjpeg-dev   libldap2-dev   libmcrypt-dev   libmemcached-dev   libpng12-dev   libpq-dev   libxml2-dev   && rm -rf /var/lib/apt/lists/*
# Tue, 28 Nov 2017 05:01:24 GMT
RUN debMultiarch="$(dpkg-architecture --query DEB_BUILD_MULTIARCH)"   && docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr   && docker-php-ext-configure ldap --with-libdir="lib/$debMultiarch"   && docker-php-ext-install gd exif intl mbstring mcrypt ldap mysqli opcache pdo_mysql pdo_pgsql pgsql zip pcntl
# Tue, 28 Nov 2017 05:01:26 GMT
RUN {   echo 'opcache.enable=1';   echo 'opcache.enable_cli=1';   echo 'opcache.interned_strings_buffer=8';   echo 'opcache.max_accelerated_files=10000';   echo 'opcache.memory_consumption=128';   echo 'opcache.save_comments=1';   echo 'opcache.revalidate_freq=1';   } > /usr/local/etc/php/conf.d/opcache-recommended.ini
# Tue, 28 Nov 2017 05:01:28 GMT
RUN a2enmod rewrite
# Tue, 28 Nov 2017 05:02:36 GMT
RUN set -ex  && pecl install APCu-5.1.8  && pecl install memcached-3.0.4  && pecl install redis-3.1.4  && docker-php-ext-enable apcu redis memcached
# Tue, 28 Nov 2017 05:02:38 GMT
RUN a2enmod rewrite
# Tue, 28 Nov 2017 05:12:45 GMT
ENV NEXTCLOUD_VERSION=12.0.3
# Tue, 28 Nov 2017 05:12:47 GMT
RUN chown -R www-data:root /var/www/html &&     chmod -R g=u /var/www/html
# Tue, 28 Nov 2017 05:12:48 GMT
VOLUME [/var/www/html]
# Tue, 28 Nov 2017 05:13:28 GMT
RUN curl -fsSL -o nextcloud.tar.bz2     "https://download.nextcloud.com/server/releases/nextcloud-${NEXTCLOUD_VERSION}.tar.bz2"  && curl -fsSL -o nextcloud.tar.bz2.asc     "https://download.nextcloud.com/server/releases/nextcloud-${NEXTCLOUD_VERSION}.tar.bz2.asc"  && export GNUPGHOME="$(mktemp -d)"  && gpg --keyserver ha.pool.sks-keyservers.net --recv-keys 28806A878AE423A28372792ED75899B9A724937A  && gpg --batch --verify nextcloud.tar.bz2.asc nextcloud.tar.bz2  && rm -r "$GNUPGHOME" nextcloud.tar.bz2.asc  && tar -xjf nextcloud.tar.bz2 -C /usr/src/  && rm nextcloud.tar.bz2  && rm -rf /usr/src/nextcloud/updater  && mkdir -p /usr/src/nextcloud/data  && mkdir -p /usr/src/nextcloud/custom_apps  && chmod +x /usr/src/nextcloud/occ
# Tue, 28 Nov 2017 05:13:31 GMT
COPY file:3fa42fa6664f03c90280a265050a78ef70bf32cd31864db727f5ee7e94828722 in /entrypoint.sh 
# Tue, 28 Nov 2017 05:13:33 GMT
COPY multi:a4ce16f733fa0a4cb4b62b3fe3229e71f5a6b970a03b912772780cdb452098f4 in /usr/src/nextcloud/config/ 
# Tue, 28 Nov 2017 05:13:34 GMT
ENTRYPOINT ["/entrypoint.sh"]
# Tue, 28 Nov 2017 05:13:35 GMT
CMD ["apache2-foreground"]
```

-	Layers:
	-	`sha256:abcff42ba939437677463734d9b81de5e60df7354c734ee3ddd879c0d3d5d595`  
		Last Modified: Mon, 09 Oct 2017 21:52:08 GMT  
		Size: 49.9 MB (49929310 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:566f7722328920229649e457c4c3f2ac00fbc51bf18e43b7e857a4bb929b14d3`  
		Last Modified: Tue, 10 Oct 2017 04:44:17 GMT  
		Size: 64.6 MB (64612700 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:336490976ea28a6a8a9bb6f3a9127ff718ef2f6b0ae5d00edc65504b2d61d00f`  
		Last Modified: Tue, 10 Oct 2017 04:43:16 GMT  
		Size: 183.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:b5dfd27021291ce354f213b19477dca9773fc1e56e213325ec2a820d746e2352`  
		Last Modified: Tue, 10 Oct 2017 04:46:10 GMT  
		Size: 2.8 MB (2788801 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:ab3ee4cd0d79dae5f32da9d943aa5e9c7f4d09d054780c65543e9af1cdd34eb5`  
		Last Modified: Tue, 10 Oct 2017 04:46:09 GMT  
		Size: 1.3 KB (1253 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:1b5530aefb17865ebab2db37820b31434bde95050efc2d0c10281fc07567c70a`  
		Last Modified: Tue, 10 Oct 2017 04:46:06 GMT  
		Size: 430.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:b640e2157bfabb87c7e4f4d15a7618d263128e48f2a7c5544050b30ba743f19b`  
		Last Modified: Tue, 10 Oct 2017 04:46:07 GMT  
		Size: 232.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:bcfe762267100f0627688ec8a9bba8612e0e698fe064150f0a41b9310bd45a5e`  
		Last Modified: Tue, 10 Oct 2017 04:46:06 GMT  
		Size: 491.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:0fe377fce93c4cafc5dbed044ad8c78f3fe1c69957effaf114f9bf990eef87e9`  
		Last Modified: Tue, 28 Nov 2017 04:01:17 GMT  
		Size: 12.5 MB (12547399 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:762041ad775058624d7ad034fd5c9b3ca38cfc4996c9898e1e9de6bd33f25e39`  
		Last Modified: Tue, 28 Nov 2017 04:01:15 GMT  
		Size: 502.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:dc32076308e2b31cf091823590e23d7037f03ac5ede0ea706fd107e08f9c7c28`  
		Last Modified: Tue, 28 Nov 2017 04:01:20 GMT  
		Size: 14.3 MB (14252557 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:8d46e03dab9c56f02411a2aa1ed78a3887418a5a70d9b3e8ede73eff870b6336`  
		Last Modified: Tue, 28 Nov 2017 04:01:15 GMT  
		Size: 2.2 KB (2182 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:a6d6c819bd7a1a96029c46e6a1282b9ec2e7496729d384e52f37160c8b9d8cdb`  
		Last Modified: Tue, 28 Nov 2017 04:01:15 GMT  
		Size: 904.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:69ee2e4fd25acd61fa301e4221ef8fad4ebafa318595c476e5bb07baa90c97d9`  
		Last Modified: Tue, 28 Nov 2017 05:15:40 GMT  
		Size: 35.8 MB (35760220 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:e84095537b372001c4c9bb8460c2aa6e25bff8069c25b798cbf85a978f174f5f`  
		Last Modified: Tue, 28 Nov 2017 05:15:28 GMT  
		Size: 1.8 MB (1817022 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:d20a202bd68d26aa533915e4e6b5272749115085e8c0fae3a0c65039410b47e7`  
		Last Modified: Tue, 28 Nov 2017 05:15:28 GMT  
		Size: 354.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:b74b57f8835c95ac69b2a5307b373a62bfb772c74b667e76eb16ed6759754d7f`  
		Last Modified: Tue, 28 Nov 2017 05:15:25 GMT  
		Size: 319.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:1558e8ddfbcc02465a268be2e6f715ebf4cf91e36a00f697ab1f8f3432dbc2ea`  
		Last Modified: Tue, 28 Nov 2017 05:15:26 GMT  
		Size: 1.4 MB (1373212 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:933725e4b3fce4f25b67188784d61225c4a5930539c8d5246f4f6248587b6b09`  
		Last Modified: Tue, 10 Oct 2017 13:24:44 GMT  
		Size: 138.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:4aea158441ac2b4f46393a79bffe3ebe96fd351c94f58b37226007cbf3f8b0ab`  
		Last Modified: Tue, 28 Nov 2017 05:19:35 GMT  
		Size: 47.0 MB (46970330 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:ecd7de8c38366d237189476c401d598e160438302e137b724b0b62782f01a446`  
		Last Modified: Tue, 28 Nov 2017 05:19:17 GMT  
		Size: 939.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:7f91534434344b129106091cffd860b032bf404dccff69a2f864291012246c88`  
		Last Modified: Tue, 28 Nov 2017 05:19:18 GMT  
		Size: 848.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip

### `nextcloud:latest` - linux; 386

```console
$ docker pull nextcloud@sha256:cd5367a17b7ff8c5590e55d44bb102553dfe2f72d36c4f02677ddbee3c1424ac
```

-	Docker Version: 17.06.2-ce
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **256.8 MB (256761731 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:ccd233bb4cc740599bcf73bd5632c0861f268ab0a5a019c996118844a254e3dd`
-	Entrypoint: `["\/entrypoint.sh"]`
-	Default Command: `["apache2-foreground"]`

```dockerfile
# Mon, 09 Oct 2017 21:42:15 GMT
ADD file:69555c5f78a887c075ee9d9449d85a723324e07872867c7f577e7fa99f6d41c0 in / 
# Mon, 09 Oct 2017 21:42:15 GMT
CMD ["bash"]
# Tue, 10 Oct 2017 00:46:25 GMT
ENV PHPIZE_DEPS=autoconf 		dpkg-dev 		file 		g++ 		gcc 		libc-dev 		libpcre3-dev 		make 		pkg-config 		re2c
# Tue, 10 Oct 2017 00:47:26 GMT
RUN apt-get update && apt-get install -y 		$PHPIZE_DEPS 		ca-certificates 		curl 		libedit2 		libsqlite3-0 		libxml2 		xz-utils 	--no-install-recommends && rm -r /var/lib/apt/lists/*
# Tue, 10 Oct 2017 00:47:26 GMT
ENV PHP_INI_DIR=/usr/local/etc/php
# Tue, 10 Oct 2017 00:48:10 GMT
RUN mkdir -p $PHP_INI_DIR/conf.d
# Tue, 10 Oct 2017 00:57:55 GMT
RUN apt-get update 	&& apt-get install -y --no-install-recommends 		apache2 	&& rm -rf /var/lib/apt/lists/*
# Tue, 10 Oct 2017 00:57:55 GMT
ENV APACHE_CONFDIR=/etc/apache2
# Tue, 10 Oct 2017 00:57:55 GMT
ENV APACHE_ENVVARS=/etc/apache2/envvars
# Tue, 10 Oct 2017 00:57:56 GMT
RUN set -ex 		&& sed -ri 's/^export ([^=]+)=(.*)$/: ${\1:=\2}\nexport \1/' "$APACHE_ENVVARS" 		&& . "$APACHE_ENVVARS" 	&& for dir in 		"$APACHE_LOCK_DIR" 		"$APACHE_RUN_DIR" 		"$APACHE_LOG_DIR" 		/var/www/html 	; do 		rm -rvf "$dir" 		&& mkdir -p "$dir" 		&& chown -R "$APACHE_RUN_USER:$APACHE_RUN_GROUP" "$dir"; 	done
# Tue, 10 Oct 2017 00:57:57 GMT
RUN a2dismod mpm_event && a2enmod mpm_prefork
# Tue, 10 Oct 2017 00:57:58 GMT
RUN set -ex 	&& . "$APACHE_ENVVARS" 	&& ln -sfT /dev/stderr "$APACHE_LOG_DIR/error.log" 	&& ln -sfT /dev/stdout "$APACHE_LOG_DIR/access.log" 	&& ln -sfT /dev/stdout "$APACHE_LOG_DIR/other_vhosts_access.log"
# Tue, 10 Oct 2017 00:57:59 GMT
RUN { 		echo '<FilesMatch \.php$>'; 		echo '\tSetHandler application/x-httpd-php'; 		echo '</FilesMatch>'; 		echo; 		echo 'DirectoryIndex disabled'; 		echo 'DirectoryIndex index.php index.html'; 		echo; 		echo '<Directory /var/www/>'; 		echo '\tOptions -Indexes'; 		echo '\tAllowOverride All'; 		echo '</Directory>'; 	} | tee "$APACHE_CONFDIR/conf-available/docker-php.conf" 	&& a2enconf docker-php
# Tue, 10 Oct 2017 00:57:59 GMT
ENV PHP_EXTRA_BUILD_DEPS=apache2-dev
# Tue, 10 Oct 2017 00:57:59 GMT
ENV PHP_EXTRA_CONFIGURE_ARGS=--with-apxs2
# Tue, 10 Oct 2017 00:58:00 GMT
ENV PHP_CFLAGS=-fstack-protector-strong -fpic -fpie -O2
# Tue, 10 Oct 2017 00:58:00 GMT
ENV PHP_CPPFLAGS=-fstack-protector-strong -fpic -fpie -O2
# Tue, 10 Oct 2017 00:58:00 GMT
ENV PHP_LDFLAGS=-Wl,-O1 -Wl,--hash-style=both -pie
# Tue, 10 Oct 2017 00:58:00 GMT
ENV GPG_KEYS=A917B1ECDA84AEC2B568FED6F50ABC807BD5DCD0 528995BFEDFBA7191D46839EF9BA0ADA31CBD89E
# Tue, 28 Nov 2017 09:59:35 GMT
ENV PHP_VERSION=7.1.12
# Tue, 28 Nov 2017 09:59:35 GMT
ENV PHP_URL=https://secure.php.net/get/php-7.1.12.tar.xz/from/this/mirror PHP_ASC_URL=https://secure.php.net/get/php-7.1.12.tar.xz.asc/from/this/mirror
# Tue, 28 Nov 2017 09:59:36 GMT
ENV PHP_SHA256=a0118850774571b1f2d4e30b4fe7a4b958ca66f07d07d65ebdc789c54ba6eeb3 PHP_MD5=
# Tue, 28 Nov 2017 10:00:11 GMT
RUN set -xe; 		fetchDeps=' 		wget 	'; 	if ! command -v gpg > /dev/null; then 		fetchDeps="$fetchDeps 			dirmngr 			gnupg 		"; 	fi; 	apt-get update; 	apt-get install -y --no-install-recommends $fetchDeps; 	rm -rf /var/lib/apt/lists/*; 		mkdir -p /usr/src; 	cd /usr/src; 		wget -O php.tar.xz "$PHP_URL"; 		if [ -n "$PHP_SHA256" ]; then 		echo "$PHP_SHA256 *php.tar.xz" | sha256sum -c -; 	fi; 	if [ -n "$PHP_MD5" ]; then 		echo "$PHP_MD5 *php.tar.xz" | md5sum -c -; 	fi; 		if [ -n "$PHP_ASC_URL" ]; then 		wget -O php.tar.xz.asc "$PHP_ASC_URL"; 		export GNUPGHOME="$(mktemp -d)"; 		for key in $GPG_KEYS; do 			gpg --keyserver ha.pool.sks-keyservers.net --recv-keys "$key"; 		done; 		gpg --batch --verify php.tar.xz.asc php.tar.xz; 		rm -rf "$GNUPGHOME"; 	fi; 		apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false $fetchDeps
# Tue, 28 Nov 2017 10:00:12 GMT
COPY file:207c686e3fed4f71f8a7b245d8dcae9c9048d276a326d82b553c12a90af0c0ca in /usr/local/bin/ 
# Tue, 28 Nov 2017 10:03:52 GMT
RUN set -xe 	&& buildDeps=" 		$PHP_EXTRA_BUILD_DEPS 		libcurl4-openssl-dev 		libedit-dev 		libsqlite3-dev 		libssl-dev 		libxml2-dev 		zlib1g-dev 	" 	&& apt-get update && apt-get install -y $buildDeps --no-install-recommends && rm -rf /var/lib/apt/lists/* 		&& export CFLAGS="$PHP_CFLAGS" 		CPPFLAGS="$PHP_CPPFLAGS" 		LDFLAGS="$PHP_LDFLAGS" 	&& docker-php-source extract 	&& cd /usr/src/php 	&& gnuArch="$(dpkg-architecture --query DEB_BUILD_GNU_TYPE)" 	&& debMultiarch="$(dpkg-architecture --query DEB_BUILD_MULTIARCH)" 	&& if [ ! -d /usr/include/curl ]; then 		ln -sT "/usr/include/$debMultiarch/curl" /usr/local/include/curl; 	fi 	&& ./configure 		--build="$gnuArch" 		--with-config-file-path="$PHP_INI_DIR" 		--with-config-file-scan-dir="$PHP_INI_DIR/conf.d" 				--disable-cgi 				--enable-ftp 		--enable-mbstring 		--enable-mysqlnd 				--with-curl 		--with-libedit 		--with-openssl 		--with-zlib 				--with-pcre-regex=/usr 		--with-libdir="lib/$debMultiarch" 				$PHP_EXTRA_CONFIGURE_ARGS 	&& make -j "$(nproc)" 	&& make install 	&& { find /usr/local/bin /usr/local/sbin -type f -executable -exec strip --strip-all '{}' + || true; } 	&& make clean 	&& cd / 	&& docker-php-source delete 		&& apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false $buildDeps 		&& pecl update-channels 	&& rm -rf /tmp/pear ~/.pearrc
# Tue, 28 Nov 2017 10:05:07 GMT
COPY multi:dbabcc0b81566a75f49e7faa9ca5f96cd22a515b80ee7ea1e34fceceee3f9c2a in /usr/local/bin/ 
# Tue, 28 Nov 2017 10:05:07 GMT
ENTRYPOINT ["docker-php-entrypoint"]
# Tue, 28 Nov 2017 10:05:08 GMT
COPY file:24613ecbb1ce6a09f683b0753da9c26a1af07547326e8a02f6eec80ad6f2774a in /usr/local/bin/ 
# Tue, 28 Nov 2017 10:05:08 GMT
WORKDIR /var/www/html
# Tue, 28 Nov 2017 10:05:08 GMT
EXPOSE 80/tcp
# Tue, 28 Nov 2017 10:05:08 GMT
CMD ["apache2-foreground"]
# Tue, 28 Nov 2017 12:02:56 GMT
RUN apt-get update && apt-get install -y   rsync   bzip2   libcurl4-openssl-dev   libfreetype6-dev   libicu-dev   libjpeg-dev   libldap2-dev   libmcrypt-dev   libmemcached-dev   libpng12-dev   libpq-dev   libxml2-dev   && rm -rf /var/lib/apt/lists/*
# Tue, 28 Nov 2017 12:05:45 GMT
RUN debMultiarch="$(dpkg-architecture --query DEB_BUILD_MULTIARCH)"   && docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr   && docker-php-ext-configure ldap --with-libdir="lib/$debMultiarch"   && docker-php-ext-install gd exif intl mbstring mcrypt ldap mysqli opcache pdo_mysql pdo_pgsql pgsql zip pcntl
# Tue, 28 Nov 2017 12:10:09 GMT
RUN {   echo 'opcache.enable=1';   echo 'opcache.enable_cli=1';   echo 'opcache.interned_strings_buffer=8';   echo 'opcache.max_accelerated_files=10000';   echo 'opcache.memory_consumption=128';   echo 'opcache.save_comments=1';   echo 'opcache.revalidate_freq=1';   } > /usr/local/etc/php/conf.d/opcache-recommended.ini
# Tue, 28 Nov 2017 12:10:10 GMT
RUN a2enmod rewrite
# Tue, 28 Nov 2017 12:10:52 GMT
RUN set -ex  && pecl install APCu-5.1.8  && pecl install memcached-3.0.4  && pecl install redis-3.1.4  && docker-php-ext-enable apcu redis memcached
# Tue, 28 Nov 2017 12:10:53 GMT
RUN a2enmod rewrite
# Tue, 28 Nov 2017 12:38:13 GMT
ENV NEXTCLOUD_VERSION=12.0.3
# Tue, 28 Nov 2017 12:38:14 GMT
RUN chown -R www-data:root /var/www/html &&     chmod -R g=u /var/www/html
# Tue, 28 Nov 2017 12:38:14 GMT
VOLUME [/var/www/html]
# Tue, 28 Nov 2017 12:38:34 GMT
RUN curl -fsSL -o nextcloud.tar.bz2     "https://download.nextcloud.com/server/releases/nextcloud-${NEXTCLOUD_VERSION}.tar.bz2"  && curl -fsSL -o nextcloud.tar.bz2.asc     "https://download.nextcloud.com/server/releases/nextcloud-${NEXTCLOUD_VERSION}.tar.bz2.asc"  && export GNUPGHOME="$(mktemp -d)"  && gpg --keyserver ha.pool.sks-keyservers.net --recv-keys 28806A878AE423A28372792ED75899B9A724937A  && gpg --batch --verify nextcloud.tar.bz2.asc nextcloud.tar.bz2  && rm -r "$GNUPGHOME" nextcloud.tar.bz2.asc  && tar -xjf nextcloud.tar.bz2 -C /usr/src/  && rm nextcloud.tar.bz2  && rm -rf /usr/src/nextcloud/updater  && mkdir -p /usr/src/nextcloud/data  && mkdir -p /usr/src/nextcloud/custom_apps  && chmod +x /usr/src/nextcloud/occ
# Tue, 28 Nov 2017 12:38:38 GMT
COPY file:3fa42fa6664f03c90280a265050a78ef70bf32cd31864db727f5ee7e94828722 in /entrypoint.sh 
# Tue, 28 Nov 2017 12:38:38 GMT
COPY multi:a4ce16f733fa0a4cb4b62b3fe3229e71f5a6b970a03b912772780cdb452098f4 in /usr/src/nextcloud/config/ 
# Tue, 28 Nov 2017 12:38:39 GMT
ENTRYPOINT ["/entrypoint.sh"]
# Tue, 28 Nov 2017 12:38:39 GMT
CMD ["apache2-foreground"]
```

-	Layers:
	-	`sha256:e0f8ffe748163b60817bbe75e602fd998e062587f8802da580ccdb711e5d6b6e`  
		Last Modified: Mon, 09 Oct 2017 21:48:11 GMT  
		Size: 52.8 MB (52773848 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:671377a40e7b26497e7f12a7eac26f6af150ea739eebde2bbba9d79637b86551`  
		Last Modified: Tue, 10 Oct 2017 02:12:39 GMT  
		Size: 83.9 MB (83886879 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:03f42450014c192b9a7782838f21339b652510d23b58558735a45cb0c723651b`  
		Last Modified: Tue, 10 Oct 2017 02:12:21 GMT  
		Size: 183.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:50a5c0800733c3b9785a87926d8034650a051c6a5a948cff91f66f1854bc4a1a`  
		Last Modified: Tue, 10 Oct 2017 02:13:37 GMT  
		Size: 3.1 MB (3118956 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:693c1c3f7bdaa4d80a14e4d22a1ee75c5fd791b9c6690f9579d6737e6b37f315`  
		Last Modified: Tue, 10 Oct 2017 02:13:36 GMT  
		Size: 1.3 KB (1254 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:92ff6ccd0fc5046c48d845d5b4107623c63a1b05af2d11c3d7971ddb9fcd9e26`  
		Last Modified: Tue, 10 Oct 2017 02:13:36 GMT  
		Size: 430.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:6a9ef5b58b8f674d4c2db1d3da274fbf82e3b689a8fc0491cc05a216aa88e85d`  
		Last Modified: Tue, 10 Oct 2017 02:13:36 GMT  
		Size: 231.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:77f9c00c5ca9ae3f811cd5023870c28b20189436ac36328e950cfbe7c3a014b0`  
		Last Modified: Tue, 10 Oct 2017 02:13:36 GMT  
		Size: 486.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:a4360b0b082660e26d1d6004aca98bf9fbbe90ea8eff394092d66c171769a07b`  
		Last Modified: Tue, 28 Nov 2017 11:18:20 GMT  
		Size: 12.5 MB (12548985 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:1f7e52e688a2bc97caa869b831ec603483633db323b07dfec804338f85222d25`  
		Last Modified: Tue, 28 Nov 2017 11:18:17 GMT  
		Size: 500.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:6e864de1a579ef6cac2637d0b7c3b93aa6bb19de34361db691c917898d20245b`  
		Last Modified: Tue, 28 Nov 2017 11:18:24 GMT  
		Size: 17.9 MB (17862992 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:3dcd9209bf085ef6c9719afca88ee11d2796bab231cdba1f3126278b50de8504`  
		Last Modified: Tue, 28 Nov 2017 11:18:17 GMT  
		Size: 2.2 KB (2182 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:f502da1fb5e0a2d60c4bffe7600eb60452db619a56f20d9e12e96ee12debc65a`  
		Last Modified: Tue, 28 Nov 2017 11:18:17 GMT  
		Size: 904.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:4cc5e0f808610dd43549ebe0477c3e1b80da22e9e3f42867566748266e7b0676`  
		Last Modified: Tue, 28 Nov 2017 12:40:58 GMT  
		Size: 36.4 MB (36366160 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:402f70ea59cd18e021703cd6bf3da4750fc47cdafb0f00a98b7ddaeaabe7948c`  
		Last Modified: Tue, 28 Nov 2017 12:40:33 GMT  
		Size: 1.9 MB (1939846 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:1573b7f75a51343f283f8794ab439fc18253cce10afb4153d5021eeef62618d1`  
		Last Modified: Tue, 28 Nov 2017 12:40:32 GMT  
		Size: 353.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:e07eab41315246122c03df7f8571a8b7dbc57e1086ac6d225a9692ac230aa825`  
		Last Modified: Tue, 28 Nov 2017 12:40:33 GMT  
		Size: 317.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:d651a5b00c3c1b79d4acebda5f63b4b7b053b54a027f162d22b11fcc6d35f9c0`  
		Last Modified: Tue, 28 Nov 2017 12:40:35 GMT  
		Size: 1.3 MB (1284963 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:5e0198dda9e85980966ddd041984764f5cf3069fd78778ba540dca3f5c2f7f36`  
		Last Modified: Tue, 10 Oct 2017 05:12:17 GMT  
		Size: 139.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:4fc1b4a0aacf710fb51ae754e7b1f50ac3f2828683a8f6edd5d8cb1a125a0122`  
		Last Modified: Tue, 28 Nov 2017 12:56:40 GMT  
		Size: 47.0 MB (46970329 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:a3f30e5f9c74b3c37184c42df12c98eea28f7759499de5344f1de3814cdf4ff7`  
		Last Modified: Tue, 28 Nov 2017 12:56:17 GMT  
		Size: 941.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:cd5021b6bd0cb6036048b086165e2db683dfb7a8cec3d88beb4c505cb8f92845`  
		Last Modified: Tue, 28 Nov 2017 12:56:17 GMT  
		Size: 853.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip

### `nextcloud:latest` - linux; ppc64le

```console
$ docker pull nextcloud@sha256:3d35fecbf57456c115d3e79e5a3786c60fc7a85d5b4f87875e28cbe18afa9489
```

-	Docker Version: 17.06.2-ce
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **239.3 MB (239254430 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:09ea097ea5c582783a64427a3bc0da4377c780793ccc6ad629768cbcaf564c0c`
-	Entrypoint: `["\/entrypoint.sh"]`
-	Default Command: `["apache2-foreground"]`

```dockerfile
# Mon, 09 Oct 2017 21:42:51 GMT
ADD file:c62750f1e0dbf2b729abca09eb7927f2ee4fa8311dc40ae8066a53a4f1c85059 in / 
# Mon, 09 Oct 2017 21:42:53 GMT
CMD ["bash"]
# Tue, 10 Oct 2017 04:59:32 GMT
ENV PHPIZE_DEPS=autoconf 		dpkg-dev 		file 		g++ 		gcc 		libc-dev 		libpcre3-dev 		make 		pkg-config 		re2c
# Tue, 10 Oct 2017 05:07:27 GMT
RUN apt-get update && apt-get install -y 		$PHPIZE_DEPS 		ca-certificates 		curl 		libedit2 		libsqlite3-0 		libxml2 		xz-utils 	--no-install-recommends && rm -r /var/lib/apt/lists/*
# Tue, 10 Oct 2017 05:07:31 GMT
ENV PHP_INI_DIR=/usr/local/etc/php
# Tue, 10 Oct 2017 05:07:38 GMT
RUN mkdir -p $PHP_INI_DIR/conf.d
# Tue, 10 Oct 2017 05:15:32 GMT
RUN apt-get update 	&& apt-get install -y --no-install-recommends 		apache2 	&& rm -rf /var/lib/apt/lists/*
# Tue, 10 Oct 2017 05:15:35 GMT
ENV APACHE_CONFDIR=/etc/apache2
# Tue, 10 Oct 2017 05:15:40 GMT
ENV APACHE_ENVVARS=/etc/apache2/envvars
# Tue, 10 Oct 2017 05:15:47 GMT
RUN set -ex 		&& sed -ri 's/^export ([^=]+)=(.*)$/: ${\1:=\2}\nexport \1/' "$APACHE_ENVVARS" 		&& . "$APACHE_ENVVARS" 	&& for dir in 		"$APACHE_LOCK_DIR" 		"$APACHE_RUN_DIR" 		"$APACHE_LOG_DIR" 		/var/www/html 	; do 		rm -rvf "$dir" 		&& mkdir -p "$dir" 		&& chown -R "$APACHE_RUN_USER:$APACHE_RUN_GROUP" "$dir"; 	done
# Tue, 10 Oct 2017 05:15:53 GMT
RUN a2dismod mpm_event && a2enmod mpm_prefork
# Tue, 10 Oct 2017 05:15:59 GMT
RUN set -ex 	&& . "$APACHE_ENVVARS" 	&& ln -sfT /dev/stderr "$APACHE_LOG_DIR/error.log" 	&& ln -sfT /dev/stdout "$APACHE_LOG_DIR/access.log" 	&& ln -sfT /dev/stdout "$APACHE_LOG_DIR/other_vhosts_access.log"
# Tue, 10 Oct 2017 05:16:13 GMT
RUN { 		echo '<FilesMatch \.php$>'; 		echo '\tSetHandler application/x-httpd-php'; 		echo '</FilesMatch>'; 		echo; 		echo 'DirectoryIndex disabled'; 		echo 'DirectoryIndex index.php index.html'; 		echo; 		echo '<Directory /var/www/>'; 		echo '\tOptions -Indexes'; 		echo '\tAllowOverride All'; 		echo '</Directory>'; 	} | tee "$APACHE_CONFDIR/conf-available/docker-php.conf" 	&& a2enconf docker-php
# Tue, 10 Oct 2017 05:16:15 GMT
ENV PHP_EXTRA_BUILD_DEPS=apache2-dev
# Tue, 10 Oct 2017 05:16:17 GMT
ENV PHP_EXTRA_CONFIGURE_ARGS=--with-apxs2
# Tue, 10 Oct 2017 05:16:19 GMT
ENV PHP_CFLAGS=-fstack-protector-strong -fpic -fpie -O2
# Tue, 10 Oct 2017 05:16:21 GMT
ENV PHP_CPPFLAGS=-fstack-protector-strong -fpic -fpie -O2
# Tue, 10 Oct 2017 05:16:23 GMT
ENV PHP_LDFLAGS=-Wl,-O1 -Wl,--hash-style=both -pie
# Tue, 10 Oct 2017 05:16:25 GMT
ENV GPG_KEYS=A917B1ECDA84AEC2B568FED6F50ABC807BD5DCD0 528995BFEDFBA7191D46839EF9BA0ADA31CBD89E
# Tue, 28 Nov 2017 09:54:01 GMT
ENV PHP_VERSION=7.1.12
# Tue, 28 Nov 2017 09:54:02 GMT
ENV PHP_URL=https://secure.php.net/get/php-7.1.12.tar.xz/from/this/mirror PHP_ASC_URL=https://secure.php.net/get/php-7.1.12.tar.xz.asc/from/this/mirror
# Tue, 28 Nov 2017 09:54:03 GMT
ENV PHP_SHA256=a0118850774571b1f2d4e30b4fe7a4b958ca66f07d07d65ebdc789c54ba6eeb3 PHP_MD5=
# Tue, 28 Nov 2017 09:54:43 GMT
RUN set -xe; 		fetchDeps=' 		wget 	'; 	if ! command -v gpg > /dev/null; then 		fetchDeps="$fetchDeps 			dirmngr 			gnupg 		"; 	fi; 	apt-get update; 	apt-get install -y --no-install-recommends $fetchDeps; 	rm -rf /var/lib/apt/lists/*; 		mkdir -p /usr/src; 	cd /usr/src; 		wget -O php.tar.xz "$PHP_URL"; 		if [ -n "$PHP_SHA256" ]; then 		echo "$PHP_SHA256 *php.tar.xz" | sha256sum -c -; 	fi; 	if [ -n "$PHP_MD5" ]; then 		echo "$PHP_MD5 *php.tar.xz" | md5sum -c -; 	fi; 		if [ -n "$PHP_ASC_URL" ]; then 		wget -O php.tar.xz.asc "$PHP_ASC_URL"; 		export GNUPGHOME="$(mktemp -d)"; 		for key in $GPG_KEYS; do 			gpg --keyserver ha.pool.sks-keyservers.net --recv-keys "$key"; 		done; 		gpg --batch --verify php.tar.xz.asc php.tar.xz; 		rm -rf "$GNUPGHOME"; 	fi; 		apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false $fetchDeps
# Tue, 28 Nov 2017 09:54:45 GMT
COPY file:207c686e3fed4f71f8a7b245d8dcae9c9048d276a326d82b553c12a90af0c0ca in /usr/local/bin/ 
# Tue, 28 Nov 2017 09:59:18 GMT
RUN set -xe 	&& buildDeps=" 		$PHP_EXTRA_BUILD_DEPS 		libcurl4-openssl-dev 		libedit-dev 		libsqlite3-dev 		libssl-dev 		libxml2-dev 		zlib1g-dev 	" 	&& apt-get update && apt-get install -y $buildDeps --no-install-recommends && rm -rf /var/lib/apt/lists/* 		&& export CFLAGS="$PHP_CFLAGS" 		CPPFLAGS="$PHP_CPPFLAGS" 		LDFLAGS="$PHP_LDFLAGS" 	&& docker-php-source extract 	&& cd /usr/src/php 	&& gnuArch="$(dpkg-architecture --query DEB_BUILD_GNU_TYPE)" 	&& debMultiarch="$(dpkg-architecture --query DEB_BUILD_MULTIARCH)" 	&& if [ ! -d /usr/include/curl ]; then 		ln -sT "/usr/include/$debMultiarch/curl" /usr/local/include/curl; 	fi 	&& ./configure 		--build="$gnuArch" 		--with-config-file-path="$PHP_INI_DIR" 		--with-config-file-scan-dir="$PHP_INI_DIR/conf.d" 				--disable-cgi 				--enable-ftp 		--enable-mbstring 		--enable-mysqlnd 				--with-curl 		--with-libedit 		--with-openssl 		--with-zlib 				--with-pcre-regex=/usr 		--with-libdir="lib/$debMultiarch" 				$PHP_EXTRA_CONFIGURE_ARGS 	&& make -j "$(nproc)" 	&& make install 	&& { find /usr/local/bin /usr/local/sbin -type f -executable -exec strip --strip-all '{}' + || true; } 	&& make clean 	&& cd / 	&& docker-php-source delete 		&& apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false $buildDeps 		&& pecl update-channels 	&& rm -rf /tmp/pear ~/.pearrc
# Tue, 28 Nov 2017 09:59:20 GMT
COPY multi:dbabcc0b81566a75f49e7faa9ca5f96cd22a515b80ee7ea1e34fceceee3f9c2a in /usr/local/bin/ 
# Tue, 28 Nov 2017 09:59:21 GMT
ENTRYPOINT ["docker-php-entrypoint"]
# Tue, 28 Nov 2017 09:59:22 GMT
COPY file:24613ecbb1ce6a09f683b0753da9c26a1af07547326e8a02f6eec80ad6f2774a in /usr/local/bin/ 
# Tue, 28 Nov 2017 09:59:23 GMT
WORKDIR /var/www/html
# Tue, 28 Nov 2017 09:59:24 GMT
EXPOSE 80/tcp
# Tue, 28 Nov 2017 09:59:25 GMT
CMD ["apache2-foreground"]
# Tue, 28 Nov 2017 11:07:10 GMT
RUN apt-get update && apt-get install -y   rsync   bzip2   libcurl4-openssl-dev   libfreetype6-dev   libicu-dev   libjpeg-dev   libldap2-dev   libmcrypt-dev   libmemcached-dev   libpng12-dev   libpq-dev   libxml2-dev   && rm -rf /var/lib/apt/lists/*
# Tue, 28 Nov 2017 11:10:48 GMT
RUN debMultiarch="$(dpkg-architecture --query DEB_BUILD_MULTIARCH)"   && docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr   && docker-php-ext-configure ldap --with-libdir="lib/$debMultiarch"   && docker-php-ext-install gd exif intl mbstring mcrypt ldap mysqli opcache pdo_mysql pdo_pgsql pgsql zip pcntl
# Tue, 28 Nov 2017 11:10:50 GMT
RUN {   echo 'opcache.enable=1';   echo 'opcache.enable_cli=1';   echo 'opcache.interned_strings_buffer=8';   echo 'opcache.max_accelerated_files=10000';   echo 'opcache.memory_consumption=128';   echo 'opcache.save_comments=1';   echo 'opcache.revalidate_freq=1';   } > /usr/local/etc/php/conf.d/opcache-recommended.ini
# Tue, 28 Nov 2017 11:10:53 GMT
RUN a2enmod rewrite
# Tue, 28 Nov 2017 11:11:36 GMT
RUN set -ex  && pecl install APCu-5.1.8  && pecl install memcached-3.0.4  && pecl install redis-3.1.4  && docker-php-ext-enable apcu redis memcached
# Tue, 28 Nov 2017 11:11:39 GMT
RUN a2enmod rewrite
# Tue, 28 Nov 2017 11:19:19 GMT
ENV NEXTCLOUD_VERSION=12.0.3
# Tue, 28 Nov 2017 11:19:22 GMT
RUN chown -R www-data:root /var/www/html &&     chmod -R g=u /var/www/html
# Tue, 28 Nov 2017 11:19:24 GMT
VOLUME [/var/www/html]
# Tue, 28 Nov 2017 11:19:59 GMT
RUN curl -fsSL -o nextcloud.tar.bz2     "https://download.nextcloud.com/server/releases/nextcloud-${NEXTCLOUD_VERSION}.tar.bz2"  && curl -fsSL -o nextcloud.tar.bz2.asc     "https://download.nextcloud.com/server/releases/nextcloud-${NEXTCLOUD_VERSION}.tar.bz2.asc"  && export GNUPGHOME="$(mktemp -d)"  && gpg --keyserver ha.pool.sks-keyservers.net --recv-keys 28806A878AE423A28372792ED75899B9A724937A  && gpg --batch --verify nextcloud.tar.bz2.asc nextcloud.tar.bz2  && rm -r "$GNUPGHOME" nextcloud.tar.bz2.asc  && tar -xjf nextcloud.tar.bz2 -C /usr/src/  && rm nextcloud.tar.bz2  && rm -rf /usr/src/nextcloud/updater  && mkdir -p /usr/src/nextcloud/data  && mkdir -p /usr/src/nextcloud/custom_apps  && chmod +x /usr/src/nextcloud/occ
# Tue, 28 Nov 2017 11:20:00 GMT
COPY file:3fa42fa6664f03c90280a265050a78ef70bf32cd31864db727f5ee7e94828722 in /entrypoint.sh 
# Tue, 28 Nov 2017 11:20:02 GMT
COPY multi:a4ce16f733fa0a4cb4b62b3fe3229e71f5a6b970a03b912772780cdb452098f4 in /usr/src/nextcloud/config/ 
# Tue, 28 Nov 2017 11:20:03 GMT
ENTRYPOINT ["/entrypoint.sh"]
# Tue, 28 Nov 2017 11:20:11 GMT
CMD ["apache2-foreground"]
```

-	Layers:
	-	`sha256:0f531bde4b154605e2d6339e50b65d65d06568d747b8bef594269dd06602062f`  
		Last Modified: Mon, 09 Oct 2017 21:48:50 GMT  
		Size: 51.8 MB (51809739 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:dc41d033d2921cba8c3fbd24aa09d8a180381ce21a996f56c5ba1b970a55b798`  
		Last Modified: Tue, 10 Oct 2017 06:45:18 GMT  
		Size: 70.0 MB (69979791 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:b6f923c00547c865a7523f58e49ceccbf4f04b88dc10b5cd3ee23729727731c2`  
		Last Modified: Tue, 10 Oct 2017 06:42:59 GMT  
		Size: 213.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:afc8808b95c3d4c76977c1f9665725fa3f91bcaef02d49caea930cf3f5a4156c`  
		Last Modified: Tue, 10 Oct 2017 06:46:09 GMT  
		Size: 2.9 MB (2908943 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:aaffaa1bcc18483f24a5c0f3cb479470ce42a1117d8450ac961edfd9af260168`  
		Last Modified: Tue, 10 Oct 2017 06:46:06 GMT  
		Size: 1.3 KB (1283 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:e6796076a2938f2fb85232af9197067b3e1d07d0fb3e13904fc27df0f065873b`  
		Last Modified: Tue, 10 Oct 2017 06:46:04 GMT  
		Size: 474.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:01602243d1dc9a2f49843681f0a849528e12248d5c70beceaa17f525d2d81a17`  
		Last Modified: Tue, 10 Oct 2017 06:46:04 GMT  
		Size: 231.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:ad2c9272a190e9de8d0a48c07cdd5abe6ff1756f10961c7c1227a7d44eb44ab0`  
		Last Modified: Tue, 10 Oct 2017 06:46:03 GMT  
		Size: 516.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:9fbd586e7aa289a5c57f6220a28fd9d97ca44c76a71dcff0454e4b04182f5d56`  
		Last Modified: Tue, 28 Nov 2017 10:30:39 GMT  
		Size: 12.5 MB (12548396 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:dac2cfc4672ee55f322de42bfc0c438d67b63edd638b26e9b0f5712ddb1e2bb9`  
		Last Modified: Tue, 28 Nov 2017 10:30:37 GMT  
		Size: 502.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:8607352884edfb1cea0abb0e744c0f49107ea299263e3a6a6a131f301a13545d`  
		Last Modified: Tue, 28 Nov 2017 10:30:41 GMT  
		Size: 15.1 MB (15144444 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:bd44447f48da9ec105d5662a9f91af0cdeabbe387c0f17d582a8f93699b8cbb6`  
		Last Modified: Tue, 28 Nov 2017 10:30:37 GMT  
		Size: 2.2 KB (2182 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:9e7d98d101879fb507c717a4e7d2a121b67a481ea3b2af85d1b79be331644853`  
		Last Modified: Tue, 28 Nov 2017 10:30:37 GMT  
		Size: 905.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:5d6cb27472450b03813989470b9a8ae23953d9d6dae2de335e8c53b6768f4433`  
		Last Modified: Tue, 28 Nov 2017 11:21:47 GMT  
		Size: 36.6 MB (36554557 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:9a429224b43e2b554cbf381ba35ef7c38a35a171fe0a393b2ea89cce83ea8c80`  
		Last Modified: Tue, 28 Nov 2017 11:21:34 GMT  
		Size: 1.9 MB (1927205 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:5f628de131e6c197d8f9a3dac40673e3334c3950826c4a61961cfbe81bd70a87`  
		Last Modified: Tue, 28 Nov 2017 11:21:32 GMT  
		Size: 356.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:6014a8121356c25d5b4251d6009da3637f3e8512962a17089f5f1fe77a5eb0ba`  
		Last Modified: Tue, 28 Nov 2017 11:21:30 GMT  
		Size: 318.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:63989078c0e6b53751a023a4a224f18ba41e63b7eb41d017b66f20ec4a97715d`  
		Last Modified: Tue, 28 Nov 2017 11:21:30 GMT  
		Size: 1.4 MB (1402077 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:d5a35f29a0041ee17e18b7651c4e29f3a759ecd658bb298a9b9b813215ce0b0e`  
		Last Modified: Tue, 10 Oct 2017 11:38:25 GMT  
		Size: 138.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:3666f8304fc657e959aa1242a6061b2ade1fd372602eb85802bef958f339fa12`  
		Last Modified: Tue, 28 Nov 2017 11:23:18 GMT  
		Size: 47.0 MB (46970370 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:41d3d8972b0fcd3a3ba51ede06a5f67324ff0843ac774bfa7ace9f9a77c999dc`  
		Last Modified: Tue, 28 Nov 2017 11:23:05 GMT  
		Size: 940.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:8fc4bf3fc5c1ece7f03c7e77678ea3721642c3a424d5a69429eb8442c798aecc`  
		Last Modified: Tue, 28 Nov 2017 11:23:06 GMT  
		Size: 850.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip

### `nextcloud:latest` - linux; s390x

```console
$ docker pull nextcloud@sha256:11b4e8be17aebb2f75c67987fcc9a2d3c9f9f002adc1a2a61162ce1a17864ff9
```

-	Docker Version: 17.06.1-ce
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **235.3 MB (235334461 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:0723af1cb4df84e4f3b69e6d905ee524f076db57f8897088ee846822d1de9209`
-	Entrypoint: `["\/entrypoint.sh"]`
-	Default Command: `["apache2-foreground"]`

```dockerfile
# Mon, 09 Oct 2017 21:42:23 GMT
ADD file:1c306ad85a0adf89bf603a6f6a34a1059ddfa0811704a847df3e785c487ee58f in / 
# Mon, 09 Oct 2017 21:42:24 GMT
CMD ["bash"]
# Mon, 09 Oct 2017 22:55:09 GMT
ENV PHPIZE_DEPS=autoconf 		dpkg-dev 		file 		g++ 		gcc 		libc-dev 		libpcre3-dev 		make 		pkg-config 		re2c
# Mon, 09 Oct 2017 22:55:37 GMT
RUN apt-get update && apt-get install -y 		$PHPIZE_DEPS 		ca-certificates 		curl 		libedit2 		libsqlite3-0 		libxml2 		xz-utils 	--no-install-recommends && rm -r /var/lib/apt/lists/*
# Mon, 09 Oct 2017 22:55:38 GMT
ENV PHP_INI_DIR=/usr/local/etc/php
# Mon, 09 Oct 2017 22:55:39 GMT
RUN mkdir -p $PHP_INI_DIR/conf.d
# Mon, 09 Oct 2017 22:59:30 GMT
RUN apt-get update 	&& apt-get install -y --no-install-recommends 		apache2 	&& rm -rf /var/lib/apt/lists/*
# Mon, 09 Oct 2017 22:59:31 GMT
ENV APACHE_CONFDIR=/etc/apache2
# Mon, 09 Oct 2017 22:59:31 GMT
ENV APACHE_ENVVARS=/etc/apache2/envvars
# Mon, 09 Oct 2017 22:59:31 GMT
RUN set -ex 		&& sed -ri 's/^export ([^=]+)=(.*)$/: ${\1:=\2}\nexport \1/' "$APACHE_ENVVARS" 		&& . "$APACHE_ENVVARS" 	&& for dir in 		"$APACHE_LOCK_DIR" 		"$APACHE_RUN_DIR" 		"$APACHE_LOG_DIR" 		/var/www/html 	; do 		rm -rvf "$dir" 		&& mkdir -p "$dir" 		&& chown -R "$APACHE_RUN_USER:$APACHE_RUN_GROUP" "$dir"; 	done
# Mon, 09 Oct 2017 22:59:32 GMT
RUN a2dismod mpm_event && a2enmod mpm_prefork
# Mon, 09 Oct 2017 22:59:33 GMT
RUN set -ex 	&& . "$APACHE_ENVVARS" 	&& ln -sfT /dev/stderr "$APACHE_LOG_DIR/error.log" 	&& ln -sfT /dev/stdout "$APACHE_LOG_DIR/access.log" 	&& ln -sfT /dev/stdout "$APACHE_LOG_DIR/other_vhosts_access.log"
# Mon, 09 Oct 2017 22:59:33 GMT
RUN { 		echo '<FilesMatch \.php$>'; 		echo '\tSetHandler application/x-httpd-php'; 		echo '</FilesMatch>'; 		echo; 		echo 'DirectoryIndex disabled'; 		echo 'DirectoryIndex index.php index.html'; 		echo; 		echo '<Directory /var/www/>'; 		echo '\tOptions -Indexes'; 		echo '\tAllowOverride All'; 		echo '</Directory>'; 	} | tee "$APACHE_CONFDIR/conf-available/docker-php.conf" 	&& a2enconf docker-php
# Mon, 09 Oct 2017 22:59:33 GMT
ENV PHP_EXTRA_BUILD_DEPS=apache2-dev
# Mon, 09 Oct 2017 22:59:34 GMT
ENV PHP_EXTRA_CONFIGURE_ARGS=--with-apxs2
# Mon, 09 Oct 2017 22:59:34 GMT
ENV PHP_CFLAGS=-fstack-protector-strong -fpic -fpie -O2
# Mon, 09 Oct 2017 22:59:34 GMT
ENV PHP_CPPFLAGS=-fstack-protector-strong -fpic -fpie -O2
# Mon, 09 Oct 2017 22:59:34 GMT
ENV PHP_LDFLAGS=-Wl,-O1 -Wl,--hash-style=both -pie
# Mon, 09 Oct 2017 22:59:34 GMT
ENV GPG_KEYS=A917B1ECDA84AEC2B568FED6F50ABC807BD5DCD0 528995BFEDFBA7191D46839EF9BA0ADA31CBD89E
# Tue, 28 Nov 2017 18:31:25 GMT
ENV PHP_VERSION=7.1.12
# Tue, 28 Nov 2017 18:31:26 GMT
ENV PHP_URL=https://secure.php.net/get/php-7.1.12.tar.xz/from/this/mirror PHP_ASC_URL=https://secure.php.net/get/php-7.1.12.tar.xz.asc/from/this/mirror
# Tue, 28 Nov 2017 18:31:26 GMT
ENV PHP_SHA256=a0118850774571b1f2d4e30b4fe7a4b958ca66f07d07d65ebdc789c54ba6eeb3 PHP_MD5=
# Tue, 28 Nov 2017 18:31:40 GMT
RUN set -xe; 		fetchDeps=' 		wget 	'; 	if ! command -v gpg > /dev/null; then 		fetchDeps="$fetchDeps 			dirmngr 			gnupg 		"; 	fi; 	apt-get update; 	apt-get install -y --no-install-recommends $fetchDeps; 	rm -rf /var/lib/apt/lists/*; 		mkdir -p /usr/src; 	cd /usr/src; 		wget -O php.tar.xz "$PHP_URL"; 		if [ -n "$PHP_SHA256" ]; then 		echo "$PHP_SHA256 *php.tar.xz" | sha256sum -c -; 	fi; 	if [ -n "$PHP_MD5" ]; then 		echo "$PHP_MD5 *php.tar.xz" | md5sum -c -; 	fi; 		if [ -n "$PHP_ASC_URL" ]; then 		wget -O php.tar.xz.asc "$PHP_ASC_URL"; 		export GNUPGHOME="$(mktemp -d)"; 		for key in $GPG_KEYS; do 			gpg --keyserver ha.pool.sks-keyservers.net --recv-keys "$key"; 		done; 		gpg --batch --verify php.tar.xz.asc php.tar.xz; 		rm -rf "$GNUPGHOME"; 	fi; 		apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false $fetchDeps
# Tue, 28 Nov 2017 18:31:40 GMT
COPY file:207c686e3fed4f71f8a7b245d8dcae9c9048d276a326d82b553c12a90af0c0ca in /usr/local/bin/ 
# Tue, 28 Nov 2017 18:33:39 GMT
RUN set -xe 	&& buildDeps=" 		$PHP_EXTRA_BUILD_DEPS 		libcurl4-openssl-dev 		libedit-dev 		libsqlite3-dev 		libssl-dev 		libxml2-dev 		zlib1g-dev 	" 	&& apt-get update && apt-get install -y $buildDeps --no-install-recommends && rm -rf /var/lib/apt/lists/* 		&& export CFLAGS="$PHP_CFLAGS" 		CPPFLAGS="$PHP_CPPFLAGS" 		LDFLAGS="$PHP_LDFLAGS" 	&& docker-php-source extract 	&& cd /usr/src/php 	&& gnuArch="$(dpkg-architecture --query DEB_BUILD_GNU_TYPE)" 	&& debMultiarch="$(dpkg-architecture --query DEB_BUILD_MULTIARCH)" 	&& if [ ! -d /usr/include/curl ]; then 		ln -sT "/usr/include/$debMultiarch/curl" /usr/local/include/curl; 	fi 	&& ./configure 		--build="$gnuArch" 		--with-config-file-path="$PHP_INI_DIR" 		--with-config-file-scan-dir="$PHP_INI_DIR/conf.d" 				--disable-cgi 				--enable-ftp 		--enable-mbstring 		--enable-mysqlnd 				--with-curl 		--with-libedit 		--with-openssl 		--with-zlib 				--with-pcre-regex=/usr 		--with-libdir="lib/$debMultiarch" 				$PHP_EXTRA_CONFIGURE_ARGS 	&& make -j "$(nproc)" 	&& make install 	&& { find /usr/local/bin /usr/local/sbin -type f -executable -exec strip --strip-all '{}' + || true; } 	&& make clean 	&& cd / 	&& docker-php-source delete 		&& apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false $buildDeps 		&& pecl update-channels 	&& rm -rf /tmp/pear ~/.pearrc
# Tue, 28 Nov 2017 18:33:40 GMT
COPY multi:dbabcc0b81566a75f49e7faa9ca5f96cd22a515b80ee7ea1e34fceceee3f9c2a in /usr/local/bin/ 
# Tue, 28 Nov 2017 18:33:40 GMT
ENTRYPOINT ["docker-php-entrypoint"]
# Tue, 28 Nov 2017 18:33:40 GMT
COPY file:24613ecbb1ce6a09f683b0753da9c26a1af07547326e8a02f6eec80ad6f2774a in /usr/local/bin/ 
# Tue, 28 Nov 2017 18:33:41 GMT
WORKDIR /var/www/html
# Tue, 28 Nov 2017 18:33:41 GMT
EXPOSE 80/tcp
# Tue, 28 Nov 2017 18:33:41 GMT
CMD ["apache2-foreground"]
# Tue, 28 Nov 2017 19:14:40 GMT
RUN apt-get update && apt-get install -y   rsync   bzip2   libcurl4-openssl-dev   libfreetype6-dev   libicu-dev   libjpeg-dev   libldap2-dev   libmcrypt-dev   libmemcached-dev   libpng12-dev   libpq-dev   libxml2-dev   && rm -rf /var/lib/apt/lists/*
# Tue, 28 Nov 2017 19:16:47 GMT
RUN debMultiarch="$(dpkg-architecture --query DEB_BUILD_MULTIARCH)"   && docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr   && docker-php-ext-configure ldap --with-libdir="lib/$debMultiarch"   && docker-php-ext-install gd exif intl mbstring mcrypt ldap mysqli opcache pdo_mysql pdo_pgsql pgsql zip pcntl
# Tue, 28 Nov 2017 19:16:48 GMT
RUN {   echo 'opcache.enable=1';   echo 'opcache.enable_cli=1';   echo 'opcache.interned_strings_buffer=8';   echo 'opcache.max_accelerated_files=10000';   echo 'opcache.memory_consumption=128';   echo 'opcache.save_comments=1';   echo 'opcache.revalidate_freq=1';   } > /usr/local/etc/php/conf.d/opcache-recommended.ini
# Tue, 28 Nov 2017 19:16:49 GMT
RUN a2enmod rewrite
# Tue, 28 Nov 2017 19:17:13 GMT
RUN set -ex  && pecl install APCu-5.1.8  && pecl install memcached-3.0.4  && pecl install redis-3.1.4  && docker-php-ext-enable apcu redis memcached
# Tue, 28 Nov 2017 19:17:13 GMT
RUN a2enmod rewrite
# Tue, 28 Nov 2017 19:21:36 GMT
ENV NEXTCLOUD_VERSION=12.0.3
# Tue, 28 Nov 2017 19:21:40 GMT
RUN chown -R www-data:root /var/www/html &&     chmod -R g=u /var/www/html
# Tue, 28 Nov 2017 19:21:40 GMT
VOLUME [/var/www/html]
# Tue, 28 Nov 2017 19:21:52 GMT
RUN curl -fsSL -o nextcloud.tar.bz2     "https://download.nextcloud.com/server/releases/nextcloud-${NEXTCLOUD_VERSION}.tar.bz2"  && curl -fsSL -o nextcloud.tar.bz2.asc     "https://download.nextcloud.com/server/releases/nextcloud-${NEXTCLOUD_VERSION}.tar.bz2.asc"  && export GNUPGHOME="$(mktemp -d)"  && gpg --keyserver ha.pool.sks-keyservers.net --recv-keys 28806A878AE423A28372792ED75899B9A724937A  && gpg --batch --verify nextcloud.tar.bz2.asc nextcloud.tar.bz2  && rm -r "$GNUPGHOME" nextcloud.tar.bz2.asc  && tar -xjf nextcloud.tar.bz2 -C /usr/src/  && rm nextcloud.tar.bz2  && rm -rf /usr/src/nextcloud/updater  && mkdir -p /usr/src/nextcloud/data  && mkdir -p /usr/src/nextcloud/custom_apps  && chmod +x /usr/src/nextcloud/occ
# Tue, 28 Nov 2017 19:21:52 GMT
COPY file:3fa42fa6664f03c90280a265050a78ef70bf32cd31864db727f5ee7e94828722 in /entrypoint.sh 
# Tue, 28 Nov 2017 19:21:56 GMT
COPY multi:a4ce16f733fa0a4cb4b62b3fe3229e71f5a6b970a03b912772780cdb452098f4 in /usr/src/nextcloud/config/ 
# Tue, 28 Nov 2017 19:21:57 GMT
ENTRYPOINT ["/entrypoint.sh"]
# Tue, 28 Nov 2017 19:22:01 GMT
CMD ["apache2-foreground"]
```

-	Layers:
	-	`sha256:a0a92d62c165393786de44f21509e9a71868aa7c2765f0334d285aa2aa19a58f`  
		Last Modified: Mon, 09 Oct 2017 21:46:27 GMT  
		Size: 52.8 MB (52788868 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:23fb66856860b5de241911f00d4159df363cf63a303d18ae7437e405aa3162e7`  
		Last Modified: Mon, 09 Oct 2017 23:36:47 GMT  
		Size: 64.0 MB (63980038 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:b38a4e89ae8f8496f476f2092ceb43def00c3fc728237b0f3ced18375fcc3431`  
		Last Modified: Mon, 09 Oct 2017 23:36:16 GMT  
		Size: 182.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:2fa08f5a322d716bc344e329f44d60ef75a976fd0ea5e530d59e527eeb8ecf40`  
		Last Modified: Mon, 09 Oct 2017 23:37:17 GMT  
		Size: 3.0 MB (3022574 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:bbf2af7622cabd637a262403d1aa90e8652eaf888035388a5660f2ef299f527e`  
		Last Modified: Mon, 09 Oct 2017 23:37:16 GMT  
		Size: 1.2 KB (1246 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:3dacb3b3a74e99a7a6559d4fe5b12de5023afcdc29fceda3e8efd5fd290a836a`  
		Last Modified: Mon, 09 Oct 2017 23:37:15 GMT  
		Size: 431.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:7b49a00cab668863e82ada97435faf0487a821fbddf62dfda16d67241390f3ba`  
		Last Modified: Mon, 09 Oct 2017 23:37:15 GMT  
		Size: 230.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:0226e5908d56361a72c804c781675ed4f60c645aadda58418219637e6872196b`  
		Last Modified: Mon, 09 Oct 2017 23:37:15 GMT  
		Size: 486.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:bb204bbe0e8b467fa1a1d2d754721849851d79a12f7631e7346729673d85aca8`  
		Last Modified: Tue, 28 Nov 2017 18:54:11 GMT  
		Size: 12.5 MB (12547145 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:dc33116c95825f9ce8958862653547addde14e0ed8bcea38ad309d486db96498`  
		Last Modified: Tue, 28 Nov 2017 18:54:10 GMT  
		Size: 502.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:9410870b611e7507b10295545507cb64d41a5782be2f9473ffba3f540a7f5f78`  
		Last Modified: Tue, 28 Nov 2017 18:54:13 GMT  
		Size: 15.8 MB (15846530 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:a67e6c6ff5dc1139cffe84102405bdef9aa89ed950d66a724bccd0163121a743`  
		Last Modified: Tue, 28 Nov 2017 18:54:10 GMT  
		Size: 2.2 KB (2183 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:660917ab3dcd1ac272fad7f05ca0ce76eb96c825645e233b499318188309288c`  
		Last Modified: Tue, 28 Nov 2017 18:54:10 GMT  
		Size: 904.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:684bb9e79aa6a84b3b461ab6ef31d09b6b5a0e1cafb44898f4ae43c10f078f98`  
		Last Modified: Tue, 28 Nov 2017 19:23:00 GMT  
		Size: 36.8 MB (36830389 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:8c275f2154b5cd9cad462b7ea304ba8426453353b752bb39f91a17b8dd114f33`  
		Last Modified: Tue, 28 Nov 2017 19:22:52 GMT  
		Size: 2.0 MB (1963789 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:7a44104513a4870bc19de6101a90b133de47906c64d26b3dba0366c011c85f32`  
		Last Modified: Tue, 28 Nov 2017 19:22:52 GMT  
		Size: 354.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:34e066966c9679bb50783e30aebb8607cda10c825dc9eeba582b3824efc6d70c`  
		Last Modified: Tue, 28 Nov 2017 19:22:51 GMT  
		Size: 315.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:ada488497f36473476d859d5f07cdc5a0924236cb18db3eb7700ea3033bf441d`  
		Last Modified: Tue, 28 Nov 2017 19:22:51 GMT  
		Size: 1.4 MB (1376060 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:d3bc3c673a57f294914083fc70c919c0f88a0529cc7d884606ca81d9118e475f`  
		Last Modified: Tue, 10 Oct 2017 01:15:24 GMT  
		Size: 137.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:55d64f3f12aac35999f51086b258ae1e37b4e4d436d25914ab4e9f8898e2d996`  
		Last Modified: Tue, 28 Nov 2017 19:24:13 GMT  
		Size: 47.0 MB (46970310 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:545fb6ff7c434c2ba7aa05d260ffb8709988796bccadbac42bc847488915af16`  
		Last Modified: Tue, 28 Nov 2017 19:24:05 GMT  
		Size: 939.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:2712d2f315b061af19b486d165e1f45a599f3ec85ee0edd3565ad4706ce21551`  
		Last Modified: Tue, 28 Nov 2017 19:24:04 GMT  
		Size: 849.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
