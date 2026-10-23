# BackendKit

BackendKit is a planned collection of reusable backend feature modules for Django and Laravel. Each module will package one feature with explicit dependencies, compatibility, installation steps, and validation guidance.

## Supported frameworks

| Framework | Language | Status |
| --- | --- | --- |
| Django | Python | Architecture ready; no modules published |
| Laravel | PHP | Architecture ready; no modules published |

No feature modules are implemented yet. The registry is intentionally empty so discovery never advertises placeholders as usable software.

## Discover and use modules

Start with [`AGENTS.md`](AGENTS.md) for the short agent workflow, then read [`registry.yaml`](registry.yaml). A listed module's `path` leads to its `MODULE.md` and `manifest.yaml`, which are its canonical integration guide and machine-readable metadata. For humans, the framework directories contain framework-specific guidance.

A future CLI can use the same registry and manifests for commands such as `backendkit list`, `backendkit info booking --framework django`, and `backendkit add booking --framework django`. The CLI is not implemented in this repository yet.

## Module conventions

[`specs/module-spec.md`](specs/module-spec.md) defines the required module layout and metadata contract. Shared feature behavior may be specified in `specs/<feature>.md` when that feature is actually introduced; framework implementations should link to and follow that specification where it applies.

## Add a module

1. Check the registry for an existing module ID and review the shared feature specification, if one exists.
2. Create `modules/<module-name>/` under the target framework with `MODULE.md`, `manifest.yaml`, `src/`, and `tests/`.
3. Document dependencies, supported versions, integration steps, and validation in the manifest and `MODULE.md`, following [`specs/module-spec.md`](specs/module-spec.md).
4. Add a registry entry only when the module exists and is ready for discovery. Keep its path, framework, language, version, dependencies, and status aligned with its manifest.
5. Validate the registry and module metadata, run the module's documented checks, and update the framework README if needed.

Keep modules isolated and documentation canonical: the registry is the compact index, the manifest is structured metadata, and `MODULE.md` is the integration guide.
