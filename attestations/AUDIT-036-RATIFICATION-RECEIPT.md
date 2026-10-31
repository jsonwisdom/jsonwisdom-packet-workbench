# LDP-1 ASCII Policy Ratification Receipt

**AUDIT_ID:** AUDIT-036  
**DECISION:** RATIFY  
**DECISION_SOURCE:** EXPLICIT_USER_AUTHORIZATION  
**Protocol:** LDP-1-v1.0  
**Date recorded:** 2026-10-31  

## Decision

The protocol owner explicitly authorized ratification of  
`LDP-1-ASCII-POLICY-DELTA-033` as a normative clarification of LDP-1-v1.0.

## Normative clarification (ratified)

Alphabetic fields:

1. Accept ASCII code points U+0000 through U+007F, inclusive, including control characters.
2. Reject all non-ASCII Unicode code points.
3. Preserve internal spaces, leading spaces, tabs, carriage returns, line feeds, NUL, DEL, and other ASCII controls.
4. Remove trailing ASCII SPACE (0x20) only.
5. Enforce `max_length` after that normalization.
6. Reject values that exceed field width without truncation.
7. Preserve every accepted, non-normalized byte through encoding and decoding.

The 80-byte record layout, numeric encoding, schema validation, and rejection rules remain unchanged.

## Supporting audit identifiers

- AUDIT 032 — control character observation
- AUDIT 033 — policy delta prepared
- AUDIT 034 — 12/12 regression vectors PASS (reference unmodified)
- AUDIT 035 — exact byte round-trip for NUL/TAB/LF/CR/DEL confirmed
- AUDIT 036 — explicit ratification decision

## Preservation controls

- Reference implementation (`ldp1.py`, `test_vectors.py`) — UNCHANGED
- Source SHA-256 digests — UNCHANGED
- EAS Schema #2003 — UNCHANGED
- Existing attestation — UNCHANGED
- IPFS manifest — UNCHANGED
- Johnny V001 — UNCHANGED
- No new EAS attestation
- No schema registration
- No deployment
- No GitHub repository modification
- No new IPFS object

## Scope limits

- Production equivalence — UNKNOWN
- Production promotion — HOLD
- Authority created — FALSE
- External publication — NOT PERFORMED

## Ledger

```
AUDIT_ID=AUDIT-036
DECISION=RATIFY
DECISION_SOURCE=EXPLICIT_USER_AUTHORIZATION
SPECIFICATION_RATIFIED=true
RATIFICATION_SCOPE=ASCII_POLICY_CLARIFICATION
REFERENCE_IMPLEMENTATION_MUTATED=false
PRODUCTION_EQUIVALENCE=UNKNOWN
PRODUCTION_PROMOTION_HOLD=true
AUTHORITY_CREATED=false
EXTERNAL_PUBLICATION=NOT_PERFORMED
```

This receipt records the decision. It does not itself constitute external publication.
