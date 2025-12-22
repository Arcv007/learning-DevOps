## Output Variables in Terraform

Output variables are used to **display values after Terraform creates infrastructure**.
They are commonly used to show important information such as IDs, IP addresses, and names of resources.

---

## Why Output Variables are Used

Output variables are used to:
- View important resource information after `terraform apply`
- Pass values from one Terraform configuration or module to another
- Avoid manually searching values in the cloud console

Common examples:
- EC2 public IP
- VPC ID
- Load balancer DNS name

---

## Output Variable Syntax

Output variables are defined using an `output` block.

Basic syntax:
```hcl
output "<output_name>" {
  value = <expression>
}

```

---

## Output Variable Example

```hcl
resource "aws_instance" "web" {
  ami           = "ami-123456"
  instance_type = "t2.micro"
}

output "instance_public_ip" {
  value = aws_instance.web.public_ip
}

```

After running `terraform apply`, Terraform displays:

- The public IP of the EC2 instance

---

## When to Use Output Variables

Use output variables when you need to:

- Display values to the user
- Share resource attributes with other modules
- Reference important infrastructure details externally

---

## Output with Description (Recommended)

```hcl
output "instance_id" {
  description = "ID of the EC2 instance"
  value       = aws_instance.web.id
}

```

Adding a description improves readability and documentation.

---

## Key Points to Remember

- Output variables show values after infrastructure creation
- They use resource attribute references
- Defined using `output` blocks
- Commonly used for debugging and integration

---

## Best Practice

- Output only required values
- Use clear and meaningful output names
- Add descriptions for better understanding

```
