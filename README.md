# My Advent of CALM Journey

This repository tracks my 24-day journey learning the Common Architecture Language Model (CALM).

## Progress

- [x] Day 1: Install CALM CLI and Initialize Repository
- [x] Day 2: Create Your First Node
- [x] Day 3: Connect Nodes with Relationships
- [x] Day 4: Install CALM VSCode Extension
- [x] Day 5: Add Interfaces to Nodes
- [x] Day 6: Document with Metadata
- [x] Day 7: Build Complete E-Commerce Architecture
...


## Understanding this repo

* **Architectures** - This directory will contain CALM architecture files documenting systems.
* **Patterns** - This directory will contain CALM patterns for architectural governance.
* **Docs** - Generated documentation from CALM models.

## Getting Started
### Tools

The following tools are used:

#### CALM CLI

The FINOS CALM CLI provides command-line utilities for working with CALM architectures and patterns.

**Installation:**
```bash
npm install -g @finos/calm-cli
```

**Key Features:**
- **Validation**: Validate architectures and patterns against CALM schemas
- **Generation**: Create architecture scaffolds from patterns
- **Templates**: Generate documentation and reports from CALM models
- **Docify**: Create browsable documentation websites

**Basic Commands:**
```bash
# Validate an architecture file
calm validate -a my-architecture.json

# Validate both pattern and architecture
calm validate -p pattern.json -a architecture.json

# Generate architecture from pattern
calm generate -p pattern.json -o architecture.json

# Create documentation website
calm docify -a architecture.json -o docs/
```

#### CALM VSCode Extension

The CALM VSCode extension provides rich IDE support for working with CALM files.

**Installation:**
- [CALM VSCode Plugin on Marketplace](https://marketplace.visualstudio.com/items?itemName=FINOS.calm-vscode-plugin)
- Or search for "CALM" in VSCode Extensions

**Key Features:**
- **Visualization**: Interactive architecture diagrams
- **Tree Navigation**: Explore nodes, relationships, and flows
- **Live Preview**: Real-time visual feedback as you edit
- **Schema Validation**: Inline error detection

**Keyboard Shortcuts:**
- `Ctrl+Shift+C` (Windows/Linux) / `Cmd+Shift+C` (Mac) - Open CALM preview

#### Workflow: CLI + Extension

The CLI and extension complement each other perfectly:

1. **Edit**: Use VSCode extension for visual feedback while editing CALM files
2. **Validate**: Run `calm validate` in terminal to ensure compliance
3. **Preview**: Use extension's live preview to visualize architecture
4. **Document**: Use `calm docify` to generate shareable documentation