## Factory Method

#### BASIC DESCRIPTION:
- in FactoryMethod pattern class depends on abstractions, not concrete classes - this differs this pattern in compared to SimpleFactory or StaticFactory
- for simple cases, this abstract class could be just an interface.
- the subclass can be used to implement different ways to create objects
- it achieves the Dependency Inversion principle in SOLID principle
- no coupling between the creator and the concrete products.

#### PSEUDOCODE:
```php
<?php

// This can be abstract class or interface in easy case
interface LoggerFactoryInterface
{
    public function createLogger(): Logger;
}

class StdoutLoggerFactory implements LoggerFactoryInterface
{
    public function createLogger(): Logger
    {
        return new StdoutLogger();
    }
}

class FileLoggerFactory implements LoggerFactoryInterface
{
    private string $filePath;

    public function __construct(string $filePath)
    {
        $this->filePath = $filePath;
    }

    public function createLogger(): Logger
    {
        return new FileLogger($this->filePath);
    }
}
```
