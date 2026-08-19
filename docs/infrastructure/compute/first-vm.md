# Deploying Your First Virtual Machine

Create and launch your first MyCloud virtual machine.

## Prerequisites

- ✅ MyCloud account created and verified
- ✅ Billing configured
- ✅ API access configured (if using CLI)

## Using the Web Console

### Step 1: Navigate to Compute

1. Log in to your MyCloud dashboard
2. Click **Compute** in the left navigation
3. Click **Instances** → **Create Instance**

### Step 2: Choose an Image

Select an operating system:

- **Ubuntu 22.04 LTS** - Recommended for most workloads
- **Ubuntu 20.04 LTS** - For older compatibility
- **Debian 11** - Lightweight alternative
- **CentOS 8** - Enterprise Linux
- **Windows Server 2022** - Windows workloads

For this example, choose **Ubuntu 22.04 LTS**.

### Step 3: Select Instance Type

Choose the size based on your needs:

| Type | vCPU | RAM | Monthly Cost | Best For |
|------|------|-----|--------------|----------|
| t2.nano | 1 | 512 MB | $5 | Development/testing |
| t2.small | 1 | 2 GB | $15 | Light workloads |
| t2.medium | 2 | 4 GB | $30 | General purpose |
| t2.large | 4 | 8 GB | $60 | Production apps |

Choose **t2.micro** to stay within free tier (if eligible).

### Step 4: Configure Storage

- **Boot volume size**: 30 GB (sufficient for most workloads)
- **Storage type**: SSD (default, recommended)

### Step 5: Networking

- **Virtual Network**: Default VNet (or create a new one)
- **Subnet**: Choose the default subnet
- **Public IP**: Enable (to access from the internet)
- **Security Group**: Default

### Step 6: Review and Launch

1. Review all settings
2. Click **Launch Instance**
3. Wait for the instance to start (usually 2-3 minutes)

## Accessing Your VM

### Via SSH (Linux/Mac/Windows)

Once the VM is running:

```bash
ssh -i your-key.pem ubuntu@YOUR_PUBLIC_IP
```

### Via RDP (Windows)

For Windows instances, use Remote Desktop Protocol:

```
Computer: YOUR_PUBLIC_IP
Username: Administrator
```

## After Launch

### Security: Configure Security Group

Restrict access to necessary ports only:

1. Go to **Compute** → **Instances**
2. Click your instance name
3. Go to **Security** tab
4. Add inbound rules:

| Protocol | Port | Source |
|----------|------|--------|
| SSH | 22 | Your IP |
| HTTP | 80 | 0.0.0.0/0 |
| HTTPS | 443 | 0.0.0.0/0 |

### Updates: Install Security Updates

```bash
sudo apt update
sudo apt upgrade -y
```

### Monitoring: Enable CloudWatch

1. Select your instance
2. Click **Monitoring**
3. Click **Enable Detailed Monitoring**

## Using CLI

Create an instance with the MyCloud CLI:

```bash
mycloud compute create-instance \
  --name web-server-1 \
  --image ubuntu-22.04 \
  --type t2.medium \
  --region us-east-1
```

## Using Infrastructure as Code (Terraform)

```hcl
resource "mycloud_instance" "web" {
  name      = "web-server-1"
  image     = "ubuntu-22.04"
  type      = "t2.medium"
  region    = "us-east-1"
  public_ip = true

  tags = {
    Environment = "dev"
    Owner       = "team-a"
  }
}
```

## Stopping and Deleting

### Stop Instance

Preserve the instance but stop charges:

```bash
mycloud compute stop-instance web-server-1
```

### Delete Instance

⚠️ This action cannot be undone:

```bash
mycloud compute delete-instance web-server-1
```

## Troubleshooting

### Instance won't start

- Check account has sufficient resources
- Review error logs in the console
- Contact support if issue persists

### Can't SSH into instance

- Verify public IP is assigned
- Check security group allows SSH (port 22)
- Ensure you're using the correct key pair
- Check instance is in "Running" state

---

**Next:** [Create Storage Buckets](../storage/buckets.md)
