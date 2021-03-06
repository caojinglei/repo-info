## `nextcloud:12-fpm`

```console
$ docker pull nextcloud@sha256:bc877a84894a6eb6dfaf8f87e35f0aa6663bf0c5aac1acec55719ffc92eee5f0
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

### `nextcloud:12-fpm` - linux; amd64

```console
$ docker pull nextcloud@sha256:f4fe345dfca5aefa8b280bd254c8925bb9eaca927e4e5bfa397f2677a858e888
```

-	Docker Version: 17.06.2-ce
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **247.2 MB (247215831 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:d04d81d907851c25bdf4e83e95f42deb00cf622897ce7118ec48abf6271906a3`
-	Entrypoint: `["\/entrypoint.sh"]`
-	Default Command: `["php-fpm"]`

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
# Sat, 04 Nov 2017 10:21:00 GMT
ENV PHP_EXTRA_CONFIGURE_ARGS=--enable-fpm --with-fpm-user=www-data --with-fpm-group=www-data
# Sat, 04 Nov 2017 10:21:00 GMT
ENV PHP_CFLAGS=-fstack-protector-strong -fpic -fpie -O2
# Sat, 04 Nov 2017 10:21:01 GMT
ENV PHP_CPPFLAGS=-fstack-protector-strong -fpic -fpie -O2
# Sat, 04 Nov 2017 10:21:01 GMT
ENV PHP_LDFLAGS=-Wl,-O1 -Wl,--hash-style=both -pie
# Sat, 04 Nov 2017 10:21:01 GMT
ENV GPG_KEYS=A917B1ECDA84AEC2B568FED6F50ABC807BD5DCD0 528995BFEDFBA7191D46839EF9BA0ADA31CBD89E
# Tue, 28 Nov 2017 00:08:15 GMT
ENV PHP_VERSION=7.1.12
# Tue, 28 Nov 2017 00:08:15 GMT
ENV PHP_URL=https://secure.php.net/get/php-7.1.12.tar.xz/from/this/mirror PHP_ASC_URL=https://secure.php.net/get/php-7.1.12.tar.xz.asc/from/this/mirror
# Tue, 28 Nov 2017 00:08:15 GMT
ENV PHP_SHA256=a0118850774571b1f2d4e30b4fe7a4b958ca66f07d07d65ebdc789c54ba6eeb3 PHP_MD5=
# Tue, 28 Nov 2017 00:08:31 GMT
RUN set -xe; 		fetchDeps=' 		wget 	'; 	if ! command -v gpg > /dev/null; then 		fetchDeps="$fetchDeps 			dirmngr 			gnupg 		"; 	fi; 	apt-get update; 	apt-get install -y --no-install-recommends $fetchDeps; 	rm -rf /var/lib/apt/lists/*; 		mkdir -p /usr/src; 	cd /usr/src; 		wget -O php.tar.xz "$PHP_URL"; 		if [ -n "$PHP_SHA256" ]; then 		echo "$PHP_SHA256 *php.tar.xz" | sha256sum -c -; 	fi; 	if [ -n "$PHP_MD5" ]; then 		echo "$PHP_MD5 *php.tar.xz" | md5sum -c -; 	fi; 		if [ -n "$PHP_ASC_URL" ]; then 		wget -O php.tar.xz.asc "$PHP_ASC_URL"; 		export GNUPGHOME="$(mktemp -d)"; 		for key in $GPG_KEYS; do 			gpg --keyserver ha.pool.sks-keyservers.net --recv-keys "$key"; 		done; 		gpg --batch --verify php.tar.xz.asc php.tar.xz; 		rm -rf "$GNUPGHOME"; 	fi; 		apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false $fetchDeps
# Tue, 28 Nov 2017 00:08:31 GMT
COPY file:207c686e3fed4f71f8a7b245d8dcae9c9048d276a326d82b553c12a90af0c0ca in /usr/local/bin/ 
# Tue, 28 Nov 2017 00:12:58 GMT
RUN set -xe 	&& buildDeps=" 		$PHP_EXTRA_BUILD_DEPS 		libcurl4-openssl-dev 		libedit-dev 		libsqlite3-dev 		libssl-dev 		libxml2-dev 		zlib1g-dev 	" 	&& apt-get update && apt-get install -y $buildDeps --no-install-recommends && rm -rf /var/lib/apt/lists/* 		&& export CFLAGS="$PHP_CFLAGS" 		CPPFLAGS="$PHP_CPPFLAGS" 		LDFLAGS="$PHP_LDFLAGS" 	&& docker-php-source extract 	&& cd /usr/src/php 	&& gnuArch="$(dpkg-architecture --query DEB_BUILD_GNU_TYPE)" 	&& debMultiarch="$(dpkg-architecture --query DEB_BUILD_MULTIARCH)" 	&& if [ ! -d /usr/include/curl ]; then 		ln -sT "/usr/include/$debMultiarch/curl" /usr/local/include/curl; 	fi 	&& ./configure 		--build="$gnuArch" 		--with-config-file-path="$PHP_INI_DIR" 		--with-config-file-scan-dir="$PHP_INI_DIR/conf.d" 				--disable-cgi 				--enable-ftp 		--enable-mbstring 		--enable-mysqlnd 				--with-curl 		--with-libedit 		--with-openssl 		--with-zlib 				--with-pcre-regex=/usr 		--with-libdir="lib/$debMultiarch" 				$PHP_EXTRA_CONFIGURE_ARGS 	&& make -j "$(nproc)" 	&& make install 	&& { find /usr/local/bin /usr/local/sbin -type f -executable -exec strip --strip-all '{}' + || true; } 	&& make clean 	&& cd / 	&& docker-php-source delete 		&& apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false $buildDeps 		&& pecl update-channels 	&& rm -rf /tmp/pear ~/.pearrc
# Tue, 28 Nov 2017 00:12:59 GMT
COPY multi:3a3ce8aa3891c64454909e9f8257446a1817abe660b49a7baaa26f28bfdc444d in /usr/local/bin/ 
# Tue, 28 Nov 2017 00:12:59 GMT
ENTRYPOINT ["docker-php-entrypoint"]
# Tue, 28 Nov 2017 00:12:59 GMT
WORKDIR /var/www/html
# Tue, 28 Nov 2017 00:13:00 GMT
RUN set -ex 	&& cd /usr/local/etc 	&& if [ -d php-fpm.d ]; then 		sed 's!=NONE/!=!g' php-fpm.conf.default | tee php-fpm.conf > /dev/null; 		cp php-fpm.d/www.conf.default php-fpm.d/www.conf; 	else 		mkdir php-fpm.d; 		cp php-fpm.conf.default php-fpm.d/www.conf; 		{ 			echo '[global]'; 			echo 'include=etc/php-fpm.d/*.conf'; 		} | tee php-fpm.conf; 	fi 	&& { 		echo '[global]'; 		echo 'error_log = /proc/self/fd/2'; 		echo; 		echo '[www]'; 		echo '; if we send this to /proc/self/fd/1, it never appears'; 		echo 'access.log = /proc/self/fd/2'; 		echo; 		echo 'clear_env = no'; 		echo; 		echo '; Ensure worker stdout and stderr are sent to the main error log.'; 		echo 'catch_workers_output = yes'; 	} | tee php-fpm.d/docker.conf 	&& { 		echo '[global]'; 		echo 'daemonize = no'; 		echo; 		echo '[www]'; 		echo 'listen = [::]:9000'; 	} | tee php-fpm.d/zz-docker.conf
# Tue, 28 Nov 2017 00:13:00 GMT
EXPOSE 9000/tcp
# Tue, 28 Nov 2017 00:13:01 GMT
CMD ["php-fpm"]
# Tue, 28 Nov 2017 02:37:46 GMT
RUN apt-get update && apt-get install -y   rsync   bzip2   libcurl4-openssl-dev   libfreetype6-dev   libicu-dev   libjpeg-dev   libldap2-dev   libmcrypt-dev   libmemcached-dev   libpng12-dev   libpq-dev   libxml2-dev   && rm -rf /var/lib/apt/lists/*
# Tue, 28 Nov 2017 02:39:57 GMT
RUN debMultiarch="$(dpkg-architecture --query DEB_BUILD_MULTIARCH)"   && docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr   && docker-php-ext-configure ldap --with-libdir="lib/$debMultiarch"   && docker-php-ext-install gd exif intl mbstring mcrypt ldap mysqli opcache pdo_mysql pdo_pgsql pgsql zip pcntl
# Tue, 28 Nov 2017 02:39:58 GMT
RUN {   echo 'opcache.enable=1';   echo 'opcache.enable_cli=1';   echo 'opcache.interned_strings_buffer=8';   echo 'opcache.max_accelerated_files=10000';   echo 'opcache.memory_consumption=128';   echo 'opcache.save_comments=1';   echo 'opcache.revalidate_freq=1';   } > /usr/local/etc/php/conf.d/opcache-recommended.ini
# Tue, 28 Nov 2017 02:40:29 GMT
RUN set -ex  && pecl install APCu-5.1.8  && pecl install memcached-3.0.4  && pecl install redis-3.1.4  && docker-php-ext-enable apcu redis memcached
# Tue, 28 Nov 2017 02:45:16 GMT
ENV NEXTCLOUD_VERSION=12.0.3
# Tue, 28 Nov 2017 02:45:17 GMT
RUN chown -R www-data:root /var/www/html &&     chmod -R g=u /var/www/html
# Tue, 28 Nov 2017 02:45:17 GMT
VOLUME [/var/www/html]
# Tue, 28 Nov 2017 02:45:31 GMT
RUN curl -fsSL -o nextcloud.tar.bz2     "https://download.nextcloud.com/server/releases/nextcloud-${NEXTCLOUD_VERSION}.tar.bz2"  && curl -fsSL -o nextcloud.tar.bz2.asc     "https://download.nextcloud.com/server/releases/nextcloud-${NEXTCLOUD_VERSION}.tar.bz2.asc"  && export GNUPGHOME="$(mktemp -d)"  && gpg --keyserver ha.pool.sks-keyservers.net --recv-keys 28806A878AE423A28372792ED75899B9A724937A  && gpg --batch --verify nextcloud.tar.bz2.asc nextcloud.tar.bz2  && rm -r "$GNUPGHOME" nextcloud.tar.bz2.asc  && tar -xjf nextcloud.tar.bz2 -C /usr/src/  && rm nextcloud.tar.bz2  && rm -rf /usr/src/nextcloud/updater  && mkdir -p /usr/src/nextcloud/data  && mkdir -p /usr/src/nextcloud/custom_apps  && chmod +x /usr/src/nextcloud/occ
# Tue, 28 Nov 2017 02:45:31 GMT
COPY file:3fa42fa6664f03c90280a265050a78ef70bf32cd31864db727f5ee7e94828722 in /entrypoint.sh 
# Tue, 28 Nov 2017 02:45:32 GMT
COPY multi:55b88fcd3d6a1a8ca5ef52e5d2c9e27370c13cdc4c5e94d159f82a32979740ff in /usr/src/nextcloud/config/ 
# Tue, 28 Nov 2017 02:45:32 GMT
ENTRYPOINT ["/entrypoint.sh"]
# Tue, 28 Nov 2017 02:45:32 GMT
CMD ["php-fpm"]
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
	-	`sha256:bfab6c379f391cfb1f66ebd751091084baf090beedde6dcf74d9483ae6dc2fb5`  
		Last Modified: Tue, 28 Nov 2017 01:25:33 GMT  
		Size: 12.5 MB (12532158 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:486471da0095d87278eccb7701ecf0cb6bfb190ac494478f89a26ebae008db54`  
		Last Modified: Tue, 28 Nov 2017 01:25:29 GMT  
		Size: 501.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:05a7b993700f77cba75eef4062c7322d5e34568f7ecd9c74e26959714e4fa049`  
		Last Modified: Tue, 28 Nov 2017 01:25:36 GMT  
		Size: 13.3 MB (13289708 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:f7837e27d38cf07d15698afbd812fdf9913ef924e59c783d6fa6f2caf117ac38`  
		Last Modified: Tue, 28 Nov 2017 01:25:29 GMT  
		Size: 2.2 KB (2171 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:242d326df421849cdd538b299d5fb6b82060e366a143497711e625b799bcb6a1`  
		Last Modified: Tue, 28 Nov 2017 01:25:29 GMT  
		Size: 130.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:68f1785f293b2ad89a33613acd4f7abf345ed6848445fd1a1cbfa8c913d9c790`  
		Last Modified: Tue, 28 Nov 2017 01:25:31 GMT  
		Size: 7.7 KB (7680 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:d615e6734f17e5c67c9a0da9a1268751c42d3c7d48f968db3e787ba732d3af90`  
		Last Modified: Tue, 28 Nov 2017 02:51:17 GMT  
		Size: 36.1 MB (36094847 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:e0cf663e7d6544b0327e168c0dfccf7f706fd7fae8fdc90ddb2981436f8fb693`  
		Last Modified: Tue, 28 Nov 2017 02:51:06 GMT  
		Size: 1.9 MB (1920152 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:68215b711797e311667b96518830a2f73a2a4a564b7681400f4ed156442ab8f1`  
		Last Modified: Tue, 28 Nov 2017 02:51:04 GMT  
		Size: 352.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:08ef69cb5ccc42a2f528c2ea2a6dde28fdab2da52305ea7660e7d05a71359172`  
		Last Modified: Tue, 28 Nov 2017 02:51:03 GMT  
		Size: 1.3 MB (1303078 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:05c0c3e37702fa1dbfb79e43b92d597b0a757ba4d09660691f948bf1b7793950`  
		Last Modified: Tue, 28 Nov 2017 02:51:02 GMT  
		Size: 135.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:7e6b42e2c5a152740c64bdfd154dabb9f63fcaf3635852f2ee3d6b528c29605b`  
		Last Modified: Tue, 28 Nov 2017 02:53:58 GMT  
		Size: 47.0 MB (46970318 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:8056817678cc6d081bc41dc7296aa6c1d22c3e4e26d97f6920c35087dff61197`  
		Last Modified: Tue, 28 Nov 2017 02:53:36 GMT  
		Size: 940.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:f9c3aa46f5e6a63eeeb8c1b4c93e6d6e134bc43d26d9649a64f17b6ae6df33b0`  
		Last Modified: Tue, 28 Nov 2017 02:53:36 GMT  
		Size: 783.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip

### `nextcloud:12-fpm` - linux; arm variant v5

```console
$ docker pull nextcloud@sha256:5a3269233239843c7d7fcb5cbee60c9a8429c3cb1b4e519b639c616e540101d8
```

-	Docker Version: 17.06.0-ce
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **227.6 MB (227563032 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:de12156b06af6f4ce3a54fcb9c90d832c57ab3495c8d5656110819aa3c01bd06`
-	Entrypoint: `["\/entrypoint.sh"]`
-	Default Command: `["php-fpm"]`

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
# Mon, 09 Oct 2017 22:55:05 GMT
ENV PHP_EXTRA_CONFIGURE_ARGS=--enable-fpm --with-fpm-user=www-data --with-fpm-group=www-data
# Mon, 09 Oct 2017 22:55:05 GMT
ENV PHP_CFLAGS=-fstack-protector-strong -fpic -fpie -O2
# Mon, 09 Oct 2017 22:55:06 GMT
ENV PHP_CPPFLAGS=-fstack-protector-strong -fpic -fpie -O2
# Mon, 09 Oct 2017 22:55:06 GMT
ENV PHP_LDFLAGS=-Wl,-O1 -Wl,--hash-style=both -pie
# Mon, 09 Oct 2017 22:55:06 GMT
ENV GPG_KEYS=A917B1ECDA84AEC2B568FED6F50ABC807BD5DCD0 528995BFEDFBA7191D46839EF9BA0ADA31CBD89E
# Tue, 28 Nov 2017 14:46:11 GMT
ENV PHP_VERSION=7.1.12
# Tue, 28 Nov 2017 14:46:11 GMT
ENV PHP_URL=https://secure.php.net/get/php-7.1.12.tar.xz/from/this/mirror PHP_ASC_URL=https://secure.php.net/get/php-7.1.12.tar.xz.asc/from/this/mirror
# Tue, 28 Nov 2017 14:46:11 GMT
ENV PHP_SHA256=a0118850774571b1f2d4e30b4fe7a4b958ca66f07d07d65ebdc789c54ba6eeb3 PHP_MD5=
# Tue, 28 Nov 2017 14:46:51 GMT
RUN set -xe; 		fetchDeps=' 		wget 	'; 	if ! command -v gpg > /dev/null; then 		fetchDeps="$fetchDeps 			dirmngr 			gnupg 		"; 	fi; 	apt-get update; 	apt-get install -y --no-install-recommends $fetchDeps; 	rm -rf /var/lib/apt/lists/*; 		mkdir -p /usr/src; 	cd /usr/src; 		wget -O php.tar.xz "$PHP_URL"; 		if [ -n "$PHP_SHA256" ]; then 		echo "$PHP_SHA256 *php.tar.xz" | sha256sum -c -; 	fi; 	if [ -n "$PHP_MD5" ]; then 		echo "$PHP_MD5 *php.tar.xz" | md5sum -c -; 	fi; 		if [ -n "$PHP_ASC_URL" ]; then 		wget -O php.tar.xz.asc "$PHP_ASC_URL"; 		export GNUPGHOME="$(mktemp -d)"; 		for key in $GPG_KEYS; do 			gpg --keyserver ha.pool.sks-keyservers.net --recv-keys "$key"; 		done; 		gpg --batch --verify php.tar.xz.asc php.tar.xz; 		rm -rf "$GNUPGHOME"; 	fi; 		apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false $fetchDeps
# Tue, 28 Nov 2017 14:46:51 GMT
COPY file:207c686e3fed4f71f8a7b245d8dcae9c9048d276a326d82b553c12a90af0c0ca in /usr/local/bin/ 
# Tue, 28 Nov 2017 14:50:13 GMT
RUN set -xe 	&& buildDeps=" 		$PHP_EXTRA_BUILD_DEPS 		libcurl4-openssl-dev 		libedit-dev 		libsqlite3-dev 		libssl-dev 		libxml2-dev 		zlib1g-dev 	" 	&& apt-get update && apt-get install -y $buildDeps --no-install-recommends && rm -rf /var/lib/apt/lists/* 		&& export CFLAGS="$PHP_CFLAGS" 		CPPFLAGS="$PHP_CPPFLAGS" 		LDFLAGS="$PHP_LDFLAGS" 	&& docker-php-source extract 	&& cd /usr/src/php 	&& gnuArch="$(dpkg-architecture --query DEB_BUILD_GNU_TYPE)" 	&& debMultiarch="$(dpkg-architecture --query DEB_BUILD_MULTIARCH)" 	&& if [ ! -d /usr/include/curl ]; then 		ln -sT "/usr/include/$debMultiarch/curl" /usr/local/include/curl; 	fi 	&& ./configure 		--build="$gnuArch" 		--with-config-file-path="$PHP_INI_DIR" 		--with-config-file-scan-dir="$PHP_INI_DIR/conf.d" 				--disable-cgi 				--enable-ftp 		--enable-mbstring 		--enable-mysqlnd 				--with-curl 		--with-libedit 		--with-openssl 		--with-zlib 				--with-pcre-regex=/usr 		--with-libdir="lib/$debMultiarch" 				$PHP_EXTRA_CONFIGURE_ARGS 	&& make -j "$(nproc)" 	&& make install 	&& { find /usr/local/bin /usr/local/sbin -type f -executable -exec strip --strip-all '{}' + || true; } 	&& make clean 	&& cd / 	&& docker-php-source delete 		&& apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false $buildDeps 		&& pecl update-channels 	&& rm -rf /tmp/pear ~/.pearrc
# Tue, 28 Nov 2017 14:50:14 GMT
COPY multi:3a3ce8aa3891c64454909e9f8257446a1817abe660b49a7baaa26f28bfdc444d in /usr/local/bin/ 
# Tue, 28 Nov 2017 14:50:14 GMT
ENTRYPOINT ["docker-php-entrypoint"]
# Tue, 28 Nov 2017 14:50:14 GMT
WORKDIR /var/www/html
# Tue, 28 Nov 2017 14:50:15 GMT
RUN set -ex 	&& cd /usr/local/etc 	&& if [ -d php-fpm.d ]; then 		sed 's!=NONE/!=!g' php-fpm.conf.default | tee php-fpm.conf > /dev/null; 		cp php-fpm.d/www.conf.default php-fpm.d/www.conf; 	else 		mkdir php-fpm.d; 		cp php-fpm.conf.default php-fpm.d/www.conf; 		{ 			echo '[global]'; 			echo 'include=etc/php-fpm.d/*.conf'; 		} | tee php-fpm.conf; 	fi 	&& { 		echo '[global]'; 		echo 'error_log = /proc/self/fd/2'; 		echo; 		echo '[www]'; 		echo '; if we send this to /proc/self/fd/1, it never appears'; 		echo 'access.log = /proc/self/fd/2'; 		echo; 		echo 'clear_env = no'; 		echo; 		echo '; Ensure worker stdout and stderr are sent to the main error log.'; 		echo 'catch_workers_output = yes'; 	} | tee php-fpm.d/docker.conf 	&& { 		echo '[global]'; 		echo 'daemonize = no'; 		echo; 		echo '[www]'; 		echo 'listen = [::]:9000'; 	} | tee php-fpm.d/zz-docker.conf
# Tue, 28 Nov 2017 14:50:15 GMT
EXPOSE 9000/tcp
# Tue, 28 Nov 2017 14:50:16 GMT
CMD ["php-fpm"]
# Tue, 28 Nov 2017 15:43:09 GMT
RUN apt-get update && apt-get install -y   rsync   bzip2   libcurl4-openssl-dev   libfreetype6-dev   libicu-dev   libjpeg-dev   libldap2-dev   libmcrypt-dev   libmemcached-dev   libpng12-dev   libpq-dev   libxml2-dev   && rm -rf /var/lib/apt/lists/*
# Tue, 28 Nov 2017 15:47:48 GMT
RUN debMultiarch="$(dpkg-architecture --query DEB_BUILD_MULTIARCH)"   && docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr   && docker-php-ext-configure ldap --with-libdir="lib/$debMultiarch"   && docker-php-ext-install gd exif intl mbstring mcrypt ldap mysqli opcache pdo_mysql pdo_pgsql pgsql zip pcntl
# Tue, 28 Nov 2017 15:47:49 GMT
RUN {   echo 'opcache.enable=1';   echo 'opcache.enable_cli=1';   echo 'opcache.interned_strings_buffer=8';   echo 'opcache.max_accelerated_files=10000';   echo 'opcache.memory_consumption=128';   echo 'opcache.save_comments=1';   echo 'opcache.revalidate_freq=1';   } > /usr/local/etc/php/conf.d/opcache-recommended.ini
# Tue, 28 Nov 2017 15:48:38 GMT
RUN set -ex  && pecl install APCu-5.1.8  && pecl install memcached-3.0.4  && pecl install redis-3.1.4  && docker-php-ext-enable apcu redis memcached
# Tue, 28 Nov 2017 15:50:12 GMT
ENV NEXTCLOUD_VERSION=12.0.3
# Tue, 28 Nov 2017 15:50:13 GMT
RUN chown -R www-data:root /var/www/html &&     chmod -R g=u /var/www/html
# Tue, 28 Nov 2017 15:50:13 GMT
VOLUME [/var/www/html]
# Tue, 28 Nov 2017 15:50:33 GMT
RUN curl -fsSL -o nextcloud.tar.bz2     "https://download.nextcloud.com/server/releases/nextcloud-${NEXTCLOUD_VERSION}.tar.bz2"  && curl -fsSL -o nextcloud.tar.bz2.asc     "https://download.nextcloud.com/server/releases/nextcloud-${NEXTCLOUD_VERSION}.tar.bz2.asc"  && export GNUPGHOME="$(mktemp -d)"  && gpg --keyserver ha.pool.sks-keyservers.net --recv-keys 28806A878AE423A28372792ED75899B9A724937A  && gpg --batch --verify nextcloud.tar.bz2.asc nextcloud.tar.bz2  && rm -r "$GNUPGHOME" nextcloud.tar.bz2.asc  && tar -xjf nextcloud.tar.bz2 -C /usr/src/  && rm nextcloud.tar.bz2  && rm -rf /usr/src/nextcloud/updater  && mkdir -p /usr/src/nextcloud/data  && mkdir -p /usr/src/nextcloud/custom_apps  && chmod +x /usr/src/nextcloud/occ
# Tue, 28 Nov 2017 15:50:38 GMT
COPY file:3fa42fa6664f03c90280a265050a78ef70bf32cd31864db727f5ee7e94828722 in /entrypoint.sh 
# Tue, 28 Nov 2017 15:50:39 GMT
COPY multi:55b88fcd3d6a1a8ca5ef52e5d2c9e27370c13cdc4c5e94d159f82a32979740ff in /usr/src/nextcloud/config/ 
# Tue, 28 Nov 2017 15:50:39 GMT
ENTRYPOINT ["/entrypoint.sh"]
# Tue, 28 Nov 2017 15:50:39 GMT
CMD ["php-fpm"]
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
	-	`sha256:0ca8b3335a1ce050249651ec7f4e4cf903a0677f30bb318baa76bf7de4600052`  
		Last Modified: Tue, 28 Nov 2017 15:15:08 GMT  
		Size: 12.5 MB (12530660 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:27da2e461a466ce16e6913b45f869dd14b0aba1570a623f382bb5aa193fc0d44`  
		Last Modified: Tue, 28 Nov 2017 15:15:05 GMT  
		Size: 502.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:4499e7ef74b0f33857ba647a7d53bdd61656ec72638a9713d6c528cec4202ad2`  
		Last Modified: Tue, 28 Nov 2017 15:15:10 GMT  
		Size: 14.4 MB (14422616 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:66adb093cc3c4bb3e3051ddcd688129488fc958af9201edb491e7bf5e4d4a825`  
		Last Modified: Tue, 28 Nov 2017 15:15:05 GMT  
		Size: 2.2 KB (2172 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:f4b0ae0f3db0ed5a36d04b4a9d9815f1b26e3ce93d80bffef60cd6fb9c586bbc`  
		Last Modified: Tue, 28 Nov 2017 15:15:05 GMT  
		Size: 161.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:c97d4759c8d9d3019a0523731eb9b9d0d7e2eb7bfc0e2a8043378b539d5523ad`  
		Last Modified: Tue, 28 Nov 2017 15:15:05 GMT  
		Size: 7.7 KB (7682 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:b93e59b1b8d8196091d6aed59993f0238df2fcfc81aee6880575ba896e41b01c`  
		Last Modified: Tue, 28 Nov 2017 15:52:39 GMT  
		Size: 36.0 MB (36022476 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:87beb91ffda8aae3274cf13e0911f0c4ced2ae5092c8e1c6f62c0f64c8ba7f80`  
		Last Modified: Tue, 28 Nov 2017 15:52:26 GMT  
		Size: 1.8 MB (1847636 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:c509bf9f0f44d3c79cdfae95c130b4fc33f7159ec47e76e88701300f2bdc806b`  
		Last Modified: Tue, 28 Nov 2017 15:52:26 GMT  
		Size: 354.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:08963cef93deaf0edb097a2c0211a9da7cdb3f03486d8a210802800569d13675`  
		Last Modified: Tue, 28 Nov 2017 15:52:25 GMT  
		Size: 1.3 MB (1349480 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:434e00c505cf9d7a17e784422eb5e39427a927157b7e2cfd99d865cf5b3bb911`  
		Last Modified: Tue, 28 Nov 2017 15:52:24 GMT  
		Size: 135.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:2283f30d2a7216b3dc6fad60a3596776f00b905ce1ca1e3d467877ec6aab2afb`  
		Last Modified: Tue, 28 Nov 2017 15:55:17 GMT  
		Size: 47.0 MB (46970373 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:d36e9e81933a639ec1b42dca5c526e0840ed6fe92820118a134f2b85a75843c1`  
		Last Modified: Tue, 28 Nov 2017 15:54:59 GMT  
		Size: 941.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:d56f5b9327ed1779aaf68869fdb5fa96ca0fe00a2d730d306aae425f8d437522`  
		Last Modified: Tue, 28 Nov 2017 15:55:01 GMT  
		Size: 784.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip

### `nextcloud:12-fpm` - linux; arm variant v7

```console
$ docker pull nextcloud@sha256:3e197bea176ce0030ae1ca685de53047baa414dd717ae0b1562681c81fdc31f2
```

-	Docker Version: 17.06.0-ce
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **223.1 MB (223134799 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:943052c2e86c1ec7269434cf392d6b79490036a1babf34591022bb20cd7bcac5`
-	Entrypoint: `["\/entrypoint.sh"]`
-	Default Command: `["php-fpm"]`

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
# Mon, 09 Oct 2017 23:19:26 GMT
ENV PHP_EXTRA_CONFIGURE_ARGS=--enable-fpm --with-fpm-user=www-data --with-fpm-group=www-data
# Mon, 09 Oct 2017 23:19:26 GMT
ENV PHP_CFLAGS=-fstack-protector-strong -fpic -fpie -O2
# Mon, 09 Oct 2017 23:19:26 GMT
ENV PHP_CPPFLAGS=-fstack-protector-strong -fpic -fpie -O2
# Mon, 09 Oct 2017 23:19:27 GMT
ENV PHP_LDFLAGS=-Wl,-O1 -Wl,--hash-style=both -pie
# Mon, 09 Oct 2017 23:19:27 GMT
ENV GPG_KEYS=A917B1ECDA84AEC2B568FED6F50ABC807BD5DCD0 528995BFEDFBA7191D46839EF9BA0ADA31CBD89E
# Tue, 28 Nov 2017 12:56:56 GMT
ENV PHP_VERSION=7.1.12
# Tue, 28 Nov 2017 12:56:56 GMT
ENV PHP_URL=https://secure.php.net/get/php-7.1.12.tar.xz/from/this/mirror PHP_ASC_URL=https://secure.php.net/get/php-7.1.12.tar.xz.asc/from/this/mirror
# Tue, 28 Nov 2017 12:56:56 GMT
ENV PHP_SHA256=a0118850774571b1f2d4e30b4fe7a4b958ca66f07d07d65ebdc789c54ba6eeb3 PHP_MD5=
# Tue, 28 Nov 2017 12:57:35 GMT
RUN set -xe; 		fetchDeps=' 		wget 	'; 	if ! command -v gpg > /dev/null; then 		fetchDeps="$fetchDeps 			dirmngr 			gnupg 		"; 	fi; 	apt-get update; 	apt-get install -y --no-install-recommends $fetchDeps; 	rm -rf /var/lib/apt/lists/*; 		mkdir -p /usr/src; 	cd /usr/src; 		wget -O php.tar.xz "$PHP_URL"; 		if [ -n "$PHP_SHA256" ]; then 		echo "$PHP_SHA256 *php.tar.xz" | sha256sum -c -; 	fi; 	if [ -n "$PHP_MD5" ]; then 		echo "$PHP_MD5 *php.tar.xz" | md5sum -c -; 	fi; 		if [ -n "$PHP_ASC_URL" ]; then 		wget -O php.tar.xz.asc "$PHP_ASC_URL"; 		export GNUPGHOME="$(mktemp -d)"; 		for key in $GPG_KEYS; do 			gpg --keyserver ha.pool.sks-keyservers.net --recv-keys "$key"; 		done; 		gpg --batch --verify php.tar.xz.asc php.tar.xz; 		rm -rf "$GNUPGHOME"; 	fi; 		apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false $fetchDeps
# Tue, 28 Nov 2017 12:57:36 GMT
COPY file:207c686e3fed4f71f8a7b245d8dcae9c9048d276a326d82b553c12a90af0c0ca in /usr/local/bin/ 
# Tue, 28 Nov 2017 13:00:44 GMT
RUN set -xe 	&& buildDeps=" 		$PHP_EXTRA_BUILD_DEPS 		libcurl4-openssl-dev 		libedit-dev 		libsqlite3-dev 		libssl-dev 		libxml2-dev 		zlib1g-dev 	" 	&& apt-get update && apt-get install -y $buildDeps --no-install-recommends && rm -rf /var/lib/apt/lists/* 		&& export CFLAGS="$PHP_CFLAGS" 		CPPFLAGS="$PHP_CPPFLAGS" 		LDFLAGS="$PHP_LDFLAGS" 	&& docker-php-source extract 	&& cd /usr/src/php 	&& gnuArch="$(dpkg-architecture --query DEB_BUILD_GNU_TYPE)" 	&& debMultiarch="$(dpkg-architecture --query DEB_BUILD_MULTIARCH)" 	&& if [ ! -d /usr/include/curl ]; then 		ln -sT "/usr/include/$debMultiarch/curl" /usr/local/include/curl; 	fi 	&& ./configure 		--build="$gnuArch" 		--with-config-file-path="$PHP_INI_DIR" 		--with-config-file-scan-dir="$PHP_INI_DIR/conf.d" 				--disable-cgi 				--enable-ftp 		--enable-mbstring 		--enable-mysqlnd 				--with-curl 		--with-libedit 		--with-openssl 		--with-zlib 				--with-pcre-regex=/usr 		--with-libdir="lib/$debMultiarch" 				$PHP_EXTRA_CONFIGURE_ARGS 	&& make -j "$(nproc)" 	&& make install 	&& { find /usr/local/bin /usr/local/sbin -type f -executable -exec strip --strip-all '{}' + || true; } 	&& make clean 	&& cd / 	&& docker-php-source delete 		&& apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false $buildDeps 		&& pecl update-channels 	&& rm -rf /tmp/pear ~/.pearrc
# Tue, 28 Nov 2017 13:00:45 GMT
COPY multi:3a3ce8aa3891c64454909e9f8257446a1817abe660b49a7baaa26f28bfdc444d in /usr/local/bin/ 
# Tue, 28 Nov 2017 13:00:46 GMT
ENTRYPOINT ["docker-php-entrypoint"]
# Tue, 28 Nov 2017 13:00:46 GMT
WORKDIR /var/www/html
# Tue, 28 Nov 2017 13:00:47 GMT
RUN set -ex 	&& cd /usr/local/etc 	&& if [ -d php-fpm.d ]; then 		sed 's!=NONE/!=!g' php-fpm.conf.default | tee php-fpm.conf > /dev/null; 		cp php-fpm.d/www.conf.default php-fpm.d/www.conf; 	else 		mkdir php-fpm.d; 		cp php-fpm.conf.default php-fpm.d/www.conf; 		{ 			echo '[global]'; 			echo 'include=etc/php-fpm.d/*.conf'; 		} | tee php-fpm.conf; 	fi 	&& { 		echo '[global]'; 		echo 'error_log = /proc/self/fd/2'; 		echo; 		echo '[www]'; 		echo '; if we send this to /proc/self/fd/1, it never appears'; 		echo 'access.log = /proc/self/fd/2'; 		echo; 		echo 'clear_env = no'; 		echo; 		echo '; Ensure worker stdout and stderr are sent to the main error log.'; 		echo 'catch_workers_output = yes'; 	} | tee php-fpm.d/docker.conf 	&& { 		echo '[global]'; 		echo 'daemonize = no'; 		echo; 		echo '[www]'; 		echo 'listen = [::]:9000'; 	} | tee php-fpm.d/zz-docker.conf
# Tue, 28 Nov 2017 13:00:47 GMT
EXPOSE 9000/tcp
# Tue, 28 Nov 2017 13:00:47 GMT
CMD ["php-fpm"]
# Tue, 28 Nov 2017 13:56:16 GMT
RUN apt-get update && apt-get install -y   rsync   bzip2   libcurl4-openssl-dev   libfreetype6-dev   libicu-dev   libjpeg-dev   libldap2-dev   libmcrypt-dev   libmemcached-dev   libpng12-dev   libpq-dev   libxml2-dev   && rm -rf /var/lib/apt/lists/*
# Tue, 28 Nov 2017 14:00:22 GMT
RUN debMultiarch="$(dpkg-architecture --query DEB_BUILD_MULTIARCH)"   && docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr   && docker-php-ext-configure ldap --with-libdir="lib/$debMultiarch"   && docker-php-ext-install gd exif intl mbstring mcrypt ldap mysqli opcache pdo_mysql pdo_pgsql pgsql zip pcntl
# Tue, 28 Nov 2017 14:00:29 GMT
RUN {   echo 'opcache.enable=1';   echo 'opcache.enable_cli=1';   echo 'opcache.interned_strings_buffer=8';   echo 'opcache.max_accelerated_files=10000';   echo 'opcache.memory_consumption=128';   echo 'opcache.save_comments=1';   echo 'opcache.revalidate_freq=1';   } > /usr/local/etc/php/conf.d/opcache-recommended.ini
# Tue, 28 Nov 2017 14:01:13 GMT
RUN set -ex  && pecl install APCu-5.1.8  && pecl install memcached-3.0.4  && pecl install redis-3.1.4  && docker-php-ext-enable apcu redis memcached
# Tue, 28 Nov 2017 14:03:26 GMT
ENV NEXTCLOUD_VERSION=12.0.3
# Tue, 28 Nov 2017 14:03:28 GMT
RUN chown -R www-data:root /var/www/html &&     chmod -R g=u /var/www/html
# Tue, 28 Nov 2017 14:03:28 GMT
VOLUME [/var/www/html]
# Tue, 28 Nov 2017 14:03:47 GMT
RUN curl -fsSL -o nextcloud.tar.bz2     "https://download.nextcloud.com/server/releases/nextcloud-${NEXTCLOUD_VERSION}.tar.bz2"  && curl -fsSL -o nextcloud.tar.bz2.asc     "https://download.nextcloud.com/server/releases/nextcloud-${NEXTCLOUD_VERSION}.tar.bz2.asc"  && export GNUPGHOME="$(mktemp -d)"  && gpg --keyserver ha.pool.sks-keyservers.net --recv-keys 28806A878AE423A28372792ED75899B9A724937A  && gpg --batch --verify nextcloud.tar.bz2.asc nextcloud.tar.bz2  && rm -r "$GNUPGHOME" nextcloud.tar.bz2.asc  && tar -xjf nextcloud.tar.bz2 -C /usr/src/  && rm nextcloud.tar.bz2  && rm -rf /usr/src/nextcloud/updater  && mkdir -p /usr/src/nextcloud/data  && mkdir -p /usr/src/nextcloud/custom_apps  && chmod +x /usr/src/nextcloud/occ
# Tue, 28 Nov 2017 14:03:49 GMT
COPY file:3fa42fa6664f03c90280a265050a78ef70bf32cd31864db727f5ee7e94828722 in /entrypoint.sh 
# Tue, 28 Nov 2017 14:03:50 GMT
COPY multi:55b88fcd3d6a1a8ca5ef52e5d2c9e27370c13cdc4c5e94d159f82a32979740ff in /usr/src/nextcloud/config/ 
# Tue, 28 Nov 2017 14:03:51 GMT
ENTRYPOINT ["/entrypoint.sh"]
# Tue, 28 Nov 2017 14:03:51 GMT
CMD ["php-fpm"]
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
	-	`sha256:33f015c0c617ccd56a4e5e0e40db3db18967debc5bfc94342c32db97aa4ad760`  
		Last Modified: Tue, 28 Nov 2017 13:26:03 GMT  
		Size: 12.5 MB (12530635 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:09ec322beaa823a5fd2b4a2117ed72e37fde380e2f118cc0d794a60be6c27a08`  
		Last Modified: Tue, 28 Nov 2017 13:26:00 GMT  
		Size: 500.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:2d7ae4137239a5d76a123cd13d9e19b3bf2e333be113598caeea8eb505c35ec7`  
		Last Modified: Tue, 28 Nov 2017 13:26:04 GMT  
		Size: 13.6 MB (13635029 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:9afe4a193cd029dbe5291e988335a7a9d02786fcc4ead4d822323b2555c58a2e`  
		Last Modified: Tue, 28 Nov 2017 13:26:01 GMT  
		Size: 2.2 KB (2174 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:ac21a0bda29dc22ae2cf772fe73fad699d2a377b735355ef2efb280910050ab0`  
		Last Modified: Tue, 28 Nov 2017 13:26:01 GMT  
		Size: 160.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:9a26cf010a1396763aaf90b196120996b0687b6e8d80998f205e5b17cb23d3a5`  
		Last Modified: Tue, 28 Nov 2017 13:26:02 GMT  
		Size: 7.7 KB (7682 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:60a28f448ff6c9050d3e4d6512ec5cd9b3a859e1e27f1a5bee990d88770c7535`  
		Last Modified: Tue, 28 Nov 2017 14:05:44 GMT  
		Size: 34.4 MB (34405004 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:4b67e72315b83296cda8741c28a139d4d9eacd8f749028ec9da49ccf41bdda71`  
		Last Modified: Tue, 28 Nov 2017 14:05:35 GMT  
		Size: 1.8 MB (1770325 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:7d2f0f8819b8d9b1530cbefd0bc483c3a45fe503aa051affacf1376aa99bb03e`  
		Last Modified: Tue, 28 Nov 2017 14:05:33 GMT  
		Size: 353.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:6d14b90e40a7b9088fb1f394738ae95610eda24614c7bb5855b41c17602e2281`  
		Last Modified: Tue, 28 Nov 2017 14:05:32 GMT  
		Size: 1.3 MB (1329402 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:004639602d02558ec34019d23172816c4a97bcdc1ad5d416817768849af61101`  
		Last Modified: Tue, 28 Nov 2017 14:05:32 GMT  
		Size: 135.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:74daf503626f0ef5eea259f12465793af8b78196b4ee3f41d1239753d67325f1`  
		Last Modified: Tue, 28 Nov 2017 14:08:26 GMT  
		Size: 47.0 MB (46970364 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:7e9168d83e18ca5ec239530e0cebcddcbf1240140bd22aca31e443de43460f4a`  
		Last Modified: Tue, 28 Nov 2017 14:08:09 GMT  
		Size: 940.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:4d352d0123561f8b8f934edd6bb35512a89716e0a48302e6cd74e66fd8997280`  
		Last Modified: Tue, 28 Nov 2017 14:08:10 GMT  
		Size: 785.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip

### `nextcloud:12-fpm` - linux; arm64 variant v8

```console
$ docker pull nextcloud@sha256:9a2e22287982fb068e9b4fcabf3f22441398d117ba1e0fa3a8f872a696f977ce
```

-	Docker Version: 17.06.2-ce
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **227.2 MB (227232632 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:51cf8f9f7b37536c8752fd8e768b08742aee00cb3e917868237386ca5d4b5b59`
-	Entrypoint: `["\/entrypoint.sh"]`
-	Default Command: `["php-fpm"]`

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
# Tue, 10 Oct 2017 03:19:11 GMT
ENV PHP_EXTRA_CONFIGURE_ARGS=--enable-fpm --with-fpm-user=www-data --with-fpm-group=www-data
# Tue, 10 Oct 2017 03:19:12 GMT
ENV PHP_CFLAGS=-fstack-protector-strong -fpic -fpie -O2
# Tue, 10 Oct 2017 03:19:12 GMT
ENV PHP_CPPFLAGS=-fstack-protector-strong -fpic -fpie -O2
# Tue, 10 Oct 2017 03:19:13 GMT
ENV PHP_LDFLAGS=-Wl,-O1 -Wl,--hash-style=both -pie
# Tue, 10 Oct 2017 03:19:13 GMT
ENV GPG_KEYS=A917B1ECDA84AEC2B568FED6F50ABC807BD5DCD0 528995BFEDFBA7191D46839EF9BA0ADA31CBD89E
# Tue, 28 Nov 2017 03:11:12 GMT
ENV PHP_VERSION=7.1.12
# Tue, 28 Nov 2017 03:11:12 GMT
ENV PHP_URL=https://secure.php.net/get/php-7.1.12.tar.xz/from/this/mirror PHP_ASC_URL=https://secure.php.net/get/php-7.1.12.tar.xz.asc/from/this/mirror
# Tue, 28 Nov 2017 03:11:13 GMT
ENV PHP_SHA256=a0118850774571b1f2d4e30b4fe7a4b958ca66f07d07d65ebdc789c54ba6eeb3 PHP_MD5=
# Tue, 28 Nov 2017 03:11:46 GMT
RUN set -xe; 		fetchDeps=' 		wget 	'; 	if ! command -v gpg > /dev/null; then 		fetchDeps="$fetchDeps 			dirmngr 			gnupg 		"; 	fi; 	apt-get update; 	apt-get install -y --no-install-recommends $fetchDeps; 	rm -rf /var/lib/apt/lists/*; 		mkdir -p /usr/src; 	cd /usr/src; 		wget -O php.tar.xz "$PHP_URL"; 		if [ -n "$PHP_SHA256" ]; then 		echo "$PHP_SHA256 *php.tar.xz" | sha256sum -c -; 	fi; 	if [ -n "$PHP_MD5" ]; then 		echo "$PHP_MD5 *php.tar.xz" | md5sum -c -; 	fi; 		if [ -n "$PHP_ASC_URL" ]; then 		wget -O php.tar.xz.asc "$PHP_ASC_URL"; 		export GNUPGHOME="$(mktemp -d)"; 		for key in $GPG_KEYS; do 			gpg --keyserver ha.pool.sks-keyservers.net --recv-keys "$key"; 		done; 		gpg --batch --verify php.tar.xz.asc php.tar.xz; 		rm -rf "$GNUPGHOME"; 	fi; 		apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false $fetchDeps
# Tue, 28 Nov 2017 03:11:46 GMT
COPY file:207c686e3fed4f71f8a7b245d8dcae9c9048d276a326d82b553c12a90af0c0ca in /usr/local/bin/ 
# Tue, 28 Nov 2017 03:18:36 GMT
RUN set -xe 	&& buildDeps=" 		$PHP_EXTRA_BUILD_DEPS 		libcurl4-openssl-dev 		libedit-dev 		libsqlite3-dev 		libssl-dev 		libxml2-dev 		zlib1g-dev 	" 	&& apt-get update && apt-get install -y $buildDeps --no-install-recommends && rm -rf /var/lib/apt/lists/* 		&& export CFLAGS="$PHP_CFLAGS" 		CPPFLAGS="$PHP_CPPFLAGS" 		LDFLAGS="$PHP_LDFLAGS" 	&& docker-php-source extract 	&& cd /usr/src/php 	&& gnuArch="$(dpkg-architecture --query DEB_BUILD_GNU_TYPE)" 	&& debMultiarch="$(dpkg-architecture --query DEB_BUILD_MULTIARCH)" 	&& if [ ! -d /usr/include/curl ]; then 		ln -sT "/usr/include/$debMultiarch/curl" /usr/local/include/curl; 	fi 	&& ./configure 		--build="$gnuArch" 		--with-config-file-path="$PHP_INI_DIR" 		--with-config-file-scan-dir="$PHP_INI_DIR/conf.d" 				--disable-cgi 				--enable-ftp 		--enable-mbstring 		--enable-mysqlnd 				--with-curl 		--with-libedit 		--with-openssl 		--with-zlib 				--with-pcre-regex=/usr 		--with-libdir="lib/$debMultiarch" 				$PHP_EXTRA_CONFIGURE_ARGS 	&& make -j "$(nproc)" 	&& make install 	&& { find /usr/local/bin /usr/local/sbin -type f -executable -exec strip --strip-all '{}' + || true; } 	&& make clean 	&& cd / 	&& docker-php-source delete 		&& apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false $buildDeps 		&& pecl update-channels 	&& rm -rf /tmp/pear ~/.pearrc
# Tue, 28 Nov 2017 03:18:37 GMT
COPY multi:3a3ce8aa3891c64454909e9f8257446a1817abe660b49a7baaa26f28bfdc444d in /usr/local/bin/ 
# Tue, 28 Nov 2017 03:18:38 GMT
ENTRYPOINT ["docker-php-entrypoint"]
# Tue, 28 Nov 2017 03:18:39 GMT
WORKDIR /var/www/html
# Tue, 28 Nov 2017 03:18:40 GMT
RUN set -ex 	&& cd /usr/local/etc 	&& if [ -d php-fpm.d ]; then 		sed 's!=NONE/!=!g' php-fpm.conf.default | tee php-fpm.conf > /dev/null; 		cp php-fpm.d/www.conf.default php-fpm.d/www.conf; 	else 		mkdir php-fpm.d; 		cp php-fpm.conf.default php-fpm.d/www.conf; 		{ 			echo '[global]'; 			echo 'include=etc/php-fpm.d/*.conf'; 		} | tee php-fpm.conf; 	fi 	&& { 		echo '[global]'; 		echo 'error_log = /proc/self/fd/2'; 		echo; 		echo '[www]'; 		echo '; if we send this to /proc/self/fd/1, it never appears'; 		echo 'access.log = /proc/self/fd/2'; 		echo; 		echo 'clear_env = no'; 		echo; 		echo '; Ensure worker stdout and stderr are sent to the main error log.'; 		echo 'catch_workers_output = yes'; 	} | tee php-fpm.d/docker.conf 	&& { 		echo '[global]'; 		echo 'daemonize = no'; 		echo; 		echo '[www]'; 		echo 'listen = [::]:9000'; 	} | tee php-fpm.d/zz-docker.conf
# Tue, 28 Nov 2017 03:18:41 GMT
EXPOSE 9000/tcp
# Tue, 28 Nov 2017 03:18:41 GMT
CMD ["php-fpm"]
# Tue, 28 Nov 2017 05:04:41 GMT
RUN apt-get update && apt-get install -y   rsync   bzip2   libcurl4-openssl-dev   libfreetype6-dev   libicu-dev   libjpeg-dev   libldap2-dev   libmcrypt-dev   libmemcached-dev   libpng12-dev   libpq-dev   libxml2-dev   && rm -rf /var/lib/apt/lists/*
# Tue, 28 Nov 2017 05:10:42 GMT
RUN debMultiarch="$(dpkg-architecture --query DEB_BUILD_MULTIARCH)"   && docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr   && docker-php-ext-configure ldap --with-libdir="lib/$debMultiarch"   && docker-php-ext-install gd exif intl mbstring mcrypt ldap mysqli opcache pdo_mysql pdo_pgsql pgsql zip pcntl
# Tue, 28 Nov 2017 05:10:43 GMT
RUN {   echo 'opcache.enable=1';   echo 'opcache.enable_cli=1';   echo 'opcache.interned_strings_buffer=8';   echo 'opcache.max_accelerated_files=10000';   echo 'opcache.memory_consumption=128';   echo 'opcache.save_comments=1';   echo 'opcache.revalidate_freq=1';   } > /usr/local/etc/php/conf.d/opcache-recommended.ini
# Tue, 28 Nov 2017 05:11:52 GMT
RUN set -ex  && pecl install APCu-5.1.8  && pecl install memcached-3.0.4  && pecl install redis-3.1.4  && docker-php-ext-enable apcu redis memcached
# Tue, 28 Nov 2017 05:14:15 GMT
ENV NEXTCLOUD_VERSION=12.0.3
# Tue, 28 Nov 2017 05:14:17 GMT
RUN chown -R www-data:root /var/www/html &&     chmod -R g=u /var/www/html
# Tue, 28 Nov 2017 05:14:17 GMT
VOLUME [/var/www/html]
# Tue, 28 Nov 2017 05:14:45 GMT
RUN curl -fsSL -o nextcloud.tar.bz2     "https://download.nextcloud.com/server/releases/nextcloud-${NEXTCLOUD_VERSION}.tar.bz2"  && curl -fsSL -o nextcloud.tar.bz2.asc     "https://download.nextcloud.com/server/releases/nextcloud-${NEXTCLOUD_VERSION}.tar.bz2.asc"  && export GNUPGHOME="$(mktemp -d)"  && gpg --keyserver ha.pool.sks-keyservers.net --recv-keys 28806A878AE423A28372792ED75899B9A724937A  && gpg --batch --verify nextcloud.tar.bz2.asc nextcloud.tar.bz2  && rm -r "$GNUPGHOME" nextcloud.tar.bz2.asc  && tar -xjf nextcloud.tar.bz2 -C /usr/src/  && rm nextcloud.tar.bz2  && rm -rf /usr/src/nextcloud/updater  && mkdir -p /usr/src/nextcloud/data  && mkdir -p /usr/src/nextcloud/custom_apps  && chmod +x /usr/src/nextcloud/occ
# Tue, 28 Nov 2017 05:14:47 GMT
COPY file:3fa42fa6664f03c90280a265050a78ef70bf32cd31864db727f5ee7e94828722 in /entrypoint.sh 
# Tue, 28 Nov 2017 05:14:48 GMT
COPY multi:55b88fcd3d6a1a8ca5ef52e5d2c9e27370c13cdc4c5e94d159f82a32979740ff in /usr/src/nextcloud/config/ 
# Tue, 28 Nov 2017 05:14:49 GMT
ENTRYPOINT ["/entrypoint.sh"]
# Tue, 28 Nov 2017 05:14:50 GMT
CMD ["php-fpm"]
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
	-	`sha256:02fe67703595b1d351a2c2e3dd847f31653372c04022a7517aef9d041dea1752`  
		Last Modified: Tue, 28 Nov 2017 04:03:38 GMT  
		Size: 12.5 MB (12530391 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:6e1c9de24e023767906ee2cd71c9fe41adedcc22f76d241526bc94e44635f788`  
		Last Modified: Tue, 28 Nov 2017 04:03:34 GMT  
		Size: 500.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:2eef472e96cf228172cd8e30c5bc942d5297bb422cb116f55c019aac70e828ad`  
		Last Modified: Tue, 28 Nov 2017 04:03:40 GMT  
		Size: 14.2 MB (14246108 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:7e8bedb4aaf6e9788fcf49e344bf6e2d79b79e4f80338748fcda057875e96140`  
		Last Modified: Tue, 28 Nov 2017 04:03:34 GMT  
		Size: 2.2 KB (2177 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:e4ef1a40903fbbaae223aba05e22bd5b9e8357843afdc5cd550d1a9bc213bcb2`  
		Last Modified: Tue, 28 Nov 2017 04:03:34 GMT  
		Size: 130.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:9f0fc090d1affadc994294a06b129b73126ef3b409c3fa8271198259bb28179b`  
		Last Modified: Tue, 28 Nov 2017 04:03:35 GMT  
		Size: 7.7 KB (7685 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:bec42ec8d41f902a9b07c1d7420408260891d4ad91aa50100e473735168e5d47`  
		Last Modified: Tue, 28 Nov 2017 05:18:02 GMT  
		Size: 35.7 MB (35740575 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:7bcb7477161e8bb4f4fa994b7e7751cbabe874a37af8a39d8ea81c8733cb9b88`  
		Last Modified: Tue, 28 Nov 2017 05:17:50 GMT  
		Size: 1.8 MB (1817123 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:7f622a1c954807ee856d5b1840781462760191434dcad6a9b3f22710e87df6c4`  
		Last Modified: Tue, 28 Nov 2017 05:17:49 GMT  
		Size: 355.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:d8e7b45e879ae94955d7674ebf7578cbd3282ae904e9f6a2bb2e90d56f6b3699`  
		Last Modified: Tue, 28 Nov 2017 05:17:48 GMT  
		Size: 1.4 MB (1373213 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:651dbc04b71c81cd635c212e0b04092082a8a93a3666e4f48b78aa8b97f719f1`  
		Last Modified: Tue, 28 Nov 2017 05:17:47 GMT  
		Size: 136.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:3a263583d308fc7f16f4093ba8cedb1326d7148494a5db8f90f0187f9e6a5987`  
		Last Modified: Tue, 28 Nov 2017 05:23:30 GMT  
		Size: 47.0 MB (46970322 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:3e504f9251b6b9e2877e0ce099a2d4881d4e9f32f5535449fc22409b45c9bdc7`  
		Last Modified: Tue, 28 Nov 2017 05:23:12 GMT  
		Size: 939.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:4100415052255ed059331e87e82ceceda56db2f93115d9e4b11f028ae2cab6ab`  
		Last Modified: Tue, 28 Nov 2017 05:23:12 GMT  
		Size: 785.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip

### `nextcloud:12-fpm` - linux; 386

```console
$ docker pull nextcloud@sha256:52f9bc99fd48a7196e02b847464798fddd4b49f29f3ec2f9b671cf7749331d51
```

-	Docker Version: 17.06.2-ce
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **253.6 MB (253579602 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:fab3c2abdbac27d5d841ce9c3cf09770415b2d6e83067ead7da294171f858f59`
-	Entrypoint: `["\/entrypoint.sh"]`
-	Default Command: `["php-fpm"]`

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
# Tue, 10 Oct 2017 01:03:42 GMT
ENV PHP_EXTRA_CONFIGURE_ARGS=--enable-fpm --with-fpm-user=www-data --with-fpm-group=www-data
# Tue, 10 Oct 2017 01:03:42 GMT
ENV PHP_CFLAGS=-fstack-protector-strong -fpic -fpie -O2
# Tue, 10 Oct 2017 01:03:42 GMT
ENV PHP_CPPFLAGS=-fstack-protector-strong -fpic -fpie -O2
# Tue, 10 Oct 2017 01:03:43 GMT
ENV PHP_LDFLAGS=-Wl,-O1 -Wl,--hash-style=both -pie
# Tue, 10 Oct 2017 01:03:43 GMT
ENV GPG_KEYS=A917B1ECDA84AEC2B568FED6F50ABC807BD5DCD0 528995BFEDFBA7191D46839EF9BA0ADA31CBD89E
# Tue, 28 Nov 2017 10:09:27 GMT
ENV PHP_VERSION=7.1.12
# Tue, 28 Nov 2017 10:09:27 GMT
ENV PHP_URL=https://secure.php.net/get/php-7.1.12.tar.xz/from/this/mirror PHP_ASC_URL=https://secure.php.net/get/php-7.1.12.tar.xz.asc/from/this/mirror
# Tue, 28 Nov 2017 10:09:27 GMT
ENV PHP_SHA256=a0118850774571b1f2d4e30b4fe7a4b958ca66f07d07d65ebdc789c54ba6eeb3 PHP_MD5=
# Tue, 28 Nov 2017 10:10:04 GMT
RUN set -xe; 		fetchDeps=' 		wget 	'; 	if ! command -v gpg > /dev/null; then 		fetchDeps="$fetchDeps 			dirmngr 			gnupg 		"; 	fi; 	apt-get update; 	apt-get install -y --no-install-recommends $fetchDeps; 	rm -rf /var/lib/apt/lists/*; 		mkdir -p /usr/src; 	cd /usr/src; 		wget -O php.tar.xz "$PHP_URL"; 		if [ -n "$PHP_SHA256" ]; then 		echo "$PHP_SHA256 *php.tar.xz" | sha256sum -c -; 	fi; 	if [ -n "$PHP_MD5" ]; then 		echo "$PHP_MD5 *php.tar.xz" | md5sum -c -; 	fi; 		if [ -n "$PHP_ASC_URL" ]; then 		wget -O php.tar.xz.asc "$PHP_ASC_URL"; 		export GNUPGHOME="$(mktemp -d)"; 		for key in $GPG_KEYS; do 			gpg --keyserver ha.pool.sks-keyservers.net --recv-keys "$key"; 		done; 		gpg --batch --verify php.tar.xz.asc php.tar.xz; 		rm -rf "$GNUPGHOME"; 	fi; 		apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false $fetchDeps
# Tue, 28 Nov 2017 10:10:04 GMT
COPY file:207c686e3fed4f71f8a7b245d8dcae9c9048d276a326d82b553c12a90af0c0ca in /usr/local/bin/ 
# Tue, 28 Nov 2017 10:15:13 GMT
RUN set -xe 	&& buildDeps=" 		$PHP_EXTRA_BUILD_DEPS 		libcurl4-openssl-dev 		libedit-dev 		libsqlite3-dev 		libssl-dev 		libxml2-dev 		zlib1g-dev 	" 	&& apt-get update && apt-get install -y $buildDeps --no-install-recommends && rm -rf /var/lib/apt/lists/* 		&& export CFLAGS="$PHP_CFLAGS" 		CPPFLAGS="$PHP_CPPFLAGS" 		LDFLAGS="$PHP_LDFLAGS" 	&& docker-php-source extract 	&& cd /usr/src/php 	&& gnuArch="$(dpkg-architecture --query DEB_BUILD_GNU_TYPE)" 	&& debMultiarch="$(dpkg-architecture --query DEB_BUILD_MULTIARCH)" 	&& if [ ! -d /usr/include/curl ]; then 		ln -sT "/usr/include/$debMultiarch/curl" /usr/local/include/curl; 	fi 	&& ./configure 		--build="$gnuArch" 		--with-config-file-path="$PHP_INI_DIR" 		--with-config-file-scan-dir="$PHP_INI_DIR/conf.d" 				--disable-cgi 				--enable-ftp 		--enable-mbstring 		--enable-mysqlnd 				--with-curl 		--with-libedit 		--with-openssl 		--with-zlib 				--with-pcre-regex=/usr 		--with-libdir="lib/$debMultiarch" 				$PHP_EXTRA_CONFIGURE_ARGS 	&& make -j "$(nproc)" 	&& make install 	&& { find /usr/local/bin /usr/local/sbin -type f -executable -exec strip --strip-all '{}' + || true; } 	&& make clean 	&& cd / 	&& docker-php-source delete 		&& apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false $buildDeps 		&& pecl update-channels 	&& rm -rf /tmp/pear ~/.pearrc
# Tue, 28 Nov 2017 10:16:47 GMT
COPY multi:3a3ce8aa3891c64454909e9f8257446a1817abe660b49a7baaa26f28bfdc444d in /usr/local/bin/ 
# Tue, 28 Nov 2017 10:16:47 GMT
ENTRYPOINT ["docker-php-entrypoint"]
# Tue, 28 Nov 2017 10:16:48 GMT
WORKDIR /var/www/html
# Tue, 28 Nov 2017 10:16:48 GMT
RUN set -ex 	&& cd /usr/local/etc 	&& if [ -d php-fpm.d ]; then 		sed 's!=NONE/!=!g' php-fpm.conf.default | tee php-fpm.conf > /dev/null; 		cp php-fpm.d/www.conf.default php-fpm.d/www.conf; 	else 		mkdir php-fpm.d; 		cp php-fpm.conf.default php-fpm.d/www.conf; 		{ 			echo '[global]'; 			echo 'include=etc/php-fpm.d/*.conf'; 		} | tee php-fpm.conf; 	fi 	&& { 		echo '[global]'; 		echo 'error_log = /proc/self/fd/2'; 		echo; 		echo '[www]'; 		echo '; if we send this to /proc/self/fd/1, it never appears'; 		echo 'access.log = /proc/self/fd/2'; 		echo; 		echo 'clear_env = no'; 		echo; 		echo '; Ensure worker stdout and stderr are sent to the main error log.'; 		echo 'catch_workers_output = yes'; 	} | tee php-fpm.d/docker.conf 	&& { 		echo '[global]'; 		echo 'daemonize = no'; 		echo; 		echo '[www]'; 		echo 'listen = [::]:9000'; 	} | tee php-fpm.d/zz-docker.conf
# Tue, 28 Nov 2017 10:16:48 GMT
EXPOSE 9000/tcp
# Tue, 28 Nov 2017 10:16:49 GMT
CMD ["php-fpm"]
# Tue, 28 Nov 2017 12:17:49 GMT
RUN apt-get update && apt-get install -y   rsync   bzip2   libcurl4-openssl-dev   libfreetype6-dev   libicu-dev   libjpeg-dev   libldap2-dev   libmcrypt-dev   libmemcached-dev   libpng12-dev   libpq-dev   libxml2-dev   && rm -rf /var/lib/apt/lists/*
# Tue, 28 Nov 2017 12:26:31 GMT
RUN debMultiarch="$(dpkg-architecture --query DEB_BUILD_MULTIARCH)"   && docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr   && docker-php-ext-configure ldap --with-libdir="lib/$debMultiarch"   && docker-php-ext-install gd exif intl mbstring mcrypt ldap mysqli opcache pdo_mysql pdo_pgsql pgsql zip pcntl
# Tue, 28 Nov 2017 12:31:31 GMT
RUN {   echo 'opcache.enable=1';   echo 'opcache.enable_cli=1';   echo 'opcache.interned_strings_buffer=8';   echo 'opcache.max_accelerated_files=10000';   echo 'opcache.memory_consumption=128';   echo 'opcache.save_comments=1';   echo 'opcache.revalidate_freq=1';   } > /usr/local/etc/php/conf.d/opcache-recommended.ini
# Tue, 28 Nov 2017 12:32:11 GMT
RUN set -ex  && pecl install APCu-5.1.8  && pecl install memcached-3.0.4  && pecl install redis-3.1.4  && docker-php-ext-enable apcu redis memcached
# Tue, 28 Nov 2017 12:39:45 GMT
ENV NEXTCLOUD_VERSION=12.0.3
# Tue, 28 Nov 2017 12:39:46 GMT
RUN chown -R www-data:root /var/www/html &&     chmod -R g=u /var/www/html
# Tue, 28 Nov 2017 12:39:46 GMT
VOLUME [/var/www/html]
# Tue, 28 Nov 2017 12:40:06 GMT
RUN curl -fsSL -o nextcloud.tar.bz2     "https://download.nextcloud.com/server/releases/nextcloud-${NEXTCLOUD_VERSION}.tar.bz2"  && curl -fsSL -o nextcloud.tar.bz2.asc     "https://download.nextcloud.com/server/releases/nextcloud-${NEXTCLOUD_VERSION}.tar.bz2.asc"  && export GNUPGHOME="$(mktemp -d)"  && gpg --keyserver ha.pool.sks-keyservers.net --recv-keys 28806A878AE423A28372792ED75899B9A724937A  && gpg --batch --verify nextcloud.tar.bz2.asc nextcloud.tar.bz2  && rm -r "$GNUPGHOME" nextcloud.tar.bz2.asc  && tar -xjf nextcloud.tar.bz2 -C /usr/src/  && rm nextcloud.tar.bz2  && rm -rf /usr/src/nextcloud/updater  && mkdir -p /usr/src/nextcloud/data  && mkdir -p /usr/src/nextcloud/custom_apps  && chmod +x /usr/src/nextcloud/occ
# Tue, 28 Nov 2017 12:40:10 GMT
COPY file:3fa42fa6664f03c90280a265050a78ef70bf32cd31864db727f5ee7e94828722 in /entrypoint.sh 
# Tue, 28 Nov 2017 12:40:10 GMT
COPY multi:55b88fcd3d6a1a8ca5ef52e5d2c9e27370c13cdc4c5e94d159f82a32979740ff in /usr/src/nextcloud/config/ 
# Tue, 28 Nov 2017 12:40:11 GMT
ENTRYPOINT ["/entrypoint.sh"]
# Tue, 28 Nov 2017 12:40:11 GMT
CMD ["php-fpm"]
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
	-	`sha256:15d3b655ef146938f218e990251f380acc0e599433c9747f383df39945ce9785`  
		Last Modified: Tue, 28 Nov 2017 11:21:39 GMT  
		Size: 12.5 MB (12531594 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:051078e6b0849f350221ab52ace5bedc885972b36ae76cad55aac46f6b37e38d`  
		Last Modified: Tue, 28 Nov 2017 11:21:34 GMT  
		Size: 501.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:c5d4093ac4088728aa9bf02ac530ebdfd73eac8de55d57ce92c0de5b6b8a3e59`  
		Last Modified: Tue, 28 Nov 2017 11:21:42 GMT  
		Size: 17.8 MB (17832816 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:be828b1d7165992419e19eee1c9f268ee6106e7152e4c13836807486effbfa9f`  
		Last Modified: Tue, 28 Nov 2017 11:21:34 GMT  
		Size: 2.2 KB (2177 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:e5e4fb8891edc4015821292f1abf37b84e0e11a8594acfa67c66a0de5f80ae3e`  
		Last Modified: Tue, 28 Nov 2017 11:21:34 GMT  
		Size: 130.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:ca5da6ccaa91b47442003767d1dafd6a13b82536fb0b5e3478d1b6a182c74018`  
		Last Modified: Tue, 28 Nov 2017 11:21:35 GMT  
		Size: 7.7 KB (7684 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:64bed9f464dfb6143f457c0ee797fe084e06a5e49a2369702b6e347f7bd93ef2`  
		Last Modified: Tue, 28 Nov 2017 12:49:01 GMT  
		Size: 36.3 MB (36346253 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:4e6c0aa122d5308137854ca17b8b92c269f76b0fbc6acd1b408f12f230012fbd`  
		Last Modified: Tue, 28 Nov 2017 12:48:47 GMT  
		Size: 1.9 MB (1939982 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:46ecf85076bf01c686973b340a0cb8734d09be428266cd98086127876508c930`  
		Last Modified: Tue, 28 Nov 2017 12:48:47 GMT  
		Size: 356.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:38769644dd090a3b6a6e10b934917b0b63be30b849c1da47066699b97cdda3e9`  
		Last Modified: Tue, 28 Nov 2017 12:48:48 GMT  
		Size: 1.3 MB (1284975 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:f1426c13d03ede748305a4030af774dceca2e1c374704c0d09b662987ce7c5d0`  
		Last Modified: Tue, 28 Nov 2017 12:48:47 GMT  
		Size: 135.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:6d9b73aaec12d775ea71b32acbdd9fb7e9aa3920967f4e903bd1ae248fd8a28b`  
		Last Modified: Tue, 28 Nov 2017 12:59:54 GMT  
		Size: 47.0 MB (46970364 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:b520113d3ac4281cf6396c5ebcfec7dc3560f6541e4d98466f6dca1e8428986f`  
		Last Modified: Tue, 28 Nov 2017 12:58:59 GMT  
		Size: 939.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:19a56c1f63046376ef90878af975af3e5890cfb4e8ece9f11c787729d3a4fd24`  
		Last Modified: Tue, 28 Nov 2017 12:58:58 GMT  
		Size: 786.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip

### `nextcloud:12-fpm` - linux; ppc64le

```console
$ docker pull nextcloud@sha256:65aa37b69c7ba74be80226c8f4f13a0c2e1e747cb0de630e1574bb104240b40d
```

-	Docker Version: 17.06.2-ce
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **236.3 MB (236299515 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:a815ea27d3feb5ff4c700fd0f43f12598b10c1ed2c26cdf0ed4ba18ec9a04dde`
-	Entrypoint: `["\/entrypoint.sh"]`
-	Default Command: `["php-fpm"]`

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
# Tue, 10 Oct 2017 05:24:20 GMT
ENV PHP_EXTRA_CONFIGURE_ARGS=--enable-fpm --with-fpm-user=www-data --with-fpm-group=www-data
# Tue, 10 Oct 2017 05:24:22 GMT
ENV PHP_CFLAGS=-fstack-protector-strong -fpic -fpie -O2
# Tue, 10 Oct 2017 05:24:25 GMT
ENV PHP_CPPFLAGS=-fstack-protector-strong -fpic -fpie -O2
# Tue, 10 Oct 2017 05:24:28 GMT
ENV PHP_LDFLAGS=-Wl,-O1 -Wl,--hash-style=both -pie
# Tue, 10 Oct 2017 05:24:31 GMT
ENV GPG_KEYS=A917B1ECDA84AEC2B568FED6F50ABC807BD5DCD0 528995BFEDFBA7191D46839EF9BA0ADA31CBD89E
# Tue, 28 Nov 2017 09:59:43 GMT
ENV PHP_VERSION=7.1.12
# Tue, 28 Nov 2017 09:59:44 GMT
ENV PHP_URL=https://secure.php.net/get/php-7.1.12.tar.xz/from/this/mirror PHP_ASC_URL=https://secure.php.net/get/php-7.1.12.tar.xz.asc/from/this/mirror
# Tue, 28 Nov 2017 09:59:45 GMT
ENV PHP_SHA256=a0118850774571b1f2d4e30b4fe7a4b958ca66f07d07d65ebdc789c54ba6eeb3 PHP_MD5=
# Tue, 28 Nov 2017 10:00:21 GMT
RUN set -xe; 		fetchDeps=' 		wget 	'; 	if ! command -v gpg > /dev/null; then 		fetchDeps="$fetchDeps 			dirmngr 			gnupg 		"; 	fi; 	apt-get update; 	apt-get install -y --no-install-recommends $fetchDeps; 	rm -rf /var/lib/apt/lists/*; 		mkdir -p /usr/src; 	cd /usr/src; 		wget -O php.tar.xz "$PHP_URL"; 		if [ -n "$PHP_SHA256" ]; then 		echo "$PHP_SHA256 *php.tar.xz" | sha256sum -c -; 	fi; 	if [ -n "$PHP_MD5" ]; then 		echo "$PHP_MD5 *php.tar.xz" | md5sum -c -; 	fi; 		if [ -n "$PHP_ASC_URL" ]; then 		wget -O php.tar.xz.asc "$PHP_ASC_URL"; 		export GNUPGHOME="$(mktemp -d)"; 		for key in $GPG_KEYS; do 			gpg --keyserver ha.pool.sks-keyservers.net --recv-keys "$key"; 		done; 		gpg --batch --verify php.tar.xz.asc php.tar.xz; 		rm -rf "$GNUPGHOME"; 	fi; 		apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false $fetchDeps
# Tue, 28 Nov 2017 10:00:22 GMT
COPY file:207c686e3fed4f71f8a7b245d8dcae9c9048d276a326d82b553c12a90af0c0ca in /usr/local/bin/ 
# Tue, 28 Nov 2017 10:04:08 GMT
RUN set -xe 	&& buildDeps=" 		$PHP_EXTRA_BUILD_DEPS 		libcurl4-openssl-dev 		libedit-dev 		libsqlite3-dev 		libssl-dev 		libxml2-dev 		zlib1g-dev 	" 	&& apt-get update && apt-get install -y $buildDeps --no-install-recommends && rm -rf /var/lib/apt/lists/* 		&& export CFLAGS="$PHP_CFLAGS" 		CPPFLAGS="$PHP_CPPFLAGS" 		LDFLAGS="$PHP_LDFLAGS" 	&& docker-php-source extract 	&& cd /usr/src/php 	&& gnuArch="$(dpkg-architecture --query DEB_BUILD_GNU_TYPE)" 	&& debMultiarch="$(dpkg-architecture --query DEB_BUILD_MULTIARCH)" 	&& if [ ! -d /usr/include/curl ]; then 		ln -sT "/usr/include/$debMultiarch/curl" /usr/local/include/curl; 	fi 	&& ./configure 		--build="$gnuArch" 		--with-config-file-path="$PHP_INI_DIR" 		--with-config-file-scan-dir="$PHP_INI_DIR/conf.d" 				--disable-cgi 				--enable-ftp 		--enable-mbstring 		--enable-mysqlnd 				--with-curl 		--with-libedit 		--with-openssl 		--with-zlib 				--with-pcre-regex=/usr 		--with-libdir="lib/$debMultiarch" 				$PHP_EXTRA_CONFIGURE_ARGS 	&& make -j "$(nproc)" 	&& make install 	&& { find /usr/local/bin /usr/local/sbin -type f -executable -exec strip --strip-all '{}' + || true; } 	&& make clean 	&& cd / 	&& docker-php-source delete 		&& apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false $buildDeps 		&& pecl update-channels 	&& rm -rf /tmp/pear ~/.pearrc
# Tue, 28 Nov 2017 10:04:09 GMT
COPY multi:3a3ce8aa3891c64454909e9f8257446a1817abe660b49a7baaa26f28bfdc444d in /usr/local/bin/ 
# Tue, 28 Nov 2017 10:04:11 GMT
ENTRYPOINT ["docker-php-entrypoint"]
# Tue, 28 Nov 2017 10:04:12 GMT
WORKDIR /var/www/html
# Tue, 28 Nov 2017 10:04:15 GMT
RUN set -ex 	&& cd /usr/local/etc 	&& if [ -d php-fpm.d ]; then 		sed 's!=NONE/!=!g' php-fpm.conf.default | tee php-fpm.conf > /dev/null; 		cp php-fpm.d/www.conf.default php-fpm.d/www.conf; 	else 		mkdir php-fpm.d; 		cp php-fpm.conf.default php-fpm.d/www.conf; 		{ 			echo '[global]'; 			echo 'include=etc/php-fpm.d/*.conf'; 		} | tee php-fpm.conf; 	fi 	&& { 		echo '[global]'; 		echo 'error_log = /proc/self/fd/2'; 		echo; 		echo '[www]'; 		echo '; if we send this to /proc/self/fd/1, it never appears'; 		echo 'access.log = /proc/self/fd/2'; 		echo; 		echo 'clear_env = no'; 		echo; 		echo '; Ensure worker stdout and stderr are sent to the main error log.'; 		echo 'catch_workers_output = yes'; 	} | tee php-fpm.d/docker.conf 	&& { 		echo '[global]'; 		echo 'daemonize = no'; 		echo; 		echo '[www]'; 		echo 'listen = [::]:9000'; 	} | tee php-fpm.d/zz-docker.conf
# Tue, 28 Nov 2017 10:04:17 GMT
EXPOSE 9000/tcp
# Tue, 28 Nov 2017 10:04:19 GMT
CMD ["php-fpm"]
# Tue, 28 Nov 2017 11:14:07 GMT
RUN apt-get update && apt-get install -y   rsync   bzip2   libcurl4-openssl-dev   libfreetype6-dev   libicu-dev   libjpeg-dev   libldap2-dev   libmcrypt-dev   libmemcached-dev   libpng12-dev   libpq-dev   libxml2-dev   && rm -rf /var/lib/apt/lists/*
# Tue, 28 Nov 2017 11:17:29 GMT
RUN debMultiarch="$(dpkg-architecture --query DEB_BUILD_MULTIARCH)"   && docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr   && docker-php-ext-configure ldap --with-libdir="lib/$debMultiarch"   && docker-php-ext-install gd exif intl mbstring mcrypt ldap mysqli opcache pdo_mysql pdo_pgsql pgsql zip pcntl
# Tue, 28 Nov 2017 11:17:33 GMT
RUN {   echo 'opcache.enable=1';   echo 'opcache.enable_cli=1';   echo 'opcache.interned_strings_buffer=8';   echo 'opcache.max_accelerated_files=10000';   echo 'opcache.memory_consumption=128';   echo 'opcache.save_comments=1';   echo 'opcache.revalidate_freq=1';   } > /usr/local/etc/php/conf.d/opcache-recommended.ini
# Tue, 28 Nov 2017 11:18:17 GMT
RUN set -ex  && pecl install APCu-5.1.8  && pecl install memcached-3.0.4  && pecl install redis-3.1.4  && docker-php-ext-enable apcu redis memcached
# Tue, 28 Nov 2017 11:20:19 GMT
ENV NEXTCLOUD_VERSION=12.0.3
# Tue, 28 Nov 2017 11:20:22 GMT
RUN chown -R www-data:root /var/www/html &&     chmod -R g=u /var/www/html
# Tue, 28 Nov 2017 11:20:23 GMT
VOLUME [/var/www/html]
# Tue, 28 Nov 2017 11:20:58 GMT
RUN curl -fsSL -o nextcloud.tar.bz2     "https://download.nextcloud.com/server/releases/nextcloud-${NEXTCLOUD_VERSION}.tar.bz2"  && curl -fsSL -o nextcloud.tar.bz2.asc     "https://download.nextcloud.com/server/releases/nextcloud-${NEXTCLOUD_VERSION}.tar.bz2.asc"  && export GNUPGHOME="$(mktemp -d)"  && gpg --keyserver ha.pool.sks-keyservers.net --recv-keys 28806A878AE423A28372792ED75899B9A724937A  && gpg --batch --verify nextcloud.tar.bz2.asc nextcloud.tar.bz2  && rm -r "$GNUPGHOME" nextcloud.tar.bz2.asc  && tar -xjf nextcloud.tar.bz2 -C /usr/src/  && rm nextcloud.tar.bz2  && rm -rf /usr/src/nextcloud/updater  && mkdir -p /usr/src/nextcloud/data  && mkdir -p /usr/src/nextcloud/custom_apps  && chmod +x /usr/src/nextcloud/occ
# Tue, 28 Nov 2017 11:21:01 GMT
COPY file:3fa42fa6664f03c90280a265050a78ef70bf32cd31864db727f5ee7e94828722 in /entrypoint.sh 
# Tue, 28 Nov 2017 11:21:03 GMT
COPY multi:55b88fcd3d6a1a8ca5ef52e5d2c9e27370c13cdc4c5e94d159f82a32979740ff in /usr/src/nextcloud/config/ 
# Tue, 28 Nov 2017 11:21:10 GMT
ENTRYPOINT ["/entrypoint.sh"]
# Tue, 28 Nov 2017 11:21:14 GMT
CMD ["php-fpm"]
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
	-	`sha256:e2b7ee8b44ac6ca73fb1500445f01b9ca76f025dee12c98d53f585f4f04b186d`  
		Last Modified: Tue, 28 Nov 2017 10:31:31 GMT  
		Size: 12.5 MB (12531151 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:8c538b15e1d9621d8043266c32f9c4a539f6bd6dc308b008da95c37594ac726b`  
		Last Modified: Tue, 28 Nov 2017 10:31:27 GMT  
		Size: 499.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:652ebbd80b590fbe13ec7dc1f4c0aba2923e19c6f0b20a9f509bb24bd8981a52`  
		Last Modified: Tue, 28 Nov 2017 10:31:32 GMT  
		Size: 15.1 MB (15132103 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:6387f3e117c15eff4253e3b75f54e436b6ca9231d95a001fb80c1d22f28e73fe`  
		Last Modified: Tue, 28 Nov 2017 10:31:28 GMT  
		Size: 2.2 KB (2174 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:87e6d607ce7fd1eb38321040e7e00ffc63790b38351c30f47b478fc81bd5c9c1`  
		Last Modified: Tue, 28 Nov 2017 10:31:27 GMT  
		Size: 160.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:f5fb9de3a6010fbacb9f89487f7623c7bb0dc9f022ee02b7f6733a236dd72c34`  
		Last Modified: Tue, 28 Nov 2017 10:31:28 GMT  
		Size: 7.7 KB (7683 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:262858be8607e7c6f9654f6276017483448269131c44ca1e41bbb52cd8f54f5b`  
		Last Modified: Tue, 28 Nov 2017 11:22:45 GMT  
		Size: 36.5 MB (36533968 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:2315d2356ca05df95fa9401d6324c3eddf68546aac0e33b5a7c53cdfc0eea60a`  
		Last Modified: Tue, 28 Nov 2017 11:22:34 GMT  
		Size: 1.9 MB (1927355 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:5c964dc4ca3f0bf8599215d8de43dc9508e61355f5f155adb70c100616847902`  
		Last Modified: Tue, 28 Nov 2017 11:22:33 GMT  
		Size: 354.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:706ac3b87637fc5da9c6ade87bc60a738ce97f1b3dd9a52d2de381cae1d361f9`  
		Last Modified: Tue, 28 Nov 2017 11:22:31 GMT  
		Size: 1.4 MB (1402094 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:36dd7511d22b328c2d6e63781db0b5c5a80f302e4c8704ab11c87c14584928ad`  
		Last Modified: Tue, 28 Nov 2017 11:22:30 GMT  
		Size: 135.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:9441077103af0a8b451a2467d7dfa5393c28f8e680f26501a5f9d9a267349406`  
		Last Modified: Tue, 28 Nov 2017 11:24:18 GMT  
		Size: 47.0 MB (46970371 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:a27a27b114b9bb59bbfaa2ae69e01a31107a9e045e736c34914c61507d84998a`  
		Last Modified: Tue, 28 Nov 2017 11:24:08 GMT  
		Size: 939.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:14fabd062608fe075491c8845b363c8f0d7d3b23fc8c1c4d40fde61c47d265e1`  
		Last Modified: Tue, 28 Nov 2017 11:24:07 GMT  
		Size: 786.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip

### `nextcloud:12-fpm` - linux; s390x

```console
$ docker pull nextcloud@sha256:71a066efeebbb7b5a5f728a156c586577ccdc4cdcc503a2ccdb449d48c46b244
```

-	Docker Version: 17.06.1-ce
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **232.3 MB (232299513 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:de2879ea860adef42c915395e8b5eb861f60b047390806d4c6e82f5f7d01f0e5`
-	Entrypoint: `["\/entrypoint.sh"]`
-	Default Command: `["php-fpm"]`

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
# Mon, 09 Oct 2017 23:02:28 GMT
ENV PHP_EXTRA_CONFIGURE_ARGS=--enable-fpm --with-fpm-user=www-data --with-fpm-group=www-data
# Mon, 09 Oct 2017 23:02:28 GMT
ENV PHP_CFLAGS=-fstack-protector-strong -fpic -fpie -O2
# Mon, 09 Oct 2017 23:02:28 GMT
ENV PHP_CPPFLAGS=-fstack-protector-strong -fpic -fpie -O2
# Mon, 09 Oct 2017 23:02:28 GMT
ENV PHP_LDFLAGS=-Wl,-O1 -Wl,--hash-style=both -pie
# Mon, 09 Oct 2017 23:02:28 GMT
ENV GPG_KEYS=A917B1ECDA84AEC2B568FED6F50ABC807BD5DCD0 528995BFEDFBA7191D46839EF9BA0ADA31CBD89E
# Tue, 28 Nov 2017 18:34:00 GMT
ENV PHP_VERSION=7.1.12
# Tue, 28 Nov 2017 18:34:00 GMT
ENV PHP_URL=https://secure.php.net/get/php-7.1.12.tar.xz/from/this/mirror PHP_ASC_URL=https://secure.php.net/get/php-7.1.12.tar.xz.asc/from/this/mirror
# Tue, 28 Nov 2017 18:34:00 GMT
ENV PHP_SHA256=a0118850774571b1f2d4e30b4fe7a4b958ca66f07d07d65ebdc789c54ba6eeb3 PHP_MD5=
# Tue, 28 Nov 2017 18:34:15 GMT
RUN set -xe; 		fetchDeps=' 		wget 	'; 	if ! command -v gpg > /dev/null; then 		fetchDeps="$fetchDeps 			dirmngr 			gnupg 		"; 	fi; 	apt-get update; 	apt-get install -y --no-install-recommends $fetchDeps; 	rm -rf /var/lib/apt/lists/*; 		mkdir -p /usr/src; 	cd /usr/src; 		wget -O php.tar.xz "$PHP_URL"; 		if [ -n "$PHP_SHA256" ]; then 		echo "$PHP_SHA256 *php.tar.xz" | sha256sum -c -; 	fi; 	if [ -n "$PHP_MD5" ]; then 		echo "$PHP_MD5 *php.tar.xz" | md5sum -c -; 	fi; 		if [ -n "$PHP_ASC_URL" ]; then 		wget -O php.tar.xz.asc "$PHP_ASC_URL"; 		export GNUPGHOME="$(mktemp -d)"; 		for key in $GPG_KEYS; do 			gpg --keyserver ha.pool.sks-keyservers.net --recv-keys "$key"; 		done; 		gpg --batch --verify php.tar.xz.asc php.tar.xz; 		rm -rf "$GNUPGHOME"; 	fi; 		apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false $fetchDeps
# Tue, 28 Nov 2017 18:34:15 GMT
COPY file:207c686e3fed4f71f8a7b245d8dcae9c9048d276a326d82b553c12a90af0c0ca in /usr/local/bin/ 
# Tue, 28 Nov 2017 18:37:14 GMT
RUN set -xe 	&& buildDeps=" 		$PHP_EXTRA_BUILD_DEPS 		libcurl4-openssl-dev 		libedit-dev 		libsqlite3-dev 		libssl-dev 		libxml2-dev 		zlib1g-dev 	" 	&& apt-get update && apt-get install -y $buildDeps --no-install-recommends && rm -rf /var/lib/apt/lists/* 		&& export CFLAGS="$PHP_CFLAGS" 		CPPFLAGS="$PHP_CPPFLAGS" 		LDFLAGS="$PHP_LDFLAGS" 	&& docker-php-source extract 	&& cd /usr/src/php 	&& gnuArch="$(dpkg-architecture --query DEB_BUILD_GNU_TYPE)" 	&& debMultiarch="$(dpkg-architecture --query DEB_BUILD_MULTIARCH)" 	&& if [ ! -d /usr/include/curl ]; then 		ln -sT "/usr/include/$debMultiarch/curl" /usr/local/include/curl; 	fi 	&& ./configure 		--build="$gnuArch" 		--with-config-file-path="$PHP_INI_DIR" 		--with-config-file-scan-dir="$PHP_INI_DIR/conf.d" 				--disable-cgi 				--enable-ftp 		--enable-mbstring 		--enable-mysqlnd 				--with-curl 		--with-libedit 		--with-openssl 		--with-zlib 				--with-pcre-regex=/usr 		--with-libdir="lib/$debMultiarch" 				$PHP_EXTRA_CONFIGURE_ARGS 	&& make -j "$(nproc)" 	&& make install 	&& { find /usr/local/bin /usr/local/sbin -type f -executable -exec strip --strip-all '{}' + || true; } 	&& make clean 	&& cd / 	&& docker-php-source delete 		&& apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false $buildDeps 		&& pecl update-channels 	&& rm -rf /tmp/pear ~/.pearrc
# Tue, 28 Nov 2017 18:37:15 GMT
COPY multi:3a3ce8aa3891c64454909e9f8257446a1817abe660b49a7baaa26f28bfdc444d in /usr/local/bin/ 
# Tue, 28 Nov 2017 18:37:15 GMT
ENTRYPOINT ["docker-php-entrypoint"]
# Tue, 28 Nov 2017 18:37:15 GMT
WORKDIR /var/www/html
# Tue, 28 Nov 2017 18:37:16 GMT
RUN set -ex 	&& cd /usr/local/etc 	&& if [ -d php-fpm.d ]; then 		sed 's!=NONE/!=!g' php-fpm.conf.default | tee php-fpm.conf > /dev/null; 		cp php-fpm.d/www.conf.default php-fpm.d/www.conf; 	else 		mkdir php-fpm.d; 		cp php-fpm.conf.default php-fpm.d/www.conf; 		{ 			echo '[global]'; 			echo 'include=etc/php-fpm.d/*.conf'; 		} | tee php-fpm.conf; 	fi 	&& { 		echo '[global]'; 		echo 'error_log = /proc/self/fd/2'; 		echo; 		echo '[www]'; 		echo '; if we send this to /proc/self/fd/1, it never appears'; 		echo 'access.log = /proc/self/fd/2'; 		echo; 		echo 'clear_env = no'; 		echo; 		echo '; Ensure worker stdout and stderr are sent to the main error log.'; 		echo 'catch_workers_output = yes'; 	} | tee php-fpm.d/docker.conf 	&& { 		echo '[global]'; 		echo 'daemonize = no'; 		echo; 		echo '[www]'; 		echo 'listen = [::]:9000'; 	} | tee php-fpm.d/zz-docker.conf
# Tue, 28 Nov 2017 18:37:16 GMT
EXPOSE 9000/tcp
# Tue, 28 Nov 2017 18:37:16 GMT
CMD ["php-fpm"]
# Tue, 28 Nov 2017 19:18:14 GMT
RUN apt-get update && apt-get install -y   rsync   bzip2   libcurl4-openssl-dev   libfreetype6-dev   libicu-dev   libjpeg-dev   libldap2-dev   libmcrypt-dev   libmemcached-dev   libpng12-dev   libpq-dev   libxml2-dev   && rm -rf /var/lib/apt/lists/*
# Tue, 28 Nov 2017 19:20:21 GMT
RUN debMultiarch="$(dpkg-architecture --query DEB_BUILD_MULTIARCH)"   && docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr   && docker-php-ext-configure ldap --with-libdir="lib/$debMultiarch"   && docker-php-ext-install gd exif intl mbstring mcrypt ldap mysqli opcache pdo_mysql pdo_pgsql pgsql zip pcntl
# Tue, 28 Nov 2017 19:20:23 GMT
RUN {   echo 'opcache.enable=1';   echo 'opcache.enable_cli=1';   echo 'opcache.interned_strings_buffer=8';   echo 'opcache.max_accelerated_files=10000';   echo 'opcache.memory_consumption=128';   echo 'opcache.save_comments=1';   echo 'opcache.revalidate_freq=1';   } > /usr/local/etc/php/conf.d/opcache-recommended.ini
# Tue, 28 Nov 2017 19:20:47 GMT
RUN set -ex  && pecl install APCu-5.1.8  && pecl install memcached-3.0.4  && pecl install redis-3.1.4  && docker-php-ext-enable apcu redis memcached
# Tue, 28 Nov 2017 19:22:16 GMT
ENV NEXTCLOUD_VERSION=12.0.3
# Tue, 28 Nov 2017 19:22:17 GMT
RUN chown -R www-data:root /var/www/html &&     chmod -R g=u /var/www/html
# Tue, 28 Nov 2017 19:22:17 GMT
VOLUME [/var/www/html]
# Tue, 28 Nov 2017 19:22:32 GMT
RUN curl -fsSL -o nextcloud.tar.bz2     "https://download.nextcloud.com/server/releases/nextcloud-${NEXTCLOUD_VERSION}.tar.bz2"  && curl -fsSL -o nextcloud.tar.bz2.asc     "https://download.nextcloud.com/server/releases/nextcloud-${NEXTCLOUD_VERSION}.tar.bz2.asc"  && export GNUPGHOME="$(mktemp -d)"  && gpg --keyserver ha.pool.sks-keyservers.net --recv-keys 28806A878AE423A28372792ED75899B9A724937A  && gpg --batch --verify nextcloud.tar.bz2.asc nextcloud.tar.bz2  && rm -r "$GNUPGHOME" nextcloud.tar.bz2.asc  && tar -xjf nextcloud.tar.bz2 -C /usr/src/  && rm nextcloud.tar.bz2  && rm -rf /usr/src/nextcloud/updater  && mkdir -p /usr/src/nextcloud/data  && mkdir -p /usr/src/nextcloud/custom_apps  && chmod +x /usr/src/nextcloud/occ
# Tue, 28 Nov 2017 19:22:35 GMT
COPY file:3fa42fa6664f03c90280a265050a78ef70bf32cd31864db727f5ee7e94828722 in /entrypoint.sh 
# Tue, 28 Nov 2017 19:22:36 GMT
COPY multi:55b88fcd3d6a1a8ca5ef52e5d2c9e27370c13cdc4c5e94d159f82a32979740ff in /usr/src/nextcloud/config/ 
# Tue, 28 Nov 2017 19:22:36 GMT
ENTRYPOINT ["/entrypoint.sh"]
# Tue, 28 Nov 2017 19:22:36 GMT
CMD ["php-fpm"]
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
	-	`sha256:13bb7a9b8ab04acc47feafef23390fc9c2f8ce2279667b1f11c08b1084bdf45e`  
		Last Modified: Tue, 28 Nov 2017 18:55:15 GMT  
		Size: 12.5 MB (12530243 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:3ed1ff1eaa361c20d8ad746e4b996cdea46ee9ffad86fe148c1c979f1d1f7f3d`  
		Last Modified: Tue, 28 Nov 2017 18:54:53 GMT  
		Size: 500.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:9b74af0249884dc1ab8dbee6489f59396f410260aff09871e689cedbd83e405b`  
		Last Modified: Tue, 28 Nov 2017 18:54:56 GMT  
		Size: 15.9 MB (15866070 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:5b0b6c5e5f1477a137adcc3c948743c0f10fc6b64e463b635cbb71b46200ccba`  
		Last Modified: Tue, 28 Nov 2017 18:54:52 GMT  
		Size: 2.2 KB (2174 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:83966cd282558b469b9476792261028908abf59463b80e3f0332630a83975a41`  
		Last Modified: Tue, 28 Nov 2017 18:54:52 GMT  
		Size: 130.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:05730d9f9a7b6f6f7aacb871cc50dd62ad4f75497ffb2c843d4564c214592817`  
		Last Modified: Tue, 28 Nov 2017 18:54:53 GMT  
		Size: 7.7 KB (7685 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:6ecb7ef905434cf983ec598f4b1c127650137512921dbab91b5dc2b907a79e41`  
		Last Modified: Tue, 28 Nov 2017 19:23:45 GMT  
		Size: 36.8 MB (36811065 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:78e744fbe7996a7fdcb25ac87f3fd92eeba89c630f4153f53559369cf628f008`  
		Last Modified: Tue, 28 Nov 2017 19:23:38 GMT  
		Size: 2.0 MB (1963925 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:92dd904f77ca3979402fdedff9e4f862cdfc87dad908d864abf929b89f9bf2e7`  
		Last Modified: Tue, 28 Nov 2017 19:23:38 GMT  
		Size: 356.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:2963356377a6d5c3a5753ca1f3caac02bf64d29e951d765afdbfa36dc9815cb0`  
		Last Modified: Tue, 28 Nov 2017 19:23:37 GMT  
		Size: 1.4 MB (1376087 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:d767505e6dd950a5362f16fb8afb6cb59f39b750ee3c6f8a3361697e6e715f83`  
		Last Modified: Tue, 28 Nov 2017 19:23:37 GMT  
		Size: 135.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:0cf84329e2e77c97e9e7398533f58b9a6530366a368ef595dbaaab4340afbe14`  
		Last Modified: Tue, 28 Nov 2017 19:25:03 GMT  
		Size: 47.0 MB (46970327 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:5072ce4ea3b14a539ca5b8f9c51445544b5faf62230f9105e19d570a244a3b90`  
		Last Modified: Tue, 28 Nov 2017 19:24:54 GMT  
		Size: 941.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:3ee9848fa90f705d609bac429739375f4708390c4186dc9d862311b6320f4a5b`  
		Last Modified: Tue, 28 Nov 2017 19:24:55 GMT  
		Size: 787.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
