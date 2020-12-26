## Builder

#### BASIC DESCRIPTION:
- builder is an interface that builds a complex object or part of an object
- builders have often a fluent interface (function to configure created object return self builder object - pseudocode)
- can construct objects step-by-step
- the same construction code when building various representations of products

#### PSEUDOCODE:
```php
<?php

class System
{
    public function __construct(StorageInterface $storage, CacheInterface $cache)
    {
        //...
    }
}

class SystemBuilder
{
    private StorageInterface $storage;
    private CacheInterface $cache;

    public function setStorage(StorageInterface $storage): self
    {
        $this->storage = $storage;

        return $this;
    }

    public function setCache(CacheInterface $cache): self
    {
        $this->cache = $cache;

        return $this;
    }

    public function build(): System
    {
        return new System($this->storage, $this->cache);
    }
}

$system = (new SystemBuilder())
    ->setStorage($storage)
    ->setCache($cache)
    ->build();
```
