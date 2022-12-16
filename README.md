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

This buildpack accepts several config vars. All of them are optional:

- `DDTRACE_EXT_PHP_API` - The PHP API version that your application uses. Defaults to `20210902`. Use `phpinfo()` to find the API version if you're not sure.
- `DDTRACE_EXT_RELEASE` - The release name of [dd-trace-php](https://github.com/DataDog/dd-trace-php/releases/) to download. Defaults to `0.82.0`.
- `DDTRACE_EXT_PKG_URL` - The URL to a dd-trace-php `.deb` file. This option overides `DDTRACE_EXT_RELEASE`.

### More information: `DDTRACE_EXT_PHP_API`

This buildpack does not determine that PHP API version automatically. The default value should work for most PHP versions, but if the version is wrong then you will see warnings like this in your application logs:

```
PHP Warning:  PHP Startup: ddtrace: Unable to initialize module
Module compiled with module API=20210902
PHP    compiled with module API=20220829
These options need to match
```

You can change the version by setting the `DDTRACE_EXT_VERSION` config var in Heroku. For example:

```
heroku config:set --app <your-app-name> DDTRACE_EXT_VERSION=20220829
```
