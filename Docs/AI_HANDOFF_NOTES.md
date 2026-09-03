# Heavenrend AI Handoff Notes

## Current Rule

Claude drafts larger C++ code changes. ChatGPT reviews, corrects, and gives Unreal Editor application steps.

## UI Naming Rule

Use the user's actual Unreal 5.7 Korean UI labels first. English/internal names are secondary.

Examples:

- Actual UI label: `리디렉터 레퍼런스 업데이트`
  - Functional meaning: Fix Up Redirectors / redirector reference update
- StateTree binding menu may show C++ variable names:
  - Evaluator panel may show `Has Target`
  - Binding menu may show `bHasTarget`
  - Correct actual binding: `HR Enemy Target → bHasTarget`

## Current Blueprint / StateTree Names

- `BP_JeongpaSwordsman`
- `BP_JeongpaAIController_New`
- `ST_JeongpaEnemy`

Current intended link:

```text
BP_JeongpaSwordsman
→ AI Controller Class = BP_JeongpaAIController_New

BP_JeongpaAIController_New
→ State Tree = ST_JeongpaEnemy
```

## C4-2 StateTree

```text
Root
├─ Idle
│  ├─ HR Hold
│  └─ On Tick → Chase
│     IF HR Enemy Target.bHasTarget = True
│
├─ Chase
│  ├─ Move To / 이동
│  │  TargetActor = HR Enemy Target.TargetActor
│  │  Acceptable Radius / 허용 가능 반경 = HR Enemy Target.AttackRange
│  │  Track Moving Goal / 움직이는 목표 트래킹 = true
│  ├─ On Tick → Idle
│  │  IF HR Enemy Target.bHasTarget = False
│  └─ On Tick → Attack
│     IF HR Enemy Target.DistanceToTarget <= HR Enemy Target.AttackRange
│
└─ Attack
   ├─ HR Hold
   ├─ On Tick → Idle
   │  IF HR Enemy Target.bHasTarget = False
   └─ On Tick → Chase
      IF HR Enemy Target.DistanceToTarget > HR Enemy Target.AttackRange
```

## Known C4-2 Observations

- Enemy follows the player.
- Movement animation may not play; looks like sliding. Treat as AnimBP follow-up, not C4-3 blocker.
- Dodging away may not break chase because `LoseTargetRange = 1600`.
- Do not slow enemy movement just to test C4-3.
