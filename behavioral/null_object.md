## Null Object

#### BASIC DESCRIPTION:
- methods that return an object or null should instead return an object or NullObject
- client code is simplified
- reduces the chance of null pointer exceptions
- fewer conditionals require less test cases

#### PSEUDOCODE:
```php
<?php

interface LoggerInterface
{
    public function log(string $str): void;
}

class NullLogger implements LoggerInterface
{
    public function log(string $str): void
    {
        // do nothing
    }
}
```
