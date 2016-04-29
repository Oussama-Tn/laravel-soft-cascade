# Laravel 5 Soft Cascade
Cascade delete and restore when using the Laravel SoftDeletes feature.

# Why do I need it?
### To make it easy to soft delete and restore relations.
If you enjoy features like MySQL cascade deleting but want to use Laravels SoftDeletes feature you'll need to do some extra steps to ensure your relations are properly deleted or restored.

This package is intended to replace those steps with a simple array that defines the relations you want to cascade.

# Installation
Install with composer
~~~
  composer require askedio/laravel5-soft-cascade
~~~

Register the service provider in your config/app.php
~~~
Askedio\SoftCascade\Providers\GenericServiceProvider::class,
~~~

In your Model(s), enable the trait and define $softcascade. [Example](https://github.com/Askedio/laravel5-soft-cascade/blob/master/tests/app/User.php).
~~~
use \Askedio\SoftCascade\Traits\SoftCascadeTrait;

protected $softcascade = ['profiles'];
~~~
`$softcascade` is an array of your relation names, in the [example](https://github.com/Askedio/laravel5-soft-cascade/blob/master/tests/app/User.php) you'll see we've defined `function profiles()` for the relation.

Nested relations work by defining `$softcascade` in the related Model as you can see [here](https://github.com/Askedio/laravel5-soft-cascade/blob/master/tests/app/Profiles.php).



# Supported Databases
* MySQL
* SQLite

# Testing
I have written some very basic tests, certainly more needs to be done here. If you find this useful please help by testing other databases or writing better unit tests because I must move on.
