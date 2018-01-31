---
layout: partial
title:  "Intro"
---

<h1 class="page-title">Introducing Niuware WebFramework</h1>

Niuware WebFramework is a lightweight and ready to use PHP framework for developing full MVC and MVP web applications using synchronous and asynchronous requests.

#### Get the best features of *Laravel* and *Symfony* in one unified PHP web framework.
The framework integrates the [Eloquent ORM](https://laravel.com/docs/master/eloquent) (well known for its use in Laravel) for implementing database models and [Twig](https://twig.sensiolabs.org) (well known for its use in Symfony) for smart template redering.

<br />
## One, two, three installation

1. Download or clone the repository from [GitHub](https://github.com/niuware/web-framework.git).
2. Run `composer install` to install all dependencies.
3. Enjoy!

<br />
## One, two, three usage

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

You have defined the route, now is time to define who will listen to it. For this task, it's as simple as defining a method in a Controller class using the same name you used in the previous step. For example:

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

### 3. Third, the View

Your application has a route, a listener, what is missing? Yep, the thing to display your stuff. The easiest way is to add a file with the same name as your route and the framework will do the rest for you. For example:

{% highlight twig %}
[public/views/apple/my-apples.twig]

<h1>{% raw %}{{ greetings }}{% endraw %}, this are my apples with color: {% raw %}{{ appleColor }}{% endraw %}</h1>

...

{% endhighlight %}

<br />
## What to do now?

You've just realized how easy is to create and start running your new web application, but there are much more things to explore. You need to know the cool stuff like how easy is to restrict HTTP requests from Controllers and API classes, define custom view names, recycling Controllers, add custom classes, applications spaces, global helper functions, using Eloquent Model classes, database migration features and more.

→ Continue with the [web app tutorial]({%link tutorial-web.md %})
<br />
→ See the full [Documentation]({%link documentation.md %}) 