# RxScan Data Releases

Public, read-only distribution registry for versioned RxScan medication identity data.

This repository is the publication boundary between RxScan Data and its consumers. RxScan Data remains the sole authority that generates release artifacts. Guide, Paramedic, and future RxScan applications consume only published channel pointers and immutable release directories from this repository.

## Repository layout

```text
approvals/
  README.md
channels/
  dev.json
  stable.json
registry/
  events/
    README.md
releases/
  README.md
schema/
  README.md
  *.schema.json
recognition/
  channels/
    stable.json
  releases/
    <releaseId>/
```

- `channels/dev.json` and `channels/stable.json` are the only mutable distribution pointers.
- `approvals/<releaseId>.json` will contain immutable approval evidence.
- `registry/events/` will contain append-only lifecycle events.
- `releases/<releaseId>/` will contain immutable, versioned release artifacts.
- `schema/` contains only the public JSON contracts required to verify releases.
- `recognition/channels/stable.json` is the mutable Recognition Stable pointer.
- `recognition/releases/<releaseId>/` contains immutable Recognition artifacts
  copied byte-for-byte from an authorized RxScan Data promotion.

Both channels are intentionally uninitialized. No DEV or stable release is published by this infrastructure bootstrap.

## Immutability

Release directories are append-only. Once `releases/<releaseId>/` is merged, its files must never be changed, replaced, moved, or deleted. Corrections require a new release identifier. Rollbacks update a channel pointer to an already approved release; they do not rewrite release bytes.

The same append-only rule applies to `recognition/releases/<releaseId>/`.

Repository protection and CI reject modifications or deletions beneath an existing release path. Channel pointers remain reviewable, short-lived metadata and must reference manifests by SHA-256.

## Public-data boundary

Published releases may contain consumer identity profiles and their verification metadata only. They must not contain internal scripts, validation tooling, governance records, working history, unpublished candidates, clinical overlays, OCR rules, patient data, secrets, or internal documentation.

This repository does not replace or remove the historical `prehos-rxscan-data` repository during migration. No Guide or Paramedic application is migrated by this bootstrap.

## License

See [LICENSE](LICENSE).
