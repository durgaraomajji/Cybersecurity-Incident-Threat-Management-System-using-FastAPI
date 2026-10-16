# Swagger / OpenAPI verification

Verified against the live server at `http://127.0.0.1:8000` (OpenAPI 3.1.0, API version 1.0.0).

## Checks

| Result | Check | Detail |
|---|---|---|
| PASS | OpenAPI document validates against the specification | OpenAPI 3.1.0 |
| PASS | Swagger UI served at /docs |  |
| PASS | ReDoc served at /redoc |  |
| PASS | 'Authorize' button: OAuth2 password flow declared | {'scopes': {}, 'tokenUrl': '/api/v1/auth/token'} |
| PASS | Token endpoint accepts the Swagger form login |  |
| PASS | Every operation has a summary | 167 operations |
| PASS | Every operation documents a 2xx response |  |
| PASS | Every non-public operation declares security |  |
| PASS | Protected operations document 401/403/404/409 error envelopes |  |
| PASS | All tags are described | [] |
| PASS | Real responses conform to documented schemas | 47 validated, 0 mismatches |

## Surface: 167 operations / 135 paths / 203 schemas

### Authentication

| Method | Path | Summary | Auth | Success | Errors |
|---|---|---|---|---|---|
| POST | `/api/v1/auth/change-password` | Change own password | Bearer | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/auth/login` | Log in (JSON) | public | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/auth/logout` | Log out and invalidate the tokens | Bearer | 200 | 400,401,403,404,409,422 |
| GET | `/api/v1/auth/me` | Current user | Bearer | 200 | 400,401,403,404,409 |
| POST | `/api/v1/auth/password-reset/confirm` | Set a new password with a reset token | public | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/auth/password-reset/request` | Request a password reset | public | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/auth/refresh` | Rotate tokens with a refresh token | public | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/auth/register` | Register an account | public | 201 | 400,401,403,404,409,422 |
| POST | `/api/v1/auth/token` | Log in (OAuth2 form, used by Swagger 'Authorize') | public | 200 | 400,401,403,404,409,422 |

### Users

| Method | Path | Summary | Auth | Success | Errors |
|---|---|---|---|---|---|
| GET | `/api/v1/users` | List users | Bearer | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/users` | Create a user | Bearer | 201 | 400,401,403,404,409,422 |
| GET | `/api/v1/users/{user_id}` | Get a user | Bearer | 200 | 400,401,403,404,409,422 |
| PATCH | `/api/v1/users/{user_id}` | Update a user | Bearer | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/users/{user_id}/activate` | Activate an account | Bearer | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/users/{user_id}/deactivate` | Deactivate an account | Bearer | 200 | 400,401,403,404,409,422 |
| PUT | `/api/v1/users/{user_id}/role` | Assign a role | Bearer | 200 | 400,401,403,404,409,422 |

### Roles & Permissions

| Method | Path | Summary | Auth | Success | Errors |
|---|---|---|---|---|---|
| GET | `/api/v1/roles` | List roles with their permissions | Bearer | 200 | 400,401,403,404,409 |
| POST | `/api/v1/roles` | Create a custom role | Bearer | 201 | 400,401,403,404,409,422 |
| GET | `/api/v1/roles/permissions` | List every permission in the system | Bearer | 200 | 400,401,403,404,409 |
| DELETE | `/api/v1/roles/{role_id}` | Delete a custom role | Bearer | 200 | 400,401,403,404,409,422 |
| GET | `/api/v1/roles/{role_id}` | Get a role | Bearer | 200 | 400,401,403,404,409,422 |
| PUT | `/api/v1/roles/{role_id}/permissions` | Replace a role's permission set | Bearer | 200 | 400,401,403,404,409,422 |

### Organizations

| Method | Path | Summary | Auth | Success | Errors |
|---|---|---|---|---|---|
| GET | `/api/v1/organizations` | List organizations | Bearer | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/organizations` | Register an organization | Bearer | 201 | 400,401,403,404,409,422 |
| GET | `/api/v1/organizations/{organization_id}` | Get an organization | Bearer | 200 | 400,401,403,404,409,422 |
| PATCH | `/api/v1/organizations/{organization_id}` | Update an organization | Bearer | 200 | 400,401,403,404,409,422 |

### Departments

| Method | Path | Summary | Auth | Success | Errors |
|---|---|---|---|---|---|
| GET | `/api/v1/departments` | List departments | Bearer | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/departments` | Register a department | Bearer | 201 | 400,401,403,404,409,422 |
| GET | `/api/v1/departments/{department_id}` | Get a department | Bearer | 200 | 400,401,403,404,409,422 |
| PATCH | `/api/v1/departments/{department_id}` | Update a department | Bearer | 200 | 400,401,403,404,409,422 |
| GET | `/api/v1/departments/{department_id}/assets` | View assets by department | Bearer | 200 | 400,401,403,404,409,422 |

### Security Teams

| Method | Path | Summary | Auth | Success | Errors |
|---|---|---|---|---|---|
| GET | `/api/v1/teams` | List teams | Bearer | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/teams` | Create a security team | Bearer | 201 | 400,401,403,404,409,422 |
| GET | `/api/v1/teams/{team_id}` | Get a team with its members | Bearer | 200 | 400,401,403,404,409,422 |
| PATCH | `/api/v1/teams/{team_id}` | Update a team | Bearer | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/teams/{team_id}/members` | Assign an analyst to the team | Bearer | 200 | 400,401,403,404,409,422 |
| DELETE | `/api/v1/teams/{team_id}/members/{user_id}` | Remove a member from the team | Bearer | 200 | 400,401,403,404,409,422 |

### Assets

| Method | Path | Summary | Auth | Success | Errors |
|---|---|---|---|---|---|
| GET | `/api/v1/assets` | Search and filter assets | Bearer | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/assets` | Register an asset (server, endpoint, application or database) | Bearer | 201 | 400,401,403,404,409,422 |
| GET | `/api/v1/assets/{asset_id}` | Get an asset | Bearer | 200 | 400,401,403,404,409,422 |
| PATCH | `/api/v1/assets/{asset_id}` | Update an asset | Bearer | 200 | 400,401,403,404,409,422 |
| GET | `/api/v1/assets/{asset_id}/history` | Asset change history | Bearer | 200 | 400,401,403,404,409,422 |
| PUT | `/api/v1/assets/{asset_id}/owner` | Assign (or clear) the asset owner | Bearer | 200 | 400,401,403,404,409,422 |
| PATCH | `/api/v1/assets/{asset_id}/status` | Change the asset status | Bearer | 200 | 400,401,403,404,409,422 |

### Security Alerts

| Method | Path | Summary | Auth | Success | Errors |
|---|---|---|---|---|---|
| GET | `/api/v1/alerts` | Search, filter, sort and paginate alerts | Bearer | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/alerts` | Create a security alert | Bearer | 201 | 400,401,403,404,409,422 |
| GET | `/api/v1/alerts/{alert_id}` | Get an alert | Bearer | 200 | 400,401,403,404,409,422 |
| PATCH | `/api/v1/alerts/{alert_id}` | Update an alert | Bearer | 200 | 400,401,403,404,409,422 |
| PUT | `/api/v1/alerts/{alert_id}/assignee` | Assign (or un-assign) an alert | Bearer | 200 | 400,401,403,404,409,422 |
| PATCH | `/api/v1/alerts/{alert_id}/status` | Change the alert status | Bearer | 200 | 400,401,403,404,409,422 |

### Alert Correlation

| Method | Path | Summary | Auth | Success | Errors |
|---|---|---|---|---|---|
| GET | `/api/v1/correlations` | List correlation groups | Bearer | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/correlations` | Group related alerts manually | Bearer | 201 | 400,401,403,404,409,422 |
| POST | `/api/v1/correlations/auto` | Group repeated alerts automatically | Bearer | 200 | 400,401,403,404,409,422 |
| GET | `/api/v1/correlations/repeated-alerts` | Identify repeated alerts affecting the same asset | Bearer | 200 | 400,401,403,404,409,422 |
| GET | `/api/v1/correlations/{correlation_id}` | Get a correlation group | Bearer | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/correlations/{correlation_id}/alerts` | Add alerts to a correlation | Bearer | 200 | 400,401,403,404,409,422 |
| DELETE | `/api/v1/correlations/{correlation_id}/alerts/{alert_id}` | Remove an alert from a correlation | Bearer | 200 | 400,401,403,404,409,422 |
| GET | `/api/v1/correlations/{correlation_id}/history` | Correlation history | Bearer | 200 | 400,401,403,404,409,422 |

### Incidents

| Method | Path | Summary | Auth | Success | Errors |
|---|---|---|---|---|---|
| GET | `/api/v1/incidents` | List incidents | Bearer | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/incidents` | Create an incident (from alerts, a correlation group, or manually) | Bearer | 201 | 400,401,403,404,409,422 |
| GET | `/api/v1/incidents/{incident_id}` | Get an incident with its linked alerts | Bearer | 200 | 400,401,403,404,409,422 |
| PATCH | `/api/v1/incidents/{incident_id}` | Update an incident | Bearer | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/incidents/{incident_id}/alerts` | Link more alerts to the incident | Bearer | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/incidents/{incident_id}/assign` | Assign a responsible analyst | Bearer | 200 | 400,401,403,404,409,422 |
| GET | `/api/v1/incidents/{incident_id}/assignments` | Assignment history | Bearer | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/incidents/{incident_id}/closure/approve` | Approve closure | Bearer | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/incidents/{incident_id}/closure/reject` | Reject closure | Bearer | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/incidents/{incident_id}/closure/request` | Request closure approval | Bearer | 200 | 400,401,403,404,409,422 |
| GET | `/api/v1/incidents/{incident_id}/history` | Incident history | Bearer | 200 | 400,401,403,404,409,422 |
| GET | `/api/v1/incidents/{incident_id}/notes` | Investigation notes | Bearer | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/incidents/{incident_id}/notes` | Add an investigation note | Bearer | 201 | 400,401,403,404,409,422 |
| GET | `/api/v1/incidents/{incident_id}/related` | Related incidents | Bearer | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/incidents/{incident_id}/related` | Mark another incident as related | Bearer | 201 | 400,401,403,404,409,422 |
| POST | `/api/v1/incidents/{incident_id}/resolve` | Resolve an incident | Bearer | 200 | 400,401,403,404,409,422 |
| PATCH | `/api/v1/incidents/{incident_id}/status` | Change the incident status | Bearer | 200 | 400,401,403,404,409,422 |

### Search

| Method | Path | Summary | Auth | Success | Errors |
|---|---|---|---|---|---|
| GET | `/api/v1/search` | Search incidents and alerts together | Bearer | 200 | 400,401,403,404,409,422 |

### Vulnerabilities

| Method | Path | Summary | Auth | Success | Errors |
|---|---|---|---|---|---|
| GET | `/api/v1/vulnerabilities` | Search and filter vulnerabilities | Bearer | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/vulnerabilities` | Record a vulnerability (optionally mapped to affected assets) | Bearer | 201 | 400,401,403,404,409,422 |
| GET | `/api/v1/vulnerabilities/{vulnerability_id}` | Get a vulnerability | Bearer | 200 | 400,401,403,404,409,422 |
| PATCH | `/api/v1/vulnerabilities/{vulnerability_id}` | Update a vulnerability | Bearer | 200 | 400,401,403,404,409,422 |
| GET | `/api/v1/vulnerabilities/{vulnerability_id}/assets` | Affected assets | Bearer | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/vulnerabilities/{vulnerability_id}/assets` | Map the vulnerability to affected assets | Bearer | 201 | 400,401,403,404,409,422 |
| GET | `/api/v1/vulnerabilities/{vulnerability_id}/history` | Vulnerability history | Bearer | 200 | 400,401,403,404,409,422 |
| PATCH | `/api/v1/vulnerabilities/{vulnerability_id}/status` | Change the status | Bearer | 200 | 400,401,403,404,409,422 |

### Risk Assessment

| Method | Path | Summary | Auth | Success | Errors |
|---|---|---|---|---|---|
| GET | `/api/v1/risks/acceptances` | Risk acceptances | Bearer | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/risks/acceptances` | Formally accept the risk of a vulnerability on an asset | Bearer | 201 | 400,401,403,404,409,422 |
| POST | `/api/v1/risks/acceptances/{acceptance_id}/revoke` | Revoke a risk acceptance | Bearer | 200 | 400,401,403,404,409,422 |
| GET | `/api/v1/risks/assessments` | Risk assessments | Bearer | 200 | 400,401,403,404,409,422 |
| GET | `/api/v1/risks/assets/{asset_id}` | Risk summary of one asset | Bearer | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/risks/calculate` | Calculate / re-calculate risk scores | Bearer | 200 | 400,401,403,404,409,422 |
| GET | `/api/v1/risks/formula` | The documented risk-scoring formula | Bearer | 200 | 400,401,403,404,409 |
| GET | `/api/v1/risks/high-risk-assets` | Highest-risk assets | Bearer | 200 | 400,401,403,404,409,422 |

### Remediation

| Method | Path | Summary | Auth | Success | Errors |
|---|---|---|---|---|---|
| GET | `/api/v1/remediation/tasks` | Search and filter remediation tasks | Bearer | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/remediation/tasks` | Create a remediation task for a vulnerability | Bearer | 201 | 400,401,403,404,409,422 |
| GET | `/api/v1/remediation/tasks/{task_id}` | Get a remediation task | Bearer | 200 | 400,401,403,404,409,422 |
| PATCH | `/api/v1/remediation/tasks/{task_id}` | Update a remediation task | Bearer | 200 | 400,401,403,404,409,422 |
| GET | `/api/v1/remediation/tasks/{task_id}/approvals` | Approval decisions | Bearer | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/remediation/tasks/{task_id}/approve` | Approve the remediation | Bearer | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/remediation/tasks/{task_id}/cancel` | Cancel the task | Bearer | 200 | 400,401,403,404,409,422 |
| GET | `/api/v1/remediation/tasks/{task_id}/evidence` | Task evidence | Bearer | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/remediation/tasks/{task_id}/evidence` | Attach evidence of the fix | Bearer | 201 | 400,401,403,404,409,422 |
| GET | `/api/v1/remediation/tasks/{task_id}/history` | Task history | Bearer | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/remediation/tasks/{task_id}/reject` | Reject the remediation | Bearer | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/remediation/tasks/{task_id}/start` | Start work on the task | Bearer | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/remediation/tasks/{task_id}/submit` | Submit the fix for approval | Bearer | 200 | 400,401,403,404,409,422 |

### Investigations

| Method | Path | Summary | Auth | Success | Errors |
|---|---|---|---|---|---|
| GET | `/api/v1/investigations` | List investigations | Bearer | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/investigations` | Open an investigation | Bearer | 201 | 400,401,403,404,409,422 |
| GET | `/api/v1/investigations/{investigation_id}` | Get an investigation | Bearer | 200 | 400,401,403,404,409,422 |
| PATCH | `/api/v1/investigations/{investigation_id}` | Update an investigation | Bearer | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/investigations/{investigation_id}/close` | Close a completed investigation | Bearer | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/investigations/{investigation_id}/complete` | Complete the investigation with a summary of findings | Bearer | 200 | 400,401,403,404,409,422 |
| GET | `/api/v1/investigations/{investigation_id}/evidence` | List evidence (access is audited) | Bearer | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/investigations/{investigation_id}/evidence` | Register evidence | Bearer | 201 | 400,401,403,404,409,422 |
| GET | `/api/v1/investigations/{investigation_id}/evidence/{evidence_id}` | Get one piece of evidence (access is audited) | Bearer | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/investigations/{investigation_id}/links` | Link incidents, alerts and assets | Bearer | 200 | 400,401,403,404,409,422 |
| GET | `/api/v1/investigations/{investigation_id}/notes` | Investigation notes and events | Bearer | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/investigations/{investigation_id}/notes` | Add an investigation note | Bearer | 201 | 400,401,403,404,409,422 |
| PUT | `/api/v1/investigations/{investigation_id}/owner` | Change the owner | Bearer | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/investigations/{investigation_id}/start` | Start the investigation | Bearer | 200 | 400,401,403,404,409,422 |

### Response Playbooks

| Method | Path | Summary | Auth | Success | Errors |
|---|---|---|---|---|---|
| GET | `/api/v1/playbooks` | List playbooks | Bearer | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/playbooks` | Create a playbook | Bearer | 201 | 400,401,403,404,409,422 |
| GET | `/api/v1/playbooks/executions` | List playbook executions | Bearer | 200 | 400,401,403,404,409,422 |
| GET | `/api/v1/playbooks/executions/{execution_id}` | Get an execution | Bearer | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/playbooks/executions/{execution_id}/cancel` | Cancel a running execution | Bearer | 200 | 400,401,403,404,409,422 |
| GET | `/api/v1/playbooks/executions/{execution_id}/history` | Execution history | Bearer | 200 | 400,401,403,404,409,422 |
| GET | `/api/v1/playbooks/tasks/mine` | My playbook tasks | Bearer | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/playbooks/tasks/{task_id}/approve` | Approve a sensitive step | Bearer | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/playbooks/tasks/{task_id}/assign` | Assign a task to an analyst | Bearer | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/playbooks/tasks/{task_id}/complete` | Complete a task (the action is simulated) | Bearer | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/playbooks/tasks/{task_id}/reject` | Reject a sensitive step | Bearer | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/playbooks/tasks/{task_id}/start` | Start a task | Bearer | 200 | 400,401,403,404,409,422 |
| GET | `/api/v1/playbooks/{playbook_id}` | Get a playbook | Bearer | 200 | 400,401,403,404,409,422 |
| PATCH | `/api/v1/playbooks/{playbook_id}` | Update a playbook | Bearer | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/playbooks/{playbook_id}/execute` | Run a playbook against an incident (simulated) | Bearer | 201 | 400,401,403,404,409,422 |
| PUT | `/api/v1/playbooks/{playbook_id}/steps` | Replace the playbook steps | Bearer | 200 | 400,401,403,404,409,422 |

### SLA Management

| Method | Path | Summary | Auth | Success | Errors |
|---|---|---|---|---|---|
| GET | `/api/v1/slas/approaching` | Incidents approaching a deadline | Bearer | 200 | 400,401,403,404,409,422 |
| GET | `/api/v1/slas/breached` | Incidents that breached an SLA | Bearer | 200 | 400,401,403,404,409,422 |
| GET | `/api/v1/slas/escalated` | Escalated incidents | Bearer | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/slas/evaluate` | Evaluate all open incidents now | Bearer | 200 | 400,401,403,404,409 |
| GET | `/api/v1/slas/incidents/{incident_id}` | SLA of an incident | Bearer | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/slas/incidents/{incident_id}/escalate` | Escalate manually | Bearer | 200 | 400,401,403,404,409,422 |
| GET | `/api/v1/slas/incidents/{incident_id}/history` | SLA history | Bearer | 200 | 400,401,403,404,409,422 |
| GET | `/api/v1/slas/policies` | SLA policy per severity | Bearer | 200 | 400,401,403,404,409 |
| PUT | `/api/v1/slas/policies/{severity}` | Update an SLA policy | Bearer | 200 | 400,401,403,404,409,422 |

### Audit Logs

| Method | Path | Summary | Auth | Success | Errors |
|---|---|---|---|---|---|
| GET | `/api/v1/audit-logs` | Search the audit trail (newest first) | Bearer | 200 | 400,401,403,404,409,422 |
| GET | `/api/v1/audit-logs/{audit_log_id}` | Get one audit entry | Bearer | 200 | 400,401,403,404,409,422 |

### Notifications

| Method | Path | Summary | Auth | Success | Errors |
|---|---|---|---|---|---|
| GET | `/api/v1/notifications` | My notifications (newest first) | Bearer | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/notifications/process` | Deliver queued notifications now | Bearer | 200 | 400,401,403,404,409 |
| POST | `/api/v1/notifications/read-all` | Mark all my notifications as read | Bearer | 200 | 400,401,403,404,409 |
| GET | `/api/v1/notifications/unread-count` | Number of unread notifications | Bearer | 200 | 400,401,403,404,409 |
| POST | `/api/v1/notifications/{notification_id}/read` | Mark as read | Bearer | 200 | 400,401,403,404,409,422 |
| POST | `/api/v1/notifications/{notification_id}/unread` | Mark as unread | Bearer | 200 | 400,401,403,404,409,422 |

### Dashboard

| Method | Path | Summary | Auth | Success | Errors |
|---|---|---|---|---|---|
| GET | `/api/v1/dashboard` | Full dashboard summary | Bearer | 200 | 400,401,403,404,409,422 |
| GET | `/api/v1/dashboard/alerts` | Alert counters | Bearer | 200 | 400,401,403,404,409 |
| GET | `/api/v1/dashboard/analyst-workload` | Workload per analyst | Bearer | 200 | 400,401,403,404,409 |
| GET | `/api/v1/dashboard/high-risk-assets` | High-risk assets | Bearer | 200 | 400,401,403,404,409,422 |
| GET | `/api/v1/dashboard/incident-trend` | Incidents created/resolved per day | Bearer | 200 | 400,401,403,404,409,422 |
| GET | `/api/v1/dashboard/incidents` | Incident counters | Bearer | 200 | 400,401,403,404,409 |
| GET | `/api/v1/dashboard/remediation` | Overdue remediation | Bearer | 200 | 400,401,403,404,409 |
| GET | `/api/v1/dashboard/response-times` | Average response / resolution times | Bearer | 200 | 400,401,403,404,409 |
| GET | `/api/v1/dashboard/sla` | SLA compliance | Bearer | 200 | 400,401,403,404,409 |
| GET | `/api/v1/dashboard/vulnerabilities` | Vulnerability counters | Bearer | 200 | 400,401,403,404,409 |

### Reports

| Method | Path | Summary | Auth | Success | Errors |
|---|---|---|---|---|---|
| GET | `/api/v1/reports` | Available reports | Bearer | 200 | 400,401,403,404,409 |
| GET | `/api/v1/reports/{report_type}` | Generate a report | Bearer | 200 | 400,401,403,404,409,422 |
| GET | `/api/v1/reports/{report_type}/export` | Export a report as CSV | Bearer | 200 | 400,401,403,404,409,422 |

### Health

| Method | Path | Summary | Auth | Success | Errors |
|---|---|---|---|---|---|
| GET | `/health` | Liveness probe | public | 200 |  |
| GET | `/health/ready` | Readiness probe (checks the database) | public | 200 | 503 |

## Real sample responses (from the live demo run)

**POST /auth/login** -> `200`

```json
{
  "access_token": "<redacted>",
  "refresh_token": "<redacted>",
  "token_type": "bearer",
  "expires_in": 1800
}
```

**POST /alerts** -> `201`

```json
{
  "id": 1,
  "reference": "ALR-2026-000001",
  "title": "Brute force attempt #0",
  "description": null,
  "source": "SIEM",
  "category": "unauthorized_access",
  "severity": "high",
  "status": "new",
  "asset": {
    "id": 1,
    "name": "db-876165",
    "asset_type": "database",
    "criticality": "critical"
  },
  "assigned_to": null,
  "detected_at": "2026-10-13T06:32:48.792267Z",
  "is_duplicate": false,
  "duplicate_of_id": null,
  "occurrence_count": 1,
  "correlation_id": null,
  "created_at": "2026-10-13T07:22:48.814117Z",
  "updated_at": "2026-10-13T07:22:48.815889Z"
}
```

**POST /incidents** -> `201`

```json
{
  "id": 1,
  "reference": "INC-2026-000001",
  "title": "Credential attack on db-876165",
  "description": null,
  "category": "unauthorized_access",
  "severity": "critical",
  "status": "new",
  "is_sensitive": false,
  "asset": {
    "id": 1,
    "name": "db-876165",
    "asset_type": "database",
    "criticality": "critical"
  },
  "correlation_id": 1,
  "assigned_to": null,
  "created_by_id": 3,
  "resolution_summary": null,
  "resolution_details": null,
  "root_cause": null,
  "resolved_at": null,
  "closed_at": null,
  "closure_requested_by_id": null,
  "closure_requested_at": null,
  "closure_approved_by_id": null,
  "closure_note": null,
  "sla": {
    "incident_id": 1,
    "severity": "critical",
    "ack_deadline": "2026-10-13T07:37:48.996843Z",
    "investigation_deadline": "2026-10-13T08:22:48.996843Z",
    "resolution_deadline": "2026-10-13T11:22:48.996843Z",
    "acknowledged_at": null,
    "investigation_started_at": null,
    "resolved_at": null,
    "response_time_minutes": null,
    "resolution_time_minutes": null,
    "ack_breached": false,
    "investigation_breached": false,
    "resolution_breached": false,
    "sla_status": "on_track",
    "escalation_status": "none",
    "escalation_level": 0,
    "escalated_at": null,
    "escalation_reason": null,
    "minutes_to_resolution_deadline": 240.0
  },
  "created_at": "2026-10-13T07:22:48.996843Z",
  "updated_at": "2026-10-13T07:22:49.001854Z",
  "alerts": [
    {
      "id": 1,
      "reference": "ALR-2026-000001",
      "title": "Brute force attempt #0",
      "severity": "high",
      "status": "in_progress",
      "detected_at": "2026-10-13T06:32:48.792267Z"
    },
    {
      "id": 2,
      "reference": "ALR-2026-000002",
      "title": "Brute force attempt #1",
      "severity": "high",
     
  ... (truncated)
```

**GET /risks/assets/1** -> `200`

```json
{
  "asset": {
    "id": 1,
    "name": "db-876165",
    "asset_type": "database",
    "criticality": "critical"
  },
  "risk_score": 76.8,
  "risk_level": "critical",
  "open_vulnerabilities": 1,
  "accepted_vulnerabilities": 0
}
```

**GET /slas/incidents/1** -> `200`

```json
{
  "incident_id": 1,
  "severity": "critical",
  "ack_deadline": "2026-10-13T07:37:48.996843Z",
  "investigation_deadline": "2026-10-13T08:22:48.996843Z",
  "resolution_deadline": "2026-10-13T11:22:48.996843Z",
  "acknowledged_at": "2026-10-13T07:22:49.060862Z",
  "investigation_started_at": "2026-10-13T07:22:49.379569Z",
  "resolved_at": null,
  "response_time_minutes": 0.0,
  "resolution_time_minutes": null,
  "ack_breached": false,
  "investigation_breached": false,
  "resolution_breached": false,
  "sla_status": "on_track",
  "escalation_status": "none",
  "escalation_level": 0,
  "escalated_at": null,
  "escalation_reason": null,
  "minutes_to_resolution_deadline": 240.0
}
```

**GET /dashboard** -> `200`

```json
{
  "generated_at": "2026-10-13T07:22:49.501872Z",
  "incidents": {
    "total": 1,
    "open": 0,
    "resolved": 1,
    "by_status": {
      "closed": 1
    },
    "by_severity": {
      "critical": 1
    }
  },
  "alerts": {
    "total": 3,
    "critical_total": 1,
    "critical_open": 0,
    "by_severity": {
      "critical": 1,
      "high": 2
    }
  },
  "vulnerabilities": {
    "total": 1,
    "unresolved": 1,
    "by_severity": {
      "high": 1
    },
    "by_status": {
      "in_remediation": 1
    }
  },
  "high_risk_assets": [
    {
      "asset": {
        "id": 2,
        "name": "web-876165",
        "asset_type": "server",
        "criticality": "high"
      },
      "risk_score": 63.67,
      "risk_level": "high",
      "open_vulnerabilities": 1
    }
  ],
  "response_times": {
    "average_response_minutes": 0.0,
    "average_resolution_minutes": 0.01,
    "incidents_measured": 1
  },
  "sla": {
    "tracked": 1,
    "compliant": 1,
    "breached": 0,
    "in_progress": 0,
    "compliance_percent": 100.0
  },
  "remediation": {
    "overdue": 0,
    "total_unfinished": 0
  },
  "analyst_workload": [
    {
      "user_id": 5,
      "full_name": "security_analyst 1",
      "open_incidents": 0,
      "open_alerts": 0,
      "open_remediation_tasks": 0,
      "open_playbook_tasks": 0,
      "total_open": 0
    }
  ],
  "incident_trend": [
    {
      "date": "2026-09-14",
      "created": 0,
      "resolved": 0
    },
    {
      "date": "2026-09-15",
      "created": 0,
      "resolved": 0
    },
    {
      "date": "2026-09-16",
      "created": 0,
      "resolved": 0
    },
    {
      "date": "2026-09-17",
      "created": 0,
      "resolved": 0
    },
    {
      "date": "2026-09-18",
      "created": 0,
      "resolved": 0
    },
    {
      "date":
  ... (truncated)
```

**GET /audit-logs** -> `200`

```json
{
  "items": [
    {
      "id": 37,
      "user_id": 3,
      "action": "report.export",
      "entity_type": "report",
      "entity_id": null,
      "previous_value": null,
      "new_value": {
        "report": "sla-compliance",
        "rows": 1,
        "parameters": {}
      },
      "ip_address": "127.0.0.1",
      "timestamp": "2026-10-13T07:22:49.557166Z"
    },
    {
      "id": 36,
      "user_id": 4,
      "action": "incident.closure_approve",
      "entity_type": "incident",
      "entity_id": 1,
      "previous_value": {
        "status": "resolved"
      },
      "new_value": {
        "status": "closed",
        "comment": null
      },
      "ip_address": "127.0.0.1",
      "timestamp": "2026-10-13T07:22:49.466002Z"
    },
    {
      "id": 35,
      "user_id": 3,
      "action": "incident.closure_request",
      "entity_type": "incident",
      "entity_id": 1,
      "previous_value": null,
      "new_value": {
        "comment": null
      },
      "ip_address": "127.0.0.1",
      "timestamp": "2026-10-13T07:22:49.440629Z"
    },
    {
      "id": 34,
      "user_id": 5,
      "action": "incident.resolve",
      "entity_type": "incident",
      "entity_id": 1,
      "previous_value": {
        "status": "investigating"
      },
      "new_value": {
        "status": "resolved",
        "resolution_summary": "Attack blocked"
      },
      "ip_address": "127.0.0.1",
      "timestamp": "2026-10-13T07:22:49.418655Z"
    },
    {
      "id": 33,
      "user_id": 5,
      "action": "incident.status_change",
      "entity_type": "incident",
      "entity_id": 1,
      "previous_value": {
        "status": "assigned"
      },
      "new_value": {
        "status": "investigating",
        "comment": null
      },
      "ip_address": "127.0.0.1",
      "times
  ... (truncated)
```
