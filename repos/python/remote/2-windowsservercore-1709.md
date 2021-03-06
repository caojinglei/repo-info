## `python:2-windowsservercore-1709`

```console
$ docker pull python@sha256:9514b7f29cf1bd0ef92ea0d351964dd2d64e34ec36aafbe8eb432435c418a308
```

-	Manifest MIME: `application/vnd.docker.distribution.manifest.list.v2+json`
-	Platforms:
	-	windows version 10.0.16299.64; amd64

### `python:2-windowsservercore-1709` - windows version 10.0.16299.64; amd64

```console
$ docker pull python@sha256:2cb1789079e3fead4cb59e1ff808950730a3d2fcf8c3c064d1b4e7116f8c51c9
```

-	Docker Version: 17.06.1-ee-2
-	Manifest MIME: `application/vnd.docker.distribution.manifest.v2+json`
-	Total Size: **2.7 GB (2728738420 bytes)**  
	(compressed transfer size, not on-disk size)
-	Image ID: `sha256:8f441d204aa536ef512bb70212439730988ff9ba51c8323315bc5d92e4679348`
-	Default Command: `["python"]`
-	`SHELL`: `["powershell","-Command","$ErrorActionPreference = 'Stop'; $ProgressPreference = 'SilentlyContinue';"]`

```dockerfile
# Fri, 29 Sep 2017 14:43:28 GMT
RUN Apply image 10.0.16299.15
# Thu, 02 Nov 2017 14:03:00 GMT
RUN Install update 10.0.16299.64
# Thu, 23 Nov 2017 03:14:48 GMT
SHELL [powershell -Command $ErrorActionPreference = 'Stop'; $ProgressPreference = 'SilentlyContinue';]
# Thu, 23 Nov 2017 17:36:12 GMT
ENV PYTHON_VERSION=2.7.14
# Thu, 23 Nov 2017 17:36:13 GMT
ENV PYTHON_RELEASE=2.7.14
# Thu, 23 Nov 2017 17:37:58 GMT
RUN $url = ('https://www.python.org/ftp/python/{0}/python-{1}.amd64.msi' -f $env:PYTHON_RELEASE, $env:PYTHON_VERSION); 	Write-Host ('Downloading {0} ...' -f $url); 	Invoke-WebRequest -Uri $url -OutFile 'python.msi'; 		Write-Host 'Installing ...'; 	Start-Process msiexec -Wait 		-ArgumentList @( 			'/i', 			'python.msi', 			'/quiet', 			'/qn', 			'TARGETDIR=C:\Python', 			'ALLUSERS=1', 			'ADDLOCAL=DefaultFeature,Extensions,TclTk,Tools,PrependPath' 		); 		$env:PATH = [Environment]::GetEnvironmentVariable('PATH', [EnvironmentVariableTarget]::Machine); 		Write-Host 'Verifying install ...'; 	Write-Host '  python --version'; python --version; 		Write-Host 'Removing ...'; 	Remove-Item python.msi -Force; 		Write-Host 'Complete.';
# Thu, 23 Nov 2017 17:37:59 GMT
ENV PYTHON_PIP_VERSION=9.0.1
# Thu, 23 Nov 2017 17:39:09 GMT
RUN Write-Host ('Installing pip=={0} ...' -f $env:PYTHON_PIP_VERSION); 	[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; 	Invoke-WebRequest -Uri 'https://bootstrap.pypa.io/get-pip.py' -OutFile 'get-pip.py'; 	python get-pip.py 		--disable-pip-version-check 		--no-cache-dir 		('pip=={0}' -f $env:PYTHON_PIP_VERSION) 	; 	Remove-Item get-pip.py -Force; 		Write-Host 'Verifying pip install ...'; 	pip --version; 		Write-Host 'Complete.';
# Thu, 23 Nov 2017 17:39:57 GMT
RUN pip install --no-cache-dir virtualenv
# Thu, 23 Nov 2017 17:39:58 GMT
CMD ["python"]
```

-	Layers:
	-	`sha256:5847a47b8593f7c39aa5e3db09e50b76d42aa8898c0440c70cc9c69747d4c479`  
		Last Modified: Tue, 17 Oct 2017 15:51:05 GMT  
		Size: 2.3 GB (2274300585 bytes)  
		MIME: application/vnd.docker.image.rootfs.foreign.diff.tar.gzip
	-	`sha256:0e0a3062a7ac7e07eda6c54e1ddfafc80550c98dd5e1933799f934bc4bdcf0ab`  
		Last Modified: Tue, 14 Nov 2017 18:59:18 GMT  
		Size: 401.9 MB (401851142 bytes)  
		MIME: application/vnd.docker.image.rootfs.foreign.diff.tar.gzip
	-	`sha256:72ebc5a9d332e2a64fb3a65257e303100db8bcd07f6ccb562e3dc2e77f2cd3c5`  
		Last Modified: Thu, 23 Nov 2017 10:07:03 GMT  
		Size: 1.2 KB (1159 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:fd48c706ef9b305f71dce5fe7f2446ccc78e4c20d3d6352d7dab86ea968393c3`  
		Last Modified: Thu, 23 Nov 2017 17:42:19 GMT  
		Size: 1.2 KB (1187 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:2854caa76c6da380092c1c7b50f40d2bc052c2e65a00bccccda6b3d6e7764285`  
		Last Modified: Thu, 23 Nov 2017 17:42:19 GMT  
		Size: 1.2 KB (1192 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:00460713a026ee1bfa07708cb03a0e0d6c1261eb74937d760bde6c96e2991c07`  
		Last Modified: Thu, 23 Nov 2017 17:42:29 GMT  
		Size: 37.9 MB (37876619 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:611a256744bbd52437d2ac218e9aa33dbe225e0f40d861cee3d02e5343f114eb`  
		Last Modified: Thu, 23 Nov 2017 17:42:16 GMT  
		Size: 1.2 KB (1170 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:a0ff3a5ee94ba5c1c9de7c2d73eeaf5501c3e081e177c4eae48427e7a2ca7254`  
		Last Modified: Thu, 23 Nov 2017 17:42:22 GMT  
		Size: 8.5 MB (8476227 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:73065d63f4b18f0ab17d0ebe2eec21504e9282344e92e25b0a2e6879e017edc5`  
		Last Modified: Thu, 23 Nov 2017 17:42:19 GMT  
		Size: 6.2 MB (6227944 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
	-	`sha256:dee6da8a9d937d40fb6d173330845dc246e42100777904e7e3d718ee7476b4e0`  
		Last Modified: Thu, 23 Nov 2017 17:42:17 GMT  
		Size: 1.2 KB (1195 bytes)  
		MIME: application/vnd.docker.image.rootfs.diff.tar.gzip
