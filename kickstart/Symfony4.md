# Docs
- https://github.com/sugalvojau/Installs/blob/master/list-of-software-to-install/my-linux-ubuntu.md 
- https://symfony.sh/ (symfony/flex aliases, e.g. `symfony.lock` uses it)

# Install Symfony4
- `composer create-project symfony/skeleton myprojectnameasthenewdir`
- `cd myprojectnameasthenewdir`
- Push changes to git

# Install Docker
- Add docker support: https://github.com/joeymasip/docker-symfony4
- `docker-compose up`
- Push changes to git

# Build project under project dir
- `docker-compose exec php-fpm bash`
  - `composer require annotations`
  - `composer require sec-checker --dev`
    - `bin/console security:check`
  - `composer require twig`
    - `{{ say_something }}`
    - `{% do_something %}`
    - `{# comments #}`
  - `composer require asset`
  - `composer require profiler --dev`
  - `composer require debug --dev`
    - `./bin/console debug:router`
    - `./bin/console debug:autowiring`
    - `./bin/console debug:container --show-private` - list all services on the container
    - `./bin/console debug:container --show-private log` - list all services on the container that contains "log"
    - `./bin/console debug:container monolog.logger` - info on the service
    - `./bin/console debug:config TwigBundle` - dumps current config
  - ...config
    - `./bin/console config:dump`
    - `./bin/console config:dump TwigBundle` - dumps available config
  - `composer unpack debug` - unpacks the package = replaces the package with childron packages of the package
  
# Good practices
- Service dependencies (other services) are being injected into constructor of the service, not other methods of the service. Other methods uses services injected to and set by constructor.

# Cleaning cache
- `rm -rf var/cache/dev/*`
- `./bin/console cache:clear` 
(Symfony had a bug prior to v4.0.5 - it kept an old cache file after we copy the older file, like template file, on top of the existing one. Which means Symfony will not overwrite the cache automatically, need to manually run cache:clear.)
- `./bin/console cache:warmup`
