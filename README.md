# Deskilling Guard

**Use AI without quietly giving up your judgment.**

[한국어](#deskilling-guard-한국어) · [English](#deskilling-guard)

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

---

# Deskilling Guard (한국어)

**AI를 쓰되, 내 판단력을 조용히 넘겨주지는 않도록.**

Deskilling Guard는 전문성을 만드는 핵심 과정—문제 정의, 가설 수립, 실패 진단, 중요한 트레이드오프 선택—을 사용자가 직접 통과하도록 돕는 가벼운 에이전트 스킬이야. 모든 일을 느리게 만들지 않고, 인지적으로 중요하면서 결과가 무거운 작업에만 짧은 체크포인트를 둔다.

## 하는 일

- 결정이나 해석이 중요한 경우, 답을 공개하기 전에 짧은 예측을 먼저 받는다.
- 첫 에러·실패에서는 원인을 바로 말하지 않고 사용자가 먼저 진단해 보게 한다. 같은 작업의 두 번째 실패부터는 바로 고친다.
- 도전자 모드, 핵심 지점 표본 검증, 가끔의 AI-off 연습은 도움이 될 때만 쓴다.
- 긴급 상황, 장애 대응, 마감 압박, 이미 제시된 가설, 빠르게 처리해 달라는 요청에서는 즉시 물러난다.

목표는 AI를 덜 쓰는 게 아니다. 사람이 AI를 제대로 감독할 수 있는 판단 능력을 지키는 것이다.

## 설치

### OpenClaw

이 저장소의 `SKILL.md`를 `deskilling-guard`라는 이름의 스킬 디렉터리에 복사한다.

```text
<OpenClaw 스킬 디렉터리>/deskilling-guard/SKILL.md
```

그다음 평소 사용하는 스킬 탐색·검증 명령을 실행하고 새 대화를 시작하면 된다. AI 의존, 스스로 생각하며 학습하기, 고치기 전 진단하기, 판단력 보존과 관련된 요청에서 동작하도록 설계되어 있다.

### Codex

Codex는 전역 또는 프로젝트의 `AGENTS.md` 지침을 읽는다. [`integrations/codex/AGENTS.md`](integrations/codex/AGENTS.md) 내용을 다음 중 한 곳에 넣으면 된다.

- 전역 Codex 지침: 모든 프로젝트에 적용
- 특정 프로젝트 루트의 `AGENTS.md`: 그 프로젝트에만 적용

## 동작 방식

| 상황 | 동작 |
| --- | --- |
| 중요한 설계·전략·해석 | 짧은 예측 체크포인트 1회 |
| 첫 에러 또는 테스트 실패 | 증상을 보여주고 진단을 묻는다 |
| 같은 작업의 두 번째 실패 | 바로 수정한다 |
| 보일러플레이트·포맷팅·리팩터링·반복 실행 | 개입하지 않는다 |
| 장애·마감·“빨리 그냥 해줘” | 개입하지 않는다 |
| 사용자가 이미 가설을 말했다 | 다시 묻지 않는다 |

## 사용자 제어 문구

- **“오늘은 빨리 가자” / “Let’s move fast today”** — 그 세션의 체크포인트를 끈다.
- **“더 빡세게” / “Be stricter”** — 중요한 답을 주기 전에 사용자 예측을 받는다.
- **“이건 내가 잘 아는 영역” / “I know this area well”** — 스캐폴딩을 줄이고 도전자 모드와 표본 검증만 유지한다.
- **“건너뛸게요” / “Skip it”** — 즉시 진행하며 다시 권하지 않는다.

## 설계 원칙

1. **개입은 아껴서 한다.** 성가신 마찰은 결국 꺼진다.
2. **한 번 묻고, 반드시 대조한다.** 피드백 없는 예측은 지연일 뿐이다.
3. **긴급함을 학습 기회로 바꾸지 않는다.** 핫픽스와 마감이 우선이다.
4. **구체적으로 말한다.** 전부 보라고 하지 않고 위험한 한두 곳만 짚는다.
5. **훈계하지 않는다.** 이 스킬은 교육용 강의가 아니라 자연스러운 협업 습관이어야 한다.

## 근거와 한계

이 스킬은 예측 후 공개나 생산적 실패처럼 근거가 비교적 탄탄한 개입과, 감사 표본 검증처럼 비유·응용 성격이 강한 개입을 구분한다. AI가 보편적으로 능력을 떨어뜨린다고 단정하지 않는다. 인용한 연구와 각 주장에 대한 한계는 [`SKILL.md`](SKILL.md)의 **근거** 섹션에서 확인할 수 있다.

## 저장소 구성

```text
.
├── SKILL.md                    # 스킬 기반 에이전트용 본문
└── integrations/codex/AGENTS.md # Codex 적용용 지침 버전
```

## 기여

Issue와 Pull Request를 환영한다. 다만 핵심 원칙은 지켜야 한다. 의미 있는 인간의 판단을 보호할 때만 마찰을 만들고, 사용자가 원하면 언제든 빠르게 건너뛸 수 있어야 한다.

## 라이선스

[MIT](LICENSE)
