# README

Small, powerful, scalable web/proxy server

If you like / use this project, please let me known by adding a ★ on the [GitHub repository](https://github.com/timonier/nginx).

## Usage

```sh
docker run --interactive --publish 80:80 --rm --tty timonier/nginx
```

__Note__: By default `nginx` opens port `80`.

It is possible to change `UID` and / or `GID` of user `nginx` (user used to run `nginx`) with environment variables `NGINX_UID` and `NGINX_GID`:

```sh
docker run --env NGINX_GID=1005 --env NGINX_UID=1005 --interactive --publish 80:80 --rm --tty timonier/nginx
```

It is possible to run a container in `read-only` mode if you mount the following folders:
* `/etc` if you want to change `UID` or `GID` of user `nginx`.
* `/etc/nginx`, `/run`, `/tmp` and `/var/cache/nginx`.

__Note__: `/run`, `/tmp` and `/var/cache/nginx` can be mount as `tmpfs`. In that case, `/run` must have flag `exec`.

```sh
# If you do not want to change "UID" or "GID" of user "nginx"

docker run --interactive --publish 80:80 --read-only --rm --tmpfs /run:exec --tmpfs /tmp --tmpfs /var/cache/nginx --tty timonier/nginx

# If you want to change "UID" or "GID" of user "nginx"

docker run --env NGINX_GID=1005 --env NGINX_UID=1005 --interactive --publish 80:80 --read-only --rm --tmpfs /run:exec --tmpfs /tmp --tmpfs /var/cache/nginx --tty --volume /etc timonier/nginx
```

## Links

* [image "timonier/nginx"](https://hub.docker.com/r/timonier/nginx/)
* [just-containers/s6-overlay](https://github.com/just-containers/s6-overlay)
* [jwilder/dockerize](https://github.com/jwilder/dockerize)
* [nginx](https://nginx.org/)
* [timonier/nginx](https://github.com/timonier/nginx)
