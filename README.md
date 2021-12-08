## UTC Bedrock Overview

This is a base repo that contains:
- [Bedrock](https://roots.io/docs/bedrock/master/installation/) WordPress stack with multi-environment capability 
  - (change .env.example to .env for the local environment configuration)
- [Lando](http://lando.dev) config to start a local development environment (`lando start`)
- [Laravel Envoy](https://laravel.com/docs/8.x/envoy) deployment script, targeting the UTC Web App Server, test environment (twebvmin11.is.utc.edu)

Fork this repo to a new UTCWeb Github repo to begin a new WordPress development project intended for deployment to the UTC Web App Server.

## Features

- Better folder structure
- Dependency management with [Composer](https://getcomposer.org)
- Easy WordPress configuration with environment specific files
- Environment variables with [Dotenv](https://github.com/vlucas/phpdotenv)
- Autoloader for mu-plugins (use regular plugins as mu-plugins)
- Enhanced security (separated web root and secure passwords with [wp-password-bcrypt](https://github.com/roots/wp-password-bcrypt))

## Requirements, Plugins, Themes

- PHP >= 7.4 (provided by Lando, so no need to update PHP on your development environment)
- Composer (provided by Lando, so run Composer commands `lando composer require repo/package`)
- Add WordPress themes and plugins as Composer requirements from [WPackagist](https://wpackagist.org)
- For [custom/private packages](https://getcomposer.org/doc/05-repositories.md#using-private-repositories), Github repo release zip via composer/installers, similar to how JS libs and custom packages are required in the UTC Cloud Drupal project.

## Deployment Overview

This project includes Laravel Envoy, for "Zero-downtime" deployments with symlinks and rollbacks. Supports various scenarios for deploying WordPress (Bedrock), Laravel and static html projects.

See Envoy.blade.php and envoy.config.php for the configuration and script, adapted from koterle/envoy-oven.

The project is pre-configured with an example storybook of tasks to deploy via SSH to a WordPress host on the UTC Web App Server, Test environment (twebvmin). Only a user who has the SSH keys for that virtual host can run the deploy command:
- `lando envoy run deploy`
- `lando envoy run rollback`
