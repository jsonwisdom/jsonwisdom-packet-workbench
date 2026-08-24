# Evidence Scope Doctrine V1

- Status: normative evidence discipline
- Version: `1.0`
- Authority created: `false`

## 1. Scope is declared before the read

Every evidentiary read MUST declare its scope before execution. Scope is an input, not a conclusion.

A result MUST NOT silently enlarge the scope that was inspected. Inspecting `bin/pak` establishes facts about `bin/pak`; it does not establish facts about "the verifier" unless that broader scope was declared and completely inspected.

A declared scope should identify, as applicable:

- object or repository;
- fixed state or snapshot;
- membership boundary;
- content boundary;
- predicate being tested.

## 2. Core predicates

### `SURFACE_COMPLETE(scope)`

TRUE only when the read enumerates every member inside the declared scope at the fixed state.

### `THIRD_PARTY_REPLAYABLE(tuple)`

TRUE only when another party can reproduce the observation from the recorded identifiers alone.

Completeness and replayability are independent. A local complete directory listing may be complete but not independently replayable. A content-addressed snapshot can provide both.

## 3. Negative evidence classes

### `BOUNDED_NEGATIVE(scope)`

A proof of absence inside a declared, completely inspected scope.

Requirements:

1. scope declared before the read;
2. fixed state identified when state can change;
3. `SURFACE_COMPLETE(scope) = TRUE` for the tested predicate;
4. the negative claim does not exceed that scope.

Replayability strengthens provenance but does not enlarge scope.

### `SEARCH_NEGATIVE`

A query returned no visible match.

`SEARCH_NEGATIVE = INDETERMINATE` for existence claims. Search indexes, permissioned connectors, ranking systems, and partial discovery surfaces do not prove absence unless they independently satisfy `SURFACE_COMPLETE` for the predeclared scope.

## 4. Membership and semantic content are separate scopes

Complete membership inspection proves what paths or members exist. It does not automatically prove what logic or meaning is contained inside those members.

A semantic negative requires a predeclared content predicate and complete inspection of the content set relevant to that predicate.

Example:

- fixed Git commit + `bin/pak` lookup returning no path -> `BOUNDED_NEGATIVE(bin/pak@commit)`;
- full Git tree enumeration -> complete file-placement coverage for that commit;
- full tree enumeration plus inspection of every blob for a predeclared verifier-implementation predicate -> bounded semantic conclusion for that commit.

## 5. Immutable evidence pointers

For Git file evidence, record:

`{ repository, commit_sha, path, blob_sha }`

- `blob_sha` binds content;
- `commit_sha + path` binds placement;
- repository binds namespace;
- branch names are discovery metadata, not canonical immutable refs.

## 6. Corroboration guard

Repetition is not corroboration. Agreement, acknowledgement, countersigning, or repeated restatement does not increase evidentiary strength unless it introduces an independent evidentiary origin.

Ten agreeing statements with one origin remain one evidentiary origin.

## 7. Fail-closed rule

When completeness, provenance, replayability, or scope is unresolved, preserve the narrower claim and fail closed.

`PASS != authority`

`CI-SIGNED != authority`

`SEARCH_NEGATIVE != absence`

`ACKNOWLEDGEMENT != evidence`
