# Identity and Access Management (IAM)

Manage user access and permissions across your MyCloud resources.

## IAM Concepts

### Users

Individual accounts that authenticate with credentials.

### Roles

Collections of permissions that define what actions a user can perform.

### Policies

Rules that grant or deny permissions for specific resources.

### Service Accounts

Special accounts for applications and automated processes.

## Pre-defined Roles

MyCloud provides several built-in roles:

| Role | Permissions | Use Case |
|------|-------------|----------|
| **Owner** | Full access to all resources | Account administrator |
| **Admin** | Manage users, billing, resources | Team lead |
| **Developer** | Create and manage resources | Development team |
| **Viewer** | Read-only access | Auditing, reporting |
| **Operator** | Manage running resources | Operations team |

## Create a Custom Role

For fine-grained access control:

1. Go to **Settings** → **IAM** → **Roles**
2. Click **Create Role**
3. Enter role name and description
4. Select permissions:
   - `compute.instances.list`
   - `compute.instances.start`
   - `compute.instances.stop`
5. Click **Create Role**

## Add Users to Your Account

### Step 1: Invite User

1. Go to **Settings** → **Team Members**
2. Click **Invite Member**
3. Enter their email address
4. Select a role

### Step 2: User Accepts Invitation

The user receives an email invitation and:

1. Clicks the link in the email
2. Creates their MyCloud account or logs in
3. Gains access to your resources

## Assign Roles to Users

To change a user's role:

1. Go to **Settings** → **Team Members**
2. Click the user's name
3. Select a new role from the dropdown
4. Click **Update**

## Create a Service Account

Service accounts allow applications to authenticate:

1. Go to **Settings** → **IAM** → **Service Accounts**
2. Click **Create Service Account**
3. Enter a name (e.g., "terraform-provisioner")
4. Select a role
5. Click **Create**

Your service account will receive an API key automatically.

## Grant Permissions on Specific Resources

Assign permissions to a specific resource:

1. Open the resource (e.g., a storage bucket)
2. Go to **Permissions** or **Sharing**
3. Click **Add Member**
4. Enter user email or service account
5. Select role
6. Click **Add**

## IAM Best Practices

✅ **Do:**

- Use least privilege principle (minimum permissions needed)
- Create custom roles for specific job functions
- Regularly audit user permissions
- Use service accounts for applications
- Remove access immediately when users leave

❌ **Don't:**

- Give everyone Owner or Admin role
- Share service account credentials
- Use personal accounts for automated processes
- Leave unused users or service accounts active

## Audit IAM Changes

Monitor IAM activity:

1. Go to **Settings** → **Audit Log**
2. Filter by activity type: "IAM"
3. Review user additions, removals, and role changes

---

**Related:** [Enable Audit Logging](../security/audit-logging.md)
