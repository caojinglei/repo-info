## `haproxy:latest`

```console
$ docker pull haproxy@sha256:943b0c4c0921863798b8407ea2213a97a21767b133a3d476d0b16dbfa6e234ad
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

### `haproxy:latest` - linux; amd64

```console
$ docker pull haproxy@sha256:e8f2619d83fc05c76a682b798419b99a5fefbc5538c6c07e92354309b34088c0
```

-	Docker Version: 17.06.2-ce
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **28.2 MB (28216466 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:b79715c1dcfa349eff32406debb3386af356a9f599038cd33ed9ffdbb3155a95`
-	Entrypoint: `["\/docker-entrypoint.sh"]`
-	Default Command: `["haproxy","-f","\/usr\/local\/etc\/haproxy\/haproxy.cfg"]`

```dockerfile
# Sat, 04 Nov 2017 05:26:48 GMT
ADD file:45233d6b5c9b91e9437065d3e7c332d1c4eb4bce8e1079a4c1af342c450abe67 in / 
# Sat, 04 Nov 2017 05:26:48 GMT
CMD ["bash"]
# Thu, 23 Nov 2017 01:23:03 GMT
RUN apt-get update 	&& apt-get install -y --no-install-recommends 		liblua5.3-0 		libpcre3 		libssl1.1 	&& rm -rf /var/lib/apt/lists/*
# Thu, 23 Nov 2017 01:23:04 GMT
ENV HAPROXY_MAJOR=1.8
# Tue, 28 Nov 2017 01:35:17 GMT
ENV HAPROXY_VERSION=1.8.0
# Tue, 28 Nov 2017 01:35:17 GMT
ENV HAPROXY_MD5=6ccea4619b7183fbcc8c98bae1f9823d
# Tue, 28 Nov 2017 01:35:56 GMT
RUN set -x 		&& buildDeps=' 		gcc 		libc6-dev 		liblua5.3-dev 		libpcre3-dev 		libssl-dev 		zlib1g-dev 		make 		wget 	' 	&& apt-get update && apt-get install -y $buildDeps --no-install-recommends && rm -rf /var/lib/apt/lists/* 		&& wget -O haproxy.tar.gz "http://www.haproxy.org/download/${HAPROXY_MAJOR}/src/haproxy-${HAPROXY_VERSION}.tar.gz" 	&& echo "$HAPROXY_MD5 *haproxy.tar.gz" | md5sum -c 	&& mkdir -p /usr/src/haproxy 	&& tar -xzf haproxy.tar.gz -C /usr/src/haproxy --strip-components=1 	&& rm haproxy.tar.gz 		&& makeOpts=' 		TARGET=linux2628 		USE_LUA=1 LUA_INC=/usr/include/lua5.3 		USE_OPENSSL=1 		USE_PCRE=1 PCREDIR= 		USE_ZLIB=1 	' 	&& make -C /usr/src/haproxy -j "$(nproc)" all $makeOpts 	&& make -C /usr/src/haproxy install-bin $makeOpts 		&& mkdir -p /usr/local/etc/haproxy 	&& cp -R /usr/src/haproxy/examples/errorfiles /usr/local/etc/haproxy/errors 	&& rm -rf /usr/src/haproxy 		&& apt-get purge -y --auto-remove $buildDeps
# Tue, 28 Nov 2017 01:35:59 GMT
COPY file:9489da093f9bbacb372aa24916cd4607d45b831e8054d997ab55a1be7b595c17 in / 
# Tue, 28 Nov 2017 01:35:59 GMT
ENTRYPOINT ["/docker-entrypoint.sh"]
# Tue, 28 Nov 2017 01:36:00 GMT
CMD ["haproxy" "-f" "/usr/local/etc/haproxy/haproxy.cfg"]
```

-	Layers:
	-	`sha256:bc95e04b23c06ba1b9bf092d07d1493177b218e0340bd2ed49dac351c1e34313`  
		Last Modified: Mon, 09 Oct 2017 21:42:28 GMT  
		Size: 22.5 MB (22492350 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:041d775ae156140f3febe57be6b7e48f1a7273cad78e7fc0cb62270a38de4580`  
		Last Modified: Thu, 23 Nov 2017 01:29:43 GMT  
		Size: 2.1 MB (2102289 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:9b22ac8ba3ea8176334a2d0edeff850f95dfdaa810057c8c4a86edbaaaa613ab`  
		Last Modified: Tue, 28 Nov 2017 01:37:16 GMT  
		Size: 3.6 MB (3621447 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:99bfa5416fc72f0ec382db4b27e05897795776f48d17426c052d8592bd6137ce`  
		Last Modified: Tue, 28 Nov 2017 01:37:15 GMT  
		Size: 380.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip

### `haproxy:latest` - linux; arm variant v5

```console
$ docker pull haproxy@sha256:c0c903a1254593f5d52fb1cf23b8407b3e182baaea90d94c2e565e875bbaebcf
```

-	Docker Version: 17.06.0-ce
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **26.5 MB (26545723 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:8d2ebfe319e86e488679d6c8e3ce382cbc8a48e876e21dcf655c22842c3e3979`
-	Entrypoint: `["\/docker-entrypoint.sh"]`
-	Default Command: `["haproxy","-f","\/usr\/local\/etc\/haproxy\/haproxy.cfg"]`

```dockerfile
# Mon, 09 Oct 2017 21:44:48 GMT
ADD file:ff9945b48b1ac236dcec24eb9dfaf52b7c151a3b11c8502391f0866dfb4e3ac3 in / 
# Mon, 09 Oct 2017 21:44:48 GMT
CMD ["bash"]
# Thu, 23 Nov 2017 09:58:32 GMT
RUN apt-get update 	&& apt-get install -y --no-install-recommends 		liblua5.3-0 		libpcre3 		libssl1.1 	&& rm -rf /var/lib/apt/lists/*
# Thu, 23 Nov 2017 09:58:32 GMT
ENV HAPROXY_MAJOR=1.8
# Tue, 28 Nov 2017 09:57:53 GMT
ENV HAPROXY_VERSION=1.8.0
# Tue, 28 Nov 2017 09:57:53 GMT
ENV HAPROXY_MD5=6ccea4619b7183fbcc8c98bae1f9823d
# Tue, 28 Nov 2017 09:58:35 GMT
RUN set -x 		&& buildDeps=' 		gcc 		libc6-dev 		liblua5.3-dev 		libpcre3-dev 		libssl-dev 		zlib1g-dev 		make 		wget 	' 	&& apt-get update && apt-get install -y $buildDeps --no-install-recommends && rm -rf /var/lib/apt/lists/* 		&& wget -O haproxy.tar.gz "http://www.haproxy.org/download/${HAPROXY_MAJOR}/src/haproxy-${HAPROXY_VERSION}.tar.gz" 	&& echo "$HAPROXY_MD5 *haproxy.tar.gz" | md5sum -c 	&& mkdir -p /usr/src/haproxy 	&& tar -xzf haproxy.tar.gz -C /usr/src/haproxy --strip-components=1 	&& rm haproxy.tar.gz 		&& makeOpts=' 		TARGET=linux2628 		USE_LUA=1 LUA_INC=/usr/include/lua5.3 		USE_OPENSSL=1 		USE_PCRE=1 PCREDIR= 		USE_ZLIB=1 	' 	&& make -C /usr/src/haproxy -j "$(nproc)" all $makeOpts 	&& make -C /usr/src/haproxy install-bin $makeOpts 		&& mkdir -p /usr/local/etc/haproxy 	&& cp -R /usr/src/haproxy/examples/errorfiles /usr/local/etc/haproxy/errors 	&& rm -rf /usr/src/haproxy 		&& apt-get purge -y --auto-remove $buildDeps
# Tue, 28 Nov 2017 09:58:35 GMT
COPY file:9489da093f9bbacb372aa24916cd4607d45b831e8054d997ab55a1be7b595c17 in / 
# Tue, 28 Nov 2017 09:58:35 GMT
ENTRYPOINT ["/docker-entrypoint.sh"]
# Tue, 28 Nov 2017 09:58:35 GMT
CMD ["haproxy" "-f" "/usr/local/etc/haproxy/haproxy.cfg"]
```

-	Layers:
	-	`sha256:836d5b6056a9815be79c76480a90299267f60201bd1e3396817003e6c14819cc`  
		Last Modified: Mon, 09 Oct 2017 21:50:56 GMT  
		Size: 21.2 MB (21166251 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:31733362de6bf9588f054cd414af095827c165f1f22befcf4406d10bb29ad527`  
		Last Modified: Thu, 23 Nov 2017 10:00:41 GMT  
		Size: 1.8 MB (1816054 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:7ad9f4b387c93060951a2070eded581f33999ce7fbd6a2af491ddd473bbce57b`  
		Last Modified: Tue, 28 Nov 2017 09:58:52 GMT  
		Size: 3.6 MB (3563038 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:0e9e7a3ae0e22a67a070604994021c8c28ad455b78bc01e72838846aeefb285c`  
		Last Modified: Tue, 28 Nov 2017 09:58:51 GMT  
		Size: 380.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip

### `haproxy:latest` - linux; arm variant v7

```console
$ docker pull haproxy@sha256:77ceeb83d36f92b5c3c98d5d94375641ee3aa9b1f2ae2b093c7dc10d464ab04d
```

-	Docker Version: 17.06.0-ce
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **24.5 MB (24524456 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:ea8c48d05ffd1925b92fbe165109e290fcaf9ec0208124150d9fb597931afb9c`
-	Entrypoint: `["\/docker-entrypoint.sh"]`
-	Default Command: `["haproxy","-f","\/usr\/local\/etc\/haproxy\/haproxy.cfg"]`

```dockerfile
# Mon, 09 Oct 2017 21:45:43 GMT
ADD file:b758c6c3ff989778bd740dde35c86b953fa09be913a7e02711b2881de6b8911d in / 
# Mon, 09 Oct 2017 21:45:44 GMT
CMD ["bash"]
# Thu, 23 Nov 2017 17:23:50 GMT
RUN apt-get update 	&& apt-get install -y --no-install-recommends 		liblua5.3-0 		libpcre3 		libssl1.1 	&& rm -rf /var/lib/apt/lists/*
# Thu, 23 Nov 2017 17:23:50 GMT
ENV HAPROXY_MAJOR=1.8
# Tue, 28 Nov 2017 17:23:05 GMT
ENV HAPROXY_VERSION=1.8.0
# Tue, 28 Nov 2017 17:23:06 GMT
ENV HAPROXY_MD5=6ccea4619b7183fbcc8c98bae1f9823d
# Tue, 28 Nov 2017 17:23:31 GMT
RUN set -x 		&& buildDeps=' 		gcc 		libc6-dev 		liblua5.3-dev 		libpcre3-dev 		libssl-dev 		zlib1g-dev 		make 		wget 	' 	&& apt-get update && apt-get install -y $buildDeps --no-install-recommends && rm -rf /var/lib/apt/lists/* 		&& wget -O haproxy.tar.gz "http://www.haproxy.org/download/${HAPROXY_MAJOR}/src/haproxy-${HAPROXY_VERSION}.tar.gz" 	&& echo "$HAPROXY_MD5 *haproxy.tar.gz" | md5sum -c 	&& mkdir -p /usr/src/haproxy 	&& tar -xzf haproxy.tar.gz -C /usr/src/haproxy --strip-components=1 	&& rm haproxy.tar.gz 		&& makeOpts=' 		TARGET=linux2628 		USE_LUA=1 LUA_INC=/usr/include/lua5.3 		USE_OPENSSL=1 		USE_PCRE=1 PCREDIR= 		USE_ZLIB=1 	' 	&& make -C /usr/src/haproxy -j "$(nproc)" all $makeOpts 	&& make -C /usr/src/haproxy install-bin $makeOpts 		&& mkdir -p /usr/local/etc/haproxy 	&& cp -R /usr/src/haproxy/examples/errorfiles /usr/local/etc/haproxy/errors 	&& rm -rf /usr/src/haproxy 		&& apt-get purge -y --auto-remove $buildDeps
# Tue, 28 Nov 2017 17:23:32 GMT
COPY file:9489da093f9bbacb372aa24916cd4607d45b831e8054d997ab55a1be7b595c17 in / 
# Tue, 28 Nov 2017 17:23:32 GMT
ENTRYPOINT ["/docker-entrypoint.sh"]
# Tue, 28 Nov 2017 17:23:32 GMT
CMD ["haproxy" "-f" "/usr/local/etc/haproxy/haproxy.cfg"]
```

-	Layers:
	-	`sha256:59e81a3fde58ec8d4b8f2f58b98ef2f4d951d37dd9b99b016fd294a8e07d7796`  
		Last Modified: Mon, 09 Oct 2017 21:52:49 GMT  
		Size: 19.3 MB (19277135 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:101d4d936d95ab3dbdcb7ec3808ff887e54ec3c7862ff652a2132bb21e27d0df`  
		Last Modified: Thu, 23 Nov 2017 17:26:13 GMT  
		Size: 1.7 MB (1736053 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:cb9b608dcf7f781cba5c398c74041541c14bc8d59914affb6e3edd252703c85b`  
		Last Modified: Tue, 28 Nov 2017 17:23:53 GMT  
		Size: 3.5 MB (3510888 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:c52dc9c38b190f27be592a633d4b6da59a79aa00e757ede22c0afa74ae5f3588`  
		Last Modified: Tue, 28 Nov 2017 17:23:53 GMT  
		Size: 380.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip

### `haproxy:latest` - linux; arm64 variant v8

```console
$ docker pull haproxy@sha256:8c826de4b1932b032505eedcf814d9ac4442b20e99a5cd71bb0928264ecd3aca
```

-	Docker Version: 17.06.2-ce
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **25.7 MB (25684390 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:d42e015e2ab8fa917f181db6cb1f66fb109f13b8067275abb55dc4a669bc0823`
-	Entrypoint: `["\/docker-entrypoint.sh"]`
-	Default Command: `["haproxy","-f","\/usr\/local\/etc\/haproxy\/haproxy.cfg"]`

```dockerfile
# Mon, 09 Oct 2017 21:47:55 GMT
ADD file:3a528355cfc75437716aff3b517ef99ae602918d84d26dbafff0ed142248fb93 in / 
# Mon, 09 Oct 2017 21:47:56 GMT
CMD ["bash"]
# Thu, 23 Nov 2017 20:43:50 GMT
RUN apt-get update 	&& apt-get install -y --no-install-recommends 		liblua5.3-0 		libpcre3 		libssl1.1 	&& rm -rf /var/lib/apt/lists/*
# Thu, 23 Nov 2017 20:43:51 GMT
ENV HAPROXY_MAJOR=1.8
# Tue, 28 Nov 2017 20:42:42 GMT
ENV HAPROXY_VERSION=1.8.0
# Tue, 28 Nov 2017 20:42:42 GMT
ENV HAPROXY_MD5=6ccea4619b7183fbcc8c98bae1f9823d
# Tue, 28 Nov 2017 20:44:11 GMT
RUN set -x 		&& buildDeps=' 		gcc 		libc6-dev 		liblua5.3-dev 		libpcre3-dev 		libssl-dev 		zlib1g-dev 		make 		wget 	' 	&& apt-get update && apt-get install -y $buildDeps --no-install-recommends && rm -rf /var/lib/apt/lists/* 		&& wget -O haproxy.tar.gz "http://www.haproxy.org/download/${HAPROXY_MAJOR}/src/haproxy-${HAPROXY_VERSION}.tar.gz" 	&& echo "$HAPROXY_MD5 *haproxy.tar.gz" | md5sum -c 	&& mkdir -p /usr/src/haproxy 	&& tar -xzf haproxy.tar.gz -C /usr/src/haproxy --strip-components=1 	&& rm haproxy.tar.gz 		&& makeOpts=' 		TARGET=linux2628 		USE_LUA=1 LUA_INC=/usr/include/lua5.3 		USE_OPENSSL=1 		USE_PCRE=1 PCREDIR= 		USE_ZLIB=1 	' 	&& make -C /usr/src/haproxy -j "$(nproc)" all $makeOpts 	&& make -C /usr/src/haproxy install-bin $makeOpts 		&& mkdir -p /usr/local/etc/haproxy 	&& cp -R /usr/src/haproxy/examples/errorfiles /usr/local/etc/haproxy/errors 	&& rm -rf /usr/src/haproxy 		&& apt-get purge -y --auto-remove $buildDeps
# Tue, 28 Nov 2017 20:44:12 GMT
COPY file:9489da093f9bbacb372aa24916cd4607d45b831e8054d997ab55a1be7b595c17 in / 
# Tue, 28 Nov 2017 20:44:13 GMT
ENTRYPOINT ["/docker-entrypoint.sh"]
# Tue, 28 Nov 2017 20:44:13 GMT
CMD ["haproxy" "-f" "/usr/local/etc/haproxy/haproxy.cfg"]
```

-	Layers:
	-	`sha256:e907afd6e25615a4d3eb554d930cef57b87e79ec82413889c2eac38beb4eb8f7`  
		Last Modified: Mon, 09 Oct 2017 22:03:08 GMT  
		Size: 20.3 MB (20337143 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:ab04b73ae073d0004082c69ca62cd1e64d97c53f45bfebff13383b7c3d859a12`  
		Last Modified: Thu, 23 Nov 2017 20:50:04 GMT  
		Size: 1.8 MB (1818801 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:56a4a9a7536d92e19085c82a183d2cab15f34bb60ade4304c9e092e51d587020`  
		Last Modified: Tue, 28 Nov 2017 20:46:03 GMT  
		Size: 3.5 MB (3528066 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:ead16e58f549c98a6d0a53a4606dfab5800199147ea2f5a6fe2f869ea6c0f7e7`  
		Last Modified: Tue, 28 Nov 2017 20:46:02 GMT  
		Size: 380.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip

### `haproxy:latest` - linux; 386

```console
$ docker pull haproxy@sha256:5fdd27b31c0d2457c4d5569d6f07f38e6ac08ece8ef08198296c713ffdacadf3
```

-	Docker Version: 17.06.2-ce
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **28.8 MB (28790863 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:5db65839892d3f463f79df69cd567fec2885adf54d050d164237ee176d03f899`
-	Entrypoint: `["\/docker-entrypoint.sh"]`
-	Default Command: `["haproxy","-f","\/usr\/local\/etc\/haproxy\/haproxy.cfg"]`

```dockerfile
# Mon, 09 Oct 2017 21:45:36 GMT
ADD file:6582536277127947668f7bfdc1471a4e36170915b91a4cb841e7e1bfa1de6535 in / 
# Mon, 09 Oct 2017 21:45:36 GMT
CMD ["bash"]
# Thu, 23 Nov 2017 05:37:02 GMT
RUN apt-get update 	&& apt-get install -y --no-install-recommends 		liblua5.3-0 		libpcre3 		libssl1.1 	&& rm -rf /var/lib/apt/lists/*
# Thu, 23 Nov 2017 05:37:02 GMT
ENV HAPROXY_MAJOR=1.8
# Tue, 28 Nov 2017 05:29:57 GMT
ENV HAPROXY_VERSION=1.8.0
# Tue, 28 Nov 2017 05:29:57 GMT
ENV HAPROXY_MD5=6ccea4619b7183fbcc8c98bae1f9823d
# Tue, 28 Nov 2017 05:35:37 GMT
RUN set -x 		&& buildDeps=' 		gcc 		libc6-dev 		liblua5.3-dev 		libpcre3-dev 		libssl-dev 		zlib1g-dev 		make 		wget 	' 	&& apt-get update && apt-get install -y $buildDeps --no-install-recommends && rm -rf /var/lib/apt/lists/* 		&& wget -O haproxy.tar.gz "http://www.haproxy.org/download/${HAPROXY_MAJOR}/src/haproxy-${HAPROXY_VERSION}.tar.gz" 	&& echo "$HAPROXY_MD5 *haproxy.tar.gz" | md5sum -c 	&& mkdir -p /usr/src/haproxy 	&& tar -xzf haproxy.tar.gz -C /usr/src/haproxy --strip-components=1 	&& rm haproxy.tar.gz 		&& makeOpts=' 		TARGET=linux2628 		USE_LUA=1 LUA_INC=/usr/include/lua5.3 		USE_OPENSSL=1 		USE_PCRE=1 PCREDIR= 		USE_ZLIB=1 	' 	&& make -C /usr/src/haproxy -j "$(nproc)" all $makeOpts 	&& make -C /usr/src/haproxy install-bin $makeOpts 		&& mkdir -p /usr/local/etc/haproxy 	&& cp -R /usr/src/haproxy/examples/errorfiles /usr/local/etc/haproxy/errors 	&& rm -rf /usr/src/haproxy 		&& apt-get purge -y --auto-remove $buildDeps
# Tue, 28 Nov 2017 05:35:37 GMT
COPY file:9489da093f9bbacb372aa24916cd4607d45b831e8054d997ab55a1be7b595c17 in / 
# Tue, 28 Nov 2017 05:35:38 GMT
ENTRYPOINT ["/docker-entrypoint.sh"]
# Tue, 28 Nov 2017 05:35:38 GMT
CMD ["haproxy" "-f" "/usr/local/etc/haproxy/haproxy.cfg"]
```

-	Layers:
	-	`sha256:b2b52fe46b29fe5d0689f26449c2114e40f0731d4ce3eb8c3941397b74205432`  
		Last Modified: Mon, 09 Oct 2017 21:53:42 GMT  
		Size: 23.1 MB (23128678 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:08724654510187f71cbd16d8a1c24b9a6848cf7b598e221a8f85be7502a1e6ca`  
		Last Modified: Thu, 23 Nov 2017 05:41:11 GMT  
		Size: 2.1 MB (2128534 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:d6ab5fbe1cd05134a274c90690fe9a3c7873503876ce4ce6ce3bf2ee75e0d0d0`  
		Last Modified: Tue, 28 Nov 2017 05:38:28 GMT  
		Size: 3.5 MB (3533271 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:6d4d693bdc5090dadce4d0051d930f93ac489de274403e54017b61002a05e4f1`  
		Last Modified: Tue, 28 Nov 2017 05:38:27 GMT  
		Size: 380.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip

### `haproxy:latest` - linux; ppc64le

```console
$ docker pull haproxy@sha256:a86af491cb6d21f5f912e3e642e47e7012c60d20a749a4ebae8d72cccddd9f26
```

-	Docker Version: 17.06.2-ce
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **28.1 MB (28134482 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:ad8d5b1d81436cd5e37a7301f45249484f923f761ac16b5f9d0d6202e50bdfcf`
-	Entrypoint: `["\/docker-entrypoint.sh"]`
-	Default Command: `["haproxy","-f","\/usr\/local\/etc\/haproxy\/haproxy.cfg"]`

```dockerfile
# Mon, 09 Oct 2017 21:45:56 GMT
ADD file:7edf73437495be24244c16841b563be06c15452963f41ac940fb5e105ed96027 in / 
# Mon, 09 Oct 2017 21:45:58 GMT
CMD ["bash"]
# Thu, 23 Nov 2017 03:12:06 GMT
RUN apt-get update 	&& apt-get install -y --no-install-recommends 		liblua5.3-0 		libpcre3 		libssl1.1 	&& rm -rf /var/lib/apt/lists/*
# Thu, 23 Nov 2017 03:12:07 GMT
ENV HAPROXY_MAJOR=1.8
# Tue, 28 Nov 2017 03:11:48 GMT
ENV HAPROXY_VERSION=1.8.0
# Tue, 28 Nov 2017 03:11:48 GMT
ENV HAPROXY_MD5=6ccea4619b7183fbcc8c98bae1f9823d
# Tue, 28 Nov 2017 03:13:59 GMT
RUN set -x 		&& buildDeps=' 		gcc 		libc6-dev 		liblua5.3-dev 		libpcre3-dev 		libssl-dev 		zlib1g-dev 		make 		wget 	' 	&& apt-get update && apt-get install -y $buildDeps --no-install-recommends && rm -rf /var/lib/apt/lists/* 		&& wget -O haproxy.tar.gz "http://www.haproxy.org/download/${HAPROXY_MAJOR}/src/haproxy-${HAPROXY_VERSION}.tar.gz" 	&& echo "$HAPROXY_MD5 *haproxy.tar.gz" | md5sum -c 	&& mkdir -p /usr/src/haproxy 	&& tar -xzf haproxy.tar.gz -C /usr/src/haproxy --strip-components=1 	&& rm haproxy.tar.gz 		&& makeOpts=' 		TARGET=linux2628 		USE_LUA=1 LUA_INC=/usr/include/lua5.3 		USE_OPENSSL=1 		USE_PCRE=1 PCREDIR= 		USE_ZLIB=1 	' 	&& make -C /usr/src/haproxy -j "$(nproc)" all $makeOpts 	&& make -C /usr/src/haproxy install-bin $makeOpts 		&& mkdir -p /usr/local/etc/haproxy 	&& cp -R /usr/src/haproxy/examples/errorfiles /usr/local/etc/haproxy/errors 	&& rm -rf /usr/src/haproxy 		&& apt-get purge -y --auto-remove $buildDeps
# Tue, 28 Nov 2017 03:14:00 GMT
COPY file:9489da093f9bbacb372aa24916cd4607d45b831e8054d997ab55a1be7b595c17 in / 
# Tue, 28 Nov 2017 03:14:01 GMT
ENTRYPOINT ["/docker-entrypoint.sh"]
# Tue, 28 Nov 2017 03:14:02 GMT
CMD ["haproxy" "-f" "/usr/local/etc/haproxy/haproxy.cfg"]
```

-	Layers:
	-	`sha256:c4860466fa1e6824151f4fa3a51ef0e9d7d3c3ba860e21d94e69988b65601260`  
		Last Modified: Mon, 09 Oct 2017 21:52:59 GMT  
		Size: 22.7 MB (22746217 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:e75adab98bffb08aa0ec4b66a1fb8bab79e29ba591819001b1c0c7010d578582`  
		Last Modified: Thu, 23 Nov 2017 03:17:29 GMT  
		Size: 1.8 MB (1781153 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:76c67ab90ee7dcb694121afea3aa9bbac24da6b3eb2feed6e92e1ab938f4e107`  
		Last Modified: Tue, 28 Nov 2017 03:15:25 GMT  
		Size: 3.6 MB (3606732 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:4bcdede432e2b127f255fcd81bd6f8f0b8eb44931a812c30369bce325616b187`  
		Last Modified: Tue, 28 Nov 2017 03:15:23 GMT  
		Size: 380.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip

### `haproxy:latest` - linux; s390x

```console
$ docker pull haproxy@sha256:3bb6a02b030fae6bfcb4145a4e11522cd2ab9f66b446205663f6822ae429476f
```

-	Docker Version: 17.06.1-ce
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **27.9 MB (27885094 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:e8b63aa6c94fefa2f2d3958abeeb13776e7b9ba149c19203d92c3ff08a06f552`
-	Entrypoint: `["\/docker-entrypoint.sh"]`
-	Default Command: `["haproxy","-f","\/usr\/local\/etc\/haproxy\/haproxy.cfg"]`

```dockerfile
# Mon, 09 Oct 2017 21:44:35 GMT
ADD file:ae4aaa6affe22f36ab5478771d5c84917f72de7a8dac16345a035709a1a5edf4 in / 
# Mon, 09 Oct 2017 21:44:36 GMT
CMD ["bash"]
# Thu, 23 Nov 2017 17:54:41 GMT
RUN apt-get update 	&& apt-get install -y --no-install-recommends 		liblua5.3-0 		libpcre3 		libssl1.1 	&& rm -rf /var/lib/apt/lists/*
# Thu, 23 Nov 2017 17:54:41 GMT
ENV HAPROXY_MAJOR=1.8
# Tue, 28 Nov 2017 17:54:11 GMT
ENV HAPROXY_VERSION=1.8.0
# Tue, 28 Nov 2017 17:54:11 GMT
ENV HAPROXY_MD5=6ccea4619b7183fbcc8c98bae1f9823d
# Tue, 28 Nov 2017 17:54:55 GMT
RUN set -x 		&& buildDeps=' 		gcc 		libc6-dev 		liblua5.3-dev 		libpcre3-dev 		libssl-dev 		zlib1g-dev 		make 		wget 	' 	&& apt-get update && apt-get install -y $buildDeps --no-install-recommends && rm -rf /var/lib/apt/lists/* 		&& wget -O haproxy.tar.gz "http://www.haproxy.org/download/${HAPROXY_MAJOR}/src/haproxy-${HAPROXY_VERSION}.tar.gz" 	&& echo "$HAPROXY_MD5 *haproxy.tar.gz" | md5sum -c 	&& mkdir -p /usr/src/haproxy 	&& tar -xzf haproxy.tar.gz -C /usr/src/haproxy --strip-components=1 	&& rm haproxy.tar.gz 		&& makeOpts=' 		TARGET=linux2628 		USE_LUA=1 LUA_INC=/usr/include/lua5.3 		USE_OPENSSL=1 		USE_PCRE=1 PCREDIR= 		USE_ZLIB=1 	' 	&& make -C /usr/src/haproxy -j "$(nproc)" all $makeOpts 	&& make -C /usr/src/haproxy install-bin $makeOpts 		&& mkdir -p /usr/local/etc/haproxy 	&& cp -R /usr/src/haproxy/examples/errorfiles /usr/local/etc/haproxy/errors 	&& rm -rf /usr/src/haproxy 		&& apt-get purge -y --auto-remove $buildDeps
# Tue, 28 Nov 2017 17:54:55 GMT
COPY file:9489da093f9bbacb372aa24916cd4607d45b831e8054d997ab55a1be7b595c17 in / 
# Tue, 28 Nov 2017 17:54:56 GMT
ENTRYPOINT ["/docker-entrypoint.sh"]
# Tue, 28 Nov 2017 17:54:56 GMT
CMD ["haproxy" "-f" "/usr/local/etc/haproxy/haproxy.cfg"]
```

-	Layers:
	-	`sha256:671716cc49517eef5f430c695ce344d63e390cb65f58d30939f2ba615c953686`  
		Last Modified: Mon, 09 Oct 2017 21:49:09 GMT  
		Size: 22.3 MB (22339951 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:c4a670965f9b47131be07001a257862b7026719a76da436763a0901d9d6bec97`  
		Last Modified: Thu, 23 Nov 2017 17:56:52 GMT  
		Size: 1.8 MB (1841010 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:6e0ffd74f5cdc7f94eecdddaa62accd971518d4d7f166b9d3a93b79be918314c`  
		Last Modified: Tue, 28 Nov 2017 17:55:50 GMT  
		Size: 3.7 MB (3703753 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:2908a55ed247fb9ba83100147002b3bbbf3d5629f09ffabc02c2e5e6b1e29767`  
		Last Modified: Tue, 28 Nov 2017 17:55:49 GMT  
		Size: 380.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
