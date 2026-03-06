# 17-aws-reliability-security-backup

A production-minded database reliability toolkit: HA lab, backup/PITR drills, and zero-downtime migration playbooks.

Focus: backup


## Why this repo exists
This is a portfolio-grade, runnable toolkit that demonstrates how I approach database reliability work:
safe changes, predictable operations, and recovery you can actually trust.

## The top pains this repo addresses
1) Making databases boring again—high availability, predictable performance, safe backups, and zero/low-downtime migrations with solid tooling and runbooks.
2) Keeping production stable while the system scales—reducing incident frequency, improving MTTR, and building predictable operations (SLOs/runbooks/on-call hygiene).
3) Controlling cloud spend while meeting performance targets—capacity planning, right-sizing, and automation that prevents cost regressions.

## Quick demo (local)
Prereqs: Docker + Docker Compose.

```bash
make demo
```

What you get:
- a Postgres primary + replica setup
- PgBouncer for connection pooling
- scripts to verify replication and run verified backup/restore drills

## Design decisions (high level)
- Prefer drills and runbooks over “tribal knowledge”.
- Keep the lab small but realistic (replication + pooling + backup).
- Make failure modes explicit and testable.

## What I would do next in production
- Add PITR with WAL archiving + periodic restore tests.
- Add SLOs (p95 query latency, replication lag) and alert thresholds.
- Add automated migration checks (preflight, locks, backout plan).

## Tests (two modes)
This repository supports exactly two test modes via `TEST_MODE`:

- `demo`: fast, offline checks against fixtures only (no Docker calls).
- `production`: real integration checks against Dockerized Postgres when properly configured.

Demo:
```bash
TEST_MODE=demo python3 tests/run_tests.py
```

Production (guarded):
```bash
TEST_MODE=production PRODUCTION_TESTS_CONFIRM=1 python3 tests/run_tests.py
```

## Sponsorship and authorship
Sponsored by:
CloudForgeLabs  
https://cloudforgelabs.ainextstudios.com/  
support@ainextstudios.com

Built by:
Freddy D. Alvarez  
https://www.linkedin.com/in/freddy-daniel-alvarez/

For job opportunities, contact:
it.freddy.alvarez@gmail.com

## License
Personal/non-commercial use is free. Commercial use requires permission (paid license).
See `LICENSE` and `COMMERCIAL_LICENSE.md` for details. For commercial licensing, contact: `it.freddy.alvarez@gmail.com`.
Note: this is a non-commercial license and is not OSI-approved; GitHub may not classify it as a standard open-source license.
