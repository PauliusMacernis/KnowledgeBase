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
  - ...config
    - `./bin/console config:dump `
    - `./bin/console config:dump TwigBundle`
  - `composer unpack debug` - unpacks the package = replaces the package with childron packages of the package

# Cleaning cache
- `rm -rf var/cache/dev/*`
