# dotfiles-colors

Desired state for the current Ubuntu machine's home configuration, using the
[`getcolors/dotfiles`](https://github.com/getcolors/dotfiles) green Package
Skill. The installed package also carries a macOS profile, but this deployment
selects Ubuntu.

```sh
./green build
./green diff
./green create --dry-run
COLORS_PAR_DOTFILES_PREVENT_OVERWRITE=false ./green create
```

Build output is generated under `.colors/dotfiles-colors/dotfiles/`. Diff
renders first and prints safe, color unified differences against `$HOME` while
redacting target-only contents. A real create writes the managed files into
`$HOME` and verifies every copy. Delete is
unsupported and unrelated home files are never removed. No credentials are
required; `.envrc.private` remains available for future private parameters.

The root `green` launcher is a copy of
`.agents/skills/package-dotfiles-green/green`. After `npx skills update -p -y`,
copy the payload again before committing.
