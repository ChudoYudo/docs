# Debug - Dumping Variables
Use `Spiral\Debug\Dumper` class or function `dump` to view content of your variables and instances without xDebug:

```php
protected function indexAction(Dumper $dumper, MemcacheStore $memcacheStore)
{
    $dumper->dump($memcacheStore);
}
```
```php
protected function indexAction(MemcacheStore $memcacheStore)
{
    dump($memcacheStore);
}
```

![Dump](https://raw.githubusercontent.com/spiral/guide/master/resources/dumps.png)

The Spiral `Dumper` supports the `__debugInfo` [method](http://php.net/manual/en/language.oop5.magic.php) which allows you to dump only relevant information. 

## Usage
In your code (works in web and CLI SAPIs):

```php
use Spiral\Debug;

$d = new Debug\Dumper();

$d->dump($variable);
```

Dump to Log:

```php
use Spiral\Debug;

$d = new Debug\Dumper($loggerInterface);

$d->dump($variable, Debug\Dumper::LOGGER);
```

Dump to STDERR:

```php
use Spiral\Debug;

$d = new Debug\Dumper($loggerInterface);

$d->dump($variable, Debug\Dumper::STDERR);
```

Force dump to STDERR with color support:

```php
use Spiral\Debug;

$d = new Debug\Dumper($loggerInterface);
$d->setRenderer(Debug\Dumper::STDERR, new Debug\Renderer\ConsoleRenderer());

$d->dump($variable, Debug\Dumper::STDERR);
```

> You can use function `dump` as a shortcut. Use `dumprr` to dump to the RoadRunner error log.

## Internal Fields
To hide specific fields of your objects without the `__debugInfo` method, add an "@internal" annotation to your property.

```php
class TestService
{
    /**
     * @internal
     * @var ContainerInterface
     */
    protected $container = null;
}
```

## In RoadRunner
You can dump variable into roadrunner debug log using function `dumprr`. Make sure to use this function in your job handlers.
