# Ruby on Rails Framework Research Notes

## Overview
Ruby on Rails is a full-stack web framework written in Ruby. It follows the **MVC (Model-View-Controller)** architecture and emphasizes rapid development with an opinionated approach.

## The Rails Doctrine: Nine Pillars

### 1. Optimize for Programmer Happiness
Rails inherits Ruby's core philosophy of placing programmer happiness on a pedestal. Ruby valued expressiveness, subtlety, and accommodating programmer feelings over rigid constraints. Rails was created to make the creator (DHH) smile first and foremost, enriching the daily work of building web applications.

### 2. Convention over Configuration
Rails assumes application structure and needs rather than requiring explicit configuration details. Developers only specify unconventional aspects. This reduces boilerplate and decision fatigue by providing sensible defaults.

### 3. The Menu is Omakase
Rails is opinionated and curated like an omakase menu at a sushi restaurant. The framework makes choices for you, providing a complete integrated solution rather than requiring developers to assemble components.

### 4. No One Paradigm
Rails doesn't subscribe to a single programming paradigm. It embraces multiple approaches (object-oriented, functional elements, metaprogramming) to solve problems pragmatically.

### 5. Exalt Beautiful Code
Code aesthetics matter. Rails values code that is not just functional but also beautiful and expressive to read and write.

### 6. Provide Sharp Knives
Rails gives developers powerful tools without excessive safety guardrails. It trusts developers to use advanced features responsibly rather than protecting them from themselves.

### 7. Value Integrated Systems
Rails is a **full-stack framework** that ships with all tools needed to build web apps on both front and back end. Components are designed to work together seamlessly:
- Rendering HTML templates
- Updating databases
- Sending/receiving emails
- Maintaining live pages via WebSockets
- Enqueuing jobs for asynchronous work
- Storing uploads in the cloud
- Security protections

The framework values tight integration over loosely coupled components that must be assembled.

### 8. Progress over Stability
Rails prioritizes moving forward and adding new features over maintaining absolute backward compatibility. The framework evolves to embrace new ideas and technologies.

### 9. Push Up a Big Tent
Rails welcomes diverse developers and use cases rather than catering to a narrow audience.

## MVC Architecture

### Model (Active Record)
- Databases come to life with business logic encapsulated in rich objects
- Modeling associations between tables
- Callbacks when saved
- Encrypting sensitive data seamlessly
- Expressing SQL queries beautifully
- Follows Martin Fowler's Active Record design pattern

### View (Action View)
- Templates mix Ruby and HTML
- Full versatility of Ruby available
- Excessive code extracted into helpers
- Domain model used directly and interwoven with HTML

### Controller (Action Controller)
- Expose domain model to the web
- Process incoming parameters
- Set caching headers
- Render templates
- Respond with HTML or JSON

### Routing (Action Dispatch)
- Configure how URLs connect to controllers
- Routes expose bundles of actions as resources
- Standard actions: index, show, new, create, edit, update, destroy

## Philosophy vs. Hexagonal Architecture

Rails represents a **tightly integrated, opinionated full-stack** approach where:
- Components are designed to work together seamlessly
- The framework makes architectural decisions for you
- Integration is valued over interchangeability
- Convention reduces configuration needs

This contrasts sharply with hexagonal architecture's emphasis on:
- Complete framework independence
- Interchangeable adapters
- Explicit ports and protocols
- Business logic isolation from infrastructure
