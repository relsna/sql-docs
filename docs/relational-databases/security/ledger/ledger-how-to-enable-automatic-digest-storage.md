---
title: Enable automatic digest storage
description: This article discusses how to enable automatic digest storage in Azure SQL Database using the Azure portal, PowerShell, and the Azure CLI.
ms.service: sql-database
ms.subservice: security
ms.devlang:
ms.custom:
- event-tier1-build-2022
ms.topic: how-to
author: VanMSFT
ms.author: vanto
ms.reviewer: kendralittle, mathoma
ms.date: "05/24/2022"
monikerRange: "= azuresqldb-current"
---

# Enable automatic digest storage

[!INCLUDE [Azure SQL Database](../../../includes/applies-to-version/asdb.md)]

In this article, we'll describe how you can configure automatic generation and storage of database digests through the Azure portal, PowerShell, or the Azure CLI.

## Prerequisites

- Have an active Azure subscription. If you don't have one, [create a free account](https://azure.microsoft.com/free/).
- An Azure SQL Database

## Enable automatic digest storage using the Azure portal

# [Portal](#tab/Portal)

1. Open the [Azure portal](https://portal.azure.com/) and locate the database for which you want to enable automatic digest storage. Select that database in SQL Database.
> [!NOTE]
> Enable automatic digest storage can also be configured when creating a new database.

1. In **Security**, select the **Ledger** option. 

   :::image type="content" source="media/ledger/ledger-portal-manage-ledger.png" alt-text="Screenshot that shows the Azure portal with the Security Ledger tab selected.":::

1. In the **Ledger** pane, select **Enable automatic digest storage**. Select the storage type. You can choose between Azure Storage or Azure Confidential Ledger (ACL). Depending on the storage type you picked, you have to select an existing storage account or ACL, or create a new one. The storage container name is fixed and can't be modified.

   :::image type="content" source="media/ledger/automatic-digest-management.png" alt-text="Screenshot that shows the selections for enabling digest storage.":::

1. Select **Save** to save your automatic digest storage configuration.

# [PowerShell](#tab/PowerShell)

## Enable database digest uploads using PowerShell

Update the database to start uploading ledger digests to the Azure Blob Storage account or Azure Confidential Ledger, by using the [Enable-AzSqlDatabaseLedgerDigestUpload](/powershell/module/az.sql/enable-azsqldatabaseledgerdigestupload) cmdlet. When the endpoint parameter is an Azure Blob Storage endpoint, the database server will create a new container, named **sqldbledgerdigests**, within the storage account and it will start writing ledger digests to the container.
  
*Note: Make sure you modify the parameters ResourceGroupName, ServerName, DatabaseName and Endpoint (ACL endpoint or Azure Storage endpoint)*

```azurepowershell-interactive
Write-host "Enabling ledger digest upload..." 
$ledgerDigestUploadConfig = Enable-AzSqlDatabaseLedgerDigestUpload `
     -ResourceGroupName "ResourceGroup01" `
     -ServerName "Server01" `
     -DatabaseName "Database01" `
     -Endpoint "https://mystorage.blob.core.windows.net"
$ledgerDigestUploadConfig
```

# [Azure CLI](#tab/AzureCLI)

## Enable database digest uploads using the Azure CLI

Update the database to start uploading ledger digests to the Azure Blob Storage account or Azure Confidential Ledger, by using the [az sql db ledger-digest-uploads enable](/cli/azure/sql/db) command.  

> [!NOTE]
> Modify the parameters `name`, `resource-group`, `server` and `endpoint` (ACL endpoint or Azure Storage endpoint)

```azurecli-interactive
az sql db ledger-digest-uploads enable \
    --name Database01 \
    --resource-group ResourceGroup01 \
    --server Server01 \
    --endpoint https://mystorage.blob.core.windows.net
```

---

## Next steps

- [Ledger overview](ledger-overview.md)
- [Digest management](ledger-digest-management.md)
- [Verify a ledger table to detect tampering](ledger-verify-database.md)
- [sys.database_ledger_digest_locations](/sql/relational-databases/system-catalog-views/sys-database-ledger-digest-locations-transact-sql)
- [sp_verify_database_ledger_from_digest_storage](/sql/relational-databases/system-stored-procedures/sys-sp-verify-database-ledger-from-digest-storage-transact-sql)