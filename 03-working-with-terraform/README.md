## Common Terraform Commands (with Examples)

Terraform provides multiple commands to validate, format, inspect, and understand infrastructure and state.

---

## `terraform validate`

### Purpose
Checks whether Terraform configuration files are **syntactically correct and logically valid**.

- Does NOT contact cloud providers
- Does NOT read or update state
- Only checks `.tf` files

### Example

```bash
terraform validate

```

Output example:

```
Success! The configuration is valid.

```

If there is an error:

```
Error: Unsupported argument

```

Use this command before running `terraform plan`.

---

## `terraform fmt`

### Purpose

Formats Terraform configuration files to a **standard, readable format**.

- Improves readability
- Enforces consistent style

### Example

```bash
terraform fmt

```

Formats all `.tf` files in the current directory.

Recursive formatting:

```bash
terraform fmt -recursive

```

---

## `terraform show`

### Purpose

Displays the **current Terraform state** in a human-readable format.

- Reads from `terraform.tfstate`
- Shows all resources and attributes

### Example

```bash
terraform show

```

Sample output:

```
aws_instance.web:
  id = i-0123456789
  instance_type = t2.micro
  public_ip = 54.10.20.30

```

Show a saved plan file:

```bash
terraform show tfplan

```

---

## `terraform providers`

### Purpose

Shows **which providers are used** in the configuration and state.

### Example

```bash
terraform providers

```

Sample output:

```
provider[registry.terraform.io/hashicorp/aws] ~> 5.0

```

Useful for:

- Auditing providers
- Verifying versions and sources

---

## `terraform refresh`

### Purpose

Updates the **state file** to match the real infrastructure.

- Does NOT change infrastructure
- Only updates state values

### Example

```bash
terraform refresh

```

Use case:

- Resources were modified manually in the cloud
- You want Terraform state to reflect current reality

> Note: terraform plan and terraform apply refresh state by default.
> 

---

## `terraform graph`

### Purpose

Generates a **dependency graph** of Terraform resources.

- Shows how resources depend on each other
- Output is in DOT format

### Example

```bash
terraform graph

```

This outputs text, not an image.

---

## Terraform Graph with Graphviz (Visual Example)

To convert the graph into an image, use **Graphviz**.

### Step 1: Install Graphviz (Ubuntu)

```bash
sudo apt install graphviz

```

---

### Step 2: Generate Dependency Graph Image

```bash
terraform graph | dot -Tpng > graph.png

```

This creates `graph.png`, which visually shows:

- Resource dependencies
- Creation order
- Implicit and explicit relationships

---

## When to Use `terraform graph`

- Understanding complex configurations
- Learning how Terraform builds dependency graphs
- Debugging unexpected resource ordering

---

## Summary Table

| Command | What It Does | Example |
| --- | --- | --- |
| terraform validate | Validates config syntax | `terraform validate` |
| terraform fmt | Formats code | `terraform fmt` |
| terraform show | Displays state | `terraform show` |
| terraform providers | Lists providers | `terraform providers` |
| terraform refresh | Syncs state | `terraform refresh` |
| terraform graph | Shows dependencies | `terraform graph` |

---

## Best Practices

- Run `terraform fmt` before committing
- Always run `terraform validate`
- Use `terraform show` for debugging
- Avoid frequent manual `terraform refresh`
- Use Graphviz to understand dependencies

```
