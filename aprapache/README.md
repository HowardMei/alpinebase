# docker image: aprapache [Layer 4]

This layer 4 docker image is built upon [hwdm/aprunit image](https://hub.docker.com/r/hwdm/aprunit/) `latest` tag

## Description
This is the runit managed apache2 docker image.  

## Additions
Packages: `libressl apache2 etc...`

## Usage: 
	`sudo docker run --rm -it -p 80:80 hwdm/aprapache`
	Visit localhost and localhost/_svstatus

## Tags

* `latest` tracks the newest tag from [upstream](https://hub.docker.com/r/hwdm/aprunit/)
* `2425r0` indicates the apache2 version in the image, i.e, `2425r0=apache2 v2.4.25-r0`

# License
[Apache 2.0](https://www.tldrlegal.com/l/apache2)
