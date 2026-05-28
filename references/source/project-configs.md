# gcloud source project-configs

manage Cloud Source Repositories configuration of a project

### `gcloud source project-configs describe`

Show details about the configuration of a project

Show details about the configuration of a project.

**Synopsis:**
```
gcloud source project-configs describe [GCLOUD_WIDE_FLAG ...]
```

**Examples:**
```bash
To show the current configuration of the current project run:

    $ gcloud source project-configs describe
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/source/project-configs/describe)

---
### `gcloud source project-configs update`

Update the Cloud Source Repositories configuration of the current project

**Synopsis:**
```
gcloud source project-configs update
    (--disable-pushblock | --enable-pushblock
      | --message-format=MESSAGE_FORMAT --service-account=SERVICE_ACCOUNT
      --topic-project=TOPIC_PROJECT --add-topic=ADD_TOPIC
      | --remove-topic=REMOVE_TOPIC | --update-topic=UPDATE_TOPIC)
    [GCLOUD_WIDE_FLAG ...]
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--disable-pushblock` |  |  | _[Exactly one of these must be specified:]_ Disable PushBlock for all repositories under current project. PushBlock allows repository owners to block git push transactions containing private key data. |
| `--enable-pushblock` |  |  | _[Exactly one of these must be specified:]_ Enable PushBlock for all repositories under current project. PushBlock allows repository owners to block git push transactions containing private key data. |


**Examples:**
```bash
To enable PushBlock for all repositories under current project, run:

    $ gcloud source project-configs update --enable-pushblock

To associate a Cloud Pub/Sub topic to receive repository update
notifications, run:

    $ gcloud source project-configs update --add-topic=TOPIC_NAME \
        --service-account=SERVICE_ACCOUNT_EMAIL --message-format=json
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/source/project-configs/update)

---