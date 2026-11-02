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

**Command Handler:** Receives commands, validates them, and performs actions.
**Event:** Keeps a record of completed events.
**Event Store:** A database that only adds new events and never changes old ones.
**Projection:** A view of data created by processing events for fast reading.
