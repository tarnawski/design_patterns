## Composite

#### BASIC DESCRIPTION:
- to treat a group of objects the same way as a single instance of the object
- the Composite pattern makes sense only when the core model of your app can be represented as a tree.
- use the pattern when you want the client code to treat both simple and complex elements uniformly

#### PSEUDOCODE:
```php
<?php

interface Capacity
{
    public function getCapacity(): float;
}

class Department implements Capacity
{
    private array $employees;
    
    public function getCapacity(): float
    {
        $capacity = 0.0;
        foreach ($this->employees as $employee) {
            $capacity += $employee->getCapacity();
        }
        
        return $capacity;
    }
}

class Employee implements Capacity
{
    private float $capacity;

    public function getCapacity(): float
    {
        return $this->capacity;
    }
}

```
