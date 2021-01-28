```
docker build . -t islamicnetwork/php:8.0-cli --build-arg PHP_VERSION=8.0 -f Dockerfile.cli
docker build . -t islamicnetwork/php:8.0-apache --build-arg PHP_VERSION=8.0 -f Dockerfile.apache
docker build . -t islamicnetwork/php:8.0-apache-dev --build-arg PHP_VERSION=8.0 -f Dockerfile.apache.dev
```

