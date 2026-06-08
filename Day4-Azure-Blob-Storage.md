# Day 4 - Azure Blob Storage & File Upload API (AZ-204)

## Objective

Learn Azure Blob Storage and integrate it with ASP.NET Core Web API for file uploads.

By the end of Day 4:

* Azure Storage Account configured
* Blob Container created
* Azure Storage SDK integrated
* File Upload API implemented
* Files uploaded to Azure Blob Storage
* Blob URL returned to client

---

# Architecture

```text
React Application
        ↓
ASP.NET Core API
        ↓
Azure Blob Storage
        ↓
Documents / Images / PDFs
```

---

# What is Azure Blob Storage?

Azure Blob Storage is Microsoft's object storage service used for storing large amounts of unstructured data.

Examples:

* Images
* PDFs
* Videos
* Documents
* Backups
* Logs

---

# Why Use Blob Storage?

Instead of storing files in SQL Server:

❌ Large database size

❌ Poor performance

❌ Expensive storage

Use Blob Storage:

✅ Optimized for files

✅ Cost effective

✅ Highly scalable

✅ Secure

---

# Blob Storage Hierarchy

```text
Storage Account
       ↓
Container
       ↓
Blob (File)
```

Example:

```text
hanmantstorage001
       ↓
documents
       ↓
resume.pdf
photo.jpg
invoice.pdf
```

---

# Important Blob Storage Components

## Storage Account

Top-level Azure resource used to store data.

Examples:

* Blob Storage
* Queue Storage
* Table Storage
* File Storage

Example:

```text
hanmantstorage001
```

---

## Container

A logical folder inside Blob Storage.

Example:

```text
documents
images
resumes
reports
```

---

## Blob

An individual file stored inside a container.

Examples:

```text
resume.pdf
profile.jpg
invoice.pdf
```

---

# Types of Blob Storage

## Block Blob

Used for:

* Images
* PDFs
* Documents
* Videos

Most commonly used.

---

## Append Blob

Used for:

* Logging
* Audit files

Data is appended at the end.

---

## Page Blob

Used for:

* Azure Virtual Machine disks

---

# Azure Storage SDK

NuGet Package:

```bash
dotnet add package Azure.Storage.Blobs
```

Purpose:

* Upload files
* Download files
* Delete files
* Generate URLs

---

# Connection String

Used to connect the application to Azure Storage.

Example:

```text
DefaultEndpointsProtocol=https;
AccountName=storageaccount;
AccountKey=xxxxxxxx;
EndpointSuffix=core.windows.net
```

Store in:

```json
{
  "ConnectionStrings": {
    "StorageConnection": "your-storage-connection-string"
  }
}
```

Never commit secrets to GitHub.

---

# BlobStorageService

Example Service Responsibilities:

* Connect to Storage Account
* Access Container
* Upload Files
* Return Blob URL

---

# File Upload Endpoint

Example:

```csharp
app.MapPost("/upload",
async (
    IFormFile file,
    BlobStorageService storage) =>
{
    var url =
        await storage.UploadAsync(file);

    return Results.Ok(url);
})
.DisableAntiforgery();
```

---

# Why Disable Anti-Forgery?

When uploading files using Minimal APIs:

```text
IFormFile
```

may trigger anti-forgery validation.

For learning/demo APIs:

```csharp
.DisableAntiforgery();
```

prevents runtime errors.

Example error:

```text
Endpoint contains anti-forgery metadata
```

---

# Security Best Practices

Do NOT:

```text
Store connection strings in source code
```

Use:

* Azure Key Vault
* Managed Identity
* Environment Variables

---

# Blob Access Levels

## Private

Recommended

Only authorized users can access files.

---

## Blob

Files accessible via URL.

---

## Container

Entire container publicly accessible.

Not recommended for sensitive files.

---

# Common Use Cases

## Profile Pictures

```text
/profile-images
```

---

## Resume Upload

```text
/resumes
```

---

## Product Images

```text
/product-images
```

---

## Medical Reports

```text
/reports
```

---

# Hands-On Completed

✓ Created Blob Container

✓ Installed Azure.Storage.Blobs SDK

✓ Configured Connection String

✓ Implemented BlobStorageService

✓ Created Upload API

✓ Uploaded File to Azure

✓ Retrieved Blob URL

✓ Fixed Anti-Forgery Issue

---

# Key Learning Summary

1. Blob Storage stores unstructured data.
2. Storage Account contains Containers.
3. Containers contain Blobs.
4. Azure Storage SDK enables upload/download operations.
5. Blob Storage is preferred over SQL Server for files.
6. Private access is recommended for secure applications.
7. Azure Key Vault should store secrets in production.

---

# AZ-204 Interview Questions & Answers

## Q1. What is Azure Blob Storage?

Azure Blob Storage is an object storage service used to store unstructured data such as images, videos, PDFs, and documents.

---

## Q2. What is a Blob?

A Blob (Binary Large Object) is an individual file stored in Azure Blob Storage.

---

## Q3. What is a Container?

A Container is a logical grouping of blobs inside a Storage Account.

---

## Q4. What is the hierarchy of Blob Storage?

```text
Storage Account
      ↓
Container
      ↓
Blob
```

---

## Q5. What are the types of blobs?

1. Block Blob
2. Append Blob
3. Page Blob

---

## Q6. Which blob type is most commonly used?

Block Blob.

Used for:

* Images
* Documents
* PDFs
* Videos

---

## Q7. Why use Blob Storage instead of SQL Server?

Blob Storage is optimized for file storage and is more scalable and cost-effective than storing files in a database.

---

## Q8. Which NuGet package is used for Blob Storage?

```text
Azure.Storage.Blobs
```

---

## Q9. What is a Storage Account?

A Storage Account is an Azure resource that provides access to Blob, Queue, Table, and File storage services.

---

## Q10. What is a Connection String?

A Connection String contains the information required to connect an application to Azure Storage.

---

## Q11. Where should connection strings be stored in production?

* Azure Key Vault
* Managed Identity
* Environment Variables

---

## Q12. What are Blob Access Levels?

* Private
* Blob
* Container

---

## Q13. What is the recommended access level?

Private.

---

## Q14. What is Azure Key Vault?

Azure Key Vault is a service used to securely store:

* Secrets
* Passwords
* Certificates
* Connection Strings

---

## Q15. What are common Blob Storage use cases?

* Profile Images
* Resume Uploads
* Medical Reports
* Product Images
* Invoice PDFs

---

## Q16. How do you upload a file using ASP.NET Core?

Using:

```text
IFormFile
```

and Azure Storage SDK.

---

## Q17. What is Managed Identity?

Managed Identity allows Azure services to authenticate securely without storing credentials.

---

## Q18. What AZ-204 topics are covered in Day 4?

* Azure Storage Accounts
* Azure Blob Storage
* Storage Security
* Azure SDK Integration
* ASP.NET Core File Upload APIs
* Secret Management Concepts

---

# AZ-204 Revision Diagram

```text
Subscription
      ↓
Resource Group
      ↓
Storage Account
      ↓
Container
      ↓
Blob
      ↓
File URL
```

This storage architecture is heavily tested in AZ-204 and commonly used in enterprise ASP.NET Core applications.
