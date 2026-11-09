# team-skills

Three [Claude Code](https://claude.com/claude-code) skills for running several Claude Code sessions as one team for
one person: a named **coordinator**, its named **workers**, and a daily **standup** and **wrap**.

## Why

Several sessions working in parallel get a lot done, but they also cause trouble:
- two sessions edit the same branch;
- one ticket needs another, and they're built to different shapes;
- two branches pick the same migration number;
- a test database gets used by two sessions at the same time;
- five questions reach the user at once;
- "the user said go" gets passed from session to session until nobody knows who actually approved what.

These skills give the team one coordinator, one written board and one set of rules.

## How it works

- **Everyone has a name**, the coordinator too: for example adam coordinates, and rex and rosy work. The name is the
  identity. Open a new chat, run `/team-worker rex`, and it takes up rex's work where rex stopped.
- **Every name keeps a notebook**, `team/<name>.md`: its memory between sessions. It holds what it's on, where it
  stopped, what it's waiting for, what it owes a teammate, and what it has learned. Only its owner writes it, and it
  outlasts the sprint boards.
- **The coordinator runs the team:**
  - plans and sequences the tickets;
  - makes tickets that need each other agree their contract before they build;
  - hands out slots (such as a test database and its servers) and migration numbers;
  - relays the user's approvals;
  - integrates the branches;
  - keeps the user's queue to one thing at a time.
- **Workers talk to each other directly** about shared work, and tell the coordinator only what it needs: done,
  blocked, a question for the user, a booking, or a finding that touches another ticket.
- **One board holds the state:**
  - the team, the plan, the contracts, the shared-file rules, the slots, the numbers and the user's queue;
  - an append-only log that everyone writes to.
- **The day has a rhythm:** `/team-standup` in the morning gives the user one page per name and a proposed order;
  `/team-standup wrap` in the evening has everyone update their notebook and release their slots, and writes down
  what.s open for tomorrow.

The skills are built around these rules:
- approvals flow down from the user, never up from a worker;
- no session does what another was denied;
- outward actions (pushes, PRs, posts) need the user's go on the exact text.

They work well with [dev-notes](https://github.com/luuk-atlantis-engineering/dev-notes), which records the reason
behind every decision the team makes.

## Install

```sh
git clone https://github.com/luuk-atlantis-engineering/team-skills.git
cp -r team-skills/skills/team-coordinator team-skills/skills/team-worker team-skills/skills/team-standup ~/.claude/skills/
```

Start the sessions and give each one its name:

```
/team-coordinator adam
/team-worker rex
/team-worker rosy
```

Without a name, the skill asks for one. A name that's already on the board takes up that name's work. A new
coordinator name starts a board from `templates/BOARD.md`, finds the sessions with `ListAgents`, and maps each name to
its session.

## Configure

Tell the team where the board lives, in your `CLAUDE.md`:

```
Coordination board: ~/development_notes/coordination/
```
