## Observer/Event-Subscriber/Listener

#### BASIC DESCRIPTION:
- define a subscription mechanism to notify multiple objects about any events that happen to the object they’re observing
- is possible to introduce new subscriber classes without having to change the publisher’s code
- help establish relations between objects at runtime

#### PSEUDOCODE:
```php
<?php

interface SubscriberInterface
{
    public function update(): void;
}

class EmailAlertsSubscriber implements SubscriberInterface
{
    public function update(): void
    {
        //...
    }
}

class LoggingSubscriber implements SubscriberInterface
{
    public function update(): void
    {
        //...
    }
}

class Publisher
{
    /** @var SubscriberInterface[] */
    private array $subscribers = [];

    public function addSubscribe(SubscriberInterface $subscriber): void
    {
        $this->subscribers[] = $subscriber;
    }

    public function notifySubscribes(): void
    {
        foreach ($this->subscribers as $subscriber) {
            $subscriber->update();
        }
    }
}

$publisher = new Publisher();
$publisher->addSubscribe(new EmailAlertsSubscriber());
$publisher->addSubscribe(new LoggingSubscriber());

$publisher->notifySubscribes();
```
