# Agent instructions

1. Read `registry.yaml` first to discover available modules and their paths.
2. Do not scan the repository broadly. Open only the requested framework and module directory.
3. Read that module's `MODULE.md` before inspecting or changing its source.
4. Resolve dependencies and compatibility from its `manifest.yaml`; do not search the repository for them.
5. Inspect the target project before integrating anything. Reuse its authentication, models, and infrastructure when compatible.
6. Follow the module's documented installation and integration steps, then run its documented tests or validation.
7. If the requested module is absent from the registry, report that it is unavailable. Do not treat examples or specifications as implementations.

Module metadata and layout are defined in `specs/module-spec.md`.
