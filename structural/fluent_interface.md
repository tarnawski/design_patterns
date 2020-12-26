## Fluent Interface

#### BASIC DESCRIPTION:
- to write code that is easily readable just like sentences in a natural language
- achieved by a fluent return (return self-object)

#### PSEUDOCODE:
```php
<?php

class Employee
{
    private string $firstName;
    private string $lastName;

    public function setFirstName(string $firstName): Employee
    {
        $this->firstName = $firstName;
        return $this;
    }

    public function setLastName(string $lastName): Employee
    {
        $this->lastName = $lastName;
        return $this;
    }
    
    public function __toString(): string
    {
        return sprintf('%s %s', $this->firstName, $this->lastName);
    }
}

$employee = (new Employee())
     ->setFirstName('Johanes')
     ->setLastName('Ford');
```
