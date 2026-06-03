# Azure Day 1 Notes

## What is Azure?

Microsoft Azure is a cloud computing platform that provides services such as:

* Virtual Machines
* App Services
* SQL Databases
* Storage
* AI Services
* Networking

Instead of buying and maintaining servers, we rent resources from Azure.

---

## Core Azure Hierarchy

Subscription
→ Resource Group
→ Resources

Example:

Subscription
└── EmployeeApp-RG
├── App Service
├── Azure SQL Database
├── Storage Account
└── Key Vault

---

## Subscription

Definition:
A billing and management boundary for Azure resources.

Purpose:

* Owns Azure resources
* Tracks costs
* Controls access

Example:
My Azure Account Subscription

Key Point:
Without a subscription, resources cannot be created.

---

## Resource Group

Definition:
A logical container for related Azure resources.

Purpose:

* Organize resources
* Manage permissions
* Monitor costs
* Delete related resources together

Example:

Resource Group: EmployeeManagement-RG

Contains:

* Employee API
* Employee Database
* Employee Storage

Key Point:
Resources used by the same application are usually placed in one Resource Group.

---

## Region

Definition:
A physical Azure datacenter location.

Examples:

* Central India
* West India
* East US
* West Europe

Purpose:

* Determines where resources run
* Affects latency and compliance

Best Practice:
Choose a region close to users.

For Indian applications:

* Central India
* West India

---

## Resource

Definition:
Any Azure service that is created and managed.

Examples:

| Resource           | Purpose                   |
| ------------------ | ------------------------- |
| App Service        | Host ASP.NET applications |
| Azure SQL Database | Store application data    |
| Storage Account    | Store files and blobs     |
| Key Vault          | Store secrets and keys    |
| Function App       | Serverless computing      |

Key Point:
Everything created in Azure is a resource.

---

## Storage Account

Definition:
A service used to store data in Azure.

Can store:

* Images
* Videos
* PDFs
* Application files
* Backups

Common Storage Types:

* Blob Storage
* File Storage
* Queue Storage
* Table Storage

---

## Day 1 Practical Work Completed

✓ Azure Account Created

✓ Resource Group Created

Name:
rg-learning-dev

✓ Storage Account Created

Purpose:
Store application files and documents.

---

## Interview Questions

Q: What is a Subscription?
A: A billing and management boundary for Azure resources.

Q: What is a Resource Group?
A: A logical container that groups related Azure resources.

Q: What is a Region?
A: A physical location where Azure resources are deployed.

Q: What is a Resource?
A: Any Azure service such as App Service, SQL Database, or Storage Account.

Q: What is a Storage Account?
A: A service used to store files, blobs, queues, and other data in Azure.

---

## Key Takeaways

1. Azure resources belong to a Subscription.
2. Resources are organized using Resource Groups.
3. Resources are deployed to a Region.
4. Storage Accounts are used to store files and application data.
5. Resource Group is one of the most important organizational units in Azure.

