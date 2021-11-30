[![CircleCI](https://circleci.com/gh/islamic-network/php.svg?style=shield)](https://circleci.com/gh/islamic-network/php)
[![](https://img.shields.io/github/license/islamic-network/php.svg)](https://github.com/islamic-network/php/blob/master/LICENSE.txt)
![Docker Pulls](https://img.shields.io/docker/pulls/islamicnetwork/php)

# PHP Docker Images 

This repository produces PHP Images for the CLI and with Apache, ready for production use.

These are based on the official PHP Docker Images and run Debian.

They come pre-bundled with linux packages and PECLs used within the Islamic Network ecosystem. Whilst some may find the installation of many of these
packages on production containers controversial, it just makes resolving production issues easier, especially when you are not a 100 person team.
*These images are not for you if you only like to deploy 30 MB Alpine images in production.*

These images will work with OpenShift Online, Sloppy.io, any managed Kubernetes service or any other Docker hosts. 

## CLI Images
CLI Images are available on Docker Hub and Quay.io as:

* islamicnetwork/php:8.1-cli
* islamicnetwork/php:8.0-cli
* islamicnetwork/php:7.4-cli
* quay.io/islamic-network/php:8.1-cli
* quay.io/islamic-network/php:8.0-cli
* quay.io/islamic-network/php:7.4-cli


## Apache Images
Apache Images are available on Docker Hub and Quay.io as:

* islamicnetwork/php:8.1-apache
* islamicnetwork/php:8.0-apache
* islamicnetwork/php:7.4-apache
* quay.io/islamic-network/php:8.1-apache
* quay.io/islamic-network/php:8.0-apache
* quay.io/islamic-network/php:7.4-apache

The Apache document root in the container is /var/www/html and Apache is exposed on port 8080.

These images come with opcache enabled and no xdebug, so they cannot be used for development purposes.

## Apache Images for Development Purposes
Apache Images are available on Docker Hub and Quay.io and come bundled with xdebug. Opcache is disabled in these images.

* islamicnetwork/php:8.1-apache-dev
* islamicnetwork/php:8.0-apache-dev
* islamicnetwork/php:7.4-apache-dev
* quay.io/islamic-network/php:8.1-apache-dev
* quay.io/islamic-network/php:8.0-apache-dev
* quay.io/islamic-network/php:7.4-apache-dev

The Apache document root in the container is /var/www/html and Apache is exposed on port 8080.


## Using Docker Secrets
These new images no longer support converting Docker secrets into Environment Variables. If you are using PHP 7.4 and need to use Docker Secrets (if,
for instance, you are using Docker Swarm in a production environment), you can use the older images from https://github.com/islamic-network/php74.

## Important Information:

### Apache Settings

The container is setup by default to allow 150 Apache Request Workers. Knowing what this means is important when using this image for production applications.
You don't want to size your Docker container to where resources are either wasted or you end up swapping memory.
So, to tune this properly, for your running application, calculate the RAM needed for each request / process. Run the following where your app runs:
```
ps aux | grep 'apache2' | awk '{print $6/1024 " MB";}'
```

This will produce something like this:
```
18.1953 MB
15.2539 MB
15.4766 MB
15.3789 MB
15.3516 MB
15.3281 MB
15.3711 MB
15.3477 MB
0.6875 MB
```

This means your app is taking on average, 16-17 MB to serve a request. If you run WordPress or Drupal, this may be closer to 60 MB.

So, this would mean that to serve upto 150 requests, your container needs a maximum of 17 MB x 150 = 2550 + 100 MB opcache = 2650 MB of RAM.

Add another 200 MB as a safety net for any other processes. So, an image running this container should get no more than 2750 MB of RAM. Additional RAM will likely go unused.

Less RAM will result in usage of SWAP on disk if you hit more than 150 requests, which means it may take a few minutes for Apache to respond with extremely high CPU load.

If you expect more than 150 requests a second (or at one time) with a single instance, they will be queued. Alternatively, you can scale horizontally and deploy multiple instances.

You can also extend this container and overwrite these settings using your own Dockerfile. See, for instance, the Dockerfile in this project: https://github.com/islamic-network/alquran.cloud.

### PHP Modules and Extensions
 
The following modules / extensions / PECLs are enabled on this container (excluding XDebug which is only available in the :dev tag):

#### Extensions
* calendar
* iconv 
* bcmath 
* xml 
* gd 
* mbstring 
* pdo 
* tidy 
* gettext 
* intl 
* pdo 
* pdo_mysql 
* mysqli 
* simplexml 
* sockets
* tokenizer 
* xml 
* xmlwriter 
* zip

#### PECLs
* Redis
* GeoIP
* gRPC
* Memcached
* TimezoneDB
* APCu

## Need something else added?

Raise a pull request or an issue. 

## License
This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.
```


