Docker Resources
-

The goal of this project is to simplify the process of creating and 
updating base docker images to be used from within your projects.

https://hub.docker.com/explore


Building
-

Build all the docker images
```
ACCOUNT=dockerhub VERSION=stable make all
```

Output:

```
$ docker images
REPOSITORY                 TAG                 IMAGE ID            CREATED              SIZE
dockerhub/redis            stable              4db50e8084ff        About a minute ago   21.03 MB
dockerhub/php-fpm          stable              5dbbfdde4d7c        About a minute ago   57.61 MB
dockerhub/node             stable              495cf5ac0f56        About a minute ago   55.3 MB
dockerhub/nginx            stable              8e60e7087ea0        About a minute ago   54.23 MB
dockerhub/memcached        stable              93aadbd3e301        About a minute ago   6.546 MB
```

Build one or multiple docker files
```
ACCOUNT=dockerhub VERSION=stable make redis node
```


Pushing
-

Push all the docker images
```
ACCOUNT=dockerhub VERSION=stable make push
```

Push one or multiple docker images
```
ACCOUNT=dockerhub VERSION=stable make push_redis push_nginx
```



Cleaning Up
-

There are 2 ways to cleanup.

`make clean`: cleans only the build files saving the downloaded dockers

`make cleanall`: cleans everything, built files and downloaded dockers


Cleans up all the docker images
```
ACCOUNT=dockerhub VERSION=stable make clean

ACCOUNT=dockerhub VERSION=stable make cleanall
```

Output:

```
$ ACCOUNT=dockerhub VERSION=stable make clean
docker rmi dockerhub/memcached:stable
Untagged: dockerhub/memcached:stable
Deleted: sha256:93aadbd3e301d128a849ea45f17d2d65e38cc754a7cb888b1911386adaa07639
docker rmi dockerhub/nginx:stable
Untagged: dockerhub/nginx:stable
Deleted: sha256:8e60e7087ea08539e3036012f5c51a2832db870fe2b05f5c508bad086ebda169
Deleted: sha256:961d2a6d1954151a0701a0ad8b3d951990f24b496b0742742044a30bf9859ef8
Deleted: sha256:1acb3b1ca2156ebfb7e8e4b0b4e947d1868160b51e41df9988ebad7ddb4cb0be
docker rmi dockerhub/node:stable
Untagged: dockerhub/node:stable
Deleted: sha256:495cf5ac0f56d6c03c4c5b1f6efce3f3fe7e529c018d84a2ba9f937931c9a09d
docker rmi dockerhub/php-fpm:stable
Untagged: dockerhub/php-fpm:stable
Deleted: sha256:5dbbfdde4d7c1a0b16e51023a64d7f75fbb8fe5dccdab513c3f003b340d23282
docker rmi dockerhub/redis:stable
Untagged: dockerhub/redis:stable
Deleted: sha256:4db50e8084ff6e24705223b58772894f23ade8c24a466d2a8d3dcdf22d60918a
```

Clean single or multiple images
```
ACCOUNT=dockerhub VERSION=stable make clean_redis

ACCOUNT=dockerhub VERSION=stable make clean_redis clean_node

ACCOUNT=dockerhub VERSION=stable make cleanall_redis

ACCOUNT=dockerhub VERSION=stable make cleanall_redis cleanall_node
```



