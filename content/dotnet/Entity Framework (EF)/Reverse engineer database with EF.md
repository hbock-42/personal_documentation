---
creation date: 2023-12-18 20:39
tags:
  - dotnet
  - database
  - orm
---
# Create database connection and entity classes from existing database
```bash
dotnet ef dbcontext scaffold -f "Host=localhost;Database=testdb;Username=hugo_read_only;Password=izob2orbillybob" Npgsql.EntityFrameworkCore.PostgreSQL
```
