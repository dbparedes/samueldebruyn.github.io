---
title: Workaround for password confirmation with Laravel & Ardent
layout: post
author: Sam
---

While I was working on a website made with Laravel and Ardent I has to validate a password confirmation field for a user registration. This will not work if you follow the standard documentation.

This is how your [validation rules](http://laravel.com/docs/validation){:target="_blank"} in your [Ardent](https://github.com/laravelbook/ardent){:target="_blank"} model should look like (users only have an email address and a password):

{% highlight php linenos=table %}
public static $rules = array(
  'email' => 'required|email|max:100|unique:users',
  'password' => 'required|min:6|confirmed',
);
{% endhighlight %}

Your model should also have the following line somewhere:

{% highlight php %}
public $autoPurgeRedundantAttributes = true;
{% endhighlight %}

Now, if you follow the documentation and include every database field in the _fillable_ array, validation will always fail on the password confirmation.

The workaround is to include the password confirmation field in the fillable array, even if it isn't a column in your database.

{% highlight php %}
protected $fillable = array('email', 'password', 'activation_code', 'confirmed', 'reset_password', 'password_confirmation');
{% endhighlight %}
