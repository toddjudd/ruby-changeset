# README

## Rake Tasks

```bash
bundle exec rake "release:version[2.1.0]"
```

sets the version in the `.version` file to `2.1.0`. Make sure to use semantic
versioning (x.y.z) when specifying the version.

```bash
bundle exec rake release:publish
```

creates a git tag with the version from the `.version` file and pushes it to the
remote repository.

```bash
bundle exec rake changeset
```

launches the changeset CLI to create a new changeset. - see Changesets section
below.

## Changesets

install @changesets/cli

```bash
pnpm i @changesets/cli
```

create a changeset

```bash
pnpm changeset
```
