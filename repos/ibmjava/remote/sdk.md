## `ibmjava:sdk`

```console
$ docker pull ibmjava@sha256:93875bbdddd62b88d71f9123962ac6aa2a873bc8cb598e5f9475aa434cdfb6c8
```

-	Manifest MIME: `application/vnd.docker.distribution.manifest.list.v2+json`
-	Platforms:
	-	linux; amd64
	-	linux; 386
	-	linux; ppc64le
	-	linux; s390x

### `ibmjava:sdk` - linux; amd64

```console
$ docker pull ibmjava@sha256:c9c00c0d4d490a82de53c152a994d53768ef628bb4fea4290305e7ecbb290f06
```

-	Docker Version: 17.06.2-ce
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **212.7 MB (212700508 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:7a59c87ca76a368ded8c16caf63f747b2c4555f4ca42e8d5963080fdcdc075aa`
-	Default Command: `["\/bin\/bash"]`

```dockerfile
# Fri, 17 Nov 2017 21:59:22 GMT
ADD file:280a445783f309c90ab928883d98e4326c1fbe19927c8a555da41bcb74c71a45 in / 
# Fri, 17 Nov 2017 21:59:22 GMT
RUN set -xe 		&& echo '#!/bin/sh' > /usr/sbin/policy-rc.d 	&& echo 'exit 101' >> /usr/sbin/policy-rc.d 	&& chmod +x /usr/sbin/policy-rc.d 		&& dpkg-divert --local --rename --add /sbin/initctl 	&& cp -a /usr/sbin/policy-rc.d /sbin/initctl 	&& sed -i 's/^exit.*/exit 0/' /sbin/initctl 		&& echo 'force-unsafe-io' > /etc/dpkg/dpkg.cfg.d/docker-apt-speedup 		&& echo 'DPkg::Post-Invoke { "rm -f /var/cache/apt/archives/*.deb /var/cache/apt/archives/partial/*.deb /var/cache/apt/*.bin || true"; };' > /etc/apt/apt.conf.d/docker-clean 	&& echo 'APT::Update::Post-Invoke { "rm -f /var/cache/apt/archives/*.deb /var/cache/apt/archives/partial/*.deb /var/cache/apt/*.bin || true"; };' >> /etc/apt/apt.conf.d/docker-clean 	&& echo 'Dir::Cache::pkgcache ""; Dir::Cache::srcpkgcache "";' >> /etc/apt/apt.conf.d/docker-clean 		&& echo 'Acquire::Languages "none";' > /etc/apt/apt.conf.d/docker-no-languages 		&& echo 'Acquire::GzipIndexes "true"; Acquire::CompressionTypes::Order:: "gz";' > /etc/apt/apt.conf.d/docker-gzip-indexes 		&& echo 'Apt::AutoRemove::SuggestsImportant "false";' > /etc/apt/apt.conf.d/docker-autoremove-suggests
# Fri, 17 Nov 2017 21:59:23 GMT
RUN rm -rf /var/lib/apt/lists/*
# Fri, 17 Nov 2017 21:59:24 GMT
RUN sed -i 's/^#\s*\(deb.*universe\)$/\1/g' /etc/apt/sources.list
# Fri, 17 Nov 2017 21:59:24 GMT
RUN mkdir -p /run/systemd && echo 'docker' > /run/systemd/container
# Fri, 17 Nov 2017 21:59:25 GMT
CMD ["/bin/bash"]
# Fri, 17 Nov 2017 22:54:43 GMT
MAINTAINER Dinakar Guniguntala <dinakar.g@in.ibm.com> (@dinogun)
# Fri, 17 Nov 2017 22:54:55 GMT
RUN apt-get update     && apt-get install -y --no-install-recommends wget ca-certificates     && rm -rf /var/lib/apt/lists/*
# Mon, 27 Nov 2017 18:38:28 GMT
ENV JAVA_VERSION=1.8.0_sr5fp5
# Mon, 27 Nov 2017 18:41:43 GMT
RUN set -eux;     ARCH="$(dpkg --print-architecture)";     case "${ARCH}" in        amd64|x86_64)          ESUM='5989bd22deb8147fb14f5ef0b225c3514331eee82b8bd43a43688927b3867db0';          YML_FILE='sdk/linux/x86_64/index.yml';          ;;        i386)          ESUM='95f6c61db9581255f708988d1fc13df46a53561c3a4eb78ac0440b06b9680fab';          YML_FILE='sdk/linux/i386/index.yml';          ;;        ppc64el|ppc64le)          ESUM='a635df7beafc8f318cab0630cfc0d2009051c095a755d27b0d617e9dee627807';          YML_FILE='sdk/linux/ppc64le/index.yml';          ;;        s390)          ESUM='facfa6623ac39e1c103e05c4b98638ab1ffd3dcd50f6347563691561f9a95383';          YML_FILE='sdk/linux/s390/index.yml';          ;;        s390x)          ESUM='1e0237eeaa96c168f5ce54fcbddbb949e4654f31d2a5f60314ee06dca98fc6bd';          YML_FILE='sdk/linux/s390x/index.yml';          ;;        *)          echo "Unsupported arch: ${ARCH}";          exit 1;          ;;     esac;     BASE_URL="https://public.dhe.ibm.com/ibmdl/export/pub/systems/cloud/runtimes/java/meta/";     wget -q -U UA_IBM_JAVA_Docker -O /tmp/index.yml ${BASE_URL}/${YML_FILE};     JAVA_URL=$(cat /tmp/index.yml | sed -n '/'${JAVA_VERSION}'/{n;p}' | sed -n 's/\s*uri:\s//p' | tr -d '\r');     wget -q -U UA_IBM_JAVA_Docker -O /tmp/ibm-java.bin ${JAVA_URL};     echo "${ESUM}  /tmp/ibm-java.bin" | sha256sum -c -;     echo "INSTALLER_UI=silent" > /tmp/response.properties;     echo "USER_INSTALL_DIR=/opt/ibm/java" >> /tmp/response.properties;     echo "LICENSE_ACCEPTED=TRUE" >> /tmp/response.properties;     mkdir -p /opt/ibm;     chmod +x /tmp/ibm-java.bin;     /tmp/ibm-java.bin -i silent -f /tmp/response.properties;     rm -f /tmp/response.properties;     rm -f /tmp/index.yml;     rm -f /tmp/ibm-java.bin;     cd /opt/ibm/java/jre/lib;     rm -rf icc;
# Mon, 27 Nov 2017 18:41:44 GMT
ENV JAVA_HOME=/opt/ibm/java/jre PATH=/opt/ibm/java/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
```

-	Layers:
	-	`sha256:660c48dd555dcbfdfe19c80a30f557ac57a15f595250e67bfad1e5663c1725bb`  
		Last Modified: Fri, 17 Nov 2017 22:01:36 GMT  
		Size: 47.8 MB (47759720 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:4c7380416e7816a5ab1f840482c9c3ca8de58c6f3ee7f95e55ad299abbfe599f`  
		Last Modified: Fri, 17 Nov 2017 22:01:29 GMT  
		Size: 846.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:421e436b5f80d876128b74139531693be9b4e59e4f1081c9a3c379c95094e375`  
		Last Modified: Fri, 17 Nov 2017 22:01:29 GMT  
		Size: 620.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:e4ce6c3651b3a090bb43688f512f687ea6e3e533132bcbc4a83fb97e7046cea3`  
		Last Modified: Fri, 17 Nov 2017 22:01:29 GMT  
		Size: 849.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:be588e74bd348ce48bb7161350f4b9d783c331f37a853a80b0b4abc0a33c569e`  
		Last Modified: Fri, 17 Nov 2017 22:01:29 GMT  
		Size: 169.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:6da4611cbdb35a7b7d50ab0e09e97c9a5bdc6ce1656a01fb0765f61439677adc`  
		Last Modified: Fri, 17 Nov 2017 23:02:27 GMT  
		Size: 3.0 MB (3020945 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:f472b4628607772af6b675ca915787c24b453dc80557532e3a37d8c450a0454b`  
		Last Modified: Mon, 27 Nov 2017 18:45:07 GMT  
		Size: 161.9 MB (161917359 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip

### `ibmjava:sdk` - linux; 386

```console
$ docker pull ibmjava@sha256:72a943c350a464b02968cee895d368e122403b5a7d3ce9efa0004030026794f8
```

-	Docker Version: 17.06.2-ce
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **201.5 MB (201485113 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:78907d921880e19e5a7d401b50a5128708a38a42dcf200cb3f7e4800d32baa4f`
-	Default Command: `["\/bin\/bash"]`

```dockerfile
# Fri, 17 Nov 2017 22:51:30 GMT
ADD file:9568289c0621d85725d9ec76f81ff82cd74d503bd00c810a4f2995a2140bf472 in / 
# Fri, 17 Nov 2017 22:51:31 GMT
RUN set -xe 		&& echo '#!/bin/sh' > /usr/sbin/policy-rc.d 	&& echo 'exit 101' >> /usr/sbin/policy-rc.d 	&& chmod +x /usr/sbin/policy-rc.d 		&& dpkg-divert --local --rename --add /sbin/initctl 	&& cp -a /usr/sbin/policy-rc.d /sbin/initctl 	&& sed -i 's/^exit.*/exit 0/' /sbin/initctl 		&& echo 'force-unsafe-io' > /etc/dpkg/dpkg.cfg.d/docker-apt-speedup 		&& echo 'DPkg::Post-Invoke { "rm -f /var/cache/apt/archives/*.deb /var/cache/apt/archives/partial/*.deb /var/cache/apt/*.bin || true"; };' > /etc/apt/apt.conf.d/docker-clean 	&& echo 'APT::Update::Post-Invoke { "rm -f /var/cache/apt/archives/*.deb /var/cache/apt/archives/partial/*.deb /var/cache/apt/*.bin || true"; };' >> /etc/apt/apt.conf.d/docker-clean 	&& echo 'Dir::Cache::pkgcache ""; Dir::Cache::srcpkgcache "";' >> /etc/apt/apt.conf.d/docker-clean 		&& echo 'Acquire::Languages "none";' > /etc/apt/apt.conf.d/docker-no-languages 		&& echo 'Acquire::GzipIndexes "true"; Acquire::CompressionTypes::Order:: "gz";' > /etc/apt/apt.conf.d/docker-gzip-indexes 		&& echo 'Apt::AutoRemove::SuggestsImportant "false";' > /etc/apt/apt.conf.d/docker-autoremove-suggests
# Fri, 17 Nov 2017 22:51:32 GMT
RUN rm -rf /var/lib/apt/lists/*
# Fri, 17 Nov 2017 22:51:32 GMT
RUN sed -i 's/^#\s*\(deb.*universe\)$/\1/g' /etc/apt/sources.list
# Fri, 17 Nov 2017 22:51:33 GMT
RUN mkdir -p /run/systemd && echo 'docker' > /run/systemd/container
# Fri, 17 Nov 2017 22:51:33 GMT
CMD ["/bin/bash"]
# Fri, 17 Nov 2017 23:15:15 GMT
MAINTAINER Dinakar Guniguntala <dinakar.g@in.ibm.com> (@dinogun)
# Fri, 17 Nov 2017 23:15:27 GMT
RUN apt-get update     && apt-get install -y --no-install-recommends wget ca-certificates     && rm -rf /var/lib/apt/lists/*
# Tue, 28 Nov 2017 14:33:33 GMT
ENV JAVA_VERSION=1.8.0_sr5fp5
# Tue, 28 Nov 2017 14:41:01 GMT
RUN set -eux;     ARCH="$(dpkg --print-architecture)";     case "${ARCH}" in        amd64|x86_64)          ESUM='5989bd22deb8147fb14f5ef0b225c3514331eee82b8bd43a43688927b3867db0';          YML_FILE='sdk/linux/x86_64/index.yml';          ;;        i386)          ESUM='95f6c61db9581255f708988d1fc13df46a53561c3a4eb78ac0440b06b9680fab';          YML_FILE='sdk/linux/i386/index.yml';          ;;        ppc64el|ppc64le)          ESUM='a635df7beafc8f318cab0630cfc0d2009051c095a755d27b0d617e9dee627807';          YML_FILE='sdk/linux/ppc64le/index.yml';          ;;        s390)          ESUM='facfa6623ac39e1c103e05c4b98638ab1ffd3dcd50f6347563691561f9a95383';          YML_FILE='sdk/linux/s390/index.yml';          ;;        s390x)          ESUM='1e0237eeaa96c168f5ce54fcbddbb949e4654f31d2a5f60314ee06dca98fc6bd';          YML_FILE='sdk/linux/s390x/index.yml';          ;;        *)          echo "Unsupported arch: ${ARCH}";          exit 1;          ;;     esac;     BASE_URL="https://public.dhe.ibm.com/ibmdl/export/pub/systems/cloud/runtimes/java/meta/";     wget -q -U UA_IBM_JAVA_Docker -O /tmp/index.yml ${BASE_URL}/${YML_FILE};     JAVA_URL=$(cat /tmp/index.yml | sed -n '/'${JAVA_VERSION}'/{n;p}' | sed -n 's/\s*uri:\s//p' | tr -d '\r');     wget -q -U UA_IBM_JAVA_Docker -O /tmp/ibm-java.bin ${JAVA_URL};     echo "${ESUM}  /tmp/ibm-java.bin" | sha256sum -c -;     echo "INSTALLER_UI=silent" > /tmp/response.properties;     echo "USER_INSTALL_DIR=/opt/ibm/java" >> /tmp/response.properties;     echo "LICENSE_ACCEPTED=TRUE" >> /tmp/response.properties;     mkdir -p /opt/ibm;     chmod +x /tmp/ibm-java.bin;     /tmp/ibm-java.bin -i silent -f /tmp/response.properties;     rm -f /tmp/response.properties;     rm -f /tmp/index.yml;     rm -f /tmp/ibm-java.bin;     cd /opt/ibm/java/jre/lib;     rm -rf icc;
# Tue, 28 Nov 2017 14:41:01 GMT
ENV JAVA_HOME=/opt/ibm/java/jre PATH=/opt/ibm/java/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
```

-	Layers:
	-	`sha256:3d848dba019041e0794611dec2d82312dfc538f953f9f3e87151786b8d37d05a`  
		Last Modified: Fri, 17 Nov 2017 22:57:51 GMT  
		Size: 48.0 MB (47985638 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:4c64dd2e73bc201c0f7ba39f4c3ee8664a02a4a13f953ac03c05e4c5058580f1`  
		Last Modified: Fri, 17 Nov 2017 22:57:38 GMT  
		Size: 853.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:523332a0298bc7026601255ecb9a16ef6b6b8fb4ceb8904770476bcfd1a864f6`  
		Last Modified: Fri, 17 Nov 2017 22:57:39 GMT  
		Size: 583.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:37b996445e8d0352cb06cb47ebc7c965b74ecfc8d009ae03fc93c6ec9af2178a`  
		Last Modified: Fri, 17 Nov 2017 22:57:38 GMT  
		Size: 849.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:20bfa0c827cc7b5dd0854d74e314b8dc07bda7cb93d618198ddfcf9192aede8c`  
		Last Modified: Fri, 17 Nov 2017 22:57:39 GMT  
		Size: 169.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:241eaaceb0115f292cc5a6981c7aebd59186675ddd1e4ac1e85c896a087508cf`  
		Last Modified: Fri, 17 Nov 2017 23:31:16 GMT  
		Size: 2.9 MB (2877123 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:0bf6ef1d9eac0a56e94d19f819d7122d97aa2607a9f379f655a2886f1b37bf69`  
		Last Modified: Tue, 28 Nov 2017 14:49:46 GMT  
		Size: 150.6 MB (150619898 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip

### `ibmjava:sdk` - linux; ppc64le

```console
$ docker pull ibmjava@sha256:fa3e7ae30146b22f81f93f48e0d9b4a6cf35f74858dd7bc1f75adbd211418522
```

-	Docker Version: 17.06.2-ce
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **228.2 MB (228222141 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:ea866893deee38bbd0d039c97abff6e4ee471f9a6151a4f491e4a1199c2a4013`
-	Default Command: `["\/bin\/bash"]`

```dockerfile
# Fri, 17 Nov 2017 22:09:45 GMT
ADD file:392e323a73965750d9189d716d79fb80d688920977f201027a917643672a68a3 in / 
# Fri, 17 Nov 2017 22:09:49 GMT
RUN set -xe 		&& echo '#!/bin/sh' > /usr/sbin/policy-rc.d 	&& echo 'exit 101' >> /usr/sbin/policy-rc.d 	&& chmod +x /usr/sbin/policy-rc.d 		&& dpkg-divert --local --rename --add /sbin/initctl 	&& cp -a /usr/sbin/policy-rc.d /sbin/initctl 	&& sed -i 's/^exit.*/exit 0/' /sbin/initctl 		&& echo 'force-unsafe-io' > /etc/dpkg/dpkg.cfg.d/docker-apt-speedup 		&& echo 'DPkg::Post-Invoke { "rm -f /var/cache/apt/archives/*.deb /var/cache/apt/archives/partial/*.deb /var/cache/apt/*.bin || true"; };' > /etc/apt/apt.conf.d/docker-clean 	&& echo 'APT::Update::Post-Invoke { "rm -f /var/cache/apt/archives/*.deb /var/cache/apt/archives/partial/*.deb /var/cache/apt/*.bin || true"; };' >> /etc/apt/apt.conf.d/docker-clean 	&& echo 'Dir::Cache::pkgcache ""; Dir::Cache::srcpkgcache "";' >> /etc/apt/apt.conf.d/docker-clean 		&& echo 'Acquire::Languages "none";' > /etc/apt/apt.conf.d/docker-no-languages 		&& echo 'Acquire::GzipIndexes "true"; Acquire::CompressionTypes::Order:: "gz";' > /etc/apt/apt.conf.d/docker-gzip-indexes 		&& echo 'Apt::AutoRemove::SuggestsImportant "false";' > /etc/apt/apt.conf.d/docker-autoremove-suggests
# Fri, 17 Nov 2017 22:09:52 GMT
RUN rm -rf /var/lib/apt/lists/*
# Fri, 17 Nov 2017 22:09:57 GMT
RUN sed -i 's/^#\s*\(deb.*universe\)$/\1/g' /etc/apt/sources.list
# Fri, 17 Nov 2017 22:10:00 GMT
RUN mkdir -p /run/systemd && echo 'docker' > /run/systemd/container
# Fri, 17 Nov 2017 22:10:01 GMT
CMD ["/bin/bash"]
# Fri, 17 Nov 2017 22:28:51 GMT
MAINTAINER Dinakar Guniguntala <dinakar.g@in.ibm.com> (@dinogun)
# Fri, 17 Nov 2017 22:29:28 GMT
RUN apt-get update     && apt-get install -y --no-install-recommends wget ca-certificates     && rm -rf /var/lib/apt/lists/*
# Tue, 28 Nov 2017 16:23:21 GMT
ENV JAVA_VERSION=1.8.0_sr5fp5
# Tue, 28 Nov 2017 16:29:44 GMT
RUN set -eux;     ARCH="$(dpkg --print-architecture)";     case "${ARCH}" in        amd64|x86_64)          ESUM='5989bd22deb8147fb14f5ef0b225c3514331eee82b8bd43a43688927b3867db0';          YML_FILE='sdk/linux/x86_64/index.yml';          ;;        i386)          ESUM='95f6c61db9581255f708988d1fc13df46a53561c3a4eb78ac0440b06b9680fab';          YML_FILE='sdk/linux/i386/index.yml';          ;;        ppc64el|ppc64le)          ESUM='a635df7beafc8f318cab0630cfc0d2009051c095a755d27b0d617e9dee627807';          YML_FILE='sdk/linux/ppc64le/index.yml';          ;;        s390)          ESUM='facfa6623ac39e1c103e05c4b98638ab1ffd3dcd50f6347563691561f9a95383';          YML_FILE='sdk/linux/s390/index.yml';          ;;        s390x)          ESUM='1e0237eeaa96c168f5ce54fcbddbb949e4654f31d2a5f60314ee06dca98fc6bd';          YML_FILE='sdk/linux/s390x/index.yml';          ;;        *)          echo "Unsupported arch: ${ARCH}";          exit 1;          ;;     esac;     BASE_URL="https://public.dhe.ibm.com/ibmdl/export/pub/systems/cloud/runtimes/java/meta/";     wget -q -U UA_IBM_JAVA_Docker -O /tmp/index.yml ${BASE_URL}/${YML_FILE};     JAVA_URL=$(cat /tmp/index.yml | sed -n '/'${JAVA_VERSION}'/{n;p}' | sed -n 's/\s*uri:\s//p' | tr -d '\r');     wget -q -U UA_IBM_JAVA_Docker -O /tmp/ibm-java.bin ${JAVA_URL};     echo "${ESUM}  /tmp/ibm-java.bin" | sha256sum -c -;     echo "INSTALLER_UI=silent" > /tmp/response.properties;     echo "USER_INSTALL_DIR=/opt/ibm/java" >> /tmp/response.properties;     echo "LICENSE_ACCEPTED=TRUE" >> /tmp/response.properties;     mkdir -p /opt/ibm;     chmod +x /tmp/ibm-java.bin;     /tmp/ibm-java.bin -i silent -f /tmp/response.properties;     rm -f /tmp/response.properties;     rm -f /tmp/index.yml;     rm -f /tmp/ibm-java.bin;     cd /opt/ibm/java/jre/lib;     rm -rf icc;
# Tue, 28 Nov 2017 16:29:45 GMT
ENV JAVA_HOME=/opt/ibm/java/jre PATH=/opt/ibm/java/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
```

-	Layers:
	-	`sha256:275cfb52349b54241f21ad678f1d4ac09f272703b5c14b0dc7b1462f938eb3dc`  
		Last Modified: Fri, 17 Nov 2017 22:12:47 GMT  
		Size: 49.7 MB (49719729 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:befb9c5f1f0c8cef24366df7015d606758a8100bb4d7875e33f912abe6e4c1e8`  
		Last Modified: Fri, 17 Nov 2017 22:12:34 GMT  
		Size: 850.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:d44f79a867b8828a6e81e7b80a0771b8386d74ab44a60b69dd9c1d4a6ed1f076`  
		Last Modified: Fri, 17 Nov 2017 22:12:35 GMT  
		Size: 647.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:717848f4cefe5308aaf4936d634c0bde4e23406fbe32cf9ba61217645bdcc6d3`  
		Last Modified: Fri, 17 Nov 2017 22:12:34 GMT  
		Size: 855.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:87feb5fb9fd99d95d01c1ed12dfad1c72d3114cf533c775c8773993885387bef`  
		Last Modified: Fri, 17 Nov 2017 22:12:34 GMT  
		Size: 169.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:f999661d1e0a6fb684415ff115cfb6ee4c305f6432c0ddb261d2395899ded841`  
		Last Modified: Fri, 17 Nov 2017 22:43:04 GMT  
		Size: 2.9 MB (2878072 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:50a890d858c2fdcddb08ea4590f5dbfff744b9fd9ed0d1ce415e62830c632137`  
		Last Modified: Tue, 28 Nov 2017 16:31:37 GMT  
		Size: 175.6 MB (175621819 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip

### `ibmjava:sdk` - linux; s390x

```console
$ docker pull ibmjava@sha256:35e93d714b24642e8db213f66a3b3c1b885c019bbc8dccc64e0fb17e9861e918
```

-	Docker Version: 17.06.1-ce
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **203.8 MB (203756139 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:2796fe9dadea7f1049483cf82348a5e64ed16698e88e38f80c689fdc4acd4e9c`
-	Default Command: `["\/bin\/bash"]`

```dockerfile
# Fri, 17 Nov 2017 22:08:02 GMT
ADD file:0d75a1a112d5c06900f4081c4a778cb5e4a2765b5873a3bf0b379766f6b0e9a0 in / 
# Fri, 17 Nov 2017 22:08:03 GMT
RUN set -xe 		&& echo '#!/bin/sh' > /usr/sbin/policy-rc.d 	&& echo 'exit 101' >> /usr/sbin/policy-rc.d 	&& chmod +x /usr/sbin/policy-rc.d 		&& dpkg-divert --local --rename --add /sbin/initctl 	&& cp -a /usr/sbin/policy-rc.d /sbin/initctl 	&& sed -i 's/^exit.*/exit 0/' /sbin/initctl 		&& echo 'force-unsafe-io' > /etc/dpkg/dpkg.cfg.d/docker-apt-speedup 		&& echo 'DPkg::Post-Invoke { "rm -f /var/cache/apt/archives/*.deb /var/cache/apt/archives/partial/*.deb /var/cache/apt/*.bin || true"; };' > /etc/apt/apt.conf.d/docker-clean 	&& echo 'APT::Update::Post-Invoke { "rm -f /var/cache/apt/archives/*.deb /var/cache/apt/archives/partial/*.deb /var/cache/apt/*.bin || true"; };' >> /etc/apt/apt.conf.d/docker-clean 	&& echo 'Dir::Cache::pkgcache ""; Dir::Cache::srcpkgcache "";' >> /etc/apt/apt.conf.d/docker-clean 		&& echo 'Acquire::Languages "none";' > /etc/apt/apt.conf.d/docker-no-languages 		&& echo 'Acquire::GzipIndexes "true"; Acquire::CompressionTypes::Order:: "gz";' > /etc/apt/apt.conf.d/docker-gzip-indexes 		&& echo 'Apt::AutoRemove::SuggestsImportant "false";' > /etc/apt/apt.conf.d/docker-autoremove-suggests
# Fri, 17 Nov 2017 22:08:03 GMT
RUN rm -rf /var/lib/apt/lists/*
# Fri, 17 Nov 2017 22:08:04 GMT
RUN sed -i 's/^#\s*\(deb.*universe\)$/\1/g' /etc/apt/sources.list
# Fri, 17 Nov 2017 22:08:04 GMT
RUN mkdir -p /run/systemd && echo 'docker' > /run/systemd/container
# Fri, 17 Nov 2017 22:08:04 GMT
CMD ["/bin/bash"]
# Fri, 17 Nov 2017 22:25:45 GMT
MAINTAINER Dinakar Guniguntala <dinakar.g@in.ibm.com> (@dinogun)
# Fri, 17 Nov 2017 22:25:53 GMT
RUN apt-get update     && apt-get install -y --no-install-recommends wget ca-certificates     && rm -rf /var/lib/apt/lists/*
# Tue, 28 Nov 2017 11:42:35 GMT
ENV JAVA_VERSION=1.8.0_sr5fp5
# Tue, 28 Nov 2017 11:44:46 GMT
RUN set -eux;     ARCH="$(dpkg --print-architecture)";     case "${ARCH}" in        amd64|x86_64)          ESUM='5989bd22deb8147fb14f5ef0b225c3514331eee82b8bd43a43688927b3867db0';          YML_FILE='sdk/linux/x86_64/index.yml';          ;;        i386)          ESUM='95f6c61db9581255f708988d1fc13df46a53561c3a4eb78ac0440b06b9680fab';          YML_FILE='sdk/linux/i386/index.yml';          ;;        ppc64el|ppc64le)          ESUM='a635df7beafc8f318cab0630cfc0d2009051c095a755d27b0d617e9dee627807';          YML_FILE='sdk/linux/ppc64le/index.yml';          ;;        s390)          ESUM='facfa6623ac39e1c103e05c4b98638ab1ffd3dcd50f6347563691561f9a95383';          YML_FILE='sdk/linux/s390/index.yml';          ;;        s390x)          ESUM='1e0237eeaa96c168f5ce54fcbddbb949e4654f31d2a5f60314ee06dca98fc6bd';          YML_FILE='sdk/linux/s390x/index.yml';          ;;        *)          echo "Unsupported arch: ${ARCH}";          exit 1;          ;;     esac;     BASE_URL="https://public.dhe.ibm.com/ibmdl/export/pub/systems/cloud/runtimes/java/meta/";     wget -q -U UA_IBM_JAVA_Docker -O /tmp/index.yml ${BASE_URL}/${YML_FILE};     JAVA_URL=$(cat /tmp/index.yml | sed -n '/'${JAVA_VERSION}'/{n;p}' | sed -n 's/\s*uri:\s//p' | tr -d '\r');     wget -q -U UA_IBM_JAVA_Docker -O /tmp/ibm-java.bin ${JAVA_URL};     echo "${ESUM}  /tmp/ibm-java.bin" | sha256sum -c -;     echo "INSTALLER_UI=silent" > /tmp/response.properties;     echo "USER_INSTALL_DIR=/opt/ibm/java" >> /tmp/response.properties;     echo "LICENSE_ACCEPTED=TRUE" >> /tmp/response.properties;     mkdir -p /opt/ibm;     chmod +x /tmp/ibm-java.bin;     /tmp/ibm-java.bin -i silent -f /tmp/response.properties;     rm -f /tmp/response.properties;     rm -f /tmp/index.yml;     rm -f /tmp/ibm-java.bin;     cd /opt/ibm/java/jre/lib;     rm -rf icc;
# Tue, 28 Nov 2017 11:44:47 GMT
ENV JAVA_HOME=/opt/ibm/java/jre PATH=/opt/ibm/java/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
```

-	Layers:
	-	`sha256:04bba6f6626b090990bcc7dbbecd1fe7fa001404fa9e2d86b538dea288d27b7e`  
		Last Modified: Fri, 17 Nov 2017 22:09:37 GMT  
		Size: 46.4 MB (46420553 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:eb360dc7c011c7c5bdff218629c9f72e12ded36e76ebdfd506a03257e74f9c2d`  
		Last Modified: Fri, 17 Nov 2017 22:09:28 GMT  
		Size: 846.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:d937301f048fa82e96871e32d3654b18b0cc883c421107927d29dd79549fa761`  
		Last Modified: Fri, 17 Nov 2017 22:09:28 GMT  
		Size: 618.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:d560dd7c61a1c77dbb4205d1df9c45479ff6bd1cf61d50d098a09122a45ea5d1`  
		Last Modified: Fri, 17 Nov 2017 22:09:28 GMT  
		Size: 852.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:84dcf3356243fb4ea3ce6793fb4ff924805a7fb5c3a88204de30042868765e50`  
		Last Modified: Fri, 17 Nov 2017 22:09:28 GMT  
		Size: 169.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:a67927f5e6f9b7d56b02bc875b79f5c1431aaaa1b5a5dc1e5cfeec13d468f382`  
		Last Modified: Fri, 17 Nov 2017 22:33:05 GMT  
		Size: 2.8 MB (2765446 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:2e5c1226dfc1a62bb34286a1380345521a9316e11dd9be73e6bc384c13540b97`  
		Last Modified: Tue, 28 Nov 2017 11:48:52 GMT  
		Size: 154.6 MB (154567655 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
