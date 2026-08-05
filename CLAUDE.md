# CLAUDE.md

## What this repository is

Desired state for applying `getcolors/dotfiles` to the current Ubuntu machine.
`colors.yml` is source; `.colors/` is generated and must never be edited or
committed. Credential-bearing source dotfiles are excluded by the package.

The root `green` launcher is a copy of
`.agents/skills/package-dotfiles-green/green`, installed from
`getcolors/dotfiles` and recorded in `skills-lock.json`. `.claude` and `.pi`
discovery paths symlink to the canonical `.agents` payload. After
`npx skills update -p -y`, synchronize the root launcher copy.

## Commands

```sh
./green build
./green diff
./green create --dry-run
COLORS_PAR_DOTFILES_PREVENT_OVERWRITE=false ./green create
```

Diff is read-only: it renders first, reports drift without failing, and redacts
target-only contents. A real create overwrites the package's managed files in
`$HOME` and requires explicit authorization plus the one-run environment
override above. Keep the
committed guard true. `delete` is unsupported.

Never export `COLORS_PAR_PROFILE`. No credentials are currently required. If
future private parameters are introduced, they belong only in the ignored
`.envrc.private`.

## Verification

After create, build again and compare each generated managed file with the
corresponding file under `$HOME`; `.local/bin/dev` must remain executable.

## Git

Do not commit or push unless explicitly asked.
