# Mysqldump + aws s3 store

Helm chart to install cronjob to backup database(s) base on docker container from here:
- https://github.com/databacker/mysql-backup

## Installation

1. Install repo:

```
helm repo add mysql-backup https://zenithtecnologia.github.io/helm-mysql-backup/
```

## Configuration

Miniamal values.yaml file:

```
  mysql:
    host: "db host name"
    username: "root"
    password: "myrootpassword"
    port: 3306
    dbNames: "db1,db2"

  schedule: "00 01 * * *"

  s3:
    accessKeyId: "access key id"
    accessKeySecret: "access key secret"
    defaultRegion: "uswest-1"
    destination: "bucket/path/to/backup"
```

## Custom s3 compatible object stores
This chart also supports custom s3 endpoint. This makes it possible to use with digitalocean spaces, i.e:

```
mysql:
  ...

schedule: ...

s3:
  accessKeyId: "access key id"
  accessKeySecret: "access key secret"
  endpointUrl: "https://fra1.digitaloceanspaces.com/"
  destination: "bucket/path/to/backup"
```
