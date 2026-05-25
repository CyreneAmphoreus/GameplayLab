# GameplayLab

GameplayLab is a long-term Unity Gameplay / client development practice project.

This repository is used to grow a small player-controller sandbox into a more complete gameplay engineering lab. The focus is not only finishing isolated exercises, but building the habits behind real Unity client work: input handling, controller structure, physics decisions, camera behavior, gameplay state, animation parameters, UI feedback, and small reusable systems.

## 当前目标

Build a Unity Gameplay / client development growth path step by step.

The current stage is focused on player control fundamentals:

- Understand the difference between Transform-driven movement and physics/controller-driven movement.
- Use Unity Input System with clear gameplay action names and callback flow.
- Build a player controller that can gradually evolve instead of becoming a single messy script.
- Record each practice step, common mistakes, and reusable gameplay notes.

## 当前已完成

The project has completed the first player-control foundation stage:

- WASD movement with `Input.GetKey` and `transform.Translate`
- Q/E rotation with `transform.Rotate`
- Unity Input System setup
- `InputAction.CallbackContext` input callbacks
- Movement input cached as `Vector2`
- Mouse Delta look control
- Character yaw and camera pitch separation
- Camera pitch clamp
- Cursor lock for FPS-style control
- Shift sprint with `performed` / `canceled`
- `isRunning` state-based sprint logic

The main practice script for this stage is:

- `Assets/Scripts/Lesson01.cs`

## 后续计划

Next stages will move from basic input and Transform control into more production-like gameplay systems:

- Rigidbody jump
- Grounded detection
- CharacterController movement
- Camera follow
- Animator parameters
- FSM state machine
- Interaction system
- Simple skill system
- UI health / stamina bars
- Simple enemy AI

The immediate next stage is Rigidbody jump, followed by grounded detection and CharacterController comparison.

## 使用技术

- Unity
- C#
- Unity Input System
- Input Actions
- `InputAction.CallbackContext`
- Transform movement and rotation
- Camera pitch clamp
- Rigidbody and CharacterController planned for upcoming stages

## 项目结构

- `Assets/`
  Unity assets, scenes, materials, input actions, and gameplay scripts.
- `Assets/Scripts/`
  Practice scripts and generated Input System C# wrapper code.
- `Docs/`
  Long-term learning records, common mistake tracking, and reusable gameplay notes.
- `Docs/LearningProgress.md`
  Chronological progress log. Updated after code reviews and stage summaries.
- `Docs/CommonMistakes.md`
  Repeated issues and habits that need attention.
- `Docs/GameplayNotes.md`
  Stable gameplay/client patterns worth keeping for future work.
- `AGENTS.md`
  Project-specific coaching, documentation, and Git workflow rules.
- `Packages/`
  Unity package manifest and package lock.
- `ProjectSettings/`
  Unity project settings.

## 学习记录

Progress is tracked in:

- `Docs/LearningProgress.md`

Common recurring issues are tracked in:

- `Docs/CommonMistakes.md`

Reusable gameplay notes are tracked in:

- `Docs/GameplayNotes.md`

GameplayLab should keep growing as a real practice repository: each completed stage should leave behind code, notes, and a clearer direction for the next system.
