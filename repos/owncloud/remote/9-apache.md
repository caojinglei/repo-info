## `owncloud:9-apache`

```console
$ docker pull owncloud@sha256:35c9fdb61ce90c5b5ae38c0799551bd4c75a00c851f462952391cd2f08cee37e
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

### `owncloud:9-apache` - linux; amd64

```console
$ docker pull owncloud@sha256:fc0f7fb5ebf5525277c65d5debbd9cd676d36f3704399a0b4cdc304c1a1f4f13
```

-	Docker Version: 17.06.2-ce
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **233.0 MB (232974241 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:c40d23dab08ee103b82b4b7e3ff93a6a827ac52eecc521e650bef6f6582fc420`
-	Entrypoint: `["docker-entrypoint.sh"]`
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
# Sat, 04 Nov 2017 10:51:08 GMT
ENV GPG_KEYS=1A4E8B7277C42E53DBA9C7B9BCAA30EA9C0D5763 6E4F6AB321FDC07F2C332E3AC2BF0BC433CFC8B3
# Tue, 28 Nov 2017 00:41:36 GMT
ENV PHP_VERSION=7.0.26
# Tue, 28 Nov 2017 00:41:36 GMT
ENV PHP_URL=https://secure.php.net/get/php-7.0.26.tar.xz/from/this/mirror PHP_ASC_URL=https://secure.php.net/get/php-7.0.26.tar.xz.asc/from/this/mirror
# Tue, 28 Nov 2017 00:41:36 GMT
ENV PHP_SHA256=ed5cbb4bbb0ddef8985f100bba2e94002ad22a230b5da2dccfe148915df5f199 PHP_MD5=
# Tue, 28 Nov 2017 00:41:52 GMT
RUN set -xe; 		fetchDeps=' 		wget 	'; 	if ! command -v gpg > /dev/null; then 		fetchDeps="$fetchDeps 			dirmngr 			gnupg 		"; 	fi; 	apt-get update; 	apt-get install -y --no-install-recommends $fetchDeps; 	rm -rf /var/lib/apt/lists/*; 		mkdir -p /usr/src; 	cd /usr/src; 		wget -O php.tar.xz "$PHP_URL"; 		if [ -n "$PHP_SHA256" ]; then 		echo "$PHP_SHA256 *php.tar.xz" | sha256sum -c -; 	fi; 	if [ -n "$PHP_MD5" ]; then 		echo "$PHP_MD5 *php.tar.xz" | md5sum -c -; 	fi; 		if [ -n "$PHP_ASC_URL" ]; then 		wget -O php.tar.xz.asc "$PHP_ASC_URL"; 		export GNUPGHOME="$(mktemp -d)"; 		for key in $GPG_KEYS; do 			gpg --keyserver ha.pool.sks-keyservers.net --recv-keys "$key"; 		done; 		gpg --batch --verify php.tar.xz.asc php.tar.xz; 		rm -rf "$GNUPGHOME"; 	fi; 		apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false $fetchDeps
# Tue, 28 Nov 2017 00:41:52 GMT
COPY file:207c686e3fed4f71f8a7b245d8dcae9c9048d276a326d82b553c12a90af0c0ca in /usr/local/bin/ 
# Tue, 28 Nov 2017 00:44:35 GMT
RUN set -xe 	&& buildDeps=" 		$PHP_EXTRA_BUILD_DEPS 		libcurl4-openssl-dev 		libedit-dev 		libsqlite3-dev 		libssl-dev 		libxml2-dev 		zlib1g-dev 	" 	&& apt-get update && apt-get install -y $buildDeps --no-install-recommends && rm -rf /var/lib/apt/lists/* 		&& export CFLAGS="$PHP_CFLAGS" 		CPPFLAGS="$PHP_CPPFLAGS" 		LDFLAGS="$PHP_LDFLAGS" 	&& docker-php-source extract 	&& cd /usr/src/php 	&& gnuArch="$(dpkg-architecture --query DEB_BUILD_GNU_TYPE)" 	&& debMultiarch="$(dpkg-architecture --query DEB_BUILD_MULTIARCH)" 	&& if [ ! -d /usr/include/curl ]; then 		ln -sT "/usr/include/$debMultiarch/curl" /usr/local/include/curl; 	fi 	&& ./configure 		--build="$gnuArch" 		--with-config-file-path="$PHP_INI_DIR" 		--with-config-file-scan-dir="$PHP_INI_DIR/conf.d" 				--disable-cgi 				--enable-ftp 		--enable-mbstring 		--enable-mysqlnd 				--with-curl 		--with-libedit 		--with-openssl 		--with-zlib 				--with-pcre-regex=/usr 		--with-libdir="lib/$debMultiarch" 				$PHP_EXTRA_CONFIGURE_ARGS 	&& make -j "$(nproc)" 	&& make install 	&& { find /usr/local/bin /usr/local/sbin -type f -executable -exec strip --strip-all '{}' + || true; } 	&& make clean 	&& cd / 	&& docker-php-source delete 		&& apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false $buildDeps 		&& pecl update-channels 	&& rm -rf /tmp/pear ~/.pearrc
# Tue, 28 Nov 2017 00:44:36 GMT
COPY multi:dbabcc0b81566a75f49e7faa9ca5f96cd22a515b80ee7ea1e34fceceee3f9c2a in /usr/local/bin/ 
# Tue, 28 Nov 2017 00:44:36 GMT
ENTRYPOINT ["docker-php-entrypoint"]
# Tue, 28 Nov 2017 00:44:36 GMT
COPY file:24613ecbb1ce6a09f683b0753da9c26a1af07547326e8a02f6eec80ad6f2774a in /usr/local/bin/ 
# Tue, 28 Nov 2017 00:44:36 GMT
WORKDIR /var/www/html
# Tue, 28 Nov 2017 00:44:36 GMT
EXPOSE 80/tcp
# Tue, 28 Nov 2017 00:44:37 GMT
CMD ["apache2-foreground"]
# Tue, 28 Nov 2017 02:53:29 GMT
RUN apt-get update && apt-get install -y --no-install-recommends 		bzip2 		libcurl4-openssl-dev 		libfreetype6-dev 		libicu-dev 		libjpeg-dev 		libldap2-dev 		libmcrypt-dev 		libmemcached-dev 		libpng12-dev 		libpq-dev 		libxml2-dev 	&& rm -rf /var/lib/apt/lists/*
# Tue, 28 Nov 2017 02:55:35 GMT
RUN set -ex; 	docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr; 	debMultiarch="$(dpkg-architecture --query DEB_BUILD_MULTIARCH)"; 	docker-php-ext-configure ldap --with-libdir="lib/$debMultiarch"; 	docker-php-ext-install exif gd intl ldap mbstring mcrypt opcache pdo pdo_mysql pdo_pgsql pgsql zip
# Tue, 28 Nov 2017 02:55:36 GMT
RUN { 		echo 'opcache.memory_consumption=128'; 		echo 'opcache.interned_strings_buffer=8'; 		echo 'opcache.max_accelerated_files=4000'; 		echo 'opcache.revalidate_freq=60'; 		echo 'opcache.fast_shutdown=1'; 		echo 'opcache.enable_cli=1'; 	} > /usr/local/etc/php/conf.d/opcache-recommended.ini
# Tue, 28 Nov 2017 02:55:37 GMT
RUN a2enmod rewrite
# Tue, 28 Nov 2017 02:56:10 GMT
RUN set -ex 	&& pecl install APCu-5.1.8 	&& pecl install memcached-3.0.3 	&& pecl install redis-3.1.2 	&& docker-php-ext-enable apcu memcached redis
# Tue, 28 Nov 2017 03:07:19 GMT
ENV OWNCLOUD_VERSION=9.1.6
# Tue, 28 Nov 2017 03:07:20 GMT
VOLUME [/var/www/html]
# Tue, 28 Nov 2017 03:07:31 GMT
RUN curl -fsSL -o owncloud.tar.bz2 		"https://download.owncloud.org/community/owncloud-${OWNCLOUD_VERSION}.tar.bz2" 	&& curl -fsSL -o owncloud.tar.bz2.asc 		"https://download.owncloud.org/community/owncloud-${OWNCLOUD_VERSION}.tar.bz2.asc" 	&& export GNUPGHOME="$(mktemp -d)" 	&& gpg --keyserver ha.pool.sks-keyservers.net --recv-keys E3036906AD9F30807351FAC32D5D5E97F6978A26 	&& gpg --batch --verify owncloud.tar.bz2.asc owncloud.tar.bz2 	&& rm -r "$GNUPGHOME" owncloud.tar.bz2.asc 	&& tar -xjf owncloud.tar.bz2 -C /usr/src/ 	&& rm owncloud.tar.bz2
# Tue, 28 Nov 2017 03:07:32 GMT
COPY file:03fe90b626a097c27835e553f0b22ca55dc76d64d966006644b50609fffa4161 in /usr/local/bin/ 
# Tue, 28 Nov 2017 03:07:32 GMT
RUN ln -s usr/local/bin/docker-entrypoint.sh /entrypoint.sh # backwards compat
# Tue, 28 Nov 2017 03:07:32 GMT
ENTRYPOINT ["docker-entrypoint.sh"]
# Tue, 28 Nov 2017 03:07:33 GMT
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
	-	`sha256:a660c6abc97681691b11b60288d5bad2aa30e580f8852ed61788e534cf783a04`  
		Last Modified: Tue, 28 Nov 2017 01:35:46 GMT  
		Size: 12.3 MB (12321026 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:8612c8b55415d2b8dd7b644b1fb72bed8951066a0e6dd24bc194528f4c31f0e1`  
		Last Modified: Tue, 28 Nov 2017 01:35:45 GMT  
		Size: 502.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:156576fdc4d8c03900d7848b5f297b6aea45b2f94810c52f79cfe872a92ae8a7`  
		Last Modified: Tue, 28 Nov 2017 01:35:51 GMT  
		Size: 13.2 MB (13185904 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:553b63468cae9342a943b7d62e11c0e2df7860bc19e6e16d7bafa88af16fe8a6`  
		Last Modified: Tue, 28 Nov 2017 01:35:44 GMT  
		Size: 2.2 KB (2180 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:f2e4e437953bd11efbe794a31960841d722cf435a0f55be58d11277db376fc03`  
		Last Modified: Tue, 28 Nov 2017 01:35:45 GMT  
		Size: 904.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:2a8d21ae0e85e83f2ffe413dac0606f55ce09aa08046b41e3b2d7f2830dc5e33`  
		Last Modified: Tue, 28 Nov 2017 03:09:14 GMT  
		Size: 34.3 MB (34342328 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:8bef619ad00d222a38a1572345047d78ea2311821dc4e8e520d561fafafb8531`  
		Last Modified: Tue, 28 Nov 2017 03:09:07 GMT  
		Size: 1.8 MB (1814258 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:c1ce629c72510ae6230557aae5b71d48c31dbe388808bb2961d4437965d94a06`  
		Last Modified: Tue, 28 Nov 2017 03:09:03 GMT  
		Size: 356.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:97740fe4cee4577b25dbc6d6a8c35de5dc9601acc0cdb842f16f6be4677947cf`  
		Last Modified: Tue, 28 Nov 2017 03:09:05 GMT  
		Size: 313.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:3f47a80312c4fd8c2357065bb943f3c5b5cd8c05c48ab66867a8f3dd3cefc688`  
		Last Modified: Tue, 28 Nov 2017 03:09:04 GMT  
		Size: 1.3 MB (1328045 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:5a06dd1d27b18d4eec99d37ba3346ac763818f6b269f401ca7c098185793b166`  
		Last Modified: Tue, 28 Nov 2017 03:11:09 GMT  
		Size: 31.9 MB (31869744 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:7c9cc8eaac46e3e47faaf20a08a4ac3e659fc6091139f5c8295bae8cfe981a7f`  
		Last Modified: Tue, 28 Nov 2017 03:11:04 GMT  
		Size: 334.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:c95e66661af8f23e45f2fc7cbe053db51f090ba4e0ee0f03c17eec348b7e1ef4`  
		Last Modified: Tue, 28 Nov 2017 03:11:03 GMT  
		Size: 121.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip

### `owncloud:9-apache` - linux; arm variant v5

```console
$ docker pull owncloud@sha256:645c5b3d09e32d03bef08432bb0e02bbebdf585670b578009d2dcd33914d6ae8
```

-	Docker Version: 17.06.0-ce
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **213.0 MB (213030403 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:6ae989927e50d5532f981a4f5d9073470119600a81a9a19c4590fe9cb646dcbe`
-	Entrypoint: `["docker-entrypoint.sh"]`
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
# Mon, 09 Oct 2017 23:09:16 GMT
ENV GPG_KEYS=1A4E8B7277C42E53DBA9C7B9BCAA30EA9C0D5763 6E4F6AB321FDC07F2C332E3AC2BF0BC433CFC8B3
# Tue, 28 Nov 2017 14:59:11 GMT
ENV PHP_VERSION=7.0.26
# Tue, 28 Nov 2017 14:59:12 GMT
ENV PHP_URL=https://secure.php.net/get/php-7.0.26.tar.xz/from/this/mirror PHP_ASC_URL=https://secure.php.net/get/php-7.0.26.tar.xz.asc/from/this/mirror
# Tue, 28 Nov 2017 14:59:12 GMT
ENV PHP_SHA256=ed5cbb4bbb0ddef8985f100bba2e94002ad22a230b5da2dccfe148915df5f199 PHP_MD5=
# Tue, 28 Nov 2017 14:59:52 GMT
RUN set -xe; 		fetchDeps=' 		wget 	'; 	if ! command -v gpg > /dev/null; then 		fetchDeps="$fetchDeps 			dirmngr 			gnupg 		"; 	fi; 	apt-get update; 	apt-get install -y --no-install-recommends $fetchDeps; 	rm -rf /var/lib/apt/lists/*; 		mkdir -p /usr/src; 	cd /usr/src; 		wget -O php.tar.xz "$PHP_URL"; 		if [ -n "$PHP_SHA256" ]; then 		echo "$PHP_SHA256 *php.tar.xz" | sha256sum -c -; 	fi; 	if [ -n "$PHP_MD5" ]; then 		echo "$PHP_MD5 *php.tar.xz" | md5sum -c -; 	fi; 		if [ -n "$PHP_ASC_URL" ]; then 		wget -O php.tar.xz.asc "$PHP_ASC_URL"; 		export GNUPGHOME="$(mktemp -d)"; 		for key in $GPG_KEYS; do 			gpg --keyserver ha.pool.sks-keyservers.net --recv-keys "$key"; 		done; 		gpg --batch --verify php.tar.xz.asc php.tar.xz; 		rm -rf "$GNUPGHOME"; 	fi; 		apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false $fetchDeps
# Tue, 28 Nov 2017 14:59:52 GMT
COPY file:207c686e3fed4f71f8a7b245d8dcae9c9048d276a326d82b553c12a90af0c0ca in /usr/local/bin/ 
# Tue, 28 Nov 2017 15:02:47 GMT
RUN set -xe 	&& buildDeps=" 		$PHP_EXTRA_BUILD_DEPS 		libcurl4-openssl-dev 		libedit-dev 		libsqlite3-dev 		libssl-dev 		libxml2-dev 		zlib1g-dev 	" 	&& apt-get update && apt-get install -y $buildDeps --no-install-recommends && rm -rf /var/lib/apt/lists/* 		&& export CFLAGS="$PHP_CFLAGS" 		CPPFLAGS="$PHP_CPPFLAGS" 		LDFLAGS="$PHP_LDFLAGS" 	&& docker-php-source extract 	&& cd /usr/src/php 	&& gnuArch="$(dpkg-architecture --query DEB_BUILD_GNU_TYPE)" 	&& debMultiarch="$(dpkg-architecture --query DEB_BUILD_MULTIARCH)" 	&& if [ ! -d /usr/include/curl ]; then 		ln -sT "/usr/include/$debMultiarch/curl" /usr/local/include/curl; 	fi 	&& ./configure 		--build="$gnuArch" 		--with-config-file-path="$PHP_INI_DIR" 		--with-config-file-scan-dir="$PHP_INI_DIR/conf.d" 				--disable-cgi 				--enable-ftp 		--enable-mbstring 		--enable-mysqlnd 				--with-curl 		--with-libedit 		--with-openssl 		--with-zlib 				--with-pcre-regex=/usr 		--with-libdir="lib/$debMultiarch" 				$PHP_EXTRA_CONFIGURE_ARGS 	&& make -j "$(nproc)" 	&& make install 	&& { find /usr/local/bin /usr/local/sbin -type f -executable -exec strip --strip-all '{}' + || true; } 	&& make clean 	&& cd / 	&& docker-php-source delete 		&& apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false $buildDeps 		&& pecl update-channels 	&& rm -rf /tmp/pear ~/.pearrc
# Tue, 28 Nov 2017 15:02:48 GMT
COPY multi:dbabcc0b81566a75f49e7faa9ca5f96cd22a515b80ee7ea1e34fceceee3f9c2a in /usr/local/bin/ 
# Tue, 28 Nov 2017 15:02:48 GMT
ENTRYPOINT ["docker-php-entrypoint"]
# Tue, 28 Nov 2017 15:02:48 GMT
COPY file:24613ecbb1ce6a09f683b0753da9c26a1af07547326e8a02f6eec80ad6f2774a in /usr/local/bin/ 
# Tue, 28 Nov 2017 15:02:48 GMT
WORKDIR /var/www/html
# Tue, 28 Nov 2017 15:02:49 GMT
EXPOSE 80/tcp
# Tue, 28 Nov 2017 15:02:49 GMT
CMD ["apache2-foreground"]
# Tue, 28 Nov 2017 15:36:15 GMT
RUN apt-get update && apt-get install -y --no-install-recommends 		bzip2 		libcurl4-openssl-dev 		libfreetype6-dev 		libicu-dev 		libjpeg-dev 		libldap2-dev 		libmcrypt-dev 		libmemcached-dev 		libpng12-dev 		libpq-dev 		libxml2-dev 	&& rm -rf /var/lib/apt/lists/*
# Tue, 28 Nov 2017 15:40:34 GMT
RUN set -ex; 	docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr; 	debMultiarch="$(dpkg-architecture --query DEB_BUILD_MULTIARCH)"; 	docker-php-ext-configure ldap --with-libdir="lib/$debMultiarch"; 	docker-php-ext-install exif gd intl ldap mbstring mcrypt opcache pdo pdo_mysql pdo_pgsql pgsql zip
# Tue, 28 Nov 2017 15:40:35 GMT
RUN { 		echo 'opcache.memory_consumption=128'; 		echo 'opcache.interned_strings_buffer=8'; 		echo 'opcache.max_accelerated_files=4000'; 		echo 'opcache.revalidate_freq=60'; 		echo 'opcache.fast_shutdown=1'; 		echo 'opcache.enable_cli=1'; 	} > /usr/local/etc/php/conf.d/opcache-recommended.ini
# Tue, 28 Nov 2017 15:40:36 GMT
RUN a2enmod rewrite
# Tue, 28 Nov 2017 15:41:28 GMT
RUN set -ex 	&& pecl install APCu-5.1.8 	&& pecl install memcached-3.0.3 	&& pecl install redis-3.1.2 	&& docker-php-ext-enable apcu memcached redis
# Tue, 28 Nov 2017 15:48:32 GMT
ENV OWNCLOUD_VERSION=9.1.6
# Tue, 28 Nov 2017 15:48:32 GMT
VOLUME [/var/www/html]
# Tue, 28 Nov 2017 15:48:48 GMT
RUN curl -fsSL -o owncloud.tar.bz2 		"https://download.owncloud.org/community/owncloud-${OWNCLOUD_VERSION}.tar.bz2" 	&& curl -fsSL -o owncloud.tar.bz2.asc 		"https://download.owncloud.org/community/owncloud-${OWNCLOUD_VERSION}.tar.bz2.asc" 	&& export GNUPGHOME="$(mktemp -d)" 	&& gpg --keyserver ha.pool.sks-keyservers.net --recv-keys E3036906AD9F30807351FAC32D5D5E97F6978A26 	&& gpg --batch --verify owncloud.tar.bz2.asc owncloud.tar.bz2 	&& rm -r "$GNUPGHOME" owncloud.tar.bz2.asc 	&& tar -xjf owncloud.tar.bz2 -C /usr/src/ 	&& rm owncloud.tar.bz2
# Tue, 28 Nov 2017 15:48:49 GMT
COPY file:03fe90b626a097c27835e553f0b22ca55dc76d64d966006644b50609fffa4161 in /usr/local/bin/ 
# Tue, 28 Nov 2017 15:48:50 GMT
RUN ln -s usr/local/bin/docker-entrypoint.sh /entrypoint.sh # backwards compat
# Tue, 28 Nov 2017 15:48:50 GMT
ENTRYPOINT ["docker-entrypoint.sh"]
# Tue, 28 Nov 2017 15:48:50 GMT
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
	-	`sha256:e5433685a2ac55bedb2dec5ac05aa45b40165fb1f738321b0d93e5dd793c9294`  
		Last Modified: Tue, 28 Nov 2017 15:18:09 GMT  
		Size: 12.3 MB (12319382 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:03351b1f8c1ad1db9d99b923c2cf16445752000712bfabe0c9726070a051f3dc`  
		Last Modified: Tue, 28 Nov 2017 15:18:07 GMT  
		Size: 502.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:ef96886ca5738520083c36451119cff6e9fdbe93fed764b0eefa80185418ed3c`  
		Last Modified: Tue, 28 Nov 2017 15:18:12 GMT  
		Size: 14.2 MB (14213933 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:c19c2bb1e291fc379dcad1d6899c9be155edd305bca0aa30ff85dbc4f90b5574`  
		Last Modified: Tue, 28 Nov 2017 15:18:07 GMT  
		Size: 2.2 KB (2181 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:3cb8f4c8de8e51225be1ef09807f00a85f50f9560e89b22e0d8ff04eea38da62`  
		Last Modified: Tue, 28 Nov 2017 15:18:07 GMT  
		Size: 906.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:d5bf91bd565666fe84b714267436f2802f5873aff81bebc2579d5b0f3211bb50`  
		Last Modified: Tue, 28 Nov 2017 15:50:51 GMT  
		Size: 34.3 MB (34262931 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:6703695e180cb81c59e55d9643737d72d4388e0201f0b60610ec9b9400fa4241`  
		Last Modified: Tue, 28 Nov 2017 15:50:40 GMT  
		Size: 1.7 MB (1745006 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:d73082eddb9bcecfe02ac37bc4d9b6807a21fecf58f11f2fb41d46b94c885b34`  
		Last Modified: Tue, 28 Nov 2017 15:50:38 GMT  
		Size: 354.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:ef68080f916bbc5167480e8d685473a65b530aa3a19639a09334a29f0c266337`  
		Last Modified: Tue, 28 Nov 2017 15:50:39 GMT  
		Size: 313.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:61a2ce7a431dfe9e210f39869fda1b772a28d5ed625a28330d69de35ade3f340`  
		Last Modified: Tue, 28 Nov 2017 15:50:39 GMT  
		Size: 1.4 MB (1381145 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:5558749e0efd49f9e09b67a1934980f454a9d10cf73e2e82bef09deaf2dd96a4`  
		Last Modified: Tue, 28 Nov 2017 15:53:23 GMT  
		Size: 31.9 MB (31869499 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:c4b2d7da4f2dea6c247275648a90fbc218fc3120fbf3652047a2708fb8e82c33`  
		Last Modified: Tue, 28 Nov 2017 15:53:13 GMT  
		Size: 338.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:272f216b162e4bb755fc53f5e297ccd9b4e12c49fda7d8de086f94201a5a0415`  
		Last Modified: Tue, 28 Nov 2017 15:53:11 GMT  
		Size: 121.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip

### `owncloud:9-apache` - linux; arm variant v7

```console
$ docker pull owncloud@sha256:1cf9c6d5828742ae1aa60cab4950d262ee71bcc960c530de231cc45c48d726ef
```

-	Docker Version: 17.06.0-ce
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **208.6 MB (208551671 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:fcf62283382a1e2f2005c4669ad63c8f06c27ea0742fafaf36d4376388a35c5a`
-	Entrypoint: `["docker-entrypoint.sh"]`
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
# Mon, 09 Oct 2017 23:32:28 GMT
ENV GPG_KEYS=1A4E8B7277C42E53DBA9C7B9BCAA30EA9C0D5763 6E4F6AB321FDC07F2C332E3AC2BF0BC433CFC8B3
# Tue, 28 Nov 2017 13:09:29 GMT
ENV PHP_VERSION=7.0.26
# Tue, 28 Nov 2017 13:09:29 GMT
ENV PHP_URL=https://secure.php.net/get/php-7.0.26.tar.xz/from/this/mirror PHP_ASC_URL=https://secure.php.net/get/php-7.0.26.tar.xz.asc/from/this/mirror
# Tue, 28 Nov 2017 13:09:29 GMT
ENV PHP_SHA256=ed5cbb4bbb0ddef8985f100bba2e94002ad22a230b5da2dccfe148915df5f199 PHP_MD5=
# Tue, 28 Nov 2017 13:10:08 GMT
RUN set -xe; 		fetchDeps=' 		wget 	'; 	if ! command -v gpg > /dev/null; then 		fetchDeps="$fetchDeps 			dirmngr 			gnupg 		"; 	fi; 	apt-get update; 	apt-get install -y --no-install-recommends $fetchDeps; 	rm -rf /var/lib/apt/lists/*; 		mkdir -p /usr/src; 	cd /usr/src; 		wget -O php.tar.xz "$PHP_URL"; 		if [ -n "$PHP_SHA256" ]; then 		echo "$PHP_SHA256 *php.tar.xz" | sha256sum -c -; 	fi; 	if [ -n "$PHP_MD5" ]; then 		echo "$PHP_MD5 *php.tar.xz" | md5sum -c -; 	fi; 		if [ -n "$PHP_ASC_URL" ]; then 		wget -O php.tar.xz.asc "$PHP_ASC_URL"; 		export GNUPGHOME="$(mktemp -d)"; 		for key in $GPG_KEYS; do 			gpg --keyserver ha.pool.sks-keyservers.net --recv-keys "$key"; 		done; 		gpg --batch --verify php.tar.xz.asc php.tar.xz; 		rm -rf "$GNUPGHOME"; 	fi; 		apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false $fetchDeps
# Tue, 28 Nov 2017 13:10:09 GMT
COPY file:207c686e3fed4f71f8a7b245d8dcae9c9048d276a326d82b553c12a90af0c0ca in /usr/local/bin/ 
# Tue, 28 Nov 2017 13:12:46 GMT
RUN set -xe 	&& buildDeps=" 		$PHP_EXTRA_BUILD_DEPS 		libcurl4-openssl-dev 		libedit-dev 		libsqlite3-dev 		libssl-dev 		libxml2-dev 		zlib1g-dev 	" 	&& apt-get update && apt-get install -y $buildDeps --no-install-recommends && rm -rf /var/lib/apt/lists/* 		&& export CFLAGS="$PHP_CFLAGS" 		CPPFLAGS="$PHP_CPPFLAGS" 		LDFLAGS="$PHP_LDFLAGS" 	&& docker-php-source extract 	&& cd /usr/src/php 	&& gnuArch="$(dpkg-architecture --query DEB_BUILD_GNU_TYPE)" 	&& debMultiarch="$(dpkg-architecture --query DEB_BUILD_MULTIARCH)" 	&& if [ ! -d /usr/include/curl ]; then 		ln -sT "/usr/include/$debMultiarch/curl" /usr/local/include/curl; 	fi 	&& ./configure 		--build="$gnuArch" 		--with-config-file-path="$PHP_INI_DIR" 		--with-config-file-scan-dir="$PHP_INI_DIR/conf.d" 				--disable-cgi 				--enable-ftp 		--enable-mbstring 		--enable-mysqlnd 				--with-curl 		--with-libedit 		--with-openssl 		--with-zlib 				--with-pcre-regex=/usr 		--with-libdir="lib/$debMultiarch" 				$PHP_EXTRA_CONFIGURE_ARGS 	&& make -j "$(nproc)" 	&& make install 	&& { find /usr/local/bin /usr/local/sbin -type f -executable -exec strip --strip-all '{}' + || true; } 	&& make clean 	&& cd / 	&& docker-php-source delete 		&& apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false $buildDeps 		&& pecl update-channels 	&& rm -rf /tmp/pear ~/.pearrc
# Tue, 28 Nov 2017 13:12:47 GMT
COPY multi:dbabcc0b81566a75f49e7faa9ca5f96cd22a515b80ee7ea1e34fceceee3f9c2a in /usr/local/bin/ 
# Tue, 28 Nov 2017 13:12:47 GMT
ENTRYPOINT ["docker-php-entrypoint"]
# Tue, 28 Nov 2017 13:12:48 GMT
COPY file:24613ecbb1ce6a09f683b0753da9c26a1af07547326e8a02f6eec80ad6f2774a in /usr/local/bin/ 
# Tue, 28 Nov 2017 13:12:48 GMT
WORKDIR /var/www/html
# Tue, 28 Nov 2017 13:12:48 GMT
EXPOSE 80/tcp
# Tue, 28 Nov 2017 13:12:48 GMT
CMD ["apache2-foreground"]
# Tue, 28 Nov 2017 13:49:28 GMT
RUN apt-get update && apt-get install -y --no-install-recommends 		bzip2 		libcurl4-openssl-dev 		libfreetype6-dev 		libicu-dev 		libjpeg-dev 		libldap2-dev 		libmcrypt-dev 		libmemcached-dev 		libpng12-dev 		libpq-dev 		libxml2-dev 	&& rm -rf /var/lib/apt/lists/*
# Tue, 28 Nov 2017 13:53:22 GMT
RUN set -ex; 	docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr; 	debMultiarch="$(dpkg-architecture --query DEB_BUILD_MULTIARCH)"; 	docker-php-ext-configure ldap --with-libdir="lib/$debMultiarch"; 	docker-php-ext-install exif gd intl ldap mbstring mcrypt opcache pdo pdo_mysql pdo_pgsql pgsql zip
# Tue, 28 Nov 2017 13:53:23 GMT
RUN { 		echo 'opcache.memory_consumption=128'; 		echo 'opcache.interned_strings_buffer=8'; 		echo 'opcache.max_accelerated_files=4000'; 		echo 'opcache.revalidate_freq=60'; 		echo 'opcache.fast_shutdown=1'; 		echo 'opcache.enable_cli=1'; 	} > /usr/local/etc/php/conf.d/opcache-recommended.ini
# Tue, 28 Nov 2017 13:53:25 GMT
RUN a2enmod rewrite
# Tue, 28 Nov 2017 13:54:13 GMT
RUN set -ex 	&& pecl install APCu-5.1.8 	&& pecl install memcached-3.0.3 	&& pecl install redis-3.1.2 	&& docker-php-ext-enable apcu memcached redis
# Tue, 28 Nov 2017 14:03:39 GMT
ENV OWNCLOUD_VERSION=9.1.6
# Tue, 28 Nov 2017 14:03:39 GMT
VOLUME [/var/www/html]
# Tue, 28 Nov 2017 14:03:55 GMT
RUN curl -fsSL -o owncloud.tar.bz2 		"https://download.owncloud.org/community/owncloud-${OWNCLOUD_VERSION}.tar.bz2" 	&& curl -fsSL -o owncloud.tar.bz2.asc 		"https://download.owncloud.org/community/owncloud-${OWNCLOUD_VERSION}.tar.bz2.asc" 	&& export GNUPGHOME="$(mktemp -d)" 	&& gpg --keyserver ha.pool.sks-keyservers.net --recv-keys E3036906AD9F30807351FAC32D5D5E97F6978A26 	&& gpg --batch --verify owncloud.tar.bz2.asc owncloud.tar.bz2 	&& rm -r "$GNUPGHOME" owncloud.tar.bz2.asc 	&& tar -xjf owncloud.tar.bz2 -C /usr/src/ 	&& rm owncloud.tar.bz2
# Tue, 28 Nov 2017 14:03:56 GMT
COPY file:03fe90b626a097c27835e553f0b22ca55dc76d64d966006644b50609fffa4161 in /usr/local/bin/ 
# Tue, 28 Nov 2017 14:03:58 GMT
RUN ln -s usr/local/bin/docker-entrypoint.sh /entrypoint.sh # backwards compat
# Tue, 28 Nov 2017 14:03:58 GMT
ENTRYPOINT ["docker-entrypoint.sh"]
# Tue, 28 Nov 2017 14:03:58 GMT
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
	-	`sha256:03b5fb54e517f368a853edb0df6f12180ad769e9c0419d2eea42baa3536acc67`  
		Last Modified: Tue, 28 Nov 2017 13:30:07 GMT  
		Size: 12.3 MB (12319355 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:fcb2ed3f64211d88e87501f813ee3ff0a33bc025ceeedca059f27cb599d8c477`  
		Last Modified: Tue, 28 Nov 2017 13:30:05 GMT  
		Size: 499.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:6ec3a947f3e080cdd26387fe9b31bd0a40b92f801e545d3821a4632798b936c0`  
		Last Modified: Tue, 28 Nov 2017 13:30:09 GMT  
		Size: 13.5 MB (13468633 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:d84f831f0141b7700439c423f016dffd77bf63b79c1f9b09d80aecdb652b9216`  
		Last Modified: Tue, 28 Nov 2017 13:30:05 GMT  
		Size: 2.2 KB (2180 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:48641ae66abe5361d27a80b7d37f319ad05723e2dc777c4657fbac3b78f27ff0`  
		Last Modified: Tue, 28 Nov 2017 13:30:05 GMT  
		Size: 903.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:62264bc7aaf96c53e028c2af9cb62574e3441cc9efe48b28422a6b5bf5d9a86a`  
		Last Modified: Tue, 28 Nov 2017 14:11:12 GMT  
		Size: 32.7 MB (32675666 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:22c4cf40e946c4cb145d0385904e7aeef93c66adbde2e5c2edf76faf5acffc71`  
		Last Modified: Tue, 28 Nov 2017 14:11:03 GMT  
		Size: 1.7 MB (1677458 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:8b094c372797946030ae4a31dd196fe2e922dfed78b1ff89ced0cb2198df4110`  
		Last Modified: Tue, 28 Nov 2017 14:11:01 GMT  
		Size: 355.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:8b63b70a3fec5a57a75842180f72629e69922f0f4395b06f044e1bdffd5d0c10`  
		Last Modified: Tue, 28 Nov 2017 14:11:01 GMT  
		Size: 317.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:86721d11ca3d48caf9ce25df7d2cb757f7fbb3a10dd33bf5a5df407c44de388e`  
		Last Modified: Tue, 28 Nov 2017 14:11:01 GMT  
		Size: 1.4 MB (1373119 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:e5cab34811ce7be15bc8d748b0d9191dd282b90e5303f95a87cfacd3ea355ddd`  
		Last Modified: Tue, 28 Nov 2017 14:14:01 GMT  
		Size: 31.9 MB (31869493 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:4fa38bb8d31f8c644177a404a9d4bb5b3dbb9f03accefe54acdffe206f5e907d`  
		Last Modified: Tue, 28 Nov 2017 14:13:48 GMT  
		Size: 338.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:5b2ba8363ab2f9375f7de034a0beea867395d17ea15f924e218b0dfdd5217c8c`  
		Last Modified: Tue, 28 Nov 2017 14:13:49 GMT  
		Size: 121.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip

### `owncloud:9-apache` - linux; arm64 variant v8

```console
$ docker pull owncloud@sha256:cedc0882a17c60d45254dd1e4c9a6ae52c8ec6311ce951a84563e12f3cdd1925
```

-	Docker Version: 17.06.2-ce
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **212.6 MB (212617919 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:513b94eef0388f3093d79465d8b5afc4964c0e8dcb2ca88b122f0b3ac1e063c3`
-	Entrypoint: `["docker-entrypoint.sh"]`
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
# Tue, 10 Oct 2017 03:45:34 GMT
ENV GPG_KEYS=1A4E8B7277C42E53DBA9C7B9BCAA30EA9C0D5763 6E4F6AB321FDC07F2C332E3AC2BF0BC433CFC8B3
# Tue, 28 Nov 2017 03:34:50 GMT
ENV PHP_VERSION=7.0.26
# Tue, 28 Nov 2017 03:34:50 GMT
ENV PHP_URL=https://secure.php.net/get/php-7.0.26.tar.xz/from/this/mirror PHP_ASC_URL=https://secure.php.net/get/php-7.0.26.tar.xz.asc/from/this/mirror
# Tue, 28 Nov 2017 03:34:51 GMT
ENV PHP_SHA256=ed5cbb4bbb0ddef8985f100bba2e94002ad22a230b5da2dccfe148915df5f199 PHP_MD5=
# Tue, 28 Nov 2017 03:35:23 GMT
RUN set -xe; 		fetchDeps=' 		wget 	'; 	if ! command -v gpg > /dev/null; then 		fetchDeps="$fetchDeps 			dirmngr 			gnupg 		"; 	fi; 	apt-get update; 	apt-get install -y --no-install-recommends $fetchDeps; 	rm -rf /var/lib/apt/lists/*; 		mkdir -p /usr/src; 	cd /usr/src; 		wget -O php.tar.xz "$PHP_URL"; 		if [ -n "$PHP_SHA256" ]; then 		echo "$PHP_SHA256 *php.tar.xz" | sha256sum -c -; 	fi; 	if [ -n "$PHP_MD5" ]; then 		echo "$PHP_MD5 *php.tar.xz" | md5sum -c -; 	fi; 		if [ -n "$PHP_ASC_URL" ]; then 		wget -O php.tar.xz.asc "$PHP_ASC_URL"; 		export GNUPGHOME="$(mktemp -d)"; 		for key in $GPG_KEYS; do 			gpg --keyserver ha.pool.sks-keyservers.net --recv-keys "$key"; 		done; 		gpg --batch --verify php.tar.xz.asc php.tar.xz; 		rm -rf "$GNUPGHOME"; 	fi; 		apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false $fetchDeps
# Tue, 28 Nov 2017 03:35:23 GMT
COPY file:207c686e3fed4f71f8a7b245d8dcae9c9048d276a326d82b553c12a90af0c0ca in /usr/local/bin/ 
# Tue, 28 Nov 2017 03:40:13 GMT
RUN set -xe 	&& buildDeps=" 		$PHP_EXTRA_BUILD_DEPS 		libcurl4-openssl-dev 		libedit-dev 		libsqlite3-dev 		libssl-dev 		libxml2-dev 		zlib1g-dev 	" 	&& apt-get update && apt-get install -y $buildDeps --no-install-recommends && rm -rf /var/lib/apt/lists/* 		&& export CFLAGS="$PHP_CFLAGS" 		CPPFLAGS="$PHP_CPPFLAGS" 		LDFLAGS="$PHP_LDFLAGS" 	&& docker-php-source extract 	&& cd /usr/src/php 	&& gnuArch="$(dpkg-architecture --query DEB_BUILD_GNU_TYPE)" 	&& debMultiarch="$(dpkg-architecture --query DEB_BUILD_MULTIARCH)" 	&& if [ ! -d /usr/include/curl ]; then 		ln -sT "/usr/include/$debMultiarch/curl" /usr/local/include/curl; 	fi 	&& ./configure 		--build="$gnuArch" 		--with-config-file-path="$PHP_INI_DIR" 		--with-config-file-scan-dir="$PHP_INI_DIR/conf.d" 				--disable-cgi 				--enable-ftp 		--enable-mbstring 		--enable-mysqlnd 				--with-curl 		--with-libedit 		--with-openssl 		--with-zlib 				--with-pcre-regex=/usr 		--with-libdir="lib/$debMultiarch" 				$PHP_EXTRA_CONFIGURE_ARGS 	&& make -j "$(nproc)" 	&& make install 	&& { find /usr/local/bin /usr/local/sbin -type f -executable -exec strip --strip-all '{}' + || true; } 	&& make clean 	&& cd / 	&& docker-php-source delete 		&& apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false $buildDeps 		&& pecl update-channels 	&& rm -rf /tmp/pear ~/.pearrc
# Tue, 28 Nov 2017 03:40:14 GMT
COPY multi:dbabcc0b81566a75f49e7faa9ca5f96cd22a515b80ee7ea1e34fceceee3f9c2a in /usr/local/bin/ 
# Tue, 28 Nov 2017 03:40:15 GMT
ENTRYPOINT ["docker-php-entrypoint"]
# Tue, 28 Nov 2017 03:40:16 GMT
COPY file:24613ecbb1ce6a09f683b0753da9c26a1af07547326e8a02f6eec80ad6f2774a in /usr/local/bin/ 
# Tue, 28 Nov 2017 03:40:16 GMT
WORKDIR /var/www/html
# Tue, 28 Nov 2017 03:40:17 GMT
EXPOSE 80/tcp
# Tue, 28 Nov 2017 03:40:17 GMT
CMD ["apache2-foreground"]
# Tue, 28 Nov 2017 04:57:22 GMT
RUN apt-get update && apt-get install -y --no-install-recommends 		bzip2 		libcurl4-openssl-dev 		libfreetype6-dev 		libicu-dev 		libjpeg-dev 		libldap2-dev 		libmcrypt-dev 		libmemcached-dev 		libpng12-dev 		libpq-dev 		libxml2-dev 	&& rm -rf /var/lib/apt/lists/*
# Tue, 28 Nov 2017 05:02:41 GMT
RUN set -ex; 	docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr; 	debMultiarch="$(dpkg-architecture --query DEB_BUILD_MULTIARCH)"; 	docker-php-ext-configure ldap --with-libdir="lib/$debMultiarch"; 	docker-php-ext-install exif gd intl ldap mbstring mcrypt opcache pdo pdo_mysql pdo_pgsql pgsql zip
# Tue, 28 Nov 2017 05:02:43 GMT
RUN { 		echo 'opcache.memory_consumption=128'; 		echo 'opcache.interned_strings_buffer=8'; 		echo 'opcache.max_accelerated_files=4000'; 		echo 'opcache.revalidate_freq=60'; 		echo 'opcache.fast_shutdown=1'; 		echo 'opcache.enable_cli=1'; 	} > /usr/local/etc/php/conf.d/opcache-recommended.ini
# Tue, 28 Nov 2017 05:02:45 GMT
RUN a2enmod rewrite
# Tue, 28 Nov 2017 05:04:00 GMT
RUN set -ex 	&& pecl install APCu-5.1.8 	&& pecl install memcached-3.0.3 	&& pecl install redis-3.1.2 	&& docker-php-ext-enable apcu memcached redis
# Tue, 28 Nov 2017 05:13:12 GMT
ENV OWNCLOUD_VERSION=9.1.6
# Tue, 28 Nov 2017 05:13:13 GMT
VOLUME [/var/www/html]
# Tue, 28 Nov 2017 05:13:35 GMT
RUN curl -fsSL -o owncloud.tar.bz2 		"https://download.owncloud.org/community/owncloud-${OWNCLOUD_VERSION}.tar.bz2" 	&& curl -fsSL -o owncloud.tar.bz2.asc 		"https://download.owncloud.org/community/owncloud-${OWNCLOUD_VERSION}.tar.bz2.asc" 	&& export GNUPGHOME="$(mktemp -d)" 	&& gpg --keyserver ha.pool.sks-keyservers.net --recv-keys E3036906AD9F30807351FAC32D5D5E97F6978A26 	&& gpg --batch --verify owncloud.tar.bz2.asc owncloud.tar.bz2 	&& rm -r "$GNUPGHOME" owncloud.tar.bz2.asc 	&& tar -xjf owncloud.tar.bz2 -C /usr/src/ 	&& rm owncloud.tar.bz2
# Tue, 28 Nov 2017 05:13:37 GMT
COPY file:03fe90b626a097c27835e553f0b22ca55dc76d64d966006644b50609fffa4161 in /usr/local/bin/ 
# Tue, 28 Nov 2017 05:13:38 GMT
RUN ln -s usr/local/bin/docker-entrypoint.sh /entrypoint.sh # backwards compat
# Tue, 28 Nov 2017 05:13:39 GMT
ENTRYPOINT ["docker-entrypoint.sh"]
# Tue, 28 Nov 2017 05:13:40 GMT
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
	-	`sha256:0ae3289c930e51a4f476c3a053c8f09d71ff8610832508f06b6f90c7dba71ea4`  
		Last Modified: Tue, 28 Nov 2017 04:10:27 GMT  
		Size: 12.3 MB (12318756 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:21459ddb518af36b03f8f142f0b77d6aba9409d6ac78a566b2c9c3ec9e8ee356`  
		Last Modified: Tue, 28 Nov 2017 04:10:24 GMT  
		Size: 501.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:f5ae4c5236fed9690ba7ec28efb95ca5074e11c66aa3b41f9df38d5d76d07d75`  
		Last Modified: Tue, 28 Nov 2017 04:10:29 GMT  
		Size: 14.0 MB (13964824 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:3a936ee5bae2bfb060fb53ad04b949af094c95c485c80fcb8793f7ef299a05ca`  
		Last Modified: Tue, 28 Nov 2017 04:10:24 GMT  
		Size: 2.2 KB (2184 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:d960017cbcfab05bbbae1b38e88d0fa254678f8c308101a58e7c7bf06f8f2d6b`  
		Last Modified: Tue, 28 Nov 2017 04:10:24 GMT  
		Size: 904.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:7b15a37f380b707c53c485b5bb3277e65f33a8b3a9170beecbc32f05e99f68fd`  
		Last Modified: Tue, 28 Nov 2017 05:18:31 GMT  
		Size: 34.0 MB (34008850 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:e2644010c0882e4f19ad0453e19f03d9a3a9b4a5248d5b98fbabe3251a0aa719`  
		Last Modified: Tue, 28 Nov 2017 05:18:18 GMT  
		Size: 1.7 MB (1715701 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:6db878407c48973d9545b70c78601144153f4724a58ee28bbe3dbc4eb50ef43d`  
		Last Modified: Tue, 28 Nov 2017 05:18:16 GMT  
		Size: 355.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:832de64505a969e33911ee5d1de7714512b3d07a7402215ff5dde34d454f9781`  
		Last Modified: Tue, 28 Nov 2017 05:18:16 GMT  
		Size: 317.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:4cf0d24bae0b116e2c9872f93ae02685a03d22a95d9ae02c08107ebff0bf749f`  
		Last Modified: Tue, 28 Nov 2017 05:18:18 GMT  
		Size: 1.4 MB (1401923 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:4f2100fe219f9cbbad425ccbd050e29afb5fb76af57a1e4b11af33e293683f39`  
		Last Modified: Tue, 28 Nov 2017 05:24:25 GMT  
		Size: 31.9 MB (31869747 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:b4251fb711461131fe595390b34260c96ee5a098eb6731d1c5994031e776b2a2`  
		Last Modified: Tue, 28 Nov 2017 05:24:12 GMT  
		Size: 337.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:dc31ea8a7f584e78a546974b0ede04026106959d95c0688c408e12fa99dbb0f0`  
		Last Modified: Tue, 28 Nov 2017 05:24:11 GMT  
		Size: 120.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip

### `owncloud:9-apache` - linux; 386

```console
$ docker pull owncloud@sha256:b1eab0e539dfa60ef62920d6299006a470640e7aee4876dd8c8acdb5562f2035
```

-	Docker Version: 17.06.2-ce
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **239.2 MB (239238218 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:6ce6b4dca128f204f1909f767f4cb9d8d140d0dd9c02b47328a8dcf2917d4385`
-	Entrypoint: `["docker-entrypoint.sh"]`
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
# Tue, 10 Oct 2017 01:28:08 GMT
ENV GPG_KEYS=1A4E8B7277C42E53DBA9C7B9BCAA30EA9C0D5763 6E4F6AB321FDC07F2C332E3AC2BF0BC433CFC8B3
# Tue, 28 Nov 2017 10:41:53 GMT
ENV PHP_VERSION=7.0.26
# Tue, 28 Nov 2017 10:41:53 GMT
ENV PHP_URL=https://secure.php.net/get/php-7.0.26.tar.xz/from/this/mirror PHP_ASC_URL=https://secure.php.net/get/php-7.0.26.tar.xz.asc/from/this/mirror
# Tue, 28 Nov 2017 10:41:53 GMT
ENV PHP_SHA256=ed5cbb4bbb0ddef8985f100bba2e94002ad22a230b5da2dccfe148915df5f199 PHP_MD5=
# Tue, 28 Nov 2017 10:42:23 GMT
RUN set -xe; 		fetchDeps=' 		wget 	'; 	if ! command -v gpg > /dev/null; then 		fetchDeps="$fetchDeps 			dirmngr 			gnupg 		"; 	fi; 	apt-get update; 	apt-get install -y --no-install-recommends $fetchDeps; 	rm -rf /var/lib/apt/lists/*; 		mkdir -p /usr/src; 	cd /usr/src; 		wget -O php.tar.xz "$PHP_URL"; 		if [ -n "$PHP_SHA256" ]; then 		echo "$PHP_SHA256 *php.tar.xz" | sha256sum -c -; 	fi; 	if [ -n "$PHP_MD5" ]; then 		echo "$PHP_MD5 *php.tar.xz" | md5sum -c -; 	fi; 		if [ -n "$PHP_ASC_URL" ]; then 		wget -O php.tar.xz.asc "$PHP_ASC_URL"; 		export GNUPGHOME="$(mktemp -d)"; 		for key in $GPG_KEYS; do 			gpg --keyserver ha.pool.sks-keyservers.net --recv-keys "$key"; 		done; 		gpg --batch --verify php.tar.xz.asc php.tar.xz; 		rm -rf "$GNUPGHOME"; 	fi; 		apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false $fetchDeps
# Tue, 28 Nov 2017 10:42:23 GMT
COPY file:207c686e3fed4f71f8a7b245d8dcae9c9048d276a326d82b553c12a90af0c0ca in /usr/local/bin/ 
# Tue, 28 Nov 2017 10:45:15 GMT
RUN set -xe 	&& buildDeps=" 		$PHP_EXTRA_BUILD_DEPS 		libcurl4-openssl-dev 		libedit-dev 		libsqlite3-dev 		libssl-dev 		libxml2-dev 		zlib1g-dev 	" 	&& apt-get update && apt-get install -y $buildDeps --no-install-recommends && rm -rf /var/lib/apt/lists/* 		&& export CFLAGS="$PHP_CFLAGS" 		CPPFLAGS="$PHP_CPPFLAGS" 		LDFLAGS="$PHP_LDFLAGS" 	&& docker-php-source extract 	&& cd /usr/src/php 	&& gnuArch="$(dpkg-architecture --query DEB_BUILD_GNU_TYPE)" 	&& debMultiarch="$(dpkg-architecture --query DEB_BUILD_MULTIARCH)" 	&& if [ ! -d /usr/include/curl ]; then 		ln -sT "/usr/include/$debMultiarch/curl" /usr/local/include/curl; 	fi 	&& ./configure 		--build="$gnuArch" 		--with-config-file-path="$PHP_INI_DIR" 		--with-config-file-scan-dir="$PHP_INI_DIR/conf.d" 				--disable-cgi 				--enable-ftp 		--enable-mbstring 		--enable-mysqlnd 				--with-curl 		--with-libedit 		--with-openssl 		--with-zlib 				--with-pcre-regex=/usr 		--with-libdir="lib/$debMultiarch" 				$PHP_EXTRA_CONFIGURE_ARGS 	&& make -j "$(nproc)" 	&& make install 	&& { find /usr/local/bin /usr/local/sbin -type f -executable -exec strip --strip-all '{}' + || true; } 	&& make clean 	&& cd / 	&& docker-php-source delete 		&& apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false $buildDeps 		&& pecl update-channels 	&& rm -rf /tmp/pear ~/.pearrc
# Tue, 28 Nov 2017 10:45:15 GMT
COPY multi:dbabcc0b81566a75f49e7faa9ca5f96cd22a515b80ee7ea1e34fceceee3f9c2a in /usr/local/bin/ 
# Tue, 28 Nov 2017 10:45:16 GMT
ENTRYPOINT ["docker-php-entrypoint"]
# Tue, 28 Nov 2017 10:45:16 GMT
COPY file:24613ecbb1ce6a09f683b0753da9c26a1af07547326e8a02f6eec80ad6f2774a in /usr/local/bin/ 
# Tue, 28 Nov 2017 10:45:16 GMT
WORKDIR /var/www/html
# Tue, 28 Nov 2017 10:45:16 GMT
EXPOSE 80/tcp
# Tue, 28 Nov 2017 10:45:16 GMT
CMD ["apache2-foreground"]
# Tue, 28 Nov 2017 12:58:47 GMT
RUN apt-get update && apt-get install -y --no-install-recommends 		bzip2 		libcurl4-openssl-dev 		libfreetype6-dev 		libicu-dev 		libjpeg-dev 		libldap2-dev 		libmcrypt-dev 		libmemcached-dev 		libpng12-dev 		libpq-dev 		libxml2-dev 	&& rm -rf /var/lib/apt/lists/*
# Tue, 28 Nov 2017 13:01:51 GMT
RUN set -ex; 	docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr; 	debMultiarch="$(dpkg-architecture --query DEB_BUILD_MULTIARCH)"; 	docker-php-ext-configure ldap --with-libdir="lib/$debMultiarch"; 	docker-php-ext-install exif gd intl ldap mbstring mcrypt opcache pdo pdo_mysql pdo_pgsql pgsql zip
# Tue, 28 Nov 2017 13:05:48 GMT
RUN { 		echo 'opcache.memory_consumption=128'; 		echo 'opcache.interned_strings_buffer=8'; 		echo 'opcache.max_accelerated_files=4000'; 		echo 'opcache.revalidate_freq=60'; 		echo 'opcache.fast_shutdown=1'; 		echo 'opcache.enable_cli=1'; 	} > /usr/local/etc/php/conf.d/opcache-recommended.ini
# Tue, 28 Nov 2017 13:05:49 GMT
RUN a2enmod rewrite
# Tue, 28 Nov 2017 13:06:28 GMT
RUN set -ex 	&& pecl install APCu-5.1.8 	&& pecl install memcached-3.0.3 	&& pecl install redis-3.1.2 	&& docker-php-ext-enable apcu memcached redis
# Tue, 28 Nov 2017 13:27:44 GMT
ENV OWNCLOUD_VERSION=9.1.6
# Tue, 28 Nov 2017 13:27:44 GMT
VOLUME [/var/www/html]
# Tue, 28 Nov 2017 13:29:03 GMT
RUN curl -fsSL -o owncloud.tar.bz2 		"https://download.owncloud.org/community/owncloud-${OWNCLOUD_VERSION}.tar.bz2" 	&& curl -fsSL -o owncloud.tar.bz2.asc 		"https://download.owncloud.org/community/owncloud-${OWNCLOUD_VERSION}.tar.bz2.asc" 	&& export GNUPGHOME="$(mktemp -d)" 	&& gpg --keyserver ha.pool.sks-keyservers.net --recv-keys E3036906AD9F30807351FAC32D5D5E97F6978A26 	&& gpg --batch --verify owncloud.tar.bz2.asc owncloud.tar.bz2 	&& rm -r "$GNUPGHOME" owncloud.tar.bz2.asc 	&& tar -xjf owncloud.tar.bz2 -C /usr/src/ 	&& rm owncloud.tar.bz2
# Tue, 28 Nov 2017 13:33:40 GMT
COPY file:03fe90b626a097c27835e553f0b22ca55dc76d64d966006644b50609fffa4161 in /usr/local/bin/ 
# Tue, 28 Nov 2017 13:33:41 GMT
RUN ln -s usr/local/bin/docker-entrypoint.sh /entrypoint.sh # backwards compat
# Tue, 28 Nov 2017 13:33:41 GMT
ENTRYPOINT ["docker-entrypoint.sh"]
# Tue, 28 Nov 2017 13:33:41 GMT
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
	-	`sha256:8362896c1084411083eabb7fc567750018afa90324595ebce94a2d9f42b436e4`  
		Last Modified: Tue, 28 Nov 2017 11:26:30 GMT  
		Size: 12.3 MB (12320612 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:3cdce7f91675e5ecf0d3f06546a9ade89cf11dc71d68d9aac6c3af3c485cb957`  
		Last Modified: Tue, 28 Nov 2017 11:26:29 GMT  
		Size: 503.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:67eb788445ee84865b2a1d1782f50118b93101b888d38050cee10464f9343270`  
		Last Modified: Tue, 28 Nov 2017 11:26:35 GMT  
		Size: 17.6 MB (17551733 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:fb2589fae2ee5cec9bf14dfe790bd321757aeb1da82dc45f61fa8291bffe1668`  
		Last Modified: Tue, 28 Nov 2017 11:26:29 GMT  
		Size: 2.2 KB (2185 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:c6413e08a69056348b82cab65dd73316ef09b76b8eb44d94601d1bce099b3cad`  
		Last Modified: Tue, 28 Nov 2017 11:26:29 GMT  
		Size: 905.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:989c8852a6c1ccf5d3befd81ea7dc444d2cc1d85307702a92aea81f64c9d1640`  
		Last Modified: Tue, 28 Nov 2017 13:44:05 GMT  
		Size: 34.6 MB (34588450 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:942093b68a49a80784107ce87807abb4e4965909252a52a3386a100f84960278`  
		Last Modified: Tue, 28 Nov 2017 13:43:43 GMT  
		Size: 1.8 MB (1837613 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:b1fe7d379326cc58b5d5402f9de91e8ea4d70d6946de87399637eb7c8c3e3435`  
		Last Modified: Tue, 28 Nov 2017 13:43:41 GMT  
		Size: 355.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:e9c30406c61da3692470a82388b37a03a6224db07b367004cab7f24ca659923d`  
		Last Modified: Tue, 28 Nov 2017 13:43:42 GMT  
		Size: 315.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:7d77b7672e5646784858b31f7eb1870495b26602ce84fccef7e1c9374dd6fa57`  
		Last Modified: Tue, 28 Nov 2017 13:43:43 GMT  
		Size: 1.3 MB (1283079 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:264d6d705654f63bc3d8cefb75656d1e6bed8ee2eaf8f39ad3f84152f7474a55`  
		Last Modified: Tue, 28 Nov 2017 13:59:16 GMT  
		Size: 31.9 MB (31869742 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:ab873b0037a0cad2824c1cfd557a87a404efcb094646104b22288af8ce0e3164`  
		Last Modified: Tue, 28 Nov 2017 13:59:02 GMT  
		Size: 338.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:a8be58548253cdc8abd409d2625d12a7e500dd1f4120568217de4ca8dba430bf`  
		Last Modified: Tue, 28 Nov 2017 13:59:02 GMT  
		Size: 121.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip

### `owncloud:9-apache` - linux; ppc64le

```console
$ docker pull owncloud@sha256:5f649954d656975f8415b4a127eccc0849a8e6250e4bfd271e85e4d55220f790
```

-	Docker Version: 17.06.2-ce
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **221.8 MB (221756446 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:1a3005b28514bd8389991d877f7193b81150997962b2e2cf251e8ef71dd6ff12`
-	Entrypoint: `["docker-entrypoint.sh"]`
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
# Tue, 10 Oct 2017 05:44:35 GMT
ENV GPG_KEYS=1A4E8B7277C42E53DBA9C7B9BCAA30EA9C0D5763 6E4F6AB321FDC07F2C332E3AC2BF0BC433CFC8B3
# Tue, 28 Nov 2017 10:13:55 GMT
ENV PHP_VERSION=7.0.26
# Tue, 28 Nov 2017 10:13:57 GMT
ENV PHP_URL=https://secure.php.net/get/php-7.0.26.tar.xz/from/this/mirror PHP_ASC_URL=https://secure.php.net/get/php-7.0.26.tar.xz.asc/from/this/mirror
# Tue, 28 Nov 2017 10:13:58 GMT
ENV PHP_SHA256=ed5cbb4bbb0ddef8985f100bba2e94002ad22a230b5da2dccfe148915df5f199 PHP_MD5=
# Tue, 28 Nov 2017 10:14:49 GMT
RUN set -xe; 		fetchDeps=' 		wget 	'; 	if ! command -v gpg > /dev/null; then 		fetchDeps="$fetchDeps 			dirmngr 			gnupg 		"; 	fi; 	apt-get update; 	apt-get install -y --no-install-recommends $fetchDeps; 	rm -rf /var/lib/apt/lists/*; 		mkdir -p /usr/src; 	cd /usr/src; 		wget -O php.tar.xz "$PHP_URL"; 		if [ -n "$PHP_SHA256" ]; then 		echo "$PHP_SHA256 *php.tar.xz" | sha256sum -c -; 	fi; 	if [ -n "$PHP_MD5" ]; then 		echo "$PHP_MD5 *php.tar.xz" | md5sum -c -; 	fi; 		if [ -n "$PHP_ASC_URL" ]; then 		wget -O php.tar.xz.asc "$PHP_ASC_URL"; 		export GNUPGHOME="$(mktemp -d)"; 		for key in $GPG_KEYS; do 			gpg --keyserver ha.pool.sks-keyservers.net --recv-keys "$key"; 		done; 		gpg --batch --verify php.tar.xz.asc php.tar.xz; 		rm -rf "$GNUPGHOME"; 	fi; 		apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false $fetchDeps
# Tue, 28 Nov 2017 10:14:50 GMT
COPY file:207c686e3fed4f71f8a7b245d8dcae9c9048d276a326d82b553c12a90af0c0ca in /usr/local/bin/ 
# Tue, 28 Nov 2017 10:19:44 GMT
RUN set -xe 	&& buildDeps=" 		$PHP_EXTRA_BUILD_DEPS 		libcurl4-openssl-dev 		libedit-dev 		libsqlite3-dev 		libssl-dev 		libxml2-dev 		zlib1g-dev 	" 	&& apt-get update && apt-get install -y $buildDeps --no-install-recommends && rm -rf /var/lib/apt/lists/* 		&& export CFLAGS="$PHP_CFLAGS" 		CPPFLAGS="$PHP_CPPFLAGS" 		LDFLAGS="$PHP_LDFLAGS" 	&& docker-php-source extract 	&& cd /usr/src/php 	&& gnuArch="$(dpkg-architecture --query DEB_BUILD_GNU_TYPE)" 	&& debMultiarch="$(dpkg-architecture --query DEB_BUILD_MULTIARCH)" 	&& if [ ! -d /usr/include/curl ]; then 		ln -sT "/usr/include/$debMultiarch/curl" /usr/local/include/curl; 	fi 	&& ./configure 		--build="$gnuArch" 		--with-config-file-path="$PHP_INI_DIR" 		--with-config-file-scan-dir="$PHP_INI_DIR/conf.d" 				--disable-cgi 				--enable-ftp 		--enable-mbstring 		--enable-mysqlnd 				--with-curl 		--with-libedit 		--with-openssl 		--with-zlib 				--with-pcre-regex=/usr 		--with-libdir="lib/$debMultiarch" 				$PHP_EXTRA_CONFIGURE_ARGS 	&& make -j "$(nproc)" 	&& make install 	&& { find /usr/local/bin /usr/local/sbin -type f -executable -exec strip --strip-all '{}' + || true; } 	&& make clean 	&& cd / 	&& docker-php-source delete 		&& apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false $buildDeps 		&& pecl update-channels 	&& rm -rf /tmp/pear ~/.pearrc
# Tue, 28 Nov 2017 10:19:46 GMT
COPY multi:dbabcc0b81566a75f49e7faa9ca5f96cd22a515b80ee7ea1e34fceceee3f9c2a in /usr/local/bin/ 
# Tue, 28 Nov 2017 10:19:47 GMT
ENTRYPOINT ["docker-php-entrypoint"]
# Tue, 28 Nov 2017 10:19:48 GMT
COPY file:24613ecbb1ce6a09f683b0753da9c26a1af07547326e8a02f6eec80ad6f2774a in /usr/local/bin/ 
# Tue, 28 Nov 2017 10:19:49 GMT
WORKDIR /var/www/html
# Tue, 28 Nov 2017 10:19:51 GMT
EXPOSE 80/tcp
# Tue, 28 Nov 2017 10:19:52 GMT
CMD ["apache2-foreground"]
# Tue, 28 Nov 2017 10:52:03 GMT
RUN apt-get update && apt-get install -y --no-install-recommends 		bzip2 		libcurl4-openssl-dev 		libfreetype6-dev 		libicu-dev 		libjpeg-dev 		libldap2-dev 		libmcrypt-dev 		libmemcached-dev 		libpng12-dev 		libpq-dev 		libxml2-dev 	&& rm -rf /var/lib/apt/lists/*
# Tue, 28 Nov 2017 10:55:25 GMT
RUN set -ex; 	docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr; 	debMultiarch="$(dpkg-architecture --query DEB_BUILD_MULTIARCH)"; 	docker-php-ext-configure ldap --with-libdir="lib/$debMultiarch"; 	docker-php-ext-install exif gd intl ldap mbstring mcrypt opcache pdo pdo_mysql pdo_pgsql pgsql zip
# Tue, 28 Nov 2017 10:55:29 GMT
RUN { 		echo 'opcache.memory_consumption=128'; 		echo 'opcache.interned_strings_buffer=8'; 		echo 'opcache.max_accelerated_files=4000'; 		echo 'opcache.revalidate_freq=60'; 		echo 'opcache.fast_shutdown=1'; 		echo 'opcache.enable_cli=1'; 	} > /usr/local/etc/php/conf.d/opcache-recommended.ini
# Tue, 28 Nov 2017 10:55:34 GMT
RUN a2enmod rewrite
# Tue, 28 Nov 2017 10:56:40 GMT
RUN set -ex 	&& pecl install APCu-5.1.8 	&& pecl install memcached-3.0.3 	&& pecl install redis-3.1.2 	&& docker-php-ext-enable apcu memcached redis
# Tue, 28 Nov 2017 11:06:44 GMT
ENV OWNCLOUD_VERSION=9.1.6
# Tue, 28 Nov 2017 11:06:46 GMT
VOLUME [/var/www/html]
# Tue, 28 Nov 2017 11:07:34 GMT
RUN curl -fsSL -o owncloud.tar.bz2 		"https://download.owncloud.org/community/owncloud-${OWNCLOUD_VERSION}.tar.bz2" 	&& curl -fsSL -o owncloud.tar.bz2.asc 		"https://download.owncloud.org/community/owncloud-${OWNCLOUD_VERSION}.tar.bz2.asc" 	&& export GNUPGHOME="$(mktemp -d)" 	&& gpg --keyserver ha.pool.sks-keyservers.net --recv-keys E3036906AD9F30807351FAC32D5D5E97F6978A26 	&& gpg --batch --verify owncloud.tar.bz2.asc owncloud.tar.bz2 	&& rm -r "$GNUPGHOME" owncloud.tar.bz2.asc 	&& tar -xjf owncloud.tar.bz2 -C /usr/src/ 	&& rm owncloud.tar.bz2
# Tue, 28 Nov 2017 11:07:36 GMT
COPY file:03fe90b626a097c27835e553f0b22ca55dc76d64d966006644b50609fffa4161 in /usr/local/bin/ 
# Tue, 28 Nov 2017 11:07:39 GMT
RUN ln -s usr/local/bin/docker-entrypoint.sh /entrypoint.sh # backwards compat
# Tue, 28 Nov 2017 11:07:41 GMT
ENTRYPOINT ["docker-entrypoint.sh"]
# Tue, 28 Nov 2017 11:07:42 GMT
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
	-	`sha256:adaf936200ce74399ec488b73c59987c34f1562bd35fd895b38c6325e3db9220`  
		Last Modified: Tue, 28 Nov 2017 10:33:39 GMT  
		Size: 12.3 MB (12319772 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:b6e31ccffba59fd846f5ec8eae2a14c30af4bbdafe62a62da854768751762193`  
		Last Modified: Tue, 28 Nov 2017 10:33:37 GMT  
		Size: 503.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:1ad74460e2582f6527c92f7eaea4b8668ca611c2826354deef0c04cd2b52e4a7`  
		Last Modified: Tue, 28 Nov 2017 10:33:42 GMT  
		Size: 14.8 MB (14839959 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:0ebbb497ec03466072c5cf97dad475b57df50b50555f8b4ccc7a1688ddfcca91`  
		Last Modified: Tue, 28 Nov 2017 10:33:37 GMT  
		Size: 2.2 KB (2183 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:194578ee9d8a303937d68da50ecffad2365cea771c07c36de067a911b2598a7e`  
		Last Modified: Tue, 28 Nov 2017 10:33:37 GMT  
		Size: 903.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:a1665ebd14759cedc78bf29be1d899597b4ea980a411354de6fc89cdda35eea5`  
		Last Modified: Tue, 28 Nov 2017 11:12:36 GMT  
		Size: 34.8 MB (34783443 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:57774649f76f71f31df42db9f1633dd5d60f05b1768b911eb461996c14530777`  
		Last Modified: Tue, 28 Nov 2017 11:12:23 GMT  
		Size: 1.8 MB (1814495 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:987cffa96b87296a65424975654fbe8e9385c05ea5fc0575a198959697aee756`  
		Last Modified: Tue, 28 Nov 2017 11:12:19 GMT  
		Size: 356.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:ffd4f5e1831442b5212cedca48dd2c6e1d106741fdb33680a6284926b7d13074`  
		Last Modified: Tue, 28 Nov 2017 11:12:19 GMT  
		Size: 319.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:5d854a3de3af8662bbf7bdefc221d36ea8f8b026ddae9b7bb1dddc940e4af06a`  
		Last Modified: Tue, 28 Nov 2017 11:12:20 GMT  
		Size: 1.4 MB (1423352 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:6a8c1cd62ac152b8a3283548857f47d34a909d366030c675f899236c67bc2f03`  
		Last Modified: Tue, 28 Nov 2017 11:14:28 GMT  
		Size: 31.9 MB (31869513 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:b730257188f75a5a5a7e786ec5fb67ca228ab687c6322772f08ebd77a7413224`  
		Last Modified: Tue, 28 Nov 2017 11:14:13 GMT  
		Size: 338.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:3974ce51a768c635d7c7a1b4d1f889b37fd0816aac67d86cbc929bac38f98b00`  
		Last Modified: Tue, 28 Nov 2017 11:14:13 GMT  
		Size: 120.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip

### `owncloud:9-apache` - linux; s390x

```console
$ docker pull owncloud@sha256:e62c8571d4f6e3a5b27e1202a1f89e64ecbd272103ddd73f3278c5caf5604f83
```

-	Docker Version: 17.06.1-ce
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **217.8 MB (217815943 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:5cda0422996a94de60edb90c3759d6f99f097c73177efb2e399ce9e0f0dd2289`
-	Entrypoint: `["docker-entrypoint.sh"]`
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
# Mon, 09 Oct 2017 23:13:34 GMT
ENV GPG_KEYS=1A4E8B7277C42E53DBA9C7B9BCAA30EA9C0D5763 6E4F6AB321FDC07F2C332E3AC2BF0BC433CFC8B3
# Tue, 28 Nov 2017 18:44:05 GMT
ENV PHP_VERSION=7.0.26
# Tue, 28 Nov 2017 18:44:05 GMT
ENV PHP_URL=https://secure.php.net/get/php-7.0.26.tar.xz/from/this/mirror PHP_ASC_URL=https://secure.php.net/get/php-7.0.26.tar.xz.asc/from/this/mirror
# Tue, 28 Nov 2017 18:44:05 GMT
ENV PHP_SHA256=ed5cbb4bbb0ddef8985f100bba2e94002ad22a230b5da2dccfe148915df5f199 PHP_MD5=
# Tue, 28 Nov 2017 18:44:19 GMT
RUN set -xe; 		fetchDeps=' 		wget 	'; 	if ! command -v gpg > /dev/null; then 		fetchDeps="$fetchDeps 			dirmngr 			gnupg 		"; 	fi; 	apt-get update; 	apt-get install -y --no-install-recommends $fetchDeps; 	rm -rf /var/lib/apt/lists/*; 		mkdir -p /usr/src; 	cd /usr/src; 		wget -O php.tar.xz "$PHP_URL"; 		if [ -n "$PHP_SHA256" ]; then 		echo "$PHP_SHA256 *php.tar.xz" | sha256sum -c -; 	fi; 	if [ -n "$PHP_MD5" ]; then 		echo "$PHP_MD5 *php.tar.xz" | md5sum -c -; 	fi; 		if [ -n "$PHP_ASC_URL" ]; then 		wget -O php.tar.xz.asc "$PHP_ASC_URL"; 		export GNUPGHOME="$(mktemp -d)"; 		for key in $GPG_KEYS; do 			gpg --keyserver ha.pool.sks-keyservers.net --recv-keys "$key"; 		done; 		gpg --batch --verify php.tar.xz.asc php.tar.xz; 		rm -rf "$GNUPGHOME"; 	fi; 		apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false $fetchDeps
# Tue, 28 Nov 2017 18:44:19 GMT
COPY file:207c686e3fed4f71f8a7b245d8dcae9c9048d276a326d82b553c12a90af0c0ca in /usr/local/bin/ 
# Tue, 28 Nov 2017 18:46:12 GMT
RUN set -xe 	&& buildDeps=" 		$PHP_EXTRA_BUILD_DEPS 		libcurl4-openssl-dev 		libedit-dev 		libsqlite3-dev 		libssl-dev 		libxml2-dev 		zlib1g-dev 	" 	&& apt-get update && apt-get install -y $buildDeps --no-install-recommends && rm -rf /var/lib/apt/lists/* 		&& export CFLAGS="$PHP_CFLAGS" 		CPPFLAGS="$PHP_CPPFLAGS" 		LDFLAGS="$PHP_LDFLAGS" 	&& docker-php-source extract 	&& cd /usr/src/php 	&& gnuArch="$(dpkg-architecture --query DEB_BUILD_GNU_TYPE)" 	&& debMultiarch="$(dpkg-architecture --query DEB_BUILD_MULTIARCH)" 	&& if [ ! -d /usr/include/curl ]; then 		ln -sT "/usr/include/$debMultiarch/curl" /usr/local/include/curl; 	fi 	&& ./configure 		--build="$gnuArch" 		--with-config-file-path="$PHP_INI_DIR" 		--with-config-file-scan-dir="$PHP_INI_DIR/conf.d" 				--disable-cgi 				--enable-ftp 		--enable-mbstring 		--enable-mysqlnd 				--with-curl 		--with-libedit 		--with-openssl 		--with-zlib 				--with-pcre-regex=/usr 		--with-libdir="lib/$debMultiarch" 				$PHP_EXTRA_CONFIGURE_ARGS 	&& make -j "$(nproc)" 	&& make install 	&& { find /usr/local/bin /usr/local/sbin -type f -executable -exec strip --strip-all '{}' + || true; } 	&& make clean 	&& cd / 	&& docker-php-source delete 		&& apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false $buildDeps 		&& pecl update-channels 	&& rm -rf /tmp/pear ~/.pearrc
# Tue, 28 Nov 2017 18:46:12 GMT
COPY multi:dbabcc0b81566a75f49e7faa9ca5f96cd22a515b80ee7ea1e34fceceee3f9c2a in /usr/local/bin/ 
# Tue, 28 Nov 2017 18:46:12 GMT
ENTRYPOINT ["docker-php-entrypoint"]
# Tue, 28 Nov 2017 18:46:13 GMT
COPY file:24613ecbb1ce6a09f683b0753da9c26a1af07547326e8a02f6eec80ad6f2774a in /usr/local/bin/ 
# Tue, 28 Nov 2017 18:46:13 GMT
WORKDIR /var/www/html
# Tue, 28 Nov 2017 18:46:13 GMT
EXPOSE 80/tcp
# Tue, 28 Nov 2017 18:46:13 GMT
CMD ["apache2-foreground"]
# Tue, 28 Nov 2017 19:23:27 GMT
RUN apt-get update && apt-get install -y --no-install-recommends 		bzip2 		libcurl4-openssl-dev 		libfreetype6-dev 		libicu-dev 		libjpeg-dev 		libldap2-dev 		libmcrypt-dev 		libmemcached-dev 		libpng12-dev 		libpq-dev 		libxml2-dev 	&& rm -rf /var/lib/apt/lists/*
# Tue, 28 Nov 2017 19:25:28 GMT
RUN set -ex; 	docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr; 	debMultiarch="$(dpkg-architecture --query DEB_BUILD_MULTIARCH)"; 	docker-php-ext-configure ldap --with-libdir="lib/$debMultiarch"; 	docker-php-ext-install exif gd intl ldap mbstring mcrypt opcache pdo pdo_mysql pdo_pgsql pgsql zip
# Tue, 28 Nov 2017 19:25:30 GMT
RUN { 		echo 'opcache.memory_consumption=128'; 		echo 'opcache.interned_strings_buffer=8'; 		echo 'opcache.max_accelerated_files=4000'; 		echo 'opcache.revalidate_freq=60'; 		echo 'opcache.fast_shutdown=1'; 		echo 'opcache.enable_cli=1'; 	} > /usr/local/etc/php/conf.d/opcache-recommended.ini
# Tue, 28 Nov 2017 19:25:34 GMT
RUN a2enmod rewrite
# Tue, 28 Nov 2017 19:26:03 GMT
RUN set -ex 	&& pecl install APCu-5.1.8 	&& pecl install memcached-3.0.3 	&& pecl install redis-3.1.2 	&& docker-php-ext-enable apcu memcached redis
# Tue, 28 Nov 2017 19:29:34 GMT
ENV OWNCLOUD_VERSION=9.1.6
# Tue, 28 Nov 2017 19:29:34 GMT
VOLUME [/var/www/html]
# Tue, 28 Nov 2017 19:29:42 GMT
RUN curl -fsSL -o owncloud.tar.bz2 		"https://download.owncloud.org/community/owncloud-${OWNCLOUD_VERSION}.tar.bz2" 	&& curl -fsSL -o owncloud.tar.bz2.asc 		"https://download.owncloud.org/community/owncloud-${OWNCLOUD_VERSION}.tar.bz2.asc" 	&& export GNUPGHOME="$(mktemp -d)" 	&& gpg --keyserver ha.pool.sks-keyservers.net --recv-keys E3036906AD9F30807351FAC32D5D5E97F6978A26 	&& gpg --batch --verify owncloud.tar.bz2.asc owncloud.tar.bz2 	&& rm -r "$GNUPGHOME" owncloud.tar.bz2.asc 	&& tar -xjf owncloud.tar.bz2 -C /usr/src/ 	&& rm owncloud.tar.bz2
# Tue, 28 Nov 2017 19:29:43 GMT
COPY file:03fe90b626a097c27835e553f0b22ca55dc76d64d966006644b50609fffa4161 in /usr/local/bin/ 
# Tue, 28 Nov 2017 19:29:44 GMT
RUN ln -s usr/local/bin/docker-entrypoint.sh /entrypoint.sh # backwards compat
# Tue, 28 Nov 2017 19:29:44 GMT
ENTRYPOINT ["docker-entrypoint.sh"]
# Tue, 28 Nov 2017 19:29:44 GMT
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
	-	`sha256:1733eaef7df6f9c2025e46fc412761410a6a0938f66e6aa59135b5a2d2dfe4b9`  
		Last Modified: Tue, 28 Nov 2017 18:57:18 GMT  
		Size: 12.3 MB (12318510 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:f8b9347d5e8f7b682659a7b44a0e9920eaa005023c159bffe45233f067e908c1`  
		Last Modified: Tue, 28 Nov 2017 18:57:17 GMT  
		Size: 503.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:d14e940c95598e1f4ee31c3e4a25dcb28d23648f15d023ff128f55568172f2ad`  
		Last Modified: Tue, 28 Nov 2017 18:57:21 GMT  
		Size: 15.5 MB (15520983 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:5fd2d310e10cc02b9b703697c00cb0f4f27929a890ea00ebb4fc04486d3bb2f8`  
		Last Modified: Tue, 28 Nov 2017 18:57:17 GMT  
		Size: 2.2 KB (2184 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:2b8391a516c967edf3cff6abd20c20370709781c04e7e0a78ea6a4f2f772dd2c`  
		Last Modified: Tue, 28 Nov 2017 18:57:17 GMT  
		Size: 902.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:fa496f196dba526e078d3fc6024acb83550b1c87d219284762a8b4cc2f290ee8`  
		Last Modified: Tue, 28 Nov 2017 19:31:29 GMT  
		Size: 35.0 MB (35048512 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:9dd074332af1f15895e4588f98d59b327271c882e05f5111fbf38dbcd1b93689`  
		Last Modified: Tue, 28 Nov 2017 19:31:22 GMT  
		Size: 1.9 MB (1853132 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:86996e6a2a8f7e60f6a09162f7b7699bc019eb68b28f9a331df2f569539c9101`  
		Last Modified: Tue, 28 Nov 2017 19:31:21 GMT  
		Size: 354.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:42bf118ff1bc12bf25b1d459c119c7a568af52e5662fe7836bd6e054f462ae7e`  
		Last Modified: Tue, 28 Nov 2017 19:31:21 GMT  
		Size: 317.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:7361443d3b42515dfc7250fb7d5f0c08b79d190310a3e7ea842003d7fcaf4e45`  
		Last Modified: Tue, 28 Nov 2017 19:31:21 GMT  
		Size: 1.4 MB (1406294 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:7114beb8917cd0aed973d018a484d9b0549213a853f0228157b110db072447da`  
		Last Modified: Tue, 28 Nov 2017 19:33:11 GMT  
		Size: 31.9 MB (31869738 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:8d7555323b08ec9203b3c824ad2ff3931b26a61f2ed92f2a2fee87902b57e614`  
		Last Modified: Tue, 28 Nov 2017 19:33:06 GMT  
		Size: 338.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:1683840664460768bec285f5ecb25741367242776b3db72c65823c2f7e617627`  
		Last Modified: Tue, 28 Nov 2017 19:33:06 GMT  
		Size: 121.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
