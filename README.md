# identity-workflow

This repository provides the necessary configurations to enable workflow support in **WSO2 Identity Server**.

## Deployment Configuration

Add the following configurations to the `deployment.toml` file in order to enable the required API scopes and console features.

### Workflow Management API Scopes 

```toml
[[api_resources]]
name = "Workflow Management API"
identifier = "/api/server/v1/workflows"
requiresAuthorization = true
type = "TENANT"
description = "API representation of the Workflow Management API"

[[api_resources.scopes]]
displayName = "View Workflow"
name = "internal_workflow_view"

[[api_resources.scopes]]
displayName = "Create Workflow"
name = "internal_workflow_create"

[[api_resources.scopes]]
displayName = "Update Workflow"
name = "internal_workflow_update"

[[api_resources.scopes]]
displayName = "Delete Workflow"
name = "internal_workflow_delete"
```

### Workflow Association Management API Scopes 

```toml
[[api_resources]]
name = "Workflow Association Management API"
identifier = "/api/server/v1/workflow-associations"
requiresAuthorization = true
type = "TENANT"
description = "API representation of the Workflow Association Management API"

[[api_resources.scopes]]
displayName = "View Workflow Association"
name = "internal_workflow_association_view"

[[api_resources.scopes]]
displayName = "Create Workflow Association"
name = "internal_workflow_association_create"

[[api_resources.scopes]]
displayName = "Update Workflow Association"
name = "internal_workflow_association_update"

[[api_resources.scopes]]
displayName = "Delete Workflow Association"
name = "internal_workflow_association_delete"

```

### Workflow Approvals API Scopes

```toml
[[api_resources]]
name = "Workflow Approval API"
identifier = "/me/approval-tasks"
requiresAuthorization = true
type = "TENANT"
description = "API representation of the workflow Approval API"

[[api_resources.scopes]]
displayName = "View Workflow Approvals"
name = "internal_humantask_view"
```

### Resource Access Control Configurations

```toml
[[resource.access_control]]
context = "(.*)/api/server/v1/workflows(.*)"
secure = true
http_method = "GET"
scopes = ["internal_workflow_view"]

[[resource.access_control]]
context = "(.*)/api/server/v1/workflows(.*)"
secure = true
http_method = "POST"
scopes = ["internal_workflow_create"]

[[resource.access_control]]
context = "(.*)/api/server/v1/workflows(.*)"
secure = true
http_method = "PUT"
scopes = ["internal_workflow_update"]

[[resource.access_control]]
context = "(.*)/api/server/v1/workflows(.*)"
secure = true
http_method = "DELETE"
scopes = ["internal_workflow_delete"]

[[resource.access_control]]
context = "(.*)/api/server/v1/workflow-associations(.*)"
secure = true
http_method = "GET"
scopes = ["internal_workflow_association_view"]

[[resource.access_control]]
context = "(.*)/api/server/v1/workflow-associations(.*)"
secure = true
http_method = "POST"
scopes = ["internal_workflow_association_create"]

[[resource.access_control]]
context = "(.*)/api/server/v1/workflow-associations(.*)"
secure = true
http_method = "PUT"
scopes = ["internal_workflow_association_update"]

[[resource.access_control]]
context = "(.*)/api/server/v1/workflow-associations(.*)"
secure = true
http_method = "DELETE"
scopes = ["internal_workflow_association_delete"]
```

### Console features

```toml
[console.approvals]
enabled=true

[console.workflows]
enabled=true
```

