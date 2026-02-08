---
alwaysApply: true
keywords: ["godot", "client", "server"]
---

# Godot Client/Server Mirror Rule

Use this rule for Godot projects that split client and server into separate folders.

## Addons/Resources Mirrors

- Treat `client/addons` as a mirror of `server/addons` via symlink/junction.
- Treat `client/resources` as a mirror of `server/resources` via symlink/junction.
- Treat `client/domain` as a mirror of `server/domain` via symlink/junction.
- Do not modify any file under `addons/` unless explicitly requested.
- Do not modify files under `client/resources`; update `server/resources` instead.
- Do not modify files under `client/domain`; update `server/domain` instead.

## Intent

- Keep third‑party addons consistent across client and server.
- Ensure resource edits are centralized in the server project.
