# gcloud firebase test

interact with Firebase Test Lab


## `gcloud firebase test android` — command group for Android application testing
### `gcloud firebase test android list-device-capacities`

List capacity information for Android models & versions

List device capacity information (high/medium/low/none) for all Android
models & versions which are available for testing and have capacity
information published.

Device capacity is the number of online devices in Firebase Test Lab. For
physical devices, the number is the average of online devices in the last
30 days. It's important to note that device capacity does not directly
reflect any real-time data, like the length of the test queue, or the
available/busy state of the devices based on current test traffic.

**Synopsis:**
```
gcloud firebase test android list-device-capacities [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all published capacity information for Android devices, run:

    $ gcloud firebase test android list-device-capacities

To list capacity only for the model named 'redfin', run:

    $ gcloud firebase test android list-device-capacities --filter=redfin

To list capacities only for models that support API version 30, run:

    $ gcloud firebase test android list-device-capacities --filter=30
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firebase/test/android/list-device-capacities)

---
### `gcloud firebase test android run`

Invoke a test in Firebase Test Lab for Android and view test results

gcloud firebase test android run invokes and monitors tests in Firebase
Test Lab for Android.

Three main types of Android tests are currently supported:
  o robo: runs a smart, automated exploration of the activities in your
    Android app which records any installation failures or crashes and
    builds an activity map with associated screenshots and video.
  o instrumentation: runs automated unit or integration tests written
    using a testing framework. Firebase Test Lab for Android currently
    supports the Espresso and UI Automator 2.0 testing frameworks.
  o game-loop: executes a special intent built into the game app (a "demo
    mode") that simulates the actions of a real player. This test type can
    include multiple game loops (also called "scenarios"), which can be
    logically organized using scenario labels so that you can run related
    loops together. Refer to
    https://firebase.google.com/docs/test-lab/android/game-loop for more
    information about how to build and run Game Loop tests.

The type of test to run can be specified with the --type flag, although the
type can often be inferred from other flags. Specifically, if the --test
flag is present, the test --type defaults to instrumentation. If --test is
not present, then --type defaults to robo.

All arguments for gcloud firebase test android run may be specified on the
command line and/or within an argument file. Run $ gcloud topic arg-files
for more information about argument files.

**Synopsis:**
```
gcloud firebase test android run [ARGSPEC] [--app=APP]
    [--device=DIMENSION=VALUE,[...]] [--test=TEST] [--timeout=TIMEOUT]
    [--type=TYPE] [--additional-apks=APK,[APK,...]]
    [--app-package=APP_PACKAGE] [--async] [--auto-google-login]
    [--client-details=[KEY=VALUE,...]]
    [--directories-to-pull=[DIR_TO_PULL,...]]
    [--environment-variables=[KEY=VALUE,...]]
    [--network-profile=PROFILE_ID] [--num-flaky-test-attempts=int]
    [--obb-files=OBB_FILE,[OBB_FILE]]
    [--other-files=DEVICE_PATH=FILE_PATH,[...]] [--performance-metrics]
    [--record-video] [--results-bucket=RESULTS_BUCKET]
    [--results-dir=RESULTS_DIR]
    [--results-history-name=RESULTS_HISTORY_NAME]
    [--scenario-labels=LABEL,[LABEL,...]]
    [--scenario-numbers=int,[int,...]] [--test-package=TEST_PACKAGE]
    [--test-runner-class=TEST_RUNNER_CLASS]
    [--test-targets=TEST_TARGET,[TEST_TARGET,...]] [--use-orchestrator]
    [--resign] [--robo-directives=[TYPE:RESOURCE_NAME=INPUT,...]]
    [--robo-script=ROBO_SCRIPT]
    [--device-ids=MODEL_ID,[MODEL_ID,...], -d MODEL_ID,[MODEL_ID,...]]
    [--locales=LOCALE,[LOCALE,...], -l LOCALE,[LOCALE,...]]
    [--orientations=ORIENTATION,[ORIENTATION],
      -o ORIENTATION,[ORIENTATION]]
    [--os-version-ids=OS_VERSION_ID,[...], -v OS_VERSION_ID,[...]]
    [--filter=EXPRESSION] [--limit=LIMIT] [--page-size=PAGE_SIZE]
    [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[ARGSPEC]
   An ARG_FILE:ARG_GROUP_NAME pair, where ARG_FILE is the path to a file
   containing groups of test arguments in yaml format, and ARG_GROUP_NAME
   is the particular yaml object holding a group of arg:value pairs to
   use. Run $ gcloud topic arg-files for more information and examples.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--additional-apks` | APK,[APK,...] |  | A list of up to 100 additional APKs to install, in addition to those being directly tested. The path may be in the local filesystem or in Google Cloud Storage using gs:// notation. |
| `--app-package` | APP_PACKAGE |  | (REMOVED) The Java package of the application under test. By default, the application package name is parsed from the APK manifest. Flag --app-package has been removed. |
| `--async` |  |  | Invoke a test asynchronously without waiting for test results. |
| `--auto-google-login` |  |  | Automatically log into the test device using a preconfigured Google account before beginning the test. Enabled by default, use --no-auto-google-login to disable. |
| `--client-details` | [KEY=VALUE,...] |  | Comma-separated, KEY=VALUE map of additional details to attach to the test matrix. Arbitrary KEY=VALUE pairs may be attached to a test matrix to provide additional context about the tests being run. When consuming the test results, such as in Cloud Functions or a CI system, these details can add additional context such as a link to the corresponding pull request. Example: --client-details=buildNumber=1234,pullRequest=https://example.com/link/to/pull-request To help you identify and locate your test matrix in the Firebase console, use the matrixLabel key. Example: --client-details=matrixLabel="Example matrix label" |
| `--directories-to-pull` | [DIR_TO_PULL,...] |  | A list of paths that will be copied from the device's storage to the designated results bucket after the test is complete. These must be absolute paths under /sdcard, /storage, or /data/local/tmp (for example, --directories-to-pull /sdcard/tempDir1,/data/local/tmp/tempDir2). Path names are restricted to the characters a-zA-Z0-9_-./+. The paths /sdcard and /data will be made available and treated as implicit path substitutions. E.g. if /sdcard on a particular device does not map to external storage, the system will replace it with the external storage path prefix for that device. Note that access to some directories on API levels 29 and later may also be limited by scoped storage rules. |
| `--environment-variables` | [KEY=VALUE,...] |  | A comma-separated, key=value map of environment variables and their desired values. The environment variables are mirrored as extra options to the am instrument -e KEY1 VALUE1 ... command and passed to your test runner (typically AndroidJUnitRunner). Examples: Enable code coverage and provide a directory to store the coverage results when using Android Test Orchestrator (--use-orchestrator): --environment-variables clearPackageData=true,coverage=true,coverageFilePath=/sdcard/Download/ Enable code coverage and provide a file path to store the coverage results when not using Android Test Orchestrator (--no-use-orchestrator): --environment-variables coverage=true,coverageFile=/sdcard/Download/coverage.ec Note: If you need to embed a comma into a VALUE string, please refer to gcloud topic escaping for ways to change the default list delimiter. |
| `--network-profile` | PROFILE_ID |  | The name of the network traffic profile, for example --network-profile=LTE, which consists of a set of parameters to emulate network conditions when running the test (default: no network shaping; see available profiles listed by the $ gcloud firebase test network-profiles list command). This feature only works on physical devices. |
| `--num-flaky-test-attempts` | int |  | Specifies the number of times a test execution should be reattempted if one or more of its test cases fail for any reason. An execution that initially fails but succeeds on any reattempt is reported as FLAKY. The maximum number of reruns allowed is 10. (Default: 0, which implies no reruns.) All additional attempts are executed in parallel. |
| `--obb-files` | OBB_FILE,[OBB_FILE] |  | A list of one or two Android OBB file names which will be copied to each test device before the tests will run (default: None). Each OBB file name must conform to the format as specified by Android (e.g. [main\|patch].0300110.com.example.android.obb) and will be installed into <shared-storage>/Android/obb/<package-name>/ on the test device. |
| `--other-files` | DEVICE_PATH=FILE_PATH,[...] |  | A list of device-path=file-path pairs that indicate the device paths to push files to the device before starting tests, and the paths of files to push. Device paths must be under absolute, approved paths (${EXTERNAL_STORAGE}, or ${ANDROID_DATA}/local/tmp). Source file paths may be in the local filesystem or in Google Cloud Storage (gs://...). Examples: --other-files /sdcard/dir1/file1.txt=local/file.txt,/storage/dir2/file2.jpg=gs://bucket/file.jpg This flag only copies files to the device. To install files, like OBB or APK files, see --obb-files and --additional-apks. |
| `--performance-metrics` |  |  | Monitor and record performance metrics: CPU, memory, network usage, and FPS (game-loop only). Enabled by default, use --no-performance-metrics to disable. |
| `--record-video` |  |  | Enable video recording during the test. Enabled by default, use --no-record-video to disable. |
| `--results-bucket` | RESULTS_BUCKET |  | The name of a Google Cloud Storage bucket where raw test results will be stored (default: "test-lab-<random-UUID>"). Note that the bucket must be owned by a billing-enabled project, and that using a non-default bucket will result in billing charges for the storage used. |
| `--results-dir` | RESULTS_DIR |  | The name of a unique Google Cloud Storage object within the results bucket where raw test results will be stored (default: a timestamp with a random suffix). Caution: if specified, this argument must be unique for each test matrix you create, otherwise results from multiple test matrices will be overwritten or intermingled. |
| `--results-history-name` | RESULTS_HISTORY_NAME |  | The history name for your test results (an arbitrary string label; default: the application's label from the APK manifest). All tests which use the same history name will have their results grouped together in the Firebase console in a time-ordered test history list. |


**Examples:**
```bash
To invoke a robo test lasting 100 seconds against the default device
environment, run:

    $ gcloud firebase test android run --app=APP_APK --timeout=100s

When specifying devices to test against, the preferred method is to use the
--device flag. For example, to invoke a robo test against a virtual,
generic MDPI Nexus device in landscape orientation, run:

    $ gcloud firebase test android run --app=APP_APK \
        --device=model=NexusLowRes,orientation=landscape

To invoke an instrumentation test against a physical Nexus 6 device
(MODEL_ID: shamu) which is running Android API level 21 in French, run:

    $ gcloud firebase test android run --app=APP_APK --test=TEST_APK \
        --device=model=shamu,version=21,locale=fr

To test against multiple devices, specify --device more than once:

    $ gcloud firebase test android run --app=APP_APK --test=TEST_APK \
        --device=model=Nexus4,version=19 \
        --device=model=Nexus4,version=21 \
        --device=model=NexusLowRes,version=25

To invoke a robo test on an Android App Bundle, pass the .aab file using
the --app flag.

    $ gcloud firebase test android run --app=bundle.aab

You may also use the legacy dimension flags (deprecated) to specify which
devices to use. Firebase Test Lab will run tests against every possible
combination of the listed device dimensions. Note that some combinations of
device models and OS versions may not be valid or available in Test Lab.
Any unsupported combinations of dimensions in the test matrix will be
skipped.

For example, to execute a series of 5-minute robo tests against a very
comprehensive matrix of virtual and physical devices, OS versions, locales
and orientations, run:

    $ gcloud firebase test android run --app=APP_APK --timeout=5m \
        --device-ids=shamu,NexusLowRes,Nexus5,g3,zeroflte \
        --os-version-ids=19,21,22,23,24,25 --locales=en_GB,es,fr,ru,zh \
        --orientations=portrait,landscape

The above command will generate a test matrix with a total of 300 test
executions, but only the subset of executions with valid dimension
combinations will actually run your tests.

To help you identify and locate your test matrix in the Firebase console,
run:

    $ gcloud firebase test android run --app=APP_APK \
        --client-details=matrixLabel="Example matrix label"

Controlling Results Storage

By default, Firebase Test Lab stores detailed test results for a limited
time in a Google Cloud Storage bucket provided for you at no charge. Note:
This requires the principal executing the test to have "roles/editor" role
for the project. If either you do not have that role, you wish to use a
storage bucket that you control, or you need to retain detailed test
results for a longer period, use the --results-bucket option. See
https://firebase.google.com/docs/test-lab/analyzing-results#detailed for
more information.

Detailed test result files are prefixed by default with a timestamp and a
random character string. If you require a predictable path where detailed
test results are stored within the results bucket (say, if you have a
Continuous Integration system which does custom post-processing of test
result artifacts), use the --results-dir option. Note that each test
invocation must have a unique storage location, so never reuse the same
value for --results-dir between different test runs. Possible strategies
could include using a UUID or sequence number for --results-dir.

For example, to run a robo test using a specific Google Cloud Storage
location to hold the raw test results, run:

    $ gcloud firebase test android run --app=APP_APK \
        --results-bucket=gs://my-bucket \
        --results-dir=my/test/results/<unique-value>

To run an instrumentation test and specify a custom name under which the
history of your tests will be collected and displayed in the Firebase
console, run:

    $ gcloud firebase test android run --app=APP_APK --test=TEST_APK \
        --results-history-name='Excelsior App Test History'

Argument Files

All test arguments for a given test may alternatively be stored in an
argument group within a YAML-formatted argument file. The ARG_FILE may
contain one or more named argument groups, and argument groups may be
combined using the include: attribute (Run $ gcloud topic arg-files for
more information). The ARG_FILE can easily be shared with colleagues or
placed under source control to ensure consistent test executions.

To run a test using arguments loaded from an ARG_FILE named excelsior_args,
which contains an argument group named robo-args:, use the following
syntax:

    $ gcloud firebase test android run path/to/excelsior_args:robo-args
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firebase/test/android/run)

---

## `gcloud firebase test android locales` — explore Android locales available for testing
### `gcloud firebase test android locales describe`

Describe an Android locale

Describe an Android locale.

**Synopsis:**
```
gcloud firebase test android locales describe LOCALE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
LOCALE
   The locale to describe, found using $ gcloud firebase test android
   locales list.
```

**Examples:**
```bash
To see the attributes of the Android locale 'my-locale', run:

    $ gcloud firebase test android locales describe my-locale
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firebase/test/android/locales/describe)

---
### `gcloud firebase test android locales list`

List all Android locales available for testing internationalized apps

List all Android locales available for testing internationalized apps.

**Synopsis:**
```
gcloud firebase test android locales list [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all available locales which can be used for testing
internationalized Android applications, run:

    $ gcloud firebase test android locales list

To filter the locales to see only Spanish-speaking regions, run:

    $ gcloud firebase test android locales list --filter=Spanish
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firebase/test/android/locales/list)

---

## `gcloud firebase test android models` — explore Android models available in the Test Environment catalog
### `gcloud firebase test android models describe`

Describe an Android model

Describe an Android model.

**Synopsis:**
```
gcloud firebase test android models describe MODEL_ID
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
MODEL_ID
   ID of the model to describe, found using $ gcloud firebase test android
   models list.
```

**Examples:**
```bash
To see the attributes of the android model 'my-model', run:

    $ gcloud firebase test android models describe my-model
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firebase/test/android/models/describe)

---
### `gcloud firebase test android models list`

List all Android models available for testing

List all Android models available for testing.

**Synopsis:**
```
gcloud firebase test android models list [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all models which are available for testing, run:

    $ gcloud firebase test android models list

To list all models made by Samsung, run:

    $ gcloud firebase test android models list --filter=Samsung

To list all virtual device models, run:

    $ gcloud firebase test android models list --filter=virtual
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firebase/test/android/models/list)

---

## `gcloud firebase test android versions` — explore Android versions available for testing
### `gcloud firebase test android versions describe`

Describe an Android OS version

Describe an Android OS version.

**Synopsis:**
```
gcloud firebase test android versions describe VERSION_ID
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
VERSION_ID
   The version ID to describe, found using $ gcloud firebase test android
   versions list.
```

**Examples:**
```bash
To see attributes of the Android OS version 'my-version', run:

    $ gcloud firebase test android versions describe my-version
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firebase/test/android/versions/describe)

---
### `gcloud firebase test android versions list`

List all Android OS versions available for testing

List all Android OS versions available for testing.

**Synopsis:**
```
gcloud firebase test android versions list [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all versions available for testing, run:

    $ gcloud firebase test android versions list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firebase/test/android/versions/list)

---

## `gcloud firebase test ios` — command group for iOS application testing
### `gcloud firebase test ios list-device-capacities`

List capacity information for iOS models & versions

List device capacity information (high/medium/low/none) for all iOS models
& versions which are available for testing and have capacity information
published.

Device capacity is the number of online devices in Firebase Test Lab. For
physical devices, the number is the average of online devices in the last
30 days. It's important to note that device capacity does not directly
reflect any real-time data, like the length of the test queue, or the
available/busy state of the devices based on current test traffic.

**Synopsis:**
```
gcloud firebase test ios list-device-capacities [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all published capacity information for iOS devices, run:

    $ gcloud firebase test ios list-device-capacities

To list capacities for only iPad devices, run:

    $ gcloud firebase test ios list-device-capacities --filter=ipad

To list capacities for only iOS version 14.2 devices, run:

    $ gcloud firebase test ios list-device-capacities --filter=14.2
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firebase/test/ios/list-device-capacities)

---
### `gcloud firebase test ios run`

Invoke a test in Firebase Test Lab for iOS and view test results

gcloud firebase test ios run invokes and monitors tests in Firebase Test
Lab for iOS.

The currently supported iOS test frameworks are XCTest and XCUITest. Other
iOS testing frameworks which are built upon XCTest and XCUITest should also
work.

The XCTEST_ZIP test package is a zip file built using Apple's Xcode and
supporting tools. For a detailed description of the process to create your
XCTEST_ZIP file, see
https://firebase.google.com/docs/test-lab/ios/command-line.

All arguments for gcloud firebase test ios run may be specified on the
command line and/or within an argument file. Run $ gcloud topic arg-files
for more information about argument files.

**Synopsis:**
```
gcloud firebase test ios run [ARGSPEC] [--device=DIMENSION=VALUE,[...]]
    [--test=XCTEST_ZIP] [--timeout=TIMEOUT] [--type=TYPE]
    [--xcode-version=XCODE_VERSION] [--xctestrun-file=XCTESTRUN_FILE]
    [--app=APP] [--async] [--client-details=[KEY=VALUE,...]]
    [--num-flaky-test-attempts=int] [--record-video]
    [--results-bucket=RESULTS_BUCKET] [--results-dir=RESULTS_DIR]
    [--results-history-name=RESULTS_HISTORY_NAME]
    [--test-special-entitlements] [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[ARGSPEC]
   An ARG_FILE:ARG_GROUP_NAME pair, where ARG_FILE is the path to a file
   containing groups of test arguments in yaml format, and ARG_GROUP_NAME
   is the particular yaml object holding a group of arg:value pairs to
   use. Run $ gcloud topic arg-files for more information and examples.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--app` | APP |  | The path to the application archive (.ipa file) for game-loop testing. The path may be in the local filesystem or in Google Cloud Storage using gs:// notation. This flag is only valid when --type is game-loop or robo. |
| `--async` |  |  | Invoke a test asynchronously without waiting for test results. |
| `--client-details` | [KEY=VALUE,...] |  | Comma-separated, KEY=VALUE map of additional details to attach to the test matrix. Arbitrary KEY=VALUE pairs may be attached to a test matrix to provide additional context about the tests being run. When consuming the test results, such as in Cloud Functions or a CI system, these details can add additional context such as a link to the corresponding pull request. Example: --client-details=buildNumber=1234,pullRequest=https://example.com/link/to/pull-request To help you identify and locate your test matrix in the Firebase console, use the matrixLabel key. Example: --client-details=matrixLabel="Example matrix label" |
| `--num-flaky-test-attempts` | int |  | Specifies the number of times a test execution should be reattempted if one or more of its test cases fail for any reason. An execution that initially fails but succeeds on any reattempt is reported as FLAKY. The maximum number of reruns allowed is 10. (Default: 0, which implies no reruns.) All additional attempts are executed in parallel. |
| `--record-video` |  |  | Enable video recording during the test. Enabled by default, use --no-record-video to disable. |
| `--results-bucket` | RESULTS_BUCKET |  | The name of a Google Cloud Storage bucket where raw test results will be stored (default: "test-lab-<random-UUID>"). Note that the bucket must be owned by a billing-enabled project, and that using a non-default bucket will result in billing charges for the storage used. |
| `--results-dir` | RESULTS_DIR |  | The name of a unique Google Cloud Storage object within the results bucket where raw test results will be stored (default: a timestamp with a random suffix). Caution: if specified, this argument must be unique for each test matrix you create, otherwise results from multiple test matrices will be overwritten or intermingled. |
| `--results-history-name` | RESULTS_HISTORY_NAME |  | The history name for your test results (an arbitrary string label; default: the bundle ID for the iOS application). All tests which use the same history name will have their results grouped together in the Firebase console in a time-ordered test history list. |
| `--test-special-entitlements` |  |  | Enables testing special app entitlements. Re-signs an app having special entitlements with a new application-identifier. This currently supports testing Push Notifications (aps-environment) entitlement for up to one app in a project. Note: Because this changes the app's identifier, make sure none of the resources in your zip file contain direct references to the test app's bundle id. |


**Examples:**
```bash
To invoke an XCTest lasting up to five minutes against the default device
environment, run:

    $ gcloud firebase test ios run --test=XCTEST_ZIP --timeout=5m

To invoke an XCTest against an iPad 5 running iOS 11.2, run:

    $ gcloud firebase test ios run --test=XCTEST_ZIP \
        --device=model=ipad5,version=11.2

To run your tests against multiple iOS devices simultaneously, specify the
--device flag more than once:

    $ gcloud firebase test ios run --test=XCTEST_ZIP \
        --device=model=iphone7 --device=model=ipadmini4,version=11.2 \
        --device=model=iphonese

To run your XCTest using a specific version of Xcode, say 9.4.1, run:

    $ gcloud firebase test ios run --test=XCTEST_ZIP \
        --xcode-version=9.4.1

To help you identify and locate your test matrix in the Firebase console,
run:

    $ gcloud firebase test ios run --test=XCTEST_ZIP \
        --client-details=matrixLabel="Example matrix label"

All test arguments for a given test may alternatively be stored in an
argument group within a YAML-formatted argument file. The ARG_FILE may
contain one or more named argument groups, and argument groups may be
combined using the include: attribute (Run $ gcloud topic arg-files for
more information). The ARG_FILE can easily be shared with colleagues or
placed under source control to ensure consistent test executions.

To run a test using arguments loaded from an ARG_FILE named
excelsior_app_args, which contains an argument group named ios-args:, use
the following syntax:

    $ gcloud firebase test ios run path/to/excelsior_app_args:ios-args
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firebase/test/ios/run)

---

## `gcloud firebase test ios locales` — explore iOS locales available for testing
### `gcloud firebase test ios locales describe`

Describe an iOS locale

Describe an iOS locale.

**Synopsis:**
```
gcloud firebase test ios locales describe LOCALE [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
LOCALE
   The locale to describe, found using $ gcloud firebase test ios locales
   list.
```

**Examples:**
```bash
To describe an iOS locale, run:

    gcloud firebase test ios locales describe es_419

To describe an iOS locale in JSON format, run:

    gcloud firebase test ios locales describe es_419 --format=json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firebase/test/ios/locales/describe)

---
### `gcloud firebase test ios locales list`

List all iOS locales available for testing internationalized apps

List all iOS locales available for testing internationalized apps.

**Synopsis:**
```
gcloud firebase test ios locales list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all available locales which can be used for testing
internationalized iOS applications, run:

    $ gcloud firebase test ios locales list

To filter the locales to see only Spanish-speaking regions, run:

    $ gcloud firebase test ios locales list --filter=Spanish
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firebase/test/ios/locales/list)

---

## `gcloud firebase test ios models` — explore iOS models available in the Test Environment catalog
### `gcloud firebase test ios models describe`

Describe an iOS model

Describe an iOS model.

**Synopsis:**
```
gcloud firebase test ios models describe MODEL_ID [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
MODEL_ID
   ID of the model to describe, found using $ gcloud firebase test ios
   models list.
```

**Examples:**
```bash
To describe an iOS model, run:

    gcloud firebase test ios models describe iphone7

To describe an iOS model in JSON format, run:

    gcloud firebase test ios models describe iphone7 --format=json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firebase/test/ios/models/describe)

---
### `gcloud firebase test ios models list`

List all iOS models available for testing

List all iOS models available for testing.

**Synopsis:**
```
gcloud firebase test ios models list [--filter=EXPRESSION] [--limit=LIMIT]
    [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]] [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all iOS models available for testing, run:

    gcloud firebase test ios models list
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firebase/test/ios/models/list)

---

## `gcloud firebase test ios versions` — explore iOS versions available for testing
### `gcloud firebase test ios versions describe`

Describe an iOS operating system version

Describe an iOS operating system version.

**Synopsis:**
```
gcloud firebase test ios versions describe VERSION_ID
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
VERSION_ID
   The version ID to describe, found using $ gcloud firebase test ios
   versions list.
```

**Examples:**
```bash
To describe an iOS operating system version available for testing, run:

    gcloud firebase test ios versions describe 12.1

To describe an iOS operating system version available for testing in JSON
format, run:

    gcloud firebase test ios versions describe 12.1 --format=json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firebase/test/ios/versions/describe)

---
### `gcloud firebase test ios versions list`

List all iOS versions available for testing

List all iOS versions available for testing.

**Synopsis:**
```
gcloud firebase test ios versions list [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all iOS versions available for testing, run:

    gcloud firebase test ios versions list

To filter major versions available for testing, run:

    gcloud firebase test ios versions list --filter=majorVersion:12
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firebase/test/ios/versions/list)

---

## `gcloud firebase test network-profiles` — explore network profiles available for testing
### `gcloud firebase test network-profiles describe`

Describe a network profile

Describe a network profile.

Run $ gcloud firebase test network-profiles --help for descriptions of the
network profile parameters.

**Synopsis:**
```
gcloud firebase test network-profiles describe PROFILE_ID
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
PROFILE_ID
   The network profile to describe, found using $ gcloud firebase test
   network-profiles list.
```

**Examples:**
```bash
To describe a network profile, run:

    gcloud firebase test network-profiles describe GSM

To describe a network profiles in JSON format, run:

    gcloud firebase test network-profiles describe GSM --format=json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firebase/test/network-profiles/describe)

---
### `gcloud firebase test network-profiles list`

List all network profiles available for testing

List all network profiles available for testing.

Run $ gcloud firebase test network-profiles --help for descriptions of the
network profile parameters.

**Synopsis:**
```
gcloud firebase test network-profiles list [--filter=EXPRESSION]
    [--limit=LIMIT] [--page-size=PAGE_SIZE] [--sort-by=[FIELD,...]]
    [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To list all network profiles, run:

    gcloud firebase test network-profiles list

To list all GSM network profiles, run:

    gcloud firebase test network-profiles list --filter="id:GSM"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/firebase/test/network-profiles/list)

---