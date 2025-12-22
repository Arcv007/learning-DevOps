## Mutable vs Immutable Infrastructure

Infrastructure can be managed in two main ways: **mutable** and **immutable**.

---

## Mutable Infrastructure

In mutable infrastructure:
- Existing resources are **updated or modified**
- Changes are applied on the same server
- Over time, servers drift from their original state

### Example
- Update software on an existing EC2 instance
- Modify configuration files on a running server

### Problems
- Configuration drift
- Hard to debug issues
- Inconsistent environments

---

## Immutable Infrastructure

In immutable infrastructure:
- Existing resources are **never modified**
- New resources are created with changes
- Old resources are destroyed

### Example
- Create a new EC2 instance with updated AMI
- Replace the old instance after deployment

### Benefits
- Predictable behavior
- Easier rollbacks
- Reduced configuration drift

Terraform works best with **immutable infrastructure**.

---

## Configuration Drift

### What is Configuration Drift?

**Configuration drift** happens when:
- Actual infrastructure changes
- Terraform configuration does not reflect those changes

This usually occurs due to:
- Manual changes in cloud console
- Changes made outside Terraform

---

### Example of Drift

Terraform code:
```hcl
instance_type = "t2.micro"

```

Manual change:

- Instance type changed to `t3.micro` in AWS Console

Result:

- Infrastructure no longer matches Terraform code

---

### How Terraform Handles Drift

When you run:

```bash
terraform plan

```

Terraform:

- Compares configuration
- Compares state
- Compares real infrastructure
- Detects drift and proposes changes

---

## Terraform Lifecycle Rules

Terraform provides **lifecycle rules** to control how resources are created, updated, and destroyed.

Lifecycle rules are defined inside a `lifecycle` block.

---

## `create_before_destroy`

### Purpose

Ensures a **new resource is created before the old one is destroyed**.

### Why It Is Used

- Prevent downtime
- Useful for production environments

### Example

```hcl
resource "aws_instance" "web" {
  ami           = "ami-123456"
  instance_type = "t2.micro"

  lifecycle {
    create_before_destroy = true
  }
}

```

Terraform will:

1. Create new instance
2. Destroy old instance

---

## `prevent_destroy`

### Purpose

Prevents accidental deletion of critical resources.

### Why It Is Used

- Protect production resources
- Avoid data loss

### Example

```hcl
resource "aws_s3_bucket" "data" {
  bucket = "prod-data-bucket"

  lifecycle {
    prevent_destroy = true
  }
}

```

If destroy is attempted:

```
Error: Instance cannot be destroyed

```

---

## `ignore_changes`

### Purpose

Tells Terraform to **ignore changes to specific attributes**.

### Why It Is Used

- When changes are managed outside Terraform
- To avoid unnecessary updates

---

### Example: Ignore Tag Changes

```hcl
resource "aws_instance" "web" {
  ami           = "ami-123456"
  instance_type = "t2.micro"

  tags = {
    Name = "web-server"
  }

  lifecycle {
    ignore_changes = [
      tags
    ]
  }
}

```

Terraform will ignore:

- Manual changes to tags
- Drift related to ignored attributes

---

## Lifecycle Rules Summary

| Rule | Purpose |
| --- | --- |
| create_before_destroy | Avoid downtime |
| prevent_destroy | Protect critical resources |
| ignore_changes | Ignore specific attribute changes |

---

## Key Points to Remember

- Mutable infrastructure changes existing resources
- Immutable infrastructure replaces resources
- Configuration drift occurs due to manual changes
- Lifecycle rules control Terraform behavior
- Use lifecycle rules carefully

---

## Best Practices

- Prefer immutable infrastructure
- Avoid manual changes in cloud console
- Use `prevent_destroy` for critical resources
- Use `ignore_changes` only when necessary
- Always review `terraform plan`

```