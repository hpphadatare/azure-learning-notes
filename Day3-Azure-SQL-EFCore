# Day 3 - Azure SQL Database & Entity Framework Core

## Objective

Connect the ASP.NET Core Web API to Azure SQL Database using Entity Framework Core.

By the end of Day 3:

* Azure SQL Database created
* SQL Server created
* Entity Framework Core configured
* Database migrations executed
* Employees table created
* API connected to Azure SQL

---

# Architecture

```text
ASP.NET Core Web API
          ↓
    Entity Framework Core
          ↓
     Azure SQL Database
```

---

# What is Azure SQL Database?

Azure SQL Database is a fully managed relational database service based on Microsoft SQL Server.

Azure manages:

* Backups
* Security
* Updates
* High Availability
* Monitoring

Benefits:

* No server maintenance
* Automatic backups
* Built-in security
* Cloud scalability

---

# SQL Server vs Azure SQL Database

| Feature        | SQL Server   | Azure SQL Database |
| -------------- | ------------ | ------------------ |
| Hosting        | Self Managed | Managed by Azure   |
| Updates        | Manual       | Automatic          |
| Backups        | Manual       | Automatic          |
| Infrastructure | Customer     | Azure              |
| Scaling        | Manual       | Easy               |

---

# Important Components

## SQL Server

A logical database server hosted in Azure.

Example:

```text
employee-sql-hanmant.database.windows.net
```

Contains one or more databases.

---

## Database

Stores application data.

Example:

```text
EmployeeDB
```

Contains tables such as:

```text
Employees
Departments
Users
```

---

## Connection String

Used by applications to connect to the database.

Example:

```text
Server=tcp:employee-sql.database.windows.net;
Database=EmployeeDB;
User ID=sqladmin;
Password=********;
```

Never commit passwords to GitHub.

---

# Entity Framework Core

## What is Entity Framework Core?

Entity Framework Core (EF Core) is Microsoft's ORM (Object Relational Mapper).

It converts:

```text
C# Objects
      ↓
SQL Queries
      ↓
Database Tables
```

Benefits:

* Less SQL writing
* Faster development
* Type safety
* Migration support

---

# ORM (Object Relational Mapper)

ORM maps:

```text
C# Class
    ↓
Database Table
```

Example:

```csharp
public class Employee
{
    public int Id { get; set; }

    public string Name { get; set; } = "";

    public string Email { get; set; } = "";
}
```

Creates:

```sql
Employees
---------
Id
Name
Email
```

---

# Employee Entity

```csharp
public class Employee
{
    public int Id { get; set; }

    public string Name { get; set; } = "";

    public string Email { get; set; } = "";

    public string Department { get; set; } = "";
}
```

---

# DbContext

## What is DbContext?

DbContext acts as a bridge between ASP.NET Core and the database.

Example:

```csharp
public class AppDbContext : DbContext
{
    public AppDbContext(DbContextOptions<AppDbContext> options)
        : base(options)
    {
    }

    public DbSet<Employee> Employees => Set<Employee>();
}
```

Responsibilities:

* Database connection
* Query execution
* Tracking changes
* Saving data

---

# DbSet

Represents a table in the database.

Example:

```csharp
public DbSet<Employee> Employees => Set<Employee>();
```

Maps to:

```text
Employees Table
```

---

# Dependency Injection Registration

Program.cs

```csharp
builder.Services.AddDbContext<AppDbContext>(options =>
    options.UseSqlServer(
        builder.Configuration.GetConnectionString("DefaultConnection")));
```

Purpose:

* Registers DbContext
* Enables dependency injection
* Configures SQL Server connection

---

# appsettings.json

Store connection string.

Example:

```json
{
  "ConnectionStrings": {
    "DefaultConnection": "Server=tcp:employee-sql.database.windows.net;Database=EmployeeDB;User ID=sqladmin;Password=YourPassword;"
  }
}
```

Best Practice:

Use Azure Key Vault in production.

---

# Migrations

## What is a Migration?

Migration is a mechanism that tracks database schema changes.

Example:

```text
Employee class changed
         ↓
Migration Generated
         ↓
Database Updated
```

Benefits:

* Version control for database schema
* Easy deployment
* Repeatable changes

---

# Create Migration

```bash
dotnet ef migrations add InitialCreate
```

Result:

```text
Migrations
 ├── InitialCreate.cs
 └── Snapshot.cs
```

---

# Apply Migration

```bash
dotnet ef database update
```

Result:

```text
Azure SQL Database
       ↓
Employees Table Created
```

---

# CRUD Operations

CRUD =

| Operation | Meaning  |
| --------- | -------- |
| Create    | Insert   |
| Read      | Retrieve |
| Update    | Modify   |
| Delete    | Remove   |

Examples:

```http
POST /employees
GET /employees
PUT /employees/1
DELETE /employees/1
```

---

# NuGet Packages Used

Install:

```bash
dotnet add package Microsoft.EntityFrameworkCore.SqlServer

dotnet add package Microsoft.EntityFrameworkCore.Tools
```

Purpose:

* SQL Server support
* Migration support

---

# Hands-On Completed

✓ Azure SQL Database Created

✓ SQL Server Created

✓ EF Core Installed

✓ Employee Model Created

✓ DbContext Created

✓ Connection String Configured

✓ Migration Generated

✓ Database Updated

✓ API Connected to Azure SQL

---

# Key Learning Summary

1. Azure SQL Database is a managed SQL Server service.
2. EF Core simplifies database operations.
3. DbContext manages database communication.
4. DbSet represents database tables.
5. Migrations manage schema changes.
6. Connection Strings connect applications to databases.
7. ASP.NET Core integrates with Azure SQL using EF Core.

---

# Interview Questions & Answers

## Q1. What is Azure SQL Database?

Azure SQL Database is a fully managed relational database service provided by Microsoft Azure.

---

## Q2. What is the difference between SQL Server and Azure SQL Database?

SQL Server is self-managed, while Azure SQL Database is fully managed by Azure.

---

## Q3. What is Entity Framework Core?

Entity Framework Core is an ORM framework that enables .NET applications to interact with relational databases using C# objects.

---

## Q4. What is an ORM?

ORM (Object Relational Mapper) maps C# classes to database tables.

---

## Q5. What is DbContext?

DbContext is the primary EF Core class used to interact with the database.

---

## Q6. What is DbSet?

DbSet represents a database table within DbContext.

---

## Q7. What is a Migration?

A migration is a version-controlled set of database schema changes.

---

## Q8. Why are migrations useful?

They allow database schema changes to be tracked and deployed consistently.

---

## Q9. How do you create a migration?

```bash
dotnet ef migrations add InitialCreate
```

---

## Q10. How do you apply migrations?

```bash
dotnet ef database update
```

---

## Q11. What is a Connection String?

A connection string contains the information required to connect an application to a database.

---

## Q12. Where should connection strings be stored?

Development:

* appsettings.json

Production:

* Azure Key Vault
* Azure App Configuration

---

## Q13. What is Dependency Injection?

Dependency Injection is a design pattern that provides required services to classes automatically.

---

## Q14. Why use EF Core instead of writing SQL manually?

Benefits:

* Faster development
* Strong typing
* Easier maintenance
* Migration support

---

## Q15. What Azure services are used in this architecture?

* Azure App Service
* Azure SQL Database
* Resource Group

---

## Q16. What is CRUD?

CRUD stands for:

* Create
* Read
* Update
* Delete

---

## Q17. What is a Primary Key?

A primary key uniquely identifies each row in a table.

Example:

```text
EmployeeId
```

---

## Q18. What happens when dotnet ef database update runs?

EF Core executes migration scripts and updates the database schema.

---

# AZ-204 Revision

Remember this architecture:

```text
Subscription
      ↓
Resource Group
      ↓
App Service
      ↓
ASP.NET Core API
      ↓
Entity Framework Core
      ↓
Azure SQL Database
```

This architecture is one of the most common patterns used in Azure-based .NET applications.
