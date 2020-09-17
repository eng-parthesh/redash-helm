# Redash Helm Chart

* Install the [redash](https://redash.io/) on kubernetes

## TL;DR;

```console
$ helm install stable/redash-helm
```

## Install

To install the chart with the release name `my-release`:

```console
$ helm install --name my-release stable/redash-helm
```

Note: for fresh install `createDB: true` and `upgradeDB: false`

## Uninstall

To uninstall/delete the my-release deployment:

```console
$ helm delete my-release
```

The command removes all the Kubernetes components associated with the chart and deletes the release.


## Configuration

| Parameter                                 | Description                            |Default             |
|-------------------------------------------|----------------------------------------|--------------------|
| `nameOverride`                            | Name override                          | `Name` |
| `replicaCount`                            | Number of nodes                        | `1` |
| `image.repository`                        | Imgage repository                      | `redash/redash` |
| `image.tag`                               | Image tag                              | `latest` |
| `image.pullPolicy`                        | Image pull policy                      | `IfNotPresent`
| `service.type`                            | Kubernetes service type                | `ClusterIP` |
| `web.workersCount`                        | Redash web ui server worker count      | `1` |
| `scheduledWorker.workersCount`            | Redash scheduled_queries worker count  | `1` |
| `adhocWorker.workersCount`                | Redash queries worker count            | `1` |
| `scheduled.workersCount`                  | Redash celery worker count             | `1` |
| `resources`                               | Resources for each pod                 | `{}` |
| `mail.server`                             | Mail server url                        | `` |
| `mail.port`                               | Mail server port                       | `` |
| `mail.useTls`                             | Mail server TLS                        | `` |
| `mail.useSSL`                             | Mail server SSL                        | `` |
| `mail.username`                           | Mail server username                   | `` |
| `mail.password`                           | Mail server password                   | `` |
| `mail.defaultSender`                      | Default mail sender                    | `` |
| `mail.maxEmails`                          | Default maxEmails                      | `` |
| `mail.asciiAttachments`                   | Default asciiAttachments               | `false` |
| `redashName`                              | Redash name                            | `Redash` |
| `redashStaticAssetsPath`                  | Redash assets path                     | `../client/dist/` |
| `redashCookieSecret`                      | Redash cookie secret                   | `secret token` |
| `redashEnforceHTTPs`                      | Enforce HTTPs                          | `false` |
| `redashJobExpiryTime`                     | Job expiry time                        | `300` |
| `redashAdhocQueryTimeLimit`               | Ad-hoc query time limit                       | `300` |
| `redashFeatureShowPermissionsControl`     | Redash permissions control             | `false` |
| `logLevel`                                | Redash loglevel                        | `DEBUG` |
| `extraEnvironment`                        | Extra environment variable             | `{}` |
| `googleOAuth.enabled`                     | Google OAuth enabled                   | `false` |
| `googleOAuth.redashGoogleClientId`        | Google client ID                       | `ClientId` |
| `googleOAuth.redashGoogleClientSecret`    | Google client secret                   | `ClientSecret` |
| `googleOAuth.redashPasswordLoginEnabled`  | Redash password login enabled          | `false` |
| `redis.enabled`                           | Redis instance                         | `true` |
| `redis.usePassword`                     | Redis password                         | `false` |
| `externalRedis.enabled`                   | External redis instance                | `false` |
| `externalRedis.RedisPassword`             | External redis password                | `` |
| `externalRedis.RedisHost`                 | External redis host                    | `` |
| `externalRedis.RedisPort`                 | External redis port                    | `` |
| `externalRedis.RedisDb`                   | External redis db                      | `` |
| `createDB`                          | If true, Create database table         | `true` |
| `upgradeDB`                          | If true, Upgrade database schema         | `false` |
| `ingress.enabled`                         | If true, Ingress will be created       | `false` |
| `ingress.annotations`                     | alertmanager Ingress annotations       | `{}` |
| `ingress.labels`                          | Ingress additional labels              | `{}` |
| `ingress.path`                            | Ingress path                           | `\` |
| `ingress.hosts`                           | Ingress hostnames                      | `[]` |
| `ingress.tls`                             | Ingress TLS configuration (YAML)       | `[]` |
| `nodeSelector`                            | node labels for pod assignment         | `{}` |
| `tolerations`                             | node taints to tolerate                | `[]` |
| `affinity`                                | pod affinity                           | `{}` |
| `postgresql.enabled`                      | Postgres helm dependency               | `true` |
| `postgresql.persistence.enabled`          | Postgres persistence volume            | `false` |
| `postgresql.postgresqlUsername`           | Postgres username                      | `` |
| `postgresql.postgresqlPassword`           | Postgres password                      | `` |
| `postgresql.postgresqlDatabase`           | Postgres database                      | `` |
| `externalPostgres.enabled`                | External postgres database             | `false` |
| `externalPostgres.postgresqlHost`         | External postgres host                 | `` |
| `externalPostgres.postgresqlPort`         | External postgres port                 | `` |
| `externalPostgres.postgresqlUsername`     | Postgres username                      | `` |
| `externalPostgres.postgresqlPassword`     | Postgres password                      | `` |
| `externalPostgres.postgresqlDatabase`     | Postgres database                      | `` |

## Upgrade

- change redash version
- set `upgradeDB: true`
