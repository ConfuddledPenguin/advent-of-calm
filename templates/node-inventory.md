---
architecture: ../architectures/ecommerce-platform.json
---
# Node Inventory: {{metadata.description}}

| Name | Type | ID | Description |
|------|------|-------|-------------|
{{#each nodes}}
| {{name}} | {{kebabToTitleCase node-type}} | `{{unique-id}}` | {{description}} |
{{/each}}

## Services Only

{{#each nodes}}
{{#if (eq node-type "service")}}
- **{{name}}** (`{{unique-id}}`): {{description}}
{{/if}}
{{/each}}

## Databases Only

{{#each nodes}}
{{#if (eq node-type "database")}}
- **{{name}}** (`{{unique-id}}`): {{description}}
{{/if}}
{{/each}}

## Actors

{{#each nodes}}
{{#if (eq node-type "actor")}}
- **{{name}}**: {{description}}
{{/if}}
{{/each}}