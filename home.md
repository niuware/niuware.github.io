---
layout: partial
title:  "Intro"
---

<h1 class="page-title">Introducing Niuware WebFramework</h1>

Niuware WebFramework is a lightweight and ready to use PHP framework for developing full MVC and MVP web applications using synchronous and asynchronous requests.

The latest version integrates the [Eloquent ORM](https://laravel.com/docs/master/eloquent) (well known for its use in Laravel Framework) for implementing automatic models associated with your application database and [Twig](https://twig.sensiolabs.org) for rendering templates. Now database migrations and seeding, integrated with [Phinx](https://phinx.org), are easy to execute through the framework console either in the terminal or browser mode.

<br />
## One, two, three installation

1. Download the repository from [GitHub](https://github.com/niuware/web-framework.git).
2. Run `composer install` to install dependencies.
3. Enjoy!

<br />
## The basics

Suppose you have a web application to sell apples (why not?). You need to add a cart web page at some point, so you just need to define 3 things:

### 1. First, the Route

You need to say to the framework the path for accessing your apple catalogue. For example:

{% highlight php %}
[app/config/routes.php]

<?php

... 

'my-apples/{color}' => ['use' => 'Apple']

{% endhighlight %}

Now your web application can be accessed through the following URL:

> http://myurl.com/**my-apples**/green

### 2. Second, the Controller

You have defined the path, now is time to define who will listen to it. For this to happen, it's as simple as defining a method with the same name in a Controller class named as you wrote in the previous step. For example:

{% highlight php %}
[app/controllers/Apple.php]

<?php

...

final class Apple extends Controller {

    public function myApples(HttpRequest $request) {

        $this->appleColor = $request->color;
        $this->greetings = "Hello!";

        return $this->render();
    }
}
{% endhighlight %}

### 3. Third, and lastly, the View

Your application has a path, the listener,... what is missing? Yep, the thing to display your stuff. The easiest way is just adding a file with the same name as your path and the framework will do the rest for you. For example:

{% highlight twig %}
[public/views/my-apples.twig]

<h1>{% raw %}{{ greetings }}{% endraw %}, this are my apples with color: {% raw %}{{ appleColor }}{% endraw %}</h1>

...

{% endhighlight %}

<br />
## What to do now?

You've just realized how easy is to create and start running your new web application, but the framework is not just this. You need to know the cool stuff like how easy is to restrict HTTP requests from Controllers and API classes, define custom view names, recycling Controllers, add custom classes and global helper functions, using Eloquent Model classes, database migration features and more.

→ Continue with the [Quick documentation]({%link quick-docs.md %}) 