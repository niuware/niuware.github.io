---
layout: tutorial
title: "Step 2: Configuration"
---

<div class="tutorial-nav">
    <a class="anchor-left" href="{%link tutorial/step-1-installation.md %}">← Previous</a>
    <a class="anchor-right" href="{%link tutorial/step-3-application-space.md %}">Next →</a>
</div>

After the installation you will need to configure the basics for running your web application.

Open the `Settings.php` file located in `App/Config` and edit the `BASE_PATH` and `BASE_URL` constants to match your domain.  

If your application is located in a main directory, for example **https://sample.com**, you just need to configure de  `BASE_URL` value. Your `Settings.php` file should look like this:

{% highlight php %}
<?php 

...

define(__NAMESPACE__ . '\BASE_PATH',        '/');
define(__NAMESPACE__ . '\BASE_URL',         'https://sample.com/');

...
{% endhighlight %}

On the contrary, if your application is located on a subdirectory, for example **https://sample.com/sample-app**, then you should configure the `BASE_PATH` value as well. Your file should look like this:

{% highlight php %}
<?php 

...

define(__NAMESPACE__ . '\BASE_PATH',        'sample-app/');
define(__NAMESPACE__ . '\BASE_URL',         'https://sample.com/sample-app/');

...
{% endhighlight %}

> Notice the trailing slash for both constant values.

That's it! Now go to your browser, type your domain and you will see the framework default welcome message. Now is time for the <a href="{%link tutorial/step-3-application-space.md %}">next step</a>.

#### Errors?

**Too many redirects error:** Please ensure you added the correct name of your domain (and/or subdirectory) and both have the trailing slash.  
**500 server error:** Verify your server has the module_rewrite on, and the path of your application is accessible.
