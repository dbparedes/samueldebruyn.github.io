---
author: Sam
comments: true
date: 2014-06-14 10:54:30+00:00
layout: post
slug: workaround-for-password-confirmation-with-laravel-ardent
title: Workaround for password confirmation with Laravel & Ardent
wordpress_id: 153
categories:
- English
- PHP
---

While I was working on a website made with Laravel and Ardent I has to validate a password confirmation field for a user registration. This will not work if you follow the standard documentation.<!-- more -->

This is how your [validation rules](http://laravel.com/docs/validation) in your [Ardent ](https://github.com/laravelbook/ardent)model should look like (users only have an email address and a password):

[php]
public static $rules = array(
'email' => 'required|email|max:100|unique:users',
'password' => 'required|min:6|confirmed',
);
[/php]

Your model should also have the following line somewhere:

[php]
public $autoPurgeRedundantAttributes = true;
[/php]

Now, if you follow the documentation and include every database field in the _fillable_ array, validation will always fail on the password confirmation.

The workaround is to include the password confirmation field in the fillable array, even if it isn't a column in your database.

[php]
protected $fillable = array('email', 'password', 'activation_code', 'confirmed', 'reset_password', 'password_confirmation');
[/php]

