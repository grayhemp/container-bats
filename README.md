# container-bats

[![Build Status](https://travis-ci.org/grayhemp/container-bats.svg?branch=master)](https://travis-ci.org/grayhemp/container-bats)

A [Bats] testing framework image.

## Usage

```dockerfile
COPY --from=grayhemp/bats /usr/local /usr/local
```

For a build-time testing use the following in your test image

```dockerfile
COPY test /mnt/test
RUN bats /mnt/test
```

and build it to trigger the tests. Note that it might be beneficial
for immutable tests (like unit tests) due to caching.

For a run-time testing mount `/mnt/test` to the test image and use

```dockerfile
ENTRYPOINT bats
CMD /mnt/test
```

to invoke the tests when the container is started.

## Development

Relies on [grayhemp/container-build] for image build and push steps.

```bash
make
make push
```

[grayhemp/container-build]: https://github.com/grayhemp/container-build
[Bats]: https://github.com/bats-core/bats-core
