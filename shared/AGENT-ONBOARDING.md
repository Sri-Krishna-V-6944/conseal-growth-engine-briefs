# Hermes Intelligence Platform — Agent Onboarding

You are a Hermes agent. This platform is your memory and learning system.
Humans review your output here; their decisions, edits and feedback are
collected and served back to you so every run is better than the last.

## The loop you are part of

1. **Before you work**, load what has been learned:
   - Local agents: read `<vault>/<platform>/memory/context-pack.md`
     (e.g. `/home/hermes/conseal-briefs-vault/reddit/memory/context-pack.md`).
     It is regenerated automatically whenever humans review your work.
   - API agents: `GET /api/v1/agent/context-pack?platform=<slug>` (add
     `&format=md` for markdown).
2. **Do your work** — write briefs into the vault (they are ingested within
   seconds) or POST signals/briefs directly to the API.
3. **Save what you learn** — POST notable lessons to `/api/v1/agent/memory`.

## API basics

- Base URL: `http://localhost:3050` (same host as the vault)
- Auth: `Authorization: Bearer hip_<your key>` on every endpoint
- Discover endpoints: `GET /api/v1/agent/` (no auth needed)
- Check your key: `GET /api/v1/agent/ping`

## Endpoints

| Method | Path | Purpose |
|---|---|---|
| GET | /api/v1/agent/context-pack?platform=&format=json\|md | Everything learned, one call |
| GET | /api/v1/agent/memory?platform=&tags=&q=&limit= | Search memory (pinned first) |
| POST | /api/v1/agent/memory | Save a learning: {title, content_md, platform?, tags?[]} |
| GET | /api/v1/agent/examples?platform=&status=approved\|rejected | Your drafts vs final human text |
| GET | /api/v1/agent/feedback?platform=&since=&kind= | Human feedback, newest first |
| POST | /api/v1/agent/signals | Submit a signal: {platform, title, external_url?, community?, pain_md?, icp_fit_md?, confidence?, drafts?[]} |
| POST | /api/v1/agent/briefs | Submit a whole brief: {platform, brief_type, raw_markdown} |

## File conventions (vault: /home/hermes/conseal-briefs-vault)

- Write briefs to `<platform>/<type>-briefs/DD-MM-YYYY HH:MM.md`
  (e.g. `reddit/morning-briefs/12-06-2026 09:00.md`). They are ingested
  automatically; signals and drafts are extracted into the review queue.
- Read `<platform>/memory/context-pack.md` before drafting. Never edit it.
- `confidence` on API-submitted signals: 0–1; values >= 0.8 alert the team.

## What humans do with your output

Each signal moves through: new → in_review → approved/rejected →
responded → won. Every draft edit is versioned; rejection reasons and
corrections are written down. All of it flows back into your context pack.
