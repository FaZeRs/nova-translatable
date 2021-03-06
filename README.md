# Nova Translatable

[![Latest Version on Packagist](https://img.shields.io/packagist/v/optimistdigital/nova-translatable.svg?style=flat-square)](https://packagist.org/packages/optimistdigital/nova-translatable)
[![Total Downloads](https://img.shields.io/packagist/dt/optimistdigital/nova-translatable.svg?style=flat-square)](https://packagist.org/packages/optimistdigital/nova-translatable)

This [Laravel Nova](https://nova.laravel.com) allows you to make any input field `spatie/laravel-translatable` compatible and localisable.

## Requirements

- `laravel/nova: ^2.9`
- `spatie/laravel-translatable: ^4.0`

## Features

- **Supports almost all fields** (including third party ones)
- **Supports default validation automatically**
- **Simple to implement** with minimal code changes (after `spatie/laravel-translatable` support)
- Locale tabs to switch between different locale values of the same field
- **Double click** on a tab to switch all fields to that locale
- Supports [nova-settings](https://github.com/optimistdigital/nova-settings) package

## Screenshots

![Detail View](./docs/detail.png)

![Form View](./docs/form.png)

![Form View w/ Validation Errors](./docs/validation.png)

## Known non-working fields

- `Image` and `File` inside `Flexible (nova-flexible-content)`
  - Workarounds:
    - [optimistdigital/nova-media-field](https://github.com/optimistdigital/nova-media-field)
    - [ebess/advanced-nova-media-library](https://github.com/ebess/advanced-nova-media-library)
    - Or any library that uploads images/files using XHR

## Installation

Firstly, set up [spatie/laravel-translatable](https://github.com/spatie/laravel-translatable).

Install the package in a Laravel Nova project via Composer:

```bash
# Install nova-translatable
composer require optimistdigital/nova-translatable

# Publish configuration (optional, but useful for setting default locales)
php artisan vendor:publish --tag="nova-translatable-config"
```

## Usage

Call `->translatable()` on any field, like so:

```php
// Any Nova field
Text::make('Name')
  ->rules('required', 'min:2')
  ->translatable(),

// Any third-party input field
Multiselect::make('Football teams')
  ->rules('required')
  ->translatable(),

// Optionally pass custom locales on a per-field basis
Number::make('Population')
  ->translatable([
    'en' => 'English',
    'et' => 'Estonian',
  ]),
```

## Configuration

You can define default locales for all the `translatable` fields in the config file. The config file can be published using:

```bash
php artisan vendor:publish --tag="nova-translatable-config"
```

## Credits

- [Tarvo Reinpalu](https://github.com/Tarpsvo)

## License

This project is open-sourced software licensed under the [MIT license](LICENSE.md).
