## Using Input Variables in Terraform

Input variables allow you to **parameterize Terraform configurations**.
They make Terraform code **flexible, reusable, and easy to update** without changing the main configuration files.

---

## Why Input Variables are Used

Input variables are used to:
- Avoid hardcoding values
- Reuse the same configuration in multiple environments
- Make updates easier
- Improve readability and maintainability

Example use cases:
- Region
- Instance type
- Resource names
- Environment (dev, test, prod)

---

## How Input Variables are Created

Input variables are defined using a **variable configuration file**, commonly named:

```

variables.tf

```

Each variable is defined using a `variable` block.

---

## Basic Variable Example

### Variable Definition (`variables.tf`)
```hcl
variable "instance_type" {
  default = "t2.micro"
}

```

This defines a variable named `instance_type` with a default value.

---

## How to Use Variables in Main Configuration

Variables are referenced using:

```
var.<variable_name>

```

### Example (`main.tf`)

```hcl
resource "aws_instance" "example" {
  instance_type = var.instance_type
}

```

Terraform replaces `var.instance_type` with the actual value.

---

## How to Update Variable Values

There are multiple ways to update input variables.

### 1. Update Default Value

Change the `default` value in `variables.tf`.

---

### 2. Using `terraform.tfvars`

Create a file named:

```
terraform.tfvars

```

Example:

```hcl
instance_type = "t3.micro"

```

Terraform automatically loads this file.

---

### 3. Using Command Line

```bash
terraform apply -var="instance_type=t3.small"

```

---

## Understanding the Variable Block

A variable block supports the following elements:

### 1. default

- Provides a default value
- Makes the variable optional

Example:

```hcl
default = "us-east-1"

```

---

### 2. type

- Restricts the kind of value allowed
- Helps catch errors early

Example:

```hcl
type = string

```

---

### 3. description

- Explains the purpose of the variable
- Improves readability and documentation

Example:

```hcl
description = "EC2 instance type"

```

---

## Complete Variable Block Example

```hcl
variable "instance_type" {
  description = "Type of EC2 instance"
  type        = string
  default     = "t2.micro"
}

```

---

## Types of Input Variables

Terraform supports multiple variable types.

---

### 1. String

Single text value.

```hcl
variable "region" {
  type    = string
  default = "us-east-1"
}

```

---

### 2. Number

Numeric values.

```hcl
variable "instance_count" {
  type    = number
  default = 2
}

```

---

### 3. Boolean

True or false values.

```hcl
variable "enable_monitoring" {
  type    = bool
  default = true
}

```

---

## Collection Variable Types

---

### 4. List

Ordered collection of values of the same type.

```hcl
variable "availability_zones" {
  type    = list(string)
  default = ["us-east-1a", "us-east-1b"]
}

```

Access example:

```hcl
var.availability_zones[0]

```

---

### 5. Map

Key-value pairs.

```hcl
variable "tags" {
  type = map(string)
  default = {
    Name = "web-server"
    Env  = "dev"
  }
}

```

Access example:

```hcl
var.tags["Name"]

```

---

### 6. Set

Unordered collection of unique values.

```hcl
variable "security_groups" {
  type    = set(string)
  default = ["sg-123", "sg-456"]
}

```

---

### 7. Object

Collection of named attributes with different types.

```hcl
variable "instance_config" {
  type = object({
    instance_type = string
    volume_size   = number
  })
  default = {
    instance_type = "t2.micro"
    volume_size   = 20
  }
}

```

Access example:

```hcl
var.instance_config.instance_type

```

---

### 8. Tuple

Ordered collection of values with different types.

```hcl
variable "server_details" {
  type    = tuple([string, number, bool])
  default = ["web", 2, true]
}

```

Access example:

```hcl
var.server_details[0]

```

---

## Key Points to Remember

- Input variables make Terraform configurations reusable
- Variables are defined using `variable` blocks
- Values can be updated without changing main code
- Type constraints improve safety
- Use `terraform.tfvars` for clean configuration

---

## Best Practice

- Keep variables in `variables.tf`
- Use descriptive names
- Always add `description`
- Avoid hardcoding values in `main.tf`

```