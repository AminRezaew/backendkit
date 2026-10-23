# Module specification

Every discoverable module is an implemented, installable feature for one framework. Do not register placeholders or planned modules.

## Layout

```text
modules/<module-name>/
├── MODULE.md
├── manifest.yaml
├── src/
├── tests/
├── docs/       # only for necessary detail beyond MODULE.md
└── examples/   # optional
```

Keep each module self-contained. Use predictable paths and avoid copying guidance between files. `MODULE.md` is the canonical integration guide; `manifest.yaml` is the canonical machine-readable metadata. Additional docs should be linked from `MODULE.md`.

## Manifest contract

Each `manifest.yaml` must be valid YAML and contain:

```yaml
schema_version: 1
id: booking
group: booking
name: Booking
framework: django
language: python
version: 1.0.0
description: Short, one-line purpose.
status: stable
dependencies:
  runtime: []
  development: []
compatibility:
  framework: ">=5.0,<6.0"
integration:
  install: "Documented command or concise procedure"
  validation: "Documented command or concise procedure"
```

Use a unique `id` for the framework-specific package and a shared `group` for corresponding cross-framework implementations. `framework` and `language` use lowercase names (`django`/`python`, `laravel`/`php`). `version` is the module version. `status` is one of `stable`, `beta`, or `deprecated`; only usable modules may appear in the registry. Runtime and development dependencies are explicit lists. Add configuration, routes, migrations, or other integration metadata only when relevant and document its shape here.

The repository registry is a compact index with `schema_version` and a `modules` list. Each listed module has `id`, `name`, `framework`, `language`, `path`, `version`, `description`, `dependencies`, and `status`. Keep those values aligned with its manifest; use `path` relative to the repository root and `dependencies` as a concise runtime dependency list. Do not duplicate full compatibility or setup instructions in the registry.

## MODULE.md contents

Keep this guide concise and action-oriented. Include the following sections, omitting only sections that do not apply:

- Purpose and features
- Requirements and dependencies (consistent with the manifest)
- Installation and configuration
- API, routes, models, or entities when relevant
- Integration points and customization or extension points
- Tests and validation
- Important constraints
- Link to the shared feature specification, when one exists

Give exact commands and paths where possible. The guide must state any assumptions and compatibility limits that affect integration.
