# PHPUnit and faker feature test escapes

If generating data with faker, while looking for person names, sometimes the tests may break because they contain a name that has an apostrophe in it `'`. 

Since the laravel's `{{ $user->name}}` escapes the name, but the tests do not, we need to escape them in the tests too.

That can be done by using 

```php
$response->assertSee( htmlspecialchars( $user->getFullName(), ENT_QUOTES, 'UTF-8', false);
```