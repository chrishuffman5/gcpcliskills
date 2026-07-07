# gcloud storage (top-level commands)

### `gcloud storage cat`

Outputs the contents of one or more URLs to stdout

The cat command outputs the contents of one or more URLs to stdout. While
the cat command does not compute a checksum, it is otherwise equivalent to
doing:

    $ gcloud storage cp url... -

(The final '-' causes gcloud to stream the output to stdout.)

**Synopsis:**
```
gcloud storage cat URL [URL ...] [--additional-headers=HEADER=VALUE]
    [--display-url, -d] [--range=RANGE, -r RANGE]
    [--decryption-keys=[DECRYPTION_KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
URL [URL ...]
   The url of objects to list.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--additional-headers` | HEADER=VALUE |  | Includes arbitrary headers in storage API calls. Accepts a comma separated list of key=value pairs, e.g. header1=value1,header2=value2. Overrides the default storage/additional_headers property value for this command invocation. |
| `--display-url, -d` |  |  | Prints the header before each object. |
| `--range` | RANGE, -r RANGE |  | Causes gcloud storage to output just the specified byte range of the object. In a case where "start" = 'x', and "end" = 'y', ranges take the form: x-y (e.g., -r 256-5939), x- (e.g., -r 256-), -y (e.g., -r -5) When offsets start at 0, x-y means to return bytes x through y (inclusive), x- means to return bytes x through the end of the object, and -y changes the role of y. If -y is present, then it returns the last y bytes of the object. If the bytes are out of range of the object, then nothing is printed |


**Examples:**
```bash
The following command writes all text files in a bucket to stdout:

    $ gcloud storage cat gs://bucket/*.txt

The following command outputs a short header describing file.txt, along
with its contents:

    $ gcloud storage cat -d gs://my-bucket/file.txt

The following command outputs bytes 256-939 of file.txt:

    $ gcloud storage cat -r 256-939 gs://my-bucket/file.txt

The following command outputs the last 5 bytes of file.txt:

    $ gcloud storage cat -r -5 gs://my-bucket/file.txt
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/cat)

---
### `gcloud storage cp`

Upload, download, and copy Cloud Storage objects

Copy data between your local file system and the cloud, within the cloud,
and between cloud storage providers.

Please Note - By default, the cp command does not follow directory
symlinks. You can use the --preserve-symlinks flag to follow directory
symlinks.

**Synopsis:**
```
gcloud storage cp [SOURCE ...] DESTINATION
    [--additional-headers=HEADER=VALUE] [--all-versions, -A]
    [--no-clobber, -n] [--content-md5=MD5_DIGEST] [--continue-on-error, -c]
    [--daisy-chain, -D] [--do-not-decompress] [--include-managed-folders]
    [--manifest-path=MANIFEST_PATH, -L MANIFEST_PATH]
    [--preserve-posix, -P] [--print-created-message, -v]
    [--read-paths-from-stdin, -I] [--recursive, -R, -r]
    [--skip-unsupported, -U]
    [--storage-class=STORAGE_CLASS, -s STORAGE_CLASS]
    [--canned-acl=PREDEFINED_ACL, --predefined-acl=PREDEFINED_ACL,
      -a PREDEFINED_ACL --[no-]preserve-acl, -p]
    [--gzip-in-flight=[FILE_EXTENSIONS,...], -j [FILE_EXTENSIONS,...]
      | --gzip-in-flight-all, -J
      | --gzip-local=[FILE_EXTENSIONS,...], -z [FILE_EXTENSIONS,...]
      | --gzip-local-all, -Z] [--ignore-symlinks | --preserve-symlinks]
    [--decryption-keys=[DECRYPTION_KEY,...]
      --encryption-key=ENCRYPTION_KEY]
    [--cache-control=CACHE_CONTROL
      --content-disposition=CONTENT_DISPOSITION
      --content-encoding=CONTENT_ENCODING
      --content-language=CONTENT_LANGUAGE --content-type=CONTENT_TYPE
      --custom-time=CUSTOM_TIME --clear-custom-metadata
      | --custom-metadata=[CUSTOM_METADATA_KEYS_AND_VALUES,...]
      | --remove-custom-metadata=[METADATA_KEYS,...]
      --update-custom-metadata=[CUSTOM_METADATA_KEYS_AND_VALUES,...]]
    [--if-generation-match=GENERATION
      --if-metageneration-match=METAGENERATION]
    [--retain-until=DATETIME --retention-mode=RETENTION_MODE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[SOURCE ...]
   The source path(s) to copy.

DESTINATION
   The destination path.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--additional-headers` | HEADER=VALUE |  | Includes arbitrary headers in storage API calls. Accepts a comma separated list of key=value pairs, e.g. header1=value1,header2=value2. Overrides the default storage/additional_headers property value for this command invocation. |
| `--all-versions, -A` |  |  | Copy all source versions from a source bucket or folder. If not set, only the live version of each source object is copied. Note: This option is only useful when the destination bucket has Object Versioning enabled. Additionally, the generation numbers of copied versions do not necessarily match the order of the original generation numbers. |
| `--no-clobber, -n` |  |  | Do not overwrite existing files or objects at the destination. Skipped items will be printed. This option may perform an additional GET request for cloud objects before attempting an upload. |
| `--content-md5` | MD5_DIGEST |  | Manually specified MD5 hash digest for the contents of an uploaded file. This flag cannot be used when uploading multiple files. The custom digest is used by the cloud provider for validation. |
| `--continue-on-error, -c` |  |  | If any operations are unsuccessful, the command will exit with a non-zero exit status after completing the remaining operations. This flag takes effect only in sequential execution mode (i.e. processor and thread count are set to 1). Parallelism is default. |
| `--daisy-chain, -D` |  |  | Copy in "daisy chain" mode, which means copying an object by first downloading it to the machine where the command is run, then uploading it to the destination bucket. The default mode is a "copy in the cloud," where data is copied without uploading or downloading. During a copy in the cloud, a source composite object remains composite at its destination. However, you can use daisy chain mode to change a composite object into a non-composite object. Note: Daisy chain mode is automatically used when copying between providers. |
| `--do-not-decompress` |  |  | Do not automatically decompress downloaded gzip files. |
| `--include-managed-folders` |  |  | Includes managed folders in command operations. For transfers, gcloud storage will set up managed folders in the destination with the same IAM policy bindings as the source. Managed folders are only included with recursive cloud-to-cloud transfers. Please note that for hierarchical namespace buckets, managed folders are always included. Hence this flag would not be applicable to hierarchical namespace buckets. |
| `--manifest-path` | MANIFEST_PATH, -L MANIFEST_PATH |  | Outputs a manifest log file with detailed information about each item that was copied. This manifest contains the following information for each item: * Source path. * Destination path. * Source size. * Bytes transferred. * MD5 hash. * Transfer start time and date in UTC and ISO 8601 format. * Transfer completion time and date in UTC and ISO 8601 format. * Final result of the attempted transfer: OK, error, or skipped. * Details, if any. If the manifest file already exists, gcloud storage appends log items to the existing file. Objects that are marked as "OK" or "skipped" in the existing manifest file are not retried by future commands. Objects marked as "error" are retried. |
| `--preserve-posix, -P` |  |  | Causes POSIX attributes to be preserved when objects are copied. With this feature enabled, gcloud storage will copy several fields provided by the stat command: access time, modification time, owner UID, owner group GID, and the mode (permissions) of the file. For uploads, these attributes are read off of local files and stored in the cloud as custom metadata. For downloads, custom cloud metadata is set as POSIX attributes on files after they are downloaded. On Windows, this flag will only set and restore access time and modification time because Windows doesn't have a notion of POSIX UID, GID, and mode. |
| `--print-created-message, -v` |  |  | Prints the version-specific URL for each copied object. |
| `--read-paths-from-stdin, -I` |  |  | Read the list of resources to copy from stdin. No need to enter a source argument if this flag is present. Example: "storage cp -I gs://bucket/destination". The input format must consist of one path (e.g., "Documents/data/file1.txt") or one object URL (e.g., "gs://example-bucket/event.log") per line. Use a pipe to send the file list to the command. Example: "cat example-file-list.txt \| gcloud storage cp --read-paths-from-stdin gs://example-destination-bucket". Note: To copy the contents of one file directly from stdin, use "-" as the source argument without the "-I" flag. |
| `--recursive, -R, -r` |  |  | Recursively copy the contents of any directories that match the source path expression. |
| `--skip-unsupported, -U` |  |  | Skip objects with unsupported object types. |
| `--storage-class` | STORAGE_CLASS, -s STORAGE_CLASS |  | Specify the storage class of the destination object. If not specified, the default storage class of the destination bucket is used. This option is not valid for copying to non-cloud destinations. |
| `--canned-acl` | PREDEFINED_ACL, --predefined-acl=PREDEFINED_ACL, -a PREDEFINED_ACL |  | Applies predefined, or "canned," ACLs to a resource. See docs for a list of predefined ACL constants: https://cloud.google.com/storage/docs/access-control/lists#predefined-acl |
| `--[no-]preserve-acl, -p` |  |  | Preserves ACLs when copying in the cloud. This option is Cloud Storage-only, and you need OWNER access to all copied objects. If all objects in the destination bucket should have the same ACL, you can also set a default object ACL on that bucket instead of using this flag. Preserving ACLs is the default behavior for updating existing objects. Use --preserve-acl to enable and --no-preserve-acl to disable. |


**Examples:**
```bash
The following command uploads all text files from the local directory to a
bucket:

    $ gcloud storage cp *.txt gs://my-bucket

The following command downloads all text files from a bucket to your
current directory:

    $ gcloud storage cp gs://my-bucket/*.txt .

The following command transfers all text files from a bucket to a different
cloud storage provider:

    $ gcloud storage cp gs://my-bucket/*.txt s3://my-bucket

Use the --recursive option to copy an entire directory tree. The following
command uploads the directory tree dir:

    $ gcloud storage cp --recursive dir gs://my-bucket

Recursive listings are similar to adding ** to a query, except ** matches
only cloud objects and will not match prefixes. For example, the following
would not match gs://my-bucket/dir/log.txt

    $ gcloud storage cp gs://my-bucket/**/dir dir

** retrieves a flat list of objects in a single API call. However, **
matches folders for non-cloud queries. For example, a folder dir would be
copied in the following.

    $ gcloud storage cp ~/Downloads/**/dir gs://my-bucket
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/cp)

---
### `gcloud storage diagnose`

Diagnose Google Cloud Storage

The diagnose command runs a series of diagnostic tests for common gcloud
storage issues.

The URL argument must name an exisiting bucket for which the user already
has write permissions. Standard billing also applies. Several test
files/objects will be uploaded and downloaded to this bucket to gauge out
the performance metrics. All the temporary files will be deleted on
successfull completion of the command.

By default, the command executes DOWNLOAD_THROUGHPUT, UPLOAD_THROUGHPUT and
LATENCY tests. Tests to execute can be overriden by using the --test-type
flag. Each test uses the command defaults or gcloud CLI configurations for
performing the operations. This command also provides a way to override
these values via means of different flags like --process-count,
--thread-count, --download-type, etc.

The command outputs a diagnostic report with sytem information like free
memory, available CPU, average CPU load per test, disk counter deltas and
diagnostic information specific to individual tests on successful
completion.

**Synopsis:**
```
gcloud storage diagnose URL [--test-type=[TEST_TYPES,...]]
    [--download-type=DOWNLOAD_TYPE; default=<DownloadType.FILE: 'FILE'>]
    [--logs-path=LOGS_PATH]
    [--upload-type=UPLOAD_TYPE; default=<UploadType.FILE: 'FILE'>]
    [--process-count=PROCESS_COUNT] [--thread-count=THREAD_COUNT]
    [--object-count=OBJECT_COUNT (--object-size=OBJECT_SIZE
      | --object-sizes=[OBJECT_SIZES,...])]
    [--export : --destination=DESTINATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
URL
   Bucket URL to use for the diagnostic tests.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--test-type` | one of: DIRECT_CONNECTIVITY, DOWNLOAD_THROUGHPUT, LATENCY, UPLOAD_THROUGHPUT |  | Tests to run as part of this diagnosis. Following tests are supported: DIRECT_CONNECTIVITY: Run a test upload over the Direct Connectivity network path and run other diagnostics if the upload fails. DOWNLOAD_THROUGHPUT: Upload objects to the specified bucket and record the number of bytes transferred per second. UPLOAD_THROUGHPUT: Download objects from the specified bucket and record the number of bytes transferred per second. LATENCY: Write the objects, retrieve their metadata, read the objects, and record latency of each operation. TEST_TYPES must be one of: DIRECT_CONNECTIVITY, DOWNLOAD_THROUGHPUT, LATENCY, UPLOAD_THROUGHPUT. |
| `--download-type` | one of: FILE, SLICED, STREAMING | <DownloadType.FILE: 'FILE'> | Download strategy to use for the DOWNLOAD_THROUGHPUT diagnostic test. STREAMING: Downloads the file in memory, does not use parallelism. --process-count and --thread-count flag values will be ignored if provided. SLICED: Performs a sliced download (https://cloud.google.com/storage/docs/sliced-object-downloads) of objects to a directory. Parallelism can be controlled via --process-count and --thread-count flags. FILE: Download objects as files. Parallelism can be controlled via --process-count and --thread-count flags. DOWNLOAD_TYPE must be one of: FILE, SLICED, STREAMING. |
| `--logs-path` | LOGS_PATH |  | If the diagnostic supports writing logs, write the logs to this file location. |
| `--upload-type` | one of: FILE, PARALLEL_COMPOSITE, STREAMING | <UploadType.FILE: 'FILE'> | Upload strategy to use for the UPLOAD_THROUGHPUT diagnostic test. FILE: Uploads files to a bucket. Parallelism can be controlled via --process-count and --thread-count flags. PARALLEL_COMPOSITE: Uploads files using a parallel composite strategy (https://cloud.google.com/storage/docs/parallel-composite-uploads). Parallelism can be controlled via --process-count and --thread-count flags. STREAMING: Streams the data to the bucket, does not use parallelism. --process-count and --thread-count flag values will be ignored if provided. UPLOAD_TYPE must be one of: FILE, PARALLEL_COMPOSITE, STREAMING. |
| `--process-count` | PROCESS_COUNT |  | Number of processes at max to use for each diagnostic test. |
| `--thread-count` | THREAD_COUNT |  | Number of threads at max to use for each diagnostic test. |


**Examples:**
```bash
The following command runs the default diagnostic tests on my-bucket
bucket:

    $ gcloud storage diagnose gs://my-bucket

The following command runs only UPLOAD_THROUGHPUT and DOWNLOAD_THROUGHPUT
diagnostic tests:

    $ gcloud storage diagnose gs://my-bucket \
        --test-type=UPLOAD_THROUGHPUT,DOWNLOAD_THROUGHPUT

The following command runs the diagnostic tests using 10 objects of 1MiB
size each with 10 threads and 10 processes at max:

    $ gcloud storage diagnose gs://my-bucket --no-of-objects=10 \
        --object-size=1MiB --process-count=10 --thread-count=10

The following command can be used to bundle and export the diagnostic
information to a user defined PATH destination:

    $ gcloud storage diagnose gs://my-bucket --export \
        --destination=<PATH>
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/diagnose)

---
### `gcloud storage du`

Displays the amount of space in bytes used by storage resources

Displays the amount of space in bytes used by the objects in a bucket,
subdirectory, or project. This command calculates the current space usage
by making a series of object listing requests, which can take a long time
for large buckets. If your bucket contains hundreds of thousands of
objects, or if you want to monitor your bucket size over time, use
Monitoring instead, as described in Get bucket size
(https://cloud.google.com/storage/docs/getting-bucket-size)

**Synopsis:**
```
gcloud storage du [URL ...] [--additional-headers=HEADER=VALUE]
    [--all-versions, -a]
    [--exclude-name-pattern=EXCLUDE_NAME_PATTERN, -e EXCLUDE_NAME_PATTERN]
    [--exclude-name-pattern-file=EXCLUDE_NAME_PATTERN_FILE,
      -X EXCLUDE_NAME_PATTERN_FILE] [--readable-sizes, -r]
    [--summarize, -s] [--total, -c] [--zero-terminator, -0]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[URL ...]
   The url of objects to list.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--additional-headers` | HEADER=VALUE |  | Includes arbitrary headers in storage API calls. Accepts a comma separated list of key=value pairs, e.g. header1=value1,header2=value2. Overrides the default storage/additional_headers property value for this command invocation. |
| `--all-versions, -a` |  |  | Includes noncurrent object versions for a bucket with Object Versioning enabled. Also prints the generation and metageneration number for each listed object. |
| `--exclude-name-pattern` | EXCLUDE_NAME_PATTERN, -e EXCLUDE_NAME_PATTERN |  | Exclude a pattern from the report. Example: -e "*.o" excludes any object that ends in ".o". Can be specified multiple times. |
| `--exclude-name-pattern-file` | EXCLUDE_NAME_PATTERN_FILE, -X EXCLUDE_NAME_PATTERN_FILE |  | Similar to -e, but excludes patterns from the given file. The patterns to exclude should be listed one per line. |
| `--readable-sizes, -r` |  |  | Prints object sizes in human-readable format. For example, 1 KiB, 234 MiB, or 2GiB. |
| `--summarize, -s` |  |  | Displays only the summary for each argument. |
| `--total, -c` |  |  | Includes a total size of all input sources. |
| `--zero-terminator, -0` |  |  | Ends each output line with a 0 byte rather than a newline. You can use this to make the output machine-readable. |


**Examples:**
```bash
To list the size of each object in a bucket:

    $ gcloud storage du gs://bucketname

To list the size of each object in the prefix subdirectory:

    $ gcloud storage du gs://bucketname/prefix/*

To print the total number of bytes in a bucket in human-readable form:

    $ gcloud storage du -c gs://bucketname

To see a summary of the total number of bytes in two given buckets:

    $ gcloud storage du -s gs://bucket1 gs://bucket2

To list the size of each object in a bucket with Object Versioning enabled,
including noncurrent objects:

    $ gcloud storage du -a gs://bucketname

To list the size of each object in a bucket, except objects that end in
".bak", with each object printed ending in a null byte:

    $ gcloud storage du -e "*.bak" -0 gs://bucketname

To list the size of each bucket in a project and the total size of the
project:

    $ gcloud storage du --summarize --readable-sizes --total
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/du)

---
### `gcloud storage hash`

Calculates hashes on local or cloud files

Calculates hashes on local or cloud files that can be used to compare with
"gcloud storage ls -L" output. If a specific hash option is not provided,
this command calculates all gcloud storage-supported hashes for the file.

Note that gcloud storage automatically performs hash validation when
uploading or downloading files, so this command is only needed if you want
to write a script that separately checks the hash for some reason.

If you calculate a CRC32C hash for the file without a precompiled
google-crc32c installation, hashing will be very slow.

**Synopsis:**
```
gcloud storage hash URLS [URLS ...] [--additional-headers=HEADER=VALUE]
    [--hex] [--skip-crc32c | --skip-md5]
    [--decryption-keys=[DECRYPTION_KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
URLS [URLS ...]
   Local or cloud URLs of objects to hash.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--additional-headers` | HEADER=VALUE |  | Includes arbitrary headers in storage API calls. Accepts a comma separated list of key=value pairs, e.g. header1=value1,header2=value2. Overrides the default storage/additional_headers property value for this command invocation. |
| `--hex` |  |  | Output hash digests in hex format. By default, digests are displayed in base64. |


**Examples:**
```bash
To get the MD5 and CRC32C hash digest of a cloud object in Base64 format:

    $ gcloud storage hash gs://bucket/object

To get just the MD5 hash digest of a local object in hex format:

    $ gcloud storage hash /dir/object.txt --skip-crc32c --hex
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/hash)

---
### `gcloud storage ls`

List Cloud Storage buckets and objects

List your Cloud Storage buckets in a project and objects in a bucket. This
command treats forward slashes in object names as directories. See below
for examples of how to use wildcards to get the listing behavior you want.

**Synopsis:**
```
gcloud storage ls [PATH ...] [--additional-headers=HEADER=VALUE]
    [--all-versions, -a] [--buckets, -b] [--etag, -e] [--exhaustive]
    [--fetch-encrypted-object-hashes] [--format=FORMAT]
    [--next-page-token=NEXT_PAGE_TOKEN] [--read-paths-from-stdin, -I]
    [--readable-sizes] [--recursive, -R, -r] [--soft-deleted]
    [--full, -L | --json, -j | --long, -l]
    [--decryption-keys=[DECRYPTION_KEY,...]] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[PATH ...]
   The path of objects and directories to list. The path must begin with
   gs:// and is allowed to contain wildcard characters.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--additional-headers` | HEADER=VALUE |  | Includes arbitrary headers in storage API calls. Accepts a comma separated list of key=value pairs, e.g. header1=value1,header2=value2. Overrides the default storage/additional_headers property value for this command invocation. |
| `--all-versions, -a` |  |  | Include noncurrent object versions in the listing. This flag is typically only useful for buckets with object versioning (https://cloud.google.com/storage/docs/object-versioning) enabled. If combined with the --long option, the metageneration for each listed object is also included. |
| `--buckets, -b` |  |  | When given a bucket URL, only return buckets. Useful for avoiding the rule that prints the top-level objects of buckets matching a query. Typically used in combination with --full to get the full metadata of buckets. |
| `--etag, -e` |  |  | Include ETag metadata in listings that use the --long flag. |
| `--exhaustive` |  |  | For features like soft delete, the API may return an empty list. If present, continue querying. This may incur costs from repeated LIST calls and may not return any additional objects. |
| `--fetch-encrypted-object-hashes` |  |  | API requests to the LIST endpoint do not fetch the hashes for encrypted objects by default. If this flag is set, a GET request is sent for each encrypted object in order to fetch hashes. This can significantly increase the cost of the command. |
| `--format` | FORMAT |  | Use "gsutil" to get the style of the older gsutil CLI. (e.g. "--format=gsutil"). Other format values (e.g. "json") do not work. See different ls flags and commands for alternative formatting. |
| `--next-page-token` | NEXT_PAGE_TOKEN |  | Page token for resuming LIST calls. |
| `--read-paths-from-stdin, -I` |  |  | Read the list of URLs from stdin. |
| `--readable-sizes` |  |  | When used with --long, print object sizes in human readable format, such as 1 KiB, 234 MiB, or 2 GiB. |
| `--recursive, -R, -r` |  |  | Recursively list the contents of any directories that match the path expression. |
| `--soft-deleted` |  |  | Displays soft-deleted resources only. For objects, it will exclude live and noncurrent ones. |


**Examples:**
```bash
The following command lists the buckets in the default project:

    $ gcloud storage ls

The following command lists the buckets in the specified project:

    $ gcloud storage ls --project=my-project

The following command lists the contents of a bucket:

    $ gcloud storage ls gs://my-bucket

You can use wildcards (https://cloud.google.com/storage/docs/wildcards) to
match multiple paths (including multiple buckets). Bucket wildcards are
expanded to match only buckets contained in your current project. The
following command matches .txt objects that begin with log and that are
stored in buckets in your project that begin with my-b:

    $ gcloud storage ls gs://my-b*/log*.txt

You can use double-star wildcards to match zero or more directory levels in
a path. The following command matches all .txt objects in a bucket.

    $ gcloud storage ls gs://my-bucket/**/*.txt

The wildcard ** retrieves a flat list of objects in a single API call and
does not match prefixes. The following command would not match
gs://my-bucket/dir/log.txt:

    $ gcloud storage ls gs://my-bucket/**/dir

Double-star expansion also can not be combined with other expressions in a
given path segment and operates as a single star in that context. For
example, the command gs://my-bucket/dir**/log.txt is treated as
gs://my-bucket/dir*/log.txt. To get the recursive behavior, the command
should instead be written the following way:

    gs://my-bucket/dir*/**/log.txt

The following command lists all items recursively with formatting by using
--recursive:

    $ gcloud storage ls --recursive gs://bucket

Recursive listings are similar to ** except recursive listings include line
breaks and header formatting for each subdirectory.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/ls)

---
### `gcloud storage mv`

Moves or renames objects

The mv command allows you to move data between your local file system and
the cloud, move data within the cloud, and move data between cloud storage
providers.

Renaming Groups Of Objects

You can use the mv command to rename all objects with a given prefix to
have a new prefix. For example, the following command renames all objects
under gs://my_bucket/oldprefix to be under gs://my_bucket/newprefix,
otherwise preserving the naming structure:

    $ gcloud storage mv gs://my_bucket/oldprefix gs://my_bucket/newprefix

Note that when using mv to rename groups of objects with a common prefix,
you cannot specify the source URL using wildcards; you must spell out the
complete name.

If you do a rename as specified above and you want to preserve ACLs.

Non-Atomic Operation

Unlike the case with many file systems, the mv command does not perform a
single atomic operation. Rather, it performs a copy from source to
destination followed by removing the source for each object.

A consequence of this is that, in addition to normal network and operation
charges, if you move a Nearline Storage, Coldline Storage, or Archive
Storage object, deletion and data retrieval charges apply. See the
documentation for pricing details.

**Synopsis:**
```
gcloud storage mv [SOURCE ...] DESTINATION
    [--additional-headers=HEADER=VALUE] [--all-versions, -A]
    [--no-clobber, -n] [--content-md5=MD5_DIGEST] [--continue-on-error, -c]
    [--daisy-chain, -D] [--do-not-decompress] [--include-managed-folders]
    [--manifest-path=MANIFEST_PATH, -L MANIFEST_PATH]
    [--preserve-posix, -P] [--print-created-message, -v]
    [--read-paths-from-stdin, -I] [--skip-unsupported, -U]
    [--storage-class=STORAGE_CLASS, -s STORAGE_CLASS]
    [--canned-acl=PREDEFINED_ACL, --predefined-acl=PREDEFINED_ACL,
      -a PREDEFINED_ACL --[no-]preserve-acl, -p]
    [--gzip-in-flight=[FILE_EXTENSIONS,...], -j [FILE_EXTENSIONS,...]
      | --gzip-in-flight-all, -J
      | --gzip-local=[FILE_EXTENSIONS,...], -z [FILE_EXTENSIONS,...]
      | --gzip-local-all, -Z] [--ignore-symlinks | --preserve-symlinks]
    [--decryption-keys=[DECRYPTION_KEY,...]
      --encryption-key=ENCRYPTION_KEY]
    [--cache-control=CACHE_CONTROL
      --content-disposition=CONTENT_DISPOSITION
      --content-encoding=CONTENT_ENCODING
      --content-language=CONTENT_LANGUAGE --content-type=CONTENT_TYPE
      --custom-time=CUSTOM_TIME --clear-custom-metadata
      | --custom-metadata=[CUSTOM_METADATA_KEYS_AND_VALUES,...]
      | --remove-custom-metadata=[METADATA_KEYS,...]
      --update-custom-metadata=[CUSTOM_METADATA_KEYS_AND_VALUES,...]]
    [--if-generation-match=GENERATION
      --if-metageneration-match=METAGENERATION]
    [--retain-until=DATETIME --retention-mode=RETENTION_MODE]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[SOURCE ...]
   The source path(s) to copy.

DESTINATION
   The destination path.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--additional-headers` | HEADER=VALUE |  | Includes arbitrary headers in storage API calls. Accepts a comma separated list of key=value pairs, e.g. header1=value1,header2=value2. Overrides the default storage/additional_headers property value for this command invocation. |
| `--all-versions, -A` |  |  | Copy all source versions from a source bucket or folder. If not set, only the live version of each source object is copied. Note: This option is only useful when the destination bucket has Object Versioning enabled. Additionally, the generation numbers of copied versions do not necessarily match the order of the original generation numbers. |
| `--no-clobber, -n` |  |  | Do not overwrite existing files or objects at the destination. Skipped items will be printed. This option may perform an additional GET request for cloud objects before attempting an upload. |
| `--content-md5` | MD5_DIGEST |  | Manually specified MD5 hash digest for the contents of an uploaded file. This flag cannot be used when uploading multiple files. The custom digest is used by the cloud provider for validation. |
| `--continue-on-error, -c` |  |  | If any operations are unsuccessful, the command will exit with a non-zero exit status after completing the remaining operations. This flag takes effect only in sequential execution mode (i.e. processor and thread count are set to 1). Parallelism is default. |
| `--daisy-chain, -D` |  |  | Copy in "daisy chain" mode, which means copying an object by first downloading it to the machine where the command is run, then uploading it to the destination bucket. The default mode is a "copy in the cloud," where data is copied without uploading or downloading. During a copy in the cloud, a source composite object remains composite at its destination. However, you can use daisy chain mode to change a composite object into a non-composite object. Note: Daisy chain mode is automatically used when copying between providers. |
| `--do-not-decompress` |  |  | Do not automatically decompress downloaded gzip files. |
| `--include-managed-folders` |  |  | Includes managed folders in command operations. For transfers, gcloud storage will set up managed folders in the destination with the same IAM policy bindings as the source. Managed folders are only included with recursive cloud-to-cloud transfers. Please note that for hierarchical namespace buckets, managed folders are always included. Hence this flag would not be applicable to hierarchical namespace buckets. |
| `--manifest-path` | MANIFEST_PATH, -L MANIFEST_PATH |  | Outputs a manifest log file with detailed information about each item that was copied. This manifest contains the following information for each item: * Source path. * Destination path. * Source size. * Bytes transferred. * MD5 hash. * Transfer start time and date in UTC and ISO 8601 format. * Transfer completion time and date in UTC and ISO 8601 format. * Final result of the attempted transfer: OK, error, or skipped. * Details, if any. If the manifest file already exists, gcloud storage appends log items to the existing file. Objects that are marked as "OK" or "skipped" in the existing manifest file are not retried by future commands. Objects marked as "error" are retried. |
| `--preserve-posix, -P` |  |  | Causes POSIX attributes to be preserved when objects are copied. With this feature enabled, gcloud storage will copy several fields provided by the stat command: access time, modification time, owner UID, owner group GID, and the mode (permissions) of the file. For uploads, these attributes are read off of local files and stored in the cloud as custom metadata. For downloads, custom cloud metadata is set as POSIX attributes on files after they are downloaded. On Windows, this flag will only set and restore access time and modification time because Windows doesn't have a notion of POSIX UID, GID, and mode. |
| `--print-created-message, -v` |  |  | Prints the version-specific URL for each copied object. |
| `--read-paths-from-stdin, -I` |  |  | Read the list of resources to copy from stdin. No need to enter a source argument if this flag is present. Example: "storage cp -I gs://bucket/destination". The input format must consist of one path (e.g., "Documents/data/file1.txt") or one object URL (e.g., "gs://example-bucket/event.log") per line. Use a pipe to send the file list to the command. Example: "cat example-file-list.txt \| gcloud storage cp --read-paths-from-stdin gs://example-destination-bucket". Note: To copy the contents of one file directly from stdin, use "-" as the source argument without the "-I" flag. |
| `--skip-unsupported, -U` |  |  | Skip objects with unsupported object types. |
| `--storage-class` | STORAGE_CLASS, -s STORAGE_CLASS |  | Specify the storage class of the destination object. If not specified, the default storage class of the destination bucket is used. This option is not valid for copying to non-cloud destinations. |
| `--canned-acl` | PREDEFINED_ACL, --predefined-acl=PREDEFINED_ACL, -a PREDEFINED_ACL |  | Applies predefined, or "canned," ACLs to a resource. See docs for a list of predefined ACL constants: https://cloud.google.com/storage/docs/access-control/lists#predefined-acl |
| `--[no-]preserve-acl, -p` |  |  | Preserves ACLs when copying in the cloud. This option is Cloud Storage-only, and you need OWNER access to all copied objects. If all objects in the destination bucket should have the same ACL, you can also set a default object ACL on that bucket instead of using this flag. Preserving ACLs is the default behavior for updating existing objects. Use --preserve-acl to enable and --no-preserve-acl to disable. |


**Examples:**
```bash
To move all objects from a bucket to a local directory you could use:

    $ gcloud storage mv gs://my_bucket/* dir

Similarly, to move all objects from a local directory to a bucket you could
use:

    $ gcloud storage mv ./dir gs://my_bucket

The following command renames all objects under gs://my_bucket/oldprefix to
be under gs://my_bucket/newprefix, otherwise preserving the naming
structure:

    $ gcloud storage mv gs://my_bucket/oldprefix gs://my_bucket/newprefix
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/mv)

---
### `gcloud storage restore`

Restore one or more soft-deleted objects

The restore command restores soft-deleted resources:

    $ gcloud storage restore url...

**Synopsis:**
```
gcloud storage restore [URLS ...] [--all-versions, -a] [--async]
    [--[no-]preserve-acl, -p] [--read-paths-from-stdin, -I]
    [--allow-overwrite --created-after-time=CREATED_AFTER_TIME
      --created-before-time=CREATED_BEFORE_TIME
      --deleted-after-time=DELETED_AFTER_TIME
      --deleted-before-time=DELETED_BEFORE_TIME]
    [--if-generation-match=GENERATION
      --if-metageneration-match=METAGENERATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[URLS ...]
   The url of objects to list.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--all-versions, -a` |  |  | _[SYNCHRONOUS RESTORE OPTIONS]_ Restores all versions of soft-deleted objects. This flag is only useful for buckets with [object versioning] (https://cloud.google.com/storage/docs/object-versioning) enabled. In this case, the latest soft-deleted version will become live and the previous generations will become noncurrent. If versioning is disabled, the latest soft-deleted version will become live and previous generations will be soft-deleted again. This flag disables parallelism to preserve version order. |
| `--async` |  |  | _[SYNCHRONOUS RESTORE OPTIONS]_ Initiates an asynchronous bulk restore operation on the specified bucket. |
| `--[no-]preserve-acl, -p` |  |  | _[SYNCHRONOUS RESTORE OPTIONS]_ Preserves ACLs when copying in the cloud. This option is Cloud Storage-only, and you need OWNER access to all copied objects. If all objects in the destination bucket should have the same ACL, you can also set a default object ACL on that bucket instead of using this flag. Preserving ACLs is the default behavior for updating existing objects. Use --preserve-acl to enable and --no-preserve-acl to disable. |
| `--read-paths-from-stdin, -I` |  |  | _[SYNCHRONOUS RESTORE OPTIONS]_ Read the list of URLs from stdin. |
| `--allow-overwrite` |  |  | _[BULK RESTORE OPTIONS]_ If included, live objects will be overwritten. If versioning is enabled, this will result in a noncurrent object. If versioning is not enabled, this will result in a soft-deleted object. |
| `--created-after-time` | CREATED_AFTER_TIME |  | _[BULK RESTORE OPTIONS]_ Restores only the objects that were created after this time. |
| `--created-before-time` | CREATED_BEFORE_TIME |  | _[BULK RESTORE OPTIONS]_ Restores only the objects that were created before this time. |
| `--deleted-after-time` | DELETED_AFTER_TIME |  | _[BULK RESTORE OPTIONS]_ Restores only the objects that were soft-deleted after this time. |
| `--deleted-before-time` | DELETED_BEFORE_TIME |  | _[BULK RESTORE OPTIONS]_ Restores only the objects that were soft-deleted before this time. |


**Examples:**
```bash
Restore soft-deleted version of bucket with generations:

    $ gcloud storage restore gs://bucket#123

Restore several soft-deleted buckets with generations:

    $ gcloud storage restore gs://bucket1#123 gs://bucket2#456

Restore latest soft-deleted version of object in a bucket.

    $ gcloud storage restore gs://bucket/file1.txt

Restore a specific soft-deleted version of object in a bucket by specifying
the generation.

    $ gcloud storage restore gs://bucket/file1.txt#123

Restore all soft-deleted versions of object in a bucket.

    $ gcloud storage restore gs://bucket/file1.txt --all-versions

Restore several objects in a bucket (with or without generation):

    $ gcloud storage restore gs://bucket/file1.txt \
        gs://bucket/file2.txt#456

Restore the latest soft-deleted version of all text objects in a bucket:

    $ gcloud storage restore gs://bucket/**.txt

Restore a list of objects read from stdin (with or without generation):

    $ cat list-of-files.txt | gcloud storage restore \
        --read-paths-from-stdin

Restore object with its original ACL policy:

    $ gcloud storage restore gs://bucket/file1.txt --preserve-acl

Restore all objects in a bucket asynchronously:

    $ gcloud storage restore gs://bucket/** --async

Restore all text files in a bucket asynchronously:

    $ gcloud storage restore gs://bucket/**.txt --async

Restore objects created within a specific time range:

    $ gcloud storage restore gs://bucket/** --async \
        --created-after-time="2023-01-01T00:00:00Z" \
        --created-before-time="2023-01-31T23:59:59Z"

Restore objects soft-deleted within a specific time range:

    $ gcloud storage restore gs://bucket/** --async \
        --deleted-after-time="2023-01-01T00:00:00Z" \
        --deleted-before-time="2023-01-31T23:59:59Z"

Restore objects using a combination of creation and deletion time filters:

    $ gcloud storage restore gs://bucket/** --async --allow-overwrite \
      --created-after-time="2023-01-01T00:00:00Z" \
      --deleted-after-time="2023-01-01T00:00:00Z"

This command filters the objects that were live at 2023-01-01T00:00:00Z and
then soft-deleted afterwards. This combination of filters is especially
helpful if there is a period of erroneous overwrites. They allow you to go
back to the point just before the overwrites began. You will also need to
set the --allow-overwrite option to true.
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/restore)

---
### `gcloud storage rm`

Delete objects and buckets

Delete objects and buckets.

**Synopsis:**
```
gcloud storage rm [URLS ...] [--additional-headers=HEADER=VALUE]
    [--all-versions, -a] [--continue-on-error, -c]
    [--exclude-managed-folders] [--read-paths-from-stdin, -I]
    [--recursive, -R, -r]
    [--if-generation-match=GENERATION
      --if-metageneration-match=METAGENERATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
[URLS ...]
   The URLs of the resources to delete.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--additional-headers` | HEADER=VALUE |  | Includes arbitrary headers in storage API calls. Accepts a comma separated list of key=value pairs, e.g. header1=value1,header2=value2. Overrides the default storage/additional_headers property value for this command invocation. |
| `--all-versions, -a` |  |  | Delete all versions (https://cloud.google.com/storage/docs/object-versioning) of an object. |
| `--continue-on-error, -c` |  |  | If any operations are unsuccessful, the command will exit with a non-zero exit status after completing the remaining operations. This flag takes effect only in sequential execution mode (i.e. processor and thread count are set to 1). Parallelism is default. |
| `--exclude-managed-folders` |  |  | Excludes managed folders from command operations. By default gcloud storage includes managed folders in recursive removals. Please note that this flag would not be applicable for hierarchical namespace buckets as we always list managed folders for these buckets. |
| `--read-paths-from-stdin, -I` |  |  | Read the list of URLs from stdin. |
| `--recursive, -R, -r` |  |  | Recursively delete the contents of buckets or directories that match the path expression. By default, this will delete managed folders as well. If the path is set to a bucket, like gs://bucket, the bucket is also deleted. This option implies the --all-versions option. If you want to delete only live object versions, use the ``**'' wildcard instead. |


**Examples:**
```bash
The following command deletes a Cloud Storage object named my-object from
the bucket my-bucket:

    $ gcloud storage rm gs://my-bucket/my-object

The following command deletes all objects directly within the directory
my-dir but no objects within subdirectories:

    $ gcloud storage rm gs://my-bucket/my-dir/*

The following command deletes all objects and subdirectories within the
directory my-dir:

    $ gcloud storage rm gs://my-bucket/my-dir/**

Note that for buckets that contain versioned objects
(https://cloud.google.com/storage/docs/object-versioning), the above
command only affects live versions. Use the --recursive flag instead to
delete all versions.

The following command deletes all versions of all resources in my-bucket
and then deletes the bucket.

    $ gcloud storage rm --recursive gs://my-bucket/

The following command deletes all text files in the top-level of my-bucket,
but not text files in subdirectories:

    $ gcloud storage rm -recursive gs://my-bucket/*.txt

The following command deletes one wildcard expression per line passed in by
stdin:

    $ some_program | gcloud storage rm -I
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/rm)

---
### `gcloud storage rsync`

Synchronize content of two buckets/directories

gcloud storage rsync copies to and updates objects at DESTINATION to match
SOURCE. SOURCE must specify a directory, bucket, or bucket subdirectory.
gcloud storage rsync does not copy empty directory trees, since storage
providers use a flat namespace
(https://cloud.google.com/storage/docs/folders).

Note, shells (like bash, zsh) sometimes attempt to expand wildcards in ways
that can be surprising. Also, attempting to copy files whose names contain
wildcard characters can result in problems.

If synchronizing a large amount of data between clouds you might consider
setting up a Google Compute Engine account and running gcloud storage rsync
there. Since gcloud storage rsync cross-provider data transfers flow
through the machine where gcloud storage rsync is running, doing this can
make your transfer run significantly faster than on your local workstation.

**Synopsis:**
```
gcloud storage rsync SOURCE DESTINATION [--additional-headers=HEADER=VALUE]
    [--canned-acl=PREDEFINED_ACL,
      --predefined-acl=PREDEFINED_ACL, -a PREDEFINED_ACL]
    [--checksums-only] [--no-clobber, -n] [--content-md5=MD5_DIGEST]
    [--continue-on-error, -c] [--delete-unmatched-destination-objects]
    [--dry-run] [--exclude=[REGEX,...], -x [REGEX,...]]
    [--gzip-in-flight=[FILE_EXTENSIONS,...], -j [FILE_EXTENSIONS,...]]
    [--gzip-in-flight-all, -J] [--no-ignore-symlinks]
    [--include-managed-folders] [--preserve-posix, -P]
    [--recursive, -R, -r] [--skip-if-dest-has-newer-mtime, -u]
    [--skip-unsupported, -U]
    [--decryption-keys=[DECRYPTION_KEY,...]
      --encryption-key=ENCRYPTION_KEY]
    [--cache-control=CACHE_CONTROL
      --content-disposition=CONTENT_DISPOSITION
      --content-encoding=CONTENT_ENCODING
      --content-language=CONTENT_LANGUAGE --content-type=CONTENT_TYPE
      --custom-time=CUSTOM_TIME --clear-custom-metadata
      | --custom-metadata=[CUSTOM_METADATA_KEYS_AND_VALUES,...]
      | --remove-custom-metadata=[METADATA_KEYS,...]
      --update-custom-metadata=[CUSTOM_METADATA_KEYS_AND_VALUES,...]]
    [--if-generation-match=GENERATION
      --if-metageneration-match=METAGENERATION] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
SOURCE
   The source container path.

DESTINATION
   The destination container path.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--additional-headers` | HEADER=VALUE |  | Includes arbitrary headers in storage API calls. Accepts a comma separated list of key=value pairs, e.g. header1=value1,header2=value2. Overrides the default storage/additional_headers property value for this command invocation. |
| `--canned-acl` | PREDEFINED_ACL, --predefined-acl=PREDEFINED_ACL, -a PREDEFINED_ACL |  | Applies predefined, or "canned," ACLs to a resource. See docs for a list of predefined ACL constants: https://cloud.google.com/storage/docs/access-control/lists#predefined-acl |
| `--checksums-only` |  |  | When comparing objects with matching names at the source and destination, skip modification time check and compare object hashes. Normally, hashes are only compared if modification times are not available. |
| `--no-clobber, -n` |  |  | Do not overwrite existing files or objects at the destination. Skipped items will be printed. This option may perform an additional GET request for cloud objects before attempting an upload. |
| `--content-md5` | MD5_DIGEST |  | Manually specified MD5 hash digest for the contents of an uploaded file. This flag cannot be used when uploading multiple files. The custom digest is used by the cloud provider for validation. |
| `--continue-on-error, -c` |  |  | If any operations are unsuccessful, the command will exit with a non-zero exit status after completing the remaining operations. This flag takes effect only in sequential execution mode (i.e. processor and thread count are set to 1). Parallelism is default. |
| `--delete-unmatched-destination-objects` |  |  | Delete extra files under DESTINATION not found under SOURCE. By default extra files are not deleted. Managed folders are not affected by this flag. Note: this option can delete data quickly if you specify the wrong source and destination combination. |
| `--dry-run` |  |  | Print what operations rsync would perform without actually executing them. |
| `--exclude` | [REGEX,...], -x [REGEX,...] |  | Exclude objects matching regex pattern from rsync. Note that this is a Python regular expression, not a pure wildcard pattern. For example, matching a string ending in "abc" is .*abc$ rather than *abc. Also note that the exclude path is relative, as opposed to absolute (similar to Linux rsync and tar exclude options). For the Windows cmd.exe command line interpreter, use ^ as an escape character instead of \ and escape the \| character. When using Windows PowerShell, use ' instead of " and surround the \| character with ". |
| `--gzip-in-flight` | [FILE_EXTENSIONS,...], -j [FILE_EXTENSIONS,...] |  | Applies gzip transport encoding to any file upload whose extension matches the input extension list. This is useful when uploading files with compressible content such as .js, .css, or .html files. This also saves network bandwidth while leaving the data uncompressed in Cloud Storage. When you specify the --gzip-in-flight option, files being uploaded are compressed in-memory and on-the-wire only. Both the local files and Cloud Storage objects remain uncompressed. The uploaded objects retain the Content-Type and name of the original files. |
| `--gzip-in-flight-all, -J` |  |  | Applies gzip transport encoding to file uploads. This option works like the --gzip-in-flight option described above, but it applies to all uploaded files, regardless of extension. CAUTION: If some of the source files don't compress well, such as binary data, using this option may result in longer uploads. |
| `--ignore-symlinks` |  |  | Ignore file symlinks instead of copying what they point to. Enabled by default, use --no-ignore-symlinks to disable. |
| `--include-managed-folders` |  |  | Includes managed folders in command operations. For transfers, gcloud storage will set up managed folders in the destination with the same IAM policy bindings as the source. Managed folders are only included with recursive cloud-to-cloud transfers. |
| `--preserve-posix, -P` |  |  | Causes POSIX attributes to be preserved when objects are copied. With this feature enabled, gcloud storage will copy several fields provided by the stat command: access time, modification time, owner UID, owner group GID, and the mode (permissions) of the file. For uploads, these attributes are read off of local files and stored in the cloud as custom metadata. For downloads, custom cloud metadata is set as POSIX attributes on files after they are downloaded. On Windows, this flag will only set and restore access time and modification time because Windows doesn't have a notion of POSIX UID, GID, and mode. |
| `--recursive, -R, -r` |  |  | Recursively copy the contents of any directories that match the source path expression. |
| `--skip-if-dest-has-newer-mtime, -u` |  |  | Skip operating on destination object if it has a newer modification time than the source. |
| `--skip-unsupported, -U` |  |  | Skip objects with unsupported object types. |


**Examples:**
```bash
To sync the contents of the local directory data to the bucket
gs://my-bucket/data:

    $ gcloud storage rsync data gs://my-bucket/data

To recurse into directories use --recursive:

    $ gcloud storage rsync data gs://my-bucket/data --recursive

To make the local directory my-data the same as the contents of
gs://mybucket/data and delete objects in the local directory that are not
in gs://mybucket/data:

    $ gcloud storage rsync gs://mybucket/data my-data --recursive \
        --delete-unmatched-destination-objects

To make the contents of gs://mybucket2 the same as gs://mybucket1 and
delete objects in gs://mybucket2 that are not in gs://mybucket1:

    $ gcloud storage rsync gs://mybucket1 gs://mybucket2 --recursive \
        --delete-unmatched-destination-objects

To copy all objects from dir1 into dir2 and delete all objects in dir2
which are not in dir1:

    $ gcloud storage rsync dir1 dir2 --recursive - \
        --delete-unmatched-destination-objects

To mirror your objects across cloud providers:

    $ gcloud storage rsync gs://my-gs-bucket s3://my-s3-bucket \
        --recursive --delete-unmatched-destination-objects

To apply gzip compression to only uploaded image files in dir:

    $ gcloud storage rsync dir gs://my-bucket/data \
        --gzip-in-flight=jpeg,jpg,gif,png

To skip the file dir/data1/a.txt:

    $ gcloud storage rsync dir gs://my-bucket --exclude="data./.*\.txt$"

To skip all .txt and .jpg files:

    $ gcloud storage rsync dir gs://my-bucket \
        --exclude=".*\.txt$|.*\.jpg$"
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/rsync)

---
### `gcloud storage service-agent`

Manage a project's Cloud Storage service agent, which is used to perform Cloud KMS operations

gcloud storage service-agent displays the Cloud Storage service agent,
which is used to perform Cloud KMS operations against your a default or
supplied project. If the project does not yet have a service agent, gcloud
storage service-agent creates one.

**Synopsis:**
```
gcloud storage service-agent [--authorize-cmek=AUTHORIZE_CMEK]
    [GCLOUD_WIDE_FLAG ...]
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--authorize-cmek` | AUTHORIZE_CMEK |  | Adds appropriate encrypt/decrypt permissions to the specified Cloud KMS key. This allows the Cloud Storage service agent to write and read Cloud KMS-encrypted objects in buckets associated with the service agent's project. |


**Examples:**
```bash
To show the service agent for your default project:

    $ gcloud storage service-agent

To show the service account for my-project:

    $ gcloud storage service-agent --project=my-project

To authorize your default project to use a Cloud KMS key:

    $ gcloud storage service-agent \
        --authorize-cmek=projects/key-project/locations/us-east1/\
    keyRings/key-ring/cryptoKeys/my-key
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/service-agent)

---
### `gcloud storage sign-url`

Generate a URL with embedded authentication that can be used by anyone

gcloud storage sign-url will generate a signed URL that embeds
authentication data so the URL can be used by someone who does not have a
Google account. Use the global --impersonate-service-account flag to
specify the service account that will be used to sign the specified URL or
authenticate with a service account directly. Otherwise, a service account
key is required. Please see the Signed URLs documentation
(https://cloud.google.com/storage/docs/access-control/signed-urls) for
background about signed URLs.

Note, gcloud storage sign-url does not support operations on
sub-directories. For example, unless you have an object named
some-directory/ stored inside the bucket some-bucket, the following command
returns an error: gcloud storage sign-url gs://some-bucket/some-directory/.

**Synopsis:**
```
gcloud storage sign-url URL [URL ...]
    [--duration=DURATION, -d DURATION; default=3600]
    [--headers=[KEY=VALUE,...]]
    [--http-verb=HTTP_VERB, -m HTTP_VERB; default="GET"] [--path-style-url]
    [--private-key-file=PRIVATE_KEY_FILE]
    [--private-key-password=PRIVATE_KEY_PASSWORD, -p PRIVATE_KEY_PASSWORD]
    [--query-params=[KEY=VALUE,...]] [--region=REGION, -r REGION]
    [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
URL [URL ...]
   The URLs to be signed. May contain wildcards.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--duration` | DURATION, -d DURATION | 3600 | Specifies the duration that the signed url should be valid for, default duration is 1 hour. For example 10s for 10 seconds. See $ gcloud topic datetimes for information on duration formats. The max duration allowed is 12 hours. This limitation exists because the system-managed key used to sign the URL may not remain valid after 12 hours. Alternatively, the max duration allowed is 7 days when signing with either the --private-key-file flag or an account that authorized with gcloud auth activate-service-account. |
| `--headers` | [KEY=VALUE,...] |  | Specifies the headers to be used in the signed request. Possible headers are listed in the XML API's documentation: https://cloud.google.com/storage/docs/xml-api/reference-headers#headers |
| `--http-verb` | HTTP_VERB, -m HTTP_VERB | GET | Specifies the HTTP verb to be authorized for use with the signed URL, default is GET. When using a signed URL to start a resumable upload session, you will need to specify the x-goog-resumable:start header in the request or else signature validation will fail. |
| `--path-style-url` |  |  | Generate path-style signed URL. By default, virtual hosted-style signed URL is generated, except for domain-named buckets (https://cloud.google.com/storage/docs/domain-name-verification). Use this flag to force the generation of path-style signed URL. Signed URL generated for domain-named buckets is always path-style. Learn more about the two URL styles here (https://cloud.google.com/storage/docs/request-endpoints#xml-api). |
| `--private-key-file` | PRIVATE_KEY_FILE |  | The service account private key used to generate the cryptographic signature for the generated URL. Must be in PKCS12 or JSON format. If encrypted, will prompt for the passphrase used to protect the private key file (default notasecret). Note: Service account keys are a security risk if not managed correctly. Review best practices for managing service account keys (https://cloud.google.com/iam/docs/best-practices-for-managing-service-account-keys) before using this option. |
| `--private-key-password` | PRIVATE_KEY_PASSWORD, -p PRIVATE_KEY_PASSWORD |  | Specifies the PRIVATE_KEY_FILE password instead of prompting. |
| `--query-params` | [KEY=VALUE,...] |  | Specifies the query parameters to be used in the signed request. Possible query parameters are listed in the XML API's documentation: https://cloud.google.com/storage/docs/xml-api/reference-headers#query |
| `--region` | REGION, -r REGION |  | Specifies the region in which the resources for which you are creating signed URLs are stored. Default value is auto which will cause gcloud storage sign-url to fetch the region for the resource. When auto-detecting the region, the current user's credentials, not the credentials from PRIVATE_KEY_FILE, are used to fetch the bucket's metadata. |


**Examples:**
```bash
To create a signed url for downloading an object valid for 10 minutes with
the credentials of an impersonated service account:

    $ gcloud storage sign-url gs://my-bucket/file.txt --duration=10m \
        --impersonate-service-account=sa@my-project.iam.gserviceaccount.\
    com

To create a signed url that will bill to my-billing-project when already
authenticated as a service account:

    $ gcloud storage sign-url gs://my-bucket/file.txt \
        --query-params=userProject=my-billing-project

To create a signed url, valid for one hour, for uploading a plain text file
via HTTP PUT:

    $ gcloud storage sign-url gs://my-bucket/file.txt --http-verb=PUT \
        --duration=1h --headers=content-type=text/plain \
        --impersonate-service-account=sa@my-project.iam.gserviceaccount.\
    com

To create a signed URL that initiates a resumable upload for a plain text
file using a private key file:

    $ gcloud storage sign-url gs://my-bucket/file.txt --http-verb=POST \
        --headers=x-goog-resumable=start,content-type=text/plain \
        --private-key-file=key.json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/storage/sign-url)

---