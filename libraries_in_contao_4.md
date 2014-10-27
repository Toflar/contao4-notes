
# Contao 4 - The way you should do it

Up to Contao 3 we had many PHP classes that have served us well over the years. However, most of them are with us for many years and thus do not follow lots of coding styles or principles that have been accepted by a broad part of the PHP community over the last few years.

To be a bit more precise:

- Most of them do not support Dependency Injection
- Most of them are tightly coupled to other Contao classes whether it's via inheritance or reference to other classes
- None of them are unit tested
- etc.

We have to move on - that's why there is Contao 4. Given the fact that we use [Composer](https://getcomposer.org) as our new dependency manager to load third party libraries, it will be very easy for any developer to use third party code within their extensions to Contao 4.

## The Contao library

As of Contao 4, a lot of our libraries _can_ still be used (making transition easier) but you _should_ be using alternatives the PHP community offers you.
__Note:__ This does not mean there are alternatives for any library in Contao! You will need to figure out where you have to use Contao libraries and where you should switch to an alternative. E.g. very specific Contao functionality such as template rendering (class `Template`), DCA loading (class `DcaLoader` and `DcaExtractor`) or `Controller` methods will obviously not have any alternative within the PHP community.

Here are a few examples of how we used to do things in Contao 3.x (that still work) but can be improved by using more advanced libraries supporting lots of the modern coding principles.

### The `Request` class

Contao 3:

```php
$objRequest = new Request();
$objRequest->send('http://domain.tld');

if ($objRequest->hasError())
{
    // Error
}

$strResponse = $objRequest->response;
```

Contao 4 / PHP Standalone:

The two most used libraries within the PHP community for HTTP requests are probably [Guzzle](https://github.com/guzzle/guzzle3) and [Buzz](https://github.com/kriswallsmith/Buzz). There may be other alternatives that you might consider using.
Here's the same example for Guzzle:

```php
use Guzzle\Http\Client;
use Guzzle\Http\Exception\BadResponseException;

$client   = new Client('http://domain.tld');
$request  = $client->get('/');

try {
    $response = $request->send();
    $response = $response->getBody();
} catch (BadResponseException $e) {
    // Error
}
```


### The `ZipWriter` and `ZipReader` classes

Try checking out libraries that can handle even more formats than only `.zip` such as [Zippy](https://github.com/alchemy-fr/Zippy) and friends.
