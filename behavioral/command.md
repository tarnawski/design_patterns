## Command

#### BASIC DESCRIPTION:
- a design pattern that turns a request into a stand-alone object that contains all information about the request
- this transformation allows to parameterize methods with different requests, delay or queue a request’s execution, and support undoable operations
- decouple classes that invoke operations from classes that perform these operations
- it is possible to introduce new commands into the app without breaking existing client code
- help implement undo/redo or keeping a history of changes
- a good approach is to assemble a set of simple commands into a complex one

#### PSEUDOCODE:
```php
<?php

abstract class Command
{
    protected Application $application;

    public abstract function execute(): void;
}

abstract class  UndoableCommand extends Command
{
    public abstract function undo(): void;
}

class Application
{
    private string $status;

    public function setStatus(string $status): void
    {
        $this->status = $status;
    }
}

class ActivateCommand extends UndoableCommand
{
    public function execute(): void
    {
        $this->application->setStatus('active');
    }

    public function undo(): void
    {
        $this->application->setStatus('inactive');
    }
}
```
