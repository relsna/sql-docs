---
title: 'How to: Activate Service Broker Message Delivery in Databases (Transact-SQL)'
description: "By default, Service Broker message delivery is active in a database when the database is created."
ms.prod: sql
ms.technology: configuration
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.reviewer: mikeray
ms.date: "03/30/2022"
---

# How to: Activate Service Broker Message Delivery in Databases (Transact-SQL)

[!INCLUDE [sql-asdbmi](../../includes/applies-to-version/sql-asdbmi.md)]

By default, Service Broker message delivery is active in a database when the database is created. When message delivery is not active, messages remain in the transmission queue. To determine whether Service Broker is active for a database, check the **is_broker_enabled** column of the **sys.databases** catalog view.

> [!NOTE]
> Activating Service Broker allows messages to be delivered to the database. A Service Broker endpoint must be created to send and receive messages from outside of the instance.

## To activate Service Broker in a database

- Alter the database to set the ENABLE_BROKER option.

## Example

```sql
    USE master ;
    GO

    ALTER DATABASE AdventureWorks2008R2 SET ENABLE_BROKER ;
    GO
```

[!INCLUDE [SQL Server Service Broker AdventureWorks2008R2](../../includes/service-broker-adventureworks-2008-r2.md)]

## See also

- [How to: Deactivate Service Broker Message Delivery in Databases (Transact-SQL)](how-to-deactivate-service-broker-message-delivery-in-databases-transact-sql.md)
- [How to: Activate Service Broker Networking (Transact-SQL)](how-to-activate-service-broker-networking-transact-sql.md)
- [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)
- [sys.databases (Transact-SQL)](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)[sys.transmission_queue (Transact-SQL)](../../relational-databases/system-catalog-views/sys-transmission-queue-transact-sql.md)