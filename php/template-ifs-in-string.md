# Template IFs in string

Given a string like:

```
I like trains{if turtles} and turtles{/if}.
```

We can parse it with `preg_replace_callback` function:

```php
$text = preg_replace_callback('/\\{if\\s(.+?)}(.+?)\\{\\/if}/s', function($matches) use ($attributes) {

  list($condition, $variable, $content) = $matches;

  if (isset($attributes[$variable]) && $attributes[$variable]) {
    return $content;
  }
  
  return "";

}, $text, -1);
```
