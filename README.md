# Datadog APM (ddtrace) PHP extension Heroku buildpack

This [Heroku buildpack](https://devcenter.heroku.com/articles/buildpacks) enables the ddtrace PHP extension.

## Requirements

- This buildpack requires the [heroku-buildpack-datadog](https://github.com/DataDog/heroku-buildpack-datadog) buildpack. Follow the instructions there.

## Installation

To add this buildpack to your project, run the following:

```
heroku buildpacks:add --app <your-app-name> https://github.com/SpeedCurve-Metrics/heroku-buildpack-php-ddtrace.git
```

## Configuration

This buildpack accepts several config vars:

- `DDTRACE_EXT_VERSION` - The extension version that PHP is compiled with. Defaults to `20180731`.
- `DDTRACE_EXT_RELEASE` - The release name of [dd-trace-php](https://github.com/DataDog/dd-trace-php/releases/) to download. Defaults to `0.54.0`.
- `DDTRACE_EXT_PKG_URL` - The URL to a dd-trace-php `.deb` file. This option overides `DDTRACE_EXT_RELEASE`.

### More information: `DDTRACE_EXT_VERSION`

PHP on Heroku is compiled with a specific version of the ddtrace extension. By default, this buildpack enables version `20190902` of the extension. If PHP was compiled with a different version, you will see warnings like this in your application logs:

```
PHP Warning:  PHP Startup: ddtrace: Unable to initialize module
Module compiled with module API=20180731
PHP    compiled with module API=20190902
These options need to match
```

You can change the extension version that is enabled by this buildpack by setting the `DDTRACE_EXT_VERSION` config var in Heroku. For example:

```
heroku config:set --app <your-app-name> DDTRACE_EXT_VERSION=20190902
```
