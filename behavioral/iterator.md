## Iterator

#### BASIC DESCRIPTION:
- to make an object iterable and to make it appear like a collection of objects
- possible to iterate over the same collection in parallel because each iterator object contains its own iteration state

#### PSEUDOCODE:
```php
<?php

class Item
{
}

class ItemList implements Countable, Iterator
{
    /** @var Item[] */
    private array $items = [];
    private int $currentIndex = 0;

    public function current(): Item
    {
        return $this->items[$this->currentIndex];
    }

    public function next(): void
    {
        $this->currentIndex++;
    }

    public function key(): int
    {
        return $this->currentIndex;
    }

    public function valid(): bool
    {
        return isset($this->items[$this->currentIndex]);
    }

    public function rewind(): void
    {
        $this->currentIndex = 0;
    }

    public function count(): int
    {
        return count($this->items);
    }
}
```
