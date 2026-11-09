---
name: team-standup
description: "Run the team's morning standup or evening wrap, as the coordinator of a team of named Claude Code sessions. Morning: read the board's log and every worker's notebook, ask only the workers whose notebook is out of date, and give the user one short page per name (yesterday, today, waiting on), the slots, the contracts at risk and the top of their queue, with a proposed order for the day. Evening ('wrap'): have every worker bring its notebook up to date, stop its servers and release its slots, then write down what's open for tomorrow. Use when the user asks for a standup, a morning round, what everyone is doing today, a wrap, the end of the day, or to close the day. Triggers: 'standup', 'stand-up', 'morning round', 'wrap', 'wrap up', 'end of day', 'close the day'."
argument-hint: "[wrap]"
---

# Team standup

Mode: **$ARGUMENTS**

An empty mode (or one that still reads `$ARGUMENTS`) means the morning standup. `wrap` means the evening wrap.

Run this in the coordinator's session (see the `team-coordinator` skill). If this session isn't the coordinator, say
so and stop: the standup needs the board, the notebooks and the right to brief the workers.

## Morning standup

1. **Read** your notebook, the board's state sections, the board's log since the last standup or wrap, and every
   worker's notebook.
2. **Ask only the workers whose notebook is out of date.** A notebook is out of date when its "Updated" time is older
   than the worker's last log line, or older than the last wrap. Send each of them one message: "Standup: bring your
   notebook's Now up to date, then reply `Done: notebook updated`." Don't message the others. Don't poll: the replies
   come to you.
   - A worker that doesn't answer gets "no answer; from its notebook of <time>". Never fill in its state yourself.
   - A message that bounces means a restart: re-map the worker and mark it on the page.
   - A worker the user keeps for ad-hoc work gets its line, but no plan from you.
3. **Check the team's state:**
   - slots: the holder and since when, whether the slot is really in use (listeners, database sessions), and who's
     next;
   - numbers assigned a while ago and still unused;
   - contracts at risk: a consumer waiting on a producer that's behind or changed course;
   - who is blocked, on whom, and since when;
   - the top of the user's queue.
4. **Write the page,** and append it to the board's log in one write:

   ```
   ## Standup 2026-11-10

   - **rex** (PROJ-12): yesterday the endpoint, committed a1b2c3d · today the tests · waiting on nothing
   - **rosy** (PROJ-14): yesterday the page, uncommitted · today wire it to rex's endpoint · waiting on rex's head
   - **max** (ad hoc for the user): the UAT config · holds nothing

   Slots: test DB copy free. Numbers: 1680 rex, unused.
   At risk: PROJ-14 needs PROJ-12's endpoint; rex expects it by noon.
   Your queue: 2 items, first: rosy asks whether the page shows inactive users.
   Proposed order: 1. rex finishes PROJ-12 and hands the head to rosy. 2. rosy wires the page. 3. max as you like.
   ```

   One line per worker. Refs, not dumps.
5. **Give the user the page** with your proposed order, and ask one thing: OK the order, or change it. The other open
   items stay in the queue, and you hand them over one at a time afterwards.
6. **On the user's answer,** log it, update the Plan, and brief only the workers whose day changed, one message each.

## Evening wrap

1. **Message every worker** that has work open or holds anything:
   "Wrap: bring your notebook's Now up to date for a cold start tomorrow, stop your servers, clean up and release your
   slots, release the numbers you no longer need, log it on the board, then reply `Done: wrapped` with anything still
   open."
2. **Check the releases yourself:** nothing listening on a released slot's ports, no open sessions on its database. A
   slot still held overnight needs a reason, and the user hears about it.
3. **Write the wrap,** and append it to the board's log in one write:
   - done today, per name, with refs;
   - open for tomorrow, per name: the next step from its notebook;
   - what's still held (slots, numbers), and why;
   - what's waiting for the user: the queue in order, and any push or post waiting for a go.
4. **Top up the time** of every ticket worked on today that already has time booked, if a time-keeping skill is
   installed (for example `ticket-time`). Put the changes in the wrap: "PROJ-12: 5 → 7 h".
5. **Update your own notebook's "Now".**
6. **Give the user the wrap.** Ask nothing, unless something needs their go before they leave. In that case, ask that
   one thing.

## Rules

- **A wrap is not a go.** Nobody commits, pushes or posts as part of it. Uncommitted work stays as it is, and the
  worker's notebook says so.
- **Report the truth.** States come from the notebooks and the log. Mark anything stale or unanswered as such.
- **Keep it short.** One page, one line per worker, and one question at most.
- **Don't ask the workers** for what their notebook or the log already shows.
