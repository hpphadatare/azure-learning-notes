# Day 6 - Full Stack Azure Deployment

## Objective

Deploy the complete application to Azure and verify end-to-end functionality.

---

# Architecture

Azure Static Web App
↓
React Frontend
↓
Azure App Service
↓
ASP.NET Core API
↓
Azure SQL Database

↓

Azure Blob Storage

---

# Azure Services Used

## Azure Static Web Apps

Hosts React frontend.

Features:

* Free SSL
* Global CDN
* GitHub Integration

## Azure App Service

Hosts ASP.NET Core API.

## Azure SQL Database

Stores application data.

## Azure Blob Storage

Stores files and documents.

---

# Deployment Steps

## Backend

Publish ASP.NET Core API to Azure App Service.

## Frontend

Build React application:

```bash
npm run build
```

Deploy to Azure Static Web Apps.

## Database

Verify Azure SQL connectivity.

## Storage

Verify Blob upload functionality.

---

# Production Configuration

Environment Variable:

```env
VITE_API_URL=https://employee-api.azurewebsites.net
```

Avoid hardcoded URLs.

---

# Common Issues

## 405 Method Not Allowed

Occurs when calling an endpoint with the wrong HTTP method.

Example:

```text
POST /employees
```

while API only supports:

```text
POST /add-employee
```

## CORS Error

Configure CORS policy in ASP.NET Core.

## SQL Connection Error

Verify firewall settings and connection string.

## Blob Upload Error

Verify storage connection string and container name.

---

# Learning Summary

* React deployed to Azure
* ASP.NET Core API deployed to Azure
* Azure SQL integrated
* Azure Blob Storage integrated
* Full-stack application running in cloud

---

# Interview Questions

## Which Azure service hosts React applications?

Azure Static Web Apps.

## Which Azure service hosts ASP.NET Core APIs?

Azure App Service.

## Which Azure service stores relational data?

Azure SQL Database.

## Which Azure service stores files?

Azure Blob Storage.

## What is a production build?

Optimized build generated using:

```bash
npm run build
```

## Why use environment variables?

To manage configuration for different environments.

## What is a full-stack deployment?

Deployment of frontend, backend, database, and storage components together.

---

# Final Architecture Revision

React
↓
Azure Static Web Apps
↓
ASP.NET Core API
↓
Azure App Service
↓
Azure SQL Database

↓

Azure Blob Storage
