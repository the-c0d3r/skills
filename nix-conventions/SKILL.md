---
name: nix-conventions
description: Use when writing or editing .nix files, or working on NixOS configuration.
---

Always run `nix eval` after editing any .nix file to catch parse/eval
errors early, before moving on to the next change. If new .nix files
were added, `git add` them first — nix flakes only see tracked files.

Config that is written at runtime must be a live out-of-store symlink
(`config.lib.file.mkOutOfStoreSymlink`), not a store path or
`builtins.readFile`.

NixOS writes SSH authorized keys to `/etc/ssh/authorized_keys.d/<user>`,
not `~/.ssh/authorized_keys`.
