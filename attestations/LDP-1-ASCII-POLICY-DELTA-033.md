# LDP-1 ASCII Policy Clarification

**Document:** LDP-1-ASCII-POLICY-DELTA-033  
**Status:** RATIFIED (AUDIT-036)  
**Baseline:** LDP-1-v1.0  
**Implementation:** REFERENCE_IMPLEMENTATION / UNCHANGED  

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

## Downstream requirements

Alphabetic fields are untrusted binary-capable data. Consumers must not treat them as safe for:

- terminal rendering without escaping,
- log injection,
- JSON string embedding without proper escaping,
- or any parser that interprets control characters as structure.

Trimming trailing spaces is intentionally lossy with respect to the original input.

## Evidence

AUDIT 034: 12/12 regression vectors PASS against unmodified reference.  
AUDIT 035: exact byte round-trip for NUL, TAB, LF, CR, DEL confirmed.

## Ratification

Ratified by explicit protocol-owner decision in AUDIT-036. See `attestations/AUDIT-036-RATIFICATION-RECEIPT.md`.
No new EAS attestation is required for this clarification. Production promotion remains HOLD.
