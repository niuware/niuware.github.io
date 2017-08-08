---
layout: page
title: Quick documentation
---

This is a quick documentation on how to use all of the available features in Niuware WebFramework.

1. <a href="#install">Installation</a>  
  1.1 <a href="#install-config">Configuration File</a>  
2. <a href="#routing">Routing</a>    
  2.1 <a href="#routing-main">Main Application</a>    
  2.2 <a href="#routing-admin">Admin Application</a>  
  2.3 <a href="#routing-api">API-Only Mode</a>  
3. <a href="#controllers">Controllers</a>    
  3.1 <a href="#controllers-define">Definition</a>    
  3.2 <a href="#controllers-access">Calls</a>    
  3.3 <a href="#controllers-protocol">Protocol Restriction</a>    
  3.4 <a href="#controllers-protocol-get">GET Protocol Methods</a>  
  3.5 <a href="#controllers-protocol-post">POST Protocol Methods</a>  
  3.6 <a href="#controllers-request">Request Attributes</a>           
  3.7 <a href="#controllers-recycle">Recycling</a>    
  3.8 <a href="#controllers-json">With JSON Response</a> 
4. <a href="#models">Models</a>  
  4.1 <a href="#models-define">Definition</a>  
  4.2 <a href="#models-eloquent">Eloquent</a>  
5. <a href="#views">Views</a>  
  5.1 <a href="#views-define">Definition</a>  
  5.2 <a href="#views-render">Rendering</a>  
  5.3 <a href="#views-main">Main Views</a>  
  5.4 <a href="#views-attributes">Template Attributes</a>  
  5.5 <a href="#views-binding">View/Controller Binding</a>  
  5.6 <a href="#views-functions">Functions and Filters</a>  
6. <a href="#sessions">Sessions</a>  
  6.1 <a href="#sessions-auth">Authentication</a>  
  6.2 <a href="#sessions-custom">Custom Values</a>  
  6.3 <a href="#sessions-terminate">Termination</a>
7. <a href="#custom">Customization</a>  
  7.1 <a href="#custom-helper">Helper Class</a>  
  7.1 <a href="#custom-define">Definition of Custom Classes</a>
8. <a href="#api">API Classes</a>  
  8.1 <a href="#api-define">Definition</a>  
  8.1 <a href="#api-syntax">Method Syntax</a>  
  8.2 <a href="#api-protocol">Protocol Restriction</a>  
  8.3 <a href="#api-params">Request Parameters</a>  
  8.4 <a href="#api-response">Response Rendering</a>  
9. <a href="#security">Security</a>  
  9.1 <a href="#security-pass">Passwords</a>  
  9.2 <a href="#security-token">Tokens</a>  
  9.3 <a href="#security-csrf">CSRF Token Form Validation</a>  
10. <a href="#file">Files</a>  
  10.1 <a href="#file-attrib">Attributes</a>  
11. <a href="#console">Console</a>  
12. <a href="#migration">Database Migrations</a>  
  12.1 <a href="#migration-migrate">Migration files</a>  
  12.2 <a href="#migration-seed">Seeding</a>  
  12.3 <a href="#migration-rollback">Rollback</a>  
  12.4 <a href="#migration-status">Status</a>  
13. <a href="#exception">Exceptions</a>  

<a name="install"></a>
## 1. Installation

For using the Niuware WebFramework follow this steps:

1. Download the repository from [GitHub](https://github.com/niuware/web-framework.git).
2. Run `composer install` to install the dependencies. 

<a name="install-config"></a>
### Installation: Configuration File

The framework uses a single configuration file to store private information such as database connection strings, third party API tokens etc. It also contains the default values for the Web application. You can find this file in `app/config/settings.php`

<a name="install-constant"></a>
#### Global Constants

The following table shows the application constants that you need to configure:

<table class="reduced">
    <thead>
        <tr>
            <th>Name</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>SERVER_ENV_VAR</td>
            <td>
                How PHP receive requests. <br />
                Either <em>\INPUT_SERVER</em> or <em>\INPUT_ENV</em>
            </td>
        </tr>
        <tr>
            <td>BASE_PATH</td>
            <td>
                If your BASE_URL has a sub path (subfolder), write it here.<br /> 
                For example: If BASE_URL is http://my_url.com/ then BASE_PATH should be '/'.<br />
                If BASE_URL is http://my_url.com/<strong>sub_domain/</strong> then BASE_PATH should be <strong>sub_domain/</strong> <br />
                <strong>Should include the trailing slash.</strong>
            </td>
        </tr>
        <tr>
            <td>BASE_URL</td>
            <td>
                Absolute URL for the Web Main application. <br />
                For example: <em>http://my_domain/</em> <br/> 
                <strong>Should include the trailing slash.</strong>
            </td>
        </tr>
        <tr>
            <td>BASE_URL_SSL</td>
            <td>
                Absolute URL for the Web Main application's SSL protocol. (Optional)<br />
                For example: <em>https://my_domain/</em> <br/> 
                <strong>Should include the trailing slash.</strong>
            </td>
        </tr>
        <tr>
            <td>BASE_URL_ADMIN</td>
            <td>
                Absolute URL for the Web Admin application. <br />
                For example: <em>http://my_domain/admin/</em> <br/> 
                <strong>Should include the trailing slash. Must end with .../admin/</strong>
            </td>
        </tr>
        <tr>
            <td>DEBUG_MODE</td>
            <td>
                Sets the debug mode for the application<br />
                Either <em>true</em> or <em>false</em>
            </td>
        </tr>
        <tr>
            <td>DEFAULT_RENDERER</td>
            <td>
                Sets the default template renderer.<br />
                Either <em>twig</em> or <em>php</em> <br/> 
            </td>
        </tr>
        <tr>
            <td>CONSOLE_MODE</td>
            <td>
                Sets if the framework console will be available for executing commands such as migrations.<br />
                Either: <em>terminal</em>, <em>web</em>, <em>enabled</em> or <em>disabled</em> 
            </td>
        </tr>
        <tr>
            <td>HOMEPAGE</td>
            <td>
                The default path for the Web Main application.<br />
                For example: <em>home</em> then the path will be {BASE_URL}/<strong>home</strong> <br/> 
            </td>
        </tr>
        <tr>
            <td>HOMEPAGE_ADMIN</td>
            <td>
                The default path for the Web Admin application.<br />
                For example: <em>home</em> then the path will be {BASE_URL_ADMIN}/home<br/> 
            </td>
        </tr>
        <tr>
            <td>DEFAULT_TITLE</td>
            <td>
                The default title for any view. (Optional)<br />
                For example: <em>Niuware WebFramework</em> <br/> 
            </td>
        </tr>
        <tr>
            <td>DEFAULT_DESCRIPTION</td>
            <td>
                The default description for any view. (Optional)<br />
                For example: <em>This is my web application.</em> <br/> 
            </td>
        </tr>
        <tr>
            <td>DEFAULT_KEYWORDS</td>
            <td>
                The default keywords for any view. (Optional)<br />
                For example: <em>One, Two, Three</em> <br/> 
            </td>
        </tr>
    </tbody>
</table>

You can also set here the default timezone for your application using the `date_default_timezone_set` function located at the top of the file. For more information check the <a href="http://php.net/manual/en/function.date-default-timezone-set.php" target="_blank">PHP documentation</a>.

<a name="install-settings"></a>
#### Settings Class

The `Settings` class contains database connection parameters, third party API's tokens and timezone formats. There are three array variables where you can set these values:

<table class="reduced">
    <tbody>
        <tr>
            <td>$database</td>
            <td>Add arrays for setting connection configurations for databases.</td>
        </tr>
        <tr>
            <td>$apps</td>
            <td>Add arrays for all 3rd party API's configurations.</td>
        </tr>
        <tr>
            <td>$languages</td>
            <td>Add arrays for timezone and location configurations.</td>
        </tr>
    </tbody>
</table>

<a name="routing"></a>
## 2. Routing

Defining easy to access routes for your application is one important task for your project and for users. With Niuware WebFramework its simple to create friendly URLs by just adding the string of the path you need. 

Web applications created with Niuware WebFramework have two sides: the *main application* or User frontend side and the *admin application* or User admin side. For example suppose you create an online shop; you'll need the frontend side where all the products will be browsable by your customers, and an admin panel side where your staff will be able to add or edit products for the shop.

<a name="routing-main"></a>
### Routing: Main Application

The main application path views can be public (by default) or require a user login. For adding routes for the main application side you only need to edit the `app/config/routes.php` file.

For example, let's suppose you want people to access this sections in your web application:

> http://my_url/**home**<br />
> http://my_url/**my-cart**<br />
> http://my_url/**categories**

Then your `routes.php` file should look like this:

{% highlight php %}
[app/config/routes.php]

<?php 

namespace Niuware\WebFramework;

/**
 * Defines the routes for the web application
 */
final class Routes {
    
    public static $views = [
        'main' => [
            'home' => ['Home'], 
            'my-cart' => ['Cart', true],    // login required
            'categories' => ['Category'],
            ...
        ],
        ...
    ];
}

{% endhighlight %}

In the previous example you can notice each path has an array value as well. This array has two values: the Controller class which will listen to the path and a boolean value which tells the framework if the path requires a login or not. This value is set to false by default so it can be omitted. The usage of Controllers is detailed in the Controllers section of this page.

<a name="routing-admin"></a>
### Routing: Admin Application

All the admin application path views require a user login by default. The framework will add the prefix `admin/` to all routes set for the Admin application. As with the previous Main application routing section, you only need to edit the `app/config/routes.php` file.

For example, let's suppose you want people to access this sections in your web application:

> http://my_url/admin/**home**<br />
> http://my_url/admin/**products**<br />
> http://my_url/admin/**accounts**

Then your `routes.php` file should look like this:

{% highlight php %}
[app/config/routes.php]

<?php 

namespace Niuware\WebFramework;

/**
 * Defines the routes for the web application
 */
final class Routes {
    
    public static $views = [
        ...
        'admin' => [
            'home' => ['Home'], 
            'products' => ['Products'],
            'accounts' => ['Accounts'],
            ...
        ]
    ];
}

{% endhighlight %}

As mentioned before, all paths for the admin side require a user login so the value for each path is just a one element array which contains the Controller class which will listen to the path.

<a name="routing-api"></a>
### Routing: API-Only Mode

You can also leave the routes empty to get an `HTTP 403 response`. This is useful when you want to use the framework only as an API, without any public web access:

{% highlight php %}
[app/config/routes.php]

<?php 

namespace Niuware\WebFramework;

final class Routes {
    
    public static $views = [
        'main' => [],
        'admin' => []
    ];
}

{% endhighlight %}

<a name="controllers"></a>
## 3. Controllers

Controller classes describe the functionality of your web application. Each controller can be called by any route or be created and executed in runtime.

<a name="controllers-define"></a>
### Controllers: Definition

All controllers inherit from the Niuware WebFramework core class `Controller` and must be placed in the `app/controllers` directory. The name of the file and the class name **must match** as well. A controller class file must be defined with the extension `.controller.php` and exist inside the namespace `Niuware\WebFramework\Controllers`. Here is an example of how it should look like:

{% highlight php %}
[app/controllers/MyController.controller.php]

<?php 

namespace Niuware\WebFramework\Controllers;
    
use Niuware\WebFramework\Controller;

final class MyController extends Controller {

    ...
}

{% endhighlight %}

For the Admin application the controller class files should be in the `controllers/admin` subdirectory and use the `Niuware\WebFramework\Controllers\Admin` namespace:

{% highlight php %}
[app/controllers/admin/MyAdminController.controller.php]

<?php 

namespace Niuware\WebFramework\Controllers\Admin;
    
use Niuware\WebFramework\Controller;

final class MyAdminController extends Controller {

    ...
}

{% endhighlight %}

<a name="controllers-access"></a>
### Controllers: Calls

Controllers are there for listening to the routes you defined. There is no need to create a controller class for each different path because each path will answer to a method with its corresponding name. For example, suppose you have this path:

> http://my_url/**my-cart**

And its route is defined like this:

{% highlight php %}
[app/config/routes.php]

<?php
...

'my-cart' => [Cart]

...
{% endhighlight %}

then the controller like this:

{% highlight php %}
[app/controllers/Cart.controller.php]

<?php 

namespace Niuware\WebFramework\Controllers;
    
use Niuware\WebFramework\Controller;

final class Cart extends Controller {

}

{% endhighlight %}

Notice that **`Cart`** was defined in the `routes.php` file as the controller who will listen to the path **`my-cart`**. Also notice that the controller class has the name **`Cart.controller.php`**. 

Now the `Cart` controller class will be called when a user access this path, but nothing will happen. We are still missing to define the method that will be executed. This is as simple as adding a public method with the same name as the path, in this case:

{% highlight php %}
[app/controllers/Cart.controller.php]

<?php 

namespace Niuware\WebFramework\Controllers;
    
use Niuware\WebFramework\Controller;

final class Cart extends Controller {

    public function myCart(HttpRequest $request) {

    }
}

{% endhighlight %}

Notice the method name can use camelBack or CamelCase naming convention without problems. If your path uses hyphen [ - ] or underscore [ _ ], you **should remove** this characters from the method name (even in PHP you can use underscore to define methods, the framework will ignore them).

For example for the path: `my-cart` or `my_cart` a method named `myCart()` or `MyCart()` can be executed.

<a name="controllers-protocol"></a>
### Controllers: Protocol Restriction

It is easy to restrict the HTTP protocol that a Controller class can accept. For the previous example our method myCart would allow GET and POST protocol to execute the call; but if we want to restrict this, is as easy as adding the *get* or *post* prefix to our method. For example:

{% highlight php %}
[app/controllers/Cart.controller.php]

<?php 

namespace Niuware\WebFramework\Controllers;
    
use Niuware\WebFramework\Controller;

final class Cart extends Controller {

    // Executed when the server receives a GET request
    public function getMyCart(HttpRequest $request) {

    }

    // Executed when the server receives a POST request
    public function postMyCart(HttpRequest $request) {

    }

    // Executed for any request (GET or POST)
    public function myCart(HttpRequest $request) {

    }
}

{% endhighlight %}

Notice that if you **cannot** use an any-protocol method combined with a GET/POST protocol method at the same time as the latter ones have execution priority.

Requests other than GET, POST and DELETE will render an `HTTP 405 Method Not Allowed` error.

<a name="controllers-protocol-get"></a>
### Controllers: GET Protocol Methods

The request parameters for a GET protocol method can be placed as part of the url, split by slashes as the following example: 

> http://my_url/my-cart/**param_0_value**/**param_1_value**/ ...

The GET protocol method will recieve the values in the `HttpRequest` object `$request` as:

{% highlight php %}
<?php 

...

    public function getMyCart(HttpRequest $request) {

        $request->{0} = param_0_value;
        $request->{1} = param_1_value;
    }
...
{% endhighlight %}

You can also receive GET request parameters as a query string, for example:

> http://my_url/my-cart**/?param0=value0&param1=value1**

> Notice you need to add the **last slash** before the parameter list as is the name of the method to execute

and your GET protocol method will recieve the parameters values in an `HttpRequest` object as follows:

{% highlight php %}
<?php 

...

    public function getMyCart(HttpRequest $request) {

        $request->param0 = value0;
        $request->param1 = value1;
    }
...
{% endhighlight %}

If by some reason you want to combine both ways of receiving request parameters as this:

> http://my_url/my-cart**/param0_value/param1_value/?param2=value2&param3=value3**

then your GET protocol method will recieve the parameters as

{% highlight php %}
<?php 

...

    public function getMyCart(HttpRequest $request) {

        // From the URL
        $request->{0} = param0;
        $request->{1} = param1;
        $request->{2} = ?param2=value2&param3=value3;

        // From the query string
        $request->param2 = value2;
        $request->param3 = value3;
    }
...
{% endhighlight %}

<a name="controllers-protocol-post"></a>
### Controllers: POST Protocol Methods

The request parameters for a POST protocol method can be placed as part of the url, split by slashes as the following example: 

> http://my_url/my-cart/**param_0_value**/**param_1_value**/ ...

The POST protocol method will recieve the values in an `HttpRequest` object `$request` as:

{% highlight php %}
<?php 

...

    public function postMyCart(HttpRequest $request) {

        $request->{0} = param_0_value;
        $request->{1} = param_1_value;
    }
...
{% endhighlight %}

You can also receive POST request parameters as a usual POST request, for example data in an HTML form. The POST protocol will receive the parameters as an `HttpRequest` object:

{% highlight html %}
<form method="POST" action="http://my_url/my-cart/">
    <input type="text" name="form_elem_name_0" value="value0" />
    <input type="text" name="form_elem_name_2" value="value1" />
</form>

{% endhighlight %}

{% highlight php %}
<?php 

...

    public function postMyCart(HttpRequest $request) {

        // From the query string
        $request->form_elem_name_0 = value0;
        $request->form_elem_name_1 = value1;
    }
...
{% endhighlight %}

> Although DELETE requests are accepted it is reserved for using in API classes. By default, a DELETE request method will only process request parameters in JSON format. If you want to use a DELETE request method, remember to send your data as a JSON.

<a name="controllers-request"></a>
### Controllers: Request Attributes

To verify if the request has attributes you can use the `has` method as follows:

{% highlight php %}
<?php 

...

    public function postMyCart(HttpRequest $request) {

        // Verify if access_token and option POST parameters exist and have 
        // a valid value
        if ($request->has(['access_token', 'option'])) {

            // do something
        }

        // Verifies if access_token and option POST parameters exist and have
        // a value including empty string as a valid value
        if ($request->has(['access_token', 'option'], true)) {

            // do something
        }

        // You can use the above method with a single parameter as well
        if ($request->has('access_token')) {

            // do something
        }
    }

{% endhighlight %}

For verifying attached files, go to the [Files](#file) section.

<a name="controllers-recycle"></a>
### Controllers: Recycling

Sometimes the functionality of one method in a Controller class can be reused after completing some other processing in the current called method. This option is very useful in the following scenarios: 
1. When you want to use the same view template for different data sources 
2. When you want to use the same view template for different paths
3. When you want to redirect one path to another controller without reloading the browser

For this is as easy as instance an object of the Controller class you want.

{% highlight php %}
[app/controllers/Cart.controller.php]

<?php 

namespace Niuware\WebFramework\Controllers;
    
use Niuware\WebFramework\Controller;

final class Cart extends Controller {

    public function getMyCart(HttpRequest $request) {

        // Do something here

        $otherController = new OtherController();

        // Additionally set controller options like
        // the view file name. For example:
        $otherController->view = "other.view.php";

        return $otherController->getOtherMethod($request);
    }
}

{% endhighlight %}

If you want to redirect the browser, call the `render` method with the name of the path:

{% highlight php %}
[app/controllers/Cart.controller.php]

<?php 

namespace Niuware\WebFramework\Controllers;
    
use Niuware\WebFramework\Controller;

final class Cart extends Controller {

    public function getMyCart(HttpRequest $request) {

        return $this->render('path');
    }
}

{% endhighlight %}

<a name="controllers-json"></a>
### Controllers: With JSON Response

A Controller can also render a JSON response (like an API class) instead of a view. For this, just use the core `Response` class as the following example:

{% highlight php %}
[app/controllers/Cart.controller.php]

<?php 

namespace Niuware\WebFramework\Controllers;
    
use Niuware\WebFramework\Controller;
use Niuware\WebFramework\Response;

final class Cart extends Controller {

    public function getMyCart(HttpRequest $request) {

        $response = new Response();

        $response->something = "value";

        return $response;
    }
}

{% endhighlight %}

The response will be something like this:

{% highlight json %}

{
    "error" : false,
    "data" : {
        "something" : "value"
    }
}

{% endhighlight %}

<a name="models"></a>
## 4. Models

Models are the way to connect a datasource with a Controller (and a View). Niuware WebFramework integrates Illuminate's Database module for this part of the framework.

<a name="models-define"></a>
### Models: Definition

All models inherit from the Illuminate\Database\Eloquent class `Model` and must be placed in the `app/models` directory. The model class file must be defined with the extension `.model.php` and exist inside the namespace `Niuware\WebFramework\Models`. Here is an example of how it should look like:

{% highlight php %}
[app/models/Product.model.php]

<?php

namespace Niuware\WebFramework\Models;
    
use Illuminate\Database\Eloquent\Model as Eloquent;

class Product extends Eloquent {
    
}

{% endhighlight %}

<a name="models-eloquent"></a>
### Models: Eloquent

To learn more on how to define and use models using Eloquen please visit the <a href="https://laravel.com/docs/master/eloquent" target="_blank">Laravel documentation</a>.

<a name="views"></a>
## 5. Views

The view holds the template where all the controller data will be displayed.

<a name="views-define"></a>
### Views: Definition

All views must be placed in the `public/views` directory and their file must be defined with the extension `.view.twig`. For the case of 'admin application side' views, the files should be inside the `views/admin` subdirectory. The content of the views use Twig syntax, for more information visit the [Twig documentation](https://twig.sensiolabs.org/doc/2.x/).

By default, the framework will load a view filename that matches the current loaded path. For example for the next URL:

> http://my_url/my-cart

the framework will try to load the following view file:

`public/views/my-cart.view.twig`

You can change the name of the view filename to load by setting the attribute `view` as shown in section Views: <a href="#views-attributes">Template Attributes</a>.

For the Admin application, all views filenames should be in the `views/admin` subdirectory.

`public/views/admin/my-account.view.twig`

<a name="views-render"></a>
### Views: Rendering

To render a view template file, you need to tell the controller to do it. This is done by calling the `render` method. For example for the following URL:

> http://my_url/my-cart

we can simply call the `render` method as this:

{% highlight php %}
[app/controllers/Cart.controller.php]

<?php 

namespace Niuware\WebFramework\Controllers;
    
use Niuware\WebFramework\Controller;

final class Cart extends Controller {

    public function getMyCart(HttpRequest $request) {

        // By default it will render the public/views/my-cart.view.twig file
        return $this->render();
    }

    public function getMyOtherCart(HttpRequest $request) {

        // You can also redirect to another controller adding a valid path 
        // set on the application routes.php file
        // For more details see the Controllers: Recycling section
        return $this->render('some-other-path');
    }
}

{% endhighlight %}

If you want to specify the filename of the view to load, simply set the template attribute as <a href="#views-attributes-view">described here</a>.

> If you are using **PHP** as the template renderer change your view template file names from *xyz.view.twig* to *xyz.view.php*. Also be sure to set *'php'* as the `DEFAULT_RENDERER` value in your application <a href="#install-config">settings file</a>.

<a name="views-main"></a>
### Views: Main Views

There are 2 main views included out of the box with the framework, which are ready to render all your views. 

<table class="variant">
    <thead>
        <tr>
            <th>Name</th>
            <th>Filename</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>main<br /> main-admin</td>
            <td>main.view.twig<br /> main-admin.view.twig</td>
            <td>
                Contains HTML used by all views. Defines CSS stylesheet, JS files and other HTML headers meta tags Twig blocks. The main and admin side have their own main vies files.<br/>
            </td>
        </tr>
    </tbody>
</table>

Then you can use them in your controller view template files as follows:

{% highlight twig %}
{% raw %}
{% extends 'main.twig' %}

{% block main %}
    
<div>Here goes your view specific content</div>

...

{% endblock %}
{% endraw %}
{% endhighlight %}

If you want to add specific stylesheet, js, etc. to the current view use the already defined Twig blocks:

<table class="variant">
    <thead>
        <tr>
            <th>Block/Var name</th>
            <th>Usage</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>metas</td>
            <td>{% raw %}{% block metas %}{% endraw %}<br />
                meta tags here <br />
                {% raw %}{% endblock %}{% endraw %}</td>
            <td>
                Adds additional meta tag content to the view template.<br/>
            </td>
        </tr>
        <tr>
            <td>title</td>
            <td>{% raw %}{% set title = 'MyTitle' %}{% endraw %}</td>
            <td>
                Sets an additional title after the DEFAULT_TITLE.<br/>
            </td>
        </tr>
        <tr>
            <td>stylesheets</td>
            <td>{% raw %}{% block stylesheets %} <br />
                css stylesheet files here <br />
            {% endblock %}{% endraw %}</td>
            <td>
                Adds additional stylesheet files to the view template.<br/>
            </td>
        </tr>
        <tr>
            <td>stylesheets</td>
            <td>{% raw %}{% block scripts %} <br />
                script files here <br />
            {% endblock %}{% endraw %}</td>
            <td>
                Adds additional script files to the view template.<br/>
            </td>
        </tr>
    </tbody>
</table>

For example:

{% highlight twig %}
{% raw %}
{% extends 'main.twig' %}

{% block stylesheets %}

<link rel="stylesheet" href="file.css" />

{% endblock %}

{% block scripts %}

<script src="file.js"></script>

{% endblock %}

{% block main %}
    
<div>Here goes your view specific content with the additional stylesheet and script files</div>

...

{% endblock %}
{% endraw %}
{% endhighlight %}

<a name="views-attributes"></a>
### Views: Template Attributes

All Controller classes can set template attributes before rendering the view file. Here is the list of available attributes:

<a name="views-attributes-view"></a>
<table class="variant">
    <tbody>
        <tr>
            <td><strong>view</strong></td>
            <td>String (optional)</td>
            <td>
                The filename of the view to load.<br />
                <em>Default: A filename with the same name as the URL path.</em>
            </td>
        </tr>
    </tbody>
</table>

Usage: 

{% highlight php %}
[MyController.controller.php]

<?php

final class MyController extends Controller {

    public function getMyPage(HttpRequest $request) {

        $this->view = "view_filename.view.twig";

        ...

        return $this->render();
    }

{% endhighlight %}

Output:

{% highlight html %}

Loaded file: public/views/view_filename.view.twig

or when using PHP as renderer:

Loaded file: public/views/view_filename.view.php

{% endhighlight %}

<a name="views-binding"></a>
### Views: View/Controller Binding

You can bind variables from a controller to a view by assigning new properties to the `Controller` object. For example let's suppose you need to render some array:

{% highlight php %}
[app/controllers/MyController.controller.php]

<?php

final class MyController extends Controller {

    public function getMyPage(HttpRequest $request) {

        // Assign the array as an attribute to the controller
        $this->myArray = [ ... ]

        ...

        return $this->render();
    }

{% endhighlight %}

Then in your view, you just need to use it as you would expect:

{% highlight twig %}
[public/views/my-controller.view.twig]

...

<ul>
    {% raw %}
    {% for data in myArray %}
        <li>{{ data }}</li>
    {% endfor %}
    {% endraw %}
</ul>

...

{% endhighlight %}

When using PHP:

{% highlight php %}
[public/views/my-controller.view.php]

...

<ul>
    <?php
        foreach ($this->myArray as $data => $value) {
    ?>
        <li><?php echo $data; ?></li>
    <?php
        }
    ?>
</ul>

...

{% endhighlight %}

<a name="views-functions"></a>
### Views: Functions and Filters

You can use the `TwigFilters.helper.php` and `TwigFunctions.helper.php` classes to define custom functions and filters. For example:

{% highlight php %}

<?php
[app/helpers/TwigFunctions.helper.php]

namespace Niuware\WebFramework\Helpers;

use Niuware\WebFramework\Helper;

class TwigFunctions {
    
    public function myCustomFunc($params) {
        
        return Helper::myCustomFunc($params);
    }
}


{% endhighlight %}

And use it in the view as:

{% highlight twig %}
[public/views/my-controller.view.twig]

...
<div>
    {% raw %}
    {{ myCustomFunc('something') }}
    {% endraw %}
</div>

{% endhighlight %}

The following is a list of defined functions that are ready to use within your views in the framework:

<table class="variant">
    <tbody>
        <tr>
            <td><strong>url</strong></td>
            <td>url('path', [mode])</td>
            <td>
                Returns a valid route string <br />
                The second optional parameter can be either 'main' or 'admin' which correspond to the Routes file.<br />
                By default the path will be searched in the 'main' array
            </td>
        </tr>
        <tr>
            <td><strong>csrfToken</strong></td>
            <td>csrfToken()</td>
            <td>
                Returns an input hidden field with the CSRF token <br />
            </td>
        </tr>
    </tbody>
</table>

You can use these functions as the following example:

{% highlight twig %}
[public/views/my-controller.view.twig]

...
<form>
    {% raw %}
    {{ csrfToken() }}
    {% endraw %}
    <a href="{% raw %}{{ url('create') }}{% endraw %}">Create user</a>
    <a href="{% raw %}{{ url('edit/id') }}{% endraw %}">Edit user</a>
</form>

{% endhighlight %}

The output will be something like:

{% highlight html %}

<form>
    <input type="hidden" name="csrf_token" value="73aef6s76d7s6bd6ad7" />
    <a href="http://my_url/create">Create user</a>
</form>

{% endhighlight %}

<a name="sessions"></a>
## 6. Sessions

Sessions are very useful for saving data for active users while they use your Web application. The `Auth` core class helps you manage sessions in a simple way.

<a name="sessions-auth"></a>
### Sessions: Authentication

The `Auth` class can help you verify if a user has successfully logged in to either the Main or Admin application. For this you can use the `grantAuth` or `revokeAuth` methods. Usually this methods will be called in the `Login.controller.php`.

The Niuware WebFramework comes with a default configuration for auto logging a user who navigates to login-protected views as you can see in the following `Login` controller:

{% highlight php %}
[controllers/Login.controller.php]

<?php 

namespace Niuware\WebFramework\Controllers;
    
use Niuware\WebFramework\Controller;
use Niuware\WebFramework\Auth;

final class Login extends Controller {

    public function getLogin(HttpRequest $request) {
        
        Auth::grantAuth();
    }
    
    public function getLogout(HttpRequest $request) {
        
        Auth::revokeAuth();
    }
}

{% endhighlight %}

You can implement the authentication in any controller you want by using the `Auth` class as:

{% highlight php %}

<?php 

namespace Niuware\WebFramework\Controllers;
    
use Niuware\WebFramework\Controller;
use Niuware\WebFramework\Auth;

final class MyController extends Controller {

    public function getMyPage(HttpRequest $request) {

        // For main application use:
        Auth::grantAuth();
        // and/or
        Auth::revokeAuth();

        // For admin application use:
        Auth::granthAuth('admin');
        // and/or
        Auth::revokeAuth('admin');
    }

{% endhighlight %}

To verify if a user has logged in to your Web application use the following method:

{% highlight php %}

<?php 

namespace Niuware\WebFramework\Controllers;
    
use Niuware\WebFramework\Controller;
use Niuware\WebFramework\Auth;

final class MyController extends Controller {

    public function getMyPage(HttpRequest $request) {

        if (!Auth::verifiedAuth()) {

            // User is not logged in, so we could 
            // redirect to the login page

            $loginController = new Login();

            return $loginController->getLogin();
        }
    }

{% endhighlight %}

For verifying the authentication for the Admin application, add `'admin'` to the method:

{% highlight php %}
Auth::verifiedAuth('admin');
{% endhighlight %}

<a name="sessions-custom"></a>
### Sessions: Custom Values

For adding and removing values to the current session, the `Auth` class contains 4 methods: `has`, `add`, `get`, and `remove` with simple functionality as shown in the following example:

{% highlight php %}

<?php 

namespace Niuware\WebFramework\Controllers;
    
use Niuware\WebFramework\Controller;
use Niuware\WebFramework\Auth;

final class MyController extends Controller {

    public function getMyPage(HttpRequest $request) {

        // Verify if a session variable exists
        if (Auth::has('myVar')) {

            // Add a session variable
            Auth::add('myVar', 'myValue');
        }

        // $sessionValue = 'myValue'
        $sessionValue = Auth::get('myVar');

        // Remove a session variable
        Auth::remove('myVar');

        // $otherValue = null
        $otherValue = Auth::get('myVar');
    }

{% endhighlight %}

For handling custom session variables for the Admin application, add to each of the methods an extra parameter with the string `'admin'`, for example:

{% highlight php %}
Auth::has('myVar', 'admin');
{% endhighlight %}

<a name="sessions-terminate"></a>
### Sessions: Termination

You can easily destroy all custom values using the Auth class method `destroy`. If you want to delete all the framework session variables, including authentication, then use the method `end`.

{% highlight php %}

<?php 

namespace Niuware\WebFramework\Controllers;
    
use Niuware\WebFramework\Controller;
use Niuware\WebFramework\Auth;

final class MyController extends Controller {

    public function getMyPage(HttpRequest $request) {

        // Authentication session variables remain active
        Auth::destroy();

        // User and authentication session variables are destroyed
        Auth::end();
    }

{% endhighlight %}

For destroying session variables from the Admin application, add to each of the methods the parameter `'admin'`, for example:

{% highlight php %}
Auth::destroy('admin');

Auth::end('admin');
{% endhighlight %}

<a name="custom"></a>
## 7. Customization

Sometimes you need to have access to share classes and methods all over the Controllers and or Views. For this reason it is very easy to add functionality to the framework by using the Helper class.

<a name="custom-helper"></a>
### Customization: Helper Class

For adding global access functions and constants, add them in the Custom trait with public static modifiers: 

{% highlight php %}
[helpers/Custom.helper.php]

<?php

namespace Niuware\WebFramework\Helpers;

trait Custom {
    
    public static $myCustomVar = 'value';

    public static function myCustomFunc() {

        // Do something
    }
}

{% endhighlight %}

Then you can access them in `Controller` classes as follows:

{% highlight php %}
[app/controllers/MyController.controller.php]

<?php 

namespace Niuware\WebFramework\Controllers;
    
use Niuware\WebFramework\Controller;
use Niuware\WebFramework\Helper;

final class MyController extends Controller {

    public function getMyPage(HttpRequest $request) {

        Helper::myCustomFunc();

        $localVar = Helper::myCustomVar;

        ...
    }

{% endhighlight %}

<a name="custom-define"></a>
### Customization: Definition of Custom Classes

For adding custom helper classes add them in the path `helpers/` with the extension `.helper.php` and exist inside the namespace `Niuware\WebFramework\Helpers`. Here is a simple example:

{% highlight php %}
[app/helpers/MyCustomClass.helper.php]

<?php 

namespace Niuware\WebFramework\Helpers;

final class MyCustomClass {

    function __construct() {

    }

    public function someFunc() {

    }

    ...
}

{% endhighlight %}

When you want to access your custom class remember to use the namespace `Niuware\WebFramework\Helpers`:

{% highlight php %}
[app/controllers/MyController.controller.php]

<?php 

namespace Niuware\WebFramework\Controllers;
    
use Niuware\WebFramework\Controller;
use Niuware\WebFramework\Helpers;

final class MyController extends Controller {

    public function getMyPage(HttpRequest $request) {

        $myCustom = new Helpers\MyCustomClass();

        $myCustom->someFunc();

        ...
    }

{% endhighlight %}

<a name="api"></a>
## 8. API Classes

Niuware WebFramework can be used to create a RESTful API to build asynchronous Web applications and API services.

<a name="api-define"></a>
### API Classes: Definition

API classes should be add in the `app/api` directory with the extension `.api.php`. Also the classes should exist inside the namespace `Niuware\WebFramework\Api` and extend from the core class `Niuware\WebFramework\ApiResponse`. The filename **should be in lowercase** so your API URL's remain in lowercase. Here is an example of how it should look like:

{% highlight php %}
[app/api/MyApi.api.php]

<?php 

namespace Niuware\WebFramework\Api;

use Niuware\WebFramework\ApiResponse;

final class MyApi extends ApiResponse {

    ...
}

{% endhighlight %}

<a name="api-syntax"></a>
### API Classes: Method Syntax

As the application <a href="#routing">Routing</a> you can create your API URL paths as you need. For example, for the following URL:

> http://my_url/**api/cart/add_product**

you should have a corresponding declaration in a file called cart.api.php with a class `Cart` and a case insensitive method name like `methodname` or `MethodName` or `methodName`, etc. (NOT `method_name`). As stated before, it is not necessary to include "-" or "_", in your method name definition even you use this characters in your API URL path.

In this case the class can be defined like the following example:

{% highlight php %}
[app/api/Cart.api.php]

<?php 

namespace Niuware\WebFramework\Api;

use Niuware\WebFramework\ApiResponse;

final class Cart extends ApiResponse {

    public function addProduct(HttpRequest $request) {

    }

    // The following declarations will work as well
    public function addproduct(HttpRequest $request) {}
    public function AddProduct(HttpRequest $request) {}

    // The following private method won't be accessed
    private function addProduct(HttpRequest $request) {}
}

{% endhighlight %}

Notice that only `public` methods are accessible to an API call, so you define `private` methods as they will never be accessed even if the API URL path contains the name of a valid method.

<a name="api-protocol"></a>
### API Classes: Protocol Restriction

Same as the `Controller` classes, you can define <a href="#controllers-protocol">protocol restriction</a> using the prefix <em>get</em>, <em>post</em> or <em>delete</em> with your method. If you omit this prefix, the request will accept API calls via GET, POST and DELETE request methods. All other request methods will render an `HTTP 405 Method Not Allowed` error.

<a name="api-params"></a>
### API Classes: Request Parameters

To recieve parameters from an API call use the `HttpRequest $request` object for a GET, POST or DELETE request.

GET Request:

> http://my_url/api/cart/product/?**id=6**&**token=7458ABDG83**

{% highlight php %}
[app/api/Cart.api.php]

<?php 

namespace Niuware\WebFramework\Api;

use Niuware\WebFramework\ApiResponse;

final class Cart extends ApiResponse {

    public function getProduct(HttpRequest $request) {

        $request->id = '6';
        $request->token = '7458ABDG83';

        // Get the product details
    }
}

{% endhighlight %}

POST Request:

{% highlight js %}

// Using jQuery / Ajax

var requestData = {
    id : 6,
    token : '7458ABDG83'
};

...

$.ajax({
    type: "POST",
    url: "http://my_url/api/cart/product",
    dataType: 'json',
    data: requestData,
    ...
})

{% endhighlight %}

{% highlight http %}

Using HTTP native request

POST /api/cart/add_product HTTP/1.1
Host: my_url
Content-Type: application/json
Cache-Control: no-cache

{
	"id": 6, 
	"token": "7458ABDG83"
}


{% endhighlight %}

{% highlight php %}
[app/api/Cart.api.php]

<?php 

namespace Niuware\WebFramework\Api;

use Niuware\WebFramework\ApiResponse;

final class Cart extends ApiResponse {

    public function postProduct(HttpRequest $request) {

        $request->id = '6';
        $request->token = '7458ABDG83';

        // Create or edit product
    }
}

{% endhighlight %}

DELETE Request:

{% highlight js %}

// Using jQuery / Ajax

var requestData = {
    id : 6,
    token : '7458ABDG83'
};

...

$.ajax({
    type: "DELETE",
    url: "http://my_url/api/cart/product",
    dataType: 'json',
    data: requestData,
    ...
})

{% endhighlight %}

{% highlight http %}

Using HTTP native request

DELETE /api/cart/add_product HTTP/1.1
Host: my_url
Content-Type: application/json
Cache-Control: no-cache

{
	"id": 6, 
	"token": "7458ABDG83"
}


{% endhighlight %}

{% highlight php %}
[app/api/Cart.api.php]

<?php 

namespace Niuware\WebFramework\Api;

use Niuware\WebFramework\ApiResponse;

final class Cart extends ApiResponse {

    public function deleteProduct(HttpRequest $request) {

        $request->id = '6';
        $request->token = '7458ABDG83';

        // Delete the product
    }
}

{% endhighlight %}

> A DELETE request will only accept request parameters in JSON format, in other words, it will only process parameters from an 'application/json' CONTENT-TYPE method request. If you are using an HTML form, remember to send a JSON to your DELETE endpoint or use a POST request instead.

<a name="api-response"></a>
### API Classes: Response Rendering

An API endpoint will render a response in JSON format. For this you only need to set the data you want to render using the `response` attribute and finally call the `render` method as the following example:

{% highlight php %}
[app/api/Cart.api.php]

<?php 

namespace Niuware\WebFramework\Api;

use Niuware\WebFramework\ApiResponse;

final class Cart extends ApiResponse {

    public function postAddProduct(HttpRequest $request) {

        $request->id = '6';
        $request->token = '7458ABDG83';

        $this->response->error = false;
        $this->response->access_token = "7458ABDG83";
        $this->response->other_var = "other value";

        // Or bulk add.
        // If the second parameter is true, clears all previous
        // set attributes (the attribute 'error' remains unaffected)
        $this->response->add([
            'access_token' => "7458ABDG83",
            'other_var' => "other value"
        ], true);

        return $this->render();
    }
}

{% endhighlight %}

The output will be something like this:

{% highlight json %}

{
    "error" : false,
    "data" : {
        "access_token" : "7458ABDG83",
        "other_var" : "other value"
    }
}

{% endhighlight %}

<a name="security"></a>
## 9. Security

The core includes 3 simple methods to manage string hashing.

<a name="security-pass"></a>
### Security: Passwords

Use the methods `hash` and `verifyHash` from the `Security` core class to create and verify password strings.

{% highlight php %}
<?php 

namespace Niuware\WebFramework\Security;

final class MyClass {

    public function someMethod() {

        $savedPassword = Security::hash($newPassword);

        ...

        if (Security::verifyHash($inputPassword, $savedPassword)) {

            // Password is correct
        }
        else {

            // Password is incorrect
        }
    }
}

{% endhighlight %}

<a name="security-token"></a>
### Security: Tokens

Use the method `generateToken` from the `Security` core class to generate securily cryptographic token strings.

{% highlight php %}
<?php 

namespace Niuware\WebFramework\Security;

final class MyClass {

    public function someMethod() {

        $token = Security::generateToken();
    }
}

{% endhighlight %}

<a name="security-csrf"></a>
### Security: CSRF Token Form Validation

In your form, use the `csrfToken` function to create the hidden field which contains the CSRF token.

{% highlight twig %}

<form>
{% raw %}{{ csrfToken() }}{% endraw %}
</form>

{% endhighlight %}

The output will be:

{% highlight html %}

<form>
    <input type="hidden" name="csrf_token" value="token_will_be_here" />
</form>

{% endhighlight %}

In your controller verify the token by using the `verifyCsrfToken` method of the `Security` core class:

{% highlight php %}
[app/controllers/MyController.controller.php]

<?php 

namespace Niuware\WebFramework\Controllers;
    
use Niuware\WebFramework\Controller;
use Niuware\WebFramework\Security;

final class MyController extends Controller {

    public function getMyPage(HttpRequest $request) {

        if (Security::verifyCsrfToken($request->csrf_token)) {

            // do something
        }
    }

{% endhighlight %}

<a name="file"></a>
## 10. Files

It's very easy to get files from a POST request using the `HttpRequest` parameter. To get an uploaded file and move it to a directory use the following example:

POST Request:

{% highlight html %}

<!-- Using an HTML From -->
<form method="post" action="mypage">
    {% raw %}{{ csrfToken() }}{% endraw %}
    <input type="file" name="myfile" />
</form>

{% endhighlight %}

{% highlight javascript %}

// Using jQuery / Ajax

var form = new FormData();
form.append("myfile", "somefile.ext");

$.ajax({
    type: "POST",
    async : true,
    url: "http://my_url/my-page",
    mimeType: 'multipart/form-data',
    contentType : false,
    processData : false,
    headers : { "cache-control" : "no-cache" }
    data: form,
    ...
})

{% endhighlight %}

{% highlight http %}

Using HTTP native request

POST /api/media/upload HTTP/1.1
Host: my_url
Cache-Control: no-cache
Content-Type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW

------WebKitFormBoundary7MA4YWxkTrZu0gW
Content-Disposition: form-data; name="myfile"; filename=""
Content-Type: 


------WebKitFormBoundary7MA4YWxkTrZu0gW--

{% endhighlight %}

Controller:

{% highlight php %}
[app/controllers/MyController.controller.php]

<?php 

namespace Niuware\WebFramework\Controllers;
    
use Niuware\WebFramework\Controller;
use Niuware\WebFramework\Security;

final class MyController extends Controller {

    public function getMyPage(HttpRequest $request) {

        // When verifying a CSRF Token
        //if (Security::verifyCsrfToken($request->csrf_token)) {
        //}

        if ($request->hasFile('myfile')) {

            // Upload the file with default options
            $file = $request->getFile('myfile')->save();

            // Renaming the file
            // Notice no extension is needed.
            $request->getFile('myfile')->save('newName');

            // Renaming the file to a unique random 32 lenght filename
            $request->getFile('myfile')->save('unique');

            // Changing the save path
            $request->getFile('myfile')->save('', 'my/new/path');

            // Renaming the file and changing the save path
            $request->getFile('myfile')->save('newName', 'my/new/path');

            // By default a MIME type directory will be appended to the path
            // If the file is an image then the file path will be:
            // my/new/path/image
            // You can remove this setting the third argument as false
            $request->getFile('myfile')->save('newName', 'my/new/path', false);
        }

        ... 

        return $this->render();
    }

{% endhighlight %}

<a name="file-attrib"></a>
### Files: Attributes

The return value for the `save` method is an `Niuware\WebFramework\File` object, or `null` if there was an error uploading the file. You can retrieve the following attributes:

{% highlight php %}
[app/controllers/MyController.controller.php]

<?php 

namespace Niuware\WebFramework\Controllers;
    
use Niuware\WebFramework\Controller;

final class MyController extends Controller {

    public function getMyPage(HttpRequest $request) {

        if ($request->hasFile('myfile')) {

            // Upload the file with default options
            $file = $request->getFile('myfile')->save();

            $fileName = $file->filename;
            $fileType = $file->filetype;
            $filePath = $file->filepath;
            $fileNameAndPath = $file->filenameAndPath;
            $fileUrl = $file->public_url; // may be empty if the path is not public

            // Or you can have the following case as well

            if (($fileName = $request->getFile('myfile')->save('', 'public/assets/other/')->filename) !== null) {

                // save the $filename string somewhere
            }
        }

        ... 

        return $this->render();
    }

{% endhighlight %}

In the previous example the name for the file will be the same as the uploaded one (if the file exists, a timestamp will be appended to the original name of the uploaded file). 

The path will be automatically selected checking the MIME type (only image, video, audio; other MIME types will be uploaded to the  'public/assets/other' directory). For example an image file will be uploaded to `public/assets/image` by default. You can change the name and path using the parameters for the `move` method as `move(filename, path)`.

<a name="console"></a>
## 11. Console

You can use the framework console to execute commands such as migratinos. To access it just go to the terminal and type:

> ~$ php core/nwf {command} [command_args]

or if you enabled the web mode, go to your browser and type:

> http://my_url/console:nwf/{command}/{command_args}

You have to enable the console in your `settings.php` file [configuration](#install-constant). The following are the valid values for the console configuration:

<table class="reduced">
    <thead>
        <tr>
            <th>Option</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>terminal</td>
            <td>
                Enables the use of the console using the terminal command <em>nwf</em>. <br />
                For example: ~$ php core/nwf migrations rollback -d XXXXXXXX
            </td>
        </tr>
        <tr>
            <td>web</td>
            <td>
                Enables the use of the console using a web browser through the <em>console:nwf</em> path. <br />
                For example: http://my_url/console:nwf/migrations/rollback/-d/XXXXXXXX
            </td>
        </tr>
        <tr>
            <td>enabled</td>
            <td>
                Enables the use of the console using either the termianl of the web browser.
            </td>
        </tr>
        <tr>
            <td>disabled</td>
            <td>
                Disables the use of the console.
            </td>
        </tr>
    </tbody>
</table>

<a name="migration"></a>
## 12. Database Migrations

Use the power of database migration definitions to have a robust way to enhance your web application. Migrations are integrated into Niuware WebFramework using [Phinx](https://phinx.org/). Notice not all Phinx functionality is available through the Niuware WebFramework console.

<a name="migration-migrate"></a>
### Database Migrations: Migration definitions

To create a migration file use the command <strong>create</strong>:

Terminal mode:
> $ php core/nwf migrations create

Web mode:
> http://my_url/console:nwf/migrations/create

This will create a new migration class in the `app/migrations/migrations` folder as `MigrationVersion_vTimestamp.php`. Notice the MigrationVersion part of the file as you can use this number for targetting commands suchs as migrate and rollback. For example:

{% highlight php %}
[app/migrations/20170605063432_v1496644472.php]

<?php

use Niuware\WebFramework\Migration;
use Illuminate\Database\Schema\Blueprint;

class V1496644472 extends Migration
{
    /**
     * Illuminate\Database\Schema\Builder $schema
     * Use the $schema object to execute your migration queries
     */
    
    public function up()
    {
        
    }
    
    public function down()
    {
        
    }
}

{% endhighlight %}

Then use Eloquent (Blueprint class) to create your definition, for example:

{% highlight php %}
[app/migrations/20170605063432_v1496644472.php]

<?php

use Niuware\WebFramework\Migration;
use Illuminate\Database\Schema\Blueprint;

class V1496644472 extends Migration
{
    /**
     * Illuminate\Database\Schema\Builder $schema
     * Use the $schema object to execute your migration queries
     */
    
    public function up()
    {
        $this->schema->create('sources', function (Blueprint $table) {
            
            $table->increments('id');
            $table->string('source', 45);
        });
        
        $this->schema->create('users', function (Blueprint $table) {
            
            $table->bigIncrements('id');
            $table->integer('source_id')->unsigned();
            $table->timestamps();
            $table->string('account_id', 100);
            $table->boolean('is_valid');
            
            $table->foreign('source_id')->references('id')->on('sources');
        });

    public function down()
    {
        
    }
}

{% endhighlight %}

Then run the migrations with the command <strong>migrate</strong>:

Terminal mode:
> $ php core/nwf migrations migrate -t [MigrationVersion]

Web mode:
> http//my_url/console:nwf/migrations/migrate/-t/MigrationVersion

Notice that if you do not add the target for the migration (Migration class name), all migrations that haven't been run will be executed.

For more information on Eloquent syntax for migrations visit the documentation for:
<br />
[Tables](https://laravel.com/docs/master/migrations#tables) <br />
[Columns](https://laravel.com/docs/master/migrations#columns) <br />
[Indexes](https://laravel.com/docs/master/migrations#indexes)

> Notice that the previous documentation has an static access to the Schema class `Schema::method`, whilst in Niuware WebFramework the access is through an instance as `$this->schema->method`.

<a name="migration-rollback"></a>
### Database Migrations: Rollback

If you want to rollback use the command <strong>rollback</strong>:

Terminal mode:
> $ php core/nwf migrations rollback [-t MigrationVersion]

Web mode:
> http//my_url/console:nwf/migrations/rollback/-t/MigrationVersion

For more information on how to use the rollback -d command visit the Phinx [documentation](http://docs.phinx.org/en/latest/commands.html#the-rollback-command).

<a name="migration-seed"></a>
### Database Migrations: Seeding

To create a seeding file use the command <strong>seedcreate</strong>:

Terminal mode:
> $ php core/nwf migrations seedcreate [NameOfSeedClass]

Web mode:
> http//my_url/console:nwf/migrations/seedcreate/NameOfSeedClass

This will create a new seeding class in the `app/migrations/seeds` folder. For example:

{% highlight php %}

<?php

use Phinx\Seed\AbstractSeed;

class NameOfSeedClass extends AbstractSeed
{
    /**
     * Run Method.
     *
     * Write your database seeder using this method.
     *
     * More information on writing seeders is available here:
     * http://docs.phinx.org/en/latest/seeding.html
     */
    public function run()
    {

    }
}

{% endhighlight %}

Then use Phinx syntax to create your definition, for example:

{% highlight php %}

<?php

use Phinx\Seed\AbstractSeed;

class NameOfSeedClass extends AbstractSeed
{
    /**
     * Run Method.
     *
     * Write your database seeder using this method.
     *
     * More information on writing seeders is available here:
     * http://docs.phinx.org/en/latest/seeding.html
     */
    public function run()
    {
        $sourcesData = [
            ['source' => 'Service A'],
            ['source' => 'Service B'],
            ['source' => 'Service C'],
            ['source' => 'Service D']
        ];
        
        $sources = $this->table('sources');
        $sources->insert($sourcesData)->save();
    }
}

{% endhighlight %}

For more information on the Phynx syntax for seed definitions visit the [documentation](http://docs.phinx.org/en/latest/seeding.html#inserting-data)

Then run the seed with the command <strong>seedrun</strong>:

Terminal mode:
> $ php core/nwf migrations seedrun -s [NameOfSeedClass]

Web mode:
> http//my_url/console:nwf/migrations/seedrun/-s/NameOfSeedClass

Notice that if you do not add the name of the seed class name, all seed files will be run. Be careful as seeds do not look up for repeated data, so if you run all seeds twice, data will be duplicated.

<a name="migration-status"></a>
### Database Migrations: Status

You can output the migrations status using the command <strong>status</strong>

Terminal mode:
> $ php core/nwf migrations status

Web mode:
> http//my_url/console:nwf/migrations/status

<a name="exception"></a>
## 13. Exceptions

If there is a problem with the configuration of your Controller classes, view template files or other exceptions, the FrameworkException will be thrown and you will see the complete list of all thrown exceptions and errors on the screen. In general it is not needed to throw exceptions but you can throw a FrameworkException in your Controller class as follows:

{% highlight php %}
[app/controllers/MyController.controller.php]

<?php 

namespace Niuware\WebFramework\Controllers;
    
use Niuware\WebFramework\Controller;
use Niuware\WebFramework\FrameworkException;

final class MyController extends Controller {

    public function getMyPage(HttpRequest $request) {

        if ($somethingIsWrong) {

            throw new FrameworkException($message, $error_code);
        }

        return $this->render();
    }

{% endhighlight %}

> When debug mode is enabled, the trace of the Exception will not be displayed.

In the case of the API classes, you will see only the last error/exception directly in the JSON rendered response. 