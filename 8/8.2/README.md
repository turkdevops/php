```
docker build . -t islamicnetwork/php:8.2-cli --build-arg PHP_VERSION=8.2 -f Dockerfile.cli
docker build . -t islamicnetwork/php:8.2-apache --build-arg PHP_VERSION=8.2 -f Dockerfile.apache
docker build . -t islamicnetwork/php:8.2-apache-dev --build-arg PHP_VERSION=8.2 -f Dockerfile.apache.dev

docker tag islamicnetwork/php:8.2-cli quay.io/islamic-network/php:8.2-cli
docker tag islamicnetwork/php:8.2-apache quay.io/islamic-network/php:8.2-apache
docker tag islamicnetwork/php:8.2-apache-dev quay.io/islamic-network/php:8.2-apache-dev

docker push islamicnetwork/php:8.2-cli 
docker push quay.io/islamic-network/php:8.2-cli
docker push islamicnetwork/php:8.2-apache 
docker push quay.io/islamic-network/php:8.2-apache
docker push islamicnetwork/php:8.2-apache-dev
docker push quay.io/islamic-network/php:8.2-apache-dev
```


