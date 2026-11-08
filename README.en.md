# Solo to Team · 一人成队

**Skills for human-led AI teams.**  
Repository: `solo-to-team-skills` · Initiated by **Dabing (大冰)** · License: MIT  
Chinese: [README.md](README.md)

**Team Organization & Collaboration Report (PDF, 17 pages): [docs/solo-to-team-value.pdf](docs/solo-to-team-value.pdf)**

> **Document status: v0.9.4-draft** (English), aligned with Chinese README.md v0.9-draft on the key facts below. Not a final release; it may still change before the public launch.
>
> **Version note:** wording may land in Chinese first. That is a drafting habit, **not** a delivery standard that allows known gaps. An overseas reader should be able to use **this English file alone** to: understand what the pack is for, install and call it on a supported host, follow the main example, and know the support scope and limits. Those key points are kept in sync with the Chinese README. Line-by-line translation is not required.

## What this is

One person can lead a team of AI assistants.

This is a pack you can **get, install, and call**: four skills + one template + instructions + redacted case notes. It is for one person coordinating several long-lived AI assistants, and it keeps a grip on the things that slip most often: handed-off work gets collected, "done" comes with evidence, steps for newcomers work on the first try, and lessons from mistakes are kept for the next person.

The pack borrows ideas and methods; what it delivers is a rewritten Chinese collaboration pack plus two original skills, installed and called by name in several agent tools. Sources are credited in [`NOTICE`](NOTICE) and in the source / attribution section at the end of each skill.

The skills carry no timers or wake-ups of their own (the plugin manifest has `hooks: {}`): checking on time, marking work "taken", "result received" and "accepted", and starting the next step follow the steps in the skill text, done by you or by your AI tool.

**Language note:** the skill bodies (`SKILL.md`) and the register template are currently written in Chinese (some descriptions also carry English hints). The hosts below can still load and follow them; ask your assistant to reply in English if you want. **Complete English walkthrough** (input, instruction to copy, passing and failing results, every register line, with the Chinese status words glossed): [examples/walkthrough-meeting-notes/README.en.md](examples/walkthrough-meeting-notes/README.en.md).

## What you get

- **A team of one: work you hand out gets picked up, tracked, and brought back.** One line from start to finish: hand out → collect → verify → decide. Before handing work out, log one "pending" line: who is doing it, who collects it, who checks at the due time. When the worker takes it, mark it "taken"; when the result is at the agreed place, mark it "result received" with the path; only after checking the evidence mark it "accepted". The register line makes unclaimed work easy to spot; the due-time check and follow-up are done by you or by your host's scheduling (see the three-column table under "Core flow").
- **Switch tools without relearning how you coordinate.** The four core skill texts are shared across hosts, so you learn the method once. Where to install, how to call, and what else each host needs are written per host, from its real setup, under "Host support".
- **Start with one table and take the first step toward leading an AI team.** The main example and the register-line template are ready to use: practice hand out, collect, and verify in a notebook or spreadsheet first. That practices the method; to have an AI assistant call the skills by name, you still need to install an agent tool.
- **Built from real work.** Two redacted cases (reworking a daily production pipeline; catching gaps in a review chain) record the problem, the change, the result, and what is still unsolved — see [`ops-case-notes`](skills/ops-case-notes/).

What that looks like in practice:

- After you hand work out, there is a logged line and someone checks at the due time. "Taken", "result received" and "accepted" are recorded separately; a task leaves the open list only when accepted or cancelled by someone with authority.
- Before anyone says "done", there is valid evidence for the current version; anything changed or failed since is re-checked, unchanged parts may reuse an earlier valid check.
- Steps are written so a newcomer can follow them; for owner-only steps, say "owner does this" and do not invent a workaround that does it for them.
- Mistakes from real operations leave redacted, reusable method notes (problem / change / result / still open).

| Skill | What it covers |
|---|---|
| [`dispatch-accept-verify`](skills/dispatch-accept-verify/) | Hand work out, log a "pending" line, check at the due time, record taken / result received / accepted separately, escalate when nobody picks it up |
| [`evidence-before-done`](skills/evidence-before-done/) | Before anyone says "done", get valid evidence for the current version: open it, rerun it, check it line by line; reuse an earlier valid check for unchanged parts |
| [`beginner-ops-writing`](skills/beginner-ops-writing/) | Write steps a newcomer can follow once and succeed; includes two fictional worked examples; owner-only steps stay "owner does this" |
| [`ops-case-notes`](skills/ops-case-notes/) | Two redacted real cases: what went wrong, what changed, what improved, what is still unsolved |

Template: [`templates/task-register-line.md`](templates/task-register-line.md) (one-line pending / taken / result received / accepted / sent back / cancelled / extend / escalate records, in Chinese; English versions of the lines are in the walkthrough; title means "copy to use", not one-click install of the whole pack).

## Core flow (first release)

One line: **set the goal → assign → hand off → verify → decide**.

| Flow step | Skill |
|---|---|
| Assign + hand off | [`dispatch-accept-verify`](skills/dispatch-accept-verify/) |
| Verify | [`evidence-before-done`](skills/evidence-before-done/) |
| How to write owner-only steps | [`beginner-ops-writing`](skills/beginner-ops-writing/) |
| Real detours | [`ops-case-notes`](skills/ops-case-notes/) |

Same job, three kinds of responsibility:

| Flow step | This pack | Your host tool | A human must |
|---|---|---|---|
| Set the goal | Fields for what / where / when (register line) | Open a session, take your words | Decide the goal, order, and definition of done |
| Assign | Log a "pending" line before hand-off: who does it, who collects, who checks on time | Open sessions or sub-agents; send cross-agent messages if the host can | Choose who gets the work; approve dangerous actions (spend, send, delete) |
| Hand off | Check on time, mark "taken" / "result received", extend, escalate, then kick off the next step | Timers / wake-ups — **use the host's if it has them; this pack does not** (`hooks: {}`) | Check on the clock yourself if the host has no timer |
| Verify | Get valid evidence for the current version (open, rerun, walk the steps again); mark "accepted" | Open files, run commands, show results | Do owner-only steps (login, payment, personal confirm) |
| Decide | Lay out evidence and status; point to similar past cases | — | Accept, send back, or change direction — final call is always human |

## How to start

Pick the path that matches you. You do **not** need any internal team handbook. The core skill texts are shared across hosts and there is no separate app; entry points and requirements differ per host — see "Host support".

### Starting from zero with AI or programming

"Starting from zero" means your starting point with AI / programming. If you can state a task clearly, divide work, and check a result, you already have enough.

1. Read the [main example](#main-example-hand-out-collect-verify-then-decide) below, then follow the complete English walkthrough: [examples/walkthrough-meeting-notes/README.en.md](examples/walkthrough-meeting-notes/README.en.md).
2. Open [`templates/task-register-line.md`](templates/task-register-line.md) and learn one "pending" line, one "result received" line, and one "accepted" line (English versions are in the walkthrough).
3. Start with one table: practice the method in a notebook or spreadsheet — write "pending" before handing work out, check at the due time, mark "result received" when it is back, and "accepted" once checked. This practices the method; to have an AI assistant call the skills by name, install an agent tool using the host sections below.

### Already using an AI assistant

1. Find your host below and follow **Prepare → Load → Call**.
2. Enable two skills first: `dispatch-accept-verify` and `evidence-before-done`.
3. Run the [main example](#main-example-hand-out-collect-verify-then-decide): pending → taken → check on time → result received → verify → accepted.
4. Open `ops-case-notes` when something goes wrong.

### Already running several assistants

1. Use the three-column table above and fill in what your host is missing under "Your host tool".
2. Read [`ops-case-notes`](skills/ops-case-notes/) for where hand-off and verify failed in real work.
3. Map the register-line fields into your own tracker. `hooks: {}` means you wire automation with the host; this pack does not do it for you.

### "About ten minutes"?

**Measured (Cursor CLI, non-interactive, prompt prepared ahead):** about **0.5 minutes** (29.6 seconds). Prerequisites: Cursor installed and signed in (including the CLI), this pack already obtained, network available; from copying the four skills into `~/.cursor/skills/` until a readable pending ("待收") line is produced. Does **not** include installing or registering the host, or time spent typing by hand. It only measures **producing a register line from the CLI in a prepared environment**; it is not how long a newcomer takes from zero (installing a host) to finishing a whole task.

"About ten minutes" remains a **design goal**, or an external framing when host install time is included; it is **not** a measured guarantee. Other hosts have not been timed to the same stopwatch definition yet.

### Main example: hand out, collect, verify, then decide

Fictional scene: you ask an AI assistant to turn a meeting transcript into notes and put them in a file you name. (Names and paths are made up.)

**Follow it end to end in English:** [examples/walkthrough-meeting-notes/README.en.md](examples/walkthrough-meeting-notes/README.en.md) — the input, an instruction to copy, a passing result, a result with missing items that gets sent back, and every register line.

| Step | Flow | You do | Skill / template | Check |
|---|---|---|---|---|
| 1 | Set the goal | Write what to summarize, where it goes (e.g. `notes/meeting.md`), when it is due, what counts as done | [`task-register-line.md`](templates/task-register-line.md) | One sentence can say what "done" means |
| 2 | Assign | Before hand-off, write one "pending" line: who does it, who collects, who checks on time | [`dispatch-accept-verify`](skills/dispatch-accept-verify/) | The pending line exists before the work is handed out |
| 3 | Hand off | When the worker takes it, mark "taken". At the due time, check: only if the file is at the agreed place, mark "result received" with the path; if not, extend (keep the original due time) or escalate | [`dispatch-accept-verify`](skills/dispatch-accept-verify/) | Someone checked on time; you did not wait for the other side to remember; "taken" is not "result back" |
| 4 | Verify | Before saying done, open the result yourself and compare it to step 1 | [`evidence-before-done`](skills/evidence-before-done/) | Evidence matches this version of the result, not a second-hand report; after a resubmission, re-check only what changed |
| 5 | Decide | Accept (mark "accepted"), send back (mark "sent back"), or change the goal | — (human) | Only "accepted" or "cancelled" takes a task off the open list |

Optional:

- A step only you can do (login, payment confirm) → follow [`beginner-ops-writing`](skills/beginner-ops-writing/) and mark "owner does this"; do not invent a workaround that skips you.
- Want to see where this chain failed in real work → open [`ops-case-notes`](skills/ops-case-notes/).

## Host support

**General rule: each host listed here has been verified separately in real use, but they install and behave differently. Do not assume that installing the skills makes your agents work as a team automatically.**

Verification standard (same for every host): get the pack → install / configure → call the skill by name → get an inspectable output (for example a readable "pending" register line). These records show install → call → a register line; the complete small task is shown separately in the walkthrough, whose samples were written by the authors and are not a new test run on each host. In addition, on the current pack version, each of the eight setups has one acceptance record for a limited task (real output → check against the request → human acceptance): the earlier separate Codex run is retained, and the other seven were tested on the same meeting-notes task. Some hosts needed another attempt after a blocked run or a revision before acceptance. This does not show stability or that every kind of task will succeed. How the host was invoked differs by host (some runs were sent by the user inside the host, some from a CLI or with assisted clicks), and some hosts kept no raw trace of skill loading. This does not mean all four skills were called on every host, and it does not prove effectiveness. The pack has been **verified in actual use across multiple agent tools**; the scope is exactly the table below. "Supported" means that specific install-and-call path has a successful run on record — it does **not** extend to other products or clients under the same brand.

The eight supported setups are **not** the same feature set. Loading a skill only means the assistant can follow this method; timers, cross-assistant messages, and wake-ups depend on the host — or on a human.

Common preparation:

- Get the pack: download or clone this repository and keep the `skills/` folder (four subfolders, each with one `SKILL.md`).
- The host app is installed and you can sign in.
- You can write to the target folder (usually under your home directory).
- **When copying by hand, copy the whole skill folder** (`skills/<skill-name>/`), not just `SKILL.md`: `dispatch-accept-verify` must keep its `templates/` folder, or the register-line template is lost. If a host takes only one text (e.g. saving a Grok Bot private skill), paste the template in as well.
- **Installing only some skills:** the "accepted" step of `dispatch-accept-verify` depends on `evidence-before-done`, so install those two together; `evidence-before-done` also works on its own. `beginner-ops-writing` and `ops-case-notes` are optional companions; the main flow works without them.
- Commands and menu labels follow the host's official docs on the day you install; what is written here is the path that worked in our verification, not a promise every version matches word for word.

| Host | Status | Install (summary) | Call |
|---|---|---|---|
| Codex | Supported | Local pack root as source: `marketplace add` → `plugin add solo-to-team-skills@solo-to-team-skills` (pack ships `.agents/plugins/marketplace.json`) | By skill name in a new session or via `codex exec` |
| WorkBuddy | Supported | Copy to `~/.workbuddy/skills/` or project `.workbuddy/skills/`, or upload a zip | By skill name |
| DeepSeek Harness | Supported | Copy to `.dsh/skills/`, `~/.dsh/skills/` or `.agents/skills/` | Reopen / refresh, then by name |
| Cursor | Supported | Copy to `~/.cursor/skills/` | By name in Agent or CLI |
| CodeBuddy | Supported | Copy to `~/.codebuddy/skills/` or project `.codebuddy/skills/` | By name in app or CLI |
| Grok Bot | Supported, manual setup required | Save each `SKILL.md` as a private skill in chat | By name |
| Kimi Work | Supported | Copy to `daimon-share/daimon/skills/` (see below), or official upload / store | `/` skill picker |
| QwenWork (千问办公) | Supported | Copy to `~/.qwenworkcn/skills/` | `/` skill picker or by name |
| Claude Code | Structure ready, not yet verified | `.claude-plugin/` | Not part of launch support |

Not yet verified: Tongyi Lingma, TRAE, Comate, and any tool not listed above.

Easy to confuse: **CodeBuddy ≠ WorkBuddy**; **QwenWork ≠ Tongyi Lingma**; **Kimi Work ≠ Kimi Code CLI**. Grok Bot "supported, manual setup" covers **private skills inside the Grok Bot product only**, not other Grok clients or product lines.

### Codex (supported)

- **Entry:** this pack ships [`.agents/plugins/marketplace.json`](.agents/plugins/marketplace.json) (marketplace name **`solo-to-team-skills`**), plus [`.codex-plugin/plugin.json`](.codex-plugin/plugin.json) (`skills: "./skills/"`, `hooks: {}`). The root [`plugin.json`](plugin.json) follows the Agent Plugins format; which file a host reads follows that host's behavior.
- **Prepare:** **Codex CLI** installed and signed in; you already have this pack on disk (the folder that contains `skills/` and `.agents/plugins/marketplace.json`). Until a public repo exists, **the source is that local folder — do not use a GitHub URL**.
- **Load** (replace `/path/to/solo-to-team-skills` with your absolute pack root):

```bash
cd /path/to/solo-to-team-skills
codex plugin marketplace add "$(pwd)"
codex plugin add solo-to-team-skills@solo-to-team-skills
```

  If `marketplace add` / `plugin add` exits non-zero, stop and check that the path is the pack root that contains `.agents/plugins/marketplace.json`. Then open a **new** session (or use `codex exec` below). Rollback: `codex plugin remove solo-to-team-skills@solo-to-team-skills`, then `codex plugin marketplace remove solo-to-team-skills`.
- **Call:** name the skill in a new session, e.g. "Use dispatch-accept-verify to log a pending task for me." Non-interactive example:

```bash
codex exec -s workspace-write --skip-git-repo-check -C "$(pwd)" 'Use skill dispatch-accept-verify; write one pending-receipt line to T044_dispatch_line.md'
```

- **You get:** register lines and verification notes from the main example, as files you can open.
- **Host / human:** no automatic wake-ups (`hooks: {}`); due-time checks are done by you or by scheduling Codex already has.

### WorkBuddy (supported)

- **Target:** `~/.workbuddy/skills/<skill-name>/`, or `<project>/.workbuddy/skills/<skill-name>/`, or in-app "upload local skill package" (one skill folder, or a zip containing `SKILL.md`).
- **Prepare:** WorkBuddy installed and signed in.
- **Load:** upload the folder / zip, or copy the whole skill folder into the path above.
- **Call:** by skill name inside WorkBuddy.
- **You get:** inspectable output from the main example.
- **Note:** WorkBuddy is **not** CodeBuddy. Different products, different folders.
- Docs: https://www.workbuddy.ai/docs/zh/workbuddy/From-Beginner-to-Expert-Guide/Function-Description/Skills

### DeepSeek Harness (supported)

- **Target:** project `.dsh/skills/<name>/`, user `~/.dsh/skills/<name>/`, or `.agents/skills/`.
- **Prepare:** DeepSeek Harness installed; your own DeepSeek account or API key (**this pack ships no keys**).
- **Load:** copy the whole skill folder into one of those paths, then reopen or refresh Harness. `dsh plugin add` is **not** how skill bodies are installed here — use the folder copy.
- **Call:** by skill name.
- **You get:** inspectable output from the main example.
- Upstream reference: https://github.com/deepseek-ai/deepseek-harness/blob/master/docs/subsystems/skills.md

### Cursor (supported)

- **Target:** `~/.cursor/skills/<skill-name>/`.
- **Prepare:** Cursor (editor or CLI) installed and signed in.
- **Load:** copy the four skill folders (or the two you need first) into that path.
- **Call:** by name in Cursor Agent, or from the CLI, e.g. `cursor agent --print`. For non-interactive runs in a workspace you just created you may need `--trust` — that marks **this workspace as trusted**; it does **not** turn off safety checks.
- **You get:** inspectable output from the main example.

### CodeBuddy (supported)

- **Target:** `~/.codebuddy/skills/<skill-name>/SKILL.md`, or project `.codebuddy/skills/<skill-name>/`.
- **Prepare:** CodeBuddy (app or CLI) installed and signed in.
- **Load:** copy the whole skill folder into that path. The first release does **not** ship a `.codebuddy-plugin` and is not listed in a marketplace; copying the folder is enough.
- **Call:** by skill name in the app or CLI (CLI syntax per official docs for the day).
- **You get:** inspectable output from the main example.
- **Note:** CodeBuddy is **not** WorkBuddy (`~/.codebuddy/…`, not `~/.workbuddy/…`).
- Docs: https://www.codebuddy.ai/docs/cli/skills

### Grok Bot (supported, manual setup required)

- **Entry:** private skills inside **Grok Bot** cloud chat. This covers the Grok Bot product only; **it does not mean other Grok clients or products can install skills the same way.**
- **Prepare:** a working Grok Bot account that can save private skills.
- **Load:** there is **no** one-click install and no "Connect apps" listing. Open one skill's `SKILL.md`, paste it into a chat and ask Grok Bot to **save it as a private skill** (use `name` / `description` from the file header), then confirm it appears in your private skills. Repeat for each skill you need; when saving `dispatch-accept-verify`, paste `templates/登记行模板.md` in too.
- **Call:** by skill name in chat.
- **You get:** inspectable output from the main example (e.g. a "pending" register line).
- **Do not mix up:** this is not Cursor's `~/.cursor/skills/` and not a local `~/.grok/skills` folder install path.
- **Host / human:** loading a skill does not make the whole workflow run by itself. Scheduled checks, cross-assistant messages, wake-ups, group chats, and shared files come from Grok Bot's own features, **not** from this pack. The method was first worked out in day-to-day use on Grok Bot; this pack is the reusable part of it.

### Kimi Work (supported)

- **Product:** **Kimi Work** (desktop). **Not** Kimi Code CLI (a separate coding tool with a different setup).
- **Target** (verified on macOS desktop): `~/Library/Application Support/kimi-desktop/daimon-share/daimon/skills/<skill-name>/` (short form: `daimon-share/daimon/skills/`). This is a community-known path. Kimi also documents uploading `.zip` / `.md`, installing from a link, or from its store — follow the official page on the day.
- **Prepare:** Kimi Work desktop installed and signed in.
- **Load:** copy the whole skill folder into that path, or use the official upload / store route.
- **Call:** pick the skill with `/` in the Kimi Work app. In our verification, the call was made **by a person pasting a prompt in the app**, not by another tool clicking for them.
- **You get:** inspectable output from the main example.
- Docs: https://www.kimi.com/features/skills

### QwenWork / 千问办公 (supported)

- **Product:** QwenWork (千问办公, desktop). **Not** Tongyi Lingma (a separate IDE assistant with different folders).
- **Target:** `~/.qwenworkcn/skills/<skill-name>/` (one folder per skill, each with a `SKILL.md`).
- **Prepare:** QwenWork desktop installed and signed in.
- **Load:** copy the whole skill folder into that path.
- **Call:** pick the skill with `/`, or name it in chat. In our verification, the call was made **by a person pasting a prompt in the app and approving file writes**, not by another tool clicking for them.
- **You get:** inspectable output from the main example.
- Docs: https://docs.qwenwork.cn/features/skills

### Claude Code (structure ready, not yet verified)

- Structure: [`.claude-plugin/plugin.json`](.claude-plugin/plugin.json) and [`.claude-plugin/marketplace.json`](.claude-plugin/marketplace.json) (plugin name `solo-to-team-skills`). Install commands: see the [official Claude Code plugin docs](https://code.claude.com/docs/en/plugins/install).
- **Not listed as supported.** It will be verified when conditions allow; until a full get → install → call → inspectable-output run succeeds, it is **not** part of launch support. You may try it; this page does not guarantee the result.

## Limits

- "Supported" covers only the install and call path written for that host.
- Copying a `SKILL.md` into some other tool's skill folder does not mean the pack has been verified there.
- `hooks: {}` = no automatic wake-ups. Nothing here dispatches, wakes, or sends receipts on its own.
- **Owner does dangerous actions:** spending money, sending, deleting, signing in, and payment confirmation are written as "owner does this"; the skills do not do them for you. The final accept / reject stays with a human.
- **Not yet proven:** the two cases show how the method changed and what that brought. There is no controlled comparison yet, so a lower team error rate or fewer reminders from the lead is **not** proven (see "Verification notes" in `ops-case-notes`).
- Pack usage and repository star counts are not claimed here (none measured yet). Initiator reach figures appear under Background; follower counts are not pack user counts.
- Method-level cases: see [`skills/ops-case-notes/`](skills/ops-case-notes/). Competitive "market blank" claims stay **TBD** until there is evidence; this page does not invent them.

## Skills in this pack

| Directory | Display name | Flow stage | Origin | Status |
|---|---|---|---|---|
| [`dispatch-accept-verify`](skills/dispatch-accept-verify/) | Collect the work you hand out | Hand-off | Adapted (closed-loop communication ideas from public discussion, plus one section of obra/superpowers; see the skill's attribution note) | Redacted method text ready |
| [`evidence-before-done`](skills/evidence-before-done/) | Evidence before calling it done | Verify | Adapted from obra/superpowers (MIT; see the skill's source and license section) | Redacted method text ready |
| [`beginner-ops-writing`](skills/beginner-ops-writing/) | Steps for newcomers | Owner-facing steps | **Original**: drawn from writing principles this team has long used; examples are fictional (see the skill's source note) | Writing guide + **two fictional examples**, ready to follow |
| [`ops-case-notes`](skills/ops-case-notes/) | Redacted operations notes | Real detours | **Original**: this team's own real operations, redacted (see the note at the top of the skill) | Redacted body (**two cases**), readable and usable as a model for writing your own notes |

Template: [`templates/task-register-line.md`](templates/task-register-line.md) — task hand-off records, ready to copy.

**What counts as working.** The first release is checked against two hard bars, and both must pass:

1. **Install and call:** on a host, get the pack → install or configure → call a skill by name and produce a register line. All eight supported setups have a run on record for this bar.
2. **Finish a real small task:** follow the [main example](#main-example-hand-out-collect-verify-then-decide) from goal to decision, with a real output, evidence, and an acceptance decision. For this bar: **on the current pack version, each of the eight setups has one acceptance record for a limited task** (real output → check against the request → human acceptance): the earlier separate Codex run is retained, and the other seven were tested on the same meeting-notes task. Some hosts needed another attempt after a blocked run or a revision before acceptance. This does not show stability or that every kind of task will succeed. How the host was invoked differs by host (some runs were sent by the user inside the host, some from a CLI or with assisted clicks), and some hosts kept no raw trace of skill loading. This does not mean all four skills were called on every host, and it does not prove effectiveness. The walkthrough itself is a teaching sample written by the authors, not a test record.

The general method needs only a shared record and someone who checks it on time: log a line, check when due, record taken / result received / accepted separately, get valid evidence for the current version before calling it done, and start the next step once approved. Use host automation where available; otherwise use manual or conversation steps. See the notes on how to describe host dependencies in [`ops-case-notes`](skills/ops-case-notes/).

`hooks: {}` means **no automatic wake-ups**. This pack does not provide or imply automated dispatch, wake-ups, or receipts.

## Results so far

**Known so far:** the method ran for a little over two weeks on the team's daily production chain, with 3 weekly reviews; the changes it produced (logging hand-in and receipt separately, kicking off the next step right after approval, independent review of source material before hand-off) are written into the skills. All eight supported setups were verified to install, be called by name, and produce a register line.

**Not yet proven:** whether team error rates or reminders from the lead went down (no controlled comparison), and stability or success on every kind of task — each of the eight setups has one acceptance record for a limited task, which does not show stability or that every kind of task will succeed.

No invented repository star counts or pack-user totals. Initiator reach figures are under Background. For method-level cases — problems, changes, results, and limits still unresolved — see [`ops-case-notes`](skills/ops-case-notes/).

## Background: a writer's first eighteen days with AI, and the start of "a team of one"

The pack was initiated by **Dabing (大冰)**. He is a writer; in this project he is also the explorer.

After about two and a half years of high-intensity live streaming, he chose to rest by learning. During the stretch when he first worked with AI, he turned **47**. He hopes to explore a path — for people starting from zero the way he is — to organize AI collaboration, learning, and growth. That path is not limited to "middle-aged people" or "beginners": anyone willing to feel their way from zero can use it. What he brings is years of writing, leading work, and talking with people for the long haul: saying clearly what needs doing, dividing the work, and checking that it is really done. That experience is the foundation of this attempt. "Starting from zero" means his starting point with AI and programming; it does not erase what he already knows how to do.

The pack grew out of a writer's first eighteen days with AI (as of 2026-11-06). Those eighteen days are the starting stage, **not** how long the whole pack took to build: the method took shape in that period, and the first release's rewriting, case notes, and multi-host verification were built on it. It will keep being refined before the public launch and developed after it.

In that period, one person working with several long-lived AI assistants kept hitting the same problems — not "the AI isn't smart enough", but: handed-off work that nobody collected, "done" that was never checked, steps only the author could follow, and the same mistake made twice. This pack collects the real fixes, including the parts that are still not fixed (see `ops-case-notes`).

- **Experimental:** still evolving, but what is released should work — install, call, and finish a small task.
- **Verification:** verified in actual use across multiple agent tools; the exact scope is the host table above.
- **Personal growth:** the initiator gained from this and hopes others might too. That is a hope, not a promised outcome.
- The "eighteen days" are a dated stage of experience. They are not part of the project name or the skill bodies. Skill text uses role words such as owner / coordinator / requester / worker.

### Supplement: public reach figures for the initiator (approximations / lower bounds)

These figures describe the initiator's own public reach. They are **not pack user counts**. Follower counts are listed **per platform** and **must not be added up as a de-duplicated audience**. How many people use this pack is not measured yet.

- **Live co-streaming hours:** more than 2,800 hours (not precise to the single hour; as of 2026-11-06)
- **Co-stream guest appearances:** more than 10,000 (counted per appearance, not de-duplicated to unique people; not an exact count; as of 2026-11-06)
- **Douyin follower count:** about 12.7 million (account YANBING1023; as of 2026-11-06)
- **Kuaishou follower count:** 9.118 million (as of 2026-11-06)
- **WeChat Channels follower count:** 3.25 million (account name "大冰"; as of 2026-11-06)
- **Bilibili clip cumulative play count:** about 700 million (**plays, not unique viewers**; lower bound from an internal sample: cumulative snapshot sum of about 7,906 clips / about 1,004 accounts, not a full-platform census; sample crawled 2026-10-18; the initiator has no personal Bilibili account)


## License and boundaries

- License: MIT — see [`LICENSE`](LICENSE).
- Notices: [`NOTICE`](NOTICE) (initiator: Dabing / 大冰; includes the full MIT license text for obra/superpowers).
- Public boundaries (summary): the pack delivers a method you can follow, templates, and redacted cases; credentials, real private contact details, internal paths, and machine details are never included; third-party attribution stays in [`NOTICE`](NOTICE) and each skill's source section. Formal public launch still follows the original approval process.
