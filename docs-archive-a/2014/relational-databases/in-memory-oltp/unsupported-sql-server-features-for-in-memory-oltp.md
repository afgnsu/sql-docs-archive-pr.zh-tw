---
title: 支援的 SQL Server 功能 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: c39f03a7-e223-4fd7-bd30-142e28f51654
author: rothja
ms.author: jroth
ms.openlocfilehash: e7eb4324d56c3ab45486063cb8097603ac3a416b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708334"
---
# <a name="supported-sql-server-features"></a><span data-ttu-id="37791-102">支援的 SQL Server 功能</span><span class="sxs-lookup"><span data-stu-id="37791-102">Supported SQL Server Features</span></span>
  <span data-ttu-id="37791-103">本主題會討論在使用記憶體最佳化的物件時，所支援或不支援的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 功能。</span><span class="sxs-lookup"><span data-stu-id="37791-103">This topic discusses [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features that are or not supported for use with memory-optimized objects.</span></span>  
  
## <a name="ssnoversion-features-supported-for-in-memory-oltp"></a><span data-ttu-id="37791-104">記憶體中 OLTP 支援的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 功能</span><span class="sxs-lookup"><span data-stu-id="37791-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Features Supported for In-Memory OLTP</span></span>  
 <span data-ttu-id="37791-105">擁有記憶體最佳化之物件的資料庫可以支援下列 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 功能，包括記憶體最佳化的檔案群組在內。</span><span class="sxs-lookup"><span data-stu-id="37791-105">The following [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features are supported on a database that has memory-optimized objects, including memory-optimized filegroup.</span></span>  
  
 <span data-ttu-id="37791-106">如需有關支援之資料類型的資訊，請參閱＜ [Supported Data Types](supported-data-types-for-in-memory-oltp.md)＞。</span><span class="sxs-lookup"><span data-stu-id="37791-106">For information about supported data types, see [Supported Data Types](supported-data-types-for-in-memory-oltp.md).</span></span>  
  
-   <span data-ttu-id="37791-107">記憶體最佳化之資料表支援的選項和作業。</span><span class="sxs-lookup"><span data-stu-id="37791-107">Options and operations supported on memory-optimized tables.</span></span> <span data-ttu-id="37791-108">如需詳細資訊，請參閱 [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="37791-108">For more information, see [CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql).</span></span>  
  
-   <span data-ttu-id="37791-109">原生編譯的預存程序上支援的選項和作業。</span><span class="sxs-lookup"><span data-stu-id="37791-109">Options and operations supported on natively compiled stored procedures.</span></span> <span data-ttu-id="37791-110">如需詳細資訊，請參閱 [CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="37791-110">For more information, see [CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql).</span></span>  
  
-   <span data-ttu-id="37791-111">能夠使用解譯的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 存取記憶體最佳化的資料表。</span><span class="sxs-lookup"><span data-stu-id="37791-111">Ability to access memory-optimized tables using interpreted [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="37791-112">解譯的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 會提供相當於存取不是記憶體最佳化的資料表的介面區，其方式是使用非原生編譯的預存程序和使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="37791-112">Interpreted [!INCLUDE[tsql](../../../includes/tsql-md.md)] provides surface area equivalent to accessing tables that are not memory optimized using stored procedures that are not natively compiled and using [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="37791-113">如需詳細資訊，請參閱[使用解譯的 Transact-SQL 存取記憶體最佳化的資料表](accessing-memory-optimized-tables-using-interpreted-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="37791-113">For more information, see [Accessing Memory-Optimized Tables Using Interpreted Transact-SQL](accessing-memory-optimized-tables-using-interpreted-transact-sql.md).</span></span>  
  
-   <span data-ttu-id="37791-114">多重版本設定和開放式並行存取控制。</span><span class="sxs-lookup"><span data-stu-id="37791-114">Multi-versioning and optimistic concurrency control.</span></span> <span data-ttu-id="37791-115">如需詳細資訊，請參閱 [Transaction Isolation Levels](../../database-engine/transaction-isolation-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="37791-115">For more information, see [Transaction Isolation Levels](../../database-engine/transaction-isolation-levels.md).</span></span>  
  
-   <span data-ttu-id="37791-116">備份和還原包含記憶體最佳化之資料檔案群組的資料庫。</span><span class="sxs-lookup"><span data-stu-id="37791-116">Backup and Restore of a database that contains memory-optimized data filegroup.</span></span> <span data-ttu-id="37791-117">如需詳細資訊，請參閱[SQL Server 資料庫的備份與還原](../backup-restore/back-up-and-restore-of-sql-server-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="37791-117">For more information, see [Back Up and Restore of SQL Server Databases](../backup-restore/back-up-and-restore-of-sql-server-databases.md).</span></span>  
  
-   <span data-ttu-id="37791-118">為了可支援性而提供的目錄檢視、動態管理檢視和擴充的事件。</span><span class="sxs-lookup"><span data-stu-id="37791-118">Catalog views, dynamic management views, and extended events for supportability.</span></span> <span data-ttu-id="37791-119">如需詳細資訊，請參閱[記憶體內部 OLTP 的系統檢視表、預存程序、DMV 和等待類型](../../database-engine/system-views-stored-procedures-dmvs-and-wait-types-for-in-memory-oltp.md)。</span><span class="sxs-lookup"><span data-stu-id="37791-119">For more information, see [System Views, Stored Procedures, DMVs and Wait Types for In-Memory OLTP](../../database-engine/system-views-stored-procedures-dmvs-and-wait-types-for-in-memory-oltp.md).</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="37791-120">管理物件。</span><span class="sxs-lookup"><span data-stu-id="37791-120">Management Objects.</span></span> <span data-ttu-id="37791-121">如需詳細資訊，請參閱[記憶體內部 OLTP 的 SQL Server 管理物件支援](sql-server-management-objects-support-for-in-memory-oltp.md)。</span><span class="sxs-lookup"><span data-stu-id="37791-121">For more information, see [SQL Server Management Objects Support for In-Memory OLTP](sql-server-management-objects-support-for-in-memory-oltp.md).</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="37791-122">.</span><span class="sxs-lookup"><span data-stu-id="37791-122">.</span></span> <span data-ttu-id="37791-123">如需詳細資訊，請參閱[記憶體內部 OLTP 的 SQL Server Management Studio 支援](sql-server-management-studio-support-for-in-memory-oltp.md)。</span><span class="sxs-lookup"><span data-stu-id="37791-123">For more information, see [SQL Server Management Studio Support for In-Memory OLTP](sql-server-management-studio-support-for-in-memory-oltp.md).</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="37791-124">PowerShell。</span><span class="sxs-lookup"><span data-stu-id="37791-124">PowerShell.</span></span> <span data-ttu-id="37791-125">如需詳細資訊，請參閱 ＜ [SQL Server PowerShell 概觀](https://msdn.microsoft.com/library/cc281954\(SQL.105\).aspx)＞。</span><span class="sxs-lookup"><span data-stu-id="37791-125">For more information, see [SQL Server PowerShell Overview](https://msdn.microsoft.com/library/cc281954\(SQL.105\).aspx).</span></span>  
  
-   <span data-ttu-id="37791-126">使用 bcp 公用程式匯入及匯出大量資料。</span><span class="sxs-lookup"><span data-stu-id="37791-126">Import and Export Bulk Data by using the bcp utility.</span></span> <span data-ttu-id="37791-127">如需詳細資訊，請參閱[使用 bcp 公用程式匯入及匯出大量資料 &#40;SQL Server&#41;](../import-export/import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="37791-127">For more information, see [Import and Export Bulk Data by Using the bcp Utility &#40;SQL Server&#41;](../import-export/import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md).</span></span>  
  
-   <span data-ttu-id="37791-128">當機復原。</span><span class="sxs-lookup"><span data-stu-id="37791-128">Crash recovery.</span></span>  
  
-   <span data-ttu-id="37791-129">記憶體最佳化的資料檔案群組中，有多個容器可以用於儲存記憶體中 OLTP 物件，可以縮短復原時間目標 (RTO)。</span><span class="sxs-lookup"><span data-stu-id="37791-129">Multiple containers in a memory-optimized data filegroup to store In-Memory OLTP objects and reduce recovery time objective (RTO).</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="37791-130">交易記錄區塊會計算總和檢查碼及驗證。</span><span class="sxs-lookup"><span data-stu-id="37791-130">transaction log blocks calculate checksum and validate.</span></span>  
  
-   <span data-ttu-id="37791-131">新的 SNAPSHOT 資料表提示。</span><span class="sxs-lookup"><span data-stu-id="37791-131">The new SNAPSHOT table hint.</span></span> <span data-ttu-id="37791-132">如需詳細資訊，請參閱[資料表提示 &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table)。</span><span class="sxs-lookup"><span data-stu-id="37791-132">For more information, see [Table Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table).</span></span>  
  
-   <span data-ttu-id="37791-133">DB COMPAT 層級。</span><span class="sxs-lookup"><span data-stu-id="37791-133">DB COMPAT level.</span></span>  
  
-   <span data-ttu-id="37791-134">部分自主資料庫。</span><span class="sxs-lookup"><span data-stu-id="37791-134">Partially contained database.</span></span> <span data-ttu-id="37791-135">支援自主資料庫驗證。</span><span class="sxs-lookup"><span data-stu-id="37791-135">Contained database authentication is supported.</span></span> <span data-ttu-id="37791-136">不過，所有記憶體中 OLTP 物件在 DMV dm_db_uncontained_entities 中都會標示為中斷內含項目 (Breaking Containment)。</span><span class="sxs-lookup"><span data-stu-id="37791-136">However, all In-Memory OLTP objects are marked as breaking containment in the DMV dm_db_uncontained_entities.</span></span>  
  
-   <span data-ttu-id="37791-137">Service Broker 有限制。</span><span class="sxs-lookup"><span data-stu-id="37791-137">Service broker, with limitations.</span></span> <span data-ttu-id="37791-138">無法從原生編譯的預存程序存取佇列。</span><span class="sxs-lookup"><span data-stu-id="37791-138">Cannot access a queue from a natively compiled stored procedure.</span></span> <span data-ttu-id="37791-139">也無法在存取記憶體最佳化的資料表的交易中存取遠端資料庫內的佇列。</span><span class="sxs-lookup"><span data-stu-id="37791-139">Cannot access a queue in a remote database in a transaction that accesses memory-optimized tables.</span></span>  
  
-   <span data-ttu-id="37791-140">容錯移轉叢集： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Alwayson 容錯移轉叢集實例會利用 Windows Server 容錯移轉叢集 (WSFC) 功能，透過伺服器實例層級的冗余來提供本機高可用性-容錯移轉叢集實例 (FCI) 。</span><span class="sxs-lookup"><span data-stu-id="37791-140">Failover Clustering: As part of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] AlwaysOn offering, AlwaysOn Failover Cluster Instances leverages Windows Server Failover Clustering (WSFC) functionality to provide local high availability through redundancy at the server-instance level-a failover cluster instance (FCI).</span></span> <span data-ttu-id="37791-141">如需詳細資訊，請參閱 [AlwaysOn 容錯移轉叢集執行個體 (SQL Server)](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="37791-141">For more information, see [AlwaysOn Failover Cluster Instances (SQL Server)](../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md).</span></span>  
  
-   <span data-ttu-id="37791-142">與 AlwaysOn 整合： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 提供幾個選項用於建立伺服器或資料庫的高可用性，包括 AlwaysOn。</span><span class="sxs-lookup"><span data-stu-id="37791-142">Integration with AlwaysOn: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides several options for creating high availability for a server or database, including AlwaysOn.</span></span> <span data-ttu-id="37791-143">如需詳細資訊，請參閱 [高可用性解決方案 &#40;SQL Server&#41;](../../sql-server/failover-clusters/high-availability-solutions-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="37791-143">For more information, see [High Availability Solutions &#40;SQL Server&#41;](../../sql-server/failover-clusters/high-availability-solutions-sql-server.md).</span></span>  
  
-   <span data-ttu-id="37791-144">記錄傳送： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 記錄傳送可讓您將主要伺服器執行個體上之主要資料庫中的交易記錄備份，自動傳送到個別之次要伺服器執行個體上的一或多個次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="37791-144">Log shipping: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Log shipping allows you to automatically send transaction log backups from a primary database on a primary server instance to one or more secondary databases on separate secondary server instances.</span></span> <span data-ttu-id="37791-145">如需詳細資訊，請參閱[關於記錄傳送 &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="37791-145">For more information, see [About Log Shipping &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md).</span></span>  
  
-   <span data-ttu-id="37791-146">訂閱者端記憶體最佳化資料表的異動複寫受到支援，但是有一些限制。</span><span class="sxs-lookup"><span data-stu-id="37791-146">Transactional replication to memory-optimized tables on subscribers is supported with some restrictions.</span></span> <span data-ttu-id="37791-147">如需詳細資訊，請參閱[複寫至記憶體最佳化資料表訂閱者](../replication/replication-to-memory-optimized-table-subscribers.md)。</span><span class="sxs-lookup"><span data-stu-id="37791-147">For more information, see [Replication to Memory-Optimized Table Subscribers](../replication/replication-to-memory-optimized-table-subscribers.md).</span></span>  
  
-   <span data-ttu-id="37791-148">資源管理員： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資源管理員功能可讓您用於管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 工作負載及系統資源耗用。</span><span class="sxs-lookup"><span data-stu-id="37791-148">Resource Governor: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Resource Governor is a feature that you can use to manage [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] workload and system resource consumption.</span></span> <span data-ttu-id="37791-149">Resource Governor 可讓您指定內送應用程式要求所能使用的 CPU、實體 IO 和記憶體數量限制。</span><span class="sxs-lookup"><span data-stu-id="37791-149">Resource Governor enables you to specify limits on the amount of CPU, physical IO, and memory that incoming application requests can use.</span></span> <span data-ttu-id="37791-150">如需相關資訊，請參閱 [Managing Memory for In-Memory OLTP](../../database-engine/managing-memory-for-in-memory-oltp.md) 及 [Resource Governor](../resource-governor/resource-governor.md)。</span><span class="sxs-lookup"><span data-stu-id="37791-150">For more information, see [Managing Memory for In-Memory OLTP](../../database-engine/managing-memory-for-in-memory-oltp.md) and [Resource Governor](../resource-governor/resource-governor.md).</span></span>  
  
-   <span data-ttu-id="37791-151">In-Memory OLTP 對於記憶體最佳化資料表中 (var)char 資料行支援的字碼頁，以及索引和原生編譯預存程序中支援的定序有其限制。</span><span class="sxs-lookup"><span data-stu-id="37791-151">In-Memory OLTP has restrictions on supported code pages for (var)char columns in memory-optimized tables and supported collations used in indexes and natively compiled stored procedures.</span></span> <span data-ttu-id="37791-152">如需詳細資訊，請參閱 [Collations and Code Pages](../../database-engine/collations-and-code-pages.md)。</span><span class="sxs-lookup"><span data-stu-id="37791-152">For more information, see [Collations and Code Pages](../../database-engine/collations-and-code-pages.md).</span></span>  
  
-   <span data-ttu-id="37791-153">BACPAC 支援。</span><span class="sxs-lookup"><span data-stu-id="37791-153">BACPAC support.</span></span>  
  
## <a name="ssnoversion-features-not-supported-for-in-memory-oltp"></a>[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="37791-154">記憶體內部 OLTP 不支援的功能</span><span class="sxs-lookup"><span data-stu-id="37791-154">Features Not Supported for In-Memory OLTP</span></span>  
 <span data-ttu-id="37791-155">擁有記憶體最佳化之物件的資料庫不支援下列 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 功能，包括記憶體最佳化的資料檔案群組在內。</span><span class="sxs-lookup"><span data-stu-id="37791-155">The following [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features are not supported on a database that has memory-optimized objects (including memory-optimized data filegroup).</span></span>  
  
|<span data-ttu-id="37791-156">不支援的功能</span><span class="sxs-lookup"><span data-stu-id="37791-156">Unsupported Feature</span></span>|<span data-ttu-id="37791-157">功能描述</span><span class="sxs-lookup"><span data-stu-id="37791-157">Feature Description</span></span>|  
|-------------------------|-------------------------|  
|<span data-ttu-id="37791-158">記憶體最佳化之資料表的資料壓縮。</span><span class="sxs-lookup"><span data-stu-id="37791-158">Data compression for memory-optimized tables.</span></span>|<span data-ttu-id="37791-159">使用資料壓縮功能有助於將資料壓縮在資料庫內及縮小資料庫的大小。</span><span class="sxs-lookup"><span data-stu-id="37791-159">You can use the data compression feature to help compress the data inside a database, and to help reduce the size of the database.</span></span> <span data-ttu-id="37791-160">如需詳細資訊，請參閱 [Data Compression](../data-compression/data-compression.md)。</span><span class="sxs-lookup"><span data-stu-id="37791-160">For more information, see [Data Compression](../data-compression/data-compression.md).</span></span>|  
|<span data-ttu-id="37791-161">分割記憶體最佳化的資料表與雜湊索引。</span><span class="sxs-lookup"><span data-stu-id="37791-161">Partitioning of memory-optimized tables and HASH indexes.</span></span>|<span data-ttu-id="37791-162">資料分割資料表和索引的資料，已分成可以在資料庫中的多個檔案群組之間分佈的單位。</span><span class="sxs-lookup"><span data-stu-id="37791-162">The data of partitioned tables and indexes is divided into units that can be spread across more than one filegroup in a database.</span></span> <span data-ttu-id="37791-163">如需詳細資訊，請參閱＜ [Partitioned Tables and Indexes](../partitions/partitioned-tables-and-indexes.md)＞。</span><span class="sxs-lookup"><span data-stu-id="37791-163">For more information, see [Partitioned Tables and Indexes](../partitions/partitioned-tables-and-indexes.md).</span></span>|  
|<span data-ttu-id="37791-164">記憶體最佳化資料庫資料檔案群組上的透明資料加密 (Transparent Data Encryption，TDE)。</span><span class="sxs-lookup"><span data-stu-id="37791-164">Transparent Data Encryption (TDE) on the memory-optimized data filegroup of a database.</span></span>|<span data-ttu-id="37791-165">透明資料加密 (TDE) 會執行資料和記錄檔的即時 I/O 加密和解密。</span><span class="sxs-lookup"><span data-stu-id="37791-165">Transparent data encryption (TDE) performs real-time I/O encryption and decryption of the data and log files.</span></span> <span data-ttu-id="37791-166">如需詳細資訊，請參閱[透明資料加密 &#40;TDE&#41;](../security/encryption/transparent-data-encryption.md)。</span><span class="sxs-lookup"><span data-stu-id="37791-166">For more information, see [Transparent Data Encryption &#40;TDE&#41;](../security/encryption/transparent-data-encryption.md).</span></span><br /><br /> <span data-ttu-id="37791-167">TDE 可在具有記憶體中 OLTP 物件的資料庫上啟用。</span><span class="sxs-lookup"><span data-stu-id="37791-167">TDE can be enabled on a database that has In-Memory OLTP objects.</span></span> <span data-ttu-id="37791-168">如果啟用 TDE，則會加密記憶體中 OLTP 記錄。</span><span class="sxs-lookup"><span data-stu-id="37791-168">In-Memory OLTP log records are encrypted if TDE is enabled.</span></span> <span data-ttu-id="37791-169">持久性資料表的檢查點檔案不會加密，即便在資料庫上啟用 TDE 也是一樣。</span><span class="sxs-lookup"><span data-stu-id="37791-169">The checkpoint files for durable tables are not encrypted, even if TDE is enabled on the database.</span></span>|  
|<span data-ttu-id="37791-170">複寫</span><span class="sxs-lookup"><span data-stu-id="37791-170">Replication</span></span>|<span data-ttu-id="37791-171">訂閱者端記憶體最佳化資料表的異動複寫以外的複寫組態與參考記憶體最佳化資料表的資料表或檢視表不相容。</span><span class="sxs-lookup"><span data-stu-id="37791-171">Replication configurations other than transactional replication to memory-optimized tables on subscribers are incompatible with tables or views referencing memory-optimized tables.</span></span> <span data-ttu-id="37791-172">如果有記憶體優化的檔案群組，則不支援使用 sync_mode = ' 資料庫快照集 ' 的複寫。</span><span class="sxs-lookup"><span data-stu-id="37791-172">Replication using sync_mode='database snapshot' is not supported if there is a memory-optimized filegroup.</span></span> <span data-ttu-id="37791-173">如需詳細資訊，請參閱[複寫至記憶體最佳化資料表訂閱者](../replication/replication-to-memory-optimized-table-subscribers.md)。</span><span class="sxs-lookup"><span data-stu-id="37791-173">For more information, see [Replication to Memory-Optimized Table Subscribers](../replication/replication-to-memory-optimized-table-subscribers.md).</span></span>|  
|<span data-ttu-id="37791-174">Multiple Active Result Sets (MARS)</span><span class="sxs-lookup"><span data-stu-id="37791-174">Multiple Active Result Sets (MARS)</span></span>|<span data-ttu-id="37791-175">記憶體最佳化資料表不支援 Multiple Active Result Sets (MARS)。</span><span class="sxs-lookup"><span data-stu-id="37791-175">Multiple Active Result Sets (MARS) is not supported with memory-optimized tables.</span></span> <span data-ttu-id="37791-176">此錯誤也可能表示使用連結的伺服器。</span><span class="sxs-lookup"><span data-stu-id="37791-176">This error can also indicate linked server use.</span></span> <span data-ttu-id="37791-177">連結的伺服器可以使用 MARS。</span><span class="sxs-lookup"><span data-stu-id="37791-177">Linked server can use MARS.</span></span> <span data-ttu-id="37791-178">記憶體最佳化資料表中不支援連結的伺服器。</span><span class="sxs-lookup"><span data-stu-id="37791-178">Linked servers are not supported with memory-optimized tables.</span></span> <span data-ttu-id="37791-179">請改為直接連接至裝載記憶體最佳化資料表的伺服器和資料庫。</span><span class="sxs-lookup"><span data-stu-id="37791-179">Instead, connect directly to the server and database that hosts the memory-optimized tables.</span></span>|  
|<span data-ttu-id="37791-180">鏡像</span><span class="sxs-lookup"><span data-stu-id="37791-180">Mirroring</span></span>|<span data-ttu-id="37791-181">資料庫鏡像是增加 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫可用性的解決方案。</span><span class="sxs-lookup"><span data-stu-id="37791-181">Database mirroring is a solution for increasing the availability of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="37791-182">如需詳細資訊，請參閱[資料庫鏡像 &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="37791-182">For more information, see [Database Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md).</span></span>|  
|<span data-ttu-id="37791-183">重建記錄檔</span><span class="sxs-lookup"><span data-stu-id="37791-183">Rebuild log</span></span>|<span data-ttu-id="37791-184">具有 MEMORY_OPTIMIZED_DATA 檔案群組的資料庫不支援透過附加或 ALTER DATABASE 重建記錄檔。</span><span class="sxs-lookup"><span data-stu-id="37791-184">Rebuilding the log, either through attach or ALTER DATABASE, is not supported for databases with a MEMORY_OPTIMIZED_DATA filegroup.</span></span>|  
|<span data-ttu-id="37791-185">連結的伺服器</span><span class="sxs-lookup"><span data-stu-id="37791-185">Linked Server</span></span>|<span data-ttu-id="37791-186">如需詳細資訊，請參閱 [連結的伺服器 &#40;Database Engine&#41;](../linked-servers/linked-servers-database-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="37791-186">For more information, see [Linked Servers &#40;Database Engine&#41;](../linked-servers/linked-servers-database-engine.md).</span></span>|  
|<span data-ttu-id="37791-187">大量記錄</span><span class="sxs-lookup"><span data-stu-id="37791-187">Bulk logging</span></span>|<span data-ttu-id="37791-188">無論資料庫使用何種復原模式，所有在持久性記憶體最佳化的資料表上的作業，一律會完整記錄。</span><span class="sxs-lookup"><span data-stu-id="37791-188">Regardless of the recovery model of the database, all operations on durable memory-optimized tables are always fully logged.</span></span>|  
|<span data-ttu-id="37791-189">最低限度記錄</span><span class="sxs-lookup"><span data-stu-id="37791-189">Minimal logging</span></span>|<span data-ttu-id="37791-190">記憶體最佳化資料表不支援最低限度記錄。</span><span class="sxs-lookup"><span data-stu-id="37791-190">Minimal logging is not supported for memory-optimized tables.</span></span> <span data-ttu-id="37791-191">如需最低限度記錄的詳細資訊，請參閱[交易記錄 &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md) 和[大量匯入採用最低限度記錄的必要條件](../import-export/prerequisites-for-minimal-logging-in-bulk-import.md)。</span><span class="sxs-lookup"><span data-stu-id="37791-191">For more information about minimal logging, see [The Transaction Log &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md) and [Prerequisites for Minimal Logging in Bulk Import](../import-export/prerequisites-for-minimal-logging-in-bulk-import.md).</span></span>|  
|<span data-ttu-id="37791-192">變更追蹤</span><span class="sxs-lookup"><span data-stu-id="37791-192">Change tracking</span></span>|<span data-ttu-id="37791-193">變更追蹤可在具有記憶體中 OLTP 物件的資料庫上啟用。</span><span class="sxs-lookup"><span data-stu-id="37791-193">Change tracking can be enabled on a database with In-Memory OLTP objects.</span></span> <span data-ttu-id="37791-194">不過，記憶體最佳化的資料表中的變更不會受到追蹤。</span><span class="sxs-lookup"><span data-stu-id="37791-194">However, changes in memory-optimized tables are not tracked.</span></span>|  
|<span data-ttu-id="37791-195">DDL 觸發程序</span><span class="sxs-lookup"><span data-stu-id="37791-195">DDL triggers</span></span>|<span data-ttu-id="37791-196">記憶體中 OLTP 資料表和原生編譯預存程序中不支援資料庫層級與伺服器層級的 DDL 觸發程序。</span><span class="sxs-lookup"><span data-stu-id="37791-196">Both database-level and server-level DDL triggers are not supported with In-Memory OLTP tables and natively compiled stored procedures.</span></span>|  
|<span data-ttu-id="37791-197">異動資料擷取 (CDC)</span><span class="sxs-lookup"><span data-stu-id="37791-197">Change Data Capture (CDC)</span></span>|<span data-ttu-id="37791-198">CDC 不應在具有記憶體中 OLTP 物件的資料庫上啟用，因為它會阻止特定作業，例如 DROP。</span><span class="sxs-lookup"><span data-stu-id="37791-198">CDC should not be enabled on a database that has In-Memory OLTP objects, as it prevents certain operations such as DROP.</span></span>|  
|<span data-ttu-id="37791-199">資料庫內含項目</span><span class="sxs-lookup"><span data-stu-id="37791-199">Database Containment</span></span>|<span data-ttu-id="37791-200">具有原生編譯的預存程序和記憶體最佳化資料表的資料庫不支援資料庫內含項目。</span><span class="sxs-lookup"><span data-stu-id="37791-200">Database containment is not supported in a database that has natively-compiled stored procedures and memory-optimized tables.</span></span> <span data-ttu-id="37791-201">如需相關資訊，請參閱 [Contained Databases](../databases/contained-databases.md)</span><span class="sxs-lookup"><span data-stu-id="37791-201">For more information, see [Contained Databases](../databases/contained-databases.md)</span></span>|  
|<span data-ttu-id="37791-202">內容連接</span><span class="sxs-lookup"><span data-stu-id="37791-202">Context Connections</span></span>|<span data-ttu-id="37791-203">不支援使用內容連接，從 CLR 預存程序內部存取記憶體最佳化的資料表。</span><span class="sxs-lookup"><span data-stu-id="37791-203">Accessing memory-optimized tables using the context connection from inside CLR stored procedures is not supported.</span></span>|  
|<span data-ttu-id="37791-204">資料指標</span><span class="sxs-lookup"><span data-stu-id="37791-204">Cursors</span></span>|<span data-ttu-id="37791-205">存取記憶體最佳化資料表之查詢上的索引鍵集與動態資料指標。</span><span class="sxs-lookup"><span data-stu-id="37791-205">Keyset and dynamic cursors on queries accessing memory-optimized tables.</span></span> <span data-ttu-id="37791-206">這些查詢會降級為靜態，變成唯讀。</span><span class="sxs-lookup"><span data-stu-id="37791-206">These queries are degraded to static becoming read-only.</span></span>|  
|<span data-ttu-id="37791-207">TABLESTAMP</span><span class="sxs-lookup"><span data-stu-id="37791-207">TABLESTAMP</span></span>|<span data-ttu-id="37791-208">不支援 TABLESTAMP。</span><span class="sxs-lookup"><span data-stu-id="37791-208">TABLESTAMP is not supported.</span></span> <span data-ttu-id="37791-209">如需詳細資訊，請參閱 [FROM &#40;Transact-SQL&#41;](/sql/t-sql/queries/from-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="37791-209">See [FROM &#40;Transact-SQL&#41;](/sql/t-sql/queries/from-transact-sql) for more information.</span></span>|  
|<span data-ttu-id="37791-210">AUTO_CLOSE</span><span class="sxs-lookup"><span data-stu-id="37791-210">AUTO_CLOSE</span></span>|<span data-ttu-id="37791-211">不支援 AUTO_CLOSE。</span><span class="sxs-lookup"><span data-stu-id="37791-211">AUTO_CLOSE is not supported.</span></span> <span data-ttu-id="37791-212">如需詳細資訊，請參閱 [Set the AUTO_CLOSE Database Option to OFF](../policy-based-management/set-the-auto-close-database-option-to-off.md)。</span><span class="sxs-lookup"><span data-stu-id="37791-212">For more information, see [Set the AUTO_CLOSE Database Option to OFF](../policy-based-management/set-the-auto-close-database-option-to-off.md).</span></span>|  
|<span data-ttu-id="37791-213">資料庫快照集</span><span class="sxs-lookup"><span data-stu-id="37791-213">Database Snapshots</span></span>|<span data-ttu-id="37791-214">不支援資料庫快照集。</span><span class="sxs-lookup"><span data-stu-id="37791-214">Database Snapshots are not supported.</span></span> <span data-ttu-id="37791-215">如需詳細資訊，請參閱[資料庫快照集 &#40;SQL Server&#41;](../databases/database-snapshots-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="37791-215">For more information, see [Database Snapshots &#40;SQL Server&#41;](../databases/database-snapshots-sql-server.md).</span></span>|  
|<span data-ttu-id="37791-216">交易式 DDL</span><span class="sxs-lookup"><span data-stu-id="37791-216">Transactional DDL</span></span>|<span data-ttu-id="37791-217">記憶體中 OLTP 不支援交易式 DDL。</span><span class="sxs-lookup"><span data-stu-id="37791-217">Transactional DDL is not supported in In-Memory OLTP.</span></span>|  
|<span data-ttu-id="37791-218">事件通知</span><span class="sxs-lookup"><span data-stu-id="37791-218">Event Notifications</span></span>|<span data-ttu-id="37791-219">不支援事件通知。</span><span class="sxs-lookup"><span data-stu-id="37791-219">Event notifications are not supported.</span></span> <span data-ttu-id="37791-220">如需詳細資訊，請參閱 [Event Notifications](../service-broker/event-notifications.md)。</span><span class="sxs-lookup"><span data-stu-id="37791-220">For more information, see [Event Notifications](../service-broker/event-notifications.md).</span></span>|  
|<span data-ttu-id="37791-221">Fiber 模式</span><span class="sxs-lookup"><span data-stu-id="37791-221">Fiber mode</span></span>|<span data-ttu-id="37791-222">記憶體中 OLTP 不支援 Fiber 模式。</span><span class="sxs-lookup"><span data-stu-id="37791-222">Fiber mode is not supported with In-Memory OLTP.</span></span>|  
|<span data-ttu-id="37791-223">原則式管理 (PBM)。</span><span class="sxs-lookup"><span data-stu-id="37791-223">Policy-based management (PBM).</span></span>|<span data-ttu-id="37791-224">不會阻止並只記錄 PBM 的模式。</span><span class="sxs-lookup"><span data-stu-id="37791-224">Prevent and log only modes of PBM are not supported.</span></span> <span data-ttu-id="37791-225">伺服器上存在這類原則時，可能會使記憶體中 OLTP DDL 無法成功執行。</span><span class="sxs-lookup"><span data-stu-id="37791-225">Existence of such policies on the server may prevent In-Memory OLTP DDL from executing successfully.</span></span> <span data-ttu-id="37791-226">支援視需要和依排程模式。</span><span class="sxs-lookup"><span data-stu-id="37791-226">On demand and on schedule modes are supported.</span></span>|  
|<span data-ttu-id="37791-227">DACFX 部署/擷取</span><span class="sxs-lookup"><span data-stu-id="37791-227">DACFX deploy/extract</span></span>|<span data-ttu-id="37791-228">記憶體中 OLTP 不支援 DAC Framework 部署/擷取。</span><span class="sxs-lookup"><span data-stu-id="37791-228">DAC Framework deploy/extract is not supported in In-Memory OLTP.</span></span>|  
  
 <span data-ttu-id="37791-229">有一些例外狀況，不支援跨資料庫的交易。</span><span class="sxs-lookup"><span data-stu-id="37791-229">With a few exceptions, cross-database transactions are not supported.</span></span> <span data-ttu-id="37791-230">下表描述支援的案例和對應的限制。</span><span class="sxs-lookup"><span data-stu-id="37791-230">The following table describes which cases are supported, and the corresponding restrictions.</span></span> <span data-ttu-id="37791-231">(另請參閱 [跨資料庫查詢](cross-database-queries.md))。</span><span class="sxs-lookup"><span data-stu-id="37791-231">(See also, [Cross-Database Queries](cross-database-queries.md).)</span></span>  
  
|<span data-ttu-id="37791-232">資料庫</span><span class="sxs-lookup"><span data-stu-id="37791-232">Databases</span></span>|<span data-ttu-id="37791-233">允許</span><span class="sxs-lookup"><span data-stu-id="37791-233">Allowed</span></span>|<span data-ttu-id="37791-234">描述</span><span class="sxs-lookup"><span data-stu-id="37791-234">Description</span></span>|  
|---------------|-------------|-----------------|  
|<span data-ttu-id="37791-235">使用者資料庫、模型和 msdb</span><span class="sxs-lookup"><span data-stu-id="37791-235">User databases, model, and msdb</span></span>|<span data-ttu-id="37791-236">否</span><span class="sxs-lookup"><span data-stu-id="37791-236">No</span></span>|<span data-ttu-id="37791-237">不支援跨資料庫的查詢和交易。</span><span class="sxs-lookup"><span data-stu-id="37791-237">Cross-database queries and transactions are not supported.</span></span><br /><br /> <span data-ttu-id="37791-238">存取記憶體最佳化的資料表或原生編譯的預存程序的查詢和交易都無法存取其他資料庫，但是系統資料庫 master (用於唯讀存取) 和 tempdb 例外。</span><span class="sxs-lookup"><span data-stu-id="37791-238">Queries and transactions that access memory-optimized tables or natively compiled stored procedures cannot access other databases, with the exception of the system databases master (read-only access) and tempdb.</span></span>|  
|<span data-ttu-id="37791-239">資源資料庫和 tempdb</span><span class="sxs-lookup"><span data-stu-id="37791-239">Resource database, and tempdb</span></span>|<span data-ttu-id="37791-240">是</span><span class="sxs-lookup"><span data-stu-id="37791-240">Yes</span></span>|<span data-ttu-id="37791-241">跨資料庫交易並沒有限制，除了單一使用者資料庫以外，只能使用資源資料庫和 tempdb。</span><span class="sxs-lookup"><span data-stu-id="37791-241">There are no restrictions on cross-database transactions that, besides a single user database, use only resource database and tempdb.</span></span>|  
|<span data-ttu-id="37791-242">master</span><span class="sxs-lookup"><span data-stu-id="37791-242">master</span></span>|<span data-ttu-id="37791-243">唯讀</span><span class="sxs-lookup"><span data-stu-id="37791-243">read-only</span></span>|<span data-ttu-id="37791-244">如果包含任何寫入 master 資料庫的作業，則接觸記憶體中 OLTP 和 master 資料庫的跨資料庫交易認可會失敗。</span><span class="sxs-lookup"><span data-stu-id="37791-244">Cross-database transactions that touch In-Memory OLTP and the master database fail to commit if it includes any writes to the master database.</span></span> <span data-ttu-id="37791-245">只允許從 master 讀取及使用一個使用者資料庫的跨資料庫交易。</span><span class="sxs-lookup"><span data-stu-id="37791-245">Cross-database transactions that only read from master and use only one user database are allowed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="37791-246">另請參閱</span><span class="sxs-lookup"><span data-stu-id="37791-246">See Also</span></span>  
 [<span data-ttu-id="37791-247">記憶體中 OLTP 的 SQL Server 支援</span><span class="sxs-lookup"><span data-stu-id="37791-247">SQL Server Support for In-Memory OLTP</span></span>](sql-server-support-for-in-memory-oltp.md)  
  
  