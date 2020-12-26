## Strategy

#### BASIC DESCRIPTION:
- define a family of algorithms, put each of them into a separate class, and make their objects interchangeable
- allow swapping algorithms used inside an object at runtime
- allow introducing new strategies without having to change the context
- isolate the implementation details of an algorithm from the code that uses it
- use the Strategy pattern when you want to use different variants of an algorithm within an object and be able to switch from one algorithm to another during runtime

#### PSEUDOCODE:
```php
<?php

class StrategyContext
{
    private ProcessStrategyInterface $strategy;

    public function __construct(string $strategy)
    {
        switch ($strategy) {
            case 'simple':
                $this->strategy = new SimpleProcessStrategy();
                break;
            case 'complex':
                $this->strategy = new ComplexProcessStrategy();
                break;
            default:
                $this->strategy = new ComplexProcessStrategy();
        }
    }

    public function process(): void
    {
        $this->strategy->process();
    }
}

interface ProcessStrategyInterface
{
    public function process(): void;
}

class SimpleProcessStrategy implements ProcessStrategyInterface
{
    public function process(): void
    {

    }
}

class ComplexProcessStrategy implements ProcessStrategyInterface
{
    public function process(): void
    {

    }
}
```
