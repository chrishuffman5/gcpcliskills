---
name: gcloud-firebase
description: >-
  Firebase Test Lab via gcloud (`gcloud firebase`). Work with Google Firebase — test.
---

# gcloud firebase — Firebase Test Lab

## Overview

`gcloud firebase` is the CLI surface for **Firebase Test Lab** — a cloud-based app-testing infrastructure that runs Android and iOS tests against real (physical) and virtual devices hosted in Google data centers. Every command lives under `gcloud firebase test`: you submit test matrices (`run`), explore the device/version/locale catalog, and inspect network profiles. Reach for it when you want to run robo, instrumentation (Espresso/UI Automator), game-loop, or XCTest suites across many device configurations from a script or CI pipeline.

Note: `gcloud firebase` covers **Test Lab only**. The rest of the Firebase platform (Authentication, Firestore, Hosting, Cloud Functions, etc.) is managed with the separate **Firebase CLI** (`firebase`, an npm package) or the Firebase console — not with `gcloud`.

## Quick reference — common workflows

### 1. Enable the APIs and discover the device catalog

```bash
# Test Lab needs both the Testing and Tool Results APIs
gcloud services enable testing.googleapis.com toolresults.googleapis.com

# Browse the Android catalog
gcloud firebase test android models list --filter=virtual
gcloud firebase test android versions list
gcloud firebase test android locales list
gcloud firebase test android list-device-capacities
```

### 2. Run an Android robo test (automated UI exploration)

```bash
# Quick robo test against the default device, 90-second timeout
gcloud firebase test android run \
  --app=my-app.apk \
  --timeout=90s

# Robo test on a specific virtual device, landscape orientation
gcloud firebase test android run \
  --app=my-app.apk \
  --device=model=NexusLowRes,orientation=landscape \
  --timeout=5m
```

With no `--test`, `--type` defaults to `robo`.

### 3. Run an Android instrumentation (Espresso) test in CI

```bash
# Single physical device, French locale, API level 21
gcloud firebase test android run \
  --app=my-app.apk \
  --test=my-test.apk \
  --device=model=shamu,version=21,locale=fr

# Fan out across several devices in one matrix
gcloud firebase test android run \
  --app=my-app.apk \
  --test=my-test.apk \
  --device=model=Nexus4,version=19 \
  --device=model=Nexus4,version=21 \
  --device=model=NexusLowRes,version=25

# Pin a controlled results bucket + unique results dir (per-build, never reused)
gcloud firebase test android run \
  --app=my-app.apk \
  --test=my-test.apk \
  --device=model=NexusLowRes,version=28 \
  --results-bucket=gs://my-ci-results-bucket \
  --results-dir=my/test/results/build-1234
```

Specifying `--test` makes `--type` default to `instrumentation`.

### 4. Run an Android test with network emulation

```bash
gcloud firebase test network-profiles list
gcloud firebase test network-profiles describe LTE

# Network shaping applies to physical devices only
gcloud firebase test android run \
  --app=my-app.apk \
  --test=my-test.apk \
  --device=model=shamu,version=23 \
  --network-profile=LTE
```

### 5. Run an iOS XCTest

```bash
gcloud firebase test ios models list
gcloud firebase test ios versions list
gcloud firebase test ios list-device-capacities

# XCTest against the default device
gcloud firebase test ios run \
  --test=MyTests.zip \
  --timeout=5m

# Specific iPad model / iOS version, and a pinned Xcode version
gcloud firebase test ios run \
  --test=MyTests.zip \
  --device=model=ipad5,version=11.2 \
  --xcode-version=9.4.1
```

### 6. Label matrices for CI traceability

```bash
gcloud firebase test android run \
  --app=my-app.apk \
  --device=model=NexusLowRes,version=28 \
  --client-details=matrixLabel="PR-456 smoke",buildNumber=456

gcloud firebase test ios run \
  --test=MyTests.zip \
  --device=model=iphone7 \
  --client-details=matrixLabel="iOS nightly build-789"
```

## Command groups

| Group | Reference file | Commands | Description |
|-------|----------------|----------|-------------|
| `firebase test` | [`test.md`](test.md) | 18 | Interact with Firebase Test Lab — `android`/`ios` `run` plus the models, versions, locales, device-capacity, and network-profile catalogs |

See [`index.md`](index.md) for a one-line index of all 18 commands.

## Common flags & tips

- **Selecting devices** — prefer the repeatable `--device=DIMENSION=VALUE,[...]` flag (e.g. `--device=model=shamu,version=21,locale=fr,orientation=portrait`). Repeat it once per device to build a matrix. The legacy dimension flags (`--device-ids`/`-d`, `--os-version-ids`/`-v`, `--locales`/`-l`, `--orientations`/`-o`) are deprecated and run the full cross-product of every listed dimension.
- **Test type** — `--type` is usually inferred: `robo` when `--test` is absent, `instrumentation` when `--test` is present; set `--type=game-loop` explicitly for game-loop tests.
- **Async + CI** — `--async` returns immediately without waiting for results. For CI, always pair `--results-bucket` with a **unique** `--results-dir` per run (never reuse it, or matrices overwrite each other) and use `--results-history-name` to group runs in the console.
- **Flaky tests** — `--num-flaky-test-attempts=N` (max 10) reruns failing cases; an execution that passes on retry is reported as `FLAKY`.
- **Catalog discovery + filtering** — `list` commands accept the standard `--filter`, `--limit`, `--sort-by`, and `--page-size` flags. Examples: `gcloud firebase test android models list --filter=Samsung`, `gcloud firebase test ios versions list --filter=majorVersion:12`, `gcloud firebase test network-profiles list --filter="id:GSM"`.
- **Output format** — `describe` commands support `--format=json` for scripting (e.g. `gcloud firebase test ios models describe iphone7 --format=json`).
- **Toggles enabled by default** — `--record-video`, `--performance-metrics` (Android), and `--auto-google-login` (Android) are on by default; disable with `--no-record-video`, `--no-performance-metrics`, `--no-auto-google-login`.
- **Argument files** — any `run` invocation can load arguments from a YAML arg file via the positional `ARGSPEC` (`gcloud firebase test android run path/to/args:robo-args`). Run `gcloud topic arg-files` for the format.
- **Storage & IAM** — default (free) result storage needs `roles/editor`; a custom `--results-bucket` needs `roles/cloudtestservice.testAdmin` (plus `roles/firebase.analyticsViewer`), and viewers need `roles/cloudtestservice.testViewer`. The bucket must belong to a billing-enabled project.

## beta / alpha

`gcloud alpha firebase test` and `gcloud beta firebase test` variants exist, but the 18-command GA surface is comprehensive for the core test-running workflows, and no capabilities are documented as alpha/beta-only in the official reference. Check `gcloud beta firebase test --help` / `gcloud alpha firebase test --help` for any experimental flags not yet promoted to GA.

## Official documentation

- [Firebase Test Lab docs home](https://firebase.google.com/docs/test-lab) — product overview, capabilities, and implementation path.
- [Android Test Lab CLI guide](https://firebase.google.com/docs/test-lab/android/command-line) — robo, instrumentation, and game-loop tests via gcloud.
- [iOS Test Lab CLI guide](https://firebase.google.com/docs/test-lab/ios/command-line) — XCTest packaging, device dimensions, and game-loop tests.
- [Android get-started guide](https://firebase.google.com/docs/test-lab/android/get-started) — intro concepts, test types, and tooling approaches.
- [iOS get-started guide](https://firebase.google.com/docs/test-lab/ios/get-started) — XCTest, game-loop, device selection, and results.
- [Android game-loop tests](https://firebase.google.com/docs/test-lab/android/game-loop) — manifest setup, multi-loop execution, and scenario labels.
- [IAM permissions reference](https://firebase.google.com/docs/test-lab/android/iam-permissions-reference) — roles for running tests, viewing results, and direct device access.
- [Analyzing Test Lab results](https://firebase.google.com/docs/test-lab/android/analyzing-results) — test outcomes, data retention, and Cloud Storage integration.
- [Quotas & pricing](https://firebase.google.com/docs/test-lab/usage-quotas-pricing) — Spark/Blaze tiers, physical vs virtual device rates, and API limits.
- [gcloud reference: `firebase`](https://cloud.google.com/sdk/gcloud/reference/firebase) — full command/flag reference for the `gcloud firebase` group.
- [gcloud reference: `firebase test android run`](https://cloud.google.com/sdk/gcloud/reference/firebase/test/android/run) — every flag, example, and storage behavior for the primary Android command.
