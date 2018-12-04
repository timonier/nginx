# README

Small, powerful, scalable web/proxy server

## Usage

```sh
docker run --interactive --publish 80:80 --rm --tty timonier/nginx
```

## Contributing

1. Fork it.
2. Create your branch: `git checkout -b my-new-feature`.
3. Commit your changes: `git commit -am 'Add some feature'`.
4. Push to the branch: `git push origin my-new-feature`.
5. Submit a pull request.

__Note__: Use the script `bin/build-image` to test your modifications locally.

If you like / use this project, please let me known by adding a [★](https://help.github.com/articles/about-stars/) on the [GitHub repository](https://github.com/timonier/nginx).

## Links

* [image "timonier/nginx"](https://hub.docker.com/r/timonier/nginx/)
* [just-containers/s6-overlay](https://github.com/just-containers/s6-overlay)
* [jwilder/dockerize](https://github.com/jwilder/dockerize)
* [nginx](https://nginx.org/)
* [timonier/dumb-entrypoint](https://github.com/timonier/dumb-entrypoint)
