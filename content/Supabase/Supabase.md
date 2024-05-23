---
title: Supabase
creation date: 2024-05-23 01:54
draft: false
tags:
  - documentation
  - supabase
  - database
  - postgres
---
# Foreign Data Wrapper
Allow access to remote data (external database, api, etc...) directly from postgres
For exemple, you can have a representation of data accessible trough Stripe api, like Customers table, Transaction table, etc ... directly in Supabase database.

https://supabase.com/docs/guides/database/extensions/wrappers/stripe

#### List installed extensions
```sql
SELECT * 
FROM pg_extension;
```

#### List foreign server information
```sql
select
	srvname as name,
	srvowner::regrole as owner,
	fdwname as wrapper,
	srvoptions as options
from pg_foreign_server
join pg_foreign_data_wrapper w on w.oid = srvfdw;
```

# RLS
![Video example](https://www.youtube.com/watch?v=Ow_Uzedfohk)
