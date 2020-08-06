---
title: MSSQLSERVER_7906 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7906 (Database Engine error)
ms.assetid: 9638a764-4ac1-40ae-a614-2726ebcc6ba4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 57485a8f330f186a4abd83182c6035168ed38e0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596005"
---
# <a name="mssqlserver_7906"></a><span data-ttu-id="92013-102">MSSQLSERVER_7906</span><span class="sxs-lookup"><span data-stu-id="92013-102">MSSQLSERVER_7906</span></span>
    
## <a name="details"></a><span data-ttu-id="92013-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="92013-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="92013-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="92013-104">Product Name</span></span>|<span data-ttu-id="92013-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="92013-105">SQL Server</span></span>|  
|<span data-ttu-id="92013-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="92013-106">Event ID</span></span>|<span data-ttu-id="92013-107">7906</span><span class="sxs-lookup"><span data-stu-id="92013-107">7906</span></span>|  
|<span data-ttu-id="92013-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="92013-108">Event Source</span></span>|<span data-ttu-id="92013-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="92013-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="92013-110">元件</span><span class="sxs-lookup"><span data-stu-id="92013-110">Component</span></span>|<span data-ttu-id="92013-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="92013-111">SQLEngine</span></span>|  
|<span data-ttu-id="92013-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="92013-112">Symbolic Name</span></span>|<span data-ttu-id="92013-113">DBCC2_FS_INVALID_TOP_LEVEL_FILE</span><span class="sxs-lookup"><span data-stu-id="92013-113">DBCC2_FS_INVALID_TOP_LEVEL_FILE</span></span>|  
|<span data-ttu-id="92013-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="92013-114">Message Text</span></span>|<span data-ttu-id="92013-115">資料庫錯誤:檔案 'FILE' 不是有效的 Filestream 檔案。</span><span class="sxs-lookup"><span data-stu-id="92013-115">Database error: The file 'FILE' is not a valid Filestream file.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="92013-116">說明</span><span class="sxs-lookup"><span data-stu-id="92013-116">Explanation</span></span>  
 <span data-ttu-id="92013-117">除了某些特殊的檔案 (例如 'filestream.hdr') 以外，您應該不會直接在 Filestream 資料空間底下找到任何檔案。</span><span class="sxs-lookup"><span data-stu-id="92013-117">Except for some special files such as, 'filestream.hdr', no files should be found directly under the Filestream dataspace.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="92013-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="92013-118">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="92013-119">尋找硬體故障</span><span class="sxs-lookup"><span data-stu-id="92013-119">Look for Hardware Failure</span></span>  
 <span data-ttu-id="92013-120">請執行硬體診斷並更正所有問題，</span><span class="sxs-lookup"><span data-stu-id="92013-120">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="92013-121">同時檢查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系統和應用程式記錄檔以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔，以查看錯誤發生的原因是否為硬體故障。</span><span class="sxs-lookup"><span data-stu-id="92013-121">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="92013-122">請修正前述記錄檔中所包含的任何硬體相關問題。</span><span class="sxs-lookup"><span data-stu-id="92013-122">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="92013-123">若有持續發生的資料損毀問題，請嘗試抽換不同的硬體元件以隔離問題。</span><span class="sxs-lookup"><span data-stu-id="92013-123">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="92013-124">請檢查以確認系統並未啟用磁碟控制器上的寫入快取功能。</span><span class="sxs-lookup"><span data-stu-id="92013-124">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="92013-125">如果您懷疑寫入快取就是問題所在，請與您的硬體廠商連絡。</span><span class="sxs-lookup"><span data-stu-id="92013-125">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="92013-126">最後，切換到新的硬體系統可能也會有幫助。</span><span class="sxs-lookup"><span data-stu-id="92013-126">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="92013-127">此切換作業可能包括重新格式化磁碟機以及重新安裝作業系統。</span><span class="sxs-lookup"><span data-stu-id="92013-127">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="92013-128">還原備份</span><span class="sxs-lookup"><span data-stu-id="92013-128">Restore from Backup</span></span>  
 <span data-ttu-id="92013-129">如果問題與硬體無關，而且確定有未受影響的備份可以使用，請利用該備份來還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="92013-129">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="92013-130">執行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="92013-130">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="92013-131">不適用。</span><span class="sxs-lookup"><span data-stu-id="92013-131">Not applicable.</span></span> <span data-ttu-id="92013-132">此錯誤無法修復。</span><span class="sxs-lookup"><span data-stu-id="92013-132">This error cannot be repaired.</span></span> <span data-ttu-id="92013-133">如果無法從備份還原資料庫，請連絡 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 客戶服務及支援中心 (CSS)。</span><span class="sxs-lookup"><span data-stu-id="92013-133">If you cannot restore the database from a backup, contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support (CSS).</span></span>  
  
  