---
id: management-api
title: "Management API"
description: "Zeebe Gateway also exposes an HTTP endpoint for cluster management operations."
---

import Tabs from "@theme/Tabs";
import TabItem from "@theme/TabItem";

Besides the [REST](/apis-tools/zeebe-api-rest/zeebe-api-rest-overview.md) and [gRPC API](/apis-tools/zeebe-api/grpc.md) for process instance execution, Zeebe Gateway also exposes an HTTP endpoint for cluster management operations. This API is not expected to be used by a typical user, but by a privileged user such as a cluster administrator. It is exposed via a different port and configured using configuration `management.server.port` (or via environment variable `MANAGEMENT_SERVER_PORT`). By default, this is set to `9600`.

The API is a custom endpoint available via [Spring Boot Actuator](https://docs.spring.io/spring-boot/docs/current/reference/html/actuator.html#actuator.endpoints). For additional configurations such as security, refer to the Spring Boot documentation.

The following operations are currently available:

- [Rebalancing](/self-managed/zeebe-deployment/operations/rebalancing.md)
- [Pause and resume exporting](#exporting-api)

## Exporting API

Exporting API is used:

- As a debugging tool.
- When taking a backup of Camunda 8 (see [backup and restore](/self-managed/operational-guides/backup-restore/backup-and-restore.md)).

<Tabs groupId="exporting" defaultValue="pause" queryString values={[{label: 'Pause exporting', value: 'pause' },{label: 'Resume exporting', value: 'resume' }]} >

<TabItem value="pause">

To pause exporting on all partitions, send the following request to the gateway's management endpoint.

```
POST actuator/exporting/pause
```

When all partitions pause exporting, a successful response is received. If the request fails, some partitions may have paused exporting. Therefore, it is important to either retry until success or revert the partial pause by resuming exporting.

</TabItem>

<TabItem value="resume">

After exporting is paused, it must eventually be resumed. Otherwise, the cluster could become unavailable. To resume exporting, send the following request to the gateway's management endpoint:

```
POST actuator/exporting/resume
```

When all partitions have resumed exporting, a successful response is received. If the request fails, only some partitions may have resumed exporting. Therefore, it is important to retry until successful.

</TabItem>
</Tabs>
