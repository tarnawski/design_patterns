## Facade

#### BASIC DESCRIPTION:
- the primary function of a Facade is to simplify the interaction between a consumer and an interface
- isolate code from the complexity of a subsystem.
- the difference between a Facade and an Adapter is that the Facade makes a simple abstraction, where as an Adapter will handle complex interactions by taking incoming data and constructing it to work with the underlying objects.

#### PSEUDOCODE:
```php
<?php

class SystemFacade
{
    private System $system;

    public function __construct(System $system)
    {
        $this->system = $system;
    }

    public function process(): void
    {
        $this->system->prepare();
        $this->system->execute();
        $this->system->save();
    } 
}

class System
{
    public function prepare(): void
    {
    }

    public function execute(): void
    {
    }

    public function save(): void
    {
    }
}

$system = new SystemFacade(new System());
$system->process();
```
