## `wordpress:4-fpm-alpine`

```console
$ docker pull wordpress@sha256:eeb4de0c51a4be1338094681e02bceb0317fc05f485585cc5ee527bf9a5a8368
```

-	Manifest MIME: `application/vnd.docker.distribution.manifest.list.v2+json`
-	Platforms:
	-	linux; amd64

### `wordpress:4-fpm-alpine` - linux; amd64

```console
$ docker pull wordpress@sha256:2e6f27d8812342ab1124379a907f30307e275a8b3f1b5867ad113a8bba029c55
```

-	Docker Version: 17.06.2-ce
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **37.0 MB (37017645 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:3638c18e9bfa892e09b31b09e6c615f60ff4693fb04a806a00d28f50e68f8980`
-	Entrypoint: `["docker-entrypoint.sh"]`
-	Default Command: `["php-fpm"]`

```dockerfile
# Fri, 03 Nov 2017 22:10:25 GMT
ADD file:90342832e4e7931e42954849ed51216e77b3c974270ed83e9da5648918fb5e66 in / 
# Fri, 03 Nov 2017 22:10:25 GMT
CMD ["/bin/sh"]
# Sat, 04 Nov 2017 10:30:48 GMT
ENV PHPIZE_DEPS=autoconf 		dpkg-dev dpkg 		file 		g++ 		gcc 		libc-dev 		make 		pcre-dev 		pkgconf 		re2c
# Sat, 04 Nov 2017 10:30:51 GMT
RUN apk add --no-cache --virtual .persistent-deps 		ca-certificates 		curl 		tar 		xz 		openssl
# Sat, 04 Nov 2017 10:30:52 GMT
RUN set -x 	&& addgroup -g 82 -S www-data 	&& adduser -u 82 -D -S -G www-data www-data
# Sat, 04 Nov 2017 10:30:52 GMT
ENV PHP_INI_DIR=/usr/local/etc/php
# Sat, 04 Nov 2017 10:30:53 GMT
RUN mkdir -p $PHP_INI_DIR/conf.d
# Sat, 04 Nov 2017 10:35:58 GMT
ENV PHP_EXTRA_CONFIGURE_ARGS=--enable-fpm --with-fpm-user=www-data --with-fpm-group=www-data
# Sat, 04 Nov 2017 10:35:58 GMT
ENV PHP_CFLAGS=-fstack-protector-strong -fpic -fpie -O2
# Sat, 04 Nov 2017 10:35:59 GMT
ENV PHP_CPPFLAGS=-fstack-protector-strong -fpic -fpie -O2
# Sat, 04 Nov 2017 10:35:59 GMT
ENV PHP_LDFLAGS=-Wl,-O1 -Wl,--hash-style=both -pie
# Sat, 04 Nov 2017 11:39:25 GMT
ENV GPG_KEYS=0BD78B5F97500D450838F95DFE857D9A90D90EC1 6E4F6AB321FDC07F2C332E3AC2BF0BC433CFC8B3
# Sat, 04 Nov 2017 11:39:25 GMT
ENV PHP_VERSION=5.6.32
# Sat, 04 Nov 2017 11:39:25 GMT
ENV PHP_URL=https://secure.php.net/get/php-5.6.32.tar.xz/from/this/mirror PHP_ASC_URL=https://secure.php.net/get/php-5.6.32.tar.xz.asc/from/this/mirror
# Sat, 04 Nov 2017 11:39:25 GMT
ENV PHP_SHA256=8c2b4f721c7475fb9eabda2495209e91ea933082e6f34299d11cba88cd76e64b PHP_MD5=
# Sat, 04 Nov 2017 11:39:42 GMT
RUN set -xe; 		apk add --no-cache --virtual .fetch-deps 		gnupg 	; 		mkdir -p /usr/src; 	cd /usr/src; 		wget -O php.tar.xz "$PHP_URL"; 		if [ -n "$PHP_SHA256" ]; then 		echo "$PHP_SHA256 *php.tar.xz" | sha256sum -c -; 	fi; 	if [ -n "$PHP_MD5" ]; then 		echo "$PHP_MD5 *php.tar.xz" | md5sum -c -; 	fi; 		if [ -n "$PHP_ASC_URL" ]; then 		wget -O php.tar.xz.asc "$PHP_ASC_URL"; 		export GNUPGHOME="$(mktemp -d)"; 		for key in $GPG_KEYS; do 			gpg --keyserver ha.pool.sks-keyservers.net --recv-keys "$key"; 		done; 		gpg --batch --verify php.tar.xz.asc php.tar.xz; 		rm -rf "$GNUPGHOME"; 	fi; 		apk del .fetch-deps
# Sat, 04 Nov 2017 11:39:42 GMT
COPY file:207c686e3fed4f71f8a7b245d8dcae9c9048d276a326d82b553c12a90af0c0ca in /usr/local/bin/ 
# Sat, 04 Nov 2017 11:43:35 GMT
RUN set -xe 	&& apk add --no-cache --virtual .build-deps 		$PHPIZE_DEPS 		coreutils 		curl-dev 		libedit-dev 		openssl-dev 		libxml2-dev 		sqlite-dev 		&& export CFLAGS="$PHP_CFLAGS" 		CPPFLAGS="$PHP_CPPFLAGS" 		LDFLAGS="$PHP_LDFLAGS" 	&& docker-php-source extract 	&& cd /usr/src/php 	&& gnuArch="$(dpkg-architecture --query DEB_BUILD_GNU_TYPE)" 	&& ./configure 		--build="$gnuArch" 		--with-config-file-path="$PHP_INI_DIR" 		--with-config-file-scan-dir="$PHP_INI_DIR/conf.d" 				--disable-cgi 				--enable-ftp 		--enable-mbstring 		--enable-mysqlnd 				--with-curl 		--with-libedit 		--with-openssl 		--with-zlib 				--with-pcre-regex=/usr 				$PHP_EXTRA_CONFIGURE_ARGS 	&& make -j "$(nproc)" 	&& make install 	&& { find /usr/local/bin /usr/local/sbin -type f -perm +0111 -exec strip --strip-all '{}' + || true; } 	&& make clean 	&& cd / 	&& docker-php-source delete 		&& runDeps="$( 		scanelf --needed --nobanner --format '%n#p' --recursive /usr/local 			| tr ',' '\n' 			| sort -u 			| awk 'system("[ -e /usr/local/lib/" $1 " ]") == 0 { next } { print "so:" $1 }' 	)" 	&& apk add --no-cache --virtual .php-rundeps $runDeps 		&& apk del .build-deps 		&& pecl update-channels 	&& rm -rf /tmp/pear ~/.pearrc
# Sat, 04 Nov 2017 11:43:36 GMT
COPY multi:3a3ce8aa3891c64454909e9f8257446a1817abe660b49a7baaa26f28bfdc444d in /usr/local/bin/ 
# Sat, 04 Nov 2017 11:43:36 GMT
ENTRYPOINT ["docker-php-entrypoint"]
# Sat, 04 Nov 2017 11:43:38 GMT
WORKDIR /var/www/html
# Sat, 04 Nov 2017 11:43:39 GMT
RUN set -ex 	&& cd /usr/local/etc 	&& if [ -d php-fpm.d ]; then 		sed 's!=NONE/!=!g' php-fpm.conf.default | tee php-fpm.conf > /dev/null; 		cp php-fpm.d/www.conf.default php-fpm.d/www.conf; 	else 		mkdir php-fpm.d; 		cp php-fpm.conf.default php-fpm.d/www.conf; 		{ 			echo '[global]'; 			echo 'include=etc/php-fpm.d/*.conf'; 		} | tee php-fpm.conf; 	fi 	&& { 		echo '[global]'; 		echo 'error_log = /proc/self/fd/2'; 		echo; 		echo '[www]'; 		echo '; if we send this to /proc/self/fd/1, it never appears'; 		echo 'access.log = /proc/self/fd/2'; 		echo; 		echo 'clear_env = no'; 		echo; 		echo '; Ensure worker stdout and stderr are sent to the main error log.'; 		echo 'catch_workers_output = yes'; 	} | tee php-fpm.d/docker.conf 	&& { 		echo '[global]'; 		echo 'daemonize = no'; 		echo; 		echo '[www]'; 		echo 'listen = [::]:9000'; 	} | tee php-fpm.d/zz-docker.conf
# Sat, 04 Nov 2017 11:43:39 GMT
EXPOSE 9000/tcp
# Sat, 04 Nov 2017 11:43:39 GMT
CMD ["php-fpm"]
# Sat, 04 Nov 2017 21:01:58 GMT
RUN apk add --no-cache 		bash 		sed
# Sat, 04 Nov 2017 21:02:31 GMT
RUN set -ex; 		apk add --no-cache --virtual .build-deps 		libjpeg-turbo-dev 		libpng-dev 	; 		docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr; 	docker-php-ext-install gd mysqli opcache; 		runDeps="$( 		scanelf --needed --nobanner --format '%n#p' --recursive /usr/local/lib/php/extensions 			| tr ',' '\n' 			| sort -u 			| awk 'system("[ -e /usr/local/lib/" $1 " ]") == 0 { next } { print "so:" $1 }' 	)"; 	apk add --virtual .wordpress-phpexts-rundeps $runDeps; 	apk del .build-deps
# Sat, 04 Nov 2017 21:02:32 GMT
RUN { 		echo 'opcache.memory_consumption=128'; 		echo 'opcache.interned_strings_buffer=8'; 		echo 'opcache.max_accelerated_files=4000'; 		echo 'opcache.revalidate_freq=2'; 		echo 'opcache.fast_shutdown=1'; 		echo 'opcache.enable_cli=1'; 	} > /usr/local/etc/php/conf.d/opcache-recommended.ini
# Sat, 04 Nov 2017 21:02:32 GMT
VOLUME [/var/www/html]
# Tue, 21 Nov 2017 00:03:30 GMT
ENV WORDPRESS_VERSION=4.9
# Tue, 21 Nov 2017 00:03:30 GMT
ENV WORDPRESS_SHA1=6127bd2aed7b7c0a2c1789c8f17a2222a9081d6c
# Tue, 21 Nov 2017 00:03:32 GMT
RUN set -ex; 	curl -o wordpress.tar.gz -fSL "https://wordpress.org/wordpress-${WORDPRESS_VERSION}.tar.gz"; 	echo "$WORDPRESS_SHA1 *wordpress.tar.gz" | sha1sum -c -; 	tar -xzf wordpress.tar.gz -C /usr/src/; 	rm wordpress.tar.gz; 	chown -R www-data:www-data /usr/src/wordpress
# Tue, 21 Nov 2017 00:03:33 GMT
COPY file:db1f48c4963a4352b4c31c18f102b71fcc06a1266db6edd17f8f52458fe13130 in /usr/local/bin/ 
# Tue, 21 Nov 2017 00:03:33 GMT
ENTRYPOINT ["docker-entrypoint.sh"]
# Tue, 21 Nov 2017 00:03:33 GMT
CMD ["php-fpm"]
```

-	Layers:
	-	`sha256:49388a8c9c86a6f56d228954eede699c64fce6c671a989e3e21c391859694645`  
		Last Modified: Wed, 25 Oct 2017 23:22:36 GMT  
		Size: 2.4 MB (2385012 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:8e5f7c337501eeff98e19cc2d10f4c50fd8bfcce7fe2640fa219b410b1cc2676`  
		Last Modified: Sat, 04 Nov 2017 11:58:11 GMT  
		Size: 1.3 MB (1308940 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:2765a1878d4da8aa3135f8e56cfa7e36daa2a263efa8fd09357aba95f6535a98`  
		Last Modified: Sat, 04 Nov 2017 11:58:09 GMT  
		Size: 1.3 KB (1275 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:95785b88ca8822903609d4912df09c6ae0866313da1f6cfeb3a68b0d3bf2a14f`  
		Last Modified: Sat, 04 Nov 2017 11:58:08 GMT  
		Size: 167.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:d4b775d773898532112140444e7000d823c0fabcc7d4e730f7023b8900c50b58`  
		Last Modified: Sat, 04 Nov 2017 12:10:24 GMT  
		Size: 12.5 MB (12483422 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:12083e252a7eca6fa791b08d2e34d03b13edeb677df6e90ade04a9bded446af2`  
		Last Modified: Sat, 04 Nov 2017 12:10:18 GMT  
		Size: 496.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:b221705bc9586f0801a488eabab14906dbc30c1647db5816be027a473a7055ff`  
		Last Modified: Sat, 04 Nov 2017 12:10:23 GMT  
		Size: 10.0 MB (10008734 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:cfacf8c43403f32ac331df3a7055d849321966bc9d65f1440562a8ffe1bb8dcf`  
		Last Modified: Sat, 04 Nov 2017 12:10:18 GMT  
		Size: 2.2 KB (2160 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:49d6845fee8a7b6d2ae45f0bc27593bb3c489021da870e6a29ab3f15a48dc60b`  
		Last Modified: Sat, 04 Nov 2017 12:10:19 GMT  
		Size: 130.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:bc7e1afbf63473fc91e23615b2a2d46367cacb4afc76f4cb1677644404493c37`  
		Last Modified: Sat, 04 Nov 2017 12:10:18 GMT  
		Size: 7.6 KB (7603 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:5a96df89bf5cb921ef65621983597cd9e36bb80f55bf4fce09bd72b9f37d8bb3`  
		Last Modified: Sat, 04 Nov 2017 21:17:21 GMT  
		Size: 611.8 KB (611810 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:69b9a33ade54157b8ed9ae8597f0a917b65725c25816173693905d1524de6a2a`  
		Last Modified: Sat, 04 Nov 2017 21:17:21 GMT  
		Size: 733.1 KB (733080 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:7305490f187b6075a0abba8788921c1ff301d1ee3c8458540d660f2f44208f10`  
		Last Modified: Sat, 04 Nov 2017 21:17:21 GMT  
		Size: 337.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:324d1f219824e770c92a2c12ba7b09be81f28cb18ecd46a42ad6912bfd61b760`  
		Last Modified: Tue, 21 Nov 2017 00:07:39 GMT  
		Size: 9.5 MB (9471263 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:831d8b4e944fde900c43d7f92d4abaa39a7ed43f1e9fb42db61ea03c9d61ef73`  
		Last Modified: Tue, 21 Nov 2017 00:07:37 GMT  
		Size: 3.2 KB (3216 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
