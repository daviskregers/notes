# Patch PHPStorm to to use OSX case sensitive file system

By default mac is not case sensitive, but you can configure it to be during installation. PHPStorm doesn't like that.

```
echo idea.case.sensitive.fs=true >> /Applications/PhpStorm.app/Contents/bin/idea.properties
```