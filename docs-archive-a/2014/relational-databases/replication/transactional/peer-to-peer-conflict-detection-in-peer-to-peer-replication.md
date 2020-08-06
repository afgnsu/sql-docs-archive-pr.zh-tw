---
title: 點對點複寫中的衝突偵測 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- transactional replication, peer-to-peer replication
- peer-to-peer transactional replication, conflict detection
ms.assetid: 754a1070-59bc-438d-998b-97fdd77d45ca
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 301a751bf5b5959ab1fc434ac2a583a6b0378fdd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596633"
---
# <a name="conflict-detection-in-peer-to-peer-replication"></a><span data-ttu-id="4dc05-102">點對點複寫中的衝突偵測</span><span class="sxs-lookup"><span data-stu-id="4dc05-102">Conflict Detection in Peer-to-Peer Replication</span></span>
  <span data-ttu-id="4dc05-103">點對點異動複寫可讓您在拓撲中的任何節點上插入、更新或刪除資料，以及讓資料變更傳播至其他節點。</span><span class="sxs-lookup"><span data-stu-id="4dc05-103">Peer-to-peer transactional replication lets you insert, update, or delete data at any node in a topology and have data changes propagated to the other nodes.</span></span> <span data-ttu-id="4dc05-104">由於您可以在任何節點上變更資料，因此不同節點的資料變更可能會彼此衝突。</span><span class="sxs-lookup"><span data-stu-id="4dc05-104">Because you can change data at any node, data changes at different nodes could conflict with each other.</span></span> <span data-ttu-id="4dc05-105">如果在一個以上的節點上修改資料列，它可能會在此資料列傳播到其他節點時，造成衝突或甚至是遺失更新。</span><span class="sxs-lookup"><span data-stu-id="4dc05-105">If a row is modified at more than one node, it can cause a conflict or even a lost update when the row is propagated to other nodes.</span></span>  
  
 <span data-ttu-id="4dc05-106">[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 及更新版本中的點對點複寫提供了在點對點拓撲之間啟用衝突偵測的選項。</span><span class="sxs-lookup"><span data-stu-id="4dc05-106">Peer-to-peer replication in [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] and later versions provides the option to enable conflict detection across a peer-to-peer topology.</span></span> <span data-ttu-id="4dc05-107">這個選項可避免因為未偵測到的衝突所導致的問題，包括不一致的應用程式行為和遺失更新。</span><span class="sxs-lookup"><span data-stu-id="4dc05-107">This option would help prevent the issues that are caused by undetected conflicts, including inconsistent application behavior and lost updates.</span></span> <span data-ttu-id="4dc05-108">啟用這個選項時，預設會將衝突的變更視為造成散發代理程式失敗的嚴重錯誤。</span><span class="sxs-lookup"><span data-stu-id="4dc05-108">With this option enabled, by default a conflicting change is treated as a critical error that causes the failure of the Distribution Agent.</span></span> <span data-ttu-id="4dc05-109">在發生衝突時，此拓撲會維持不一致的狀態，直到解決衝突並讓拓撲之間的資料變成一致為止。</span><span class="sxs-lookup"><span data-stu-id="4dc05-109">In the event of a conflict, the topology remains in an inconsistent state until the conflict is resolved and the data is made consistent across the topology.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4dc05-110">若要避免潛在的資料不一致問題，請務必要避免發生點對點拓撲中的衝突，即使是啟用了衝突偵測也一樣。</span><span class="sxs-lookup"><span data-stu-id="4dc05-110">To avoid potential data inconsistency, make sure that you avoid conflicts in a peer-to-peer topology, even with conflict detection enabled.</span></span> <span data-ttu-id="4dc05-111">若要確定只在一個節點上執行特定資料列的寫入作業，存取和變更資料的應用程式必須分割插入、更新和刪除作業。</span><span class="sxs-lookup"><span data-stu-id="4dc05-111">To ensure that write operations for a particular row are performed at only one node, applications that access and change data must partition insert, update, and delete operations.</span></span> <span data-ttu-id="4dc05-112">這樣的分割可確保，從一個節點對給定資料列的修改會在其他節點修改該資料列之前，與拓撲中的所有其他節點同步處理。</span><span class="sxs-lookup"><span data-stu-id="4dc05-112">This partitioning ensures that modifications to a given row that is originating at one node are synchronized with all other nodes in the topology before the row is modified by a different node.</span></span> <span data-ttu-id="4dc05-113">如果應用程式需要複雜的衝突偵測與解決功能，請使用合併式複寫。</span><span class="sxs-lookup"><span data-stu-id="4dc05-113">If an application requires sophisticated conflict detection and resolution capabilities, use merge replication.</span></span> <span data-ttu-id="4dc05-114">如需詳細資訊，請參閱[合併式複寫](../merge/merge-replication.md)和[偵測及解決合併式複寫衝突](../merge/advanced-merge-replication-conflict-detection-and-resolution.md)。</span><span class="sxs-lookup"><span data-stu-id="4dc05-114">For more information, see [Merge Replication](../merge/merge-replication.md) and [Detect and Resolve Merge Replication Conflicts](../merge/advanced-merge-replication-conflict-detection-and-resolution.md).</span></span>  
  
## <a name="understanding-conflicts-and-conflict-detection"></a><span data-ttu-id="4dc05-115">了解衝突和衝突偵測</span><span class="sxs-lookup"><span data-stu-id="4dc05-115">Understanding Conflicts and Conflict Detection</span></span>  
 <span data-ttu-id="4dc05-116">在單一資料庫中，由不同應用程式對相同資料列所做的變更不會導致衝突發生。</span><span class="sxs-lookup"><span data-stu-id="4dc05-116">In a single database, changes that are made to the same row by different applications do not cause a conflict.</span></span> <span data-ttu-id="4dc05-117">這是因為交易是序列化的，而且系統會使用鎖定來處理並行的變更。</span><span class="sxs-lookup"><span data-stu-id="4dc05-117">This is because transactions are serialized, and locks are used to handle concurrent changes.</span></span> <span data-ttu-id="4dc05-118">在非同步分散式系統 (例如點對點複寫) 中，交易會在每個節點上獨立運作，而且沒有任何機制可序列化多個節點之間的交易。</span><span class="sxs-lookup"><span data-stu-id="4dc05-118">In an asynchronous distributed system such as peer-to-peer replication, transactions act independently on each node; and there is no mechanism to serialize transactions across multiple nodes.</span></span> <span data-ttu-id="4dc05-119">雖然您可以使用兩階段交易認可之類的通訊協定，但是這樣做會大幅影響效能。</span><span class="sxs-lookup"><span data-stu-id="4dc05-119">A protocol like two-phase commit could be used, but this affects performance significantly.</span></span>  
  
 <span data-ttu-id="4dc05-120">在點對點複寫等系統中，當系統在個別對等中認可變更時，無法偵測衝突。</span><span class="sxs-lookup"><span data-stu-id="4dc05-120">In systems such as peer-to-peer replication, conflicts are not detected when changes are committed at individual peers.</span></span> <span data-ttu-id="4dc05-121">不過，當這些變更複寫和套用至其他對等時，就會偵測衝突。</span><span class="sxs-lookup"><span data-stu-id="4dc05-121">Instead, they are detected when those changes are replicated and applied at other peers.</span></span> <span data-ttu-id="4dc05-122">在點對點複寫中，將變更套用至每個節點的預存程序會根據每個已發行資料表中的隱藏資料行來偵測衝突。</span><span class="sxs-lookup"><span data-stu-id="4dc05-122">In peer-to-peer replication, conflicts are detected by the stored procedures that apply changes to each node, based on a hidden column in each published table.</span></span> <span data-ttu-id="4dc05-123">這個隱藏資料行會儲存結合了您針對每個節點指定的 *「訂閱者識別碼」* (Originator ID) 與資料列版本的識別碼。</span><span class="sxs-lookup"><span data-stu-id="4dc05-123">This hidden column stores an ID that combines an *originator ID* that you specify for each node and the version of the row.</span></span> <span data-ttu-id="4dc05-124">在同步處理期間，散發代理程式會針對每份資料表執行程序。</span><span class="sxs-lookup"><span data-stu-id="4dc05-124">During synchronization, the Distribution Agent executes procedures for each table.</span></span> <span data-ttu-id="4dc05-125">這些程序會從其他對等套用插入、更新和刪除作業。</span><span class="sxs-lookup"><span data-stu-id="4dc05-125">These procedures apply insert, update, and delete operations from other peers.</span></span> <span data-ttu-id="4dc05-126">如果其中一項程序在讀取隱藏資料行的值時偵測到衝突，它就會引發嚴重性層級為 16 的錯誤 22815：</span><span class="sxs-lookup"><span data-stu-id="4dc05-126">If one of the procedures detects a conflict when it reads the hidden column value, it raises error 22815 that has a severity level of 16:</span></span>  
  
 `A conflict of type '%s' was detected at peer %d between peer %d (incoming), transaction id %s  and peer %d (on disk), transaction id %s`  
  
 <span data-ttu-id="4dc05-127">根據預設，這項錯誤會導致散發代理程式停止將變更套用至該節點。</span><span class="sxs-lookup"><span data-stu-id="4dc05-127">By default, this error causes the Distribution Agent to stop applying changes to that node.</span></span> <span data-ttu-id="4dc05-128">如需有關如何處理偵測之衝突的詳細資訊，請參閱本主題後面的「處理衝突」。</span><span class="sxs-lookup"><span data-stu-id="4dc05-128">For information about how to handle the conflicts that are detected, see "Handling Conflicts" later in this topic.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4dc05-129">隱藏資料行只能由透過「專用管理員連接」(DAC) 登入的使用者存取。</span><span class="sxs-lookup"><span data-stu-id="4dc05-129">The hidden column can be accessed only by a user that is logged in through the Dedicated Administrator Connection (DAC).</span></span> <span data-ttu-id="4dc05-130">如需 DAC 的資訊，請參閱[資料庫管理員的診斷連線](../../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md)。</span><span class="sxs-lookup"><span data-stu-id="4dc05-130">For information about DAC, see [Diagnostic Connection for Database Administrators](../../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md).</span></span>  
  
 <span data-ttu-id="4dc05-131">點對點複寫會偵測下列衝突類型：</span><span class="sxs-lookup"><span data-stu-id="4dc05-131">Peer-to-peer replication detects the following types of conflicts:</span></span>  
  
-   <span data-ttu-id="4dc05-132">插入對插入</span><span class="sxs-lookup"><span data-stu-id="4dc05-132">Insert-insert</span></span>  
  
     <span data-ttu-id="4dc05-133">參與點對點複寫之每份資料表中的所有資料列都會使用主索引鍵值進行唯一識別。</span><span class="sxs-lookup"><span data-stu-id="4dc05-133">All rows in each table participating in peer-to-peer replication are uniquely identified by using primary key values.</span></span> <span data-ttu-id="4dc05-134">在多個節點上插入具有相同索引鍵值的資料列時，就會發生插入對插入的衝突。</span><span class="sxs-lookup"><span data-stu-id="4dc05-134">An insert-insert conflict occurs when a row with the same key value was inserted at more than one node.</span></span>  
  
-   <span data-ttu-id="4dc05-135">更新對更新</span><span class="sxs-lookup"><span data-stu-id="4dc05-135">Update-update</span></span>  
  
     <span data-ttu-id="4dc05-136">在多個節點上更新相同的資料列時發生。</span><span class="sxs-lookup"><span data-stu-id="4dc05-136">Occurs when the same row was updated at more than one node.</span></span>  
  
-   <span data-ttu-id="4dc05-137">插入對更新</span><span class="sxs-lookup"><span data-stu-id="4dc05-137">Insert-update</span></span>  
  
     <span data-ttu-id="4dc05-138">在某個節點上插入一個資料列，但是在另一個節點上刪除並重新插入相同的資料列時發生。</span><span class="sxs-lookup"><span data-stu-id="4dc05-138">Occurs if a row was updated at one node, but the same row was deleted and then reinserted at another node.</span></span>  
  
-   <span data-ttu-id="4dc05-139">插入對刪除</span><span class="sxs-lookup"><span data-stu-id="4dc05-139">Insert-delete</span></span>  
  
     <span data-ttu-id="4dc05-140">在某個節點上刪除一個資料列，但是在另一個節點上刪除並重新插入相同的資料列時發生。</span><span class="sxs-lookup"><span data-stu-id="4dc05-140">Occurs if a row was deleted at one node, but the same row was deleted and then reinserted at another node.</span></span>  
  
-   <span data-ttu-id="4dc05-141">更新對刪除</span><span class="sxs-lookup"><span data-stu-id="4dc05-141">Update-delete</span></span>  
  
     <span data-ttu-id="4dc05-142">在某個節點上插入一個資料列，但是在另一個節點上刪除相同的資料列時發生。</span><span class="sxs-lookup"><span data-stu-id="4dc05-142">Occurs if a row was updated at one node, but the same row was deleted at another node.</span></span>  
  
-   <span data-ttu-id="4dc05-143">刪除對刪除</span><span class="sxs-lookup"><span data-stu-id="4dc05-143">Delete-delete</span></span>  
  
     <span data-ttu-id="4dc05-144">在多個節點上刪除資料列時發生。</span><span class="sxs-lookup"><span data-stu-id="4dc05-144">Occurs when a row was deleted at more than one node.</span></span>  
  
## <a name="enabling-conflict-detection"></a><span data-ttu-id="4dc05-145">啟用衝突偵測</span><span class="sxs-lookup"><span data-stu-id="4dc05-145">Enabling Conflict Detection</span></span>  
 <span data-ttu-id="4dc05-146">若要使用衝突偵測，所有節點都必須執行 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 或更新版本，而且您必須針對所有節點啟用偵測。</span><span class="sxs-lookup"><span data-stu-id="4dc05-146">To use conflict detection, all nodes must be running [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] or a later version; and detection must be enabled for all nodes.</span></span> <span data-ttu-id="4dc05-147">在 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 和更新版本中， [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]預設會啟用衝突偵測。</span><span class="sxs-lookup"><span data-stu-id="4dc05-147">In [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] and later versions, by default, conflict detection is enabled in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="4dc05-148">我們建議您啟用偵測，即使是預期不會發生任何衝突的狀況也一樣。</span><span class="sxs-lookup"><span data-stu-id="4dc05-148">We recommend that you have detection enabled, even in scenarios in which you do not expect any conflicts.</span></span> <span data-ttu-id="4dc05-149">您可以使用 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] 或 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 預存程序來啟用和停用衝突偵測：</span><span class="sxs-lookup"><span data-stu-id="4dc05-149">Conflict detection can be enabled and disabled by using [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)] stored procedures:</span></span>  
  
-   <span data-ttu-id="4dc05-150">您可以使用 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] [發行集屬性] **對話方塊的** [訂閱選項] **頁面或「設定點對點拓撲精靈」的** [設定拓撲] **頁面，啟用和停用** 中的偵測。</span><span class="sxs-lookup"><span data-stu-id="4dc05-150">You can enable and disable detection in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] either by using the **Subscription Options** page of the **Publication Properties** dialog box or the **Configure Topology** page of the Configure Peer-to-Peer Topology Wizard.</span></span>  
  
     <span data-ttu-id="4dc05-151">如果您使用 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]來設定衝突偵測，散發代理程式就會設定為在偵測到衝突時停止套用變更。</span><span class="sxs-lookup"><span data-stu-id="4dc05-151">If you configure conflict detection by using [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], the Distribution Agent is configured to stop applying changes when a conflict is detected.</span></span>  
  
-   <span data-ttu-id="4dc05-152">您也可以使用下列預存程序來啟用和停用偵測： [sp_addpublication](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql) 或 [sp_configure_peerconflictdetection](/sql/relational-databases/system-stored-procedures/sp-configure-peerconflictdetection-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="4dc05-152">You can also enable and disable detection by using the following stored procedures: [sp_addpublication](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql) or [sp_configure_peerconflictdetection](/sql/relational-databases/system-stored-procedures/sp-configure-peerconflictdetection-transact-sql).</span></span>  
  
     <span data-ttu-id="4dc05-153">如果您使用預存程序來設定衝突偵測，就可以指定散發代理程式是否應該在偵測到衝突時停止套用變更。</span><span class="sxs-lookup"><span data-stu-id="4dc05-153">If you configure conflict detection by using stored procedures, you can specify whether the Distribution Agent should stop applying changes when a conflict is detected.</span></span> <span data-ttu-id="4dc05-154">代理程式的預設值為停止。</span><span class="sxs-lookup"><span data-stu-id="4dc05-154">The default is for the agent to stop.</span></span> <span data-ttu-id="4dc05-155">我們建議您使用預設設定。</span><span class="sxs-lookup"><span data-stu-id="4dc05-155">We recommend that you use the default setting.</span></span>  
  
## <a name="handling-conflicts"></a><span data-ttu-id="4dc05-156">處理衝突</span><span class="sxs-lookup"><span data-stu-id="4dc05-156">Handling Conflicts</span></span>  
 <span data-ttu-id="4dc05-157">在點對點複寫中發生衝突時，系統就會引發點對點衝突偵測警示。</span><span class="sxs-lookup"><span data-stu-id="4dc05-157">When a conflict occurs in peer-to-peer replication, the Peer-to-peer conflict detection alert is raised.</span></span> <span data-ttu-id="4dc05-158">我們建議您設定這個警示，以便在發生衝突時收到通知。</span><span class="sxs-lookup"><span data-stu-id="4dc05-158">We recommend that you configure this alert so that you are notified when a conflict occurs.</span></span> <span data-ttu-id="4dc05-159">如需警示的詳細資訊，請參閱[使用複寫代理程式事件的警示](../agents/use-alerts-for-replication-agent-events.md)。</span><span class="sxs-lookup"><span data-stu-id="4dc05-159">For more information about alerts, see [Use Alerts for Replication Agent Events](../agents/use-alerts-for-replication-agent-events.md).</span></span>  
  
 <span data-ttu-id="4dc05-160">在散發代理程式停止並引發警示之後，請使用下列其中一種方法來處理發生的衝突：</span><span class="sxs-lookup"><span data-stu-id="4dc05-160">After the Distribution Agent stops and the alert is raised, use one of the following approaches to handle the conflicts that occurred:</span></span>  
  
-   <span data-ttu-id="4dc05-161">根據包含必要資料的節點備份，重新初始化偵測到衝突的節點 (建議使用的方法)。</span><span class="sxs-lookup"><span data-stu-id="4dc05-161">Reinitialize the node where the conflict was detected from the backup of a node that contains the required data (the recommended approach).</span></span> <span data-ttu-id="4dc05-162">這種方法可確保資料處於一致的狀態。</span><span class="sxs-lookup"><span data-stu-id="4dc05-162">This method ensures that data is in a consistent state.</span></span>  
  
-   <span data-ttu-id="4dc05-163">透過讓散發代理程式繼續套用變更，嘗試再次同步處理節點：</span><span class="sxs-lookup"><span data-stu-id="4dc05-163">Try to synchronize the node again by enabling the Distribution Agent to continue to apply changes:</span></span>  
  
    1.  <span data-ttu-id="4dc05-164">執行[sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)：指定參數的 ' p2p_continue_onconflict ' @property 和 `true` 參數的 @value 。</span><span class="sxs-lookup"><span data-stu-id="4dc05-164">Execute [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql): specify 'p2p_continue_onconflict' for the @property parameter and `true` for the @value parameter.</span></span>  
  
    2.  <span data-ttu-id="4dc05-165">重新啟動散發代理程式。</span><span class="sxs-lookup"><span data-stu-id="4dc05-165">Restart the Distribution Agent.</span></span>  
  
    3.  <span data-ttu-id="4dc05-166">使用衝突檢視器來確認偵測到的衝突，然後判斷所涉及的資料列、衝突的類型以及成功者。</span><span class="sxs-lookup"><span data-stu-id="4dc05-166">Verify the conflicts that were detected by using the conflict viewer and determine the rows that were involved, the type of conflict, and the winner.</span></span> <span data-ttu-id="4dc05-167">系統會根據您在組態設定期間指定的訂閱者識別碼值來解決衝突：源自最高識別碼之節點的資料列會在衝突中獲勝。</span><span class="sxs-lookup"><span data-stu-id="4dc05-167">The conflict is resolved based on the originator ID value that you specified during configuration: the row that originated at the node with the highest ID wins the conflict.</span></span> <span data-ttu-id="4dc05-168">如需詳細資訊，請參閱[檢視交易式發行集的資料衝突 &#40;SQL Server Management Studio&#41;](../view-data-conflicts-for-transactional-publications-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="4dc05-168">For more information, see [View Data Conflicts for Transactional Publications &#40;SQL Server Management Studio&#41;](../view-data-conflicts-for-transactional-publications-sql-server-management-studio.md).</span></span>  
  
    4.  <span data-ttu-id="4dc05-169">執行驗證，以便確保衝突資料列會正確聚合。</span><span class="sxs-lookup"><span data-stu-id="4dc05-169">Run validation to ensure that the conflicting rows converged correctly.</span></span> <span data-ttu-id="4dc05-170">如需詳細資訊，請參閱[驗證複寫的資料](../validate-data-at-the-subscriber.md)。</span><span class="sxs-lookup"><span data-stu-id="4dc05-170">For more information, see [Validate Replicated Data](../validate-data-at-the-subscriber.md).</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="4dc05-171">如果進行這個步驟之後資料出現不一致，您就必須手動更新具有最高優先權之節點上的資料列，然後讓變更從這個節點傳播。</span><span class="sxs-lookup"><span data-stu-id="4dc05-171">If data is inconsistent after this step, you must manually update rows on the node that has the highest priority, and then let the changes propagate from this node.</span></span> <span data-ttu-id="4dc05-172">如果拓撲中沒有其他進一步的衝突變更，所有節點都會處於一致狀態。</span><span class="sxs-lookup"><span data-stu-id="4dc05-172">If there are no further conflicting changes in the topology, all nodes will be brought to a consistent state.</span></span>  
  
    5.  <span data-ttu-id="4dc05-173">執行[sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)：指定參數的 ' p2p_continue_onconflict ' @property 和 `false` 參數的 @value 。</span><span class="sxs-lookup"><span data-stu-id="4dc05-173">Execute [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql): specify 'p2p_continue_onconflict' for the @property parameter and `false` for the @value parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dc05-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4dc05-174">See Also</span></span>  
 [<span data-ttu-id="4dc05-175">@loopback_detection</span><span class="sxs-lookup"><span data-stu-id="4dc05-175">Peer-to-Peer Transactional Replication</span></span>](peer-to-peer-transactional-replication.md)  
  
  