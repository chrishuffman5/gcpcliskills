# gcloud topic (top-level commands)

### `gcloud topic accessibility`

Reference for Accessibility features

The accessibility/screen_reader property when set to true will change some
behavior to make gcloud more screen reader friendly. Currently the
following changes are implemented:

  o For progress trackers, instead of unicode spinners, the phrase
    'working' is displayed on stderr, every second while gcloud is working.
  o For progress bars, progress is displayed as a percentage, outputted
    to stderr.
  o For boxed tables, instead of the queried resources being displayed in
    tables drawn in Unicode, results are rendered as a flattened list of
    items. Also consider using the --format flag to define your own format.

To turn this on, run:

    $ gcloud config set accessibility/screen_reader true

Accessibility support is still in early stages. Please report any issues
that you would like fixed using gcloud feedback.

[Official reference](https://cloud.google.com/sdk/gcloud/reference/topic/accessibility)

---
### `gcloud topic arg-files`

Supplementary help for arg-files to be used with gcloud firebase test

Supplementary help for arg-files to be used with gcloud firebase test.

All gcloud firebase test android run arguments may be specified by flags on
the command line and/or via a YAML-formatted ARG_FILE. The optional,
positional ARG_SPEC argument on the command line is used to specify a
single ARG_FILE:ARG_GROUP_NAME pair, where ARG_FILE is the path to the YAML
argument file, and ARG_GROUP_NAME is the name of the argument group to load
and parse. The ARG_FILE must contain valid YAML syntax or gcloud will
respond with an error.

The basic format of a YAML argument file is:

    arg-group1:
      arg1: value1  # a comment
      arg2: value2
      ...

    # Another comment
    arg-group2:
      arg3: value3
      ...

List arguments may be specified within square brackets:

    directories-to-pull: [/sdcard/dir1, /data/dir2]

or by using the alternate YAML list notation with one dash per list item:

    directories-to-pull:
      - /sdcard/dir1
      - /data/dir2

If a list argument only contains a single value, you may omit the square
brackets:

    directories-to-pull: /sdcard/dir1

Composition

A special include: [ARG_GROUP1, ...] syntax allows merging or composition
of argument groups (see EXAMPLES below). Included argument groups can
include: other argument groups within the same YAML file, with unlimited
nesting.

Precedence

An argument which appears on the command line has the highest precedence
and will override the same argument if it is specified within an argument
file.

Any argument defined directly within a group will have higher precedence
than an identical argument which is merged into that group using the
include: keyword.

**Examples:**
```bash
Here are the contents of a very simple YAML argument file which is assumed
to be stored in a file named excelsior_args.yaml:

    # Run a quick 'robo' test on the 'Excelsior' app for
    # 90 seconds using only the default Test Lab device.
    quick-robo-test:
      app: path/to/excelsior.apk
      type: robo
      max-steps: 100
      timeout: 90s
      async: true

To invoke this test, run:

    $ gcloud firebase test android run \
        excelsior_args.yaml:quick-robo-test

To select which device(s) you wish to test against in an argument file, use
device: to specify one or more devices, with each device having one or more
dimensions. For example, to specify the LG G3 device in the Chinese locale
and with landscape orientation, use:

    single-device-group:
      device: [{model: g3, orientation: landscape, locale: zh}]

To specify multiple devices, use any of the following equivalent YAML
formats:

    multi-device-group1:
      device: [{model: flo}, {model: g3, version: 19, locale: zh}, {model: mako, version: 21}]

    multi-device-group2:
      device:
        - {model: flo}
        - {model: g3, version: 19, locale: zh}
        - {model: mako, version: 21}

    multi-device-group3:
      device:
        - model: flo
        - model: g3
          version: 19
          locale: zh
        - model: mako
          version: 21

If your app has a login screen, or has additional UI elements which require
input text, you may specify the resource names of the Android target UI
elements, along with their corresponding input values, in the
'robo-directives' map argument. You may also specify the elements which the
Robo test should prioritize clicking. In the example below,
"username_resource" is the resource name of the username field and
"username" is the input for that field (similarly for password), and
"signin_button_resource" is the resource name of the sign in button.

    # Run a 'robo' test on the 'Excelsior' app with login credentials.
    robo-test-with-login:
      app: path/to/excelsior.apk
      type: robo
      robo-directives:
        "text:username_resource": username
        "text:password_resource": password
        "click:sigin_button_resource": ""

Assuming the above YAML text is appended to the arg-file named
excelsior_args.yaml, you may invoke the test by running:

    $ gcloud firebase test android run \
        excelsior_args.yaml:robo-test-with-login

Here is a slightly more complicated example which demonstrates composition
of argument groups using the legacy device dimension arguments (device: is
now the preferred way to specify test devices). Assume the following YAML
text is appended to the arg-file shown above named excelsior_args.yaml:

    # Specify some unit tests to be run against a test matrix
    # with one device type, two Android versions, and four
    # locales, for a total of eight test variations (1*2*4).
    unit-tests:
      type: instrumentation
      app: path/to/excelsior.apk
      test: path/to/excelsior-test.apk  # the unit tests
      timeout: 10m
      device-ids: NexusLowRes
      include: [supported-versions, supported-locales]

    supported-versions:
      os-version-ids: [21, 22]

    supported-locales:
      locales: [en, es, fr, it]

To invoke this test matrix, run:

    $ gcloud firebase test android run excelsior_args.yaml:unit-tests

To run these unit tests with the same locales and os-version-ids, but
substituting a sampling of three physical Android devices instead of the
single virtual NexusLowRes device, run:

    $ gcloud firebase test android run excelsior_args.yaml:unit-tests \
        --device-ids shamu,htc_m8,g3

In the last example, the --device-ids argument on the command line
overrides the device-ids: specification inside the arg-file because
command-line arguments have higher precedence.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/topic/arg-files)

---
### `gcloud topic cli-trees`

CLI trees supplementary help

  CLI trees are static nested dictionaries that describe all of the groups,
  commands, flags, positionals, help text, and completer module paths for a
  CLI. A CLI tree is often much faster to load and access than one generated
  at runtime from an active CLI. It is also a more compact representation. A
  properly formed CLI tree can be used to reproduce the help documentation
  for an entire CLI.

CLI Tree Data Files
  A CLI tree is a dictionary in a JSON file. By convention, the file base
  name is the corresponding CLI name. For example, the CLI tree file name for
  gcloud is gcloud.json.

  CLI trees associated with Google Cloud CLI modules are installed in the
  data/cli subdirectory of the Google Cloud CLI installation root:

      $(gcloud info --format="value(installation.sdk_root)")/data/cli

  This includes tree data for gcloud (core component), bq, gsutil, and
  kubectl. Note that the tree data is installed with the component. If the
  component is not installed then neither is its CLI tree. An installed
  component does not require its CLI tree to run. Only the gcloud CLI tree is
  required by $ gcloud alpha interactive.

  By default, CLI trees for other commands are JSON files generated on demand
  from their man(1) or man7.org man pages. They are cached in the cli
  subdirectory of the global config directory:

      $(gcloud info --format="value(config.paths.global_config_dir)")/cli

The gcloud CLI Tree
  The gcloud CLI tree is used for static TAB completion, the corpus for $
  gcloud alpha help-search, and the data source for $ gcloud alpha
  interactive completions and help text generation.

Other CLI Trees
  $ gcloud alpha interactive uses CLI tree data files for typeahead, command
  line completion and active help. A few CLI trees are installed with their
  respective Google Cloud CLI components: gcloud (core component), bq,
  gsutil, and kubectl.

  The generated trees are a close approximation. You can construct your own,
  especially for hierarchical CLIs like git(1) that are hard to extract from
  man pages.

CLI Tree Schema
  TBD (gcloud interactive is still in ALPHA).

[Official reference](https://cloud.google.com/sdk/gcloud/reference/topic/cli-trees)

---
### `gcloud topic client-certificate`

Client certificate authorization supplementary help

Client certificate authorization supplementary help.

Device Certificate Authorization (DCA) enables Context-aware access to
identify devices by their X.509 certificates. DCA for Google Cloud APIs is
the second in a series of releases that provides administrators the
capability to protect access to their Google Cloud resources with device
certificates. This feature builds on top of the existing Context-aware
access suite (Endpoint Verification, Access Context Manager, and VPC
Service Controls) and ensures that only users on trusted devices with a
Google-generated certificate are able to access Google Cloud APIs. This
provides a stronger signal of device identity (device certificate
verification), and protects users from credential theft to accidental loss
by only granting access when credentials and the original device
certificate are presented.

To use this feature, organizations can follow the instructions below to
install an endpoint verification agent to devices:

  o Automatically deploy endpoint verification
    (https://support.google.com/a/answer/9007320#)
    * Via Chrome Policy for the extension
    * 3rd party image/software distribution tools for the Native Helper
      on macOS and Windows
  o Let users install endpoint verification themselves from the Chrome
    Webstore (https://support.google.com/a/users/answer/9018161#install)
    * Users would also be prompted to install the Native Helper as well

For a greater level of security, operating system key stores can be used to
store client certificate objects. This feature is enabled by using
enterprise-certificate-proxy
(https://github.com/googleapis/enterprise-certificate-proxy).

enterprise-certificate-proxy can be installed by running $ gcloud
components install enterprise-certificate-proxy.

In order to use enterprise-certificate-proxy it must first be configured.
By default the configuration should be written to
~/.config/gcloud/certificate_config.json.

The enterprise-certificate-proxy schema is documented on the GitHub project
page
(https://github.com/googleapis/enterprise-certificate-proxy#certificate-configuration).
Each operating system that gcloud supports uses a different key store. The
certificate_config may contain multiple OS configurations.

Provisioning the key stores is not in scope for this document.

Run $ gcloud config set context_aware/use_client_certificate True so that
the gcloud CLI will load the certificate and send it to services.

See https://cloud.google.com/sdk/gcloud/reference/topic/client-certificate
for the support list for the latest version of the gcloud CLI. Please
upgrade the gcloud command-line tool if necessary.

Note: iap_tunnel is a special service gcloud CLI uses to create the IAP
tunnel. For example, gcloud compute start-iap-tunnel can start a tunnel to
Cloud Identity-Aware Proxy through which another process can create a
connection (e.g. SSH, RDP) to a Google Compute Engine instance. Client
certificate authorization is supported in tunnel creation.

[Official reference](https://cloud.google.com/sdk/gcloud/reference/topic/client-certificate)

---
### `gcloud topic command-conventions`

Gcloud command conventions supplementary help

  gcloud command design follows a common set of principles and conventions.
  This document describes them in detail.

  Conventions are goals more than rules. Refer to individual command --help
  for any exceptions.

Command Hierarchy
  gcloud commands are organized as a tree with gcloud at the root, command
  groups in the inner nodes, and commands at the leaf nodes. Each command
  group typically contains a set of CRUD commands (create, describe, list,
  update, delete) that operate on a resource for a single API. Group commands
  are executable, but only for displaying help.

  All groups and commands have a --help flag that displays a man(1) style
  document on the standard output. The display is run through the default
  pager if the calling environment specifies one. Help documents are derived
  from the running executable, so they are always up to date, even when
  switching between multiple release installations.

Command Line
  Every gcloud command line follows the same form:

      gcloud GROUP GROUP ... COMMAND POSITIONAL ... FLAG ...

  Flag and positional arguments can be intermixed but for consistency are
  usually displayed positionals first in order, followed by flags in any
  order.

Command Usage Notation
  Command usage is a shorthand notation that contains the full command name,
  the positional arguments, and the flag arguments in group sorted order.
  Optional arguments are enclosed in [ ... ]. For example:

      gcloud foo bar NAME [EXTRA] [--format=FORMAT]

  is the usage for the gcloud foo bar command with a required NAME positional
  argument, an optional EXTRA positional argument, and an optional --format
  flag argument.

  Mutually exclusive arguments are separated by |; at most one arg in the
  list of mutually exclusive args may be specified:

      [ --foo | --bar ]

  This means that either --foo or --bar may be specified, but not both.

  Mutually exclusive args may also be required, meaning exactly one arg in
  the list must be specified. This is denoted by enclosing the args in ( ...
  ):

      ( --foo | --bar )

  Modal argument groups are also supported. If any arg in the group is
  specified, then the modal arguments must also be specified. This is denoted
  by using : to separate the modal args on the left from the other args on
  the right:

      [ --must-a --must-b : --maybe-c --maybe-d ]

  This means that if --maybe-c and/or --maybe-d are specified then both
  --must-a and --must-b must be specified.

Positional Arguments
  Positional arguments are ordered and must be specified in the order listed
  in the command usage and help document argument definition list.

  File input arguments usually accept the special name - to mean read from
  the standard input. This can be used only once per command line.

Flag Arguments
  Flag names are lower case with a -- prefix. Multi-word flags use - (dash)
  as a word separator. Single character flags are deprecated, rare and may
  not be documented at all.

  Following UNIX convention, if a flag is repeated on the command line, then
  only the rightmost occurrence takes effect, no diagnostic is emitted. This
  makes it easy to set up command aliases and wrapper scripts that provide
  default flag values; values that can easily be overridden by specifying
  them on the alias or wrapper script command line.

Boolean Flags
  Boolean flags have an implied value of false or true. The presence of --foo
  sets the flag to true. All Boolean flags have a --no- prefix variant. For
  example, --no-foo sets the Boolean --foo flag to false. Boolean flags are
  documented using the positive form. This keeps the style consistent across
  all commands, and also makes the meaning of the --no- variant clear. In the
  case a Boolean flag has a default value of true, the --no- variant will
  appear in the command usage and help text and like all other --no- flags,
  will set the value of the flag to false.

Valued Flags
  Non-Boolean flags have an explicit value. The value can be specified using
  =:

      --flag=value

  or by placing the value as the next arg after the flag:

      --flag value

  The = form must be used if value starts with -.

  The second form requires extra context to determine if --flag is Boolean
  and value is a positional, or if --flag is valued and value is its value.
  Because of the visual ambiguity, usage notation and most command examples
  use the first form to make intentions clear. The = form also has a
  diagnostic bonus: it is an error to specify a value for a Boolean flag.

Complex Flag Values
  Complex flag values that contain command interpreter special characters may
  be difficult to specify on the command line. The --flags-file=YAML-FILE
  flag solves this problem by allowing command line flags to be specified in
  a YAML/JSON file. String, numeric, list and dict flag values are specified
  using YAML/JSON notation and quoting rules. See $ gcloud topic flags-file
  for more information.

Output
  The standard output is for explicit information requested by the command.

  Depending on the context, there may be guarantees on the output format to
  support deterministic parsing. Certain commands do return resources and
  these resources are listed on standard output usually using either a
  command-specific table format or the default YAML format. Moreover, the
  --format flag can be used to change or configure these default output
  formats. yaml, json, and csv output --format values guarantee that
  successful command completion results in standard output data that can be
  parsed using the respective format. A detailed explanation of the
  capabilities of the --format flag can be found with $ gcloud topic formats.
  In the case of async commands, or commands run with --async, the resource
  returned on standard output is an operations resource. For commands that do
  not return resources, the output is defined in the command's --help.

  The standard error is reserved for diagnostics. In general, the format of
  standard error data may change from release to release. Users should not
  script against specific content, or even the existence of output to the
  standard error at all. The only reliable error indicator is the exit status
  described below.

  Most standard error messaging is also logged to a file that can be accessed
  by $ gcloud info --show-log.

  No gcloud command should crash with an uncaught exception. However, if
  gcloud does crash the stack trace is intercepted and written to the log
  file, and a crash diagnostic is written to the standard error.

Exit Status
  Exit status 0 indicates success. For async commands it indicates that the
  operation started successfully but may not have completed yet.

  Any other exit status indicates an error. Command-specific diagnostics
  should explain the nature of the error and how to correct it.

[Official reference](https://cloud.google.com/sdk/gcloud/reference/topic/command-conventions)

---
### `gcloud topic configurations`

Supplementary help for named configurations

    gcloud properties can be stored in named configurations, which are
    collections of key-value pairs that influence the behavior of gcloud.

    Named configurations are intended to be an advanced feature, and you can
    probably ignore them entirely if you only work with one project.

    Properties that are commonly stored in configurations include default
    Google Compute Engine zone, verbosity level, project ID, and active user or
    service account. Configurations allow you to define and enable these and
    other settings together as a group.

    Configuration data is typically stored in $HOME/.config/gcloud, you can
    override this location by setting the environment variable CLOUDSDK_CONFIG.
    This can be useful if $HOME points to a read only filesystem or you are
    running commands inside docker.

    Configurations are especially useful if you:
      o Work with multiple projects. You can create a separate configuration
        for each project.
      o Use multiple accounts, for example, a user account and a service
        account, etc.
      o Perform generally orthogonal tasks (work on an appengine app in
        project foo, administer a Google Compute Engine cluster in zone
        user-central-1a, manage the network configurations for region
        asia-east-1, etc.)

    Property information stored in named configurations are readable by all
    gcloud commands and may be modified by gcloud config set and gcloud config
    unset.

Creating configurations

    Named configurations may be defined by users or built into gcloud.

    User defined configurations have lowercase names, such as 'johndoe',
    'default', 'jeff-staging', or 'foo2'. These are defined by the following
    regular expression: ^[a-z][-a-z0-9]*$

    Additionally there is a builtin configuration named NONE that has no
    properties set.

    The easiest way to create a brand new configuration is by running

        $ gcloud init

    This will guide you through setting up your first named configuration,
    creating a new named configuration, or reinitializing an existing named
    configuration. (Note: reinitializing an existing configuration will remove
    all its existing properties!)

    You can create a new empty configuration with

        $ gcloud config configurations create my-config

Using configurations

    gcloud may have at most one active configuration which provides property
    values. Inactive configurations have no effect on gcloud executions.

    You can activate a configuration with

        $ gcloud config configurations activate my-config

    To display the path of the active configuration, run:

        $ gcloud info --format="get(config.paths.active_config_path)"

    Note that changes to your OS login, Google Cloud Platform account or
    project could change the path.

    You can view and change the properties of your active configuration using
    the following commands:

        $ gcloud config list
        $ gcloud config set

    Additionally, commands under gcloud config configurations allow you to to
    list, activate, describe, and delete configurations that may or may not be
    active.

    You can activate a configuration for a single gcloud invocation using flag,
    --configuration my-config, or environment variable
    CLOUDSDK_ACTIVE_CONFIG_NAME=my-config.

[Official reference](https://cloud.google.com/sdk/gcloud/reference/topic/configurations)

---
### `gcloud topic datetimes`

Date/time input format supplementary help

  gcloud command line flags and filter expressions that expect date/time
  string values support common input formats. These formats fall into two
  main categories: absolute date/times and relative durations.

Absolute date/time formats
  Absolute date/time input formats minimally support ISO 8601
  (https://en.wikipedia.org/wiki/ISO_8601) and RFC 822
  (https://www.rfc-editor.org/rfc/rfc0822.txt) date/times. When omitted the
  date/time value defaults are:

    o year, month, day - current value
    o hour, minute, second, fractional second - 0

  The supported absolute date/time input formats are listed here.

  ISO 8601 / RFC 3339 zulu:

      2003-09-25T10:49:41.519Z
      2003-09-25T10:49:41Z

  ISO 8601 numeric timezone offset:

      2003-09-25T10:49:41.5-0000
      2003-09-25T10:49:41.5-03:00
      2003-09-25T10:49:41.5+0300

  ISO with omitted parts:

      2003-09-25T10:49:41
      2003-09-25T10:49
      2003-09-25T10
      2003-09-25

  RFC 822:

      Thu, 25 Sep 2003 10:49:41 -0300

  UNIX date command, explicit timezone:

      Thu Sep 25 10:36:28 EDT 2003
      2003 10:36:28 EDT 25 Sep Thu

  local timezone:

      Thu Sep 25 10:36:28 2003

  omitted parts (date parts default to the current date, time parts default
  to 0):

      Thu Sep 25 10:36:28
      Thu Sep 10:36:28
      Thu 10:36:28
      Thu 10:36
      10:36

  omitted parts with different order:

      Thu Sep 25 2003
      Sep 25 2003
      Sep 2003
      Sep
      2003

  ISO no separators:

      20030925T104941.5-0300
      20030925T104941-0300
      20030925T104941
      20030925T1049
      20030925T10
      20030925

  no T separator:

      20030925104941
      200309251049

  other date orderings:

      2003-09-25
      2003-Sep-25
      25-Sep-2003
      Sep-25-2003
      09-25-2003

  other date separators:

      2003.Sep.25
      2003/09/25
      2003 Sep 25
      2003 09 25

Relative duration date/time formats
  A relative duration specifies a date/time relative to the current time.
  Relative durations are based on ISO 8601 durations
  (https://en.wikipedia.org/wiki/ISO_8601#Durations). They are
  case-insensitive and must be prefixed with +P or -P.

  A fully qualified duration string contains year, month, day, hour, minute,
  second, and fractional second parts. Each part is a number followed by a
  single character suffix:

    o P - period (the duration designator)
    o Y - year
    o M - minute if after T or H, month otherwise
    o D - day
    o T - separates date parts from time parts
    o H - hour
    o M - minute if after T or H, month otherwise
    o S - second (for fractional seconds, use decimal value for seconds)

  At least one part must be specified. Omitted parts default to 0.

      -P1Y2M3DT4H5M6.7S
      +p1y2m3dT4h5m6.7s

  A relative duration may be used in any context that expects a date/time
  string.

  For example:

    o 1 month ago: -p1m
    o 30 minutes from now: +pt30m
    o 2 hours and 30 minutes ago: -p2h30m

Absolute duration formats
  An absolute duration specifies a period of time. It has the same syntax as
  a relative duration except that there is no leading + or -, and the leading
  P is optional.

  For example:

    o 1 month: 1m
    o 1 hour 30 minutes: 1h30m
    o 30 minutes: t30m

[Official reference](https://cloud.google.com/sdk/gcloud/reference/topic/datetimes)

---
### `gcloud topic endpoint-override`

Gcloud endpoint override supplementary help

    Use API endpoint overrides to override the API endpoints used by the gcloud
    CLI. Applications such as Private Google Access and Private Service Connect
    use API endpoint overrides.

Setting API endpoint overrides

    gcloud API endpoints are defined as gcloud CLI properties and can be
    overridden through gcloud CLI properties or environment variables. For
    example, to override the API endpoint for the gcloud storage command to use
    the private storage-vialink1.p.googleapis.com endpoint with either http://
    or https:// prefix, you can use one of the following commands:

        # Override using a property:
        $ gcloud config set api_endpoint_overrides/storage \
            https://storage-vialink1.p.googleapis.com/

        # Override using an environment variable
        $ \
            CLOUDSDK_API_ENDPOINT_OVERRIDES_STORAGE=https://\
        storage-vialink1.p.googleapis.com/
        gcloud storage objects list gs://my-bucket

Default API endpoints

    To get the default value for an API endpoint override, use gcloud config
    get to determine the correct format for your API endpoint override:

        $ gcloud config get api_endpoint_overrides/storage

Unsetting API endpoint overrides

    To unset an API endpoint override, use gcloud config unset:

        $ gcloud config unset api_endpoint_overrides/storage

Configured API endpoint overrides

    To see the APIs which have an endpoint override set, use gcloud config
    list:

        $ gcloud config list api_endpoint_overrides/

    To see all the set and unset API endpoint override properties, use the
    --all flag:

        $ gcloud config list api_endpoint_overrides/ --all

[Official reference](https://cloud.google.com/sdk/gcloud/reference/topic/endpoint-override)

---
### `gcloud topic escaping`

List/dictionary-type argument escaping supplementary help

List/dictionary-type argument escaping supplementary help.

gcloud supports list-type and dictionary-type flags that take one argument
which is a list of one or more comma-separated items:

    --list-flag=value1,value2,value3

    --dict-flag=key1=value1,key2=value2

In the case of a dict-type flag, each item is a key-value pair separated by
'='. If more than one '=' is present, the first is used.

In order to include commas in your arguments, specify an alternate
delimiter using the following syntax:

    ^DELIM^flag value, with comma

where DELIM is a sequence of one or more characters that may not appear in
any value in the list.

NOTE: In cmd.exe and PowerShell on Windows, ^ is a special character and
you must escape it by repeating it. In the following examples, every time
you see ^, replace it with ^^^^.

**Examples:**
```bash
In these examples, a list-type or dictionary-type flag is given, along with
a shell comment explaining how it is parsed. The parsed flags are shown
here using Python-style list or dict formats (in other languages, what
Python calls "dicts" are often called "associative arrays," "maps," or
"hashes").

Basic example:

    --list-flag=^:^a,b:c,d # => ['a,b', 'c,d']

Multi-character delimiters are allowed:

    --list-flag=^--^a-,b--c # => ['a-,b', 'c']

Just one '^' has no special meaning:

    --list-flag=^a,b,c # => ['^a', 'b', 'c']

This is an alternative way of starting with '^':

    --list-flag=^,^^a,b,c # => ['^a', 'b', 'c']

A '^' anywhere but the start has no special meaning:

    --list-flag=a^:^,b,c # => ['a^:^', 'b', 'c']

Dictionary-type arguments work exactly the same as list-type arguments:

    --dict-flag=^:^a=b,c:d=f,g # => {'a': 'b,c', 'd': 'f,g'}

To reserve ephemeral IP addresses, passed in as a list, which are being
used by virtual machine instances in the us-central1 region, run:

    $ gcloud compute addresses create \
      --addresses ^:^123.456.789.198:22.333.146.189:789.312.645 \
      --region us-central1

To create a Google Compute Engine virtual machine instance with metadata as
a list ({'key1': '"value1"', 'key2': 'value2', 'key3':
'value3Index1,value3Index2', 'key4': 'value4'), run:

    $ gcloud compute instances create example-instance1 \
      --metadata \
      ^:^key1="value1":key2=value2:key3=value3Index1,value3Index2,\
    valueIndex3:key4=value4
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/topic/escaping)

---
### `gcloud topic filters`

Resource filters supplementary help

  Most gcloud commands return a list of resources on success. By default they
  are pretty-printed on the standard output. The
  --format=NAME[ATTRIBUTES](PROJECTION) and --filter=EXPRESSION flags along
  with projections can be used to format and change the default output to a
  more meaningful result.

  Use the --format flag to change the default output format of a command. For
  details run $ gcloud topic formats.

  Use the --filter flag to select resources to be listed. Resource filters
  are described in detail below.

  Use resource-keys to reach resource items through a unique path of names
  from the root. For details run $ gcloud topic resource-keys.

  Use projections to list a subset of resource keys in a resource. For
  details run $ gcloud topic projections.

  Note: To refer to a list of fields you can sort, filter, and format by for
  each resource, you can run a list command with the format set to text or
  json. For example, $ gcloud compute instances list --limit=1 --format=text.

  To work through an interactive tutorial about using the filter and format
  flags instead, see:
  https://console.cloud.google.com/cloudshell/open?git_repo=https://github.com/GoogleCloudPlatform/cloud-shell-tutorials&page=editor&tutorial=cloudsdk/tutorial.md

  Note: Depending on the specific server API, filtering may be done entirely
  by the client, entirely by the server, or by a combination of both.

Filter Expressions
  A filter expression is a Boolean function that selects the resources to
  print from a list of resources. Expressions are composed of terms connected
  by logic operators.

   LogicOperator
      Logic operators must be in uppercase: AND, OR, NOT. Additionally,
      expressions containing both AND and OR must be parenthesized to
      disambiguate precedence.

       NOT term-1
          True if term-1 is False, otherwise False.

       term-1 AND term-2
          True if both term-1 and term-2 are true.

       term-1 OR term-2
          True if at least one of term-1 or term-2 is true.

       term-1 term-2
          Term conjunction (implicit AND) is True if both term-1 and term-2
          are true. Conjunction has lower precedence than OR.

   Terms
      A term is a key operator value tuple, where key is a dotted name that
      evaluates to the value of a resource attribute, and value may be:

       number
          integer or floating point numeric constant

       unquoted literal
          character sequence terminated by space, ( or )

       quoted literal
          "..." or '...'

          Most filter expressions need to be quoted in shell commands. If you
          use '...' shell quotes then use "..." filter string literal quotes
          and vice versa.

      Quoted literals will be interpreted as string values, even when the
      value could also be a valid number. For example, 'key:1e9' will be
      interpreted as a key named 'key' with the string value '1e9', rather
      than with the float value of one billion expressed in scientific
      notation.

   Operator Terms
       key : simple-pattern
          : operator evaluation is changing for consistency across Google
          APIs. The current default is deprecated and will be dropped
          shortly. A warning will be displayed when a --filter expression
          would return different matches using both the deprecated and new
          implementations.

          The current deprecated default is True if key contains
          simple-pattern. The match is case insensitive. It allows one * that
          matches any sequence of 0 or more characters. If * is specified
          then the match is anchored, meaning all characters from the
          beginning and end of the value must match.

          The new implementation is True if simple-pattern matches any word
          in key. Words are locale specific but typically consist of
          alpha-numeric characters. Non-word characters that do not appear in
          simple-pattern are ignored. The matching is anchored and case
          insensitive. An optional trailing * does a word prefix match.

          Use key:* to test if key is defined and -key:* to test if key is
          undefined.

       key :( simple-pattern ... )
          True if key matches any simple-pattern in the (space, tab, newline,
          comma) separated list.

       key = value
          True if key is equal to value, or [deprecated] equivalent to : with
          the exception that the trailing * prefix match is not supported.

          For historical reasons, this operation currently behaves
          differently for different Google APIs. For many APIs, this is True
          if key is equal to value. For a few APIs, this is currently
          equivalent to :, with the exception that the trailing * prefix
          match is not supported. However, this behaviour is being phased
          out, and use of = for those APIs is deprecated; for those APIs, if
          you want matching, you should use : instead of =, and if you want
          to test for equality, you can use key <= value AND key >= value.

       key =( value ... )
          True if key is equal to any value in the (space, tab, newline, ,)
          separated list.

       key != value
          True if key is not value. Equivalent to -key=value and NOT
          key=value.

       key < value
          True if key is less than value. If both key and value are numeric
          then numeric comparison is used, otherwise lexicographic string
          comparison is used.

       key <= value
          True if key is less than or equal to value. If both key and value
          are numeric then numeric comparison is used, otherwise
          lexicographic string comparison is used.

       key >= value
          True if key is greater than or equal to value. If both key and
          value are numeric then numeric comparison is used, otherwise
          lexicographic string comparison is used.

       key > value
          True if key is greater than value. If both key and value are
          numeric then numeric comparison is used, otherwise lexicographic
          string comparison is used.

       key ~ value
          True if key contains a match for the RE (regular expression)
          pattern value. Depending on your shell, you might have to escape or
          quote ~ to ensure it isn't consumed as HOME.

       key !~ value
          True if key does not contain a match for the RE (regular
          expression) pattern value. Depending on your shell, you might have
          to escape or quote ~ to ensure it isn't consumed as HOME.

      Regular expressions are evaluated using Python's standard library:
      https://docs.python.org/3/library/re.html#re-syntax.

Determine which fields are available for filtering
  In order to build filters, it is often helpful to review some
  representative fields returned from commands. One simple way to do this is
  to add --format=yaml --limit=1 to a command. With these flags, a single
  record is returned and its full contents are displayed as a YAML document.
  For example, a list of project fields could be generated by running:

      $ gcloud projects list --format=yaml --limit=1

  This might display the following data:

      createTime: '2021-02-10T19:19:49.242Z'
      lifecycleState: ACTIVE
      name: MyProject
      parent:
        id: '123'
        type: folder
      projectId: my-project
      projectNumber: '456'

  Using this data, one way of filtering projects is by their parent's ID by
  specifying parent.id as the key.

Filter on a custom or nested list in response
  By default the filter expression operates on root level resources. In order
  to filter on a nested list(not at the root level of the json) , one can use
  the --flatten flag to provide a the resource-key to list. For example, To
  list members under my-project that have an editor role, one can run:

      $ gcloud projects get-iam-policy cloudsdktest --flatten=bindings \
          --filter=bindings.role:roles/editor \
          --format='value(bindings.members)'

**Examples:**
```bash
List all Google Compute Engine instance resources:

    $ gcloud compute instances list

List Compute Engine instance resources that have machineType f1-micro:

    $ gcloud compute instances list --filter="machineType:f1-micro"

List Compute Engine instance resources using a regular expression for zone
us and not MachineType f1-micro:

    $ gcloud compute instances list \
        --filter="zone ~ us AND -machineType:f1-micro"

List Compute Engine instance resources with tag my-tag:

    $ gcloud compute instances list --filter="tags.items=my-tag"

List Compute Engine instance resources with tag my-tag or my-other-tag:

    $ gcloud compute instances list \
        --filter="tags.items=(my-tag,my-other-tag)"

List Compute Engine instance resources with tag my-tag and my-other-tag:

    $ gcloud compute instances list \
        --filter="tags.items=my-tag AND tags.items=my-other-tag"

List Compute Engine instance resources which either have tag my-tag but not
my-other-tag or have tag alternative-tag:

    $ gcloud compute instances list \
        --filter="(tags.items=my-tag AND -tags.items=my-other-tag) OR \
    tags.items=alternative-tag"

List Compute Engine instance resources which contain the key fingerprint in
the metadata object:

    $ gcloud compute instances list --limit=1 \
        --filter="metadata.list(show="keys"):fingerprint"

List Compute Engine instance resources with label my-label with any value:

    $ gcloud compute instances list --filter="labels.my-label:*"

List Container Registry images that have a tag with the value '30e5504145':

    $ gcloud container images list-tags --filter="'tags:30e5504145'"

The last example encloses the filter expression in single quotes because
the value '30e5504145' could be interpreted as a number in scientific
notation.

List in JSON format those projects where the labels match specific values
(e.g. label.env is 'test' and label.version is alpha):

    $ gcloud projects list --format="json" \
        --filter="labels.env=test AND labels.version=alpha"

List projects that were created on and after a specific date:

    $ gcloud projects list \
        --format="table(projectNumber,projectId,createTime)" \
        --filter="createTime>=2018-01-15"

List projects that were created on and after a specific date and time and
sort from oldest to newest (with dates and times listed according to the
local timezone):

    $ gcloud projects list \
        --format="table(projectNumber,projectId,createTime.date(tz=LOCAL\
    ))" --filter="createTime>=2018-01-15T12:00:00" --sort-by=createTime

List projects that were created within the last two weeks, using ISO8601
durations:

    $ gcloud projects list \
        --format="table(projectNumber,projectId,createTime)" \
        --filter="createTime>-P2W"

For more about ISO8601 durations, see:
https://en.wikipedia.org/wiki/ISO_8601

The table below shows examples of pattern matching if used with the :
operator:

  PATTERN  VALUE        MATCHES  DEPRECATED_MATCHES
  abc*     abcpdqxyz    True     True
  abc      abcpdqxyz    False    True
  pdq*     abcpdqxyz    False    False
  pdq      abcpdqxyz    False    True
  xyz*     abcpdqxyz    False    False
  xyz      abcpdqxyz    False    True
  *        abcpdqxyz    True     True
  *        (None)       False    False
  *        ('')         False    False
  *        (otherwise)  True     True
  abc*     abc.pdq.xyz  True     True
  abc      abc.pdq.xyz  True     True
  abc.pdq  abc.pdq.xyz  True     True
  pdq*     abc.pdq.xyz  True     False
  pdq      abc.pdq.xyz  True     True
  pdq.xyz  abc.pdq.xyz  True     True
  xyz*     abc.pdq.xyz  True     False
  xyz      abc.pdq.xyz  True     True
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/topic/filters)

---
### `gcloud topic flags-file`

--flags-file=YAML_FILE supplementary help

The --flags-file=YAML-FILE flag, available to all gcloud commands, supports
complex flag values in any command interpreter.

Complex flag values that contain command interpreter special characters may
be difficult to specify on the command line. The combined list of special
characters across commonly used command interpreters (shell, cmd.exe,
PowerShell) is surprisingly large. Among them are ", ', `, *, ?, [, ], (,
), $, %, #, ^, &, |, {, }, ;, \, <, >, space, tab, newline. Add to that the
separator characters for list and dict valued flags, and it becomes all but
impossible to construct portable command lines.

The --flags-file=YAML-FILE flag solves this problem by allowing command
line flags to be specified in a YAML/JSON file. String, numeric, list and
dict flag values are specified using YAML/JSON notation and quoting rules.

Flag specification uses dictionary notation. Use a list of dictionaries for
flags that must be specified multiple times.

For example, this YAML file defines values for Boolean, integer, floating
point, string, dictionary and list valued flags:

        --boolean:
        --integer: 123
        --float: 456.789
        --string: A string value.
        --dictionary:
          a=b: c,d
          e,f: g=h
          i: none
          j=k=l: m=$n,o=%p
          "y:": ":z"
          meta:
          - key: foo
            value: bar
          - key: abc
            value: xyz
        --list:
          - a,b,c
          - x,y,z

If the file is named my-flags.yaml then the command line flag
--flags-file=my-flags.yaml will set the specified flags on any system using
any command interpreter. --flags-file may be specified in a YAML file, and
its value can be a YAML list to reference multiple files.

This example specifies the --metadata flag multiple times:

        - --metadata: abc
          --integer: 123
        - --metadata: xyz

Each --flags-file arg is replaced by its contents, so normal flag
precedence applies. For example, given flags-1.yaml:

        --zone: us-east2-a

flags-2.yaml:

        --verbosity: info
        --zone: us-central1-a

and command line:

        gcloud compute instances describe \
            --flags-file=flags-1.yaml my-instance --flags-file=flags-2.yaml

the effective command line is:

        gcloud compute instances describe \
            --zone=us-east2-a my-instance --verbosity=info --zone=us-central1-a

using zone us-central1-a (not us-east2-a, because flags-2.yaml, to the
right of flags-1.yaml, has higher precedence).

[Official reference](https://cloud.google.com/sdk/gcloud/reference/topic/flags-file)

---
### `gcloud topic formats`

Resource formats supplementary help

  Most gcloud commands return a list of resources on success. By default they
  are pretty-printed on the standard output. The
  --format=NAME[ATTRIBUTES](PROJECTION) and --filter=EXPRESSION flags along
  with projections can be used to format and change the default output to a
  more meaningful result.

  Use the --format flag to change the default output format of a command.
  Resource formats are described in detail below.

  Use the --filter flag to select resources to be listed. For details run $
  gcloud topic filters.

  Use resource-keys to reach resource items through a unique path of names
  from the root. For details run $ gcloud topic resource-keys.

  Use projections to list a subset of resource keys in a resource. For
  details run $ gcloud topic projections.

  Note: To refer to a list of fields you can sort, filter, and format by for
  each resource, you can run a list command with the format set to text or
  json. For example, $ gcloud compute instances list --limit=1 --format=text.

  To work through an interactive tutorial about using the filter and format
  flags instead, see:
  https://console.cloud.google.com/cloudshell/open?git_repo=https://github.com/GoogleCloudPlatform/cloud-shell-tutorials&page=editor&tutorial=cloudsdk/tutorial.md

Formats
  A format expression is used to change the default output format of a
  command. Many output formats are available; some for pretty printing
  human-readable output and others for returning machine-readable output.

  A format expression has 3 parts:

   NAME
      name
   ATTRIBUTES
      [ [no-]attribute-name[=value] [, ... ] ]
   PROJECTION
      ( resource-key [, ...] )

  NAME is required, ATTRIBUTES are optional, and PROJECTIONS may be required
  for some formats. Unknown attribute names are silently ignored.

  Each gcloud list command has a default format expression. The --format flag
  can alter or replace the default. For example,

      --format="[box]"

  adds box decorations to a default table, and

      --format=json

  lists the resource in json format.

  The formats and format specific attributes are:

   config
      A dictionary of dictionaries in config style.

      The format attributes are:

       export
          Display the dictionary as a list of system specific environment
          export commands.
       unset
          Display the dictionary as a list of system specific environment
          unset commands.

   csv
      Comma Separated Values (http://www.rfc-editor.org/rfc/rfc4180.txt) with
      no keys. This format requires a projection to define the values to be
      printed.

      To use \n or \t as an attribute value please escape the \ with your
      shell's escape sequence, example separator="\\n" for bash.

      The format attributes are:

       delimiter="string"
          The string printed between list value items, default ";".
       no-heading
          Disables the initial key name heading record.
       separator="string"
          The string printed between values, default ",".
       terminator="string"
          The string printed after each record, default "\n" (newline).

   default
      An alias for the yaml format. To override use gcloud config set
      core/default_format property.

   diff
      A unified diff of the first two projection columns.

      The format attributes are:

       format
          The format of the diffed resources. Each resource is converted to
          this format and the diff of the converted resources is displayed.
          The default is 'flattened'.

   disable
      Disables formatted output and does not consume the resources.
      Equivalent to the none format, but also short-circuits early for
      commands that return pageable lists.

   flattened
      A flattened tree. Each output line contains one key:value pair.

      The format attributes are:

       no-pad
          Don't print space after the separator. The default adjusts the
          space to align the values into the same output column. Use no-pad
          for comparing resource outputs.
       separator=SEPARATOR
          Print SEPARATOR between the key and value. The default is ": ".

   get
      Equivalent to the value[no-transforms] format. Default transforms are
      not applied to the displayed values.

   json
      JSON (http://www.json.org), JavaScript Object Notation.

      The format attributes are:

       no-undefined
          Does not display resource data items with null values.

   list
      An ordered list of items.

      The format attributes are:

       always-display-title
          Display the title even if there are no records.
       compact
          Display all items in a record on one line.

   multi
      Each projection key must have a subformat defined by the
      :format=FORMAT-STRING attribute. For example,

          `--format="multi(data:format=json, info:format='table[box](a, b, c)')"`

      formats the data field as JSON and the info field as a boxed table.

      The format attributes are:

       separator
          Separator string to print between each format. If multiple
          resources are provided, the separator is also printed between each
          resource.

   none
      Disables formatted output and consumes the resources.

   object
      Bypasses JSON-serialization and prints the object representation of
      each resource.

      The format attributes are:

       separator
          The line printed between resources.
       terminator
          The line printed after each resource.

   table
      Aligned left-adjusted columns with optional title, column headings and
      sorting. This format requires a projection to define the table columns.
      The default column headings are the disambiguated right hand components
      of the column keys in ANGRY_SNAKE_CASE. For example, the projection
      keys (first.name, last.name) produce the default column heading
      ('NAME', 'LAST_NAME').

      If --page-size=N is specified then output is grouped into tables with
      at most N rows. Headings, alignment and sorting are done per-page. The
      title, if any, is printed before the first table.

      If screen reader option is True, you may observe flattened list output
      instead of a table with columns. Please refer to $ gcloud topic
      accessibility to turn it off.

      The format attributes are:

       all-box
          Prints a box around the entire table and each cell, including the
          title if any.
       box
          Prints a box around the entire table and the title cells if any.
       format=FORMAT-STRING
          Prints the key data indented by 4 spaces using FORMAT-STRING which
          can reference any of the supported formats.
       no-heading
          Disables the column headings.
       margin=N
          Right hand side padding when one or more columns are wrapped.
       pad=N
          Sets the column horizontal pad to N spaces. The default is 1 for
          box, 2 otherwise.
       title=TITLE
          Prints a centered TITLE at the top of the table, within the table
          box if box is enabled.

   text
      An alias for the flattened format.

   value
      CSV with no heading and <TAB> separator instead of <COMMA>. Used to
      retrieve individual resource values. This format requires a projection
      to define the value(s) to be printed.

      To use \n or \t as an attribute value please escape the \ with your
      shell's escape sequence, example separator="\\n" for bash.

      The format attributes are:

       delimiter="string"
          The string printed between list value items, default ";".
       quote
          "..." quote values that contain delimiter, separator or terminator
          strings.
       separator="string"
          The string printed between values, default "\t" (tab).
       terminator="string"
          The string printed after each record, default "\n" (newline).

   yaml
      YAML (http://www.yaml.org), YAML ain't markup language.

      The format attributes are:

       null="string"
          Display string instead of null for null/None values.
       no-undefined
          Does not display resource data items with null values.
       version=VERSION
          Prints using the specified YAML version, default 1.2.

  All formats have these attributes:

   disable
      Disables formatted output and does not consume the resources.
   json-decode
      Decodes string values that are JSON compact encodings of list and
      dictionary objects. This may become the default.
   pager
      If True, sends output to a pager.
   private
      Disables log file output. Use this for sensitive resource data that
      should not be displayed in log files. Explicit command line IO
      redirection overrides this attribute.
   transforms
      Apply projection transforms to the resource values. The default is
      format specific; table-like formats may define default transforms to
      certain columns. Use no-transforms to disable.

**Examples:**
```bash
List a table of compute instance resources sorted by name with box
decorations and title Instances:

    $ gcloud compute instances list \
        --format="table[box,title=Instances](name:sort=1, \
    zone:label=zone, status)"

List a nested table of the quotas of a region:

    $ gcloud compute regions describe us-central1 \
        --format="table(quotas:format='table(metric,limit,usage)')"

Print a flattened list of global quotas in CSV format:

    $ gcloud compute project-info describe --flatten="quotas[]" \
        --format="csv(quotas.metric,quotas.limit,quotas.usage)"

List the disk interfaces for all compute instances as a compact comma
separated list:

    $ gcloud compute instances list \
        --format="value(disks[].interface.list())"

List the URIs for all compute instances:

    $ gcloud compute instances list --format="value(uri())"

List all compute instances with their creation timestamps displayed
according to the local timezone:

    $ gcloud compute instances list \
        --format="table(name,creationTimestamp.date(tz=LOCAL))"

List the project authenticated user email address:

    $ gcloud info --format="value(config.account)"

List resources filtered on repeated fields by projecting subfields on a
repeated message:

    $ gcloud alpha genomics readgroupsets list \
        --format="default(readGroups[].name)"

Return the scope of the current instance:

    $ gcloud compute zones list --format="value(selfLink.scope())"

selfLink is a fully qualified name. (e.g.
'https://www.googleapis.com/compute/v1/projects/my-project/zones/us-central1-a')
The previous example returns a list of just the names of each zone (e.g.
'us-central1-a'). This is because selfLink.scope() grabs the last part of
the URL segment. To extract selfLink starting from /projects and return the
scope of the current instance:

    $ gcloud compute zones list \
        --format="value(selfLink.scope(projects))"

List all scopes enabled for a Compute Engine instance and flatten the
multi-valued resource:

    $ gcloud compute instances list \
        --format="flattened(name,serviceAccounts[].email,serviceAccounts\
    [].scopes[].basename())"

Display a multi-valued resource's service account keys with the
corresponding service account, extracting just the first '/' delimited part
with segment(0):

    $ gcloud iam service-accounts keys list \
        --iam-account=svc-2-123@test-minutia-123.iam.gserviceaccount.com\
     --project=test-minutia-123 \
        --format="table(name.scope(serviceAccounts).segment(0):label='se\
    rvice Account',name.scope(keys):label='keyID',validAfterTime)"

The last example returns a table with service account names without their
full paths, keyID and validity.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/topic/formats)

---
### `gcloud topic gcloudignore`

Reference for .gcloudignore files

Several commands in gcloud involve uploading the contents of a directory to
Google Cloud to host or build. In many cases, you will not want to upload
certain files (i.e., "ignore" them).

If there is a file called .gcloudignore within the top-level directory
being uploaded, the files that it specifies (see "SYNTAX") will be ignored.

Gcloud commands may generate a .gcloudignore file; see the individual
command help page for details.

The following gcloud commands respect the .gcloudignore file:

  o gcloud app deploy
    * Note: If you add app.yaml to the .gcloudignore file, this command
      will fail.
  o gcloud functions deploy
  o gcloud builds submit
  o gcloud composer environments storage {dags, data, plugins} import
  o gcloud container builds submit
  o gcloud run deploy
  o gcloud run jobs deploy
  o gcloud alpha deploy releases create
  o gcloud infra-manager deployments apply
  o gcloud infra-manager previews create
  o gcloud alpha functions local deploy
  o gcloud alpha run jobs deploy
  o gcloud beta run jobs deploy
  o gcloud alpha run worker-pools deploy
  o gcloud beta run worker-pools deploy

To globally disable .gcloudignore parsing (including default file-ignore
behavior), run:

    $ gcloud config set gcloudignore/enabled false

The default content of the generated .gcloudignore file, which can be
overridden with --ignore-file, is as follows:

    .gcloudignore
    .git
    .gitignore

**Examples:**
```bash
This .gcloudignore would prevent the upload of the node_modules/ directory
and any files ending in ~:

    /node_modules/
    *~

This .gcloudignore (similar to the one generated when Git files are
present) would prevent the upload of the .gcloudignore file, the .git
directory, and any files in ignored in the .gitignore file:

    .gcloudignore
    # If you would like to upload your .git directory, .gitignore file or
    # files from your .gitignore file, remove the corresponding line below:
    .git
    .gitignore
    #!include:.gitignore
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/topic/gcloudignore)

---
### `gcloud topic offline-help`

Setting up gcloud command offline help

  There are many ways to access gcloud command help. Only the first requires
  online access:

    o Browse https://cloud.google.com/sdk/gcloud/reference/ for the most
      recent Google Cloud CLI release online documents.

    o Add the --help flag to any command. This will render a man style
      document in a terminal pager. The document is always up to date with
      the command because it is generated by collating help text from the
      command itself.

    o Use the gcloud beta interactive shell which has as-you-type help.
      Like --help, the interactive help documents are always up to date with
      the gcloud installation.

    o Generate HTML documents in a local directory and point your browser
      to the generated index.html for offline browsing. Hover over a
      navigation item to focus the menu, hover to the left to expand it
      again. More details on this below.

    o Generate and install man(1) style documents on a local host. More
      details on this below.

  All of these methods have the same content, all generated from a Google
  Cloud CLI gcloud installation. The last two are user maintained and can
  become out of date. Either use them for one time offline access, or make
  them part of your Google Cloud CLI installation/update routine.

Generating offline HTML documents
  To generate HTML documents for offline browsing:

      # Select an empty directory where the HTML and supporting *.css* and
      # *.js* files will be generated.
      HTML_DIR=<some-local-directory>

      # Generate the HTML in $HTML_DIR.
      # Should take ~1 min, 10 min or more on slower systems.
      gcloud meta generate-help-docs --html-dir=$HTML_DIR

  Then enter this URL in the browser address/search bar, where $HTML_DIR must
  be the actual path name of the directory:

      file://$HTML_DIR/index.html

Generating offline manpage documents
  To generate man page documents for the man(1) command:

      # Select an empty directory where the man page files will be generated.
      MANPAGE_DIR=<some-local-directory>

      # Generate the man pages in $MANPAGE_DIR.
      # Should take ~1 min, 10 min or more on slower systems.
      gcloud meta generate-help-docs --manpage-dir=$MANPAGE_DIR

      # Append $MANPAGE_DIR to the MANPATH environment variable:
      export MANPATH=$MANPATH:$MANPAGE_dir

  Then run the man command on gcloud manpages:

      man gcloud info

[Official reference](https://cloud.google.com/sdk/gcloud/reference/topic/offline-help)

---
### `gcloud topic projections`

Resource projections supplementary help

  Most gcloud commands return a list of resources on success. By default they
  are pretty-printed on the standard output. The
  --format=NAME[ATTRIBUTES](PROJECTION) and --filter=EXPRESSION flags along
  with projections can be used to format and change the default output to a
  more meaningful result.

  Use the --format flag to change the default output format of a command. For
  details run $ gcloud topic formats.

  Use the --filter flag to select resources to be listed. For details run $
  gcloud topic filters.

  Use resource-keys to reach resource items through a unique path of names
  from the root. For details run $ gcloud topic resource-keys.

  Use projections to list a subset of resource keys in a resource. Resource
  projections are described in detail below.

  Note: To refer to a list of fields you can sort, filter, and format by for
  each resource, you can run a list command with the format set to text or
  json. For example, $ gcloud compute instances list --limit=1 --format=text.

  To work through an interactive tutorial about using the filter and format
  flags instead, see:
  https://console.cloud.google.com/cloudshell/open?git_repo=https://github.com/GoogleCloudPlatform/cloud-shell-tutorials&page=editor&tutorial=cloudsdk/tutorial.md

Projections
  A projection is a list of keys that selects resource data values.
  Projections are used in --format flag expressions. For example, the table
  format requires a projection that describes the table columns:

      table(name, network.ip.internal, network.ip.external, uri())

Transforms
  A transform formats resource data values. Each projection key may have zero
  or more transform calls:

      _key_._transform_([arg...])...

  This example applies the foo() and then the bar() transform to the
  status.time resource value:

      (name, status.time.foo().bar())

  The builtin transform functions are:

   always()
      Marks a transform sequence to always be applied.

      In some cases transforms are disabled. Prepending always() to a
      transform sequence causes the sequence to always be evaluated.

      For example:

       some_field.always().foo().bar()
          Always applies foo() and then bar().

   basename(undefined="")
      Returns the last path component.

      The arguments are:

       undefined
          Returns this value if the resource or basename is empty.

   collection(undefined="")
      Returns the current resource collection.

      The arguments are:

       undefined
          This value is returned if r or the collection is empty.

   color(red, yellow, green, blue)
      Colorizes the resource string value.

      The red, yellow, green and blue args are RE patterns, matched against
      the resource in order. The first pattern that matches colorizes the
      matched substring with that color, and the other patterns are skipped.

      The arguments are:

       red
          The substring pattern for the color red.
       yellow
          The substring pattern for the color yellow.
       green
          The substring pattern for the color green.
       blue
          The substring pattern for the color blue.

      For example:

       color(red=STOP,yellow=CAUTION,green=GO)
          For the resource string "CAUTION means GO FASTER" displays the
          substring "CAUTION" in yellow.

   count()
      Counts the number of each item in the list.

      A string resource is treated as a list of characters.

      For example:

      "b/a/b/c".split("/").count() returns {a: 1, b: 2, c: 1}.

   date(format="%Y-%m-%dT%H:%M:%S", unit=1, undefined="", tz, tz_default)
      Formats the resource as a strftime() format.

      The arguments are:

       format
          The strftime(3) format.
       unit
          If the resource is a Timestamp then divide by unit to yield
          seconds.
       undefined
          Returns this value if the resource is not a valid time.
       tz
          Return the time relative to the tz timezone if specified, the
          explicit timezone in the resource if it has one, otherwise the
          local timezone. For example: date(tz=EST5EDT, tz_default=UTC).
       tz_default
          The default timezone if the resource does not have a timezone
          suffix.

   decode(encoding, undefined="")
      Returns the decoded value of the resource that was encoded by encoding.

      The arguments are:

       encoding
          The encoding name. base64 and utf-8 are supported.
       undefined
          Returns this value if the decoding fails.

   duration(start="", end="", parts=3, precision=3, calendar=true, unit=1, undefined="")
      Formats the resource as an ISO 8601 duration string.

      The ISO 8601 Duration
      (https://en.wikipedia.org/wiki/ISO_8601#Durations) format is:
      "[-]P[nY][nM][nD][T[nH][nM][n[.m]S]]". The 0 duration is "P0".
      Otherwise at least one part will always be displayed. Negative
      durations are prefixed by "-". "T" disambiguates months "P2M" to the
      left of "T" and minutes "PT5M" to the right.

      If the resource is a datetime then the duration of resource -
      current_time is returned.

      The arguments are:

       start
          The name of a start time attribute in the resource. The duration of
          the end - start time attributes in resource is returned. If end is
          not specified then the current time is used.
       end
          The name of an end time attribute in the resource. Defaults to the
          current time if omitted. Ignored if start is not specified.
       parts
          Format at most this many duration parts starting with largest
          non-zero part.
       precision
          Format the last duration part with precision digits after the
          decimal point. Trailing "0" and "." are always stripped.
       calendar
          Allow time units larger than hours in formatted durations if true.
          Durations specifying hours or smaller units are exact across
          daylight savings time boundaries. On by default. Use calendar=false
          to disable. For example, if calendar=true then at the daylight
          savings boundary 2016-03-13T01:00:00 + P1D => 2016-03-14T01:00:00
          but 2016-03-13T01:00:00 + PT24H => 2016-03-14T03:00:00. Similarly,
          a +P1Y duration will be inexact but "calendar correct", yielding
          the same month and day number next year, even in leap years.
       unit
          Divide the resource numeric value by unit to yield seconds.
       undefined
          Returns this value if the resource is not a valid timestamp.

      For example:

       duration(start=createTime,end=updateTime)
          The duration from resource creation to the most recent update.
       updateTime.duration()
          The duration since the most recent resource update.

   encode(encoding, undefined="")
      Returns the encoded value of the resource using encoding.

      The arguments are:

       encoding
          The encoding name. base64 and utf-8 are supported.
       undefined
          Returns this value if the encoding fails.

   enum(enums, inverse=false, undefined="")
      Returns the enums dictionary description for the resource.

      The arguments are:

       enums
          The name of a message enum dictionary.
       inverse
          Do inverse lookup if true.
       undefined
          Returns this value if there is no matching enum description.

   error(message)
      Raises an Error exception that does not generate a stack trace.

      The arguments are:

       message
          An error message. If not specified then the resource is formatted
          as the error message.

   extract(keys)
      Extract a list of non-empty values for the specified resource keys.

      The arguments are:

       keys
          The list of keys in the resource whose non-empty values will be
          included in the result.

   fatal(message)
      Raises an InternalError exception that generates a stack trace.

      The arguments are:

       message
          An error message. If not specified then the resource is formatted
          as the error message.

   filter(expression)
      Selects elements of x that match the filter expression.

      The arguments are:

       expression
          The filter expression to apply to r.

      For example:

      x.filter("key:val") selects elements of x that have 'key' fields
      containing 'val'.

   firstof(keys)
      Returns the first non-empty attribute value for key in keys.

      The arguments are:

       keys
          Keys to check for resource attribute values,

      For example:

       x.firstof(bar_foo, barFoo, BarFoo, BAR_FOO)
          Checks x.bar_foo, x.barFoo, x.BarFoo, and x.BAR_FOO in order for
          the first non-empty value.

   flatten(show="", undefined="", separator=",")
      Formats nested dicts and/or lists into a compact comma separated list.

      The arguments are:

       show
          If show=keys then list dict keys; if show=values then list dict
          values; otherwise list dict key=value pairs.
       undefined
          Return this if the resource is empty.
       separator
          The list item separator string.

      For example:

       --format="table(field.map(2).list().map().list().list()"
          Expression with explicit flattening.
       --format="table(field.flatten()"
          Equivalent expression using .flatten().

   float(precision=6, spec, undefined="")
      Returns the string representation of a floating point number.

      One of these formats is used (1) ". precision spec" if spec is
      specified (2) ". precision" unless 1e-04 <= abs(number) < 1e+09 (3)
      ".1f" otherwise.

      The arguments are:

       precision
          The maximum number of digits before and after the decimal point.
       spec
          The printf(3) floating point format "e", "f" or "g" spec character.
       undefined
          Returns this value if the resource is not a float.

   format(fmt, args)
      Formats resource key values.

      The arguments are:

       fmt
          The format string with {0} ... {nargs-1} references to the resource
          attribute name arg values.
       args
          The resource attribute key expression to format. The printer
          projection symbols and aliases may be used in key expressions. If
          no args are specified then the resource is used as the arg list if
          it is a list, otherwise the resource is used as the only arg.

      For example:

       --format='value(format("{0:f.1}/{1:f.1}", q.CPU.default, q.CPU.limit))'
          Formats q.CPU.default and q.CPU.limit as floating point numbers.

   group(keys)
      Formats a [...] grouped list.

      Each group is enclosed in [...]. The first item separator is ':',
      subsequent separators are ','. [item1] [item1] ... [item1: item2] ...
      [item1: item2] [item1: item2, item3] ... [item1: item2, item3]

      The arguments are:

       keys
          Optional attribute keys to select from the list. Otherwise the
          string value of each list item is selected.

   if(expr)
      Disables the projection key if the flag name filter expr is false.

      The arguments are:

       expr
          A command flag filter name expression. See gcloud topic filters for
          details on filter expressions. The expression variables are flag
          names without the leading -- prefix and dashes replaced by
          underscores.

      For example:

       table(name, value.if(NOT short_format))
          Lists a value column if the --short-format command line flag is not
          specified.

   iso(undefined="T")
      Formats the resource to numeric ISO time format.

      The arguments are:

       undefined
          Returns this value if the resource does not have an isoformat()
          attribute.

   join(sep="/", undefined="")
      Joins the elements of the resource list by the value of sep.

      A string resource is treated as a list of characters.

      The arguments are:

       sep
          The separator value to use when joining.
       undefined
          Returns this value if the result after joining is empty.

      For example:

      "a/b/c/d".split("/").join("!") returns "a!b!c!d".

   len()
   Returns the length of the resource if it is non-empty, 0 otherwise.
   list(show="", undefined="", separator=",")
      Formats a dict or list into a compact comma separated list.

      The arguments are:

       show
          If show=keys then list dict keys; if show=values then list dict
          values; otherwise list dict key=value pairs.
       undefined
          Return this if the resource is empty.
       separator
          The list item separator string.

   lower()
   Returns r in lowercase.
   map(depth=1)
      Applies the next transform in the sequence to each resource list item.

      The arguments are:

       depth
          The list nesting depth.

      For example:

       list_field.map().foo().list()
          Applies foo() to each item in list_field and then list() to the
          resulting value to return a compact comma-separated list.
       list_field.*foo().list()
          * is shorthand for map().
       list_field.map().foo().map().bar()
          Applies foo() to each item in list_field and then bar() to each
          item in the resulting list.
       abc.xyz.map(2).foo()
          Applies foo() to each item in xyz[] for all items in abc[].
       abc.xyz.**foo()
          ** is shorthand for map(2).

   notnull()
   Remove null values from the resource list.
   regex(expression, does_match, nomatch="")
      Returns does_match or r itself if r matches expression, nomatch
      otherwise.

      The arguments are:

       expression
          expression to apply to r.
       does_match
          If the string matches expression then return does_match otherwise
          return the string itself if does_match is not defined.
       nomatch
          Returns this value if the string does not match expression.

   resolution(undefined="", transpose=false)
      Formats a human readable XY resolution.

      The arguments are:

       undefined
          Returns this value if a recognizable resolution was not found.
       transpose
          Returns the y/x resolution if true.

   scope(args)
      Gets the /args/ suffix from a URI.

      The arguments are:

       args
          Optional URI segment names. If not specified then 'regions',
          'zones' is assumed.

      For example:

      "http://abc/foo/projects/bar/xyz".scope("projects") returns "bar/xyz".

      "http://xyz/foo/regions/abc".scope() returns "abc".

   segment(index=-1, undefined="")
      Returns the index-th URI path segment.

      The arguments are:

       index
          The path segment index to return counting from 0.
       undefined
          Returns this value if the resource or segment index is empty.

   size(zero="0", precision=1, units_in, units_out, min=0)
      Formats a human readable size in bytes.

      The arguments are:

       zero
          Returns this if size==0. Ignored if None.
       precision
          The number of digits displayed after the decimal point.
       units_in
          A unit suffix (only the first character is checked) or unit size.
          The size is multiplied by this. The default is 1.0.
       units_out
          A unit suffix (only the first character is checked) or unit size.
          The size is divided by this. The default is 1.0.
       min
          Sizes < min will be listed as "< min".

   slice(op=":", undefined="")
      Returns a list slice specified by op.

      The op parameter consists of up to three colon-delimeted integers:
      start, end, and step. The parameter supports half-open ranges: start
      and end values can be omitted, representing the first and last
      positions of the resource respectively.

      The step value represents the increment between items in the resource
      included in the slice. A step of 2 results in a slice that contains
      every other item in the resource.

      Negative values for start and end indicate that the positons should
      start from the last position of the resource. A negative value for step
      indicates that the slice should contain items in reverse order.

      If op contains no colons, the slice consists of the single item at the
      specified position in the resource.

      The arguments are:

       op
          The slice operation.
       undefined
          Returns this value if the slice cannot be created, or the resulting
          slice is empty.

      For example:

      [1,2,3].slice(1:) returns [2,3].

      [1,2,3].slice(:2) returns [1,2].

      [1,2,3].slice(-1:) returns [3].

      [1,2,3].slice(: :-1) returns [3,2,1].

      [1,2,3].slice(1) returns [2].

   sort(attr="")
      Sorts the elements of the resource list by a given attribute (or
      itself).

      A string resource is treated as a list of characters.

      The arguments are:

       attr
          The optional field of an object or dict by which to sort.

      For example:

      "b/a/d/c".split("/").sort() returns [a, b, c, d].

   split(sep="/", undefined="")
      Splits a string by the value of sep.

      The arguments are:

       sep
          The separator value to use when splitting.
       undefined
          Returns this value if the result after splitting is empty.

      For example:

      "a/b/c/d".split() returns ["a", "b", "c", "d"].

   sub(pattern, replacement, count=0, ignorecase=true)
      Replaces a pattern matched in a string with the given replacement.

      Return the string obtained by replacing the leftmost non-overlapping
      occurrences of pattern in the string by replacement. If the pattern
      isn't found, then the original string is returned unchanged.

      The arguments are:

       pattern
          The regular expression pattern to match in r that we want to
          replace with something.
       replacement
          The value to substitute into whatever pattern is matched.
       count
          The max number of pattern occurrences to be replaced. Must be
          non-negative. If omitted or zero, all occurrences will be replaces.
       ignorecase
          Whether to perform case-insensitive matching.

      For example:

       table(field.sub(" there", ""))
          If the field string is "hey there" it will be displayed as "hey".

   synthesize(args)
      Synthesizes a new resource from the schema arguments.

      A list of tuple arguments controls the resource synthesis. Each tuple
      is a schema that defines the synthesis of one resource list item. Each
      schema item defines the synthesis of one synthesized_resource attribute
      from an original_resource attribute.

      There are three kinds of schema items:

       name:literal
          The value for the name attribute in the synthesized resource is the
          literal value.
       name=key
          The value for the name attribute in the synthesized_resource is the
          value of key in the original_resource.
       key
          All the attributes of the value of key in the original_resource are
          added to the attributes in the synthesized_resource.

      The arguments are:

       args
          The list of schema tuples.

      For example:

       This returns a list of two resource items
          synthesize((name:up, upInfo), (name:down, downInfo))
       If upInfo and downInfo serialize to
          {"foo": 1, "bar": "yes"}
       and
          {"foo": 0, "bar": "no"}
       then the synthesized resource list is
          [{"name": "up", "foo": 1, "bar": "yes"}, {"name": "down", "foo": 0,
          "bar": "no"}]
       This could then be displayed by a nested table using
          synthesize(...):format="table(name, foo, bar)"

   trailoff(character_limit, undefined="")
      Returns r if less than limit, else abbreviated r followed by ellipsis.

      The arguments are:

       character_limit
          An int. Max length of return string. Must be greater than 3 because
          ellipsis (3 chars) is appended to abridged strings.
       undefined
          A string. Return if r or character_limit is invalid.

   upper()
   Returns r in uppercase.
   uri(undefined=".")
      Gets the resource URI.

      The arguments are:

       undefined
          Returns this if a the URI for r cannot be determined.

   yesno(yes, no="No")
      Returns no if the resource is empty, yes or the resource itself
      otherwise.

      The arguments are:

       yes
          If the resource is not empty then returns yes or the resource
          itself if yes is not defined.
       no
          Returns this value if the resource is empty.

  The cloudbuild transform functions are:

   build_images(undefined="")
      Returns the formatted build results images.

      The arguments are:

       undefined
          Returns this value if the resource cannot be formatted.

   build_source(undefined="")
      Returns the formatted build source.

      The arguments are:

       undefined
          Returns this value if the resource cannot be formatted.

   result_duration(resource, undefined="")
      Returns the formatted result duration.

      The arguments are:

       resource
          JSON-serializable object.
       undefined
          Returns this value if the resource cannot be formatted.

   result_status(resource, undefined="")
      Returns the formatted result status.

      The arguments are:

       resource
          JSON-serializable object.
       undefined
          Returns this value if the resource cannot be formatted.

  The compute transform functions are:

   firewall_rule(undefined="")
      Returns a compact string describing a firewall rule.

      The compact string is a comma-separated list of PROTOCOL:PORT_RANGE
      items. If a particular protocol has no port ranges then only the
      protocol is listed.

      The arguments are:

       undefined
          Returns this value if the resource cannot be formatted.

   image_alias(undefined="")
      Returns a comma-separated list of alias names for an image.

      The arguments are:

       undefined
          Returns this value if the resource cannot be formatted.

   location(undefined="")
      Return the region or zone name.

      The arguments are:

       undefined
          Returns this value if the resource cannot be formatted.

   location_scope(undefined="")
      Return the location scope name, either region or zone.

      The arguments are:

       undefined
          Returns this value if the resource cannot be formatted.

   machine_type(undefined="")
      Return the formatted name for a machine type.

      The arguments are:

       undefined
          Returns this value if the resource cannot be formatted.

   name(undefined="")
      Returns a resource name from an URI.

      The arguments are:

       undefined
          Returns this value if the resource cannot be formatted.

   next_maintenance(undefined="")
      Returns the timestamps of the next scheduled maintenance.

      All timestamps are assumed to be ISO strings in the same timezone.

      The arguments are:

       undefined
          Returns this value if the resource cannot be formatted.

   operation_http_status(undefined="")
      Returns the HTTP response code of an operation.

      The arguments are:

       undefined
          Returns this value if there is no response code.

   org_firewall_rule(rule, undefined="")
      Returns a compact string describing an organization firewall rule.

      The compact string is a comma-separated list of PROTOCOL:PORT_RANGE
      items. If a particular protocol has no port ranges then only the
      protocol is listed.

      The arguments are:

       rule
          JSON-serializable object.
       undefined
          Returns this value if the resource cannot be formatted.

   project(undefined="")
      Returns a project name from a selfLink.

      The arguments are:

       undefined
          Returns this value if the resource cannot be formatted.

   quota(undefined="")
      Formats a quota as usage/limit.

      The arguments are:

       undefined
          Returns this value if the resource cannot be formatted.

   scoped_suffixes(uris, undefined="")
   Get just the scoped part of the object the uri refers to.
   status(undefined="")
      Returns the machine status with deprecation information if applicable.

      The arguments are:

       undefined
          Returns this value if the resource cannot be formatted.

   type_suffix(uri, undefined="")
   Get the type and the name of the object the uri refers to.
   vpn_tunnel_gateway(vpn_tunnel, undefined="")
      Returns the gateway for the specified VPN tunnel resource if
      applicable.

      The arguments are:

       vpn_tunnel
          JSON-serializable object of a VPN tunnel.
       undefined
          Returns this value if the resource cannot be formatted.

   zone(undefined="")
      Returns a zone name from a selfLink.

      The arguments are:

       undefined
          Returns this value if the resource cannot be formatted.

  The container transform functions are:

   master_version(undefined="")
      Returns the formatted master version.

      The arguments are:

       undefined
          Returns this value if the resource cannot be formatted.

  The debug transform functions are:

   full_status(undefined="UNKNOWN_ERROR")
      Returns a full description of the status of a logpoint or snapshot.

      Status will be one of ACTIVE, COMPLETED, or a verbose error
      description. If the status is an error, there will be additional
      information available in the status field of the object.

      The arguments are:

       undefined
          Returns this value if the resource is not a valid status.

      For example:

       --format="table(id, location, full_status())"
          Displays the full status in the third table problem.

   short_status(undefined="UNKNOWN_ERROR")
      Returns a short description of the status of a logpoint or snapshot.

      Status will be one of ACTIVE, COMPLETED, or a short error description.
      If the status is an error, there will be additional information
      available in the status field of the object.

      The arguments are:

       undefined
          Returns this value if the resource is not a valid status.

      For example:

       --format="table(id, location, short_status())"
          Displays the short status in the third table problem.

  The functions transform functions are:

   environments(data)
      Returns the supported environments for a runtime.

      The arguments are:

       data
          JSON-serializable Runtimes object.

   generation(data, undefined="-")
      Returns Cloud Functions product version.

      The arguments are:

       data
          JSON-serializable 1st and 2nd gen Functions objects.
       undefined
          Returns this value if the resource cannot be formatted.

   state(data, undefined="")
      Returns textual information about functions state.

      The arguments are:

       data
          JSON-serializable object.
       undefined
          Returns this value if the resource cannot be formatted.

   trigger(data, undefined="")
      Returns textual information about functions trigger.

      The arguments are:

       data
          JSON-serializable 1st and 2nd gen Functions objects.
       undefined
          Returns this value if the resource cannot be formatted.

  The runtime_config transform functions are:

   waiter_status(undefined="")
      Returns a short description of the status of a waiter or waiter
      operation.

      Status will be one of WAITING, SUCCESS, FAILURE, or TIMEOUT.

      The arguments are:

       undefined
          Returns this value if the resource status cannot be determined.

      For example:

       --format="table(name, status())"
          Displays the status in table column two.

Key Attributes
  Key attributes control formatted output. Each projection key may have zero
  or more attributes:

      _key_:_attribute_=_value_...

  where =value is omitted for Boolean attributes and no-attribute sets the
  attribute to false. Attribute values may appear in any order, but must be
  specified after any transform calls. The attributes are:

   alias=ALIAS-NAME
      Sets ALIAS-NAME as an alias for the projection key.

   align=ALIGNMENT
      Specifies the output column data alignment. Used by the table format.
      The alignment values are:

       left
          Left (default).

       center
          Center.

       right
          Right.

   label=LABEL
      A string value used to label output. Use :label="" or :label='' for no
      label. The table format uses LABEL values as column headings. Also sets
      LABEL as an alias for the projection key. The default label is the
      disambiguated right hand parts of the column key name in
      ANGRY_SNAKE_CASE.

   [no-]reverse
      Sets the key sort order to descending. no-reverse resets to the default
      ascending order.

   sort=SORT-ORDER
      An integer counting from 1. Keys with lower sort-order are sorted
      first. Keys with same sort order are sorted left to right. Columns are
      sorted based on displayed value alone, irrespective of the type of
      value(date, time, etc.).

   wrap[=MIN-WIDTH]
      Enables the column text to be wrapped if the table would otherwise be
      too wide for the display. The column will be wrapped in the available
      space with a minimum width of either the default or of MIN-WIDTH if
      specified. The default is 10 characters.

   width=COLUMN-WIDTH
      An integer denoting the width for the column. The default fits the
      table to the terminal width or 80 if the output is not a terminal.

**Examples:**
```bash
List a table of instance zone (sorted in descending order) and name (sorted
by name and centered with column heading INSTANCE) and creationTimestamp
(listed using the strftime(3) year-month-day format with column heading
START):

    $ gcloud compute instances list \
        --format="table(name:sort=2:align=center:label=INSTANCE, \
    zone:sort=1:reverse, creationTimestamp.date("%Y-%m-%d"):label=START)\
    "

List only the name, status and zone instance resource keys in YAML format:

    $ gcloud compute instances list --format="yaml(name, status, zone)"

List only the config.account key value(s) in the info resource:

    $ gcloud info --format="value(config.account)"

List the name, id, and description of an imaginary foo resource, fixing the
name column width to 16 characters, wrapping the id column with the default
minimum width and the description column with a minimum width of 20
characters:

    $ gcloud example foo list \
        --format="table(name:width=16, id:wrap, description:wrap=20)"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/topic/projections)

---
### `gcloud topic resource-keys`

Resource keys supplementary help

A resource is a JSON-serializable object organized as a tree. Each node is
a scalar, indexed array, or dictionary. Structs and classes are represented
by dictionaries indexed by member name.

Each node is reachable by a unique path of names from the root. A node key
is the path names separated by '.'. [number] represents an array index. For
example:

    foo
    foo.bar
    abc.def[3].ghi

The resource keys and data values for any gcloud list command can be
printed by running gcloud ... list --format=flattened. See the command
specific documentation for details on specific resource keys.

**Examples:**
```bash
This command lists the keys and values for the regions resource:

    $ gcloud compute regions list --format=flattened

and here is sample output for the command:

    ---
    creationTimestamp: 2013-05-23T07:02:09.522-07:00
    description:       us-central1
    id:                22115839677829654
    kind:              compute#region
    name:              us-central1
    quotas[0].limit:   24.0
    quotas[0].metric:  CPUS
    quotas[0].usage:   15.0
    quotas[1].limit:   5120.0
    quotas[1].metric:  DISKS_TOTAL_GB
    quotas[1].usage:   1416.0
    quotas[2].limit:   7.0
    quotas[2].metric:  STATIC_ADDRESSES
    quotas[2].usage:   1.0
    quotas[3].limit:   23.0
    quotas[3].metric:  IN_USE_ADDRESSES
    quotas[3].usage:   16.0
    quotas[4].limit:   1024.0
    quotas[4].metric:  SSD_TOTAL_GB
    quotas[4].usage:   0.0
    quotas[5].limit:   1500.0
    quotas[5].metric:  LOCAL_SSD_TOTAL_GB
    quotas[5].usage:   750.0
    selfLink:          https://www.googleapis.com/.../us-central1
    status:            UP
    zones[0]:          us-central1-a
    zones[1]:          us-central1-b
    zones[2]:          us-central1-f

The list command produces a resource list. The keys are to the left of ':'
and the values are to the right.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/topic/resource-keys)

---
### `gcloud topic startup`

Supplementary help for gcloud startup options

Choosing a Python Interpreter

    The gcloud CLI runs under Python. Note that gcloud supports Python version
    3.9-3.14. Certain Windows and Linux installs include a bundled Python
    interpreter depending on the package and architecture. Similarly,
    Intel-based Macs offer the option to install CPython as part of the main
    install script. Otherwise, you must have a Python interpreter available on
    your system. The gcloud CLI will attempt to locate an interpreter on your
    system PATH by looking for the following binaries:

      o python3
      o python

    If you have a bundled Python installed, it will be preferred. To override
    this you will need to set the CLOUDSDK_PYTHON environment variable, see
    below.

    Other Python tools shipped in the Google Cloud CLI do not support Python 3
    and require Python 2.7.x, including:

      o dev_appserver

Bundled Python on Linux

    Linux-based installs include a bundled Python installation on x86_64
    architectures. This installation will be used by default. If you want to
    use a different Python installation, set the CLOUDSDK_PYTHON environment
    variable to the absolute path to your python interpreter.

    If you have multiple Python interpreters available (including a bundled
    python) or if you don't have one on your PATH, you can specify which
    interpreter to use by setting the CLOUDSDK_PYTHON environment variable. For
    example:

        # Use the python3 interpreter on your path

        $ export CLOUDSDK_PYTHON=python3

        # Use a python you have installed in a special location

        $ export CLOUDSDK_PYTHON=/usr/local/my-custom-python-install/python

    gsutil versions 5.0 and later support Python 3.9-3.13. To use a different
    interpreter for gsutil than for the other Python tools, set the
    CLOUDSDK_GSUTIL_PYTHON environment variable to the interpreter that you
    want.

    bq versions 2.0.99 and later support Python 3.9-3.14. To use a different
    interpreter for bq than for the other Python tools, set the
    CLOUDSDK_BQ_PYTHON environment variable to the interpreter that you want.

Configuring the Python Interpreter

    While not typically necessary, you can pass interpreter level arguments to
    the Python running gcloud using the CLOUDSDK_PYTHON_ARGS environment
    variable.

    A common use case for this (which has been special-cased) is to enable
    'site packages'. This allows Python to pick up libraries from the system (
    for example, those that may have been installed with pip). Site packages
    may be necessary if you require certain native libraries (as is the case if
    you work with service accounts using a legacy .p12 key, for example). To
    enable site packages, set CLOUDSDK_PYTHON_SITEPACKAGES=1. Note that
    enabling site packages may cause conflicts with gcloud packaged libraries,
    depending on what you have installed on your system.

Setting Configurations and Properties

    Your active configuration can also be set via the environment variable
    CLOUDSDK_ACTIVE_CONFIG_NAME. This allows you to specify a certain
    configuration in a given terminal session without changing the global
    default configuration.

    In addition to being able to set them via gcloud config set, each gcloud
    property has a corresponding environment variable. They take the form:
    CLOUDSDK_SECTION_PROPERTY. For example, if you wanted to change your active
    project for just one terminal you could run:

        $ export CLOUDSDK_CORE_PROJECT=my-project

    For more information, see gcloud topic configurations.

[Official reference](https://cloud.google.com/sdk/gcloud/reference/topic/startup)

---
### `gcloud topic uninstall`

Supplementary help for uninstalling Google Cloud CLI

Uninstalling Google Cloud CLI

    Note: For installations completed using an OS package (such as apt-get,
    yum, etc.), uninstall Google Cloud CLI via the OS package manager.

    Note: For Windows installations, execute the uninstaller.exe found under
    your Google Cloud CLI directory.

    To completely remove Google Cloud CLI, follow these instructions:

      o Locate your installation directory by running:

        $ gcloud info --format="value(installation.sdk_root)"

      o Locate your user config directory (typically ~/.config/gcloud on
        MacOS and Linux) by running:

        $ gcloud info --format="value(config.paths.global_config_dir)"

      o Delete both these directories.

      o Additionally, remove lines sourcing completion.bash.inc and
        paths.bash.inc in your .bashrc or equivalent shell init file, if you
        added them during installation.

      o Review the contents of the .boto file in your home directory and
        remove the sections '[GoogleCompute]' and '[GSUtil]'. In addition,
        review the sections '[OAuth2]' and '[Credentials]' for settings that
        are no longer needed.

      o Some systems may have Cache directories such as ~/Library/Caches/ on
        Mac OS X. Find and delete these directories for your system:

        $ find ~/Library/Caches/ -type d -name "google-cloud-sdk" | xargs \
        rm -r

[Official reference](https://cloud.google.com/sdk/gcloud/reference/topic/uninstall)

---