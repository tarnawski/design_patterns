## Chain of Responsibility

#### BASIC DESCRIPTION:
- to build a chain of objects to handle a call in sequential order
- if one object cannot handle a call, it delegates the call to the next in the chain and so forth
- it is possible to control the order of handling
- it is possible to introduce new handlers into the app without breaking the existing client code
- it is possible that in some cases requests may end up unhandled

#### PSEUDOCODE:
```php
<?php

class Record
{
    private int $code;
    private string $message;

    public function __construct(int $code, string $message)
    {
        $this->code = $code;
        $this->message = $message;
    }

    public function getCode(): int
    {
        return $this->code;
    }

    public function getMessage(): string
    {
        return $this->message;
    }
}

abstract class LoggerHandler
{
    private ?LoggerHandler $successor;

    public function __construct(?LoggerHandler $successor = null)
    {
        $this->successor = $successor;
    }

    final public function handle(Record $record): void
    {
        $this->log($record);

        if (null !== $this->successor) {
            $this->successor->handle($record);
        }
    }

    abstract protected function log(Record $record): void;
}

class InMemoryLogger extends LoggerHandler
{
    protected function log(Record $record): void
    {
    }
}

class FileLogger extends LoggerHandler
{
    protected function log(Record $record): void
    {
        if (500 === $record->getCode()) {
            // ...
        }
    }
}

$logger = new InMemoryLogger(new FileLogger());
$logger->handle(new Record(500, 'Database Error.'));
```
