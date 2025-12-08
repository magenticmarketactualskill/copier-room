# Hexagonal Architecture Research Notes

## Core Definition
The hexagonal architecture (also called "ports and adapters architecture") is an architectural pattern that aims at creating **loosely coupled application components** that can be easily connected to their software environment by means of ports and adapters. This makes components **exchangeable at any level** and facilitates test automation.

## Origin
- Invented by **Alistair Cockburn** to avoid structural pitfalls in object-oriented software design
- Addresses problems like:
  - Undesired dependencies between layers
  - Contamination of user interface code with business logic
- Originally discussed on Portland Pattern Repository wiki
- Renamed "Ports and Adapters" in 2005
- Comprehensive book published in April 2024 (coauthored with Juan Manuel Garrido de Paz)

## Key Principles

### Component Division
The architecture divides a system into several **loosely-coupled interchangeable components**:
- Application core
- Database
- User interface
- Test scripts
- Interfaces with other systems

### Ports
- Components connect through exposed "ports"
- Communication follows a given protocol depending on purpose
- Ports and protocols define an **abstract API**
- Can be implemented by any suitable technical means (method invocation, RPC, web services)
- **Granularity is not constrained**:
  - Single port for simple service consumers
  - Typical ports: event sources (UI, automatic feeding), notifications, database, administration
  - Extreme case: different port for every use case

### Adapters
- **Glue between components and the outside world**
- Tailor exchanges between external world and ports
- Multiple adapters can exist for one port
- Example: data can be provided via GUI, CLI, automated source, or test scripts

## Comparison to Layered Architecture
- Alternative to traditional layered architecture
- Creates **symmetric components** (core surrounded by interfaces)
- Martin Fowler notes it hides inherent asymmetry between service provider and consumer

## Evolution and Variants

### Microservices
According to some authors, hexagonal architecture is at the **origin of the microservices architecture**.

### Onion Architecture (Jeffrey Palermo, 2008)
- Similar to hexagonal: externalizes infrastructure with interfaces
- Ensures loose coupling between application and database
- Decomposes application core into concentric rings using inversion of control

### Clean Architecture (Robert C. Martin, 2012)
- Combines principles of hexagonal, onion, and other variants
- Provides additional levels of detail as concentric rings
- Isolates adapters/interfaces in outer rings
- Inner rings for use cases and entities
- Uses **dependency inversion**: dependencies only from outer to inner rings, never reverse

## Key Benefits
1. **Framework independence**: Application core doesn't depend on frameworks
2. **Testability**: Business logic can be tested without UI, database, or external elements
3. **UI independence**: UI can change without changing business rules
4. **Database independence**: Can swap database technologies
5. **External agency independence**: Business rules don't know about outside world
