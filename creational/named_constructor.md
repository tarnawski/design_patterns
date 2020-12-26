## Named constructor

#### BASIC DESCRIPTION:
- is allowed to have multiple object constructors 
- helps to create the object from a different type of parameters 

#### PSEUDOCODE:
```php
<?php

class User
{
    private string $username;
    private string $email;

    private function __construct(string $username, string $email)
    {
        $this->username = $username;
        $this->email = $email;
    }
    
    public static function fromValues(string $username, string $email): self
    {
        return new self($username, $email);
    }

    public static function fromArray(array $user): self
    {
        return new self($user['username'], $user['email']);
    }
    
    public function getUsername(): string
    {
        return $this->username;
    }

    public function getEmail(): string
    {
        return $this->email;
    }
}
```
