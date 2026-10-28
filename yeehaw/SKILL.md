---
name: yeehaw
description: A plan standard. Use only when the user says YEEHAW, "bring it to YEEHAW" or "run yeehaw", or asks to recheck a plan whose first word is YEEHAW or DONE. Not for small task plans, and not for builders reading a plan.
---
# YEEHAW

A plan's first word tells the reader its standing at a glance:

- **YEEHAW**: the plan earned it. Nothing is vague, every claim was checked against the real system, the plan survived a red/blue team debate and repeated recheck passes, and a final pass found nothing.
- **DONE**: everything open is resolved, but the plan is not yet great. Keep iterating toward YEEHAW if asked.
- **No word**: still in progress.

Never say YEEHAW freely. If anything is still vague, fix it first.

## What earning it means
- The user was grilled with clarifying questions until nothing was vague. The questions are 80% of the work.
- Research was updated as the answers came in.
- Every claim was checked against the real code or system, not against the audits that produced the claim.
- Design, and the one idea underneath it, was carried through every piece.
- The plan was rechecked repeatedly for errors, gaps, bugs and weak spots, and each pass fixed something.
- A confirmation pass ran before the word: every file:line handed to a builder opened and read, every "safe to delete" proven with an import map, every outside service step checked for a lockout trap, every number measured.
- A pass log in the plan records each pass, what it found, what changed. YEEHAW comes only after a final pass that finds nothing.
- A process proof: a plan that builds a new system or changes the main user path includes a working, moving view of the whole process (a simulator or prototype running on the real logic) with a written gate the user runs before any product build. No YEEHAW without it, or a stated reason it does not apply.
- A build map: every step from start to end, with what goes in, what comes out and its done check, in an order a cold reader can follow. A step starts only when the one before is checked.
- A break register: what might break, change or drift (in the build, production, data, other work lanes, outside services), each with its handling decided in advance and the step where it bites.

## The loop (go back whenever a later step finds something)
1. Grill: questions are 80%; at most 4 a round, your pick first; ask the basis before calling a claim wrong; never think for the user.
2. Research, updated as answers land; outside services from their own pages, dated.
3. Claims: compare the remote with the local checkout (`git ls-remote` against `origin/main`); read every file:line from `origin/main`; measure every number; prove every "safe to delete" with an import map; check every outside step for a lockout trap; check the primary checkout is current (its hooks run from there).
4. File homes: read the project's structure rules first (architecture doc, repo hygiene tests, agent instructions, file rules). Each output: home, rule, companions, links written from the linking file's folder; a plan that will live in the repo never writes a link pattern it cannot resolve. Stop only when a cold reader can follow the plan to every file.
5. Cards: one PR, one session; template with Tier, Merge path, Shell, Holes; decide vs do; every card written now with holes named; the next wave has no holes; prep fills holes and runs a cold read.
6. Quality gate Q1 to Q9 on every section and card, results written. (Define your own nine checks once, for example: goal stated, done check stated, inputs named, outputs named, file home named, twins found, risk tier set, holes named, cold reader could finish it.)
7. Debate, heavy: the red/blue team debate below. If Codex is reachable, also run it as an extra outside voice from Git Bash: `codex exec -C <repo> -m <model> --sandbox read-only -o <scratch>/debate.md "<order>" < /dev/null`. The sandbox stops writes, not reads, so the order says: read the agent instructions first; never open `.env*`, `secrets/` or credential files, or any file outside the repo except the plan; repo files only via `git show origin/main:<path>`; list wrong claims, missing file homes, cards a cold model would finish differently, cards over one session, unhandled breaks, order errors; cite lines; end with VERDICT. Always also a cold Sonnet read of the next wave. Every objection: a fix or a written answer.
8. Recheck passes until one finds nothing, each somewhere new: live site and API; production under a production guard (counts, never rows; test users minted and removed through the app's own deletion path; browser probes abort every non GET, proved by one blocked POST; no user content sent to an AI service; no script mails a list); other projects on the machine; tests as a twin finder (the same function defined twice); open PRs touching the same files; import chains of anything moved or bundled; hygiene guard budgets; the real shape of outside data; the Terms, privacy policy and legal docs read against the code; every cited line reprinted after edits; second and third order effects on users, data, other lanes and projects.
9. Confirmation pass, then the word.

## Red/blue team debate (step 7 engine)
Two sub agent teams argue the plan until it is better, not until someone gets tired. The main session is the only writer of the plan; teams are read only and send findings back.

**Seat the teams for the topic.** First read the plan and name its main topics (a software build, a deal or valuation, a legal or compliance move, a money or tax structure, a UX flow, an ops or people process, a data migration; most plans are two or three). Each team is staffed with experts for those topics, never generic critics. A schema change seats a database migration engineer, a production SRE, a privacy lawyer; an acquisition plan seats a deal lawyer, a quality of earnings accountant, a lender, a seller side advisor. Say the seats in the debate log.

**Blue team** defends and strengthens: finds the best form of each decision, the proof it holds, and the cheaper or safer path. **Red team** attacks: wrong claims, gaps, order errors, weak spots, second and third order effects, what a cold builder would finish differently, what breaks in production, what the other side of any deal would exploit. Each objection carries: the cited line, the basis (what makes it true, checked against the real system), severity (blocks, weakens, nit), and a proposed fix.

**Internal debates.** A team is not one voice. Each team agent runs its own debate first: it creates 3 to 5 named personas with different incentives (cautious, aggressive, cheapest path, longest horizon, the user's side, the counterparty's side), has them argue, and reports one position plus the dissent it did not settle. If it can spawn sub agents it does, in parallel; if not, it argues the personas itself. The report lists the personas and who dissented. Scale personas to the stakes: a one card change gets 3, a system or a deal gets 5.

**Rounds, until resolved.**
1. Spawn red and blue in parallel (Agent tool, general purpose, read only). Brief each with: plan path, topic seats, role, the date, and the secrets rule (never open `.env*`, `secrets/` or credential files; repo files only via `git show origin/main:<path>`).
2. Red files objections. Blue answers each: FIX (the main session edits the plan, prints the new lines), ANSWER (written, with evidence), or CONCEDE. Blue may also raise its own strengthenings.
3. Red rebuts the answers. Anything red still holds open goes another round, argued by the personas that dissented.
4. Each round must leave the plan measurably better: a fix applied, a claim proven, a hole named. A round that only polishes wording does not count as progress; stop and call it.
5. Resolved means: a full round where red finds nothing above nit, and every objection in the log is closed by a fix, an answer red accepted, or a concession. Red must show the angles it tried in that last round, so an empty round cannot be a rubber stamp.
6. Cap at 5 rounds. A deadlock, or any objection that is really the user's call (their money, their risk, their values, their goals), goes to the user as a question with both sides' best case, your pick first. Never settle it for them.
7. After resolution, run one fresh pair of agents with no history on the final plan, to catch what the long debate normalized.

**Debate log** (in the plan): seats per team; per round the objections, who raised them, and the outcome with line numbers; deadlocks and what the user decided; the final clean round. Codex, if reachable, stays an extra outside voice on top of the teams, never a replacement.

## Every YEEHAW plan carries
Context and the one idea; decisions; research; file homes; lanes, models, baton; cards; quality gate results; a process proof with a written gate (or why none); build map; break register; the user's part in minutes; out of scope; verification; debate log (red/blue seats, rounds, internal dissents, deadlocks the user decided); pass log.
