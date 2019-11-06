# sandbox_hasura_migrations

## env

> If you need to use sandbox not only for hasura gql, pls make PR.

In process environment must be defined:

```sh
HASURA_SECRET='<x-hasura-admin-secret>'
HASURA_PATH='<gqlurl>'
POSTGRES='<postgresurl>'
```

## sql

#### find all parent nodes ids of nodeId

```sql
SELECT "links_indexes"."index_node_id"
FROM "links_indexes" as "li1"
WHERE
"li1"."list_node_id" = '${nodeId}' AND
"li1"."index_node_id" != '${nodeId}';
```

#### find all children

```sql
SELECT "l1"."target_id"
FROM "links" as "l1"
WHERE "l1"."source_id" = '${nodeId}'
```
