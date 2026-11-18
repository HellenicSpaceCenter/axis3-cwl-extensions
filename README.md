# AXIS3 CWL extensions

CWL extension vocabulary for AXIS3 input UI annotations.

- [RDF vocabulary](axis3hub.ttl)
- [Usage and CWL examples](docs/cwl-ui-extension.md)

The examples use `https://github.com/hellenicspacecenter/main/axis3hub.ttl`
for `$schemas` and the same URL with a trailing `#` for the `axis3hub` namespace.

The vocabulary defines two boolean input annotations:

- `axis3hub:hidden`: omit the input control.
- `axis3hub:disabled`: display the input control without allowing edits.

Hidden takes precedence when both annotations are true. These annotations
control presentation; required inputs still need values, and execution-time
restrictions require backend enforcement.
