## Static Factory

#### BASIC DESCRIPTION:
- special class to create a specific object
- we can have multiple factories with a different object configuration
- the same as Simple Factory (the only one difference is  that the static factory pattern uses static method)

#### PSEUDOCODE:
```php
<?php

class LoggerFactory
{
    public static function createLogger(): Logger
    {
        return new Logger();
    }
}
```
