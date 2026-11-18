# CWL input UI annotations

The RDF vocabulary is stored in [`../axis3hub.ttl`](../axis3hub.ttl) in the
standalone `axis3-cwl-extensions` repository.

The namespace is
`https://github.com/hellenicspacecenter/main/axis3hub.ttl#`.
Publishing the vocabulary does not implement frontend rendering.

```yaml
cwlVersion: v1.2
$namespaces:
  axis3hub: https://github.com/hellenicspacecenter/main/axis3hub.ttl#
$schemas:
  - https://github.com/hellenicspacecenter/main/axis3hub.ttl

# Within a Workflow:
inputs:
  process_frequency:
    type: string
    default: adhoc
    axis3hub:hidden: true
  process_version:
    type: string
    default: "6.19.1"
    axis3hub:disabled: true
```

Merge `$namespaces` and `$schemas` into the document root, including for packed
`$graph` documents. `$schemas` is the standard CWL schema-loading field.
The namespace declaration makes these custom input keys valid extensions;
loading the RDF vocabulary additionally describes their boolean values.

## Intended UI behavior

- `axis3hub:hidden: true`: omit the input control.
- `axis3hub:disabled: true`: show the control without permitting edits.
- Missing or false annotations: visible and editable.
- If both are true, hidden takes precedence.

Consumers should identify properties by their expanded namespace URI, rather
than requiring the literal prefix `axis3hub`, because CWL authors can choose
another prefix. Required inputs still need defaults or backend-supplied values.
Backend enforcement is necessary to prevent API callers from overriding values.

