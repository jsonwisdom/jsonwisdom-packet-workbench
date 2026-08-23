# `src/replay/`

Owns the Replay Compare decision sequence: independently invoke packet and receipt validation, return `HOLD` on either failure, otherwise compare declared fields and return `MATCH` or `DELTA`.

Forbidden: duplicating validators, interpreting values, selecting a winner, mutating inputs, network access, identity claims, findings, and authority creation.

