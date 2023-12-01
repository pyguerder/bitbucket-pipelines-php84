# Bitbucket Pipelines PHP 8.3 image

[![](https://images.microbadger.com/badges/version/pyguerder/bitbucket-pipelines-php83.svg)](https://microbadger.com/images/pyguerder/bitbucket-pipelines-php83 "Get your own version badge on microbadger.com") [![](https://images.microbadger.com/badges/image/pyguerder/bitbucket-pipelines-php83.svg)](https://microbadger.com/images/pyguerder/bitbucket-pipelines-php83 "Get your own image badge on microbadger.com")

## Based on Ubuntu 22.04

### Packages installed

- `php8.3-zip`, `php8.3-xml`, `php8.3-mbstring`, `php8.3-curl`, `php8.3-json`, `php8.3-imap`, `php8.3-mysql`, `php8.3-tokenizer`, `php8.3-xdebug`, `php8.3-intl`, `php8.3-soap`, `php8.3-pdo`, `php8.3-cli`, `php8.3-apcu`, `php8.3-redis` and `php8.3-gd`
- wget, curl, unzip
- Composer 2
- Mysql 8
- Node 16 + Yarn

### Sample `bitbucket-pipelines.yml`

```YAML
image: pyguerder/bitbucket-pipelines-php83
pipelines:
  default:
    - step:
        script:
          - service mysql start
          - mysql -h localhost -u root -proot -e "CREATE DATABASE test;"
          - composer install --no-interaction --no-progress --prefer-dist
          - ./vendor/phpunit/phpunit/phpunit -v --coverage-text --colors=never --stderr
```
