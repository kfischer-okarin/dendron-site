---
id: xI97d5GKk7qU6EwstIAXe
title: Note CLI
desc: ''
updated: 1654386983784
created: 1635113127689
---

## Synopsis

```bash
dendron note <cmd>

note related commands

Positionals:
  cmd  a command to run        [string] [required] [choices: "lookup", "delete", "move"]

Options:
  --version         Show version number                                [boolean]
  --help            Show help                                          [boolean]
  --wsRoot          location of workspace
  --vault           name of vault
  --quiet           don't print output to stdout
  --enginePort      If set, connect to to running engine. If not set, create new
                    instance of Dendron Engine
  --attach          Use existing engine instead of spawning a new one
  --useLocalEngine  If set, use in memory engine instead of connecting to a
                    server                                             [boolean]
  --query           the query to run                                    [string]
  --output          format to output in
              [string] [choices: "json", "md_gfm", "md_dendron"] [default: "json"]
  --destFname       name to change to (for move)                        [string]
  --destVaultName   vault to move to (for move)                         [string]

```

## Methods

### lookup

Options

- for common options, see [[common options|dendron.topic.cli.quickstart#common-options]]
- `--output`: controls how note is formatted
    - values: `json|md_gfm|md_dendron`
        - json: JSON output
        - md_dendron: dendron markdown
        - md_gfm: github flavored markdown 

Examples

#### creating a note

```bash
# creates hello if it does not exist
dendron note lookup --query "hello" 
```

#### Querying a note

```bash
# retrieves hello.md if it does exist
dendron note lookup --query "hello" 
```

#### Querying a note with GitHub Flavored Markdown output

```bash
# retrieves hello.md if it does exist
dendron note lookup --query "hello" --output md_gfm
```

### delete

Examples

#### Deleting a note
```bash
dendron note delete --query "foo" 
```

#### Deleting a note within a multi-vault workspace
```bash
dendron note delete --vault vault2 --query "foo" 
```

### move

Examples

#### Moving a note
```bash
# renames the note "foo" to "bar" within a single-vault workspace
#   if there is no note in the vault already named "bar"
dendron note move --query "foo" --destFname "bar"
```

#### Moving a note in a multi-vault workspace
```bash
# moves the note "foo" to vault2 and changes its name to "bar"
#    if there is no note in vault2 already named "bar"
dendron note move --vault vault --query "foo" --destFname "bar" --destVaultName vault2
```
