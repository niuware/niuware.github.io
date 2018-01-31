---
layout: tutorial
title: "Step 3: Application Spaces"
---

<div class="tutorial-nav">
    <a class="anchor-left" href="{%link tutorial/step-2-configuration.md %}">← Previous</a>
    <a class="anchor-right" href="{%link tutorial/step-4-routes.md %}">Next →</a>
</div>

An *application space* is a way of organizing your web application. You can have each application space files contained into their own directory as well as create single sessions for each space, but still having the ability to share classes and session values across all spaces.

You have two application spaces out of the box. The **main application space** which is intended to be accessed by all your users and the **admin application space** which is intended to be accessed by specific users. For example, let's suppose you will create a blogging web application. The main application space will be where all your content will be accessed by your audience while you will add and edit the content in the admin space.

#### Features of an application space

* Files are grouped in specific subdirectories
* Custom namespaces for controller classes
* Unique session creation (allowing different logins for each space)
* Share controller methods, helper and request classes, session values and html views across all application spaces.

To create an application space just go to the `App/Config/Routes.php` file and add a *key name* to the `$views` associative array. For example if you want to create the `staff` application space, then your `Routes.php` file should look like this:

{% highlight php %}
<?php 

...

    public static $views = [
        'main' => [

            'home' => ['use' => 'Home', 'require' => []]
        ],

        'admin' => [

            'login' => ['use' => 'Login@login'],
            'logout' => ['use' => 'Login@logout'],

            'home' => ['use' => 'Home']
        ],

        'staff' => [
            'home' => ['use' => 'Home']
        ]
    ];

...
{% endhighlight %}

That's it! Now you can proceed to the <a href="{%link tutorial/step-4-routes.md %}">next step</a> of the tutorial.

#### Additional notes

If you rather prefer to use the YAML or JSON format to define your application spaces and routes, then create the file `App/Config/routes.yaml` or `App/Config/routes.json` and add the application spaces you require. For the previous example it will look like this:

{% highlight yaml %}
main:
    home:
        use: Home

admin:
    login:
        use: Login@login
        require: 
    logout:
        use: Login@logout
    home:
        use: Home

staff:
    home:
        use: Home
{% endhighlight %}

or for JSON:

{% highlight json %}

{
    "main": {
        "home": {
            "use": "Home"
        }
    },
    "admin": {
        "login": {
            "use": "Login@login"
        },
        "logout": {
            "use":  "Login@logout"
        },
        "home": {
            "use":  "Home"
        }
    },
    "staff": {
        "home": {
            "use": "Home"
        }
    }
}

{% endhighlight %}

If you decide to use the YAML or JSON routes file, don't forget to parse it after each modification with the following console command:

{% highlight powershell %}
$ php vendor/bin/nwf routes update yml
{% endhighlight %}

or through the browser:

{% highlight powershell %}
http://sample.com/console/routes/update/yml
{% endhighlight %}

For more information on how the Niuware WebFramework console works, visit [the documentation](http://localhost:4000/documentation/#routing-format)