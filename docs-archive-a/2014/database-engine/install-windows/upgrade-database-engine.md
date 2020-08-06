---
title: 升級資料庫引擎 | Microsoft Docs
ms.custom: ''
ms.date: 10/26/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- compatibility [SQL Server], databases
- compatibility levels [SQL Server], after upgrade
- Database Engine [SQL Server], upgrading
ms.assetid: 3c036813-36cf-4415-a0c9-248d0a433859
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ed13712678ab599e55b539d6226142b686106fe5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594163"
---
# <a name="upgrade-database-engine"></a><span data-ttu-id="f5fac-102">升級 Database Engine</span><span class="sxs-lookup"><span data-stu-id="f5fac-102">Upgrade Database Engine</span></span>
  <span data-ttu-id="f5fac-103">本主題提供了您在準備和了解升級程序時所需要的資訊，其中涵蓋：</span><span class="sxs-lookup"><span data-stu-id="f5fac-103">This topic provides the information that you will need to prepare for and understand the upgrade process; it covers:</span></span>  
  
-   <span data-ttu-id="f5fac-104">已知的升級問題。</span><span class="sxs-lookup"><span data-stu-id="f5fac-104">Known upgrade issues.</span></span>  
  
-   <span data-ttu-id="f5fac-105">升級前的工作和考量。</span><span class="sxs-lookup"><span data-stu-id="f5fac-105">Pre-upgrade tasks and considerations.</span></span>  
  
-   <span data-ttu-id="f5fac-106">升級 [!INCLUDE[ssDE](../../includes/ssde-md.md)]之程序主題的連結。</span><span class="sxs-lookup"><span data-stu-id="f5fac-106">Links to procedural topics for upgrading the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
-   <span data-ttu-id="f5fac-107">將資料庫移轉到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]之程序主題的連結。</span><span class="sxs-lookup"><span data-stu-id="f5fac-107">Links to procedural topics for migrating databases to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="f5fac-108">容錯移轉叢集的考量。</span><span class="sxs-lookup"><span data-stu-id="f5fac-108">Considerations for failover clusters.</span></span>  
  
-   <span data-ttu-id="f5fac-109">升級後的工作和考量。</span><span class="sxs-lookup"><span data-stu-id="f5fac-109">Post-upgrade tasks and considerations.</span></span>  
  
## <a name="known-upgrade-issues"></a><span data-ttu-id="f5fac-110">已知的升級問題</span><span class="sxs-lookup"><span data-stu-id="f5fac-110">Known Upgrade issues</span></span>  
 <span data-ttu-id="f5fac-111">在升級 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 之前，請檢閱 [SQL Server Database Engine 回溯相容性](../sql-server-database-engine-backward-compatibility.md)。</span><span class="sxs-lookup"><span data-stu-id="f5fac-111">Before upgrading the [!INCLUDE[ssDE](../../includes/ssde-md.md)], review [SQL Server Database Engine Backward Compatibility](../sql-server-database-engine-backward-compatibility.md).</span></span> <span data-ttu-id="f5fac-112">如需所支援升級狀況和升級已知問題的相關資訊，請參閱[支援的版本與版本升級](supported-version-and-edition-upgrades.md)。</span><span class="sxs-lookup"><span data-stu-id="f5fac-112">For information about supported upgrade scenarios and upgrade known issues, see [Supported Version and Edition Upgrades](supported-version-and-edition-upgrades.md).</span></span> <span data-ttu-id="f5fac-113">如需其他 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元件的回溯相容性內容，請參閱[回溯相容性](../../getting-started/backward-compatibility.md)。</span><span class="sxs-lookup"><span data-stu-id="f5fac-113">For backward compatibility content for other [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components, see [Backward Compatibility](../../getting-started/backward-compatibility.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f5fac-114">從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的一個版本升級到另一個版本之前，請確認您目前使用的功能在您想要升級後的版本中有受到支援。</span><span class="sxs-lookup"><span data-stu-id="f5fac-114">Before you upgrade from one edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to another, verify that the functionality that you are currently using is supported in the edition to which you are upgrading.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f5fac-115">當您從舊版 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Enterprise Edition 升級至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 時，請選擇 [Enterprise Edition：核心授權] 或 [Enterprise Edition]。</span><span class="sxs-lookup"><span data-stu-id="f5fac-115">When you upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] from a prior version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise edition, choose between Enterprise Edition: Core-based Licensing and Enterprise Edition.</span></span> <span data-ttu-id="f5fac-116">這些 Enterprise Edition 只有在授權模式方面不同。</span><span class="sxs-lookup"><span data-stu-id="f5fac-116">These Enterprise editions differ only with respect to the licensing modes.</span></span> <span data-ttu-id="f5fac-117">如需詳細資訊，請參閱 [Compute Capacity Limits by Edition of SQL Server](../../sql-server/compute-capacity-limits-by-edition-of-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="f5fac-117">For more information, see [Compute Capacity Limits by Edition of SQL Server](../../sql-server/compute-capacity-limits-by-edition-of-sql-server.md).</span></span>  
  
## <a name="pre-upgrade-checklist"></a><span data-ttu-id="f5fac-118">升級前檢查清單</span><span class="sxs-lookup"><span data-stu-id="f5fac-118">Pre-Upgrade Checklist</span></span>  
 <span data-ttu-id="f5fac-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式支援從舊版升級 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="f5fac-119">Upgrading [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from an earlier version is supported by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup program.</span></span> <span data-ttu-id="f5fac-120">您也可以從舊版的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 移轉資料庫。</span><span class="sxs-lookup"><span data-stu-id="f5fac-120">You can also migrate databases from previous [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versions.</span></span> <span data-ttu-id="f5fac-121">您可以從一個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體移轉到同一部電腦的另一個執行個體，或是從另一部電腦的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體移轉。</span><span class="sxs-lookup"><span data-stu-id="f5fac-121">Migration can be from one [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance to another on the same computer, or from a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance on another computer.</span></span> <span data-ttu-id="f5fac-122">移轉選項包括使用複製資料庫精靈、備份與還原功能、使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 匯入與匯出精靈，以及大量匯出/大量匯入方法。</span><span class="sxs-lookup"><span data-stu-id="f5fac-122">Migration options include use of the Copy Database Wizard, Backup and restore functionality, use of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Import and Export Wizard, and bulk export/bulk import methods.</span></span>  
  
 <span data-ttu-id="f5fac-123">在升級 [!INCLUDE[ssDE](../../includes/ssde-md.md)]之前，請檢閱下列文章：</span><span class="sxs-lookup"><span data-stu-id="f5fac-123">Before upgrading the [!INCLUDE[ssDE](../../includes/ssde-md.md)], review the following:</span></span>  
  
-   <span data-ttu-id="f5fac-124">檢閱 [Hardware and Software Requirements for Installing SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="f5fac-124">Review [Hardware and Software Requirements for Installing SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).</span></span>  
  
-   <span data-ttu-id="f5fac-125">檢閱 [Check Parameters for the System Configuration Checker](check-parameters-for-the-system-configuration-checker.md)。</span><span class="sxs-lookup"><span data-stu-id="f5fac-125">Review [Check Parameters for the System Configuration Checker](check-parameters-for-the-system-configuration-checker.md).</span></span>  
  
-   <span data-ttu-id="f5fac-126">檢閱 [Security Considerations for a SQL Server Installation](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)。</span><span class="sxs-lookup"><span data-stu-id="f5fac-126">Review [Security Considerations for a SQL Server Installation](../../sql-server/install/security-considerations-for-a-sql-server-installation.md).</span></span>  
  
-   <span data-ttu-id="f5fac-127">檢閱[支援的版本與版本升級](supported-version-and-edition-upgrades.md)。</span><span class="sxs-lookup"><span data-stu-id="f5fac-127">Review [Supported Version and Edition Upgrades](supported-version-and-edition-upgrades.md).</span></span>  
  
-   <span data-ttu-id="f5fac-128">檢閱[使用 Upgrade Advisor 來準備升級](../../sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md)。</span><span class="sxs-lookup"><span data-stu-id="f5fac-128">Review [Use Upgrade Advisor to Prepare for Upgrades](../../sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md).</span></span>  
  
-   <span data-ttu-id="f5fac-129">檢閱[使用 Distributed Replay Utility 來準備升級](../../sql-server/install/use-the-distributed-replay-utility-to-prepare-for-upgrades.md)。</span><span class="sxs-lookup"><span data-stu-id="f5fac-129">Review [Use the Distributed Replay Utility to Prepare for Upgrades](../../sql-server/install/use-the-distributed-replay-utility-to-prepare-for-upgrades.md).</span></span>  
  
-   <span data-ttu-id="f5fac-130">檢閱 [SQL Server Database Engine 回溯相容性](../sql-server-database-engine-backward-compatibility.md)。</span><span class="sxs-lookup"><span data-stu-id="f5fac-130">Review [SQL Server Database Engine Backward Compatibility](../sql-server-database-engine-backward-compatibility.md).</span></span>  
  
-   <span data-ttu-id="f5fac-131">檢閱[移轉查詢計劃](change-the-database-compatibility-mode-and-use-the-query-store.md)。</span><span class="sxs-lookup"><span data-stu-id="f5fac-131">Review [Migrate Query Plans](change-the-database-compatibility-mode-and-use-the-query-store.md).</span></span>  
  
 <span data-ttu-id="f5fac-132">在您升級 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]之前，請檢閱下列問題並進行變更：</span><span class="sxs-lookup"><span data-stu-id="f5fac-132">Review the following issues and make changes before you upgrade [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="f5fac-133">升級 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體時，如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 編列在 MSX/TSX 關聯性中，請先升級目標伺服器，然後再升級主要伺服器。</span><span class="sxs-lookup"><span data-stu-id="f5fac-133">When upgrading instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent is enlisted in MSX/TSX relationships, upgrade target servers before you upgrade master servers.</span></span> <span data-ttu-id="f5fac-134">如果您先升級主要伺服器，然後再升級目標伺服器， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 將無法連接至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的主要執行個體。</span><span class="sxs-lookup"><span data-stu-id="f5fac-134">If you upgrade master servers before target servers, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent will not be able to connect to master instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="f5fac-135">從 64 位元版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 升級成 64 位元版本的 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]時，您必須先升級 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，再升級 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f5fac-135">When upgrading from a 64-bit edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to a 64-bit edition of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], you must upgrade [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] before you upgrade the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
-   <span data-ttu-id="f5fac-136">從要升級的執行個體備份所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫檔案，好讓您可以在必要時還原它們。</span><span class="sxs-lookup"><span data-stu-id="f5fac-136">Back up all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database files from the instance to be upgraded, so that you can restore them, if it is required.</span></span>  
  
-   <span data-ttu-id="f5fac-137">對要升級的資料庫執行適當的 Database Console Commands (DBCC)，以確定它們處於一致狀態。</span><span class="sxs-lookup"><span data-stu-id="f5fac-137">Run the appropriate Database Console Commands (DBCC) on databases to be upgraded to ensure that they are in a consistent state.</span></span>  
  
-   <span data-ttu-id="f5fac-138">除了使用者資料庫以外，也要評估升級 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元件所需的磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="f5fac-138">Estimate the disk space that is required to upgrade [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components, in addition to user databases.</span></span> <span data-ttu-id="f5fac-139">如需 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元件所需的磁碟空間，請參閱[安裝 SQL Server 2014 的硬體與軟體需求](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="f5fac-139">For disk space that is required by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] components, see [Hardware and Software Requirements for Installing SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).</span></span>  
  
-   <span data-ttu-id="f5fac-140">確定現有的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系統資料庫 master、model、msdb 和 tempdb 都設定為自動成長，並確定它們有足夠的硬碟空間。</span><span class="sxs-lookup"><span data-stu-id="f5fac-140">Ensure that existing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system databases - master, model, msdb, and tempdb - are configured to autogrow, and ensure that they have sufficient hard disk space.</span></span>  
  
-   <span data-ttu-id="f5fac-141">確定所有資料庫伺服器在 master 資料庫中都有登入資訊。</span><span class="sxs-lookup"><span data-stu-id="f5fac-141">Ensure that all database servers have logon information in the master database.</span></span> <span data-ttu-id="f5fac-142">這對於還原資料庫很重要，因為系統登入資訊是位於 master 中。</span><span class="sxs-lookup"><span data-stu-id="f5fac-142">This is important for restoring a database, as system logon information resides in master.</span></span>  
  
-   <span data-ttu-id="f5fac-143">停用所有啟動預存程序，因為升級程序將會在升級的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上停止及啟動服務。</span><span class="sxs-lookup"><span data-stu-id="f5fac-143">Disable all startup stored procedures, as the upgrade process will stop and start services on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance being upgraded.</span></span> <span data-ttu-id="f5fac-144">在啟動時處理的預存程序可能會封鎖升級程序。</span><span class="sxs-lookup"><span data-stu-id="f5fac-144">Stored procedures processed at startup time might block the upgrade process.</span></span>  
  
-   <span data-ttu-id="f5fac-145">確認複寫為當前的複寫，然後將之停止。</span><span class="sxs-lookup"><span data-stu-id="f5fac-145">Make sure that Replication is current and then stop Replication.</span></span>  
  
-   <span data-ttu-id="f5fac-146">結束所有應用程式，包括具有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 相依性的所有服務。</span><span class="sxs-lookup"><span data-stu-id="f5fac-146">Quit all applications, including all services that have [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dependencies.</span></span> <span data-ttu-id="f5fac-147">如果本機應用程式連接到要升級的執行個體，則升級可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="f5fac-147">Upgrade might fail if local applications are connected to the instance being upgraded.</span></span>  
  
-   <span data-ttu-id="f5fac-148">如需詳細資訊，請參閱[在升級伺服器執行個體時將鏡像資料庫的停機時間減至最少](../database-mirroring/upgrading-mirrored-instances.md)。</span><span class="sxs-lookup"><span data-stu-id="f5fac-148">If you use Database Mirroring, see [Minimize Downtime for Mirrored Databases When Upgrading Server Instances](../database-mirroring/upgrading-mirrored-instances.md).</span></span>  
  
## <a name="upgrading-the-database-engine"></a><span data-ttu-id="f5fac-149">升級 Database Engine</span><span class="sxs-lookup"><span data-stu-id="f5fac-149">Upgrading the Database Engine</span></span>  
 <span data-ttu-id="f5fac-150">您可以用版本升級覆寫 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 或更新版本的安裝。</span><span class="sxs-lookup"><span data-stu-id="f5fac-150">You can overwrite an installation of [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] or later with a version upgrade.</span></span> <span data-ttu-id="f5fac-151">如果在執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式時偵測到舊版的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，所有舊版的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 程式檔都會升級，但是會保留舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中儲存的所有資料。</span><span class="sxs-lookup"><span data-stu-id="f5fac-151">If an earlier version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is detected when you run [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup, all previous [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] program files are upgraded, and all data stored in the previous [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance is preserved.</span></span> <span data-ttu-id="f5fac-152">此外，舊版的《 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》將原封不動地保留在電腦上。</span><span class="sxs-lookup"><span data-stu-id="f5fac-152">In addition, earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online will remain intact on the computer.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="f5fac-153">執行 SQL Server 2014 安裝程式時，SQL Server 執行個體會因為執行升級前檢查而停止並重新啟動。</span><span class="sxs-lookup"><span data-stu-id="f5fac-153">When running the SQL Server 2014 setup program, the SQL Server instance is stopped and restarted as part of running the pre-upgrade checks.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="f5fac-154">當您升級 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]時，會覆寫先前的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，所以它不再存在於電腦上。</span><span class="sxs-lookup"><span data-stu-id="f5fac-154">When you upgrade [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the previous [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance will be overwritten and will no longer exist on your computer.</span></span> <span data-ttu-id="f5fac-155">升級之前，請備份 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫以及與先前的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體相關聯的其他物件。</span><span class="sxs-lookup"><span data-stu-id="f5fac-155">Before upgrading, back up [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases and other objects associated with the previous [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span>  
  
 <span data-ttu-id="f5fac-156">您可以使用 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 安裝精靈來升級 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="f5fac-156">You can upgrade the [!INCLUDE[ssDE](../../includes/ssde-md.md)] by using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation Wizard.</span></span>  
  
### <a name="database-compatibility-level-after-upgrade"></a><span data-ttu-id="f5fac-157">升級後的資料庫相容性層級</span><span class="sxs-lookup"><span data-stu-id="f5fac-157">Database Compatibility Level After Upgrade</span></span>  
 <span data-ttu-id="f5fac-158">`tempdb`升級之後，、和資源資料庫的相容性層級 `model` `msdb` 會設定為120。 **Resource**</span><span class="sxs-lookup"><span data-stu-id="f5fac-158">The compatibility levels of the `tempdb`, `model`, `msdb` and **Resource** databases are set to 120 after upgrade.</span></span> <span data-ttu-id="f5fac-159">`master` 系統資料庫會繼續保有升級前的相容性層級。</span><span class="sxs-lookup"><span data-stu-id="f5fac-159">The `master` system database retains the compatibility level it had before upgrade.</span></span>  
  
 <span data-ttu-id="f5fac-160">如果使用者資料庫的相容性層級在升級前為 100 或更高層級，則在升級後仍會保持相同。</span><span class="sxs-lookup"><span data-stu-id="f5fac-160">If the compatibility level of a user database was 100 or higher before the upgrade, it remains the same after upgrade.</span></span> <span data-ttu-id="f5fac-161">如果升級前的相容性層級為 90，則在升級後的資料庫中，相容性層級會設定為 100 (這是 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]所支援的最低相容性層級)。</span><span class="sxs-lookup"><span data-stu-id="f5fac-161">If the compatibility level was 90 before upgrade, in the upgraded database, the compatibility level is set to 100, which is the lowest supported compatibility level in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f5fac-162">新的使用者資料庫會繼承 `model` 資料庫的相容性層級。</span><span class="sxs-lookup"><span data-stu-id="f5fac-162">New user databases will inherit the compatibility level of the `model` database.</span></span>  
  
## <a name="migrating-databases"></a><span data-ttu-id="f5fac-163">移轉資料庫</span><span class="sxs-lookup"><span data-stu-id="f5fac-163">Migrating Databases</span></span>  
 <span data-ttu-id="f5fac-164">您可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的備份和還原或是卸離和附加功能，將使用者資料庫移到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體。</span><span class="sxs-lookup"><span data-stu-id="f5fac-164">You can move user databases to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using backup and restore or detach and attach functionalities in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f5fac-165">如需詳細資訊，請參閱[使用備份與還原複製資料庫](../../relational-databases/databases/copy-databases-with-backup-and-restore.md)或[資料庫卸離與附加 &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="f5fac-165">For more information, see [Copy Databases with Backup and Restore](../../relational-databases/databases/copy-databases-with-backup-and-restore.md) or [Database Detach and Attach &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f5fac-166">來源和目的地伺服器上具有相同名稱的資料庫將無法移動或複製。</span><span class="sxs-lookup"><span data-stu-id="f5fac-166">A database that has the identical name on both source and destination servers cannot be moved or copied.</span></span> <span data-ttu-id="f5fac-167">在此情況下，會將它標示為「已存在」。</span><span class="sxs-lookup"><span data-stu-id="f5fac-167">In this case, it will be noted as "Already exists."</span></span>  
  
 <span data-ttu-id="f5fac-168">如需詳細資訊，請參閱 [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="f5fac-168">For more information, see [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).</span></span>  
  
## <a name="after-upgrading-the-database-engine"></a><span data-ttu-id="f5fac-169">升級 Database Engine 之後</span><span class="sxs-lookup"><span data-stu-id="f5fac-169">After Upgrading the Database Engine</span></span>  
 <span data-ttu-id="f5fac-170">在升級 [!INCLUDE[ssDE](../../includes/ssde-md.md)]之後，請完成下列工作：</span><span class="sxs-lookup"><span data-stu-id="f5fac-170">After upgrading the [!INCLUDE[ssDE](../../includes/ssde-md.md)], complete the following tasks:</span></span>  
  
-   <span data-ttu-id="f5fac-171">重新註冊伺服器。</span><span class="sxs-lookup"><span data-stu-id="f5fac-171">Re-register your servers.</span></span> <span data-ttu-id="f5fac-172">如需註冊伺服器的詳細資訊，請參閱[註冊伺服器](../../ssms/register-servers/register-servers.md)。</span><span class="sxs-lookup"><span data-stu-id="f5fac-172">For more information about registering servers, see [Register Servers](../../ssms/register-servers/register-servers.md).</span></span>  
  
-   <span data-ttu-id="f5fac-173">為確保查詢結果中語意的一致性，必須重新擴展全文檢索目錄。</span><span class="sxs-lookup"><span data-stu-id="f5fac-173">Re-populate full-text catalogs to ensure semantic consistency in query results.</span></span>  
  
     [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="f5fac-174">會安裝新的斷詞工具，供全文索引與語意搜尋之用。</span><span class="sxs-lookup"><span data-stu-id="f5fac-174">installs new word breakers for use by Full-Text and Semantic Search.</span></span> <span data-ttu-id="f5fac-175">編製索引及查詢時皆可使用斷詞工具。</span><span class="sxs-lookup"><span data-stu-id="f5fac-175">The word breakers are used both at indexing time and at query time.</span></span> <span data-ttu-id="f5fac-176">如不重建全文索引目錄，可能會造成搜尋結果不一致。</span><span class="sxs-lookup"><span data-stu-id="f5fac-176">If you do not rebuild the full-text catalogs, your search results may be inconsistent.</span></span> <span data-ttu-id="f5fac-177">當您發出全文索引查詢，尋找在舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 斷詞工具中與目前之斷詞工具中斷詞方式相異的片語，可能會無法擷取含有該片語的文件或資料列。</span><span class="sxs-lookup"><span data-stu-id="f5fac-177">If you issue a full-text query that looks for a phrase that is broken differently by the word breaker in a previous version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the current word breaker, a document or row containing the phrase might not be retrieved.</span></span> <span data-ttu-id="f5fac-178">這是索引片語所使用的分解邏輯與查詢所用者不相同所致。</span><span class="sxs-lookup"><span data-stu-id="f5fac-178">This is because the indexed phrases were broken using different logic than the query is using.</span></span> <span data-ttu-id="f5fac-179">此方案會使用新的斷詞工具重新擴展 (重建) 全文索引目錄，讓索引與查詢時的行為一致。</span><span class="sxs-lookup"><span data-stu-id="f5fac-179">The solution is to repopulate (rebuild) the full-text catalogs with the new word breakers so that index time and query time behavior are identical.</span></span>  
  
     <span data-ttu-id="f5fac-180">如需詳細資訊，請參閱 [sp_fulltext_catalog &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-fulltext-catalog-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="f5fac-180">For more information, see [sp_fulltext_catalog &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-fulltext-catalog-transact-sql).</span></span>  
  
-   <span data-ttu-id="f5fac-181">設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝。</span><span class="sxs-lookup"><span data-stu-id="f5fac-181">Configure the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation.</span></span> <span data-ttu-id="f5fac-182">為了減少系統的可攻擊介面區， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可以選擇性地安裝和啟用主要服務和功能。</span><span class="sxs-lookup"><span data-stu-id="f5fac-182">To reduce the attackable surface area of a system, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] selectively installs and enables key services and features.</span></span>  
  
-   <span data-ttu-id="f5fac-183">驗證或移除 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 所產生及套用至分割區資料表和索引上之查詢的 USE PLAN 提示。</span><span class="sxs-lookup"><span data-stu-id="f5fac-183">Validate or remove USE PLAN hints that are generated by [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and applied to queries on partitioned tables and indexes.</span></span>  
  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="f5fac-184">改變了在分割區資料表和索引上處理查詢的方式。</span><span class="sxs-lookup"><span data-stu-id="f5fac-184">changes the way queries on partitioned tables and indexes are processed.</span></span> <span data-ttu-id="f5fac-185">在分割區物件上，針對 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 所產生之計畫使用 USE PLAN 提示的查詢包含了無法在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中使用的計畫。</span><span class="sxs-lookup"><span data-stu-id="f5fac-185">Queries on partitioned objects that use the USE PLAN hint for a plan that is generated by [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] might contain a plan that is not usable in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="f5fac-186">我們建議您在升級到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]之後，使用以下程序。</span><span class="sxs-lookup"><span data-stu-id="f5fac-186">We recommend the following procedures after you upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
     <span data-ttu-id="f5fac-187">**在查詢中直接指定 USE PLAN 提示時：**</span><span class="sxs-lookup"><span data-stu-id="f5fac-187">**When the USE PLAN hint is specified directly in a query:**</span></span>  
  
    1.  <span data-ttu-id="f5fac-188">從查詢中移除 USE PLAN 提示。</span><span class="sxs-lookup"><span data-stu-id="f5fac-188">Remove the USE PLAN hint from the query.</span></span>  
  
    2.  <span data-ttu-id="f5fac-189">測試查詢。</span><span class="sxs-lookup"><span data-stu-id="f5fac-189">Test the query.</span></span>  
  
    3.  <span data-ttu-id="f5fac-190">如果最佳化工具未選取適當的計畫，請微調查詢，然後考慮使用所要的查詢計劃指定 USE PLAN 提示。</span><span class="sxs-lookup"><span data-stu-id="f5fac-190">If the optimizer does not select an appropriate plan, tune the query, and then consider specifying the USE PLAN hint with the desired query plan.</span></span>  
  
     <span data-ttu-id="f5fac-191">**在計畫指南中指定 USE PLAN 提示時：**</span><span class="sxs-lookup"><span data-stu-id="f5fac-191">**When the USE PLAN hint is specified in a plan guide:**</span></span>  
  
    1.  <span data-ttu-id="f5fac-192">使用 sys.fn_validate_plan_guide 函數檢查計畫指南是否有效。</span><span class="sxs-lookup"><span data-stu-id="f5fac-192">Use the sys.fn_validate_plan_guide function to check the validity of the plan guide.</span></span> <span data-ttu-id="f5fac-193">或者，您也可以使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]中的 Plan Guide Unsuccessful 事件來檢查是否有無效的計畫。</span><span class="sxs-lookup"><span data-stu-id="f5fac-193">Alternatively, you can check for invalid plans by using the Plan Guide Unsuccessful event in [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
    2.  <span data-ttu-id="f5fac-194">如果此計畫指南無效，請捨棄此計畫指南。</span><span class="sxs-lookup"><span data-stu-id="f5fac-194">If the plan guide is not valid, drop the plan guide.</span></span> <span data-ttu-id="f5fac-195">如果最佳化工具未選取適當的計畫，請微調查詢，然後考慮使用所要的查詢計劃指定 USE PLAN 提示。</span><span class="sxs-lookup"><span data-stu-id="f5fac-195">If the optimizer does not select an appropriate plan, tune the query, and then consider specifying the USE PLAN hint with the query plan that you want.</span></span>  
  
     <span data-ttu-id="f5fac-196">當計畫指南中指定了 USE PLAN 提示時，無效的計畫將不會造成查詢失敗。</span><span class="sxs-lookup"><span data-stu-id="f5fac-196">A plan that is not valid will not cause the query to fail when the USE PLAN hint is specified in a plan guide.</span></span> <span data-ttu-id="f5fac-197">而是會編譯此查詢，而不使用 USE PLAN 提示。</span><span class="sxs-lookup"><span data-stu-id="f5fac-197">Instead, the query is compiled without using the USE PLAN hint.</span></span>  
  
 <span data-ttu-id="f5fac-198">在升級之前標示為已啟用或已停用全文檢索的任何資料庫，都會在升級之後維持該狀態。</span><span class="sxs-lookup"><span data-stu-id="f5fac-198">Any databases that were marked full-text enabled or disabled before the upgrade will maintain that status after upgrade.</span></span> <span data-ttu-id="f5fac-199">升級之後，會針對所有已啟用全文檢索的資料庫自動重建及擴展全文檢索目錄。</span><span class="sxs-lookup"><span data-stu-id="f5fac-199">After the upgrade, the full-text catalogs will be rebuilt and populated automatically for all full-text enabled databases.</span></span> <span data-ttu-id="f5fac-200">這是一項耗費時間和資源的作業。</span><span class="sxs-lookup"><span data-stu-id="f5fac-200">This is a time-consuming and resource-consuming operation.</span></span> <span data-ttu-id="f5fac-201">您可以執行下列陳述式來暫停全文檢索索引作業：</span><span class="sxs-lookup"><span data-stu-id="f5fac-201">You can pause the full-text indexing operation temporarily by running the following statement:</span></span>  
  
```  
EXEC sp_fulltext_service 'pause_indexing', 1;  
```  
  
 <span data-ttu-id="f5fac-202">若要繼續全文檢索索引母體擴展，請執行下列陳述式：</span><span class="sxs-lookup"><span data-stu-id="f5fac-202">To resume full-text index population, run the following statement:</span></span>  
  
```  
EXEC sp_fulltext_service 'pause_indexing', 0;  
```  
  
## <a name="see-also"></a><span data-ttu-id="f5fac-203">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5fac-203">See Also</span></span>  
 <span data-ttu-id="f5fac-204">[支援的版本與版本升級](supported-version-and-edition-upgrades.md) </span><span class="sxs-lookup"><span data-stu-id="f5fac-204">[Supported Version and Edition Upgrades](supported-version-and-edition-upgrades.md) </span></span>  
 <span data-ttu-id="f5fac-205">[使用 SQL Server 的多個版本和實例](../../../2014/sql-server/install/work-with-multiple-versions-and-instances-of-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f5fac-205">[Work with Multiple Versions and Instances of SQL Server](../../../2014/sql-server/install/work-with-multiple-versions-and-instances-of-sql-server.md) </span></span>  
 <span data-ttu-id="f5fac-206">[回溯相容性](../../getting-started/backward-compatibility.md) </span><span class="sxs-lookup"><span data-stu-id="f5fac-206">[Backward Compatibility](../../getting-started/backward-compatibility.md) </span></span>  
 [<span data-ttu-id="f5fac-207">升級複寫的資料庫</span><span class="sxs-lookup"><span data-stu-id="f5fac-207">Upgrade Replicated Databases</span></span>](upgrade-replicated-databases.md)  
  
  