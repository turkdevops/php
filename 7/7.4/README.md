```
docker build . -t islamicnetwork/php:7.4-cli --build-arg PHP_VERSION=7.4 -f Dockerfile.cli
docker build . -t islamicnetwork/php:7.4-apache --build-arg PHP_VERSION=7.4 -f Dockerfile.apache
docker build . -t islamicnetwork/php:7.4-apache-dev --build-arg PHP_VERSION=7.4 -f Dockerfile.apache.dev
```

