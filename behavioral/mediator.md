## Mediator

#### BASIC DESCRIPTION:
- reduce chaotic dependencies between objects
- reduce coupling between various components of a program
- restricts direct communications between the objects and forces them to collaborate only via a mediator object
- components must collaborate indirectly, by calling a special mediator object
- in result, the components depend only on a single mediator class instead of being coupled to dozens of their colleagues
- "one good friend is better than many"
- use the Mediator pattern when it’s hard to change some of the classes because they are tightly coupled to a bunch of other classes
- use the Mediator when you find yourself creating tons of component subclasses just to reuse some basic behaviour in various contexts
- communication is extracted between various components into a single place, making it easier to comprehend and maintain
- the disadvantage is that the mediator can evolve into a God Object

#### PSEUDOCODE:
```php
<?php

interface StoreMediatorInterface
{
    public function checkAvailability(int $id): bool;
    public function sendNotification(string $message): void;
}


class StoreMediator implements StoreMediatorInterface
{
    private OrderService $orderService;
    private ProductService $productService;
    private NotificationService $notificationService;

    public function checkAvailability(int $id): bool
    {
        return $this->productService->checkAvailability($id);
    }

    public function sendNotification(string $message): void
    {
        $this->notificationService->send($message);
    }
}


class OrderService
{
    private StoreMediatorInterface $mediator;

    public function isProductAvailable(int $id): bool
    {
        return $this->mediator->checkAvailability($id);
    }

    public function sendNotification(string $message): void
    {
        $this->mediator->sendNotification($message);
    }
}

class ProductService
{
    private StoreMediatorInterface $mediator;
    
    public function checkAvailability(int $id): bool
    {
        //...
    }
    
    public function sendNotification(string $message): void
    {
        $this->mediator->sendNotification($message);
    }
}

class NotificationService
{
    private StoreMediatorInterface $mediator;
    
    public function send(string $message): void
    {
        //...
    }
}
```
