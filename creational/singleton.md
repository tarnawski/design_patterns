## Singleton

#### BASIC DESCRIPTION:
- to have only one instance of this object in the application that will handle all calls.
- usually used to create a database connector or logger
- this considered to by anti-pattern (can be replaced by DI)

#### PSEUDOCODE:
```php
<?php

final class Connection
{
    private static ?Connection $instance = null;

    public static function getInstance(): Connection
    {
        if (static::$instance === null) {
            static::$instance = new static();
        }

        return static::$instance;
    }
}
```
