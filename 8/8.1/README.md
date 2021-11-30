```
docker build . -t islamicnetwork/php:8.1-cli --build-arg PHP_VERSION=8.1 -f Dockerfile.cli
docker build . -t islamicnetwork/php:8.1-apache --build-arg PHP_VERSION=8.1 -f Dockerfile.apache
docker build . -t islamicnetwork/php:8.1-apache-dev --build-arg PHP_VERSION=8.1 -f Dockerfile.apache.dev

docker tag islamicnetwork/php:8.1-cli quay.io/islamic-network/php:8.1-cli
docker tag islamicnetwork/php:8.1-apache quay.io/islamic-network/php:8.1-apache
docker tag islamicnetwork/php:8.1-apache-dev quay.io/islamic-network/php:8.1-apache-dev

docker push islamicnetwork/php:8.1-cli 
docker push quay.io/islamic-network/php:8.1-cli
docker push islamicnetwork/php:8.1-apache 
docker push quay.io/islamic-network/php:8.1-apache
docker push islamicnetwork/php:8.1-apache-dev
docker push quay.io/islamic-network/php:8.1-apache-dev
```


