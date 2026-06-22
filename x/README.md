# X/Twitter Buy-Signal Briefs — Conseal

Monitors X for high-intent posts where authors have a problem Conseal solves:
AI blocked by compliance, confidential document processing, redaction frustration,
privacy-safe AI workflows, PII handling, document workflow pain, local processing needs.

## Directory Structure

```
x/
  morning-briefs/     # Files: DD-MM-YYYY HH:00.md
  evening-briefs/     # Files: DD-MM-YYYY HH:00.md (primary scan)
  ICP Notes.md        # Running observations about ICP signals on X
  Response Library.md # Reusable draft replies
  README.md           # This file
```

## Scan Schedule

- Evening scan (primary): 15:30 UTC / 21:00 IST — covers last 24 hours
- Morning scan (occasional): 03:30 UTC / 09:00 IST — covers overnight

## Credit Budget

$5 X API credits. Scan runs conservatively: 7 queries, ~70 lookups per scan.
If credits deplete, the brief reports it clearly.

## Brief Format

Each brief:
- YAML frontmatter with scan metadata
- Top 1-2 buy-signal posts with full scoring
- Draft replies (Version A with product mention, Version B without)
- Activity log entry
