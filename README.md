# README

Small, powerful, scalable web/proxy server

## Usage

```sh
docker run \
    --init \
    --interactive \
    --publish 80:80 \
    --rm \
    --tty \
    timonier/nginx
```

## Contributing

1. Fork it.
2. Create your branch: `git checkout -b my-new-feature`.
3. Commit your changes: `git commit -am 'Add some feature'`.
4. Push to the branch: `git push origin my-new-feature`.
5. Submit a pull request.

__Note__: Use the script `bin/build` to test your modifications locally.

## Links

* [image "timonier/nginx"](https://hub.docker.com/r/timonier/nginx/)
* [nginx](https://nginx.org/)
