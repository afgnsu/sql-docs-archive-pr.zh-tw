---
title: 規劃和執行還原順序 (完整復原模式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- restore sequences [SQL Server], planning for
- full recovery model [SQL Server], planning restore sequences
ms.assetid: 9cbefaf8-d2b6-41c9-83fc-b3807a841fe2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 85558c0a6361837b5645b9fc38ad040254265d72
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598479"
---
# <a name="plan-and-perform-restore-sequences-full-recovery-model"></a><span data-ttu-id="4158f-102">規劃和執行還原順序 (完整復原模式)</span><span class="sxs-lookup"><span data-stu-id="4158f-102">Plan and Perform Restore Sequences (Full Recovery Model)</span></span>
  <span data-ttu-id="4158f-103">此主題說明如何針對一般使用完整復原模式的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫，規劃及執行還原順序。</span><span class="sxs-lookup"><span data-stu-id="4158f-103">This topic explains how to plan and perform a restore sequence for a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases that ordinarily uses the full recovery model.</span></span> <span data-ttu-id="4158f-104">「還原順序」  是一或多個 [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) 陳述式的順序。</span><span class="sxs-lookup"><span data-stu-id="4158f-104">A *restore sequence* is a sequence of one or more [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) statements.</span></span> <span data-ttu-id="4158f-105">還原順序通常會初始化所還原之資料庫、檔案及/或頁面的內容 (資料複製階段)、向前復原記錄的交易 (重做階段)，再回復未認可的交易 (恢復階段)。</span><span class="sxs-lookup"><span data-stu-id="4158f-105">Typically, a restore sequences initializes the contents of the database, files, and/or pages being restored (the data-copy phase), rolls forward logged transactions (the redo phase), and rolls back uncommitted transactions (the undo phase).</span></span>  
  
 <span data-ttu-id="4158f-106">在單純的情況下，還原順序只需要一個完整資料庫備份、一個差異資料庫備份，以及一或多個後續記錄備份。</span><span class="sxs-lookup"><span data-stu-id="4158f-106">In simple cases, a restore sequence requires only a full database backup, a differential database backup, and the subsequent log backups.</span></span> <span data-ttu-id="4158f-107">這種時候，建構正確的還原順序相當容易，</span><span class="sxs-lookup"><span data-stu-id="4158f-107">In these cases, constructing a correct restore sequence is easy.</span></span> <span data-ttu-id="4158f-108">例如，若要將整個資料庫還原到失敗點，可以從備份使用中交易記錄 (記錄的「結尾」  ) 開始。</span><span class="sxs-lookup"><span data-stu-id="4158f-108">For example, to restore a whole database to the point of a failure, start by backing up the active transaction log (the *tail* of the log).</span></span> <span data-ttu-id="4158f-109">然後，還原最近一次完整資料庫備份、最近一次差異備份 (若有的話)，再依照進行記錄備份的順序還原所有後續的記錄備份。</span><span class="sxs-lookup"><span data-stu-id="4158f-109">Then, restore the most recent full database backup, the most recent differential backup (if any), and all subsequent log backups in the order in which they were taken.</span></span>  
  
 <span data-ttu-id="4158f-110">在更複雜的情況下，建構正確的還原順序會是很複雜的程序。</span><span class="sxs-lookup"><span data-stu-id="4158f-110">In more complex cases, constructing a correct restore sequence can be a complex process.</span></span> <span data-ttu-id="4158f-111">例如，還原順序可能需要多個檔案備份，或者必須將資料還原到特定的時間點。</span><span class="sxs-lookup"><span data-stu-id="4158f-111">For example, a restore sequence might require multiple file backups or restoring data to a specific point in time.</span></span> <span data-ttu-id="4158f-112">在極其複雜的情況下，甚至可能需要周遊跨越一個或多個復原分支的分岔復原路徑。</span><span class="sxs-lookup"><span data-stu-id="4158f-112">In very complex cases, you might even have to traverse a forked recovery path that spans one or more recovery forks.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4158f-113">「復原路徑」  是指將資料庫復原到特定時間點 (稱為復原點) 的資料和記錄備份順序。</span><span class="sxs-lookup"><span data-stu-id="4158f-113">A *recovery path* is the sequence of data and log backups that have brought a database to a particular point in time (known as a recovery point).</span></span> <span data-ttu-id="4158f-114">復原路徑是一組特定轉換，這些轉換會使資料庫隨時間而變化，同時又能維護資料庫的一致性。</span><span class="sxs-lookup"><span data-stu-id="4158f-114">A recovery path is a specific set of transformations that have evolved the database over time, yet have maintained the consistency of the database.</span></span> <span data-ttu-id="4158f-115">復原路徑描述從起點 (LSN,GUID) 到終點 (LSN,GUID) 的 LSN 範圍。</span><span class="sxs-lookup"><span data-stu-id="4158f-115">A recovery path describes a range of LSNs from a start point (LSN,GUID) to an end point (LSN,GUID).</span></span> <span data-ttu-id="4158f-116">復原路徑中的 LSN 範圍從開始到結束可能會跨越一個或多個復原分支。</span><span class="sxs-lookup"><span data-stu-id="4158f-116">The range of LSNs in a recovery path can traverse one or more recovery branches from start to end.</span></span>  
  
## <a name="to-plan-a-restore-sequence"></a><span data-ttu-id="4158f-117">規劃還原順序</span><span class="sxs-lookup"><span data-stu-id="4158f-117">To Plan a Restore Sequence</span></span>  
 <span data-ttu-id="4158f-118">在啟動還原順序前，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="4158f-118">Before you start a restore sequence, follow these steps:</span></span>  
  
1.  <span data-ttu-id="4158f-119">盡可能建立資料庫的結尾記錄備份。</span><span class="sxs-lookup"><span data-stu-id="4158f-119">Create a tail-log backup of the database, if you can.</span></span> <span data-ttu-id="4158f-120">如需詳細資訊，請參閱[結尾記錄備份 &#40;SQL Server&#41;](tail-log-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="4158f-120">For more information, see [Tail-Log Backups &#40;SQL Server&#41;](tail-log-backups-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="4158f-121">判斷目標復原點。</span><span class="sxs-lookup"><span data-stu-id="4158f-121">Determine the target recovery point.</span></span>  
  
     <span data-ttu-id="4158f-122">目標復原點可以是交易記錄備份中的任何時間點或標示。</span><span class="sxs-lookup"><span data-stu-id="4158f-122">The target recovery point can be any point in time or mark within a transaction log backup.</span></span> <span data-ttu-id="4158f-123">如需詳細資訊，請參閱[將 SQL Server 資料庫還原至某個時間點 &#40;完整復原模式&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md) 或[使用標示的交易以一致的方式復原相關資料庫 &#40;完整復原模式&#41;](use-marked-transactions-to-recover-related-databases-consistently.md)。</span><span class="sxs-lookup"><span data-stu-id="4158f-123">For more information, see [Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md) or [Use Marked Transactions to Recover Related Databases Consistently &#40;Full Recovery Model&#41;](use-marked-transactions-to-recover-related-databases-consistently.md).</span></span>  
  
3.  <span data-ttu-id="4158f-124">決定要執行的還原類型。</span><span class="sxs-lookup"><span data-stu-id="4158f-124">Determine the type of restore you want to perform.</span></span> <span data-ttu-id="4158f-125">如需詳細資訊，請參閱 [還原和復原概觀 &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="4158f-125">For more information, see [Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md).</span></span>  
  
4.  <span data-ttu-id="4158f-126">識別所需的備份，並確定必要的媒體集和備份裝置都可使用。</span><span class="sxs-lookup"><span data-stu-id="4158f-126">Identify which backups you require and make sure that the necessary media sets and backup devices are available.</span></span> <span data-ttu-id="4158f-127">如需詳細資訊，請參閱[備份裝置 &#40;SQL Server&#41;](backup-devices-sql-server.md) 和[媒體集、媒體家族與備份組 &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="4158f-127">For more information, see [Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md) and [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).</span></span>  
  
## <a name="to-perform-a-restore-sequence"></a><span data-ttu-id="4158f-128">執行還原順序</span><span class="sxs-lookup"><span data-stu-id="4158f-128">To Perform a Restore Sequence</span></span>  
 <span data-ttu-id="4158f-129">若要執行還原順序，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="4158f-129">To perform a restore sequence, follow these steps:</span></span>  
  
1.  <span data-ttu-id="4158f-130">若要啟動順序，請還原一或多個資料備份，例如資料庫備份、部分備份、一或多個檔案備份。</span><span class="sxs-lookup"><span data-stu-id="4158f-130">To start the sequence, restore a one or more data backups, such as: a database backup, a partial backup, one or more file backups.</span></span>  
  
2.  <span data-ttu-id="4158f-131">此外，也可以還原以這些完整備份為基礎的最新差異備份。</span><span class="sxs-lookup"><span data-stu-id="4158f-131">Optionally, restore the latest differential backups that are based on these full backups.</span></span>  
  
     <span data-ttu-id="4158f-132">針對您要還原的每個完整備份，判斷它是否為任何差異備份的基底。</span><span class="sxs-lookup"><span data-stu-id="4158f-132">For each full backup that you plan to restore, determine whether it is the base for any differential backups.</span></span> <span data-ttu-id="4158f-133">若是如此，請盡可能還原最近一次的差異備份。</span><span class="sxs-lookup"><span data-stu-id="4158f-133">If so, restore most recent differential backup, if you can.</span></span> <span data-ttu-id="4158f-134">如需詳細資訊，請參閱 [差異備份 &#40;SQL Server&#41;](differential-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="4158f-134">For more information, see [Differential Backups &#40;SQL Server&#41;](differential-backups-sql-server.md).</span></span>  
  
3.  <span data-ttu-id="4158f-135">依序還原記錄備份以向前復原資料庫，最後再還原包含復原點的備份。</span><span class="sxs-lookup"><span data-stu-id="4158f-135">Roll forward the database by restoring log backups in sequence, finishing with the backup that contains the recovery point.</span></span> <span data-ttu-id="4158f-136">是否需要套用所有的記錄備份，取決於什麼記錄備份包含了目標復原點，如下所述：</span><span class="sxs-lookup"><span data-stu-id="4158f-136">Whether you have to apply all the log backups depends on what log backup contains the target recovery point, as follows:</span></span>  
  
    -   <span data-ttu-id="4158f-137">如果復原點是失敗點，則必須還原在您還原的最後一個資料 (完整或差異) 備份之後所建立的每個記錄備份。</span><span class="sxs-lookup"><span data-stu-id="4158f-137">If the recovery point is the point of a failure, you must restore every log backup that was created since the last data (full or differential) backup you restored.</span></span> <span data-ttu-id="4158f-138">如需詳細資訊，請參閱[套用交易記錄備份 &#40;SQL Server&#41;](transaction-log-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="4158f-138">For more information, see [Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md).</span></span>  
  
    -   <span data-ttu-id="4158f-139">如果是時間點還原，您可能就不需要最近一次的記錄備份。</span><span class="sxs-lookup"><span data-stu-id="4158f-139">For a point-in-time restore, you might not require the most recent log backups.</span></span> <span data-ttu-id="4158f-140">如果您使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]，Database Recovery Advisor 會確定只選取要還原到指定的時間點所需的備份。</span><span class="sxs-lookup"><span data-stu-id="4158f-140">If you use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], the Database Recovery Advisor ensures that only backups that are required to restore to your specified point in time are selected.</span></span> <span data-ttu-id="4158f-141">這些備份為您的時間點還原構成了建議的還原計畫。</span><span class="sxs-lookup"><span data-stu-id="4158f-141">These backups make up the recommended restore plan for your point-in-time restore.</span></span> <span data-ttu-id="4158f-142">如需詳細資訊，請參閱[將 SQL Server 資料庫還原至某個時間點 &#40;完整復原模式&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)。</span><span class="sxs-lookup"><span data-stu-id="4158f-142">For more information, see [Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md).</span></span>  
  
## <a name="restarting-a-restore-sequence"></a><span data-ttu-id="4158f-143">重新啟動還原順序</span><span class="sxs-lookup"><span data-stu-id="4158f-143">Restarting a Restore Sequence</span></span>  
 <span data-ttu-id="4158f-144">如果還原順序產生的結果有問題，您可以停止還原順序，然後從頭開始重新啟動。</span><span class="sxs-lookup"><span data-stu-id="4158f-144">If you encounter a problem with the outcome of a restore sequence, you can quit it and restart the restore sequence over from the start.</span></span> <span data-ttu-id="4158f-145">例如，如果您不小心還原了太多記錄備份，並且超過預期的復原點，就必須重新啟動還原順序，一直到含有目標復原點的記錄備份。</span><span class="sxs-lookup"><span data-stu-id="4158f-145">For example, if you accidentally restore too many log backups and overshoot the intended recovery point, you must restart the restore sequence up to log backup that contains the target recovery point.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4158f-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4158f-146">See Also</span></span>  
 <span data-ttu-id="4158f-147">[備份概觀 &#40;SQL Server&#41;](backup-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="4158f-147">[Backup Overview &#40;SQL Server&#41;](backup-overview-sql-server.md) </span></span>  
 <span data-ttu-id="4158f-148">[還原和復原概觀 &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="4158f-148">[Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span></span>  
 <span data-ttu-id="4158f-149">[完整資料庫還原 &#40;完整復原模式&#41;](complete-database-restores-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="4158f-149">[Complete Database Restores &#40;Full Recovery Model&#41;](complete-database-restores-full-recovery-model.md) </span></span>  
 <span data-ttu-id="4158f-150">[線上還原 &#40;SQL Server&#41;](online-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="4158f-150">[Online Restore &#40;SQL Server&#41;](online-restore-sql-server.md) </span></span>  
 <span data-ttu-id="4158f-151">[檔案還原 &#40;完整復原模式&#41;](file-restores-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="4158f-151">[File Restores &#40;Full Recovery Model&#41;](file-restores-full-recovery-model.md) </span></span>  
 <span data-ttu-id="4158f-152">[還原頁面 &#40;SQL Server&#41;](restore-pages-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="4158f-152">[Restore Pages &#40;SQL Server&#41;](restore-pages-sql-server.md) </span></span>  
 [<span data-ttu-id="4158f-153">分次還原 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="4158f-153">Piecemeal Restores &#40;SQL Server&#41;</span></span>](piecemeal-restores-sql-server.md)  
  
  