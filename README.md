# Bitbucket Pipelines PHP 8.4 image

[![](https://images.microbadger.com/badges/version/pyguerder/bitbucket-pipelines-php84.svg)](https://microbadger.com/images/pyguerder/bitbucket-pipelines-php84 "Get your own version badge on microbadger.com") [![](https://images.microbadger.com/badges/image/pyguerder/bitbucket-pipelines-php84.svg)](https://microbadger.com/images/pyguerder/bitbucket-pipelines-php84 "Get your own image badge on microbadger.com")

## Based on Ubuntu 24.04

### Packages installed

- `php8.4-zip`, `php8.4-xml`, `php8.4-mbstring`, `php8.4-curl`, `php8.4-json`, `php8.4-imap`, `php8.4-mysql`, `php8.4-tokenizer`, `php8.4-xdebug`, `php8.4-intl`, `php8.4-soap`, `php8.4-pdo`, `php8.4-cli`, `php8.4-apcu`, `php8.4-redis` and `php8.4-gd`
- wget, curl, unzip
- Composer 2
- Mysql 8
- Node 16 + Yarn

### Sample `bitbucket-pipelines.yml`

```YAML
image: pyguerder/bitbucket-pipelines-php84
pipelines:
  default:
    - step:
        script:
          - service mysql start
          - mysql -h localhost -u root -proot -e "CREATE DATABASE test;"
          - composer install --no-interaction --no-progress --prefer-dist
          - ./vendor/phpunit/phpunit/phpunit -v --coverage-text --colors=never --stderr
```
