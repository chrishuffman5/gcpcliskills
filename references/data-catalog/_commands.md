# gcloud data-catalog (top-level commands)

### `gcloud data-catalog search`

Search Data Catalog for resources that match a query

(DEPRECATED) This command is deprecated. Please use gcloud dataplex entries
search instead.

Search Data Catalog for resources that match a query.

**Synopsis:**
```
gcloud data-catalog search QUERY
    (--include-gcp-public-datasets
      --include-organization-ids=[ORGANIZATION,...]
      --include-project-ids=[PROJECT,...]
      --restricted-locations=[LOCATION,...]) [--limit=LIMIT]
    [--order-by=ORDER_BY] [--page-size=PAGE_SIZE] [GCLOUD_WIDE_FLAG ...]
```

**Positional arguments:**
```
QUERY
   Query string in search query syntax in Data Catalog. For more
   information, see:
   https://cloud.google.com/data-catalog/docs/how-to/search-reference
```

**Required flags:**

| Flag | Value | Default | Description |
|------|-------|---------|-------------|
| `--include-gcp-public-datasets` |  |  | _[At least one of these must be specified:]_ If True, include Google Cloud Platform public datasets in the search results. |
| `--include-organization-ids` | [ORGANIZATION,...] |  | _[At least one of these must be specified:]_ List of Cloud Organization IDs to include in the search. |
| `--include-project-ids` | [PROJECT,...] |  | _[At least one of these must be specified:]_ List of Cloud Project IDs to include in the search. |
| `--restricted-locations` | [LOCATION,...] |  | _[At least one of these must be specified:]_ List of locations to search within. |


**Examples:**
```bash
To search project 'my-project' for Data Catalog resources that match the
simple predicate 'foo':

    $ gcloud data-catalog search 'foo' --include-project-ids=my-project

To search organization '1234' for Data Catalog resources that match
entities whose names match the predicate 'foo':

    $ gcloud data-catalog search 'name:foo' \
        --include-organization-ids=1234
```

[Official reference](https://cloud.google.com/sdk/gcloud/reference/data-catalog/search)

---