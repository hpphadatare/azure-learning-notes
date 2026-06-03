# Day 2 - Azure App Service & ASP.NET Core API

## Objective

Deploy an ASP.NET Core Web API to Azure App Service and make it accessible through a public HTTPS URL.

---

# Architecture

```text
Local ASP.NET Core API
        ↓
Visual Studio Publish
        ↓
Azure App Service
        ↓
Public HTTPS URL
```

Example:

```text
https://employee-api-hanmant.azurewebsites.net
```

---

# Azure App Service

## What is Azure App Service?

Azure App Service is a Platform as a Service (PaaS) offering that allows developers to host:

* ASP.NET Core Applications
* Web APIs
* Node.js Applications
* Java Applications
* Python Applications

without managing servers.

---

## Benefits of Azure App Service

* No server management
* Built-in HTTPS
* Auto-scaling
* Deployment slots
* CI/CD integration
* High availability

---

# Platform as a Service (PaaS)

## Definition

PaaS provides a platform to build, deploy, and manage applications without maintaining operating systems, servers, or infrastructure.

### Examples

* Azure App Service
* Azure SQL Database
* Azure Functions

---

# Infrastructure as a Service (IaaS) vs PaaS

| Feature          | IaaS     | PaaS              |
| ---------------- | -------- | ----------------- |
| Manage Server    | Yes      | No                |
| Manage OS        | Yes      | No                |
| Deployment Speed | Slower   | Faster            |
| Maintenance      | Customer | Azure             |
| Example          | Azure VM | Azure App Service |

---

# App Service Plan

## What is an App Service Plan?

An App Service Plan defines:

* Region
* Compute Resources
* Pricing Tier
* Scaling Capabilities

Multiple App Services can share the same App Service Plan.

### Pricing Tiers

* F1 (Free)
* B1 (Basic)
* S1 (Standard)
* Premium

For learning purposes, F1 (Free) is sufficient.

---

# Deployment Process

## Local Development

```bash
dotnet new webapi
dotnet run
```

Verify Swagger works locally.

---

## Publish to Azure

Visual Studio

```text
Right Click Project
      ↓
Publish
      ↓
Azure
      ↓
Azure App Service (Windows)
      ↓
Select Existing App Service
      ↓
Publish
```

---

# ASP.NET Core Environment

ASP.NET Core supports multiple environments:

* Development
* Staging
* Production

Azure App Service runs in Production mode by default.

---

# Swagger in Production

Default configuration:

```csharp
if (app.Environment.IsDevelopment())
{
    app.UseSwagger();
    app.UseSwaggerUI();
}
```

Result:

* Swagger works locally
* Swagger returns 404 in Azure

To enable Swagger in Azure:

```csharp
app.UseSwagger();
app.UseSwaggerUI();
```

---

# HTTPS

Azure App Service automatically provides:

* HTTPS Endpoint
* SSL Certificate
* Secure Communication

Example:

```text
https://employee-api-hanmant.azurewebsites.net
```

---

# Git Commands Used

Initialize Repository

```bash
git init
```

Commit Code

```bash
git add .
git commit -m "Initial Employee API"
```

Push to GitHub

```bash
git push
```

---

# Day 2 Hands-On Completed

✓ Created ASP.NET Core Web API

✓ Created Azure App Service

✓ Created App Service Plan

✓ Published Application to Azure

✓ Verified Public URL

✓ Connected Visual Studio with Azure

✓ Updated GitHub Repository

---

# Key Learning Summary

1. Azure App Service is a PaaS service.
2. Azure manages infrastructure and servers.
3. ASP.NET Core applications can be deployed directly from Visual Studio.
4. Azure provides public HTTPS endpoints automatically.
5. App Service Plans control pricing and compute resources.
6. Azure runs applications in Production environment by default.

---

# Interview Questions & Answers

## Q1. What is Azure App Service?

Azure App Service is a Platform as a Service (PaaS) that allows hosting web applications and APIs without managing servers.

---

## Q2. What is PaaS?

Platform as a Service provides a managed environment for building and deploying applications without managing infrastructure.

---

## Q3. What is the difference between IaaS and PaaS?

IaaS requires managing VMs and operating systems, while PaaS abstracts infrastructure management and focuses on application deployment.

---

## Q4. What is an App Service Plan?

An App Service Plan defines the region, pricing tier, compute resources, and scaling capabilities used by App Services.

---

## Q5. Can multiple App Services use the same App Service Plan?

Yes. Multiple applications can share a single App Service Plan.

---

## Q6. What pricing tier did you use?

F1 (Free Tier).

---

## Q7. How did you deploy your ASP.NET Core API?

Using Visual Studio Publish to Azure App Service.

---

## Q8. What URL do you get after deployment?

Azure provides:

```text
https://<app-name>.azurewebsites.net
```

---

## Q9. Why did Swagger return 404 in Azure?

Swagger was configured only for the Development environment while Azure runs in Production mode.

---

## Q10. What environments are supported by ASP.NET Core?

* Development
* Staging
* Production

---

## Q11. What is HTTPS?

HTTPS is a secure protocol that encrypts communication between clients and servers.

---

## Q12. What is a Web API?

A Web API exposes HTTP endpoints that allow applications to exchange data.

Examples:

```http
GET /employees
POST /employees
PUT /employees/1
DELETE /employees/1
```

---

## Q13. What is an Endpoint?

An endpoint is a URL exposed by an API.

Example:

```http
GET /employees
```

---

## Q14. What are the advantages of Azure App Service?

* Easy deployment
* No server management
* Built-in HTTPS
* Auto scaling
* CI/CD support

---

## Q15. What Azure services have you used so far?

Day 1:

* Resource Group
* Storage Account

Day 2:

* App Service
* App Service Plan

---

# AZ-204 Revision

Remember this hierarchy:

```text
Subscription
    ↓
Resource Group
    ↓
App Service Plan
    ↓
App Service
    ↓
ASP.NET Core API
```

This is a core AZ-204 concept and frequently appears in interviews.
