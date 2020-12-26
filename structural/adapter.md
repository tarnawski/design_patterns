## Adapter / Wrapper

#### BASIC DESCRIPTION:
- used to translate/adapt one interface for a class into a compatible interface
- usually used to adapt code to incompatibilities external classes  
- in DDD can be used in the infrastructure layer to adapt the external package to domain interfaces
- for normalize data
- the Adapter makes things work after they're designed - Bridge makes them work before they are
- adapter changes the interface of an existing object

#### PSEUDOCODE:
```php
<?php

interface Publisher
{
    public function publish(Post $post): void;
}

class Post
{
    public function getContent(): string
    {
        return 'Post content';
    }
}

class Facebook
{
    public function postOnWall(string $content): void
    {
    }
}

class FacebookAdapter implements Publisher
{
    private Facebook $facebook;

    public function __construct(Facebook $facebook)
    {
        $this->facebook = $facebook;
    }

     public function publish(Post $post): void
    {
        $this->facebook->postOnWall($post->getContent());
    }
}


$publisher = new FacebookAdapter(new Facebook());
$publisher->publish(new Post());
```
