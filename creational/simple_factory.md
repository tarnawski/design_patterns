## Simple Factory

#### BASIC DESCRIPTION:
- special class to create a specific object
- we can have multiple factories with a different object configuration
- the same as Static Factory (but this is not the static method - this is only one difference)
- it always should be preferred over a static factory (mostly because of testing)

#### PSEUDOCODE:
```php
<?php

class LoggerFactory
{
    public function createLogger(): Logger
    {
        return new Logger();
    }
}
```
