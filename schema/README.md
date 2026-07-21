# Public release schemas

These JSON Schemas define the public contracts used to verify RxScan release manifests, active channel pointers, approval records, and registry events.

`empty-channel-pointer-1.0.0.schema.json` applies only while a channel has never selected a release. The first publication atomically replaces that document with an active pointer conforming to `channel-pointer-1.0.0.schema.json`.

Schema files are versioned. Breaking contract changes require a new schema filename and version; existing schema files must not be rewritten after use by a published release.
