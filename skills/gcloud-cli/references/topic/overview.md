# gcloud topic — gcloud CLI Supplementary Help Guides

## Overview

`gcloud topic` is not a Google Cloud product — it is the gcloud CLI's built-in library of **supplementary help guides** that document cross-cutting CLI behaviors: output filtering, output formatting, projections, date/time input syntax, list/dict argument escaping, named configurations, `.gcloudignore` files, the `--flags-file` mechanism, and more. Each guide is printed directly in the terminal (`gcloud topic <name>`), works offline, and requires no API, project, or authentication. Reach for these guides when you need to know *how* to shape, filter, or escape arguments and output for any other gcloud command.

> These topics explain the machinery behind flags like `--filter`, `--format`, `--flatten`, and `--configuration` that nearly every other reference in this skill uses. The pattern is always **read the guide, then apply what it documents to a real command.**

## Quick reference — common workflows

### Filter resources (consult `filters`, then use `--filter`)
```bash
# Read the filter-expression guide (operators, AND/OR/NOT, : vs = vs ~)
gcloud topic filters

# Apply: list instances whose zone matches a regex AND that are not f1-micro
gcloud compute instances list \
    --filter="zone ~ us AND -machineType:f1-micro"

# Apply: list projects created within the last two weeks (ISO 8601 duration)
gcloud projects list \
    --format="table(projectNumber,projectId,createTime)" \
    --filter="createTime>-P2W"
```

### Shape output (consult `formats`, then use `--format`)
```bash
# Read the formats guide (table/json/yaml/csv/value/flattened + attributes)
gcloud topic formats

# Apply: a boxed, titled table with sorted and relabeled columns
gcloud compute instances list \
    --format="table[box,title=Instances](name:sort=1, zone:label=zone, status)"

# Apply: machine-readable value output (tab-separated, no heading)
gcloud info --format="value(config.account)"
```

### Project specific fields with transforms (consult `projections`, then use `--format`)
```bash
# Read the projections guide (key syntax, transform functions, column attributes)
gcloud topic projections

# Apply: table with a strftime-formatted creation timestamp in local time
gcloud compute instances list \
    --format="table(name, status, creationTimestamp.date(tz=LOCAL))"

# Apply: CSV of flattened global quotas
gcloud compute project-info describe --flatten="quotas[]" \
    --format="csv(quotas.metric,quotas.limit,quotas.usage)"
```

### Pass values containing commas (consult `escaping`, then use an alternate delimiter)
```bash
# Read the escaping guide (^DELIM^ syntax for list/dict flags)
gcloud topic escaping

# Apply: VM metadata whose values contain commas, using ':' as the delimiter
gcloud compute instances create example-instance1 \
    --metadata ^:^key1="value1":key2=value2:key3=value3Index1,value3Index2,valueIndex3:key4=value4
```
> On `cmd.exe` / PowerShell, `^` is a special character — repeat it (`^^^^`) as the escaping guide notes.

### Manage project profiles (consult `configurations`, then use `gcloud config`)
```bash
# Read the named-configurations guide
gcloud topic configurations

# Create and populate a dev profile
gcloud config configurations create my-config
gcloud config set project my-dev-project
gcloud config set compute/zone us-central1-a

# Switch active configuration, or override for a single command
gcloud config configurations activate my-config
gcloud compute instances list --configuration=my-config
```

### Specify complex flags portably (consult `flags-file`, then use `--flags-file`)
```bash
# Read the flags-file guide (YAML/JSON storage for any flag values)
gcloud topic flags-file

# Apply: load flags from a YAML file (right-most file wins on conflicts)
gcloud compute instances describe my-instance --flags-file=my-flags.yaml
```

## Command groups

`gcloud topic` has no subgroups — it is a flat set of 18 GA help guides invoked as `gcloud topic <name>`.

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| _(top-level)_ | [`_commands.md`](_commands.md) | 18 | All supplementary help guides (full text of each topic) |

See [`index.md`](index.md) for the one-line index of all 18 topics.

The most frequently consulted guides:

- **`filters`** — `--filter` expression syntax: operators (`:`, `=`, `!=`, `<`, `<=`, `>=`, `>`, `~`, `!~`), logic (`AND`, `OR`, `NOT`), client- vs server-side evaluation.
- **`formats`** — every `--format` value (`table`, `json`, `yaml`, `csv`, `value`, `flattened`, `list`, `multi`, `none`, …) and the `NAME[ATTRIBUTES](PROJECTION)` form.
- **`projections`** — projection key syntax, transform functions (`date()`, `size()`, `scope()`, `color()`, `list()`, …), and column attributes (`sort=`, `align=`, `label=`, `wrap`, `width=`).
- **`datetimes`** — absolute (ISO 8601 / RFC 3339 / RFC 822 / Unix) and relative (`-P1Y2M`, `+PT30M`) date/time input formats.
- **`escaping`** — alternate `^DELIM^` delimiter for list/dict flags whose values contain commas.
- **`configurations`** — named configuration lifecycle for multi-project / multi-account workflows.
- **`resource-keys`** — how to address nested resource fields (`abc.def[3].ghi`) for filters, formats, and projections.
- **`flags-file`** — `--flags-file=YAML_FILE` for portable, shell-independent complex flag values.
- **`gcloudignore`** — `.gcloudignore` (gitignore-style) file filtering for `app deploy`, `functions deploy`, `builds submit`, `run deploy`, etc.
- Plus `accessibility`, `arg-files`, `cli-trees`, `client-certificate`, `command-conventions`, `endpoint-override`, `offline-help`, `startup`, and `uninstall`.

## Common flags & tips

- **There are no resource flags here** — `gcloud topic <name>` takes no `--project`, region, or zone. Each command simply prints a guide. The standard help flags apply: `gcloud topic <name> --help`, `--document`, `--verbosity`.
- **Discover filterable/formattable fields first.** As the `filters` and `formats` guides recommend, run a command with `--format=yaml --limit=1` (or `--format=text`/`--format=flattened`) to see the exact resource keys before writing a `--filter` or `--format` expression. Example: `gcloud projects list --format=yaml --limit=1`.
- **`--filter` operator cheatsheet** (from `filters`): `key:value` (word/substring match), `key=value` (equality), `key~value` (regex), prefix a term with `-` for negation, and group alternatives with `=(a,b,c)`. Quote the whole expression; if the shell uses `'...'` use `"..."` inside it.
- **`--format` quick wins** (from `formats`): `--format="value(field)"` for scripting (tab-separated, no header), `--format=json`/`--format=yaml` for machine-readable output, `--format="table[box](a,b,c)"` for a decorated table, and `--flatten="field[]"` to expand a nested list before projecting it.
- **Relative durations** (from `datetimes`) work anywhere a date/time is expected, including inside `--filter`: `createTime>-P2W` (last two weeks), `+PT30M` (30 minutes from now).
- **Toggle global behaviors via properties** documented in these guides: `gcloud config set accessibility/screen_reader true` (accessibility), `gcloud config set gcloudignore/enabled false` (gcloudignore), `gcloud config set context_aware/use_client_certificate True` (client-certificate). Each gcloud property also has a `CLOUDSDK_SECTION_PROPERTY` environment-variable form (see `startup`).

## beta / alpha

There are no `gcloud beta topic` or `gcloud alpha topic` variants — the supplementary help guides are GA and version-agnostic, and they apply equally to GA, beta, and alpha command surfaces. (Individual topics such as `client-certificate` and `endpoint-override` may document features that relate to beta APIs, but the guides themselves are not staged.)

## Official documentation

- [gcloud topic CLI reference](https://cloud.google.com/sdk/gcloud/reference/topic) — index of all 18 supplementary help topics (the product docs home for this group).
- [topic/filters](https://cloud.google.com/sdk/gcloud/reference/topic/filters) — full `--filter` expression syntax and operators.
- [topic/formats](https://cloud.google.com/sdk/gcloud/reference/topic/formats) — all `--format` values and `NAME[ATTRIBUTES](PROJECTION)` syntax.
- [topic/projections](https://cloud.google.com/sdk/gcloud/reference/topic/projections) — projection keys, transform functions, and column attributes.
- [topic/datetimes](https://cloud.google.com/sdk/gcloud/reference/topic/datetimes) — absolute and relative date/time input formats.
- [topic/escaping](https://cloud.google.com/sdk/gcloud/reference/topic/escaping) — `^DELIM^` alternate-delimiter syntax for list/dict flags.
- [topic/configurations](https://cloud.google.com/sdk/gcloud/reference/topic/configurations) — named configuration lifecycle and usage.
- [topic/gcloudignore](https://cloud.google.com/sdk/gcloud/reference/topic/gcloudignore) — `.gcloudignore` file syntax and the commands that honor it.
- [topic/flags-file](https://cloud.google.com/sdk/gcloud/reference/topic/flags-file) — `--flags-file=YAML_FILE` for portable complex flag values.
- [Managing gcloud properties](https://cloud.google.com/sdk/docs/properties) — setting, overriding, and inspecting per-config key/value pairs.
- [Managing gcloud configurations](https://cloud.google.com/sdk/docs/configurations) — multi-project / multi-account configuration workflows.

See [`sources.md`](sources.md) for the consolidated citation list.
