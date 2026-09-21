# Deskilling Guard

**Use AI without quietly giving up your judgment.**

Deskilling Guard is a lightweight agent skill for preserving the parts of work that build expertise: framing a problem, forming a hypothesis, diagnosing a failure, and choosing between meaningful trade-offs. It does not try to slow every task down. It adds one small checkpoint only when the work is both cognitively important and consequential.

## What it does

- Asks for a brief prediction before revealing an answer when a decision or interpretation matters.
- On the first failure, lets the user diagnose before revealing the cause; subsequent failures are fixed directly.
- Uses challenger mode, focused verification, and occasional AI-off practice only when they help.
- Backs off immediately for urgency, incidents, deadlines, a stated hypothesis, or a request to move quickly.

The goal is not less AI. It is keeping the human capable of supervising AI well.

## Install

### OpenClaw

Copy this repository's `SKILL.md` into a skill directory named `deskilling-guard`.

```text
<your OpenClaw skills directory>/deskilling-guard/SKILL.md
```

Then run your normal skill discovery/check command and start a new conversation. The skill is designed to activate for requests about AI overreliance, learning by doing, diagnosing before fixing, or intentionally preserving judgment.

### Codex

Codex reads project and global guidance from `AGENTS.md`. Copy the contents of [`integrations/codex/AGENTS.md`](integrations/codex/AGENTS.md) into either:

- your global Codex instructions; or
- the `AGENTS.md` at the root of a specific project.

Use the global option if you want the behavior across projects; use the project option if you only want it for selected work.

## How it behaves

| Situation | Behavior |
| --- | --- |
| Important design, strategy, or interpretation | One concise prediction checkpoint |
| First error or failed test | Shows the symptom and asks for a diagnosis |
| Second failure in the same task | Fixes it directly |
| Boilerplate, formatting, refactoring, repeated execution | Does not intervene |
| Incident, deadline, or “just do it quickly” | Does not intervene |
| User already shared a hypothesis | Does not ask again |

## User controls

- **“오늘은 빨리 가자” / “Let’s move fast today”** — disables checkpoints for the session.
- **“더 빡세게” / “Be stricter”** — requires a user prediction before substantive answers.
- **“이건 내가 잘 아는 영역” / “I know this area well”** — reduces scaffolding; keeps only challenge and focused verification.
- **“건너뛸게요” / “Skip it”** — immediately proceeds with no repeated prompt.

## Design principles

1. **Intervene sparingly.** Annoying friction gets disabled.
2. **Ask once, then compare.** A prediction without feedback is just a delay.
3. **Never turn urgency into a lesson.** Hotfixes and deadlines come first.
4. **Be concrete.** Point to the one or two risky things worth verifying rather than asking users to check everything.
5. **Do not moralize.** The skill should feel like a natural collaboration habit, not an educational lecture.

## Evidence and limits

The skill distinguishes between well-supported interventions (for example, predict-then-reveal and productive failure) and weaker analogies such as audit-style sampling. It deliberately avoids claiming that AI universally causes skill loss. See the **근거** section in [`SKILL.md`](SKILL.md) for the cited research and limits of each claim.

## Repository layout

```text
.
├── SKILL.md                    # Main skill for skill-based agents
└── integrations/codex/AGENTS.md # Codex-compatible instruction version
```

## Contributing

Issues and pull requests are welcome. Changes should preserve the core constraint: add friction only where it protects meaningful human judgment, and always provide a fast escape hatch.

## License

[MIT](LICENSE)
