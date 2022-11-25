# Event Sourcing 
    
## What is Event Sourcing

* The Event Sourcing pattern is an approach of handling the events which happened on state and storing them in an append-only store. With this approach we can store. 
* These events describe various operations which can then be processed to find the current state.
* Typically these events are stored separately from materialized views.

## Advantages

1. Tasks that handle events can do it in background and there’s no contention during the process of transactions, this can vastly boost the performance.
2. Events do not update data directly, they are simply recording for processing at appropriate time simplifying its implementation and management.
3. Event Sourcing can prevent concurrent updates avoiding conflicts.

## Disadvantages

1. The event store is permanent, it’s event shouldn’t be updated. The only way to update is to add a compensating event.
2. If the size of the event store stream is large it will take a lot of time to process it and to store it.

## When to use Event Sourcing

* When you want to capture intent, purpose, or reason in the data.
* When it's vital to minimize or completely avoid the occurrence of conflicting updates to data.
* When you want to record events that occur, to replay them to restore the state of a system, to roll back changes, or to keep a history and audit log. 

## When to not use Event Sourcing

* Small or simple domains, systems that have little or no business logic, or non-domain systems that naturally work well with traditional CRUD data management mechanisms.
* Systems where consistency and real-time updates to the views of the data are required.
* Systems where audit trails, history, and capabilities to roll back and replay actions aren't required.


## Example 

* As shown in the example below, the items added into the cart create an event. The events can be either adding the item to the cart or removing it. So whenever an item is added to cart we create an add event and append it to the event store. If the item has been removed, we create an remove event instead of deleting the old event. With this we have a clear trace of how we got to the current state. These events are permanently stored and can be used in future as data on the customers. Apart from basic info like item name and amount, these events can also store metadata like timestamp, date, etc. 
* These events can also be used to study, like suppose we need to find out how many people removed an item within 5 minutes of checking out. Likely assuming if they removed it within 5 minutes they are likely to buy that product. So we can process these events and see if the customers actually bought those products in future through this data.

 ![ Event Sourcing Architecture](https://learn.microsoft.com/en-us/azure/architecture/patterns/_images/event-sourcing-overview.png "TEvent Sourcing Architecture")


## References Section
* [https://www.youtube.com/watch?v=rUDN40rdly8](https://www.youtube.com/watch?v=rUDN40rdly8)
* [https://learn.microsoft.com/en-us/azure/architecture/patterns/event-sourcing](https://learn.microsoft.com/en-us/azure/architecture/patterns/event-sourcing)