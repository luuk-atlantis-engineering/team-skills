# <Sprint or effort name>: coordination board

Started YYYY-MM-DD. Coordinator: <name> (`<session>`). Previous board: <link, or "none">.

## Rules

<!-- How this team works, as the user set it. Keep it short; add a line when the user corrects something. -->

- Mode: step by step | relay (until <when>)
- The user talks to: the coordinator only | each worker directly
- Pushes, PRs and posts: only on the user's go
- Checks: <what runs before a push>

## Team

<!-- The name is the identity; the session changes on a restart. -->

| Name | Session | Working on | Note |
|---|---|---|---|
| <rex> | `<session>` | <ticket, branch> | <e.g. reserved for the user's ad-hoc work> |

## Plan

| Ticket | What | Owner | Depends on | Status |
|---|---|---|---|---|
| <PROJ-1> | <one line> | <name> | <PROJ-0: the endpoint it adds> | todo / doing / review / done |

## Contracts

<!-- What two tickets agreed about the seam between them. A change stops both sides until it's agreed again. -->

| Between | What's agreed | Ready when | Notes |
|---|---|---|---|
| <PROJ-1 (rex) → PROJ-2 (rosy)> | <the names, shapes and files> | <a commit, or a stub first> | <link to the decision> |

## Shared files

| File | Tickets | Rules |
|---|---|---|
| <the login page> | <PROJ-1, PROJ-3> | each adds its own block; never moves or reformats a neighbour's lines |

## Slots

<!-- One holder at a time. Check it's free before a grant; the holder says what it left behind. -->

| Slot | Includes | Holder | Since | Next | Left behind |
|---|---|---|---|---|---|
| <test DB copy> | <database, ports 5000/4200> | free | | | |

## Numbers

<!-- Migration numbers (and other numbers that must stay unique), from the pool the user reserved. -->

Pool: <e.g. 1680–1699>. Order: <e.g. schema before data>.

| No. | Ticket | What | State |
|---|---|---|---|
| <1680> | <PROJ-1> | <adds column X> | assigned / used / released |

## Branches

| Name | Branch | Worktree | Base |
|---|---|---|---|
| <rex> | <branch> | <path> | <parent branch> |

## The user's queue

<!-- One item goes to the user at a time. Top = next. Strike through when answered and log the answer. -->

1. <who asks> · <the question or draft, one line> · <the coordinator's recommendation>

## Open decisions

<!-- Move a row to the ticket's DECISIONS.md (or the log) once it's decided, with its why. -->

| Question | Options | Who decides | Status |
|---|---|---|---|

## Log

<!-- Append only, everyone writes, one line per event, newest at the bottom: date, name, what, refs, what's next. -->

- YYYY-MM-DD <name>: board started.
