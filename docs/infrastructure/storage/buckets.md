# Creating and Managing Storage Buckets

Store and manage data in MyCloud object storage.

## What is Object Storage?

Object storage stores data as objects (files) in containers called buckets. It's ideal for:

- Backup and archival
- Log storage
- Media files
- Application data
- Data lakes

## Create a Bucket

### Using Web Console

1. Go to **Storage** → **Buckets**
2. Click **Create Bucket**
3. Enter bucket name:
   - Must be globally unique
   - Lowercase letters, numbers, hyphens only
   - 3-63 characters long

4. Select region (where data will be stored):
   - us-east-1 (N. Virginia)
   - us-west-2 (Oregon)
   - eu-west-1 (Ireland)

5. Choose access level:
   - **Private**: No public access
   - **Public**: Anyone can read objects
   - **Custom**: Fine-grained permissions

6. Click **Create**

### Using CLI

```bash
mycloud storage create-bucket \
  --name my-app-data \
  --region us-east-1 \
  --access private
```

### Using Terraform

```hcl
resource "mycloud_storage_bucket" "data" {
  name   = "my-app-data"
  region = "us-east-1"
  acl    = "private"

  tags = {
    Environment = "production"
    Application = "myapp"
  }
}
```

## Upload Objects

### Web Console

1. Open the bucket
2. Click **Upload**
3. Select files or drag and drop
4. Click **Start Upload**

### Using CLI

```bash
mycloud storage upload \
  --bucket my-app-data \
  --file local-file.txt \
  --key path/in/bucket/file.txt
```

### Using SDK

**Python:**

```python
import mycloud

client = mycloud.Client()
bucket = client.storage.get_bucket('my-app-data')
bucket.upload_file('local-file.txt', 'path/in/bucket/file.txt')
```

**Node.js:**

```javascript
const mycloud = require('mycloud');

const client = new mycloud.Client();
const bucket = client.storage.getBucket('my-app-data');
await bucket.uploadFile('local-file.txt', 'path/in/bucket/file.txt');
```

## List Bucket Contents

### CLI

```bash
mycloud storage list \
  --bucket my-app-data \
  --prefix logs/
```

### SDK

```python
bucket = client.storage.get_bucket('my-app-data')
for obj in bucket.list_objects(prefix='logs/'):
    print(obj.key, obj.size)
```

## Set Bucket Permissions

Grant access to specific users or applications:

1. Open the bucket
2. Click **Permissions**
3. Click **Add Member**
4. Select user or service account
5. Choose permission:
   - **Read Only** - Can list and download
   - **Write** - Can upload and download
   - **Admin** - Full control

6. Click **Add**

## Enable Versioning

Maintain multiple versions of objects:

1. Open the bucket
2. Click **Settings**
3. Toggle **Enable Versioning**
4. Click **Save**

With versioning enabled:

```bash
# Upload new version
mycloud storage upload --bucket my-app-data --file new-file.txt --key file.txt

# List all versions
mycloud storage list-versions --bucket my-app-data --key file.txt

# Download specific version
mycloud storage download \
  --bucket my-app-data \
  --key file.txt \
  --version-id abc123def456
```

## Set Lifecycle Policies

Automatically manage object retention and deletion:

```json
{
  "rules": [
    {
      "prefix": "logs/",
      "actions": [
        {
          "action": "transition",
          "days": 30,
          "storage_class": "glacier"
        },
        {
          "action": "delete",
          "days": 365
        }
      ]
    }
  ]
}
```

## Enable Encryption

Protect data at rest:

1. Open the bucket
2. Click **Encryption** → **Enable**
3. Choose:
   - **MyCloud Managed** - Default encryption (recommended)
   - **Customer Managed Key** - Use your own KMS key

4. Click **Save**

## Delete a Bucket

⚠️ The bucket must be empty:

1. Delete all objects in the bucket
2. Open the bucket
3. Click **Settings** → **Delete Bucket**
4. Confirm deletion

## Storage Tiers

Optimize costs based on access patterns:

| Tier | Access Speed | Cost | Best For |
|------|--------------|------|----------|
| Standard | Immediate | $0.023/GB/mo | Frequent access |
| Glacier | Hours | $0.004/GB/mo | Archival |
| Deep Archive | 12+ hours | $0.00099/GB/mo | Long-term retention |

## Monitoring and Metrics

Track bucket usage and costs:

1. Open the bucket
2. Click **Metrics**
3. View:
   - Total size
   - Number of objects
   - Data transfer
   - Requests

---

**Next:** [Configure Networking](../networking/vnets.md)
