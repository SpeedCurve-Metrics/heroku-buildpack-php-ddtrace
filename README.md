# Datadog APM (ddtrace) PHP extension Heroku buildpack

This [Heroku buildpack](https://devcenter.heroku.com/articles/buildpacks) enables the ddtrace PHP extension.

## Requirements

- This buildpack requires the [heroku-buildpack-datadog](https://github.com/DataDog/heroku-buildpack-datadog) buildpack. Follow the instructions there.

## Installation

To add this buildpack to your project, run the following:

```
heroku buildpacks:add --app <your-app-name> https://github.com/SpeedCurve-Metrics/heroku-buildpack-php-ddtrace.git
```

Make sure to add this buildpack after the PHP buildpack, as a PHP binary is
needed to run the installer.

## Configuration

This buildpack accepts several config vars. All of them are optional:

- `DD_RELEASE` - The release version of [dd-trace-php](https://github.com/DataDog/dd-trace-php/releases/) to download. Uses latest release if omited.
- `DD_INSTALLER_URL` - The URL to the `datadog-setup.php` to be used (to be found on the [dd-trace-php release page](https://github.com/DataDog/dd-trace-php/releases/)).
- `DD_PROFILING_ENABLED` - Set to a non empty value, this will install and enable the profiling extension.
- `DD_APPSEC_ENABLED` - Set to a non empty value, this will install and enable the appsec extension.

**Note:** In case `DD_RELEASE` is omited, this will always install the latest version.