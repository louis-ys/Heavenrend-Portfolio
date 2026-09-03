# Heavenrend Progress Log — C3 to C4

## C3 — Combat HUD

Completed event-driven combat HUD.

### Implemented

- `WBP_HealthHUD`
- `WBP_SwordHeartHUD`
- `WBP_DodgeHUD`
- `WBP_CombatHUD`
- PlayerController-owned HUD creation
- BlueprintImplementableEvent-based UI updates

### Confirmed

- Health display updates
- SwordHeart display updates
- Amplify-ready visibility
- Dodge charge and recharge display
- No Widget Tick / no property binding

## C4-1 — Enemy Base

### Implemented

- `AHREnemyCharacter`
- `AHREnemyAIController`
- `BP_JeongpaSwordsman`
- `BP_JeongpaAIController`

### Confirmed

- AIController possess
- hitstun from normal attack
- iaido damage
- dead state
- C3 HUD regression pass

## C4-2 — StateTree Chase

### Implemented

- `FHREnemyTargetEvaluator`
- `FHRStateTreeHoldTask`
- `ST_JeongpaEnemy`
- Idle / Chase / Attack state shell
- Move To chase using TargetActor
- Acceptable Radius bound to AttackRange
- Track Moving Goal enabled

### Confirmed

- Enemy detects player
- Enemy chases player
- Enemy stops near attack range
- C4-2 attack state is currently a hold state, not a real attack

### Notes

- `AttackRange = 200` means roughly 2 meters in Unreal units, not 200 meters.
- `LoseTargetRange = 1600` means roughly 16 meters, so a single dodge may not drop target.
- Dragging/sliding movement without walk animation is likely an AnimBP issue, not a C4-2 movement failure.
