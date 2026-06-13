# Day 5 - React + Azure Integration

## Objective

Connect a React frontend with an ASP.NET Core Web API hosted on Azure App Service.

---

# Architecture

React Frontend
↓
Axios / Fetch API
↓
Azure App Service
↓
ASP.NET Core API
↓
Azure SQL Database

---

# Key Concepts

## React

Frontend framework used to build user interfaces.

## Axios

JavaScript library used to make HTTP requests.

Example:

```javascript
axios.get(`${API_URL}/employees`);
```

## REST API

Communication between React and ASP.NET Core using:

* GET
* POST
* PUT
* DELETE

---

# CORS

Cross-Origin Resource Sharing allows React and API hosted on different domains to communicate.

Configuration:

```csharp
builder.Services.AddCors(options =>
{
    options.AddPolicy("ReactPolicy",
        policy =>
        {
            policy.AllowAnyOrigin()
                  .AllowAnyMethod()
                  .AllowAnyHeader();
        });
});

app.UseCors("ReactPolicy");
```

---

# Environment Variables

Store API URLs outside code.

Example:

```env
VITE_API_URL=https://employee-api.azurewebsites.net
```

Access:

```javascript
const API_URL = import.meta.env.VITE_API_URL;
```

---

# Learning Summary

* React consumes Azure-hosted APIs
* Axios simplifies API calls
* CORS enables frontend-backend communication
* Environment variables support multiple environments

---

# Interview Questions

## What is CORS?

A browser security mechanism that controls access between different origins.

## Why is CORS needed?

React and API are usually hosted on different domains.

## What is Axios?

A JavaScript library for sending HTTP requests.

## How does React communicate with ASP.NET Core?

Using REST APIs over HTTP.

## What is a REST API?

An API that exposes resources using HTTP methods such as GET, POST, PUT and DELETE.
