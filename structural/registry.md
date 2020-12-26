## Registry

#### BASIC DESCRIPTION:
-  storage for often-used objects

#### PSEUDOCODE:
```php
<?php

interface LoggerInterface
{
    public function log(string $message): void;
}

class NullLogger implements LoggerInterface
{
    public const LOGGER_NAME = 'null_logger'; 
    
    public function log(string $message): void
    {
        // do nothing
    }
}

class InMemoryLogger implements LoggerInterface
{
    public const LOGGER_NAME = 'in_memory_logger';
    
    private array $logs;
    
    public function log(string $message): void
    {
        $this->logs[] = $message;
    }
}

class LoggerRegistry
{
    /** @var LoggerInterface[] */
    private array $services = [];

    public function set(string $key, LoggerInterface $value)
    {
        $this->services[$key] = $value;
    }

    public function get(string $key): LoggerInterface
    {
        return $this->services[$key];
    }
}

$registry = new LoggerRegistry();
$registry->set(NullLogger::LOGGER_NAME, new NullLogger());
$registry->set(InMemoryLogger::LOGGER_NAME, new InMemoryLogger());

$nullLogger = $registry->get(NullLogger::LOGGER_NAME);
$nullLogger->log('Database error.');
```
