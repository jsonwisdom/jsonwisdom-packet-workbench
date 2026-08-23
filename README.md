# JSONWisdom Packet Workbench

Sealed JSON packet validation and deterministic Replay Compare.

**Core boundary:** shape and receipt—not identity, findings, truth, or authority.

## Contract

1. Validate each packet independently.
2. If either packet fails shape, authority, or receipt validation, emit `HOLD`.
3. Only after both pass, compare declared fields and emit `MATCH` or `DELTA`.

See [`docs/boundaries/REPLAY_COMPARE_BOUNDARY_V1.md`](docs/boundaries/REPLAY_COMPARE_BOUNDARY_V1.md).

## Status

Directory and boundary scaffold only. No executable implementation or passing-test claim exists yet.

- Version: `0.1.0-scaffold`
- Authority created: `false`

