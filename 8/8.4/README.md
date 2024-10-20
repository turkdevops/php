```
docker build . -t islamicnetwork/php:8.4-cli --build-arg PHP_VERSION=8.4 -f Dockerfile.cli
docker build . -t islamicnetwork/php:8.4-apache --build-arg PHP_VERSION=8.4 -f Dockerfile.apache
docker build . -t islamicnetwork/php:8.4-apache-dev --build-arg PHP_VERSION=8.4 -f Dockerfile.apache.dev

docker tag islamicnetwork/php:8.4-cli quay.io/islamic-network/php:8.4-cli
docker tag islamicnetwork/php:8.4-apache quay.io/islamic-network/php:8.4-apache
docker tag islamicnetwork/php:8.4-apache-dev quay.io/islamic-network/php:8.4-apache-dev

docker push islamicnetwork/php:8.4-cli 
docker push quay.io/islamic-network/php:8.4-cli
docker push islamicnetwork/php:8.4-apache 
docker push quay.io/islamic-network/php:8.4-apache
docker push islamicnetwork/php:8.4-apache-dev
docker push quay.io/islamic-network/php:8.4-apache-dev
```


