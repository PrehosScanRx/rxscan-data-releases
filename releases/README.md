# Immutable releases

This directory is intentionally empty of application releases.

Future releases use the following shape:

```text
releases/<releaseId>/
  manifest.json
  profiles/
  provenance/
```

Every `<releaseId>` directory is append-only and immutable. Never edit, replace, move, or delete an existing release. Publish corrections under a new release identifier and promote a channel pointer only after validation and approval.
