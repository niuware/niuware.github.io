---
layout: page
title: Quick documentation
---

This is a quick documentation on how to use all of the available features in Niuware WebFramework.

1. <a href="#install">Installation</a>  
  1.1 <a href="#install-config">Configuration File</a>  
  1.2 <a href="#install-constant">Global Constants</a>  
  1.3 <a href="#install-settings">Settings Class</a>
2. <a href="#routing">Routing</a>    
  2.1 <a href="#routing-main">Main application</a>    
  2.2 <a href="#routing-admin">Admin application</a>  
3. <a href="#controllers">Controllers</a>    
  3.1 <a href="#controllers-define">Definition</a>    
  3.2 <a href="#controllers-access">Calls</a>    
  3.3 <a href="#controllers-protocol">Protocol Restriction</a>    
  3.4 <a href="#controllers-protocol-get">GET Protocol Methods</a>  
  3.5 <a href="#controllers-protocol-post">POST Protocol Methods</a>          
  3.6 <a href="#controllers-recycle">Recycling</a>    
4. <a href="#models">Models</a>  
  4.1 <a href="#models-define">Definition</a>  
  4.2 <a href="#models-eloquent">Eloquent</a>  
5. <a href="#views">Views</a>  
  5.1 <a href="#views-define">Definition</a>  
  5.2 <a href="#views-render">Rendering</a>  
  5.3 <a href="#views-special">Special Views</a>  
  5.4 <a href="#views-attributes">Template attributes</a>  
  5.5 <a href="#views-binding">View/Controller Binding</a>  
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
9. <a href="#security">Security</a>  
  9.1 <a href="#security-pass">Passwords</a>  
  9.2 <a href="#security-token">Tokens</a>

<a name="install"></a>
## 1. Installation

For using the Niuware WebFramework follow this steps:

1. Download the repository from [GitHub](https://github.com/niuware/web-framework.git).
2. Run `composer install` to install the Eloquent ORM (Illuminate/database) component.

<a name="install-config"></a>
### Installation: Configuration File

The framework uses a single configuration file to store private information such as database connection strings, third party API tokens, etc. It also contains the default values for the Web application.

This file should be **out of the public scope**, for example `/etc/nwf/settings.php`. After saving the file in your selected path, then add it to the `index.php` file:

{% highlight php %}
[index.php]

<?php 

namespace Niuware\WebFramework;

// Path to your settings file
require 'path/to/your/file/settings.dev.php';

...

// Create the web application
$app = Application::getInstance();

{% endhighlight %}

<a name="install-constant"></a>
### Installation: Global Constants

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
                If your BASE_URL has a sub path, write it here.<br /> 
                For example: If BASE_URL is http://my_url.com/ then BASE_PATH should be '/'.<br />
                If BASE_URL is http://my_url.com/<strong>sub_domain/</strong> then BASE_PATH should be <strong>sub_domain/</strong> (don't forget to write the trailing slash)
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
                <strong>Should include the trailing slash.</strong>
            </td>
        </tr>
        <tr>
            <td>SESSION_ID</td>
            <td>
                A unique Id for the session (Optional)<br />
                For example: <em>Empty string</em> <br/> 
            </td>
        </tr>
        <tr>
            <td>HOMEPAGE</td>
            <td>
                The default path for the Web Main application.<br />
                For example: <em>home</em> <br/> 
            </td>
        </tr>
        <tr>
            <td>HOMEPAGE_ADMIN</td>
            <td>
                The default path for the Web Admin application.<br />
                For example: <em>home</em> <br/> 
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
### Installation: Settings Class

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

Web applications created with Niuware WebFramework have two sides: the *main application* or User frontend side and the *admin application* or User admin side. For example suppose you create an online shop; you'll need the frontend side where all the products will be browsable by any user, and an admin panel side where some special users will be able to add or edit products for the shop.

You can also leave the routes empty and the framework will return an `HTTP 403 response`. This is useful when you want to use the framework with **API mode-only**.

<a name="routing-main"></a>
### Routing: Main application

The main application path views can be public (by default) or require a user login. For adding routes for the main application side you only need to edit the `core/routes.php` file.

For example, let's suppose you want people to access this sections in your web application:

> http://my_url/**home**<br />
> http://my_url/**my-cart**<br />
> http://my_url/**categories**

Then your `routes.php` file should look like this:

{% highlight php %}
[routes.php]

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
### Routing: Admin application

All the admin application path views require a user login by default. The framework will add the prefix `admin/` to all routes set for the Admin application. As with the previous Main application routing section, you only need to edit the `core/routes.php` file.

For example, let's suppose you want people to access this sections in your web application:

> http://my_url/admin/**home**<br />
> http://my_url/admin/**products**<br />
> http://my_url/admin/**accounts**

Then your `routes.php` file should look like this:

{% highlight php %}
[routes.php]

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

<a name="controllers"></a>
## 3. Controllers

Controller classes describe the functionality of your web application. Each controller can be called by any route or be created and executed in runtime.

<a name="controllers-define"></a>
### Controllers: Definition

All controllers inherit from the Niuware WebFramework core class `Controller` and must be placed in the `controllers` directory. The name of the file and the class name **must match** as well. A controller class file must be defined with the extension `.controller.php` and exist inside the namespace `Niuware\WebFramework\Controllers`. Here is an example of how it should look like:

{% highlight php %}
[MyController.controller.php]

<?php 

namespace Niuware\WebFramework\Controllers;
    
use Niuware\WebFramework\Controller;

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
[routes.php]

<?php
...

'my-cart' => [Cart]

...
{% endhighlight %}

and then the controller like this:

{% highlight php %}
[Cart.controller.php]

<?php 

namespace Niuware\WebFramework\Controllers;
    
use Niuware\WebFramework\Controller;

final class Cart extends Controller {

}

{% endhighlight %}

Notice that **`Cart`** was defined in the `routes.php` file as the controller who will listen to the path **`my-cart`**. Also notice that the controller class has the name **`Cart.controller.php`**. 

Now the `Cart` controller class will be called when a user access this path, but nothing will happen. We are still missing to define the method that will be executed. This is as simple as adding a public method with the same name as the path, in this case:

{% highlight php %}
[Cart.controller.php]

<?php 

namespace Niuware\WebFramework\Controllers;
    
use Niuware\WebFramework\Controller;

final class Cart extends Controller {

    public function myCart($params = []) {

    }
}

{% endhighlight %}

Notice the method name can use camelBack or CamelCase naming convention without problems. If your path uses hyphen [ - ] or underscore [ _ ], you **should remove** this characters from the method name (even in PHP you can use underscore to define methods, the framework will ignore them).

For example for the path: `my-cart` or `my_cart` a method named `myCart()` or `MyCart()` can be executed.

<a name="controllers-protocol"></a>
### Controllers: Protocol Restriction

It is easy to restrict the HTTP protocol that a Controller class can accept. For the previous example our method myCart would allow GET and POST protocol to execute the call; but if we want to restrict this, is as easy as adding the *get* or *post* prefix to our method. For example:

{% highlight php %}
[Cart.controller.php]

<?php 

namespace Niuware\WebFramework\Controllers;
    
use Niuware\WebFramework\Controller;

final class Cart extends Controller {

    // Executed when the server receives a GET request
    public function getMyCart($params = []) {

    }

    // Executed when the server receives a POST request
    public function postMyCart($params = []) {

    }

    // Executed for any request (GET or POST)
    public function myCart($params = []) {

    }
}

{% endhighlight %}

Notice that if you **cannot** use an any-protocol method combined with a GET/POST protocol method at the same time as it wouldn't be executed.

<a name="controllers-protocol-get"></a>
### Controllers: GET Protocol Methods

The request parameters for a GET protocol method can be placed as part of the url, split by slashes as the following example: 

> http://my_url/my-cart/**param_0_value**/**param_1_value**/ ...

The GET protocol method will recieve the values in the `$params` array as:

{% highlight php %}
<?php 

...

    public function getMyCart($params = []) {

        $params[0] = param_0_value;
        $params[1] = param_1_value;
    }
...
{% endhighlight %}

You can also receive GET request parameters as a query string, for example:

> http://my_url/my-cart**/?param0=value0&param1=value1**

> Notice you need to add the **last slash** before the parameter list as is the name of the method to execute

and your GET protocol method will recieve the parameters values in an associative array as follows:

{% highlight php %}
<?php 

...

    public function getMyCart($params = []) {

        $params['param0'] = value0;
        $params['param1'] = value1;
    }
...
{% endhighlight %}

If by some reason you want to combine both ways of receiving request parameters as this:

> http://my_url/my-cart**/param0_value/param1_value/?param2=value2&param3=value3**

then your GET protocol method will recieve the parameters as

{% highlight php %}
<?php 

...

    public function getMyCart($params = []) {

        // From the URL
        $params[0] = param0;
        $params[1] = param1;
        $params[2] = ?param2=value2&param3=value3;

        // From the query string
        $params['param2'] = value2;
        $params['param3'] = value3;
    }
...
{% endhighlight %}

<a name="controllers-protocol-post"></a>
### Controllers: POST Protocol Methods

The request parameters for a POST protocol method can be placed as part of the url, split by slashes as the following example: 

> http://my_url/my-cart/**param_0_value**/**param_1_value**/ ...

The POST protocol method will recieve the values in the `$params` array as:

{% highlight php %}
<?php 

...

    public function postMyCart($params = []) {

        $params[0] = param_0_value;
        $params[1] = param_1_value;
    }
...
{% endhighlight %}

You can also receive POST request parameters as a usual POST request, for example data in an HTML form. The POST protocol will receive the parameters as an associative array:

{% highlight php %}
<?php 

...

    public function postMyCart($params = []) {

        // From the query string
        $params['form_elem_name_0'] = value0;
        $params['form_elem_name_1'] = value1;
    }
...
{% endhighlight %}

<a name="controllers-recycle"></a>
### Controllers: Recycling

Sometimes the functionality of one method in a Controller class can be reused after completing some other processing in the current called method. This option is very useful in the following scenarios: 
1. When you want to use the same view template for different data sources 
2. When you want to use the same view template for different paths
3. When you want to redirect one path to another controller without reloading the browser

For this is as easy as instance an object of the Controller class you want.

{% highlight php %}
[Cart.controller.php]

<?php 

namespace Niuware\WebFramework\Controllers;
    
use Niuware\WebFramework\Controller;

final class Cart extends Controller {

    public function getMyCart($params = []) {

        // Do something here

        $otherController = new OtherController();

        // Additionally set controller options like
        // CSS stylesheets, JS files, etc. For example:
        $otherController->title = "My Other Title";
        $otherController->view = "other.view.php";

        return $otherController->getOtherMethod($params);
    }
}

{% endhighlight %}

<a name="models"></a>
## 4. Models

Models are the way to connect a datasource with a Controller (and a View). Niuware WebFramework integrates Illuminate's Database module for this part of the framework.

<a name="models-define"></a>
### Models: Definition

All models inherit from the Illuminate\Database\Eloquent class `Model` and must be placed in the `models` directory. The model class file must be defined with the extension `.model.php` and exist inside the namespace `Niuware\WebFramework\Models`. Here is an example of how it should look like:

{% highlight php %}
[Product.model.php]

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

All views must be placed in the `views` directory and their file must be defined with the extension `.view.php`. For the case of admin side views, the files should have the prefix `admin-`. The content of the views is a mixture of HTML and pure PHP code, no need to learn any templating layer.

By default, the framework will load a view filename that matches the current loaded path. For example for the next URL:

> http://my_url/my-cart

the framework will try to load the following view file:

`views/my-cart.view.php`

You can change the name of the view filename to load by setting the attribute `view` as shown in section Views: <a href="#views-attributes">Template Attributes</a>.

For the Admin application, all views filenames should end with `.admin.view.php`.

<a name="views-render"></a>
### Views: Rendering

To render a view template file, you need to tell the controller to do it. This is done by calling the `render` method from the `HtmlResponse` class. For example for the following URL:

> http://my_url/my-cart

we can simply call the `render` method as this:

{% highlight php %}
[Cart.controller.php]

<?php 

namespace Niuware\WebFramework\Controllers;
    
use Niuware\WebFramework\Controller;
use Niuware\WebFramework\HtmlResponse;

final class Cart extends Controller {

    public function getMyCart($params = []) {

        // By default it will render the views/my-cart.view.php file
        HtmlResponse::getInstance()->render($this);
    }
}

{% endhighlight %}

If you want to specify the filename of the view to load, simply set the template attribute as <a href="#views-attributes-view">described here</a>.

<a name="views-special"></a>
### Views: Special Views

There are 6 special view files that must exist when running the framework. You can add HTML or PHP content to this views as you need. 

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
            <td>main-header<br /> admin-header</td>
            <td>main-header.view.php<br /> admin-header.view.php</td>
            <td>
                Contains HTML header code used by all views. Defines CSS stylesheets, JS files and other HTML headers meta tags. The main and admin side have their own header file.<br/>
                <strong>This view files contain Controller core class code to load stylesheets, JS files and other web page attributes that should not be modified unless is required.</strong>
            </td>
        </tr>
        <tr>
            <td>main-footer<br /> admin-footer</td>
            <td>main-footer.view.php<br /> admin-footer.view.php</td>
            <td>Contains HTML footer code used by all views. The main and admin side have their own header file.</td>
        </tr>
        <tr>
            <td>Default</td>
            <td>default.view.php</td>
            <td>Displayed automatically when the path exists, but the view file does not exist.</td>
        </tr>
        <tr>
            <td>404</td>
            <td>404.view.php</td>
            <td>Displayed automatically when the path exists, but there is no method defined for the path.</td>
        </tr>
    </tbody>
</table>

Normally is not necessary to use variables other than the ones already set in the header or footer views, but if you require so, instead of accessing `Controller` variables using the syntax `$this->myVariable`, it is necessary to access them through the controller object as `$this->controller->myVariable`.

<a name="views-attributes"></a>
### Views: Template Attributes

All Controller classes can set template attributes before rendering the view file. Here is the list of available attributes:

<table class="variant">
    <tbody>
        <tr>
            <td><strong>title</strong></td>
            <td>String (optional)</td>
            <td>
                The title of the current web page.<br />
                <em>Default: Title set on the configuration file.</em>
            </td>
        </tr>
    </tbody>
</table>

Usage: 

{% highlight php %}
[MyController.controller.php]

<?php

final class MyController extends Controller {

    public function getMyPage($params = []) {

        $this->title = "My New Title";

        ...

{% endhighlight %}

Output:

{% highlight html %}
[main-header.view.php]

...

<title>My New Title</title>

{% endhighlight %}

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

    public function getMyPage($params = []) {

        $this->view = "view_filename.view.php";

        ...

        HtmlResponse::getInstance()->render($this);
    }

{% endhighlight %}

Output:

{% highlight html %}

Loaded file: views/view_filename.view.php

{% endhighlight %}

<table class="variant">
    <tbody>
        <tr>
            <td><strong>styles</strong></td>
            <td>Associative array (optional)</td>
            <td>
                The CSS filenames to load. This filenames should be found in the styles/path_to_files directory.<br />
                <em>Default: Loads the following stylesheet: styles/default/main.css.</em>
            </td>
        </tr>
    </tbody>
</table>

Usage: 

{% highlight php %}
[MyController.controller.php]

<?php

final class MyController extends Controller {

    public function getMyPage($params = []) {

        // Do not write the .css extension
        $this->styles = [
            'path_to_files' => [
                'stylesheet_file_1',
                'stylesheet_file_2'
                ...
                ],
            ...
        ];

        ...

{% endhighlight %}

Output:

{% highlight html %}

...

<link rel="stylesheet" href="styles/path_to_files/stylesheet_file_1.css" />
<link rel="stylesheet" href="styles/path_to_files/stylesheet_file_2.css" />

{% endhighlight %}

<table class="variant">
    <tbody>
        <tr>
            <td><strong>js</strong></td>
            <td>Array (optional)</td>
            <td>
                The local javascript files to load. This filenames should be found in the js/ directory.<br />
                <em>Default: Does not load any local javascript files.</em>
            </td>
        </tr>
    </tbody>
</table>

Usage: 

{% highlight php %}
[MyController.controller.php]

<?php

final class MyController extends Controller {

    public function getMyPage($params = []) {

        // Do not write the .js extension
        $this->js = [
            'local_js_file_1',
            'local_js_file_2'
            ...
        ];

        ...

{% endhighlight %}

Output:

{% highlight html %}

...

<script src="js/local_js_file_1.js"></script>
<script src="js/local_js_file_2.js"></script>

{% endhighlight %}

<table class="variant">
    <tbody>
        <tr>
            <td><strong>cdn</strong></td>
            <td>Associative array (optional)</td>
            <td>
                The remote javascript files to load from a CDN.<br />
                <em>Default: Does not load any remote javascript files.</em>
            </td>
        </tr>
    </tbody>
</table>

Usage: 

{% highlight php %}
[MyController.controller.php]

<?php

final class MyController extends Controller {

    public function getMyPage($params = []) {

        $this->cdn = [
            'absolute_url_to_cdn_file' => [
                'attribute_1' => 'value_1',
                ...
            ],
            ...
        ];

        ...

{% endhighlight %}

Output:

{% highlight html %}

...

<script src="absolute_url_to_cdn_file" attribute_1="value_1"></script>

{% endhighlight %}

<table class="variant">
    <tbody>
        <tr>
            <td><strong>metaTags</strong></td>
            <td>Associative array (optional)</td>
            <td>
                The HTML header meta tags.<br />
                <em>Default: Does not add any meta tags.</em>
            </td>
        </tr>
    </tbody>
</table>

Usage: 

{% highlight php %}
[MyController.controller.php]

<?php

final class MyController extends Controller {

    public function getMyPage($params = []) {

        $this->metaTags = [
            'meta_name_1' => 'meta_content_1',
            'meta_name_2' => 'meta_content_2',
            ...
        ];

        ...

{% endhighlight %}

Output:

{% highlight html %}

...

<meta name="meta_name_1" content="meta_content_1" />
<meta name="meta_name_2" content="meta_content_2" />

{% endhighlight %}

<table class="variant">
    <tbody>
        <tr>
            <td><strong>metaProps</strong></td>
            <td>Associative array (optional)</td>
            <td>
                The HTML header meta property tags.<br />
                <em>Default: Does not add any meta property tags.</em>
            </td>
        </tr>
    </tbody>
</table>

Usage: 

{% highlight php %}
[MyController.controller.php]

<?php

final class MyController extends Controller {

    public function getMyPage($params = []) {

        $this->metaProps = [
            'meta_property_name_1' => 'meta_property_content_1',
            'meta_property_name_2' => 'meta_property_content_2',
            ...
        ];

        ...

{% endhighlight %}

Output:

{% highlight html %}

...

<meta property="meta_property_name_1" content="meta_property_content_1" />
<meta property="meta_property_name_2" content="meta_property_content_2" />

{% endhighlight %}

<a name="views-binding"></a>
### Views: View/Controller Binding

You can bind variables from a controller to a view by assigning new properties to the `Controller` object. For example let's suppose you need to render some array:

{% highlight php %}
[MyController.controller.php]

<?php

final class MyController extends Controller {

    public function getMyPage($params = []) {

        // Assign the array as an attribute to the controller
        $this->myArray = [ ... ]

        ...

        HtmlResponse::getInstance()->render($this);
    }

{% endhighlight %}

Then in your view, you just need to use it as you would expect:

{% highlight php %}
[my-controller.view.php]

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

<a name="sessions"></a>
## 6. Sessions

Sessions are very useful for saving data for active users while they use your Web application. The `Auth` core class helps you manage sessions in a simple way.

<a name="sessions-auth"></a>
### Sessions: Authentication

The `Auth` class can help you verify if a user has successfully logged in to either the Main or Admin application. For this you can use the `grantAuth` or `revokeAuth` methods. Usually this methods will be called in the `Login.controller.php` or `Login.admin.controller.php`.

The Niuware WebFramework comes with a default configuration for auto logging a user who navigates to login-protected views as you can see in the following `Login` controller:

{% highlight php %}
[controllers/Login.controller.php]

<?php 

namespace Niuware\WebFramework\Controllers;
    
use Niuware\WebFramework\Controller;
use Niuware\WebFramework\Auth;

final class Login extends Controller {

    public function getLogin($params = []) {
        
        Auth::grantAuth();
    }
    
    public function getLogout($params = []) {
        
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

    public function getMyPage($params = []) {

        // For main application use:
        Auth::grantAuth();
        // or
        Auth::revokeAuth();

        // For admin application use:
        //Auth::revokeAuth('admin');
        //Auth::revokeAuth('admin');
    }

{% endhighlight %}

To verify if a user has logged in to your Web application use the following method:

{% highlight php %}

<?php 

namespace Niuware\WebFramework\Controllers;
    
use Niuware\WebFramework\Controller;
use Niuware\WebFramework\Auth;

final class MyController extends Controller {

    public function getMyPage($params = []) {

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

    public function getMyPage($params = []) {

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

    public function getMyPage($params = []) {

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
[MyController.controller.php]

<?php 

namespace Niuware\WebFramework\Controllers;
    
use Niuware\WebFramework\Controller;
use Niuware\WebFramework\Helper;

final class MyController extends Controller {

    public function getMyPage($params = []) {

        Helper::myCustomFunc();

        $localVar = Helper::myCustomVar;

        ...
    }

{% endhighlight %}

Or in a view template as follows:

{% highlight php %}
[my-controller.view.php]

...
<div>
    <?php echo \Niuware\WebFramework\Helper::myCustomFunc(); ?>
</div>

{% endhighlight %}

<a name="custom-define"></a>
### Customization: Definition of Custom Classes

For adding custom helper classes add them in the path `helpers/` with the extension `.helper.php` and exist inside the namespace `Niuware\WebFramework\Helpers`. Here is a simple example:

{% highlight php %}
[MyCustomClass.helper.php]

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
[MyController.controller.php]

<?php 

namespace Niuware\WebFramework\Controllers;
    
use Niuware\WebFramework\Controller;
use Niuware\WebFramework\Helpers;

final class MyController extends Controller {

    public function getMyPage($params = []) {

        $myCustom = new Helpers\MyCustomClass();

        $myCustom->someFunc();

        ...
    }

{% endhighlight %}

<a name="api"></a>
## 8. API Classes

The main purpose of the Niuware WebFramework is to be used to create a RESTful API to build asynchronous Web applications and API services.

<a name="api-define"></a>
### API Classes: Definition

API classes should be add in the `api/` directory with the extension `.api.php`. Also the classes should exist inside the namespace `Niuware\WebFramework\Api`. The filename **should be in lowercase** so your API URL's remain in lowercase. Here is an example of how it should look like:

{% highlight php %}
[MyApi.api.php]

<?php 

namespace Niuware\WebFramework\Api;

final class MyApi {

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
[Cart.api.php]

<?php 

namespace Niuware\WebFramework\Api;

final class Cart {

    public function addProduct($params = []) {

    }

    // The following declarations will work as well
    // public function addproduct($params = [])
    // public function AddProduct($params = [])

    // The following declaration won't be accessed
    // private function addProduct($params = [])
}

{% endhighlight %}

Notice that only `public` methods are accessible to an API call, so you define `private` methods as they will never be accessed even if the API URL path contains the name of a valid method.

<a name="api-protocol"></a>
### API Classes: Protocol Restriction

Same as the `Controller` classes, you can define <a href="#controllers-protocol">protocol restriction</a> using the prefix <em>get</em> or <em>post</em> for your method. If you omit this prefix, the method will accept API calls via GET and POST.

<a name="api-params"></a>
### API Classes: Request Parameters

To recieve parameters from an API call, use the URL query for a GET request, and use the `params` array for a POST request.

GET Request:

> http://my_url/api/cart/add_product/?**id=6**&**token=7458ABDG83**

{% highlight php %}
[Cart.api.php]

<?php 

namespace Niuware\WebFramework\Api;

final class Cart {

    public function getAddProduct($params = []) {

        $params['id'] = '6';
        $params['token'] = '7458ABDG83';
    }
}

{% endhighlight %}

POST Request:

{% highlight js %}

var requestData = {
    id : 6,
    token : '7458ABDG83'
};

...

$.ajax({
    type: "POST",
    url: "http://my_url/api/cart/add_product",
    dataType: 'json',
    data: { params : requestData },
    ...
})

{% endhighlight %}

{% highlight php %}
[Cart.api.php]

<?php 

namespace Niuware\WebFramework\Api;

final class Cart {

    public function postAddProduct($params = []) {

        $params['id'] = '6';
        $params['token'] = '7458ABDG83';
    }
}

{% endhighlight %}

<a name="security"></a>
## 9. Security

The core includes 3 simple methods to manage string hashing.

<a name="security-pass"></a>
### Passwords

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

### Tokens

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