## `couchbase:latest`

```console
$ docker pull couchbase@sha256:f7a796aaf44ad49b5047c322d823d4032fd076972c00caba2ee3f5c812682847
```

-	Manifest MIME: `application/vnd.docker.distribution.manifest.list.v2+json`
-	Platforms:
	-	linux; amd64

### `couchbase:latest` - linux; amd64

```console
$ docker pull couchbase@sha256:418c3ec7e4d307985a3f65e1efa8d2409875010eda2e7a7de610d5b283ceca35
```

-	Docker Version: 17.06.2-ce
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **226.8 MB (226761560 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:b9a3a275e6630e2099c84a75a78b9f1e1a904ea9013a67b6a95d89ab02b49cde`
-	Entrypoint: `["\/entrypoint.sh"]`
-	Default Command: `["couchbase-server"]`

```dockerfile
# Fri, 17 Nov 2017 21:59:07 GMT
ADD file:f5013009a258adf002575679e2f6a2fbfe5fd61bf45179e2fb9864683874b2b2 in / 
# Fri, 17 Nov 2017 21:59:08 GMT
RUN set -xe 		&& echo '#!/bin/sh' > /usr/sbin/policy-rc.d 	&& echo 'exit 101' >> /usr/sbin/policy-rc.d 	&& chmod +x /usr/sbin/policy-rc.d 		&& dpkg-divert --local --rename --add /sbin/initctl 	&& cp -a /usr/sbin/policy-rc.d /sbin/initctl 	&& sed -i 's/^exit.*/exit 0/' /sbin/initctl 		&& echo 'force-unsafe-io' > /etc/dpkg/dpkg.cfg.d/docker-apt-speedup 		&& echo 'DPkg::Post-Invoke { "rm -f /var/cache/apt/archives/*.deb /var/cache/apt/archives/partial/*.deb /var/cache/apt/*.bin || true"; };' > /etc/apt/apt.conf.d/docker-clean 	&& echo 'APT::Update::Post-Invoke { "rm -f /var/cache/apt/archives/*.deb /var/cache/apt/archives/partial/*.deb /var/cache/apt/*.bin || true"; };' >> /etc/apt/apt.conf.d/docker-clean 	&& echo 'Dir::Cache::pkgcache ""; Dir::Cache::srcpkgcache "";' >> /etc/apt/apt.conf.d/docker-clean 		&& echo 'Acquire::Languages "none";' > /etc/apt/apt.conf.d/docker-no-languages 		&& echo 'Acquire::GzipIndexes "true"; Acquire::CompressionTypes::Order:: "gz";' > /etc/apt/apt.conf.d/docker-gzip-indexes 		&& echo 'Apt::AutoRemove::SuggestsImportant "false";' > /etc/apt/apt.conf.d/docker-autoremove-suggests
# Fri, 17 Nov 2017 21:59:08 GMT
RUN rm -rf /var/lib/apt/lists/*
# Fri, 17 Nov 2017 21:59:09 GMT
RUN sed -i 's/^#\s*\(deb.*universe\)$/\1/g' /etc/apt/sources.list
# Fri, 17 Nov 2017 21:59:10 GMT
RUN mkdir -p /run/systemd && echo 'docker' > /run/systemd/container
# Fri, 17 Nov 2017 21:59:10 GMT
CMD ["/bin/bash"]
# Sat, 18 Nov 2017 00:41:47 GMT
MAINTAINER Couchbase Docker Team <docker@couchbase.com>
# Sat, 18 Nov 2017 00:42:13 GMT
RUN apt-get update &&     apt-get install -yq runit wget python-httplib2 chrpath     lsof lshw sysstat net-tools numactl  &&     apt-get autoremove && apt-get clean &&     rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
# Sat, 18 Nov 2017 00:42:13 GMT
ARG CB_VERSION=5.0.0
# Sat, 18 Nov 2017 00:42:13 GMT
ARG CB_RELEASE_URL=http://packages.couchbase.com/releases
# Sat, 18 Nov 2017 00:42:14 GMT
ARG CB_PACKAGE=couchbase-server-enterprise_5.0.0-ubuntu14.04_amd64.deb
# Sat, 18 Nov 2017 00:42:14 GMT
ARG CB_SHA256=005130365956507ff14772cd8412aa8ff4793996bd88295e5bb684c625865c4e
# Sat, 18 Nov 2017 00:42:14 GMT
ENV PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/opt/couchbase/bin:/opt/couchbase/bin/tools:/opt/couchbase/bin/install
# Sat, 18 Nov 2017 00:42:15 GMT
# ARGS: CB_PACKAGE=couchbase-server-enterprise_5.0.0-ubuntu14.04_amd64.deb CB_RELEASE_URL=http://packages.couchbase.com/releases CB_SHA256=005130365956507ff14772cd8412aa8ff4793996bd88295e5bb684c625865c4e CB_VERSION=5.0.0
RUN groupadd -g 1000 couchbase && useradd couchbase -u 1000 -g couchbase -M
# Sat, 18 Nov 2017 00:42:31 GMT
# ARGS: CB_PACKAGE=couchbase-server-enterprise_5.0.0-ubuntu14.04_amd64.deb CB_RELEASE_URL=http://packages.couchbase.com/releases CB_SHA256=005130365956507ff14772cd8412aa8ff4793996bd88295e5bb684c625865c4e CB_VERSION=5.0.0
RUN wget -N $CB_RELEASE_URL/$CB_VERSION/$CB_PACKAGE &&     echo "$CB_SHA256  $CB_PACKAGE" | sha256sum -c - &&     dpkg -i ./$CB_PACKAGE && rm -f ./$CB_PACKAGE
# Sat, 18 Nov 2017 00:42:32 GMT
COPY file:f14849552c5fb3935cb7300d639612403e6af00af7528886bc07e8a778689a7e in /etc/service/couchbase-server/run 
# Sat, 18 Nov 2017 00:42:32 GMT
COPY file:8196fd8e201c5fc3873a0faa3cec28b0d85633e363c0c5788434f5b9a81cfa5b in /usr/local/bin/ 
# Sat, 18 Nov 2017 00:42:33 GMT
# ARGS: CB_PACKAGE=couchbase-server-enterprise_5.0.0-ubuntu14.04_amd64.deb CB_RELEASE_URL=http://packages.couchbase.com/releases CB_SHA256=005130365956507ff14772cd8412aa8ff4793996bd88295e5bb684c625865c4e CB_VERSION=5.0.0
RUN ln -s dummy.sh /usr/local/bin/iptables-save &&     ln -s dummy.sh /usr/local/bin/lvdisplay &&     ln -s dummy.sh /usr/local/bin/vgdisplay &&     ln -s dummy.sh /usr/local/bin/pvdisplay
# Sat, 18 Nov 2017 00:42:37 GMT
# ARGS: CB_PACKAGE=couchbase-server-enterprise_5.0.0-ubuntu14.04_amd64.deb CB_RELEASE_URL=http://packages.couchbase.com/releases CB_SHA256=005130365956507ff14772cd8412aa8ff4793996bd88295e5bb684c625865c4e CB_VERSION=5.0.0
RUN chrpath -r '$ORIGIN/../lib' /opt/couchbase/bin/curl
# Sat, 18 Nov 2017 00:42:38 GMT
COPY file:cc6a884f330c854d49f23323bc8c5cc1aa1b48965d4f0c7fe4d46a54871f866f in / 
# Sat, 18 Nov 2017 00:42:38 GMT
ENTRYPOINT ["/entrypoint.sh"]
# Sat, 18 Nov 2017 00:42:38 GMT
CMD ["couchbase-server"]
# Sat, 18 Nov 2017 00:42:38 GMT
EXPOSE 11207/tcp 11210/tcp 11211/tcp 18091/tcp 18092/tcp 18093/tcp 18094/tcp 8091/tcp 8092/tcp 8093/tcp 8094/tcp
# Sat, 18 Nov 2017 00:42:39 GMT
VOLUME [/opt/couchbase/var]
```

-	Layers:
	-	`sha256:01a4f83874576563b6cd843ab7c105d92ab000fe0cb114a645ba99e89b970b77`  
		Last Modified: Fri, 17 Nov 2017 22:01:08 GMT  
		Size: 72.8 MB (72825073 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:c887940e680c6729f0c52a833ea44ae2323e4611752bf248da7f0ed9dce573c9`  
		Last Modified: Fri, 17 Nov 2017 22:00:57 GMT  
		Size: 72.6 KB (72644 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:5432573ac160367250f315604a27532a28e12b6b25c8d8aff68d45533c52f8a7`  
		Last Modified: Fri, 17 Nov 2017 22:00:57 GMT  
		Size: 629.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:027ee9a9665e446b635a4874018e2685491914be7d8a3fb240dc80dc96af12c7`  
		Last Modified: Fri, 17 Nov 2017 22:00:57 GMT  
		Size: 852.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:5611db80430d159f886e5b556217e6b94bdbd08ec98862074fe6bec4a9d4253e`  
		Last Modified: Fri, 17 Nov 2017 22:00:57 GMT  
		Size: 163.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:32224e682759e32fc45f2a79617550f563d63ca3bfb4c6ecbb2447ad9cb5fe6c`  
		Last Modified: Sat, 18 Nov 2017 00:44:28 GMT  
		Size: 11.4 MB (11393015 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:a81a154b14902ce660827bb2ab12ebdcaf7bcd0ed257b4e4a038d518bb4ff8f7`  
		Last Modified: Sat, 18 Nov 2017 00:44:26 GMT  
		Size: 1.9 KB (1907 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:6a7bb7fa564b84b132eabfd14cb6508d84ef4e33f25a70700e70e3ea8cc21da6`  
		Last Modified: Sat, 18 Nov 2017 00:44:46 GMT  
		Size: 142.4 MB (142360789 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:80a4f9b7b3bc5e114a2f33990e7e8799566768074e8a8ed3aef7c05e212cfeab`  
		Last Modified: Sat, 18 Nov 2017 00:44:23 GMT  
		Size: 359.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:b642499a247af217c353f6e9d490410e451887546884fe3a55af9042a6275e1e`  
		Last Modified: Sat, 18 Nov 2017 00:44:24 GMT  
		Size: 235.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:b415fe61c50f6ecdeebe2bb45f9bad29a1644be2978e634f732152e512cd49e3`  
		Last Modified: Sat, 18 Nov 2017 00:44:23 GMT  
		Size: 218.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:378859087f78aad57d47e66e61af8fcbefd20b65dd48e2a72d2055db4905cd00`  
		Last Modified: Sat, 18 Nov 2017 00:44:24 GMT  
		Size: 105.4 KB (105402 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:0ba00a1cf4fe89182d61622cc768f44bf6a3408f2b86706d8c38a4375a50914c`  
		Last Modified: Sat, 18 Nov 2017 00:44:24 GMT  
		Size: 274.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
