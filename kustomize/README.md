# What is Kustomize?

Kustomize is a native Kubernetes configuration management tool designed to customize and manage resource configurations in a declarative and reusable way. Instead of relying on templating or parameterization, it works directly with Kubernetes manifests without altering their underlying structure.

## Key Features

- Dynamically creates variations of Kubernetes resources while maintaining human-readable manifests
- Fully declarative and GitOps-friendly
- Allows resource modifications without changing base files using patches, transformers, and generators
- Ensures clean separation of concerns and simplifies long-term maintenance

## Configuration Management Layering

Kustomize achieves reusability through the following layers:

- **Base Layer** - Specifies the most common resources
- **Patch Layers** - Specifies use case specific resources

## Kustomize Patches

There are two main types of patches Kustomize can apply, each suited for different use cases.

### Strategic Merge Patching

Strategic merge patching uses JSON/YAML merge semantics. This approach merges the patch with the existing resource, preserving the original configuration while introducing changes from the patch.

#### Patch Logic

When Kustomize applies a strategic merge patch:

- Any existing fields in the base that are not addressed by the patch remain untouched
- New fields from the patch get added to the base configuration
- Existing fields are overwritten by the patch's values

### JSON Patch

Kustomize JSON patching, based on the JSON Patch specification, allows for precise modifications to Kubernetes resources by applying explicit changes in JSON format. Unlike strategic patching, JSON patching directly adds, removes, or replaces fields.

#### Patch Syntax

A patch consists of an array of patch operations, each defined by:

- **op** - The operation to perform (`add`, `remove`, `replace`, `move`, `copy`, or `test`)
- **path** - The JSON path to the field that needs to be modified
- **value** - (for `add`, `replace`, and `move` operations) The new value to be set or moved

## Resources

- [Densify Kustomize Guide](https://www.densify.com/kubernetes-tools/kustomize/)
- [Practice Repository](https://github.com/shimulmahmud/devops-config/tree/main/kustomize)
