# Creating and Managing API Keys

API keys allow you to authenticate with MyCloud programmatically.

## Create an API Key

### Step 1: Navigate to API Keys

1. Go to **Settings** → **API & Integrations**
2. Click **Create API Key**

### Step 2: Configure Key Details

| Setting | Description |
|---------|-------------|
| Name | Descriptive name for the key (e.g., "Production CI/CD") |
| Permissions | Select API scopes (read, write, delete, etc.) |
| Expiration | Optional expiration date (recommended for security) |

### Step 3: Copy Your Key

⚠️ **Important:** Your API key will only be shown once. Copy it immediately and store it securely.

```
my-api-key_a1b2c3d4e5f6g7h8i9j0k1l2m3n4o5p6
```

## Using API Keys

### Authenticate with cURL

```bash
curl -H "Authorization: Bearer YOUR_API_KEY" \
  https://api.mycloud.example.com/v1/resources
```

### Authenticate with SDK

**Python:**

```python
import mycloud

client = mycloud.Client(api_key="your-api-key")
resources = client.compute.list_instances()
```

**Node.js:**

```javascript
const mycloud = require('mycloud');

const client = new mycloud.Client({
  apiKey: 'your-api-key'
});

const resources = await client.compute.listInstances();
```

## API Key Permissions

When creating an API key, select the scopes it should have access to:

| Scope | Allows |
|-------|--------|
| `compute.read` | List VMs and instances |
| `compute.write` | Create and modify VMs |
| `storage.read` | List and read storage buckets |
| `storage.write` | Create and write to buckets |
| `networking.read` | View network configuration |
| `iam.read` | Read IAM policies |

## API Key Best Practices

✅ **Do:**

- Use separate keys for different applications
- Set expiration dates on keys
- Rotate keys periodically
- Store keys in environment variables or secret managers
- Use the minimum required permissions

❌ **Don't:**

- Share API keys
- Commit keys to version control
- Use the same key across multiple applications
- Leave keys in logs or error messages

## Rotate an API Key

To rotate an API key safely:

1. Create a new API key
2. Update your application to use the new key
3. Test thoroughly
4. Delete the old key after 24-48 hours

## Revoke an API Key

If your API key is compromised:

1. Go to **Settings** → **API & Integrations**
2. Click **Revoke** next to the compromised key
3. Create a new API key
4. Update your application immediately

## Monitor API Key Usage

Track which keys are being used and when:

1. Go to **Settings** → **API & Integrations**
2. Click **Usage Log**
3. View recent API calls by key

---

**Next:** [Set Up IAM Roles and Permissions](iam-roles.md)
