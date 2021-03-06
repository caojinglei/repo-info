## `nats-streaming:nanoserver`

```console
$ docker pull nats-streaming@sha256:5904192f765eecfcac60429346a7ececf0a62a6b3ba18369611812bf9ef8df5b
```

-	Manifest MIME: `application/vnd.docker.distribution.manifest.list.v2+json`
-	Platforms:
	-	windows version 10.0.14393.1884; amd64

### `nats-streaming:nanoserver` - windows version 10.0.14393.1884; amd64

```console
$ docker pull nats-streaming@sha256:78fdcc69f25db348188f21698ee48cf12ac90d24edd83734773ea09accee134c
```

-	Docker Version: 17.06.1-ee-2
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **403.9 MB (403851865 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:466c3b97e4ed477f64f9a3e6401f78416a78de5210719181aa2ff75e2be5ff42`
-	Default Command: `["nats-streaming-server","-m","8222"]`

```dockerfile
# Tue, 13 Dec 2016 10:47:17 GMT
RUN Apply image 10.0.14393.0
# Mon, 13 Nov 2017 21:41:41 GMT
RUN Install update 10.0.14393.1884
# Tue, 14 Nov 2017 23:32:04 GMT
RUN cmd /S /C #(nop)  ENV NATS_DOCKERIZED=1
# Tue, 14 Nov 2017 23:32:05 GMT
RUN cmd /S /C #(nop) WORKDIR C:\nats-streaming-server
# Tue, 14 Nov 2017 23:32:08 GMT
RUN cmd /S /C #(nop) COPY file:c656ebbfbb58cb37d445aa025a3f93117bfda2b77866533dfe567a67a4a71e01 in nats-streaming-server.exe 
# Tue, 14 Nov 2017 23:32:09 GMT
RUN cmd /S /C #(nop)  EXPOSE 4222/tcp 8222/tcp
# Tue, 14 Nov 2017 23:32:10 GMT
RUN cmd /S /C #(nop)  CMD ["nats-streaming-server" "-m" "8222"]
```

-	Layers:
	-	`sha256:bce2fbc256ea437a87dadac2f69aabd25bed4f56255549090056c1131fad0277`  
		Last Modified: Tue, 13 Dec 2016 10:47:17 GMT  
		Size: 252.7 MB (252691002 bytes)  
		MIME: application/vnd.docker.image.rootfs.foreign.diff.tar.gzip
	-	`sha256:53a0ccfb7e6fe326c54359c802287bbe5435ac269242e4883f85a1f305e1d0cb`  
		Last Modified: Mon, 13 Nov 2017 21:41:41 GMT  
		Size: 148.0 MB (147993264 bytes)  
		MIME: application/vnd.docker.image.rootfs.foreign.diff.tar.gzip
	-	`sha256:257e2c8165f44302fd8136185d3b740bd13c09d084394ed68443f2efd5008feb`  
		Last Modified: Tue, 14 Nov 2017 23:32:28 GMT  
		Size: 946.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:75409312506ae65421384287b63e8a43b5dc41b8d221bba08e89caa44311c04c`  
		Last Modified: Tue, 14 Nov 2017 23:32:29 GMT  
		Size: 1.2 KB (1170 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:8508a1759bea1cc8f00f526e7891d5003d15a450979563eda16f687e3abfe29b`  
		Last Modified: Tue, 14 Nov 2017 23:32:29 GMT  
		Size: 3.2 MB (3163710 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:8f99c7d2a42c1799d99489a497a86d651674d0fc6174bc35c85471a0921f0131`  
		Last Modified: Tue, 14 Nov 2017 23:32:27 GMT  
		Size: 951.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:8792e80aef9f8e6def16d177909c887e06d1a5301543ea9e3a457a05863361f8`  
		Last Modified: Tue, 14 Nov 2017 23:32:28 GMT  
		Size: 822.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
