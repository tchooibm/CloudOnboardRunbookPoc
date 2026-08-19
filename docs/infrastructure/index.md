# Infrastructure Setup

Deploy and manage compute, storage, and networking resources on MyCloud.

## Core Infrastructure Components

### Compute

Virtual machines and container orchestration for running applications.

- Virtual Machines (VMs)
- Container Services
- Serverless Functions
- Batch Processing

### Storage

Persistent storage for data and applications.

- Object Storage (buckets)
- Block Storage (volumes)
- File Storage (NFS/SMB)
- Databases

### Networking

Network connectivity and security for your resources.

- Virtual Networks (VNets)
- Subnets and routing
- Load Balancers
- Firewalls and security groups

## Getting Started

1. **[Deploy Your First VM](compute/first-vm.md)** - Create a virtual machine
2. **[Create Storage Buckets](storage/buckets.md)** - Set up object storage
3. **[Configure Networking](networking/vnets.md)** - Set up virtual networks

## Infrastructure Types

### Development Environment

- 1-2 small VMs
- Shared storage
- Basic networking

### Production Environment

- Multiple VMs with load balancing
- Replicated storage
- Advanced networking and security

### High-Availability Setup

- Auto-scaling compute
- Multi-region replication
- Advanced disaster recovery

## Common Deployment Patterns

| Pattern | Use Case | Complexity |
|---------|----------|-----------|
| Single VM | Testing, demos | Low |
| Web tier + Database | Simple web app | Medium |
| Microservices | Distributed app | High |
| Multi-region | Global availability | High |

## Infrastructure as Code (IaC)

Automate infrastructure deployment with Terraform or CloudFormation:

```hcl
resource "mycloud_instance" "web_server" {
  name  = "web-server-1"
  image = "ubuntu-22.04"
  type  = "t2.medium"
}
```

---

**Start Here:** [Deploy Your First VM](compute/first-vm.md)
