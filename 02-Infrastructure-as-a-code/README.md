# Infrastructure as Code (IaC) – Fundamentals

This repository contains**basic Infrastructure as Code (IaC) concepts** that should be understood**before learning Terraform**.
The notes are written in simple language for easy understanding and quick revision.

---

## What is Infrastructure?

Infrastructure includes all the components required to run an application, such as:
- Servers (Virtual Machines / EC2)
- Networking (VPC, Subnets, Load Balancers)
- Storage (Disks, Object Storage, Databases)
- Security (Firewalls, IAM, Security Groups)

---

## What is Infrastructure as Code (IaC)?

**Infrastructure as Code (IaC)** is the practice of**managing infrastructure using code instead of manual configuration**.

With IaC:
- Infrastructure is written as files
- Stored in version control (Git)
- Created and managed automatically
- Easy to repeat and scale

Infrastructure is treated like software.

---

## Why IaC is Important

Manual infrastructure management leads to:
- Human errors
- Inconsistent environments
- Slow deployments
- Difficult recovery

IaC helps by providing:
- Automation
- Consistency
- Version control
- Faster and reliable deployments

---

## Desired State

The**desired state** is what you define in code.

Example:
> “There should be 2 servers running.”

---

## Current State

The**current state** is what actually exists in the cloud.

IaC tools compare desired state with current state and apply only required changes.

---

## Declarative Approach

In a**declarative approach**, you define**what you want**, not**how to do it**.

Terraform uses a declarative model.

---

## Idempotency

**Idempotency** means running the same code multiple times results in the same infrastructure state.

This makes infrastructure changes safe and predictable.

---

## Configuration Drift

**Configuration drift** happens when infrastructure is changed manually and no longer matches the code.

IaC tools help detect and fix drift.

---

## Mutable Infrastructure

- Existing servers are modified
- Changes accumulate over time
- Harder to maintain

---

## Immutable Infrastructure

- Servers are replaced instead of modified
- Old servers are destroyed
- More reliable and consistent

IaC works best with immutable infrastructure.

---

## Version Control and IaC

Infrastructure code is stored in Git, allowing:
- Change tracking
- Rollbacks
- Collaboration
- Audit history

---

## Imperative vs Declarative

-**Imperative**: Defines step-by-step actions
-**Declarative**: Defines final desired state

Terraform follows the declarative approach.

---

## Types of IaC Tools

### Configuration Management Tools
- Ansible
- Chef
- Puppet
Used to configure software inside servers.

### Provisioning Tools
- Terraform
- CloudFormation
Used to create and manage infrastructure.

---

## Terraform Context

Terraform is an**Infrastructure as Code provisioning tool** that:
- Uses declarative syntax
- Manages desired vs current state
- Automates cloud infrastructure
- Supports multiple cloud providers

---

## Next Step

After understanding these fundamentals:
- Learn Terraform workflow (init, plan, apply)
- Understand Terraform state
- Practice with small Terraform projects

