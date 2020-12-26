## Prototype

#### BASIC DESCRIPTION:
- clone object instead of creating
- can produce complex objects more conveniently.
- to avoid the cost of creating objects the standard way (new Class())
- cloning complex objects that have references might be very tricky

#### PSEUDOCODE:
```php
<?php

class Item
{
    protected string $name = 'book';

    public function __clone()
    {
    }
}

```
