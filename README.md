# docker image: alpinebase [Layer 1]

## Description



## Layout

Shared Users and Groups: `www-data:www-data`

Possible volumes and their purposes: 
`/run/<servname>[Owner:www-data:www-data,Temporary]` is for container-specific performance related pid, cache or tmp files.
`/etc/<servname>` is for container-shared service configuration files etc.
`/var/run/<servname>[Owner:www-data:www-data]` is for container-shared sock files etc.
`/var/log/<servname>[Owner:www-data:www-data]` is for container-shared log files etc.
`/var/www/<sitename>[Owner:www-data:www-data]` is for container-shared web application frontend source code and configurations.
`/var/opt/<appname>` is for container-shared web application backend source code and configurations.

# License
[Apache 2.0](https://www.tldrlegal.com/l/apache2)
