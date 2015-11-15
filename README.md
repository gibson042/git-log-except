# git-log-except
Show git commits not matching provided filters, honoring all `git log` options.

## Installation
Copy `git-log-except` to a directory in your `$PATH` (e.g., `~/bin/`).

## Usage
```sh
git log-except <command> |
       [[--]verbose] [<exclusion options>] [-- <output options>] [<commit range>] [[--] <path>...]

Commands:
   [--]help     Display this message
   [--]version  Show software version
```

## Examples
### Commits not by a particular author
```sh
git log-except --author=gibson -- --oneline
```

### Nonbreaking changes on a branch
```sh
git log-except -i --grep='semver[:[:space:]]*major' compat
```

### The most recent nonbreaking change on a branch
```sh
git log-except -i --grep='semver[:[:space:]]*major' compat -- -1 --patch
```

### Source changes that will survive an `--autosquash` rebase
```sh
git log-except --grep='^squash! ' --grep='^fixup! ' -- --patch master..HEAD src/
```
