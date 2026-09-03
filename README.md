# Heavenrend — UE5 Gameplay Combat Portfolio

> Work-in-progress UE5 C++ gameplay project focused on combat architecture and enemy AI.

## Highlights

- C++ component-based combat architecture
- Combat states: locomotion, attack, dodge, parry, iaido counter, hitstun, dead
- Event-driven HUD with health, sword-heart resource, and dodge recharge
- StateTree enemy AI foundation
- Enemy target evaluator with detection / lose-target hysteresis
- NavMesh-based chase flow and attack-range stop

## Current Status

### Completed

- C3 Combat HUD
- C4-1 enemy base character and AI controller
- C4-2 StateTree target evaluator and chase flow

### In Progress

- C4-3 enemy attack component and StateTree attack task

## Technical Focus

This project is being built as a gameplay programmer portfolio. The emphasis is not on final art quality, but on verifiable implementation:

- deterministic combat flow
- safe state transitions
- clear component responsibility
- minimal Blueprint logic
- reproducible test criteria

## Notes

The public repository should contain source code, documentation, screenshots, and short gameplay clips only. Full project assets should remain in the private repository unless licensing is verified.
