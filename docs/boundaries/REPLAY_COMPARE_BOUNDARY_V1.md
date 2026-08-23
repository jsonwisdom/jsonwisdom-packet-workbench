# JSONWisdom Replay Compare Boundary V1

- Status: architecture contract; no implementation claim
- Version: `1.0`
- Locked: `true`
- Authority created: `false`
- Recorded: `2026-08-23`

## 1. Object boundary

JSONWisdom is labeled-packet machinery. It is not a person, identity, finding, claims engine, truth engine, or authority.

## 2. Sealed packet

A sealed packet is a closed, schema-versioned JSON envelope plus a SHA-256 receipt over its canonically serialized receipt-bearing content. The exact receipt boundary must be declared by the future versioned schema and canonicalization specification; it must never be guessed at runtime.

## 3. Receipt meaning

SHA-256 binds bytes. A matching digest can show that the hashed bytes are unchanged under the declared canonicalization. It does not prove truth, correctness, authorship, legitimacy, safety, or authority.

## 4. Independent gates

Packet A and Packet B each independently pass:

1. closed-envelope shape validation;
2. structural enforcement that `authorityCreated` exists and equals the boolean literal `false`;
3. SHA-256 receipt verification under the declared canonicalization.

No result from one packet can validate the other.

## 5. HOLD first

If either packet fails any gate, Replay Compare emits `HOLD`. Comparison does not run. Invalid identical packets cannot produce `MATCH`; invalid differing packets cannot produce `DELTA`.

## 6. MATCH and DELTA

Only after both packets independently pass:

- `MATCH`: every schema-declared compared field binds under the comparison specification.
- `DELTA`: at least one schema-declared compared field differs.

Neither mark selects a winner or says which packet is correct.

## 7. Closed envelope

Unknown properties fail shape validation and therefore produce `HOLD`. Missing `authorityCreated`, non-boolean values, and `true` produce `HOLD`. Type coercion is forbidden.

## 8. Output boundary

Replay Compare may emit validation marks, receipt marks, field paths, and `HOLD | MATCH | DELTA`. It must not emit interpretation, findings, recommendations, identity or ownership claims, truth claims, or authority.

The UI displays engine output. It cannot compute, upgrade, or rewrite a verdict.

## 9. Repository separation

Anti-Drift News replay, ReceiptOS, replay-membrane, and other event or authorization replay systems are outside this repository. Their schemas, state models, and conclusions are not imported implicitly.

## 10. Enforcement sentence

`HOLD first. MATCH and DELTA only after both packets independently pass. No interpretation. No authority minted.`

