# Lightweight PHP-FPM & Nginx Docker Image for WordPress
[![nodesource/node](http://dockeri.co/image/devgeniem/alpine-wordpress)](https://registry.hub.docker.com/u/devgeniem/alpine-wordpress/)

[![License](http://img.shields.io/:license-mit-blue.svg?style=flat-square)](http://badges.mit-license.org)

This is maintained repository. We use this project in production and recommend this for your projects too.

## Aren't you only supposed to run one process per container?
We think that docker container should be small set of processes which provide one service rather than one clumsy process. This container uses [s6-overlay](https://github.com/just-containers/s6-overlay) in order to run php-fpm and nginx together.

## Container layout
Mount your wordpress project into:
```
/data/code
```

Your project should define web root in:
```
/data/code/web
```
This is the place where nginx will serve requests. This is compatible with [bedrock layout](https://github.com/roots/bedrock).

## Environment Variables

### Database variables (mysql/mariadb)

```
DB_NAME     # Default: ''
DB_PASSWORD # Default: ''
DB_USER     # Default: ''
DB_HOST     # Default: '172.17.0.1' (the docker host machine)
DB_PORT     # Default: '3306'
```

Remember to set `DB_NAME`, `DB_PASSWORD` and `DB_USER` and use these variables in your wp-config.php. These are automatically added as envs in php context.

### Email variables

```
SMTP_HOST
```

This variable changes the host where container tries to send mail from. By default this is docker host ```172.17.0.1```.

```
SMTP_PORT
```

This variable changes the port where container tries to connect in order to send mail. By default this is default smtp-port ```25```.

```
SMTP_TLS
```

If this is `on` mail will use secure connections to smtp server. Default: `off`

```
SMTP_AUTH
```

If this is `on` mail will use authentication when connecting to external smtp. Default: `off`

See more about these variables in [msmtp docs](http://msmtp.sourceforge.net/doc/msmtp.html#Authentication).

## What's inside container:
### For running WordPress
- php7
- php-fpm7
- nginx
- wp-cli
- composer

### For testing WordPress (Or any web application)
- phantomjs
- ruby
- poltergeist
- rspec
- capybara
