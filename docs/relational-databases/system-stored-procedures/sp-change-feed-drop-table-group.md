---
description: "The sp_change_feed_drop_table_group system stored procedure drops a table group and internal metadata objects for Azure Synapse Link for SQL."
title: "sp_change_feed_drop_table_group (Transact-SQL)"
ms.custom:
- event-tier1-build-2022
ms.date: "05/24/2022"
ms.service: synapse-analytics
ms.prod_service: "database-engine, sql-database, synapse-analytics"
ms.reviewer: ""
ms.topic: "reference"
f1_keywords: 
  - "sp_change_feed_drop_table_group_TSQL"
  - "sp_change_feed_drop_table_group"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "sp_change_feed_drop_table_group"
author: WilliamDAssafMSFT
ms.author: wiassaf
monikerRange: ">=sql-server-ver16 || =azuresqldb-current"
---
# sp_change_feed_drop_table_group (Transact-SQL)
[!INCLUDE [sqlserver2022-asdb](../../includes/applies-to-version/sqlserver2022-asdb.md)]

Drops a table group and internal metadata objects for [Azure Synapse Link for SQL](/azure/synapse-analytics/synapse-link/sql-synapse-link-overview). For more information, see [Manage Azure Synapse Link for SQL Server and Azure SQL Database](../../sql-server/synapse-link/synapse-link-sql-server-change-feed-manage.md).

> [!NOTE]
> This stored procedure is used internally and is not recommended for direct administrative use. Use Synapse Studio instead. Using this procedure will introduce inconsistency with Synapse Workspace configuration.

## Syntax  
   
 ![Topic link icon](../../database-engine/configure-windows/media/topic-link.gif "Topic link icon") [Transact-SQL Syntax Conventions](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
```syntaxsql  
EXECUTE sys.sp_change_feed_drop_table_group
      @table_group_id  
GO
```  

## Arguments  

#### @table_group_id

Required. Data type is uniqueidentifier. 

The unique identifier of the table group. It is a GUID generated by the initial setup.

## Permissions  

 Only a member of the sysadmin server role or db_owner database role can execute this procedure. 

## See also  

- [What is Synapse Link for SQL?](/azure/synapse-analytics/synapse-link/sql-synapse-link-overview)
- [sp_change_feed_disable_db (Transact-SQL)](sp-change-feed-disable-db.md)
- [sp_change_feed_disable_table (Transact-SQL)](sp-change-feed-disable-table.md)


## Next steps

- [Manage Azure Synapse Link for SQL Server and Azure SQL Database](../../sql-server/synapse-link/synapse-link-sql-server-change-feed-manage.md)
- [Get started with Synapse Link for SQL Server 2022 (Preview)](/azure/synapse-analytics/synapse-link/connect-synapse-link-sql-server-2022)