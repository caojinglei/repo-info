## `jetty:jre7`

```console
$ docker pull jetty@sha256:9acad1602ca8a90b6793d90ceeb559bfae1200b2285e2dc368b326122bbdab00
```

-	Manifest MIME: `application/vnd.docker.distribution.manifest.list.v2+json`
-	Platforms:
	-	linux; amd64

### `jetty:jre7` - linux; amd64

```console
$ docker pull jetty@sha256:f7b67ebc8bfa31151c6de5e302c87528c401ec3779cc71225f8d14ae9bca298c
```

-	Docker Version: 17.06.2-ce
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **200.0 MB (200037185 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:c91c344f79e47cb9ec88c23c118bdfdfa12364001afcbb2161483946ea676f7b`
-	Entrypoint: `["\/docker-entrypoint.sh"]`
-	Default Command: `["java","-jar","\/usr\/local\/jetty\/start.jar"]`

```dockerfile
# Sat, 04 Nov 2017 05:21:35 GMT
ADD file:55b071e2cfc3ea2f4bbf048d7d676e3c06a77a9a98d63f7af291f3decb495ec8 in / 
# Sat, 04 Nov 2017 05:21:36 GMT
CMD ["bash"]
# Sat, 04 Nov 2017 15:25:24 GMT
RUN apt-get update && apt-get install -y --no-install-recommends 		ca-certificates 		curl 		wget 	&& rm -rf /var/lib/apt/lists/*
# Sat, 04 Nov 2017 15:25:25 GMT
RUN set -ex; 	if ! command -v gpg > /dev/null; then 		apt-get update; 		apt-get install -y --no-install-recommends 			gnupg 			dirmngr 		; 		rm -rf /var/lib/apt/lists/*; 	fi
# Sat, 04 Nov 2017 18:50:48 GMT
RUN apt-get update && apt-get install -y --no-install-recommends 		bzip2 		unzip 		xz-utils 	&& rm -rf /var/lib/apt/lists/*
# Sat, 04 Nov 2017 18:50:50 GMT
ENV LANG=C.UTF-8
# Sat, 04 Nov 2017 18:50:51 GMT
RUN { 		echo '#!/bin/sh'; 		echo 'set -e'; 		echo; 		echo 'dirname "$(dirname "$(readlink -f "$(which javac || which java)")")"'; 	} > /usr/local/bin/docker-java-home 	&& chmod +x /usr/local/bin/docker-java-home
# Sat, 04 Nov 2017 18:50:52 GMT
RUN ln -svT "/usr/lib/jvm/java-7-openjdk-$(dpkg --print-architecture)" /docker-java-home
# Sat, 04 Nov 2017 18:50:54 GMT
ENV JAVA_HOME=/docker-java-home/jre
# Sat, 04 Nov 2017 18:50:54 GMT
ENV JAVA_VERSION=7u151
# Mon, 27 Nov 2017 23:47:16 GMT
ENV JAVA_DEBIAN_VERSION=7u151-2.6.11-2~deb8u1
# Mon, 27 Nov 2017 23:48:05 GMT
RUN set -ex; 		if [ ! -d /usr/share/man/man1 ]; then 		mkdir -p /usr/share/man/man1; 	fi; 		apt-get update; 	apt-get install -y 		openjdk-7-jre="$JAVA_DEBIAN_VERSION" 	; 	rm -rf /var/lib/apt/lists/*; 		[ "$(readlink -f "$JAVA_HOME")" = "$(docker-java-home)" ]; 		update-alternatives --get-selections | awk -v home="$(readlink -f "$JAVA_HOME")" 'index($3, home) == 1 { $2 = "manual"; print | "update-alternatives --set-selections" }'; 	update-alternatives --query java | grep -q 'Status: manual'
# Tue, 28 Nov 2017 00:30:12 GMT
RUN groupadd -r jetty && useradd -r -g jetty jetty
# Tue, 28 Nov 2017 00:30:12 GMT
ENV JETTY_HOME=/usr/local/jetty
# Tue, 28 Nov 2017 00:30:13 GMT
ENV PATH=/usr/local/jetty/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
# Tue, 28 Nov 2017 00:30:14 GMT
RUN mkdir -p "$JETTY_HOME"
# Tue, 28 Nov 2017 00:30:14 GMT
WORKDIR /usr/local/jetty
# Tue, 28 Nov 2017 00:30:14 GMT
ENV JETTY_VERSION=9.2.22.v20170606
# Tue, 28 Nov 2017 00:30:15 GMT
ENV JETTY_TGZ_URL=https://repo1.maven.org/maven2/org/eclipse/jetty/jetty-distribution/9.2.22.v20170606/jetty-distribution-9.2.22.v20170606.tar.gz
# Tue, 28 Nov 2017 00:30:15 GMT
ENV JETTY_GPG_KEYS=AED5EE6C45D0FE8D5D1B164F27DED4BF6216DB8F 	2A684B57436A81FA8706B53C61C3351A438A3B7D 	5989BAF76217B843D66BE55B2D0E1FB8FE4B68B4 	B59B67FD7904984367F931800818D9D68FB67BAC 	BFBB21C246D7776836287A48A04E0C74ABB35FEA 	8B096546B1A8F02656B15D3B1677D141BCF3584D 	FBA2B18D238AB852DF95745C76157BDF03D0DCD6 	5C9579B3DB2E506429319AAEF33B071B29559E1E
# Tue, 28 Nov 2017 00:30:22 GMT
RUN set -xe 	&& curl -SL "$JETTY_TGZ_URL" -o jetty.tar.gz 	&& curl -SL "$JETTY_TGZ_URL.asc" -o jetty.tar.gz.asc 	&& export GNUPGHOME="$(mktemp -d)" 	&& for key in $JETTY_GPG_KEYS; do 		gpg --keyserver ha.pool.sks-keyservers.net --recv-keys "$key"; done 	&& gpg --batch --verify jetty.tar.gz.asc jetty.tar.gz 	&& rm -rf "$GNUPGHOME" 	&& tar -xvf jetty.tar.gz --strip-components=1 	&& sed -i '/jetty-logging/d' etc/jetty.conf 	&& rm -fr demo-base javadoc 	&& rm jetty.tar.gz* 	&& rm -rf /tmp/hsperfdata_root
# Tue, 28 Nov 2017 00:30:22 GMT
ENV JETTY_BASE=/var/lib/jetty
# Tue, 28 Nov 2017 00:30:23 GMT
RUN mkdir -p "$JETTY_BASE"
# Tue, 28 Nov 2017 00:30:24 GMT
WORKDIR /var/lib/jetty
# Tue, 28 Nov 2017 00:30:28 GMT
RUN modules="$(grep -- ^--module= "$JETTY_HOME/start.ini" | cut -d= -f2 | paste -d, -s)" 	&& set -xe 	&& java -jar "$JETTY_HOME/start.jar" --add-to-startd="$modules" 	&& chown -R jetty:jetty "$JETTY_BASE" 	&& rm -rf /tmp/hsperfdata_root
# Tue, 28 Nov 2017 00:30:28 GMT
ENV TMPDIR=/tmp/jetty
# Tue, 28 Nov 2017 00:30:29 GMT
RUN set -xe 	&& mkdir -p "$TMPDIR" 	&& chown -R jetty:jetty "$TMPDIR"
# Tue, 28 Nov 2017 00:30:30 GMT
COPY multi:4510ce2f7fb9540fb389937165085b97c71d4b0659b22ddb7dfe601528a7461a in / 
# Tue, 28 Nov 2017 00:30:30 GMT
USER [jetty]
# Tue, 28 Nov 2017 00:30:30 GMT
EXPOSE 8080/tcp
# Tue, 28 Nov 2017 00:30:31 GMT
ENTRYPOINT ["/docker-entrypoint.sh"]
# Tue, 28 Nov 2017 00:30:31 GMT
CMD ["java" "-jar" "/usr/local/jetty/start.jar"]
```

-	Layers:
	-	`sha256:85b1f47fba49da65256f07c8790542a3880e9216f9c491965040f35ce2c6ca7a`  
		Last Modified: Mon, 09 Oct 2017 21:36:40 GMT  
		Size: 52.6 MB (52595124 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:ba6bd283713a743ee651be9e0a833547e00c6f31584a948db2df96fded4def55`  
		Last Modified: Sat, 04 Nov 2017 15:44:37 GMT  
		Size: 19.3 MB (19264682 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:b7aa4dbe97e5b63bd1346397b8654ed128fc921461eec37d422553901d4cc52b`  
		Last Modified: Sat, 04 Nov 2017 18:59:07 GMT  
		Size: 795.6 KB (795608 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:9e61d008c81f137f4c363ec8f7ec90a7f1a7bf47c3088ff9c2b7a407c09b2d42`  
		Last Modified: Sat, 04 Nov 2017 18:59:07 GMT  
		Size: 248.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:c29ddaee35698323a54210b8b02af863070f19e84949e3e50eba7584027c66c7`  
		Last Modified: Sat, 04 Nov 2017 18:59:07 GMT  
		Size: 130.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:af2611810f545eb47835fbd635a50d2f4c50b8bf65f78c09fc1e61cd31994ff5`  
		Last Modified: Mon, 27 Nov 2017 23:51:45 GMT  
		Size: 117.3 MB (117349464 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:5f059392ef85edb3b397aa964a5e46390cab228c62273737d784ab70fd761c8b`  
		Last Modified: Tue, 28 Nov 2017 00:31:10 GMT  
		Size: 2.1 KB (2148 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:8c5ba000132fd811c60c0415c91a8ff37c75bf1275a63e20ab1826ee4ff003a2`  
		Last Modified: Tue, 28 Nov 2017 00:31:09 GMT  
		Size: 151.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:fdc5d6f7e369461d61855eb841fec4e748da93aae7253b9fc37151f749f7ee8c`  
		Last Modified: Tue, 28 Nov 2017 00:31:09 GMT  
		Size: 10.0 MB (10026513 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:a0866dea0ee60f99c81a94ca8facaf75dfa4eaafc1ec51dddf94b830e46b6fc4`  
		Last Modified: Tue, 28 Nov 2017 00:31:07 GMT  
		Size: 137.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:c61a515cbc2b2afd8b01d7a4ec34c703cec36930575c128c4191b17ea16ee78e`  
		Last Modified: Tue, 28 Nov 2017 00:31:07 GMT  
		Size: 1.5 KB (1466 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:9d997be168ac90a89fcdf45f6cc2e79c9d3eec65ed04badba27728df31b619bb`  
		Last Modified: Tue, 28 Nov 2017 00:31:07 GMT  
		Size: 126.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:6311d71374ccf67239b9e9d922ea6a71ba85f2d4855de26ac5584476cbe8ac1d`  
		Last Modified: Tue, 28 Nov 2017 00:31:07 GMT  
		Size: 1.4 KB (1388 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
