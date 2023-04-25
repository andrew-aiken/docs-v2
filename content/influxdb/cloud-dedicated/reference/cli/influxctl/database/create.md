---
title: influxctl database create
description: >
  The `influxctl database create` command creates a new database in an InfluxDB
  Cloud Dedicated cluster.
menu:
  influxdb_cloud_dedicated:
    parent: influxctl database
weight: 301
---

The `influxctl database create` command creates a new database with a specified
retention period in an InfluxDB Cloud Dedicated cluster.

The retention period defines the maximum age of data retained in the database,
based on the timestamp of the data.
The retention period value is a time duration value made up of a numeric value
plus a duration unit. For example, `30d` means 30 days.
A zero duration retention period is infinite and data will not expire.
The retention period value cannot be negative or contain whitespace.

{{< flex >}}
{{% flex-content %}}

##### Valid durations units include

- **m**: minute
- **h**: hour
- **d**: day
- **w**: week
- **mo**: month
- **y**: year

{{% /flex-content %}}
{{% flex-content %}}

##### Example retention period values

- `0d`: infinite/none
- `3d`: 3 days
- `6w`: 6 weeks
- `1mo`: 1 month (30 days)
- `1y`: 1 year
- `30d30d`: 60 days
- `2.5d`: 60 hours

{{% /flex-content %}}
{{< /flex >}}

## Usage

```sh
influxctl database create [--retention-period 0s] <DATABASE_NAME>
```

## Arguments

| Argument          | Description            |
| :---------------- | :--------------------- |
| **DATABASE_NAME** | InfluxDB database name |

## Flags

| Flag |                      | Description                                           |
| :--- | :------------------- | :---------------------------------------------------- |
| `-h` | `--help`             | Output command help                                   |
|      | `--retention-period` | Database retention period (default is 0s or infinite) |

## Examples

- [Create a database with an infinite retention period](#create-a-database-with-an-infinite-retention-period)
- [Create a database with a 30 day retention period](#create-a-database-with-a-30-day-retention-period)

##### Create a database with an infinite retention period

```sh
influxctl database create mydb
```

##### Create a database with a 30 day retention period

```sh
influxctl database create \
  --retention-period 30d \
  mydb
```