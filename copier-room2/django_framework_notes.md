# Django Framework Research Notes

## Overview
Django is a high-level Python web framework that encourages rapid development and clean, pragmatic design. It follows the **MVT (Model-View-Template)** architecture, which is a variation of the traditional MVC pattern.

## MVT Architecture
- **Model**: Handles data and database logic (Active Record pattern)
- **View**: Handles business logic and request processing
- **Template**: Handles presentation and rendering

## Core Design Philosophies

### Overall Principles

**Loose Coupling and Tight Cohesion**
Django's fundamental goal is that various layers of the framework shouldn't "know" about each other unless absolutely necessary. For example, the template system knows nothing about web requests, the database layer knows nothing about data display, and the view system doesn't care which template system is used. Although Django comes with a full stack for convenience, the pieces are independent wherever possible.

**Less Code**
Django apps should use as little code as possible and lack boilerplate. Django takes full advantage of Python's dynamic capabilities like introspection.

**Quick Development**
The framework should make tedious aspects of web development fast, allowing for incredibly quick development.

**Don't Repeat Yourself (DRY)**
Every distinct concept or piece of data should live in one, and only one, place. Redundancy is bad, normalization is good. The framework should deduce as much as possible from as little as possible.

**Explicit is Better than Implicit**
Core Python principle from PEP 20. Django shouldn't do too much "magic." Magic is only worth using if it creates huge convenience unattainable in other ways.

**Consistency**
The framework should be consistent at all levels, from low-level Python coding style to high-level user experience.

### Models Philosophy

**Explicit is Better than Implicit**
Fields shouldn't assume behaviors based solely on field names. Behaviors should be based on keyword arguments and field types.

**Include All Relevant Domain Logic**
Models should encapsulate every aspect of an "object," following Martin Fowler's Active Record design pattern. Both the data represented by a model and information about it (human-readable name, default ordering, etc.) are defined in the model class.

### Database API Philosophy

**SQL Efficiency**
Execute SQL statements as few times as possible and optimize internally. Developers must call save() explicitly rather than the framework saving silently. The select_related() QuerySet method exists as an optional performance booster.

**Terse, Powerful Syntax**
The database API should allow rich, expressive statements in minimal syntax. Joins should be performed automatically behind the scenes when necessary.

**Option to Drop into Raw SQL**
The framework should make it easy to write custom SQL when needed.

### Template System Philosophy

**Separate Logic from Presentation**
The template system controls presentation and presentation-related logic only, nothing beyond this basic goal.

**Discourage Redundancy**
Template inheritance allows common sitewide design elements (header, footer, navigation) to be stored in a single place.

**Be Decoupled from HTML**
The template system should be equally good at generating other text-based formats or plain text.

**Don't Invent a Programming Language**
The goal is to offer just enough programming-esque functionality (branching, looping) essential for presentation-related decisions. The Django Template Language (DTL) aims to avoid advanced logic.

**Safety and Security**
The template system should forbid inclusion of malicious code. This is another reason it doesn't allow arbitrary Python code.

### URL Design Philosophy

**Loose Coupling**
URLs should not be coupled to underlying Python code. Tying URLs to Python function names is discouraged.

**Infinite Flexibility**
URLs should be as flexible as possible. Any conceivable URL design should be allowed.

**Encourage Best Practices**
The framework should make it easy to design pretty URLs. File extensions in web-page URLs should be avoided.

### Views Philosophy

**Simplicity**
Writing a view should be as simple as writing a Python function. Developers shouldn't have to instantiate a class when a function will do.

**Use Request Objects**
Views should have access to a request object storing metadata about the current request, passed directly to the view function.

## Key Characteristics

### Integration Approach
Django is a **full-stack framework** that provides integrated components:
- Object-relational mapper (ORM)
- Automatic admin interface
- Robust template system
- Quick internationalization

### Philosophy vs. Hexagonal Architecture
Django's approach represents a **tightly integrated full-stack** philosophy where components are designed to work together seamlessly, though they maintain loose coupling at the architectural level. This contrasts with hexagonal architecture's emphasis on complete framework independence and interchangeable adapters.
