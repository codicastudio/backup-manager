# A Laravel Nova tool to backup your application


This [Nova](https://nova.laravel.com) tool lets you:
- list all backups
- create a new backup
- download a backup
- delete a backup

Behind the scenes [spatie/laravel-backup](https://docs.spatie.be/laravel-backup) is used.

![screenshot of the backup tool](https://spatie.github.io/nova-backup-tool/screenshot.png)

You can see the tool in action in [this video on YouTube](https://www.youtube.com/watch?v=9wSi2ByavX8).

## Support us

Learn how to create a package like this one, by watching our premium video course:

[![Laravel Package training](https://spatie.be/github/package-training.jpg)](https://laravelpackage.training)

We invest a lot of resources into creating [best in class open source packages](https://spatie.be/open-source). You can support us by [buying one of our paid products](https://spatie.be/open-source/support-us).

We highly appreciate you sending us a postcard from your hometown, mentioning which of our package(s) you are using. You'll find our address on [our contact page](https://spatie.be/about-us). We publish all received postcards on [our virtual postcard wall](https://spatie.be/open-source/postcards).

## Requirements

Make sure you meet [the requirements for installing spatie/laravel-backup](https://docs.spatie.be/laravel-backup/v6/requirements).

## Installation

First you must install [spatie/laravel-backup](https://docs.spatie.be/laravel-backup) into your Laravel app. The installation instructions are [here](https://docs.spatie.be/laravel-backup/v6/installation-and-setup). When successfull running `php artisan backup:run` on the terminal should create a backup and `php artisan backup:list` should return a list with an overview of all backup disks.

You can install the nova tool in to a Laravel app that uses [Nova](https://nova.laravel.com) via composer:

```bash
composer require spatie/nova-backup-tool
```

Next up, you must register the tool with Nova. This is typically done in the `tools` method of the `NovaServiceProvider`.

```php
// in app/Providers/NovaServiceProvder.php

// ...

public function tools()
{
    return [
        // ...
        new \Spatie\BackupTool\BackupTool(),
    ];
}
```

Finally you should setup [a queue](https://laravel.com/docs/master/queues). This tool doesn't care what kind of queue as long as you don't use the `sync` driver.

## Configuration

You can optionally publish the config file with:

```bash
php artisan vendor:publish --provider="Spatie\BackupTool\BackupToolServiceProvider" --tag="config"
```

This is the contents of the published config file:

```php
<?php

return [
    /*
     * Enable or disable backup tool polling.
     */
    'polling' => true,

    /*
     * Interval seconds between polling requests.
     */
    'polling_interval' => 1,
];
```

## Usage

Click on the "Backups" menu item in your Nova app to see the backup tool.

### Testing

``` bash
composer test
```

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.
