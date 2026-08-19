# Troubleshooting

Resolve common issues and get help with MyCloud.

## Common Issues

### Account & Authentication

- [Can't Log In](authentication.md#cant-log-in)
- [Forgot Password](authentication.md#forgot-password)
- [MFA Not Working](authentication.md#mfa-not-working)
- [Account Locked](authentication.md#account-locked)

### Compute Resources

- [Instance Won't Start](compute.md#instance-wont-start)
- [Can't SSH into Instance](compute.md#cant-ssh-into-instance)
- [Slow Instance Performance](compute.md#slow-performance)
- [Out of Quota](compute.md#out-of-quota)

### Storage & Networking

- [Upload Failing](storage.md#upload-failing)
- [Cannot Access Bucket](storage.md#cannot-access-bucket)
- [VNet Connectivity Issues](networking.md#vnet-connectivity-issues)

## Self-Service Diagnostics

### Run Health Check

```bash
mycloud health-check
```

This will verify:

- ✅ API connectivity
- ✅ Authentication
- ✅ Resource quotas
- ✅ Billing status
- ✅ Account permissions

### Check Service Status

Visit [https://status.mycloud.example.com](https://status.mycloud.example.com) to see:

- Current incidents
- Scheduled maintenance
- Service health
- Historical uptime

### View Error Logs

In your MyCloud console:

1. Go to **Settings** → **Activity & Logs**
2. View recent errors and warnings
3. Click on an error for details

## Getting Help

### Search Documentation

Use the search bar at the top of this documentation to find answers.

### Contact Support

**Support Options:**

- **Live Chat**: Available in console at bottom right
- **Email**: support@mycloud.example.com
- **Phone**: +1-800-MYCLOUD-1 (for enterprise customers)
- **Ticket Portal**: [support.mycloud.example.com](https://support.mycloud.example.com)

### Escalation Process

1. **Tier 1 Support** - Standard support (24-48 hr response)
2. **Tier 2 Support** - Technical issues (4-8 hr response)
3. **Tier 3 Support** - Critical issues (1 hr response for enterprise)

### Emergency Support

For production outages affecting your business:

1. Call emergency line: **+1-800-MYCLOUD-911**
2. Have ready:
   - Account ID
   - Description of issue
   - Affected resources
   - Business impact

## Common Solutions

### I can't access my resources

**Check:**

1. Are you logged in?
2. Do you have permission?
3. Is the resource in the correct region?
4. Is the resource running?

### My instance keeps crashing

**Steps:**

1. Check system logs for errors
2. Verify instance has sufficient resources
3. Check application logs
4. Try restarting the instance

### Billing seems high

**Review:**

1. Which resources are consuming cost?
2. Are there orphaned resources?
3. Check for unused instances or storage
4. Review data transfer charges

## Document Conventions

Throughout this documentation:

- **Bold** indicates UI elements or menu items
- `code` indicates commands or API calls
- ⚠️ Indicates warnings or important information
- ✅ Indicates best practices or successful outcomes
- ❌ Indicates things to avoid

---

**Need more help?** Start with the specific troubleshooting guide for your issue, or contact support.
