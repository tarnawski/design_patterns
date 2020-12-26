## Proxy

#### BASIC DESCRIPTION:
- provide a substitute or placeholder for another object
- proxy controls access to the original object by performing something before or after the request gets through to the original object
- can be used for cache or log information without integration with existing code 
- can control the service object without clients knowing about it
- can be introduced without changing the service or clients.
- lazy initialization (virtual proxy) - instead of creating the object when the app launches, you can delay the object’s initialization to a time when it’s really needed.

#### PSEUDOCODE:
```php
<?php

interface ClientInterface
{
    public function request(Request $request): Response;
}

class Service
{
    private ClientInterface $client;
      
    public function __construct(ClientInterface $client)
    {
         $this->client = $client;
    }

    public function fetch(): Response
    {
        return $this->client->request(new Request());
    }
}
class ClientLoggerProxy implements ClientInterface
{
    private ClientInterface $client;
    private LoggerInterface $logger;
      
    public function __construct(ClientInterface $client, LoggerInterface $logger)
    {
         $this->client = $client;
         $this->logger = $logger;
    }

    public function request(): Response
    {
         $response = $this->client->request(new Request());
         $this->logger->log($response);

         return $response;  
    }
}

# WITHOUT PROXY
$service = new Service(new Client());

# WITH PROXY
$service = new Service(new ClientLoggerProxy(new Client(), new Logger()));
```
