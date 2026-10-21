# Kevin's personal skills

Private, reviewed snapshots of the skills I keep on my Mac, plus `own-the-logic` for deliberately writing the important logic myself. Personal installation does not imply personal authorship: upstream work is attributed below.

## Use own-the-logic

```text
Use $own-the-logic to help me build a dependency-aware task runner.
Interview me first, then scaffold it and reserve the important logic for me.
```

The workflow uses `grill-with-docs` to settle and document requirements, then reserves normally two or three meaningful clusters. It supplies contracts, callers, scaffolding, and tests while leaving the selected logic unimplemented. Later review preserves those reservations unless I explicitly transfer implementation.

## Inventory

| Skill | Authorship / source | Personal installation |
| --- | --- | --- |
| `own-the-logic` | Created for Kevin Bailey | `~/.agents/skills/own-the-logic` |
| `grill-with-docs` | [Matt Pocock's skills](https://github.com/mattpocock/skills), MIT | `~/.agents/skills/grill-with-docs` |
| `diagnose` | Matt Pocock's skills, MIT | `~/.agents/skills/diagnose` |
| `improve-codebase-architecture` | Matt Pocock's skills, MIT | `~/.agents/skills/improve-codebase-architecture` |
| `setup-matt-pocock-skills` | Matt Pocock's skills, MIT | `~/.agents/skills/setup-matt-pocock-skills` |
| `to-prd` | Matt Pocock's skills, MIT | `~/.agents/skills/to-prd` |
| `to-issues` | Matt Pocock's skills, MIT | `~/.agents/skills/to-issues` |
| `find-skills` | [Vercel Labs' skills](https://github.com/vercel-labs/skills), MIT | `~/.agents/skills/find-skills` |
| `anatomy` | [Ryan's Anatomy](https://github.com/wheresryan22/anatomy), MIT | `~/.agents/skills/anatomy` |

These are installed snapshots, not automatic upgrades to current upstream. `inventory.json` records the local installer hashes, reviewed upstream commits/licenses, and files that differ from current upstream. Differences are reported without claiming they are local customizations. Original files remain byte-for-byte intact; upstream license texts were added to the repository copies where absent. No blanket repository license overrides third-party terms. See [THIRD_PARTY.md](THIRD_PARTY.md).

Excluded: `hatch-pet` pending confirmation of its undocumented source/ownership; bundled `.system` skills; plugin/cache and app-synced skills; duplicate Claude installations and symlinks; company/project skill trees; configuration, installer state, credentials, session history, and unrelated files. Company skill contents are not copied. No existing installations were replaced or relinked.

## Install and sync

Codex discovers personal skills under `~/.agents/skills` ([official documentation](https://learn.chatgpt.com/docs/build-skills#where-codex-loads-local-skills)). Install `own-the-logic` and its `grill-with-docs` dependency together, preserving each whole directory. On Kevin's Mac both are already installed.

From this checkout, this example installs a missing skill and refuses to overwrite anything:

```bash
python3 - <<'PY'
from pathlib import Path
import shutil
source = Path('skills/own-the-logic')
target = Path.home() / '.agents/skills/own-the-logic'
shutil.copytree(source, target)  # Fails if target already exists.
PY
```

Use the same approach for a missing `grill-with-docs`, or another whole skill folder. Keep original licenses with each copy. A new Codex session should discover it; restart Codex if it does not appear. No configuration or security changes are needed.

The current sync direction is **installed personal folders → reviewed repository copies → private GitHub**. The repository is a versioned snapshot, not a live mirror. For future edits, choose one working copy, compare it with the other, review the diff for private content and licensing, then explicitly copy the intended changes. To restore from GitHub, pull into this checkout first, compare with the installed skill, and back up the installation before an explicit update. Do not bulk-copy your home directory, automatically overwrite installations, delete missing files, or replace originals with symlinks.

The disposable behavioral evaluation is documented in [validation/own-the-logic.md](validation/own-the-logic.md). Its intentionally incomplete task-runner code is not part of this repository.
