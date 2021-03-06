## `maven:ibmjava-alpine`

```console
$ docker pull maven@sha256:7921d9e93da84d74d4f8564b2e33b0451bfe28922343eb95a422e6cba33908d0
```

-	Manifest MIME: `application/vnd.docker.distribution.manifest.list.v2+json`
-	Platforms:
	-	linux; amd64

### `maven:ibmjava-alpine` - linux; amd64

```console
$ docker pull maven@sha256:57c85edece4ab2b3d4bc35dd367efc5ae25099120e75c233d446e7dfb7a85422
```

-	Docker Version: 17.06.2-ce
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **179.0 MB (179037924 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:1af4e8d87bba76a099790c8cace3deac492c7a16fa0e2cd96e734fda6b7a9406`
-	Entrypoint: `["\/usr\/local\/bin\/mvn-entrypoint.sh"]`
-	Default Command: `["mvn"]`

```dockerfile
# Fri, 03 Nov 2017 22:10:18 GMT
ADD file:1e87ff33d1b6765b793888cd50e01b2bd0dfe152b7dbb4048008bfc2658faea7 in / 
# Fri, 03 Nov 2017 22:10:18 GMT
CMD ["/bin/sh"]
# Sat, 04 Nov 2017 04:19:05 GMT
MAINTAINER Dinakar Guniguntala <dinakar.g@in.ibm.com> (@dinogun)
# Sat, 04 Nov 2017 04:19:21 GMT
RUN apk --update add --no-cache ca-certificates curl openssl binutils xz     && GLIBC_VER="2.25-r0"     && ALPINE_GLIBC_REPO="https://github.com/sgerrand/alpine-pkg-glibc/releases/download"     && curl -Ls ${ALPINE_GLIBC_REPO}/${GLIBC_VER}/glibc-${GLIBC_VER}.apk > /tmp/${GLIBC_VER}.apk     && apk add --allow-untrusted /tmp/${GLIBC_VER}.apk     && curl -Ls https://www.archlinux.org/packages/core/x86_64/gcc-libs/download > /tmp/gcc-libs.tar.xz     && mkdir /tmp/gcc     && tar -xf /tmp/gcc-libs.tar.xz -C /tmp/gcc     && mv /tmp/gcc/usr/lib/libgcc* /tmp/gcc/usr/lib/libstdc++* /usr/glibc-compat/lib     && strip /usr/glibc-compat/lib/libgcc_s.so.* /usr/glibc-compat/lib/libstdc++.so*     && apk del curl binutils     && rm -rf /tmp/${GLIBC_VER}.apk /tmp/gcc /tmp/gcc-libs.tar.xz /var/cache/apk/*
# Mon, 27 Nov 2017 18:39:11 GMT
ENV JAVA_VERSION=1.8.0_sr5fp5
# Mon, 27 Nov 2017 18:42:31 GMT
RUN set -eux;     ARCH="$(apk --print-arch)";     case "${ARCH}" in        amd64|x86_64)          ESUM='5989bd22deb8147fb14f5ef0b225c3514331eee82b8bd43a43688927b3867db0';          YML_FILE='sdk/linux/x86_64/index.yml';          ;;        i386)          ESUM='95f6c61db9581255f708988d1fc13df46a53561c3a4eb78ac0440b06b9680fab';          YML_FILE='sdk/linux/i386/index.yml';          ;;        ppc64el|ppc64le)          ESUM='a635df7beafc8f318cab0630cfc0d2009051c095a755d27b0d617e9dee627807';          YML_FILE='sdk/linux/ppc64le/index.yml';          ;;        s390)          ESUM='facfa6623ac39e1c103e05c4b98638ab1ffd3dcd50f6347563691561f9a95383';          YML_FILE='sdk/linux/s390/index.yml';          ;;        s390x)          ESUM='1e0237eeaa96c168f5ce54fcbddbb949e4654f31d2a5f60314ee06dca98fc6bd';          YML_FILE='sdk/linux/s390x/index.yml';          ;;        *)          echo "Unsupported arch: ${ARCH}";          exit 1;          ;;     esac;     BASE_URL="https://public.dhe.ibm.com/ibmdl/export/pub/systems/cloud/runtimes/java/meta/";     wget -q -U UA_IBM_JAVA_Docker -O /tmp/index.yml ${BASE_URL}/${YML_FILE};     JAVA_URL=$(cat /tmp/index.yml | sed -n '/'${JAVA_VERSION}'/{n;p}' | sed -n 's/\s*uri:\s//p' | tr -d '\r');     wget -q -U UA_IBM_JAVA_Docker -O /tmp/ibm-java.bin ${JAVA_URL};     echo "${ESUM}  /tmp/ibm-java.bin" | sha256sum -c -;     echo "INSTALLER_UI=silent" > /tmp/response.properties;     echo "USER_INSTALL_DIR=/opt/ibm/java" >> /tmp/response.properties;     echo "LICENSE_ACCEPTED=TRUE" >> /tmp/response.properties;     mkdir -p /opt/ibm;     chmod +x /tmp/ibm-java.bin;     /tmp/ibm-java.bin -i silent -f /tmp/response.properties;     rm -f /tmp/response.properties;     rm -f /tmp/index.yml;     rm -f /tmp/ibm-java.bin;     cd /opt/ibm/java/jre/lib;     rm -rf icc;
# Mon, 27 Nov 2017 18:42:31 GMT
ENV JAVA_HOME=/opt/ibm/java/jre PATH=/opt/ibm/java/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
# Mon, 27 Nov 2017 19:02:53 GMT
RUN apk add --no-cache curl tar bash
# Mon, 27 Nov 2017 19:02:56 GMT
ARG MAVEN_VERSION=3.5.2
# Mon, 27 Nov 2017 19:02:56 GMT
ARG USER_HOME_DIR=/root
# Mon, 27 Nov 2017 19:02:56 GMT
ARG SHA=707b1f6e390a65bde4af4cdaf2a24d45fc19a6ded00fff02e91626e3e42ceaff
# Mon, 27 Nov 2017 19:02:56 GMT
ARG BASE_URL=https://apache.osuosl.org/maven/maven-3/3.5.2/binaries
# Mon, 27 Nov 2017 19:02:58 GMT
# ARGS: BASE_URL=https://apache.osuosl.org/maven/maven-3/3.5.2/binaries MAVEN_VERSION=3.5.2 SHA=707b1f6e390a65bde4af4cdaf2a24d45fc19a6ded00fff02e91626e3e42ceaff USER_HOME_DIR=/root
RUN mkdir -p /usr/share/maven /usr/share/maven/ref   && curl -fsSL -o /tmp/apache-maven.tar.gz ${BASE_URL}/apache-maven-${MAVEN_VERSION}-bin.tar.gz   && echo "${SHA}  /tmp/apache-maven.tar.gz" | sha256sum -c -   && tar -xzf /tmp/apache-maven.tar.gz -C /usr/share/maven --strip-components=1   && rm -f /tmp/apache-maven.tar.gz   && ln -s /usr/share/maven/bin/mvn /usr/bin/mvn
# Mon, 27 Nov 2017 19:02:58 GMT
ENV MAVEN_HOME=/usr/share/maven
# Mon, 27 Nov 2017 19:02:58 GMT
ENV MAVEN_CONFIG=/root/.m2
# Mon, 27 Nov 2017 19:02:58 GMT
COPY file:e4099db07053a2301f4263d416cab324c1f89ee74c752bebec511d8b59464cb6 in /usr/local/bin/mvn-entrypoint.sh 
# Mon, 27 Nov 2017 19:03:03 GMT
COPY file:b3fc14e8337e0079a4e97eace880b4b7cddc0dc0ea733de80749f78fe1eb089a in /usr/share/maven/ref/ 
# Mon, 27 Nov 2017 19:03:03 GMT
VOLUME [/root/.m2]
# Mon, 27 Nov 2017 19:03:03 GMT
ENTRYPOINT ["/usr/local/bin/mvn-entrypoint.sh"]
# Mon, 27 Nov 2017 19:03:03 GMT
CMD ["mvn"]
```

-	Layers:
	-	`sha256:b56ae66c29370df48e7377c8f9baa744a3958058a766793f821dadcb144a4647`  
		Last Modified: Wed, 25 Oct 2017 23:21:25 GMT  
		Size: 2.0 MB (1991435 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:7222bb1538830b679053ac0a9e332179d6e0c472d9dc9bf48c846b6e91e2e751`  
		Last Modified: Sat, 04 Nov 2017 04:26:00 GMT  
		Size: 4.5 MB (4526455 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:c4e9d09242b1a4f4ea3d44aa580e24b12075507996f981fbced999c9067f9fc7`  
		Last Modified: Mon, 27 Nov 2017 18:45:42 GMT  
		Size: 161.9 MB (161884288 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:f667b1c9c96ad444fb124c9e40bb440aff8c89ea37ef74b5d8aa20279a1d7cf0`  
		Last Modified: Mon, 27 Nov 2017 19:03:48 GMT  
		Size: 1.8 MB (1750809 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:bd8068065985ec87029668d79724d24a2e80bed42afdb6c1ad3fc9866368761b`  
		Last Modified: Mon, 27 Nov 2017 19:03:49 GMT  
		Size: 8.9 MB (8883852 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:eee34af595143e95195f119b6fdcc301fdd9246d7cc83403c84104049d246c19`  
		Last Modified: Mon, 27 Nov 2017 19:03:47 GMT  
		Size: 734.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:dad7c6b6cfa7d740ac86cab961cafb2c162caf5a9547ec61eaa599e911cb95f8`  
		Last Modified: Mon, 27 Nov 2017 19:03:47 GMT  
		Size: 351.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
