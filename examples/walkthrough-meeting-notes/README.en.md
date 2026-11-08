# Walkthrough: turn a meeting transcript into notes (a complete small task, in English)

> 中文版：[README.md](README.md). This English page is self-contained: the input, the instruction to copy, a passing result, a failing result, and every register line are all below. Names and content are fictional.

This is a **low-dependency text task**: no network, no sign-in, no accounts. A text editor and one folder are enough. If you have an agent tool installed, hand the instruction below to your assistant.

**Two different things.** The per-host verification records (see the host table in the root [README.en.md](../../README.en.md)) show that a host can install the pack, call a skill by name, and produce one register line. This page shows **one complete small task**, from input to acceptance. The samples here were written by the authors following the method so you can compare against them; they are **not** a new test run on each host. How to install on your host: root [README.en.md](../../README.en.md), "Host support".

Status words used below (the skill and template texts are in Chinese; the Chinese word is in brackets so you can match them):

| Status | Meaning | Still on the open list? |
|---|---|---|
| pending (待收) | Handed out, nobody has confirmed taking it yet | Yes |
| taken (已接单) | The worker confirmed taking the job; **no result yet** | Yes |
| result received (已收到成果) | The deliverable is at the agreed place and you saw it; **not checked yet** | Yes (to check) |
| accepted (已验收) | Checked with `evidence-before-done`; can be passed on or closed | **No** |
| cancelled (已取消) | Someone with authority said "don't do it" | **No** |

Extra lines that never take a task off the open list: **extend** (续期), **escalate** (升级), **sent back** (退回). Only append lines; never overwrite earlier ones. Every line starts with the same task ID.

## Step 0: prepare

Make a working folder with an empty `notes/` subfolder, and save the transcript below as `input.md`. Keep a hand-off log (a text file or a spreadsheet).

**Input (`input.md`):**

```
Lin: Long-form first. I propose we publish one long article every Tuesday, starting next week. Agreed?
Zhou: Agreed.
Xu: Agreed, Tuesdays.
Lin: OK, decided: long article every Tuesday. I'll write the outline for the first one, by November 12.
Zhou: On covers, I suggest we always use a light background from now on; dark ones are hard to read on phones.
Xu: Light works for me too.
Lin: Light background, then. Zhou, can you make three sample covers?
Zhou: Sure, three sample covers by November 10.
Xu: The short-video trial numbers have been weak these two weeks. I suggest we pause it for two weeks and see.
Lin: Fine, the short-video trial is paused for two weeks. Xu, can you put the last two weeks' numbers on one page?
Xu: Yes, by November 11.
Zhou: By the way, we might move office next month. Not decided yet.
Lin: That's not decided, so it's not a decision today. Meeting over.
```

## Step 1: set the goal (what counts as done)

Write the acceptance checklist first; you will check against it later:

1. The result is at `notes/meeting.md`.
2. A "Decisions" section with the decisions made: 3 items.
3. An "Action items" section: 3 items, each with who, what, and by when.
4. Nothing that is not in the transcript; things the meeting called "not decided" are not listed as decisions.

## Step 2: assign (log before handing out)

```
pending | ID: M-01 | job: turn input.md into meeting notes | worker: Assistant A | collector: me | due: 2026-11-11 14:30 | who checks at due time / online?: me, online | result goes to: notes/meeting.md | done means: 3 decisions, 3 action items (who / what / by when), nothing added, undecided items not listed as decisions | suggested next skill: evidence-before-done
```

## Step 3: hand out (instruction to copy)

```
Please turn the meeting transcript in input.md into notes and save them to notes/meeting.md.
Requirements:
1. A "Decisions" section listing every decision made in the meeting.
2. An "Action items" section; each item says who, what, and by when.
3. Add nothing that is not in the transcript; do not list anything the meeting said was undecided as a decision.
When you take the job, reply "taken". When finished, reply with the file path and the number of items in each section.
```

The worker replies "taken" → append:

```
taken | ID: M-01 | time: 14:02 | taken by: Assistant A | due: same as original line
```

The job is only *taken*; nothing has come back. M-01 stays on the open list.

## Step 4: check at the due time

Due 14:30; at 14:35 open `notes/meeting.md`.

- File is there → append `result received | ID: M-01 | time: 14:35 | where: notes/meeting.md | agreed place?: yes | to check`. Still open.
- File is not there → do **not** write "result received". Not finished yet: append an **extend** line that keeps the original due time. Saved somewhere else: append **sent back** (see the last part of this page). A worker saying "done" without the file being where you can see it does not count. A waiting process that stopped does not mean the result is back either; go and look.

## Step 5: verify (`evidence-before-done`)

**Result A — passes:**

```
# Meeting notes

## Decisions
1. Publish one long article every Tuesday, starting next week.
2. Covers always use a light background.
3. Pause the short-video trial for two weeks.

## Action items
| Who | What | By |
|---|---|---|
| Lin | Outline for the first long article | Nov 12 |
| Zhou | Three sample covers | Nov 10 |
| Xu | One page with the last two weeks' short-video numbers | Nov 11 |

## Not decided
- Possible office move next month (the meeting said it is not decided).
```

**Result B — missing items, should be sent back:**

```
# Meeting notes

## Decisions
1. Publish one long article every Tuesday, starting next week.
2. Covers always use a light background.
3. Pause the short-video trial for two weeks.
4. Move office next month.

## Action items
| Who | What | By |
|---|---|---|
| Lin | Outline for the first long article | Nov 12 |
| Zhou | Three sample covers | Nov 10 |
```

Check each item of Step 1:

| Check | How | Result A | Result B |
|---|---|---|---|
| 1 Location | File is at `notes/meeting.md` | ✓ | ✓ |
| 2 Three decisions | Match the three "decided / then" lines in the transcript | ✓ 3/3 | ✗ adds "move office" |
| 3 Three action items with who and date | Match the three "I'll / can you" lines | ✓ 3/3 | ✗ 2/3, Xu's item missing |
| 4 Nothing added; undecided not a decision | Every item traces to a line in the transcript | ✓ | ✗ same as check 2 |

## Step 6: decide

**Branch A — accept:**

```
accepted | ID: M-01 | time: 14:41 | checked by: me | how (one line): opened the file and checked it against input.md: decisions 3/3, action items 3/3 with names and dates, office move listed as not decided | hand to / close: close
```

Only now does M-01 leave the open list.

**Branch B — send back, then accept the fix:**

```
sent back | ID: M-01 | time: 14:40 | what is missing / wrong: (1) action item "Xu | one page of short-video numbers | Nov 11" missing; (2) "move office next month" was not decided, cannot be a decision | worker told?: yes | new due: 15:00
extend | ID: M-01 | original due: 14:30 (kept) | new due: 15:00 | reason: sent back to fix two items | still collected by: me
result received | ID: M-01 | time: 14:58 | where: notes/meeting.md | agreed place?: yes | to check
accepted | ID: M-01 | time: 15:03 | checked by: me | how (one line): re-checked only the two changed sections (Decisions, Action items); the rest is word-for-word the version checked at 14:40, so that check is reused | hand to / close: close
```

From "sent back" until the final "accepted", M-01 stays on the open list. Note the re-check: only the changed parts are checked again; parts unchanged since a valid check are reused. A worker's own "fixed it" is a lead, not an independent check.

**Another missing case — wrong location:** at 14:36 `notes/meeting.md` does not exist and the worker says "it's on my desktop". Do not write "result received". Write:

```
sent back | ID: M-01 | time: 14:36 | what is missing / wrong: result not at the agreed place notes/meeting.md | worker told?: yes | new due: 14:45
```

You have now finished one real small task with this pack: input, result, evidence, acceptance, and one send-back.
