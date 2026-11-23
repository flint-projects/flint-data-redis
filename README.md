# Flint Data Redis

Flint Data Redis is the D port of the public API of [Spring Data Redis](https://github.com/spring-projects/spring-data-redis), part of the Flint family of repositories ([ADR-030](https://github.com/StevenBuglione/flint/blob/main/docs/adr/ADR-030-flint-is-a-spring-port.md)).

A developer who knows Spring Data Redis sees the same annotations, classes, methods and configuration keys. The only renaming: where an identifier or key contains the word "Spring", it says "Flint" (`spring.*` keys are accepted as aliases). The engine underneath is D or C only, and Flint's metrics (build time, binary size, throughput, p99, RSS, CPU per request) must stay ahead of Go.

## Status

Not started. This repository is scheduled for Milestone 15 of the [Flint roadmap](https://github.com/StevenBuglione/flint/blob/main/docs/adr/ADR-021-flint-platform.md). It is an *integrated* repository: Flint Boot auto-configures it, so it sits between `flint-boot` and `flint-framework` (boot → integrated → framework → flint).

## How the port is done

- Public elements follow the [Java → D API mapping rulebook](https://github.com/StevenBuglione/flint/blob/main/docs/spring/api-mapping.md); every adapted element cites a rule, and every deviation is listed.
- The pinned upstream API is extracted with `flint api extract`, and `flint api coverage` fails on any element not classified as ported, adapted or excluded.
- Upstream tests are ported alongside the code.
- How each upstream project may be used is set by [`policy/upstream-licences.json`](https://github.com/StevenBuglione/flint/blob/main/policy/upstream-licences.json).

## Licence

Apache License 2.0 (see `LICENSE` and `NOTICE`). Ported files keep their upstream headers and are marked "Modified by the Flint authors".

Spring and the names of Spring projects are trademarks of Broadcom Inc. and/or its subsidiaries. Flint is not affiliated with or endorsed by Broadcom.
