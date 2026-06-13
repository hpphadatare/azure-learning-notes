# Day 7 - Azure Key Vault & Managed Identity

## Objective

Secure application secrets using Azure Key Vault and access them securely through Managed Identity.

By the end of Day 7:

* Azure Key Vault created
* Secrets stored securely
* Managed Identity enabled
* App Service connected to Key Vault
* Connection strings removed from code

---

# Architecture

ASP.NET Core API
↓
Azure App Service
↓
Managed Identity
↓
Azure Key Vault
↓
Secrets
↓
Azure SQL Database

---

# Why Key Vault?

Avoid storing secrets in:

❌ appsettings.json

❌ Source Code

❌ GitHub Repository

Store secrets in:

✅ Azure Key Vault

---

# Azure Key Vault

Azure Key Vault is a secure service used to store:

* Passwords
* Connection Strings
* API Keys
* Certificates
* Encryption Keys

Example Secret:

```text
SqlConnectionString
```

---

# Managed Identity

Managed Identity allows Azure resources to authenticate securely without storing usernames or passwords.

Example:

App Service
↓
Managed Identity
↓
Key Vault

No credentials required.

---

# Types of Managed Identity

## System Assigned

* Created automatically
* Tied to one Azure resource
* Deleted when resource is deleted

## User Assigned

* Separate Azure resource
* Can be shared by multiple services
* Reusable

---

# Key Vault Reference (Recommended)

Store secret in Key Vault:

```text
SqlConnectionString
```

App Service Configuration:

```text
ConnectionStrings__DefaultConnection
```

Value:

```text
@Microsoft.KeyVault(SecretUri=https://your-vault.vault.azure.net/secrets/SqlConnectionString/)
```

No code changes required.

---

# Reading Secret in ASP.NET Core

Application reads normally:

```csharp
builder.Services.AddDbContext<AppDbContext>(options =>
{
    options.UseSqlServer(
        builder.Configuration.GetConnectionString("DefaultConnection"));
});
```

Azure automatically resolves the secret from Key Vault.

---

# Required Azure Role

Grant App Service access:

```text
Key Vault Secrets User
```

Assigned to:

```text
Managed Identity
```

---

# Azure SDK Approach

Packages:

```bash
dotnet add package Azure.Identity

dotnet add package Azure.Security.KeyVault.Secrets
```

Example:

```csharp
var client = new SecretClient(
    new Uri("https://kv-learning.vault.azure.net/"),
    new DefaultAzureCredential());

var secret =
    await client.GetSecretAsync("SqlConnectionString");
```

---

# Security Best Practices

✅ Use Managed Identity

✅ Use Key Vault References

✅ Store secrets outside code

✅ Use RBAC permissions

❌ Never commit secrets to GitHub

❌ Never hardcode passwords

---

# Learning Summary

* Azure Key Vault stores secrets securely
* Managed Identity eliminates stored credentials
* App Service can access Key Vault securely
* Key Vault References require no code changes
* Production applications should avoid storing secrets in configuration files

---

# Interview Questions

## What is Azure Key Vault?

A secure Azure service used to store secrets, certificates, passwords and encryption keys.

---

## Why use Azure Key Vault?

To securely store sensitive information outside source code and configuration files.

---

## What is Managed Identity?

An Azure-managed identity used to authenticate Azure resources without storing credentials.

---

## What are the types of Managed Identity?

1. System Assigned
2. User Assigned

---

## What is the difference between System Assigned and User Assigned Identity?

System Assigned:

* One resource
* Deleted with resource

User Assigned:

* Independent resource
* Reusable across services

---

## What is a Key Vault Reference?

A special App Service configuration value that automatically retrieves secrets from Azure Key Vault.

Example:

```text
@Microsoft.KeyVault(...)
```

---

## What role is required to read Key Vault secrets?

```text
Key Vault Secrets User
```

---

## What is DefaultAzureCredential?

A credential provider from Azure.Identity that automatically uses:

* Managed Identity
* Azure CLI Login
* Visual Studio Login

depending on the environment.

---

## Why is Managed Identity preferred over storing credentials?

Because credentials are never exposed or managed by developers.

---

## What AZ-204 topics are covered?

* Azure Security
* Azure Key Vault
* Managed Identity
* RBAC
* Secret Management
* Authentication

---

# AZ-204 Revision Diagram

Azure App Service
↓
Managed Identity
↓
Azure Key Vault
↓
Connection String
↓
Azure SQL Database

Key Principle:

"Never store secrets in source code. Store them in Azure Key Vault and access them through Managed Identity."
