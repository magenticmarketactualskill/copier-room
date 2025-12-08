# JSON-RPC-LD Analysis Notes

## Overview
JSON-RPC-LD is a lightweight extension to the JSON-RPC 2.0 protocol that incorporates the semantic expressiveness of JSON-LD (JSON for Linked Data) and the validation capabilities of SHACL (Shapes Constraint Language).

## Problem Statement
JSON-RPC 2.0 is a simple and effective protocol for remote procedure calls, but it lacks a standardized mechanism for expressing the semantic meaning of the data exchanged between client and server. This can lead to:
- Ambiguity in data interpretation
- Tight coupling between client and server implementations

## Solution Approach

### JSON-LD Integration
JSON-RPC-LD introduces an optional mechanism for embedding JSON-LD contexts within JSON-RPC messages. This allows clients and servers to exchange data that is:
- Structured
- Semantically rich
- Machine-readable

### SHACL Validation
JSON-RPC-LD provides a way for servers to publish SHACL shapes that define:
- Expected structure of data for each method
- Types of data
- Validation rules
- Clear documentation

## Technical Specifications

### The @context Member
A JSON-RPC-LD Request or Response object MAY include a `@context` member within the `params` or `result` object. The value MUST be a valid JSON-LD context as defined in the JSON-LD 1.1 specification.

When present, the `@context` provides a mapping from terms used in the `params` or `result` object to IRIs (Internationalized Resource Identifiers), enabling the data to be interpreted as Linked Data.

### SHACL-based Validation
A JSON-RPC-LD server MAY provide a SHACL shapes graph to describe the expected structure and types of the `params` and `result` for each method. This shapes graph can be used by:
- Clients for validation
- Developers for documentation

The mechanism for discovering the SHACL shapes graph is not defined in the specification, but it is RECOMMENDED that servers provide a link to the shapes graph in their API documentation.

## Example Structure

### Request with Semantic Context
```json
{
  "jsonrpc": "2.0",
  "method": "getUser",
  "params": {
    "@context": {
      "id": "@id",
      "User": "http://example.org/User",
      "userId": "http://example.org/User#id"
    },
    "@type": "User",
    "userId": 123
  },
  "id": 1
}
```

### Response with Semantic Context
```json
{
  "jsonrpc": "2.0",
  "result": {
    "@context": {
      "id": "@id",
      "User": "http://example.org/User",
      "name": "http://xmlns.com/foaf/0.1/name",
      "email": "http://xmlns.com/foaf/0.1/mbox"
    },
    "@id": "http://example.org/users/123",
    "@type": "User",
    "name": "John Doe",
    "email": "john.doe@example.com"
  },
  "id": 1
}
```

## Key Technologies

### JSON-RPC 2.0
A stateless, light-weight remote procedure call protocol. Defines several data structures and rules around their processing.

### JSON-LD (JSON for Linked Data)
A lightweight Linked Data format that adds semantic meaning to JSON through:
- **@context**: Defines how terms map to IRIs (vocabularies)
- **@id**: Unique identifier for the object (IRI)
- **@type**: Type of the object
- W3C Recommendation (16 January 2014)

### SHACL (Shapes Constraint Language)
Validates RDF graphs against conditions. Key concepts:
- **Shapes Graph**: RDF graph containing validation conditions
- **Data Graph**: RDF graph being validated
- **Shapes**: Define constraints and validation rules
- **Targets**: Define which nodes to validate
- **Constraints**: Validation rules applied to focus nodes
- W3C Recommendation (20 July 2017)

## Benefits for Cross-Framework Communication

### Semantic Interoperability
By using JSON-LD contexts, different systems can understand the meaning of data beyond just its structure. This enables:
- Framework-agnostic communication
- Shared vocabulary across different programming languages
- Machine-readable API contracts

### Validation and Documentation
SHACL shapes provide:
- Clear contracts for method parameters and results
- Automated validation capabilities
- Self-documenting APIs

### Loose Coupling
The semantic layer reduces tight coupling by:
- Providing explicit meaning for data fields
- Enabling evolution of data structures without breaking clients
- Supporting multiple interpretations of the same data

## Relevance to Hexagonal Architecture

JSON-RPC-LD aligns with hexagonal architecture principles by:
- Providing a **protocol-level abstraction** for communication between components
- Enabling **framework independence** through semantic interoperability
- Supporting **adapter pattern** implementation through standardized RPC interface
- Facilitating **loose coupling** between application core and external systems
- Enabling **testability** through clear contracts and validation

The semantic layer (JSON-LD) and validation layer (SHACL) provide the "protocol" that hexagonal architecture's "ports" can use to communicate, regardless of the underlying framework or programming language.
