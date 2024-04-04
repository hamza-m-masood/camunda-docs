---
id: system-configuration-platform-8
title: "Camunda 8 system configuration"
description: "Connection to Camunda 8."
---

### General settings

| YAML path               | Default value | Description                                                                                                                  |
| ----------------------- | ------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| zeebe.enabled           | false         | Toggles whether Optimize should attempt to import data from the connected Zeebe instance.                                    |
| zeebe.name              | zeebe-record  | The name suffix of the exported Zeebe records. This must match the record-prefix configured in the exporter of the instance. |
| zeebe.partitionCount    | 1             | The number of partitions configured for the Zeebe record source.                                                             |
| zeebe.maxImportPageSize | 200           | The max page size for importing Zeebe data.                                                                                  |

### Settings required for multi-tenancy

<span class="badge badge--platform">Camunda 8 Self-Managed only</span>

For more information on multi-tenancy in Camunda 8 Self-Managed environments, refer
to the [multi-tenancy documentation](./multi-tenancy.md).

To use multi-tenancy, the feature must be enabled across all components.

| YAML path                  | Default value | Description                                              |
| -------------------------- | ------------- | -------------------------------------------------------- |
| multitenancy.enabled       | false         | Enables the Camunda 8 multi-tenancy feature in Optimize. |
| security.auth.ccsm.baseUrl | null          | The base URL of Identity.                                |

### Settings related to Camunda 8 native UserTasks

<span class="badge badge--platform">Camunda 8 Self-Managed only</span>

For more information on user task reporting in Camunda 8 Self-Managed, refer to the [task analysis documentation](../../../components/userguide/process-analysis/task-analysis.md).

| YAML path                           | Default value | Description                                                          |
| ----------------------------------- | ------------- | -------------------------------------------------------------------- |
| ui.userTaskAssigneeAnalyticsEnabled | true          | Enables assignee-based analytics in Camunda 8 Self-Managed Optimize. |
