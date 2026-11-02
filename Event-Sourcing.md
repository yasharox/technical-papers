# Event Sourcing Architecture

## Introduction

Event Sourcing is a design pattern where an application saves every change as an event. Instead of saving only the object's latest state, the system keeps a sequence of events that explains how the object reached that state. By reading these events from the start, the application can determine the current state or see what the data looked like in the past.

## How Event Sourcing Works

Below are the main steps in an event-driven workflow:

1. When a user sends a request, like placing an order.
2. The system checks if the request is valid.
3. If valid, the system creates an event, such as an order being placed.
4. The event is saved in a special database called an event store.
5. The application updates its current view using this new event

## Main Components

**Command Handler:** Receives commands, validates them, and performs actions.\
**Event:** Keeps a record of completed events.\
**Event Store:** A database that only adds new events and never changes old ones.\
**Projection:** A view of data created by processing events for fast reading.

## Example: Online Shopping Order

**First event:** Order placed.\
**Second event:** Payment received.\
**Third event:** Order shipped.

If someone check for the current status, the system looks at these events in order and gives the update. If an item is canceled, the system adds a cancellation event instead of erasing the past events.

## Advantages

1. Keeps a complete history of all changes.
2. Makes it easy to audit and track data.
3. Allows the system to replay events to fix bugs or build new views.

## Challenges

The event list can become very long and slow to read over time. And fixing errors requires adding new correction events instead of editing old ones. It adds extra complexity compared to normal databases.

## Conclusion

Event Sourcing is a useful way to track data history by saving events in order. While it adds some complexity, it is great for systems that need clear audits and reliable change tracking.

## References

**Microsoft Learn:** Event Sourcing pattern (https://learn.microsoft.com/en-us/azure/architecture/patterns/event-sourcing)

**AWS Prescriptive Guidance:** Event Sourcing pattern (https://docs.aws.amazon.com/prescriptive-guidance/latest/cloud-design-patterns/event-sourcing-pattern.html)

**Martin Fowler:** Event Sourcing (https://www.martinfowler.com/eaaDev/EventSourcing.html)
