---
name: godot-development
description: Godot GDScript development patterns, typing, nodes, signals, and lifecycle rules based on official docs.
allowed-tools: Read, Write, Edit, Glob, Grep
---

# Godot Development (GDScript)

## Overview
This skill provides GDScript-specific rules for writing correct, maintainable Godot code. It emphasizes script-as-class patterns, static typing, node lifecycle, and safe data handling to reduce runtime errors.

## When to Use This Skill
- Working in Godot with GDScript
- Writing or refactoring gameplay logic, UI, or systems in Godot
- Fixing type errors, lifecycle issues, or signal wiring
- Building reusable Godot scripts and resources

## Core Rules
### Script and Class Structure
- Every GDScript file is a class, attached to a node or used as a resource.
- Use `extends` to declare the base class.
- Use `class_name` only when you need a globally accessible type.
- Prefer composition with nodes and scripts over deep inheritance.

### Static Typing First
- Use typed variables and function signatures to catch errors early.
- Prefer type inference with `:=` when the type is obvious.
- Use typed arrays: `Array[Type]` and typed dictionaries: `Dictionary[KeyType, ValueType]`.
- When assigning filtered arrays to typed arrays, use `assign()` instead of casting.

### `:=` vs `=` (Variant Declarations)
- Use `:=` when the value type is stable for the variable's lifetime.
- Use `=` when the variable may change type or needs to stay dynamic.
- Prefer explicit Variant when dynamic typing is required: `var data: Variant = {}`.
- If you need to replace `:=` with `=`, keep the rest of the type rules consistent.

### Lifecycle and Execution
- Use `_ready()` for node initialization and scene tree access.
- Use `_physics_process(delta)` for physics logic and deterministic gameplay.
- Use `_process(delta)` for visual-only updates.
- Use `_input(event)` or `_unhandled_input(event)` for input handling.

### Nodes, Paths, and References
- Use `@onready` for node references that depend on the scene tree.
- Avoid combining `@onready` with `@export` on the same variable.
- Use `%NodeName` or `$NodePath` to get nodes when appropriate(prefer Nodename).
- Prefer typed node references for clarity and autocomplete.

### Signals and Events
- Declare signals with `signal`.
- Use `.connect()` for signal wiring and `emit()` for dispatching.
- Prefer explicit, typed signal parameters.

### Resources and Loading
- Use `preload()` for resources known at compile time.
- Use `load()` for dynamic runtime loading.
- Keep constants in `const` variables and ensure they are compile-time values.

### Safety and Comparisons
- Use `is_instance_valid()` when checking nodes or objects that may have been freed.
- For floats, prefer `is_equal_approx()` or `is_zero_approx()`.
- Be aware that integer division is truncating; cast to float when needed.

## Common Pitfalls
- Mixing `@export` and `@onready` on the same property causes initialization issues.
- Assigning an untyped array directly to a typed array without `assign()`.
- `Object.get("prop")` is not `Dictionary.get("key", default)`:
  - `Object.get()` (used on Resources/Nodes) accepts only one argument and returns `null` if missing.
  - `Dictionary.get(key, default)` accepts a default value and is safe for optional keys.
- If you want a default value when reading from an Object (Resource/Node), wrap it:
  - Use a small helper like `_obj_get_or(obj, "prop", default)` that calls `obj.get("prop")` and falls back when it returns `null`.
- If Godot cannot infer a variable type in typed code, annotate it explicitly:
  - Prefer `var x := some_typed_expression()` when possible.
  - Otherwise use `var x: Vector2i = ...` / `var x: Dictionary = ...` to avoid “Cannot infer type” parser errors.
- In expressions that mix ints with `max()/min()/clamp()` or bit shifts, inference can fail; prefer explicit `: int` annotations.
- If a value comes from `Variant` (Object.get / Dictionary data / RPC payloads), Godot may treat inference as `Variant` and some projects treat that warning as an error. Prefer explicit annotations like `var delay_ms: int = int(v)` and `var color: Color = v`.
- Typed arrays are strict: don’t assign/cast `Array` into `Array[T]`.
  - Prefer `var tiles: Array[Vector2i] = []` and append only `Vector2i` items (manual copy), instead of `tiles_v as Array[Vector2i]`.
- Treating integer division as floating division.

## Sources
- https://docs.godotengine.org/en/stable/tutorials/scripting/gdscript/gdscript_basics.html
- https://school.gdquest.com/cheatsheets/gdscript
