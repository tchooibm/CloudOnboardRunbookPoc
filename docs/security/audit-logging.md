# Audit Logging and Monitoring

Track all activities in your MyCloud account for compliance and security.

## Enable Audit Logging

Audit logging captures all API calls and administrative actions.

### Enable in Console

1. Go to **Settings** → **Audit & Compliance**
2. Click **Enable Audit Logging**
3. Choose log destination:
   - **MyCloud Logs** - Store in MyCloud
   - **Storage Bucket** - Store in S3-compatible bucket
   - **SIEM Integration** - Send to external SIEM

4. Click **Save**

## Audit Log Contents

Each audit log entry contains:

| Field | Example |
|-------|---------|
| Timestamp | 2026-08-19T14:32:15Z |
| User | john@example.com |
| User ID | user_a1b2c3d4 |
| Action | compute.instance.create |
| Resource | instance_web-server-1 |
| Status | Success |
| IP Address | 203.0.113.42 |
| User Agent | MyCloud CLI v2.1.0 |

### Example Log Entry

```json
{
  "timestamp": "2026-08-19T14:32:15Z",
  "user": "john@example.com",
  "userId": "user_a1b2c3d4",
  "action": "compute.instance.create",
  "resource": "instance/web-server-1",
  "status": "success",
  "details": {
    "instanceType": "t2.medium",
    "image": "ubuntu-22.04",
    "region": "us-east-1"
  },
  "sourceIP": "203.0.113.42",
  "userAgent": "MyCloud CLI v2.1.0"
}
```

## Query Audit Logs

### Using Web Console

1. Go to **Settings** → **Audit Log**
2. Filter by:
   - **Date Range**: Select start and end dates
   - **User**: Filter by user email
   - **Action**: Select action type
   - **Resource**: Filter by resource ID
   - **Status**: Success or failure

3. Click **Filter**

### Using CLI

```bash
mycloud audit-log list \
  --start-date 2026-08-19 \
  --end-date 2026-08-20 \
  --action compute.instance.create \
  --status success
```

### Using API

```bash
curl -H "Authorization: Bearer YOUR_API_KEY" \
  "https://api.mycloud.example.com/v1/audit-logs?startDate=2026-08-19&endDate=2026-08-20"
```

## Log Retention

Configure how long logs are retained:

1. Go to **Settings** → **Audit & Compliance**
2. Select retention policy:
   - 30 days (default)
   - 90 days
   - 1 year
   - 7 years (compliance requirement)

3. Click **Save**

Logs older than the retention period are automatically deleted.

## Export Logs

Export logs for long-term archival:

### Export as CSV

1. Go to **Settings** → **Audit Log**
2. Apply filters as needed
3. Click **Export as CSV**
4. Logs download to your computer

### Stream to Storage

Configure continuous log streaming:

1. Go to **Settings** → **Audit & Compliance**
2. Click **Export Configuration**
3. Select storage bucket
4. Configure prefix: `audit-logs/`
5. Click **Save**

Logs are automatically written to your bucket daily.

## SIEM Integration

Forward logs to your Security Information and Event Management system:

### Splunk Integration

1. Install Splunk Cloud
2. Configure MyCloud add-on
3. Set up in MyCloud:
   - Go to **Settings** → **Audit & Compliance**
   - Select **SIEM Integration**
   - Choose **Splunk**
   - Enter Splunk API endpoint
   - Enter API token

### CloudTrail Integration

```bash
mycloud audit-log configure-cloudtrail \
  --trail-name mycloud-audit \
  --bucket-name mycloud-logs
```

## Alerting on Audit Events

Set up alerts for suspicious activities:

### Create Alert Rule

1. Go to **Settings** → **Audit & Compliance** → **Alert Rules**
2. Click **Create Rule**
3. Configure:

| Setting | Value |
|---------|-------|
| Rule Name | Unauthorized Delete Attempts |
| Condition | action = "*.delete" AND status = "failure" |
| Threshold | 5 events in 10 minutes |
| Action | Send email alert |

4. Click **Create**

## Audit Log Events

Common events to monitor:

| Event | Description |
|-------|-------------|
| `iam.user.create` | New user added |
| `iam.user.delete` | User removed |
| `iam.role.assign` | Role assignment |
| `security.mfa.disable` | MFA disabled |
| `compute.instance.create` | VM created |
| `compute.instance.delete` | VM deleted |
| `storage.bucket.delete` | Bucket deleted |
| `network.firewall.update` | Security group modified |

## Compliance Reports

Generate reports for audits and compliance:

1. Go to **Settings** → **Audit & Compliance** → **Reports**
2. Select report type:
   - User Activity Report
   - Resource Changes Report
   - Compliance Summary
   - Security Incident Report

3. Select date range
4. Click **Generate**
5. Download as PDF

---

**Next:** [Enable CloudTrail and Monitoring](https://mycloud.example.com/docs/monitoring)
