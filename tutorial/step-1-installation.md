---
layout: tutorial
title: "Step 1: Installation"
---

<div class="tutorial-nav">
    <a class="anchor-left" href="{%link tutorial-web.md %}">← Previous</a>
    <a class="anchor-right" href="{%link tutorial/step-2-configuration.md %}">Next →</a>
</div>

If you haven't installed Niuware WebFramework, don't worry it will take you 1 minute!

1. Clone the [GitHub](https://github.com/niuware/web-framework.git) repository.

{% highlight powershell %}
$ git clone https://github.com/niuware/web-framework.git sample-app
{% endhighlight %}

> No Git available? No problem! [Download](https://github.com/niuware/web-framework/archive/master.zip) the code directly from GitHub.

{:start="2"}
2. Run composer to install all required dependencies.

{% highlight powershell %}
$ cd sample-app
$ composer install
{% endhighlight %}

> If you don't have Composer, get it [here](https://getcomposer.org/) 

That's it, you are ready to go the <a href="{%link tutorial/step-2-configuration.md %}">next step</a>!