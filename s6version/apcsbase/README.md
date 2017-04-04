# docker image: apcsbase [Layer 4]

This layer 4 docker image is built upon [hwdm/aps6consul image](https://hub.docker.com/r/hwdm/aps6consul/) `latest` tag

## Description
This is the real base for many multi-proc docker images. Consul is for service registration.
Consul-Template is for configuration live update.  

## Additions
Packages: `consul-template`

## Tags

* `latest` tracks the newest tag from [upstream](https://hub.docker.com/r/hwdm/aps6consul/)
* `0181` indicates the consul-template version in the image, i.e, `0181=0.18.1`

# License
[Apache 2.0](https://www.tldrlegal.com/l/apache2)
