# yeehaw

A Claude Code skill that sets a high bar for plans. A plan's first word is `YEEHAW` (earned), `DONE` (everything open is resolved, not yet great) or nothing (in progress).

To earn YEEHAW, a plan is grilled with questions until nothing is vague, checked against the real system, debated by red and blue sub agent teams staffed with experts for the plan's topic (each team runs its own internal debate with multiple personas), then rechecked in passes until one finds nothing.

## Install

Copy the `yeehaw` folder into your Claude Code skills directory:

- macOS / Linux: `~/.claude/skills/yeehaw/`
- Windows: `C:\Users\<you>\.claude\skills\yeehaw\`

```bash
git clone <this repo url>
cp -r yeehaw-skill/yeehaw ~/.claude/skills/
```

## Use

Say "YEEHAW", "bring it to YEEHAW" or "run yeehaw" about a plan. It is meant for big plans (new systems, deals, migrations, anything where a wrong plan is expensive), not small task lists.

## Make it yours

Define your own nine quality checks (step 6) and your project's structure rules (step 4) once, then the skill reuses them.
