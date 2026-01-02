# CALM Patterns

## What are Patterns?

CALM Patterns are JSON Schema documents that define reusable architecture templates. They have a **dual superpower**:

1. **Generation**: Scaffolding new architectures that conform to the pattern
2. **Validation**: Ensuring existing architectures comply with the pattern's constraints

Patterns enable teams to enforce architectural standards, promote consistency, and accelerate development by providing proven architecture blueprints.

## Using the Web Application Pattern

The `web-app-pattern.json` defines a standard 3-tier web application architecture.

### Generation

Create a new architecture from the pattern:

```bash
calm generate -p patterns/web-app-pattern.json -o my-app.json
```

This generates a skeleton architecture with all required nodes and relationships that you can then customize.

### Validation

Validate an existing architecture against the pattern:

```bash
calm validate -p patterns/web-app-pattern.json -a my-app.json
```

This ensures your architecture conforms to the pattern's requirements.

## What the Pattern Enforces

The web-app-pattern.json enforces:

### Nodes (exactly 3)
- **web-frontend**: A `webclient` node named "Web Frontend"
- **api-service**: A `service` node named "API Service"  
- **app-database**: A `database` node named "Application Database"

### Relationships (exactly 2)
- **frontend-to-api**: Connects web-frontend to api-service
- **api-to-database**: Connects api-service to app-database

The pattern uses `const` constraints to lock down unique-ids, node-types, and names, ensuring architectural consistency across implementations.

## What's Flexible

While the pattern enforces structure, you can customize:

- **Descriptions**: Add meaningful descriptions to nodes and relationships
- **Interfaces**: Define host, port, protocol for services and databases
- **Metadata**: Add tags, properties, controls, or other metadata
- **Implementation details**: Specify technologies, configurations, deployment details

This balance between constraint and flexibility allows teams to maintain architectural standards while adapting to specific requirements.
