# Snowplow

Configuration files for creating custom Snowplow event schemas.

## Versioning

Each JSON file living in `conf/` contains a schema for a table. Each file also
contains a [semantic version](https://semver.org/) for the that schema - in the JSON this lives under
`self.version`.

Below we will provide a outline for the strategy of the semantic versions and give some context around previous versions and files.

### Strategy [June 2020]

Filename should contain the table name in
[snake_case](https://en.wikipedia.org/wiki/Snake_case). We can use git to track
the changes and subversions of the file by commit. Each major version should
result in a new table which will require a new file.

`{tablename}.json`

`major.minor.patch` Similar to the semantic docs linked above, but with some
more data context.

1. MAJOR occurs when you make a breaking change to the table, meaning you
   remove/rename columns or completely change the table. This should likely result in a new
table though as their may still be dependencies on the current table (all other
best practices around deprecation should be followed here)
2. MINOR must be backwards compatible - possibly something like adding columns.
3. PATCH must be backwards compatible - possibly something like making
   a column null-able.

### History

Until now (June 2020) we have been using only the `patch` to designate a new
version. In addition, each version requires its own file and is named in the
following manner.

`snowplow_{tablename}_event_schema_{version}.json`

