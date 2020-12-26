## Decorator

#### BASIC DESCRIPTION:
- extend an object’s behaviour without making a new subclass
- add or remove responsibilities from an object at runtime
- it possible to combine several behaviours by wrapping an object into multiple decorators
- use the pattern when it’s awkward or not possible to extend an object’s behaviour using inheritance
- use the Decorator pattern when you need to be able to assign extra behaviours to objects at runtime without breaking the code that uses these objects
- adapter changes the interface of an existing object, while Decorator enhances an object without changing its interface. 

#### PSEUDOCODE:
```php
<?php

interface LoggerInterface
{
    public function log(int $code, string $message): void;
}

interface SmsGatewayInterface
{
    public function send(string $message): void;
}

class Logger implements LoggerInterface
{
    public function log(int $code, string $message): void
    {
    }
}

class SmsGateway implements SmsGatewayInterface
{
    public function send(string $message): void
    {
    }
}

class LoggerDecorator implements LoggerInterface
{
    private LoggerInterface $logger;
    private SmsGatewayInterface $smsGateway;

    public function __construct(LoggerInterface $logger, SmsGatewayInterface $smsGateway)
    {
        $this->logger = $logger;
        $this->smsGateway = $smsGateway;
    }

    public function log(int $code, string $message): void
    {
        if (500 === $code) {
            $this->smsGateway->send($message);
        }

        $this->logger->log($code, $message);
    }
}

$logger = new LoggerDecorator(new Logger(), new SmsGateway());
$logger->log(500, 'Database error.');
```
