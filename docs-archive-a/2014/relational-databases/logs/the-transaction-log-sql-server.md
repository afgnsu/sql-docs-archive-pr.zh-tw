---
title: 交易記錄 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 01/04/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- transaction logs [SQL Server], about
- databases [SQL Server], transaction logs
- logs [SQL Server], transaction logs
ms.assetid: d7be5ac5-4c8e-4d0a-b114-939eb97dac4d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 025ef22e6dee1fcfaa1225a4709fa01b6c326b12
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594534"
---
# <a name="the-transaction-log-sql-server"></a><span data-ttu-id="e7154-102">交易記錄 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="e7154-102">The Transaction Log (SQL Server)</span></span>
  <span data-ttu-id="e7154-103">每個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫都有交易記錄來記錄所有交易及每項交易所作的資料庫修改。</span><span class="sxs-lookup"><span data-stu-id="e7154-103">Every [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database has a transaction log that records all transactions and the database modifications made by each transaction.</span></span> <span data-ttu-id="e7154-104">必須定期截斷交易記錄，以免被填滿。</span><span class="sxs-lookup"><span data-stu-id="e7154-104">The transaction log must be truncated on a regular basis to keep it from filling up.</span></span> <span data-ttu-id="e7154-105">但是，某些因素會影響記錄的截斷，所以監控記錄大小非常重要。</span><span class="sxs-lookup"><span data-stu-id="e7154-105">However, some factors can delay log truncation, so monitoring log size is important.</span></span> <span data-ttu-id="e7154-106">某些作業可使用最低限度記錄，以減少其對交易記錄大小的影響。</span><span class="sxs-lookup"><span data-stu-id="e7154-106">Some operations can be minimally logged to reduce their impact on transaction log size.</span></span>  
  
 <span data-ttu-id="e7154-107">交易記錄是資料庫的重要元件，而且如果系統故障，就可能需要交易記錄讓資料庫返回一致的狀態。</span><span class="sxs-lookup"><span data-stu-id="e7154-107">The transaction log is a critical component of the database and, if there is a system failure, the transaction log might be required to bring your database back to a consistent state.</span></span> <span data-ttu-id="e7154-108">永遠不要刪除或移動交易記錄，除非您完全了解執行這些動作的詳細情形。</span><span class="sxs-lookup"><span data-stu-id="e7154-108">The transaction log should never be deleted or moved unless you fully understand the ramifications of doing this.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e7154-109">檢查點會在資料庫復原期間建立開始套用交易記錄的已知恰當起點。</span><span class="sxs-lookup"><span data-stu-id="e7154-109">Known good points from which to begin applying transaction logs during database recovery are created by checkpoints.</span></span> <span data-ttu-id="e7154-110">如需詳細資訊，請參閱[資料庫檢查點 &#40;SQL Server&#41;](database-checkpoints-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="e7154-110">For more information, see [Database Checkpoints &#40;SQL Server&#41;](database-checkpoints-sql-server.md).</span></span>  
  
 <span data-ttu-id="e7154-111">**本主題內容：**</span><span class="sxs-lookup"><span data-stu-id="e7154-111">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="e7154-112">優點：交易記錄所支援的作業</span><span class="sxs-lookup"><span data-stu-id="e7154-112">Benefits: Operations Supported by the Transaction Log</span></span>](#Benefits)  
  
-   [<span data-ttu-id="e7154-113">交易記錄截斷</span><span class="sxs-lookup"><span data-stu-id="e7154-113">Transaction Log Truncation</span></span>](#Truncation)  
  
-   [<span data-ttu-id="e7154-114">可能會延遲記錄截斷的因素</span><span class="sxs-lookup"><span data-stu-id="e7154-114">Factors That Can Delay Log Truncation</span></span>](#FactorsThatDelayTruncation)  
  
-   [<span data-ttu-id="e7154-115">可以進行最低限度記錄的作業</span><span class="sxs-lookup"><span data-stu-id="e7154-115">Operations That Can Be Minimally Logged</span></span>](#MinimallyLogged)  
  
-   [<span data-ttu-id="e7154-116">相關工作</span><span class="sxs-lookup"><span data-stu-id="e7154-116">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="benefits-operations-supported-by-the-transaction-log"></a><a name="Benefits"></a><span data-ttu-id="e7154-117">優點：交易記錄所支援的作業</span><span class="sxs-lookup"><span data-stu-id="e7154-117">Benefits: Operations Supported by the Transaction Log</span></span>  
 <span data-ttu-id="e7154-118">交易記錄檔支援下列作業：</span><span class="sxs-lookup"><span data-stu-id="e7154-118">The transaction log supports the following operations:</span></span>  
  
-   <span data-ttu-id="e7154-119">復原個別的交易。</span><span class="sxs-lookup"><span data-stu-id="e7154-119">Recovery of individual transactions.</span></span>  
  
-   <span data-ttu-id="e7154-120">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 啟動時，復原所有未完成的交易。</span><span class="sxs-lookup"><span data-stu-id="e7154-120">Recovery of all incomplete transactions when [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is started.</span></span>  
  
-   <span data-ttu-id="e7154-121">將還原的資料庫、檔案、檔案群組或頁面向前復原到失敗點。</span><span class="sxs-lookup"><span data-stu-id="e7154-121">Rolling a restored database, file, filegroup, or page forward to the point of failure.</span></span>  
  
-   <span data-ttu-id="e7154-122">支援異動複寫。</span><span class="sxs-lookup"><span data-stu-id="e7154-122">Supporting transactional replication.</span></span>  
  
-   <span data-ttu-id="e7154-123">支援高可用性和災害復原解決方案： [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]、資料庫鏡像和記錄傳送。</span><span class="sxs-lookup"><span data-stu-id="e7154-123">Supporting high availability and disaster recovery solutions: [!INCLUDE[ssHADR](../../includes/sshadr-md.md)], database mirroring, and log shipping.</span></span>  
  
##  <a name="transaction-log-truncation"></a><a name="Truncation"></a> <span data-ttu-id="e7154-124">交易記錄截斷</span><span class="sxs-lookup"><span data-stu-id="e7154-124">Transaction Log Truncation</span></span>  
 <span data-ttu-id="e7154-125">記錄截斷會釋出記錄檔中的空間，以供交易記錄重複使用。</span><span class="sxs-lookup"><span data-stu-id="e7154-125">Log truncation frees space in the log file for reuse by the transaction log.</span></span> <span data-ttu-id="e7154-126">為了避免記錄被填滿，必須截斷記錄。</span><span class="sxs-lookup"><span data-stu-id="e7154-126">Log truncation is essential to keep the log from filling.</span></span> <span data-ttu-id="e7154-127">記錄截斷會從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫的邏輯交易記錄中，刪除非使用中的虛擬記錄檔，釋出邏輯記錄中的空間以供實體交易記錄重複使用。</span><span class="sxs-lookup"><span data-stu-id="e7154-127">Log truncation deletes inactive virtual log files from the logical transaction log of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, freeing space in the logical log for reuse by the Physical transaction log.</span></span> <span data-ttu-id="e7154-128">如果永遠都不截斷交易記錄，最終將會填滿配置給其實體記錄檔的所有磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="e7154-128">If a transaction log were never truncated, it would eventually fill all the disk space that is allocated to its physical log files.</span></span>  
  
 <span data-ttu-id="e7154-129">為了避免這個問題，除非記錄截斷因為某個原因而延遲，否則將在以下事件後自動進行截斷：</span><span class="sxs-lookup"><span data-stu-id="e7154-129">To avoid this problem, unless log truncation is being delayed for some reason, truncation occurs automatically after the following events:</span></span>  
  
-   <span data-ttu-id="e7154-130">在簡單復原模式下，發生在檢查點之後。</span><span class="sxs-lookup"><span data-stu-id="e7154-130">Under the simple recovery model, after a checkpoint.</span></span>  
  
-   <span data-ttu-id="e7154-131">在完整復原模式或大量記錄復原模式下，如果上一次備份之後已產生檢查點，則截斷會發生在記錄備份之後 (除非它是只複製的記錄備份)。</span><span class="sxs-lookup"><span data-stu-id="e7154-131">Under the full recovery model or bulk-logged recovery model, if a checkpoint has occurred since the previous backup, truncation occurs after a log backup (unless it is a copy-only log backup).</span></span>  
  
 <span data-ttu-id="e7154-132">如需詳細資訊，請參閱本主題稍後的[可能會延遲記錄截斷的因素](#FactorsThatDelayTruncation)。</span><span class="sxs-lookup"><span data-stu-id="e7154-132">For more information, see [Factors That Can Delay Log Truncation](#FactorsThatDelayTruncation), later in this topic.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e7154-133">記錄截斷並不會讓實體記錄檔變小。</span><span class="sxs-lookup"><span data-stu-id="e7154-133">Log truncation does not reduce the size of the physical log file.</span></span> <span data-ttu-id="e7154-134">若要減少實體記錄檔的實體大小，您必須壓縮記錄檔。</span><span class="sxs-lookup"><span data-stu-id="e7154-134">To reduce the physical size of a physical log file, you need to shrink the log file.</span></span> <span data-ttu-id="e7154-135">如需有關壓縮實體記錄檔大小的詳細資訊，請參閱＜ [管理交易記錄檔的大小](manage-the-size-of-the-transaction-log-file.md)＞。</span><span class="sxs-lookup"><span data-stu-id="e7154-135">For information about shrinking the size of the physical log file, see [Manage the Size of the Transaction Log File](manage-the-size-of-the-transaction-log-file.md).</span></span>  
  
##  <a name="factors-that-can-delay-log-truncation"></a><a name="FactorsThatDelayTruncation"></a><span data-ttu-id="e7154-136">可能會延遲記錄截斷的因素</span><span class="sxs-lookup"><span data-stu-id="e7154-136">Factors That Can Delay Log Truncation</span></span>  
 <span data-ttu-id="e7154-137">當記錄檔記錄有一段很長的時間維持在使用中狀態時，交易記錄截斷會延遲，而且可能會讓交易記錄填滿。</span><span class="sxs-lookup"><span data-stu-id="e7154-137">When log records remain active for a long time transaction log truncation is delayed, and potentially the transaction log can fill up.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e7154-138">如需如何對應寫滿交易記錄的相關資訊，請參閱 [Troubleshoot a Full Transaction Log &#40;SQL Server Error 9002&#41;](troubleshoot-a-full-transaction-log-sql-server-error-9002.md)。</span><span class="sxs-lookup"><span data-stu-id="e7154-138">For information about how to respond to a full transaction log, see [Troubleshoot a Full Transaction Log &#40;SQL Server Error 9002&#41;](troubleshoot-a-full-transaction-log-sql-server-error-9002.md).</span></span>  
  
 <span data-ttu-id="e7154-139">記錄截斷可能會因為各種因素而延遲。</span><span class="sxs-lookup"><span data-stu-id="e7154-139">Log truncation can be delayed by a variety of factors.</span></span> <span data-ttu-id="e7154-140">若要探索是否有任何原因導致記錄截斷無法進行，請查詢 **sys.databases** 目錄檢視的 **log_reuse_wait** 和 [log_reuse_wait_desc](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) 資料行。</span><span class="sxs-lookup"><span data-stu-id="e7154-140">You can discover what, if anything, is preventing log truncation by querying the **log_reuse_wait** and **log_reuse_wait_desc** columns of the [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) catalog view.</span></span> <span data-ttu-id="e7154-141">下表描述這些資料行的值。</span><span class="sxs-lookup"><span data-stu-id="e7154-141">The following table describes the values of these columns.</span></span>  
  
|<span data-ttu-id="e7154-142">log_reuse_wait 值</span><span class="sxs-lookup"><span data-stu-id="e7154-142">log_reuse_wait value</span></span>|<span data-ttu-id="e7154-143">log_reuse_wait_desc 值</span><span class="sxs-lookup"><span data-stu-id="e7154-143">log_reuse_wait_desc value</span></span>|<span data-ttu-id="e7154-144">描述</span><span class="sxs-lookup"><span data-stu-id="e7154-144">Description</span></span>|  
|----------------------------|----------------------------------|-----------------|  
|<span data-ttu-id="e7154-145">0</span><span class="sxs-lookup"><span data-stu-id="e7154-145">0</span></span>|<span data-ttu-id="e7154-146">NOTHING</span><span class="sxs-lookup"><span data-stu-id="e7154-146">NOTHING</span></span>|<span data-ttu-id="e7154-147">目前有一個或多個可重複使用的虛擬記錄檔。</span><span class="sxs-lookup"><span data-stu-id="e7154-147">Currently there are one or more reusable virtual log files.</span></span>|  
|<span data-ttu-id="e7154-148">1</span><span class="sxs-lookup"><span data-stu-id="e7154-148">1</span></span>|<span data-ttu-id="e7154-149">CHECKPOINT</span><span class="sxs-lookup"><span data-stu-id="e7154-149">CHECKPOINT</span></span>|<span data-ttu-id="e7154-150">自從上次記錄截斷後尚未出現任何檢查點，或是記錄標頭尚未移到虛擬記錄檔的範圍之外。</span><span class="sxs-lookup"><span data-stu-id="e7154-150">No checkpoint has occurred since the last log truncation, or the head of the log has not yet moved beyond a virtual log file.</span></span> <span data-ttu-id="e7154-151">(所有復原模式)</span><span class="sxs-lookup"><span data-stu-id="e7154-151">(All recovery models)</span></span><br /><br /> <span data-ttu-id="e7154-152">這是延遲記錄截斷的一般原因。</span><span class="sxs-lookup"><span data-stu-id="e7154-152">This is a routine reason for delaying log truncation.</span></span> <span data-ttu-id="e7154-153">如需詳細資訊，請參閱[資料庫檢查點 &#40;SQL Server&#41;](database-checkpoints-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="e7154-153">For more information, see [Database Checkpoints &#40;SQL Server&#41;](database-checkpoints-sql-server.md).</span></span>|  
|<span data-ttu-id="e7154-154">2</span><span class="sxs-lookup"><span data-stu-id="e7154-154">2</span></span>|<span data-ttu-id="e7154-155">LOG_BACKUP</span><span class="sxs-lookup"><span data-stu-id="e7154-155">LOG_BACKUP</span></span>|<span data-ttu-id="e7154-156">在截斷交易記錄前，需要進行記錄備份。</span><span class="sxs-lookup"><span data-stu-id="e7154-156">A log backup is required before the transaction log can be truncated.</span></span> <span data-ttu-id="e7154-157">(僅限完整或大量記錄復原模式)</span><span class="sxs-lookup"><span data-stu-id="e7154-157">(Full or bulk-logged recovery models only)</span></span><br /><br /> <span data-ttu-id="e7154-158">當下一個記錄備份完成後，某些記錄空間可能就可以重複使用。</span><span class="sxs-lookup"><span data-stu-id="e7154-158">When the next log backup is completed, some log space might become reusable.</span></span>|  
|<span data-ttu-id="e7154-159">3</span><span class="sxs-lookup"><span data-stu-id="e7154-159">3</span></span>|<span data-ttu-id="e7154-160">ACTIVE_BACKUP_OR_RESTORE</span><span class="sxs-lookup"><span data-stu-id="e7154-160">ACTIVE_BACKUP_OR_RESTORE</span></span>|<span data-ttu-id="e7154-161">正在進行資料備份或還原 (所有復原模式)。</span><span class="sxs-lookup"><span data-stu-id="e7154-161">A data backup or a restore is in progress (all recovery models).</span></span><br /><br /> <span data-ttu-id="e7154-162">如果資料備份阻礙截斷記錄，則取消備份作業可能有助於化解眼前的問題。</span><span class="sxs-lookup"><span data-stu-id="e7154-162">If a data backup is preventing log truncation, canceling the backup operation might help the immediate problem.</span></span>|  
|<span data-ttu-id="e7154-163">4</span><span class="sxs-lookup"><span data-stu-id="e7154-163">4</span></span>|<span data-ttu-id="e7154-164">ACTIVE_TRANSACTION</span><span class="sxs-lookup"><span data-stu-id="e7154-164">ACTIVE_TRANSACTION</span></span>|<span data-ttu-id="e7154-165">交易在使用中 (所有復原模式)。</span><span class="sxs-lookup"><span data-stu-id="e7154-165">A transaction is active (all recovery models).</span></span><br /><br /> <span data-ttu-id="e7154-166">長時間執行的交易可能存在於記錄備份的開頭。</span><span class="sxs-lookup"><span data-stu-id="e7154-166">A long-running transaction might exist at the start of the log backup.</span></span> <span data-ttu-id="e7154-167">在此情況下，釋出空間可能需要另一個記錄備份。</span><span class="sxs-lookup"><span data-stu-id="e7154-167">In this case, freeing the space might require another log backup.</span></span> <span data-ttu-id="e7154-168">請注意，長時間執行的交易會防止所有復原模式下的記錄截斷，包括簡單復原模式，交易記錄通常會在每個自動檢查點上截斷。</span><span class="sxs-lookup"><span data-stu-id="e7154-168">Note that a long-running transactions prevent log truncation under all recovery models, including the simple recovery model, under which the transaction log is generally truncated on each automatic checkpoint.</span></span><br /><br /> <span data-ttu-id="e7154-169">延遲交易。</span><span class="sxs-lookup"><span data-stu-id="e7154-169">A transaction is deferred.</span></span> <span data-ttu-id="e7154-170">*「延遲交易」* 實際上是回復遭到封鎖的使用中交易 (因為某些無法使用的資源所造成)。</span><span class="sxs-lookup"><span data-stu-id="e7154-170">A *deferred transaction* is effectively an active transaction whose rollback is blocked because of some unavailable resource.</span></span> <span data-ttu-id="e7154-171">如需有關延遲交易的原因以及如何將延遲交易移出延遲狀態的詳細資訊，請參閱[延遲交易 &#40;SQL Server&#41;](../backup-restore/deferred-transactions-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="e7154-171">For information about the causes of deferred transactions and how to move them out of the deferred state, see [Deferred Transactions &#40;SQL Server&#41;](../backup-restore/deferred-transactions-sql-server.md).</span></span> <br /><br /><span data-ttu-id="e7154-172">長時間執行的交易可能也會填滿 tempdb 的交易記錄。</span><span class="sxs-lookup"><span data-stu-id="e7154-172">Long-running transactions might also fill up tempdb's transaction log.</span></span> <span data-ttu-id="e7154-173">內部物件的使用者交易會隱含地使用 tempdb，例如進行排序的工作資料表、進行雜湊處理的工作檔案、資料指標工作資料表，以及資料列版本設定。</span><span class="sxs-lookup"><span data-stu-id="e7154-173">Tempdb is used implicitly by user transactions for internal objects such as work tables for sorting, work files for hashing, cursor work tables, and row versioning.</span></span> <span data-ttu-id="e7154-174">即使使用者交易僅包含讀取資料 (SELECT 查詢) ，還是可以在使用者交易下建立和使用內建物件。</span><span class="sxs-lookup"><span data-stu-id="e7154-174">Even if the user transaction includes only reading data (SELECT queries), internal objects may be created and used under user transactions.</span></span> <span data-ttu-id="e7154-175">因此，可能會填滿 tempdb 交易記錄。</span><span class="sxs-lookup"><span data-stu-id="e7154-175">Then the tempdb transaction log can be filled.</span></span>|  
|<span data-ttu-id="e7154-176">5</span><span class="sxs-lookup"><span data-stu-id="e7154-176">5</span></span>|<span data-ttu-id="e7154-177">DATABASE_MIRRORING</span><span class="sxs-lookup"><span data-stu-id="e7154-177">DATABASE_MIRRORING</span></span>|<span data-ttu-id="e7154-178">資料庫鏡像已暫停，或者在高效能模式下，鏡像資料庫已大幅落後主體資料庫。</span><span class="sxs-lookup"><span data-stu-id="e7154-178">Database mirroring is paused, or under high-performance mode, the mirror database is significantly behind the principal database.</span></span> <span data-ttu-id="e7154-179">(僅限完整復原模式)</span><span class="sxs-lookup"><span data-stu-id="e7154-179">(Full recovery model only)</span></span><br /><br /> <span data-ttu-id="e7154-180">如需詳細資訊，請參閱[資料庫鏡像 &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="e7154-180">For more information, see [Database Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md).</span></span>|  
|<span data-ttu-id="e7154-181">6</span><span class="sxs-lookup"><span data-stu-id="e7154-181">6</span></span>|<span data-ttu-id="e7154-182">複寫</span><span class="sxs-lookup"><span data-stu-id="e7154-182">REPLICATION</span></span>|<span data-ttu-id="e7154-183">進行異動複寫期間，與發行集相關的交易仍然未傳遞至散發資料庫。</span><span class="sxs-lookup"><span data-stu-id="e7154-183">During transactional replications, transactions relevant to the publications are still undelivered to the distribution database.</span></span> <span data-ttu-id="e7154-184">(僅限完整復原模式)</span><span class="sxs-lookup"><span data-stu-id="e7154-184">(Full recovery model only)</span></span><br /><br /> <span data-ttu-id="e7154-185">如需有關異動複寫的詳細資訊，請參閱＜ [SQL Server Replication](../../relational-databases/replication/sql-server-replication.md)＞。</span><span class="sxs-lookup"><span data-stu-id="e7154-185">For information about transactional replication, see [SQL Server Replication](../../relational-databases/replication/sql-server-replication.md).</span></span>|  
|<span data-ttu-id="e7154-186">7</span><span class="sxs-lookup"><span data-stu-id="e7154-186">7</span></span>|<span data-ttu-id="e7154-187">DATABASE_SNAPSHOT_CREATION</span><span class="sxs-lookup"><span data-stu-id="e7154-187">DATABASE_SNAPSHOT_CREATION</span></span>|<span data-ttu-id="e7154-188">正在建立資料庫快照集。</span><span class="sxs-lookup"><span data-stu-id="e7154-188">A database snapshot is being created.</span></span> <span data-ttu-id="e7154-189">(所有復原模式)</span><span class="sxs-lookup"><span data-stu-id="e7154-189">(All recovery models)</span></span><br /><br /> <span data-ttu-id="e7154-190">這是延遲記錄截斷的一般原因 (通常也是暫時的原因)。</span><span class="sxs-lookup"><span data-stu-id="e7154-190">This is a routine, and typically brief, cause of delayed log truncation.</span></span>|  
|<span data-ttu-id="e7154-191">8</span><span class="sxs-lookup"><span data-stu-id="e7154-191">8</span></span>|<span data-ttu-id="e7154-192">LOG_SCAN</span><span class="sxs-lookup"><span data-stu-id="e7154-192">LOG_SCAN</span></span>|<span data-ttu-id="e7154-193">正在進行記錄掃描。</span><span class="sxs-lookup"><span data-stu-id="e7154-193">A log scan is occurring.</span></span> <span data-ttu-id="e7154-194">(所有復原模式)</span><span class="sxs-lookup"><span data-stu-id="e7154-194">(All recovery models)</span></span><br /><br /> <span data-ttu-id="e7154-195">這是延遲記錄截斷的一般原因 (通常也是暫時的原因)。</span><span class="sxs-lookup"><span data-stu-id="e7154-195">This is a routine, and typically brief, cause of delayed log truncation.</span></span>|  
|<span data-ttu-id="e7154-196">9</span><span class="sxs-lookup"><span data-stu-id="e7154-196">9</span></span>|<span data-ttu-id="e7154-197">AVAILABILITY_REPLICA</span><span class="sxs-lookup"><span data-stu-id="e7154-197">AVAILABILITY_REPLICA</span></span>|<span data-ttu-id="e7154-198">可用性群組的次要複本正在將這個資料庫的交易記錄檔記錄套用到對應的次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="e7154-198">A secondary replica of an availability group is applying transaction log records of this database to a corresponding secondary database.</span></span> <span data-ttu-id="e7154-199">(完整復原模式)</span><span class="sxs-lookup"><span data-stu-id="e7154-199">(Full recovery model)</span></span><br /><br /> <span data-ttu-id="e7154-200">如需詳細資訊，請參閱[AlwaysOn 可用性群組 &#40;SQL Server&#41;的總覽](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="e7154-200">For more information, see [Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md).</span></span>|  
|<span data-ttu-id="e7154-201">10</span><span class="sxs-lookup"><span data-stu-id="e7154-201">10</span></span>|-|<span data-ttu-id="e7154-202">僅供內部使用</span><span class="sxs-lookup"><span data-stu-id="e7154-202">For internal use only</span></span>|  
|<span data-ttu-id="e7154-203">11</span><span class="sxs-lookup"><span data-stu-id="e7154-203">11</span></span>|-|<span data-ttu-id="e7154-204">僅供內部使用</span><span class="sxs-lookup"><span data-stu-id="e7154-204">For internal use only</span></span>|  
|<span data-ttu-id="e7154-205">12</span><span class="sxs-lookup"><span data-stu-id="e7154-205">12</span></span>|-|<span data-ttu-id="e7154-206">僅供內部使用</span><span class="sxs-lookup"><span data-stu-id="e7154-206">For internal use only</span></span>|  
|<span data-ttu-id="e7154-207">13</span><span class="sxs-lookup"><span data-stu-id="e7154-207">13</span></span>|<span data-ttu-id="e7154-208">OLDEST_PAGE</span><span class="sxs-lookup"><span data-stu-id="e7154-208">OLDEST_PAGE</span></span>|<span data-ttu-id="e7154-209">如果將資料庫設定為使用間接檢查點，資料庫中最舊的頁面可能會比檢查點 LSN 更舊。</span><span class="sxs-lookup"><span data-stu-id="e7154-209">If a database is configured to use indirect checkpoints, the oldest page on the database might be older than the checkpoint LSN.</span></span> <span data-ttu-id="e7154-210">在此情況下，最舊的頁面可能會延遲記錄截斷。</span><span class="sxs-lookup"><span data-stu-id="e7154-210">In this case, the oldest page can delay log truncation.</span></span> <span data-ttu-id="e7154-211">(所有復原模式)</span><span class="sxs-lookup"><span data-stu-id="e7154-211">(All recovery models)</span></span><br /><br /> <span data-ttu-id="e7154-212">如需間接檢查點的相關資訊，請參閱 [Database Checkpoints &#40;SQL Server&#41;](database-checkpoints-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="e7154-212">For information about indirect checkpoints, see [Database Checkpoints &#40;SQL Server&#41;](database-checkpoints-sql-server.md).</span></span>|  
|<span data-ttu-id="e7154-213">14</span><span class="sxs-lookup"><span data-stu-id="e7154-213">14</span></span>|<span data-ttu-id="e7154-214">OTHER_TRANSIENT</span><span class="sxs-lookup"><span data-stu-id="e7154-214">OTHER_TRANSIENT</span></span>|<span data-ttu-id="e7154-215">這個值目前尚未使用。</span><span class="sxs-lookup"><span data-stu-id="e7154-215">This value is currently not used.</span></span>|  
|<span data-ttu-id="e7154-216">16</span><span class="sxs-lookup"><span data-stu-id="e7154-216">16</span></span>|<span data-ttu-id="e7154-217">XTP_CHECKPOINT</span><span class="sxs-lookup"><span data-stu-id="e7154-217">XTP_CHECKPOINT</span></span>|<span data-ttu-id="e7154-218">當資料庫具有記憶體最佳化的檔案群組時，交易記錄檔可能會等到自動 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 檢查點觸發 (當記錄大小每成長 512 MB 時執行) 時，才會截斷記錄。</span><span class="sxs-lookup"><span data-stu-id="e7154-218">When a database has a memory-optimized filegroup, the transaction log may not truncate until automatic [!INCLUDE[hek_2](../../includes/hek-2-md.md)] checkpoint is triggered (which happens at every 512 MB of log growth).</span></span><br /><br /> <span data-ttu-id="e7154-219">注意：若要在 512 MB 大小之前截斷交易記錄，請針對有問題的資料庫手動引發檢查點命令。</span><span class="sxs-lookup"><span data-stu-id="e7154-219">Note: To truncate transaction log before 512 MB size, fire the Checkpoint command manually against the database in question.</span></span>|  
  
##  <a name="operations-that-can-be-minimally-logged"></a><a name="MinimallyLogged"></a><span data-ttu-id="e7154-220">可以進行最低限度記錄的作業</span><span class="sxs-lookup"><span data-stu-id="e7154-220">Operations That Can Be Minimally Logged</span></span>  
 <span data-ttu-id="e7154-221">「最低限度記錄」 包含僅記錄復原交易所需的資訊，不支援時間點復原。</span><span class="sxs-lookup"><span data-stu-id="e7154-221">*Minimal logging* involves logging only the information that is required to recover the transaction without supporting point-in-time recovery.</span></span> <span data-ttu-id="e7154-222">這個主題將識別在大量記錄復原模式下 (以及簡單復原模式下，但備份正在執行時除外) 會進行最低限度記錄的作業。</span><span class="sxs-lookup"><span data-stu-id="e7154-222">This topic identifies the operations that are minimally logged under the bulk-logged recovery model (as well as under the simple recovery model, except when a backup is running).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e7154-223">記憶體最佳化資料表不支援最低限度記錄。</span><span class="sxs-lookup"><span data-stu-id="e7154-223">Minimal logging is not supported for memory-optimized tables.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e7154-224">在完整復原模式下，將完整記錄所有大量作業。</span><span class="sxs-lookup"><span data-stu-id="e7154-224">Under the full recovery model, all bulk operations are fully logged.</span></span> <span data-ttu-id="e7154-225">不過，您可以暫時針對大量作業，將資料庫切換成大量記錄復原模式，藉以將大量作業集的記錄降至最低。</span><span class="sxs-lookup"><span data-stu-id="e7154-225">However, you can minimize logging for a set of bulk operations by switching the database to the bulk-logged recovery model temporarily for bulk operations.</span></span> <span data-ttu-id="e7154-226">最低限度記錄會比完整記錄更具效率，並降低大規模的大量作業在大量交易期間，填滿可用交易記錄空間的可能性。</span><span class="sxs-lookup"><span data-stu-id="e7154-226">Minimal logging is more efficient than full logging, and it reduces the possibility of a large-scale bulk operation filling the available transaction log space during a bulk transaction.</span></span> <span data-ttu-id="e7154-227">然而，如果資料庫在最低限度記錄作用時損毀或遺失，您就無法將資料庫復原至失敗點。</span><span class="sxs-lookup"><span data-stu-id="e7154-227">However, if the database is damaged or lost when minimal logging is in effect, you cannot recover the database to the point of failure.</span></span>  
  
 <span data-ttu-id="e7154-228">下列作業 (在完整復原模式下會完整記錄) 在簡單和大量記錄復原模式下會進行最低限度記錄：</span><span class="sxs-lookup"><span data-stu-id="e7154-228">The following operations, which are fully logged under the full recovery model, are minimally logged under the simple and bulk-logged recovery model:</span></span>  
  
-   <span data-ttu-id="e7154-229">大量匯入作業 ([bcp](../../tools/bcp-utility.md)、[BULK INSERT](/sql/t-sql/statements/bulk-insert-transact-sql) 及 [INSERT...SELECT](/sql/t-sql/statements/insert-transact-sql))。</span><span class="sxs-lookup"><span data-stu-id="e7154-229">Bulk import operations ([bcp](../../tools/bcp-utility.md), [BULK INSERT](/sql/t-sql/statements/bulk-insert-transact-sql), and [INSERT... SELECT](/sql/t-sql/statements/insert-transact-sql)).</span></span> <span data-ttu-id="e7154-230">如需何時大量匯入至資料表會採用最低限度記錄的詳細資訊，請參閱＜ [Prerequisites for Minimal Logging in Bulk Import](../import-export/prerequisites-for-minimal-logging-in-bulk-import.md)＞。</span><span class="sxs-lookup"><span data-stu-id="e7154-230">For more information about when bulk import into a table is minimally logged, see [Prerequisites for Minimal Logging in Bulk Import](../import-export/prerequisites-for-minimal-logging-in-bulk-import.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e7154-231">啟用異動複寫時，即使在大量記錄復原模式下也會完整記錄 BULK INSERT 作業。</span><span class="sxs-lookup"><span data-stu-id="e7154-231">When transactional replication is enabled, BULK INSERT operations are fully logged even under the Bulk Logged recovery model.</span></span>  
  
-   <span data-ttu-id="e7154-232">SELECT [INTO](/sql/t-sql/queries/select-into-clause-transact-sql)作業。</span><span class="sxs-lookup"><span data-stu-id="e7154-232">SELECT [INTO](/sql/t-sql/queries/select-into-clause-transact-sql) operations.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e7154-233">啟用異動複寫時，即使在大量記錄復原模式下也會完整記錄 SELECT INTO 作業。</span><span class="sxs-lookup"><span data-stu-id="e7154-233">When transactional replication is enabled, SELECT INTO operations are fully logged even under the Bulk Logged recovery model.</span></span>  
  
-   <span data-ttu-id="e7154-234">插入或附加新資料時，在 [UPDATE](/sql/t-sql/queries/update-transact-sql) 陳述式中使用 .WRITE 子句，對大數值資料類型執行的部分更新。</span><span class="sxs-lookup"><span data-stu-id="e7154-234">Partial updates to large value data types, using the .WRITE clause in the [UPDATE](/sql/t-sql/queries/update-transact-sql) statement when inserting or appending new data.</span></span> <span data-ttu-id="e7154-235">請注意，更新現有值時不使用最低限度記錄。</span><span class="sxs-lookup"><span data-stu-id="e7154-235">Note that minimal logging is not used when existing values are updated.</span></span> <span data-ttu-id="e7154-236">如需有關大數值資料類型的詳細資訊，請參閱[資料類型 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="e7154-236">For more information about large value data types, see [Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).</span></span>  
  
-   <span data-ttu-id="e7154-237">將新[UPDATETEXT](/sql/t-sql/queries/updatetext-transact-sql)資料插入或附加至[WRITETEXT](/sql/t-sql/queries/writetext-transact-sql) `text` 、 `ntext` 和 `image` 資料類型資料行時，WRITETEXT 和 UPDATETEXT 語句。</span><span class="sxs-lookup"><span data-stu-id="e7154-237">[WRITETEXT](/sql/t-sql/queries/writetext-transact-sql) and [UPDATETEXT](/sql/t-sql/queries/updatetext-transact-sql) statements when inserting or appending new data into the `text`, `ntext`, and `image` data type columns.</span></span> <span data-ttu-id="e7154-238">請注意，更新現有值時不使用最低限度記錄。</span><span class="sxs-lookup"><span data-stu-id="e7154-238">Note that minimal logging is not used when existing values are updated.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e7154-239">WRITETEXT 與 UPDATETEXT 陳述式已被取代，所以您應該避免在新的應用程式中使用它們。</span><span class="sxs-lookup"><span data-stu-id="e7154-239">The WRITETEXT and UPDATETEXT statements are deprecated, so you should avoid using them in new applications.</span></span>  
  
-   <span data-ttu-id="e7154-240">如果資料庫設定為簡單或大量記錄復原模式，則不管作業是離線執行或線上執行，某些索引 DDL 作業都是以最低限度的方式記錄。</span><span class="sxs-lookup"><span data-stu-id="e7154-240">If the database is set to the simple or bulk-logged recovery model, some index DDL operations are minimally logged whether the operation is executed offline or online.</span></span> <span data-ttu-id="e7154-241">以最低限度方式記錄的索引作業如下：</span><span class="sxs-lookup"><span data-stu-id="e7154-241">The minimally logged index operations are as follows:</span></span>  
  
    -   <span data-ttu-id="e7154-242">[CREATE INDEX](/sql/t-sql/statements/create-index-transact-sql) 作業 (包括索引檢視表)。</span><span class="sxs-lookup"><span data-stu-id="e7154-242">[CREATE INDEX](/sql/t-sql/statements/create-index-transact-sql) operations (including indexed views).</span></span>  
  
    -   <span data-ttu-id="e7154-243">[ALTER INDEX](/sql/t-sql/statements/alter-index-transact-sql) REBUILD 或 DBCC DBREINDEX 作業。</span><span class="sxs-lookup"><span data-stu-id="e7154-243">[ALTER INDEX](/sql/t-sql/statements/alter-index-transact-sql) REBUILD or DBCC DBREINDEX operations.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="e7154-244">DBCC DBREINDEX 陳述式已被取代，所以您應該避免在新的應用程式中使用它。</span><span class="sxs-lookup"><span data-stu-id="e7154-244">The DBCC DBREINDEX statement is deprecated so you should avoid using it in new applications.</span></span>  
  
    -   <span data-ttu-id="e7154-245">DROP INDEX 新堆積重建 (如果適用)。</span><span class="sxs-lookup"><span data-stu-id="e7154-245">DROP INDEX new heap rebuild (if applicable).</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="e7154-246">[DROP INDEX](/sql/t-sql/statements/drop-index-transact-sql) 作業期間的索引頁取消配置永遠都是完整記錄。</span><span class="sxs-lookup"><span data-stu-id="e7154-246">Index page deallocation during a [DROP INDEX](/sql/t-sql/statements/drop-index-transact-sql) operation is always fully logged.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="e7154-247">相關工作</span><span class="sxs-lookup"><span data-stu-id="e7154-247">Related Tasks</span></span>  
 `Managing the transaction log`  
  
-   [<span data-ttu-id="e7154-248">管理交易記錄檔的大小</span><span class="sxs-lookup"><span data-stu-id="e7154-248">Manage the Size of the Transaction Log File</span></span>](manage-the-size-of-the-transaction-log-file.md)  
  
-   [<span data-ttu-id="e7154-249">寫滿交易記錄疑難排解 &#40;SQL Server 錯誤 9002&#41;</span><span class="sxs-lookup"><span data-stu-id="e7154-249">Troubleshoot a Full Transaction Log &#40;SQL Server Error 9002&#41;</span></span>](troubleshoot-a-full-transaction-log-sql-server-error-9002.md)  
  
 <span data-ttu-id="e7154-250">**備份交易記錄 (完整復原模式)**</span><span class="sxs-lookup"><span data-stu-id="e7154-250">**Backing Up the Transaction Log (Full Recovery Model)**</span></span>  
  
-   [<span data-ttu-id="e7154-251">備份交易記錄 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e7154-251">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](../backup-restore/back-up-a-transaction-log-sql-server.md)  
  
 <span data-ttu-id="e7154-252">**還原交易記錄 (完整復原模式)**</span><span class="sxs-lookup"><span data-stu-id="e7154-252">**Restoring the Transaction Log (Full Recovery Model)**</span></span>  
  
-  [<span data-ttu-id="e7154-253">還原交易記錄備份</span><span class="sxs-lookup"><span data-stu-id="e7154-253">Restore a Transaction Log Backup</span></span>](../backup-restore/restore-a-transaction-log-backup-sql-server.md)   
  
## <a name="see-also"></a><span data-ttu-id="e7154-254">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7154-254">See Also</span></span>  
 <span data-ttu-id="e7154-255">[控制交易持久性](control-transaction-durability.md) </span><span class="sxs-lookup"><span data-stu-id="e7154-255">[Control Transaction Durability](control-transaction-durability.md) </span></span>  
 <span data-ttu-id="e7154-256">[大量匯入採用最低限度記錄的必要條件](../import-export/prerequisites-for-minimal-logging-in-bulk-import.md) </span><span class="sxs-lookup"><span data-stu-id="e7154-256">[Prerequisites for Minimal Logging in Bulk Import](../import-export/prerequisites-for-minimal-logging-in-bulk-import.md) </span></span>  
 <span data-ttu-id="e7154-257">[SQL Server 資料庫的備份與還原](../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="e7154-257">[Back Up and Restore of SQL Server Databases](../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span></span>  
 <span data-ttu-id="e7154-258">[資料庫檢查點 &#40;SQL Server&#41;](database-checkpoints-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e7154-258">[Database Checkpoints &#40;SQL Server&#41;](database-checkpoints-sql-server.md) </span></span>  
 <span data-ttu-id="e7154-259">[檢視或變更資料庫的屬性](../databases/view-or-change-the-properties-of-a-database.md) </span><span class="sxs-lookup"><span data-stu-id="e7154-259">[View or Change the Properties of a Database](../databases/view-or-change-the-properties-of-a-database.md) </span></span>  
 [<span data-ttu-id="e7154-260">復原模式 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e7154-260">Recovery Models &#40;SQL Server&#41;</span></span>](../backup-restore/recovery-models-sql-server.md)  
  
  