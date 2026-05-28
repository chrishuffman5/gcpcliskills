# gcloud spanner (top-level commands)

### `gcloud spanner cli`

An interactive shell for Spanner

An interactive shell for Spanner.

**Synopsis:**
```
gcloud spanner cli (DATABASE : --instance=INSTANCE)
    [--database-role=DATABASE_ROLE] [--delimiter=DELIMITER; default=";"]
    [--directed-read=DIRECTED_READ] [--execute=EXECUTE]
    [--host=HOST; default="localhost"] [--html]
    [--idle-transaction-timeout=IDLE_TRANSACTION_TIMEOUT; default=60]
    [--init-command=INIT_COMMAND] [--init-command-add=INIT_COMMAND_ADD]
    [--port=PORT] [--prompt=PROMPT; default="spanner-cli> "]
    [--proto-descriptor-file=PROTO_DESCRIPTOR_FILE] [--skip-column-names]
    [--skip-system-command] [--source=SOURCE]
    [--system-command=SYSTEM_COMMAND; default="ON"] [--table] [--tee=TEE]
    [--xml] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
Database resource - The Cloud Spanner database to use within the
interactive shell. The arguments in this group can be used to specify the
attributes of this resource. (NOTE) Some attributes are not given
arguments in this group but can be set in other ways.

To set the project attribute:
 * provide the argument database on the command line with a fully
   specified name;
 * provide the argument --project on the command line;
 * set the property core/project.

This must be specified.

  DATABASE
     ID of the database or fully qualified identifier for the database.

     To set the database attribute:
     + provide the argument database on the command line.

     This positional argument must be specified if any of the other
     arguments in this group are specified.

  --instance=INSTANCE
     The Cloud Spanner instance for the database.

     To set the instance attribute:
     + provide the argument database on the command line with a fully
       specified name;
     + provide the argument --instance on the command line;
     + set the property spanner/instance.
```

**Optional flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--database-role` | DATABASE_ROLE |  | Database role user used to access the database. |
| `--delimiter` | DELIMITER |  | Set the statement delimiter. |
| `--directed-read` | DIRECTED_READ |  | Enables directed reads to provide the flexibility to route read-only transactions and single reads to a specific replica type or region (replica_location:replica_type). The replica_type is optional and can be either READ_ONLY or READ_WRITE. |
| `--execute` | EXECUTE |  | Execute the statement and then exits. |
| `--host` | HOST | localhost | Host on which Spanner server is located. |
| `--html` |  |  | Show output in HTML format. |
| `--idle-transaction-timeout` | IDLE_TRANSACTION_TIMEOUT | 60 | Set the idle transaction timeout. The default timeout is 60 seconds. |
| `--init-command` | INIT_COMMAND |  | SQL statement to execute after startup. |
| `--init-command-add` | INIT_COMMAND_ADD |  | Additional SQL statement to execute after startup. |
| `--port` | PORT |  | Port number that gcloud uses to connect to Spanner. |
| `--prompt` | PROMPT | spanner-cli> | Set the prompt to the specified format. |
| `--proto-descriptor-file` | PROTO_DESCRIPTOR_FILE |  | Path of a file that contains a protobuf-serialized google.protobuf.FileDescriptorSet message to use in this invocation. |
| `--skip-column-names` |  |  | Do not show column names in output. |
| `--skip-system-command` |  |  | Do not allow system command. |
| `--source` | SOURCE |  | Execute the statement from a file and then exits. |
| `--system-command` | one of: ON, OFF | ON | Enable or disable system commands. Default: ON. SYSTEM_COMMAND must be one of: ON, OFF. |
| `--table` |  |  | Show output in table format. |
| `--tee` | TEE |  | Append a copy of the output to a named file. |
| `--xml` |  |  | Show output in XML format. |


**Examples:**
```bash
To start an interactive shell with your Spanner example database, run the
following command:

    $ gcloud spanner cli example-database --instance=example-instance
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/spanner/cli)

---