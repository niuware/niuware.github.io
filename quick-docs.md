---
layout: page
title: Quick documentation
---

This is a quick documentation on how to use all of the available features in Niuware WebFramework.

1. <a href="#install">Installation</a>  
  1.1 <a href="#install-config">Configuration File</a>  
2. <a href="#routing">Routing</a>    
  2.1 <a href="#routing-main">Application Main Space</a>    
  2.2 <a href="#routing-admin">Application Admin Space</a>  
  2.3 <a href="#routing-spaces">Application Spaces</a>  
  2.4 <a href="#routing-map">Mapped Variables</a>  
  2.5 <a href="#routing-options">Options</a>  
  2.6 <a href="#routing-request">Custom Requests</a>  
  2.7 <a href="#routing-override">Overriding Methods</a>  
  2.8 <a href="#routing-api">API-Only Mode</a>  
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
  8.5 <a href="#api-multiple">Multiple Version Support</a> 
9. <a href="#security">Security</a>  
  9.1 <a href="#security-pass">Passwords</a>  
  9.2 <a href="#security-token">Tokens</a>  
  9.3 <a href="#security-csrf">CSRF Token Form Validation</a>  
10. <a href="#request">Requests</a>  
  10.1 <a href="#request-define">Definition</a>  
  10.2 <a href="#request-validate">Validation</a>  
  10.3 <a href="#request-mutate">Mutation</a>  
11. <a href="#file">Files</a>  
  11.1 <a href="#file-attrib">Attributes</a>  
12. <a href="#console">Console</a>  
13. <a href="#migration">Database Migrations</a>  
  13.1 <a href="#migration-migrate">Migration files</a>  
  13.2 <a href="#migration-seed">Seeding</a>  
  13.3 <a href="#migration-rollback">Rollback</a>  
  13.4 <a href="#migration-status">Status</a>  
14. <a href="#pagination">Pagination</a>  
15. <a href="#exception">Exceptions</a>
16. <a href="#compatibility">PHP < 7.0 compatibility</a>  

<a name="install"></a>
## 1. Installation

For using the Niuware WebFramework follow this steps:

1. Download the repository from [GitHub](https://github.com/niuware/web-framework.git).
2. Run `composer install` to install the dependencies. 

<a name="install-config"></a>
### Installation: Configuration File

The framework uses a single configuration file to store private information such as database connection strings, third party API tokens etc. It also contains the default values for the Web application. You can find this file in `App/Config/Settings.php`

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
                If your BASE_URL has a sub path (subdirectory), write it here.<br /> 
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

Web applications created with Niuware WebFramework have *application spaces* and the *application admin space*. For example suppose you create an online shop; you'll need the frontend side where all the products will be browsable by your customers, and an admin panel side where your staff will be able to add or edit products for the shop.

<a name="routing-main"></a>
### Routing: Application Main Space

The main application path views can be public (by default) or require a user login. For adding routes for the **main** space application you only need to edit the `App/Config/Routes.php` file.

For example, let's suppose you want people to access this sections in your web application:

> http://my_url/**home**<br />
> http://my_url/**my-cart**<br />
> http://my_url/**category/category-name**

Then your `Routes.php` file should look like this:

{% highlight php %}
[App/Config/Routes.php]

<?php 

namespace App\Config;

/**
 * Defines the routes for the web application
 */
final class Routes {
    
    public static $views = [
        'main' => [
            // Simple route
            'home' => ['use' => 'Home'], 

            // Login required
            'my-cart' => ['use' => 'Cart', 'require' => ['login']],  

            // Login and CSRF validation required
            'my-form' => ['use' => 'Cart', 'require' => ['login', 'csrf']],

            // Login and CSRF custom validation
            'my-form' => ['use' => 'Cart', 'require' => ['login' => false, 'csrf' => ['get', 'post', 'delete']]],

            // Mapped variables
            'category/{name}' => ['use' => 'Category'],

            // Overriding methods
            'login' => ['use' => 'Login@logout']

            // Overriding custom request
            'search' => ['use' => 'Search', 'request' => 'CustomSearchRequest']
            ...
        ],
        ...
    ];
}

{% endhighlight %}

In the previous example you can notice each path has an array value as well. This array has two keys: **use** which points to the Controller class that will listen to the path and **require**, that has values such as 'login' or 'csrf' and tells the framework if the path requires an active logged in session and/or a CSRF validation when sending data to the server (see <a href="#security-csrf">CSRF Token Form Validation</a> for more details). This values are set to false by default so you can omit the whole 'require' key. The usage of Controllers is detailed in the Controllers section of this page.

<a name="routing-admin"></a>
### Routing: Application Admin Space

All the application admin space path views require a user login by default. The framework will add the prefix `admin/` to all routes set for the Admin application. As with the previous Main application routing section, you only need to edit the `App/Config/Routes.php` file.

For example, let's suppose you want people to access this sections in your web application:

> http://my_url/admin/**home**<br />
> http://my_url/admin/**products**<br />
> http://my_url/admin/**accounts**

Then your `Routes.php` file should look like this:

{% highlight php %}
[App/Config/Routes.php]

<?php 

namespace App\Config;

/**
 * Defines the routes for the web application
 */
final class Routes {
    
    public static $views = [
        ...
        'admin' => [
            'home' => ['use' => 'Home'], 
            'products' => ['use' => 'Products'],
            'accounts' => ['use' => 'Accounts'],
            ...
        ]
    ];
}

{% endhighlight %}

As mentioned before, all paths for the admin side require a logged in session. Additionally an automatic CSRF validation will be executed within POST and DELETE requests. You can also activate or deactivate the CSRF validation for any request (GET, POST, DELETE) of any route as prefered.

<a name="routing-spaces"></a>
### Routing: Application Spaces

Just as the application admin space, you can create custom spaces. Each of the spaces has its own session so a login in the 'main' space, won't grant access to the 'admin' or any other spaces. This is very useful not only for splitting access to your application but to have a better order in your project.

Let's suppose you want an space called 'user', and you want to define the following routes:

> http://my_url/staff/**home**<br />
> http://my_url/staff/**settings**<br />

Then your `Routes.php` file should look like this:

{% highlight php %}
[App/Config/Routes.php]

<?php 

namespace App\Config;

/**
 * Defines the routes for the web application
 */
final class Routes {
    
    public static $views = [
        ...
        'staff' => [
            'home' => ['use' => 'Home', 'require' => ['login']], 
            'settings' => ['use' => 'Settings', 'require' => ['login']],
            ...
        ]
    ];
}

{% endhighlight %}

<a name="routing-map"></a>
### Routing: Mapped Variables

It is easy to map variables in a route path by declaring them between `{curly braces}`. For example, for the following route:

> http://my_url/product/edit/34/something-else

You can map it in the `Routes.php` file as:

{% highlight php %}
[App/Config/Routes.php]

<?php 

...    
    public static $views = [
        ...
        'main' => [
            'product/edit/{id}/{other}' => ['use' => 'Product'], 
            ...
        ]
    ];
}

{% endhighlight %}

With this you will recieve the `id` and `other` parameters inside the `HttpRequest` object in a controller method. See <a href="#controllers">controllers</a> for learning more about it.

<a name="routing-admin"></a>
### Routing: Options

You can define some extra options for a route. For this you only need to add the `require` array with the options you need. At the moment the following options are supported:

<table class="reduced">
    <tbody>
        <tr>
            <td>login</td>
            <td>Defines if the route requires a valid session to be accessed. You can define either true/false to verify the session.</td>
        </tr>
        <tr>
            <td>csrf</td>
            <td>Defines if the route requires a valid CSRF token to be accessed. You can define either of the request methods to verify (get, post, and/or delete).</td>
        </tr>
    </tbody>
</table>

Here is an example using routing options. The first route will ignore a valid session even if it's contained in the <a href="#routing-admin">Application Admin Space</a> (which defines a login required by default). The second route will validate the CSRF token only if it is accessed through a POST or DELETE request method. The third route will verify the CSRF token for all requests and a valid session:

{% highlight php %}
[App/Config/Routes.php]

<?php 

...    
    public static $views = [
        ...
        'admin' => [
            'product' => ['use' => 'Product', 'require' => ['login' => false]], 
            'cart' => ['use' => 'Cart', 'require' => ['csrf' => ['post', 'delete']]], 
            ...
        ],
        'main' => [
            'special-contact' => ['use' => 'Contact', 'require' => ['login', 'csrf']]
        ]
    ];
}

{% endhighlight %}

<a name="routing-request"></a>
### Routing: Custom Requests

Sometimes you will want to reuse custom <a href="#request">Request</a> classes. In this case, you need to add the `request` parameter with the name of the `Request` class you require. Here is an example:

{% highlight php %}
[App/Config/Routes.php]

<?php 

...    
    public static $views = [
        ...
        'main' => [
            'special' => ['use' => 'Product', 'request' => 'SearchRequest'], 
            ...
        ]
    ];
}

{% endhighlight %}

<a name="routing-override"></a>
### Routing: Overriding Methods

By default the framework will try to execute a method which matches the path in the route. You can override this feature by defining your controller as follows:

{% highlight php %}
[App/Config/Routes.php]

<?php 

...    
    public static $views = [
        ...
        'main' => [
            'special' => ['use' => 'Product@index'], 
            ...
        ]
    ];
}

{% endhighlight %}

In the previous example the url: http://my_url/special will load the `Product` controller and execute the `index` method, either `getIndex` or `postIndex` depending on the request method to your server. See <a href="#controllers-protocol">Protocol Restriction</a> for more details.

<a name="routing-api"></a>
### Routing: API-Only Mode

You can also leave the routes empty to get an `HTTP 403 response`. This is useful when you want to use the framework only as an API, without any public web access:

{% highlight php %}
[App/Config/Routes.php]

<?php 

namespace App\Config;

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

All controllers inherit from the Niuware WebFramework core class `Controller` and must be placed in the `App/Controllers` directory. The name of the file and the class name **must match** as well. A controller class file must exist inside the namespace `App\Controllers`. Here is an example of how it should look like:

{% highlight php %}
[App/Controllers/MyController.php]

<?php 

namespace App\Controllers;
    
use Niuware\WebFramework\Application\Controller;

final class MyController extends Controller {

    ...
}

{% endhighlight %}

For the application Admin space, the controller class files should be in the `Controllers/Admin` subdirectory and use the `App\Controllers\Admin` namespace:

{% highlight php %}
[App/Controllers/Admin/MyAdminController.php]

<?php 

namespace App\Controllers\Admin;
    
use Niuware\WebFramework\Application\Controller;

final class MyAdminController extends Controller {

    ...
}

{% endhighlight %}

For other application spaces, the controllers class files should be located in the `Controllers/NameOfSpace` subdirectory and use the `App\Controllers\NameOfSpace` namespace. For example:

{% highlight php %}
[App/Controllers/NameOfSpace/MyController.php]

<?php 

namespace App\Controllers\NameOfSpace;
    
use Niuware\WebFramework\Application\Controller;

final class MyController extends Controller {

    ...
}

{% endhighlight %}

<a name="controllers-access"></a>
### Controllers: Calls

Controllers are there for listening to the routes you defined. There is no need to create a controller class for each different path because each path will answer to a method with its corresponding name. For example, suppose you have this path:

> http://my_url/**my-cart**

And its route is defined like this:

{% highlight php %}
[App/Config/Routes.php]

<?php
...

'my-cart' => ['use' => Cart]

...
{% endhighlight %}

then the controller like this:

{% highlight php %}
[App/Controllers/Cart.php]

<?php 

namespace App\Controllers;
    
use Niuware\WebFramework\Application\Controller;

final class Cart extends Controller {

}

{% endhighlight %}

Notice that **`Cart`** was defined in the `Routes.php` file as the controller who will listen to the path **`my-cart`**. Also notice that the controller class has the name **`Cart.php`**. 

Now the `Cart` controller class will be called when a user access this path, but nothing will happen. We are still missing to define the method that will be executed. This is as simple as adding a public method with the same name as the path, in this case:

{% highlight php %}
[App/Controllers/Cart.php]

<?php 

namespace App\Controllers;
    
use Niuware\WebFramework\Application\Controller;
use Niuware\WebFramework\Http\HttpRequest;

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
[App/Controllers/Cart.php]

<?php 

namespace App\Controllers;
    
use Niuware\WebFramework\Application\Controller;
use Niuware\WebFramework\Http\HttpRequest;

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

The GET protocol method will recieve the values in the `HttpRequest` object `$request` with the names you defined in the `Routes.php` file. For example if the route is:

{% highlight php %}
[App/Config/Routes.php]

<?php
...

'my-cart/{cartName}/{user}' => ['use' => Cart]

...
{% endhighlight %}

Then you can access those values as follows:

{% highlight php %}
<?php 

...

    public function getMyCart(HttpRequest $request) {

        $request->cartName = param_0_value;
        $request->user = param_1_value;
    }
...
{% endhighlight %}

You can also receive GET request parameters as a query string, for example:

> http://my_url/my-cart**/?param0=value0&param1=value1**

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

using the previous route example, then your GET protocol method will recieve the parameters as:

{% highlight php %}
<?php 

...

    public function getMyCart(HttpRequest $request) {

        // From the URL
        $request->cartName = param0;
        $request->user = param1;

        // From the query string
        $request->param2 = value2;
        $request->param3 = value3;
    }
...
{% endhighlight %}

<a name="controllers-protocol-post"></a>
### Controllers: POST Protocol Methods

The request parameters for a POST protocol method can be placed as part of the url just as the GET Protocol methods: 

> http://my_url/my-cart/**param_0_value**/**param_1_value**/ ...

{% highlight php %}
[App/Config/Routes.php]

<?php
...

'my-cart/{cartName}/{user}' => ['use' => Cart]

...
{% endhighlight %}

The POST protocol method will recieve the values in an `HttpRequest` object `$request` as:

{% highlight php %}
<?php 

...

    public function postMyCart(HttpRequest $request) {

        $request->cartName = param_0_value;
        $request->user = param_1_value;
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

> Although DELETE requests are accepted it is reserved for being used by API classes. By default, a DELETE request method will only process request parameters in JSON format. If you want to use a DELETE request method, remember to send your data as a JSON.

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
[App/Controllers/Cart.php]

<?php 

namespace App\Controllers;
    
use Niuware\WebFramework\Application\Controller;
use Niuware\WebFramework\Http\HttpRequest;

final class Cart extends Controller {

    public function getMyCart(HttpRequest $request) {

        // Do something here

        $otherController = new OtherController();

        // Additionally set controller options like
        // the view file name. For example:
        $otherController->view = "other.twig";

        return $otherController->getOtherMethod($request);
    }
}

{% endhighlight %}

If you want to redirect the browser, call the `render` method with the name of the path:

{% highlight php %}
[App/Controllers/Cart.php]

<?php 

namespace App\Controllers;
    
use Niuware\WebFramework\Application\Controller;
use Niuware\WebFramework\Http\HttpRequest;

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
[App/Controllers/Cart.php]

<?php 

namespace App\Controllers;
    
use Niuware\WebFramework\Application\Controller;
use Niuware\WebFramework\Http\HttpRequest;
use Niuware\WebFramework\Http\Response;

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

All models inherit from the Illuminate\Database\Eloquent class `Model` and must be placed in the `App/models` directory. The model class file must exist inside the namespace `App\Models`. Here is an example of how it should look like:

{% highlight php %}
[App/Models/Product.php]

<?php

namespace App\Models;
    
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

All views must be placed in the `public/views/route-path` directory and their file must be defined with the extension `.twig`. For the case of application spaces and application admin space views, the files should be inside the `public/views/spaceName/route-path` subdirectory. The content of the views use Twig syntax, for more information visit the [Twig documentation](https://twig.sensiolabs.org/doc/2.x/).

By default, the framework will load a view filename that matches the current loaded path. For example for the next URLs:

> http://my_url/cart
> http://my_url/cart/edit/{id}

the framework will try to load the following view files:

`public/views/cart/index.twig`<br/>
`public/views/cart/edit.twig`

You can change the name of the view filename to load by setting the attribute `view` as shown in section Views: <a href="#views-attributes">Template Attributes</a>.

For the application Admin space, all views filenames should be in the `views/admin/route-path` subdirectory. For example for the next URLs:

> http://my_url/admin/account <br />
> http://my_url/admin/account/edit

`public/views/admin/account/index.twig` <br/>
`public/views/admin/account/edit.twig`

And the same for other application spaces:

`public/views/spaceName/my-path/my-view.twig`

<a name="views-render"></a>
### Views: Rendering

To render a view template file, you need to tell the controller to do it. This is done by calling the `render` method. For example for the following URL:

> http://my_url/my-cart

we can simply call the `render` method as this:

{% highlight php %}
[App/Controllers/Cart.php]

<?php 

namespace App\Controllers;
    
use Niuware\WebFramework\Application\Controller;
use Niuware\WebFramework\Http\HttpRequest;

final class Cart extends Controller {

    public function getIndex(HttpRequest $request) {

        // By default it will render the public/views/cart/index.twig file
        return $this->render();
    }

    public function getMyOtherCart(HttpRequest $request) {

        // You can also redirect to another controller adding a valid path 
        // set on the application Routes.php file
        // For more details see the Controllers: Recycling section
        return $this->render('some-other-path');
    }
}

{% endhighlight %}

If you want to specify the filename of the view to load, simply set the template attribute as <a href="#views-attributes-view">described here</a>.

> If you are using **PHP** as the template renderer change your view template file names from *xyz.twig* to *xyz.php*. Also be sure to set *'php'* as the `DEFAULT_RENDERER` value in your application <a href="#install-config">settings file</a>.

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
            <td>main</td>
            <td>main.twig<br /> admin/main.twig</td>
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
[MyController.php]

<?php

final class MyController extends Controller {

    public function getMyPage(HttpRequest $request) {

        $this->view = "my-controller/view_filename.twig";

        ...

        return $this->render();
    }

{% endhighlight %}

Output:

{% highlight html %}

Loaded file: public/views/my-controller/view_filename.twig

or when using PHP as renderer:

Loaded file: public/views/my-controller/view_filename.php

{% endhighlight %}

<a name="views-binding"></a>
### Views: View/Controller Binding

You can bind variables from a controller to a view by assigning new properties to the `Controller` object. For example let's suppose you need to render some array:

{% highlight php %}
[App/Controllers/MyController.php]

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
[public/views/my-controller.twig]

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
[public/views/my-controller.php]

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

You can use the `TwigFilters.php` and `TwigFunctions.php` classes to define custom functions and filters. For example:

{% highlight php %}

<?php
[App/Helpers/TwigFunctions.php]

namespace App\Helpers;

use Niuware\WebFramework\Application\Helper;

class TwigFunctions {
    
    public function myCustomFunc($params) {

        // Notice that $params is an array 
        // $params[0] = 'something'
        // $params[1] = 'other thing'
        
        return Helper::myHelperFunc($params);
    }
}


{% endhighlight %}

And use it in the view as:

{% highlight twig %}
[public/views/my-controller/my-view.twig]

...
<div>
    {% raw %}
    {{ myCustomFunc('something', 'other thing') }}
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
[public/views/my-controller/my-view.twig]

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

The `Auth` class can help you verify if a user has successfully logged in to either the Main or Admin application. For this you can use the `grantAuth` or `revokeAuth` methods. Usually this methods will be called in the `Login` controller.

The Niuware WebFramework comes with a default configuration for auto logging a user who navigates to login-protected views as you can see in the following `Login` controller:

{% highlight php %}
[Controllers/Login.php]

<?php 

namespace App\Controllers;
    
use Niuware\WebFramework\Application\Controller;
use Niuware\WebFramework\Http\HttpRequest;
use Niuware\WebFramework\Auth\Auth;

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

namespace App\Controllers;
    
use Niuware\WebFramework\Application\Controller;
use Niuware\WebFramework\Http\HttpRequest;
use Niuware\WebFramework\Auth\Auth;

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

namespace App\Controllers;
    
use Niuware\WebFramework\Application\Controller;
use Niuware\WebFramework\Http\HttpRequest;
use Niuware\WebFramework\Auth\Auth;

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

namespace App\Controllers;
    
use Niuware\WebFramework\Application\Controller;
use Niuware\WebFramework\Http\HttpRequest;
use Niuware\WebFramework\Auth\Auth;

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

For handling custom session variables for the application Admin space, add to each of the methods an extra parameter with the string `'admin'`, for example:

{% highlight php %}
Auth::has('myVar', 'admin');
{% endhighlight %}

And for other application spaces just use the extra parameter with the string name of the space, for example:

{% highlight php %}
Auth::has('myVar', 'staff');
{% endhighlight %}

<a name="sessions-terminate"></a>
### Sessions: Termination

You can easily destroy all custom values using the Auth class method `destroy`. If you want to delete all the framework session variables, including authentication, then use the method `end`.

{% highlight php %}

<?php 

namespace App\Controllers;
    
use Niuware\WebFramework\Application\Controller;
use Niuware\WebFramework\Http\HttpRequest;
use Niuware\WebFramework\Auth\Auth;

final class MyController extends Controller {

    public function getMyPage(HttpRequest $request) {

        // Authentication session variables remain active
        Auth::destroy();

        // User and authentication session variables are destroyed
        Auth::end();
    }

{% endhighlight %}

For destroying session variables from the application Admin space or other spaces, add to each of the methods the parameter `'admin'`, or the name of the space. For example:

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
[Helpers/Custom.php]

<?php

namespace App\Helpers;

trait Custom {
    
    public static $myCustomVar = 'value';

    public static function myCustomFunc() {

        // Do something
    }
}

{% endhighlight %}

Then you can access them in `Controller` classes as follows:

{% highlight php %}
[App/Controllers/MyController.php]

<?php 

namespace App\Controllers;
    
use Niuware\WebFramework\Application\Controller;
use Niuware\WebFramework\Http\HttpRequest;
use Niuware\WebFramework\Application\Helper;

final class MyController extends Controller {

    public function getMyPage(HttpRequest $request) {

        Helper::myCustomFunc();

        $localVar = Helper::myCustomVar;

        ...
    }

{% endhighlight %}

<a name="custom-define"></a>
### Customization: Definition of Custom Classes

For adding custom helper classes add them in the path `Helpers/` within the namespace `App\Helpers`. Here is a simple example:

{% highlight php %}
[App/Helpers/MyCustomClass.php]

<?php 

namespace App\Helpers;

final class MyCustomClass {

    function __construct() {

    }

    public function someFunc() {

    }

    ...
}

{% endhighlight %}

When you want to access your custom class remember to use the namespace `App\Helpers`:

{% highlight php %}
[App/Controllers/MyController.php]

<?php 

namespace App\Controllers;
    
use Niuware\WebFramework\Application\Controller;
use Niuware\WebFramework\Http\HttpRequest;
use App\Helpers;

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

API classes should be add in the `App/Api` directory. Also the classes should exist inside the namespace `App\Api` and extend from the core class `Niuware\WebFramework\Http\ApiResponse`. The filename **should be in lowercase** so your API URL's remain in lowercase. Here is an example of how it should look like:

{% highlight php %}
[App/Api/MyApi.php]

<?php 

namespace App\Api;

use Niuware\WebFramework\Http\ApiResponse;

final class MyApi extends ApiResponse {

    ...
}

{% endhighlight %}

<a name="api-syntax"></a>
### API Classes: Method Syntax

As the application <a href="#routing">Routing</a> you can create your API URL paths as you need. For example, for the following URL:

> http://my_url/**api/cart/add_product**

you should have a corresponding declaration in a file called cart.php with a class `Cart` and a case insensitive method name like `methodname` or `MethodName` or `methodName`, etc. (NOT `method_name`). As stated before, it is not necessary to include "-" or "_", in your method name definition even you use this characters in your API URL path.

In this case the class can be defined like the following example:

{% highlight php %}
[App/Api/Cart.php]

<?php 

namespace App\Api;

use Niuware\WebFramework\Http\ApiResponse;

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
[App/Api/Cart.php]

<?php 

namespace App\Api;

use Niuware\WebFramework\Http\ApiResponse;

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
[App/Api/Cart.php]

<?php 

namespace App\Api;

use Niuware\WebFramework\Http\ApiResponse;

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
[App/Api/Cart.php]

<?php 

namespace App\Api;

use Niuware\WebFramework\Http\ApiResponse;

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
[App/Api/Cart.php]

<?php 

namespace App\Api;

use Niuware\WebFramework\Http\ApiResponse;

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

<a name="api-multiple"></a>
### API Classes: Multiple Version Support

The framework supports multiple versions for your API. You just need to add the version pattern as `v#.#.#` to the URL and add the API classes inside a directory corresponding to the version. 

For example if you access:

> http://my_url/api/cart/product

the framework will load the default class version which should be found in `App/Api/Product`. On the contrary, if you access:

> http://my_url/api/**v2.1.0**/cart/product

then the framework will try to load the class version found in the subdirectory v2.1.0 -> **V210**: `App/Api/V210/Product`.

Notice that there is no fallback for the default version if the class version, so if the version is not found an *API Not found class* error code will be rendered instead.

<a name="security"></a>
## 9. Security

The core includes 3 simple methods to manage string hashing.

<a name="security-pass"></a>
### Security: Passwords

Use the methods `hash` and `verifyHash` from the `Security` core class to create and verify password strings.

{% highlight php %}
<?php 

use Niuware\WebFramework\Auth\Security;

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

use Niuware\WebFramework\Auth\Security;

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

You can set the route for automatically validating the CSRF token by defining the `csrf` value in the require array for your routes:

{% highlight php %}
[App/Config/Routes.php]

...

            // Login and CSRF validation required
            'my-form' => ['use' => 'Cart', 'require' => ['csrf']],
}

{% endhighlight %}

If you send a request with an invalid CSRF Token to a CSRF protected route, then the framework will render an `HTTP 403 response`.

Note that by default, all POST and DELETE requests within the Application Admin space will be CSRF validated. If you additionally need a CSRF validation for GET requests in this applicacion space, add the `require => ['csrf']` attribute to the route.

If you want to implement the validation manually within your controller, you can either use the `hasValidCsrf` method of the `HttpRequest` core class which validated the application CSRF token with the recieved `csrf_token` parameter (for example when using the previos `csrfToken` function in your Twig template):

{% highlight php %}
[App/Controllers/MyController.php]

<?php 

namespace App\Controllers;
    
use Niuware\WebFramework\Application\Controller;
use Niuware\WebFramework\Http\HttpRequest;
use Niuware\WebFramework\Auth\Security;

final class MyController extends Controller {

    public function getMyPage(HttpRequest $request) {

        if ($request->hasValidCsrf()) {

            // do something
        }
    }

{% endhighlight %}

or use the `verifyCsrfToken` method of the `Security` core class, where you can pass any parameter to validate with the application CSRF token:

{% highlight php %}
[App/Controllers/MyController.php]

<?php 

namespace App\Controllers;
    
use Niuware\WebFramework\Application\Controller;
use Niuware\WebFramework\Http\HttpRequest;
use Niuware\WebFramework\Auth\Security;

final class MyController extends Controller {

    public function getMyPage(HttpRequest $request) {

        if (Security::verifyCsrfToken($request->csrf_token)) {

            // do something
        }
    }

{% endhighlight %}

<a name="request"></a>
## 10. Requests

By default each controller method recieves the request in an `Niuware\WebFramework\Http\HttpRequest` object, but you can define your own Request classes and its independent validation rules. 

<a name="request-define"></a>
## Requests: Definition

All requests inherit from the Niuwre WebFramework core class `Request` and implement the `RequestInterface`. A request class file must exist inside the namespace `App\Requests`. If you are inside a subspace then you will need to append the correct namespace path. For example for the application Admin space the request class files shoudl be in the `Requests/Admin` subdirectory and use the `App\Requests\Admin namespace:

{% highlight php %}
[App/Requests/MyRequest.php]

<?php 

namespace App\Requests;
    
use Niuware\WebFramework\Http\Request;
use Niuware\WebFramework\Http\RequestInterface;

final class MyRequest extends Request implements RequestInterface {

    function __construct(array $params, $method = "") {
        parent::__construct($params, $method);
    }
    
    public function rules() {
        
        return [];
    }
    
    public function validate() {
        parent::validateWith($this->rules());
    }

{% endhighlight %}

<a name="request-validate"></a>
## Requests: Validation

You can add validation rules for your custom request as follows:

{% highlight php %}
[App/Requests/MyRequest.php]

<?php 

namespace App\Requests;
    
use Niuware\WebFramework\Http\Request;
use Niuware\WebFramework\Http\RequestInterface;

final class MyRequest extends Request implements RequestInterface {

    ...
    
    public function rules() {
        
        return [
            // Rules for GET request method
            'get' => [
                'fieldName' => [
                    'rule|parameter' => 'Error message string'
                ],
                'otherFieldName' => [
                    ...
                ]
            ],
            // Rules for POST request method
            'post' => [
                'fieldName' => [
                    'rule|parameter' => 'Error message string'
                ],
                ...
            ],
            // Rules for DELETE request method
            'delete' => [
                'fieldName' => [
                    'rule|parameter' => 'Error message string'
                ],
                ...
            ]
        ];
    }
    
    ...

{% endhighlight %}

As you may notice, the rules can be set independently for each Request Method (GET, POST or DELETE). The current valid rules are: 

<table class="variant">
    <thead>
        <tr>
            <th>Rule</th>
            <th>Parameters</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>required</td>
            <td>boolean (optional)</td>
            <td>
                Sets the field as required in the request. If the parameter is true, the field will be considered as valid if the request contains it even its value is empty.
            </td>
        </tr>
        <tr>
            <td>pattern</td>
            <td>string</td>
            <td>
                Sets a pattern to take for validating the field. The pattern string is defined in the parameter.
            </td>
        </tr>
        <tr>
            <td>numeric</td>
            <td>-</td>
            <td>
                Validates if the field is numeric.
            </td>
        </tr>
        <tr>
            <td>minlength</td>
            <td>number</td>
            <td>
                Sets a minimum string length for the field.
            </td>
        </tr>
        <tr>
            <td>maxlength</td>
            <td>number</td>
            <td>
                Sets a maximum string length for the field.
            </td>
        </tr>
    </tbody>
</table>

When you use a custom Request class in your controller the validation will be executed during the request and you can verify its result using the `isValid` or `getErrors` methods as in the following example:

{% highlight php %}
[App/Controllers/MyController.php]

<?php 

namespace App\Controllers;
    
use Niuware\WebFramework\Application\Controller;

use App\Requests\MyRequest

final class MyController extends Controller {

    public function getMyPage(MyRequest $request) {

        $valid = $request->validation()->isValid();
        $errors = $request->validation()->getErrors();

        $firstError = $request->validation()->getFirstError();
        $lastError = $request->validation()->getLastError();
        ... 

        return $this->render();
    }

{% endhighlight %}

<a name="request-mutate"></a>
## Requests: Mutation

A request validation ensures the user has sent valid data to your application, but the ability to automtically mutate this data helps you optmize your controller code. For example let's suppose you want to cast a variable to a certain type, or execute a function over the value, in this case you can add mutable rules to your `Request` class. The current available mutable rules are:

<table class="variant">
    <thead>
        <tr>
            <th>Rule</th>
            <th>Parameters</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>default</td>
            <td>string (optional)</td>
            <td>
                Adds the field with the default value if it does not exist or mutate the value if it is different from the parameter value.
            </td>
        </tr>
        <tr>
            <td>cast</td>
            <td>-</td>
            <td>
                Casts the field as a given valid type: bool, int, double, object, string, or array.
            </td>
        </tr>
        <tr>
            <td>callback</td>
            <td>boolean (optional)</td>
            <td>
                Executes a PHP or global valid function over the field. If the parameters is true, the function mutates the value by reference.
            </td>
        </tr>
    </tbody>
</table>

In the following example the field `search` will be trimmed, and then cast to an integer type. The `order` field will be added to the request if does not exist with a value of `ASC`. It also will be assigned de `ASC` value if it has a different value from `DESC`:

{% highlight php %}
[App/Requests/MyRequest.php]

<?php 

namespace App\Requests;
    
use Niuware\WebFramework\Http\Request;
use Niuware\WebFramework\Http\RequestInterface;

final class SearchRequest extends Request implements RequestInterface {

    ...
    
    public function rules() {
        
        return [
            // Rules for GET request method
            'get' => [
                'search' => [
                    'callback' => 'trim',
                    'cast' => 'int'
                ],
                'order' => [
                    'default|DESC' => 'ASC'
                ]
            ]
        ];
    }
    
    ...

{% endhighlight %}

Finally you can use your request in any controller method as:

{% highlight php %}
[App/Controllers/MyController.php]

<?php 

namespace App\Controllers;
    
use Niuware\WebFramework\Application\Controller;

use App\Requests\MyRequest

final class MyController extends Controller {

    public function getMyPage(SearchRequest $request) {

        if ($request->validation()->isValid()) {

            // $search is a trimmed string cast to an integer type
            $search = $request->search;

            // $order is either 'ASC' or 'DESC'. By default will be 'ASC'
            $order = $request->order;
        }

        return $this->render();
    }

{% endhighlight %}

<a name="file"></a>
## 11. Files

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
[App/Controllers/MyController.php]

<?php 

namespace App\Controllers;
    
use Niuware\WebFramework\Application\Controller;
use Niuware\WebFramework\Http\HttpRequest;
use Niuware\WebFramework\Auth\Security;

final class MyController extends Controller {

    public function getMyPage(HttpRequest $request) {

        // When verifying a CSRF Token
        //if (Security::verifyCsrfToken($request->csrf_token)) {
        //}

        if ($request->hasFile('myfile')) {

            // Use one of the following options to save a file

            // Option 1
            // Upload the file with default options
            $file = $request->getFile('myfile')->save();

            // Option 2
            // Renaming the file
            // Notice no extension is needed
            $request->getFile('myfile')->save('newName');

            // Option 3
            // Renaming the file to a unique random 32 lenght filename
            $request->getFile('myfile')->save('unique');

            // Option 4
            // Changing the save path
            $request->getFile('myfile')->save('', 'my/new/path');

            // Option 5
            // Renaming the file and changing the save path
            $request->getFile('myfile')->save('newName', 'my/new/path');

            // Option 6
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

The return value for the `save` method is an `Niuware\WebFramework\Http\File` object, or `null` if there was an error uploading the file. You can retrieve the following attributes:

{% highlight php %}
[App/Controllers/MyController.php]

<?php 

namespace App\Controllers;
    
use Niuware\WebFramework\Application\Controller;
use Niuware\WebFramework\Http\HttpRequest;

final class MyController extends Controller {

    public function getMyPage(HttpRequest $request) {

        if ($request->hasFile('myfile')) {

            // Upload the file with default options
            $file = $request->getFile('myfile')->save();

            $fileName = $file->filename;
            $fileExtension = $file->extension;
            $fileSize = $file->size;
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
## 12. Console

You can use the framework console to execute commands such as migratinos. To access it just go to the terminal and type:

> ~$ php vendor/niuware/webframework/src/nwf {command} [command_args]

or if you enabled the web mode, go to your browser and type:

> http://my_url/console/{command}/{command_args}

You have to enable the console in your `Settings.php` file [configuration](#install-constant). The following are the valid values for the console configuration:

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
                For example: ~$ php vendor/niuware/webframework/src/nwf migrations rollback -d XXXXXXXX
            </td>
        </tr>
        <tr>
            <td>web</td>
            <td>
                Enables the use of the console using a web browser through the <em>console</em> path. <br />
                For example: http://my_url/console/migrations/rollback/-d/XXXXXXXX
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
## 13. Database Migrations

Use the power of database migration definitions to have a robust way to enhance your web application. Migrations are integrated into Niuware WebFramework using [Phinx](https://phinx.org/). Notice not all Phinx functionality is available through the Niuware WebFramework console.

<a name="migration-migrate"></a>
### Database Migrations: Migration definitions

To create a migration file use the command <strong>create</strong>:

Terminal mode:
> $ php vendor/niuware/webframework/src/nwf migrations create

Web mode:
> http://my_url/console/migrations/create

This will create a new migration class in the `App/Migrations/Migrations` directory as `MigrationVersion_vTimestamp.php`. Notice the MigrationVersion part of the file as you can use this number for targetting commands suchs as migrate and rollback. For example:

{% highlight php %}
[App/Migrations/20170605063432_v1496644472.php]

<?php

use Niuware\WebFramework\Database\Migration;
use Illuminate\Database\Schema\Blueprint;

class V1496644472 extends Migration
{
    /**
     * Illuminate\Database\Schema\Builder $schema
     * Use the $schema object to execute your migration queries
     *
     * Created on Y/m/d h:i:s
     * Migration comments:
     * 
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
[App/Migrations/20170605063432_v1496644472.php]

<?php

use Niuware\WebFramework\Database\Migration;
use Illuminate\Database\Schema\Blueprint;

class V1496644472 extends Migration
{
    /**
     * Illuminate\Database\Schema\Builder $schema
     * Use the $schema object to execute your migration queries
     *
     * Created on Y/m/d h:i:s
     * Migration comments:
     * 
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
> $ php vendor/niuware/webframework/src/nwf migrations migrate -t [MigrationVersion]

Web mode:
> http//my_url/console/migrations/migrate/-t/MigrationVersion

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
> $ php vendor/niuware/webframework/src/nwf migrations rollback [-t TargetMigrationVersion]
> $ php vendor/niuware/webframework/src/nwf migrations rollback [-d RollbackToDate]

Web mode:
> http//my_url/console/migrations/rollback/-t/TargetMigrationVersion
> http//my_url/console/migrations/rollback/-d/RollbackToDate

For more information on how to use the rollback -t and -d commands, visit the Phinx [documentation](http://docs.phinx.org/en/latest/commands.html#the-rollback-command).

<a name="migration-seed"></a>
### Database Migrations: Seeding

To create a seeding file use the command <strong>seedcreate</strong>:

Terminal mode:
> $ php vendor/niuware/webframework/src/nwf migrations seedcreate [NameOfSeedClass]

Web mode:
> http//my_url/console/migrations/seedcreate/NameOfSeedClass

This will create a new seeding class in the `App/Migrations/Seeds` directory. For example:

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
> $ php vendor/niuware/webframework/src/nwf migrations seedrun -s [NameOfSeedClass]

Web mode:
> http//my_url/console/migrations/seedrun/-s/NameOfSeedClass

Notice that if you do not add the name of the seed class name, all seed files will be run. Be careful as seeds do not look up for repeated data, so if you run all seeds twice, data will be duplicated.

<a name="migration-status"></a>
### Database Migrations: Status

You can output the migrations status using the command <strong>status</strong>

Terminal mode:
> $ php vendor/niuware/webframework/src/nwf migrations status

Web mode:
> http//my_url/console/migrations/status

<a name="pagination"></a>
## 14. Pagination

When querying data from your database it is easy to paginate results using the `Paginate` core class. Here is a basic example of how to use this feature:

First, set the data in your controller class: 

{% highlight php %}
[App/Controllers/MyController.php]

<?php 

namespace App\Controllers;
    
use Niuware\WebFramework\Application\Controller;
use Niuware\WebFramework\Http\HttpRequest;
use Niuware\WebFramework\Pagination\Paginate;

use App\Models\Item;

final class MyController extends Controller {

    public function getMyPage(HttpRequest $request) {

        // Let's suppose you have an 'Item' model
        $items = Item::orderBy('name', 'asc')->get();

        $this->paginate = new Paginate();

        // You can optionally customize the number of items per page
        $this->paginate->itemsPerPage = 15

        $this->paginate->paginate($items, $request);

        return $this->render();
    }

{% endhighlight %}

In the view, use the method `data` in the paginate object to display the items por the current page.

{% highlight twig %}
[public/views/my-page.twig]

...

<ul>
    {% raw %}
    {% for item in paginate.data %}
        <li>{{ item.name }}</li>
        ...
    {% endfor %}
    {% endraw %}
</ul>

{% endhighlight %}

For displaying the menu to navigate through pages, use the method `render` in the paginate object. This method receives 5 optional string parameters which define in order: the *Previous* button link label, the *Next* button link label, the class for the *&lt;li&gt;* tag, the class for the *&lt;a&gt;* tag and finally the class for the current page (active) *&lt;li&gt;* tag. The default values are: *'&lt;'*, *'&gt;'*, *'page-item'*, *'page-link'* and *'active'*.

{% highlight twig %}
[public/views/my-page.twig]

...

{% raw %}
{% if paginate is defined and paginate.shouldRender %}
<nav>
    <ul>
        {{ paginate.render('Prev', 'Next') }}
    </ul>
</nav>
{% endraw %}
...

{% endhighlight %}

For the previous example the HTML output will be something like this:

{% highlight html %}

...

<nav>
    <ul>
        <li class="page-item"><a class="page-link" href="myurl/?p=1">Prev</a></li>
        <li class="page-item active"><a class="page-link" href="myurl/?p=1">1</a></li>
        <li class="page-item"><a class="page-link" href="myurl/?p=2">2</a></li>
        ...
        <li class="page-item"><a class="page-link" href="myurl/?p=2">Next</a></li>
    </ul>
</nav>

{% endhighlight %}

> Note that if your current URL has query parameters, they will be included safely into the pagination result links.

<a name="exception"></a>
## 15. Exceptions

If there is a problem with the configuration of your Controller classes, view template files or other exceptions, the FrameworkException will be thrown and you will see the complete list of all thrown exceptions and errors on the screen. In general it is not needed to throw exceptions but you can throw a FrameworkException in your Controller class as follows:

{% highlight php %}
[App/Controllers/MyController.php]

<?php 

namespace App\Controllers;
    
use Niuware\WebFramework\Application\Controller;
use Niuware\WebFramework\Http\HttpRequest;
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

<a name="compatibility"></a>
## 16. PHP < 7.0 compatibility

The core of Niuware WebFramework is compatible with PHP 5.6+. On the other hand, the default versions for the dependencies Eloquent and Twig are set to use a minimum version of PHP 7.0. If you require to use a version lower than PHP 7.0 you can update the composer file for using aliases on illuminate/database < 5.5.0 and twig/twig < 2.0.0

{% highlight text %}
{
    "require": {
        "niuware/webframework" : "dev-master",
        "illuminate/database": "<5.5.0 as 5.5.x-dev",
        "twig/twig" : "<2.0.0 as 2.x-dev"
    }
}
{% endhighlight %}