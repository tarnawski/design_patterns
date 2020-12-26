## Data Mapper

#### BASIC DESCRIPTION:
- bidirectional transfer of data between a persistent data store and an in-memory data representation
- the goal of the pattern is to keep the in-memory representation and the persistent data store independent of each other and the data mapper itself

#### PSEUDOCODE:
```php
<?php

class User
{
    private string $username;
    private string $email;

    public function __construct(string $username, string $email)
    {
        $this->username = $username;
        $this->email = $email;
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

class UserRepository
{
    private UserMapper $mapper;

    public function __construct(UserMapper $mapper)
    {
        $this->mapper = $mapper;
    }

    public function getById(int $id): User
    {
        // Data after fetch from data storage
        $data = ['user_name' => 'Johannes', 'email' => 'johannes@example.com'];

        return $this->mapper->mapRowToUser($data);
    }
    
    public function save(User $user): void
    {
        $data = $this->mapper->mapUserToRow($user);
        
        // Data to save in data storage
    }
}

class UserMapper
{
    public function mapRowToUser(array $row): User
    {
        return new User($row['user_name'], $row['email']);
    }

    public function mapUserToRow(User $user): array
    {
        return ['user_name' => $user->getUsername(), 'email' => $user->getEmail()];
    }
}

```
