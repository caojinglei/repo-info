## `neurodebian:buster`

```console
$ docker pull neurodebian@sha256:3268c60ca7af9cce3a16bb5b5f39082142f8c887623ba73424ed1ea8051f9294
```

-	Manifest MIME: `application/vnd.docker.distribution.manifest.list.v2+json`
-	Platforms:
	-	linux; amd64

### `neurodebian:buster` - linux; amd64

```console
$ docker pull neurodebian@sha256:b9124e28d27e72e70bde9303c07d08b72c55dac3e1eeac31fee39c9876becd0a
```

-	Docker Version: 17.06.2-ce
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **57.5 MB (57522993 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:e8cd6123ef9f6a8512c4323f44f841b27909e12c434c6e4c5996420b64c19f11`
-	Default Command: `["bash"]`

```dockerfile
# Sat, 04 Nov 2017 05:19:49 GMT
ADD file:2ad6832b35851b2a96b581ef8ed45d25ac9de93d41289c5560c271fed9ba920e in / 
# Sat, 04 Nov 2017 05:19:49 GMT
CMD ["bash"]
# Sat, 04 Nov 2017 08:42:37 GMT
RUN set -x 	&& apt-get update 	&& { 		which gpg 		|| apt-get install -y --no-install-recommends gnupg 	; } 	&& { 		gpg --version | grep -q '^gpg (GnuPG) 1\.' 		|| apt-get install -y --no-install-recommends dirmngr 	; } 	&& rm -rf /var/lib/apt/lists/*
# Sat, 04 Nov 2017 08:42:40 GMT
RUN set -x 	&& export GNUPGHOME="$(mktemp -d)" 	&& gpg --keyserver ha.pool.sks-keyservers.net --recv-keys DD95CC430502E37EF840ACEEA5D32F012649A5A9 	&& gpg --export DD95CC430502E37EF840ACEEA5D32F012649A5A9 > /etc/apt/trusted.gpg.d/neurodebian.gpg 	&& rm -rf "$GNUPGHOME" 	&& apt-key list | grep neurodebian
# Sat, 04 Nov 2017 08:42:41 GMT
RUN { 	echo 'deb http://neuro.debian.net/debian buster main'; 	echo 'deb http://neuro.debian.net/debian data main'; 	echo '#deb-src http://neuro.debian.net/debian-devel buster main'; } > /etc/apt/sources.list.d/neurodebian.sources.list
```

-	Layers:
	-	`sha256:85800cfdb88adf2f09c8fa7b9007830b06b159216512a8073639d55ef65bef2d`  
		Last Modified: Mon, 09 Oct 2017 21:35:49 GMT  
		Size: 47.5 MB (47527292 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:a615d59fdb099e2c5dbd4ec774253008f01e8f68400c2a19efbe475ca24ed623`  
		Last Modified: Sat, 04 Nov 2017 08:46:04 GMT  
		Size: 10.0 MB (9992303 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:e06113edd07cefe46b2d3da5f2536a705d326fc2e1cbb1cbab0a948531a1b0ab`  
		Last Modified: Sat, 04 Nov 2017 08:46:03 GMT  
		Size: 3.2 KB (3152 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:8dd21098848368521a8f4feedd901cb67e028af0873450f7d02bf3b846f80657`  
		Last Modified: Sat, 04 Nov 2017 08:46:04 GMT  
		Size: 246.0 B  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
