# Setting Up Virtual Networks

Create isolated networks for your cloud resources.

## Virtual Networks (VNets)

A virtual network is a private network where your resources communicate.

### Default VNet

When you create an account, MyCloud provides a default VNet:

- Address space: 10.0.0.0/16
- Pre-configured with default subnets
- Ready for immediate use

## Create a Custom VNet

### Using Web Console

1. Go to **Networking** → **Virtual Networks**
2. Click **Create VNet**
3. Enter VNet details:

| Field | Example |
|-------|---------|
| Name | production-network |
| Region | us-east-1 |
| Address Space | 10.1.0.0/16 |

4. Add subnets:
   - **Subnet Name**: web-tier
   - **Subnet CIDR**: 10.1.1.0/24

5. Click **Create**

### Using CLI

```bash
mycloud networking create-vnet \
  --name production-network \
  --region us-east-1 \
  --cidr 10.1.0.0/16
```

### Using Terraform

```hcl
resource "mycloud_virtual_network" "prod" {
  name            = "production-network"
  region          = "us-east-1"
  address_space   = "10.1.0.0/16"

  subnet {
    name             = "web-tier"
    address_prefix   = "10.1.1.0/24"
  }

  subnet {
    name             = "db-tier"
    address_prefix   = "10.1.2.0/24"
  }
}
```

## Add Subnets

Divide your VNet into subnets for better organization:

1. Open your VNet
2. Click **Subnets** → **Add Subnet**
3. Enter:
   - **Name**: db-tier
   - **Address Prefix**: 10.1.2.0/24

4. Click **Add**

## Configure Routing

Control traffic flow between subnets:

1. Open your VNet
2. Click **Route Tables** → **Create Route Table**
3. Add routes:

| Destination | Next Hop | Purpose |
|-------------|----------|---------|
| 0.0.0.0/0 | Internet Gateway | Outbound internet |
| 10.1.0.0/16 | Local | Internal traffic |

## Security Groups

Control inbound and outbound traffic to resources.

### Create a Security Group

1. Go to **Networking** → **Security Groups**
2. Click **Create Security Group**
3. Add inbound rules:

```
Rule 1: SSH
  Protocol: TCP
  Port: 22
  Source: Your IP (e.g., 203.0.113.0/32)

Rule 2: HTTP
  Protocol: TCP
  Port: 80
  Source: 0.0.0.0/0

Rule 3: HTTPS
  Protocol: TCP
  Port: 443
  Source: 0.0.0.0/0
```

4. Click **Create**

### Assign Security Group to Instance

1. Open your instance
2. Click **Networking**
3. Select security group from dropdown
4. Click **Update**

## Network Access Control Lists (NACLs)

Layer 2 security at the subnet level:

1. Open your VNet
2. Click **Subnets**
3. Select a subnet
4. Click **Edit NACL**
5. Add rules:

| Rule # | Type | Protocol | Port | Source | Action |
|--------|------|----------|------|--------|--------|
| 100 | Inbound | TCP | 80 | 0.0.0.0/0 | Allow |
| 110 | Inbound | TCP | 443 | 0.0.0.0/0 | Allow |
| 120 | Inbound | TCP | 22 | 10.0.0.0/8 | Allow |
| 32767 | Inbound | All | All | 0.0.0.0/0 | Deny |

## Connect VNets (VNet Peering)

Link two VNets for direct communication:

1. Go to **Networking** → **VNet Peering**
2. Click **Create Peering**
3. Select source and destination VNets
4. Configure peering:
   - Allow forwarded traffic: Yes
   - Allow gateway transit: No
   - Use remote gateway: No

5. Click **Create**

## Public and Private Subnets

### Public Subnet

Resources can communicate with the internet:

- Has a route to the Internet Gateway
- Instances get public IPs
- Enables inbound internet traffic

### Private Subnet

Resources cannot directly access the internet:

- Routes traffic through NAT Gateway
- No public IPs assigned
- More secure for databases and internal services

## NAT Gateway

Allow private resources to access the internet:

1. Go to **Networking** → **NAT Gateways**
2. Click **Create NAT Gateway**
3. Select public subnet
4. Click **Create**
5. Add route to private subnet:
   - **Destination**: 0.0.0.0/0
   - **Next Hop**: NAT Gateway

## Network Monitoring

Monitor traffic and health:

1. Open your VNet
2. Click **Monitoring**
3. View metrics:
   - Bytes in/out
   - Packets in/out
   - Connected devices

---

**Related:** [Security Best Practices](../../security/index.md)
