---
title: 系統設定 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- Master Data Services, system settings
- system settings [Master Data Services]
ms.assetid: 83075cdf-f059-4646-8ba2-19be8202f130
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 667c154998a0e3f43018b63472619bcb37d9795a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596751"
---
# <a name="system-settings-master-data-services"></a><span data-ttu-id="aadf4-102">系統設定 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="aadf4-102">System Settings (Master Data Services)</span></span>
  <span data-ttu-id="aadf4-103">針對與 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 資料庫相關聯的所有 Web 應用程式和 Web 服務，您可以設定系統設定。</span><span class="sxs-lookup"><span data-stu-id="aadf4-103">For all web applications and web services associated with a [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database, you can configure system settings.</span></span>  
  
 <span data-ttu-id="aadf4-104">這些設定中有許多都是可在 [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] 的 [資料庫]\*\*\*\* 頁面上設定。</span><span class="sxs-lookup"><span data-stu-id="aadf4-104">Many of these settings can be configured in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] on the **Database** page.</span></span> <span data-ttu-id="aadf4-105">有些設定可在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 資料庫的 [系統設定] 資料表 (mdm.tblSystemSetting) 中設定。</span><span class="sxs-lookup"><span data-stu-id="aadf4-105">Others can be configured in the System Settings table (mdm.tblSystemSetting) in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span>  
  
 <span data-ttu-id="aadf4-106">這些設定會依下列類別目錄分組：</span><span class="sxs-lookup"><span data-stu-id="aadf4-106">The settings can be grouped in the following categories:</span></span>  
  
-   [<span data-ttu-id="aadf4-107">一般設定</span><span class="sxs-lookup"><span data-stu-id="aadf4-107">General Settings</span></span>](#General)  
  
-   [<span data-ttu-id="aadf4-108">版本管理設定</span><span class="sxs-lookup"><span data-stu-id="aadf4-108">Version Management Settings</span></span>](#Versions)  
  
-   [<span data-ttu-id="aadf4-109">預備設定</span><span class="sxs-lookup"><span data-stu-id="aadf4-109">Staging Settings</span></span>](#Staging)  
  
-   [<span data-ttu-id="aadf4-110">Explorer 設定</span><span class="sxs-lookup"><span data-stu-id="aadf4-110">Explorer Settings</span></span>](#Explorer)  
  
-   [<span data-ttu-id="aadf4-111">Excel 增益集設定</span><span class="sxs-lookup"><span data-stu-id="aadf4-111">Add-in for Excel Settings</span></span>](#xls)  
  
-   [<span data-ttu-id="aadf4-112">商務規則設定</span><span class="sxs-lookup"><span data-stu-id="aadf4-112">Business Rule Settings</span></span>](#BusinessRules)  
  
-   [<span data-ttu-id="aadf4-113">通知設定</span><span class="sxs-lookup"><span data-stu-id="aadf4-113">Notification Settings</span></span>](#Notifications)  
  
-   [<span data-ttu-id="aadf4-114">安全性設定</span><span class="sxs-lookup"><span data-stu-id="aadf4-114">Security Settings</span></span>](#Security)  
  
-   [<span data-ttu-id="aadf4-115">未使用</span><span class="sxs-lookup"><span data-stu-id="aadf4-115">Not Used</span></span>](#NotUsed)  
  
##  <a name="general-settings"></a><a name="General"></a><span data-ttu-id="aadf4-116">一般設定</span><span class="sxs-lookup"><span data-stu-id="aadf4-116">General Settings</span></span>  
  
|<span data-ttu-id="aadf4-117">組態管理員設定</span><span class="sxs-lookup"><span data-stu-id="aadf4-117">Configuration Manager Setting</span></span>|<span data-ttu-id="aadf4-118">系統設定</span><span class="sxs-lookup"><span data-stu-id="aadf4-118">System Setting</span></span>|<span data-ttu-id="aadf4-119">描述</span><span class="sxs-lookup"><span data-stu-id="aadf4-119">Description</span></span>|  
|-----------------------------------|--------------------|-----------------|  
|<span data-ttu-id="aadf4-120">**資料庫連接逾時**</span><span class="sxs-lookup"><span data-stu-id="aadf4-120">**Database connection time-out**</span></span>|<span data-ttu-id="aadf4-121">**DatabaseConnectionTimeOut**</span><span class="sxs-lookup"><span data-stu-id="aadf4-121">**DatabaseConnectionTimeOut**</span></span>|<span data-ttu-id="aadf4-122">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 資料庫允許連接完成的秒數。</span><span class="sxs-lookup"><span data-stu-id="aadf4-122">The number of seconds the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database allows for a connection to complete.</span></span> <span data-ttu-id="aadf4-123">如果連接未在此時間內完成，則會取消連接並傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="aadf4-123">If the connection does not complete within this time, the connection is cancelled and an error is returned.</span></span> <span data-ttu-id="aadf4-124">預設值為 **60** 秒 (1 分鐘)。</span><span class="sxs-lookup"><span data-stu-id="aadf4-124">The default value is **60** seconds (1 minute).</span></span>|  
|<span data-ttu-id="aadf4-125">**資料庫命令逾時**</span><span class="sxs-lookup"><span data-stu-id="aadf4-125">**Database command time-out**</span></span>|<span data-ttu-id="aadf4-126">**DatabaseCommandTimeOut**</span><span class="sxs-lookup"><span data-stu-id="aadf4-126">**DatabaseCommandTimeOut**</span></span>|<span data-ttu-id="aadf4-127">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 資料庫允許命令完成的秒數。</span><span class="sxs-lookup"><span data-stu-id="aadf4-127">The number of seconds the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database allows for a command to complete.</span></span> <span data-ttu-id="aadf4-128">如果命令未在此時間內完成，則會取消命令並傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="aadf4-128">If the command does not complete within this time, the command is cancelled and an error is returned.</span></span> <span data-ttu-id="aadf4-129">預設值為 **3600** 秒 (60 分鐘)。</span><span class="sxs-lookup"><span data-stu-id="aadf4-129">The default value is **3600** seconds (60 minutes).</span></span>|  
|<span data-ttu-id="aadf4-130">**Web 服務逾時**</span><span class="sxs-lookup"><span data-stu-id="aadf4-130">**Web service time-out**</span></span>|<span data-ttu-id="aadf4-131">**ServerTimeOut**</span><span class="sxs-lookup"><span data-stu-id="aadf4-131">**ServerTimeOut**</span></span>|<span data-ttu-id="aadf4-132">ASP.NET 允許 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 頁面要求完成的秒數。</span><span class="sxs-lookup"><span data-stu-id="aadf4-132">The number of seconds ASP.NET allows for a [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] page request to complete.</span></span> <span data-ttu-id="aadf4-133">如果要求未在此時間內完成，則會取消要求並傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="aadf4-133">If the request does not complete within this time, the request is cancelled and an error is returned.</span></span> <span data-ttu-id="aadf4-134">預設值為 **120000** 秒 (2000 分鐘)。</span><span class="sxs-lookup"><span data-stu-id="aadf4-134">The default value is **120000** seconds (2000 minutes).</span></span>|  
|<span data-ttu-id="aadf4-135">**用戶端逾時**</span><span class="sxs-lookup"><span data-stu-id="aadf4-135">**Client time-out**</span></span>|<span data-ttu-id="aadf4-136">**ClientTimeOut**</span><span class="sxs-lookup"><span data-stu-id="aadf4-136">**ClientTimeOut**</span></span>|<span data-ttu-id="aadf4-137">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 返回到首頁之前非使用狀態的秒數。</span><span class="sxs-lookup"><span data-stu-id="aadf4-137">The number of seconds of inactivity before [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] returns to the home page.</span></span> <span data-ttu-id="aadf4-138">預設值為 **300** 秒 (5 分鐘)。</span><span class="sxs-lookup"><span data-stu-id="aadf4-138">The default value is **300** seconds (5 minutes).</span></span>|  
|<span data-ttu-id="aadf4-139">**每批次的資料列數目**</span><span class="sxs-lookup"><span data-stu-id="aadf4-139">**Number of rows per batch**</span></span>|<span data-ttu-id="aadf4-140">**RowsPerBatch**</span><span class="sxs-lookup"><span data-stu-id="aadf4-140">**RowsPerBatch**</span></span>|<span data-ttu-id="aadf4-141">Web 服務傳回之每個批次中所要擷取的記錄數目。</span><span class="sxs-lookup"><span data-stu-id="aadf4-141">The number of records to retrieve in each batch by the web service.</span></span> <span data-ttu-id="aadf4-142">預設值為**50**。</span><span class="sxs-lookup"><span data-stu-id="aadf4-142">The default value is **50**.</span></span>|  
||<span data-ttu-id="aadf4-143">**ApplicationName**</span><span class="sxs-lookup"><span data-stu-id="aadf4-143">**ApplicationName**</span></span>|<span data-ttu-id="aadf4-144">事件記錄檔中顯示的文字。</span><span class="sxs-lookup"><span data-stu-id="aadf4-144">The text that is displayed in event logs.</span></span> <span data-ttu-id="aadf4-145">預設值為 **MDM**。</span><span class="sxs-lookup"><span data-stu-id="aadf4-145">The default value is **MDM**.</span></span>|  
||<span data-ttu-id="aadf4-146">**SiteTitle**</span><span class="sxs-lookup"><span data-stu-id="aadf4-146">**SiteTitle**</span></span>|<span data-ttu-id="aadf4-147">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web 瀏覽器標題列中顯示的文字。</span><span class="sxs-lookup"><span data-stu-id="aadf4-147">The text that is displayed in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web browser's title bar.</span></span> <span data-ttu-id="aadf4-148">預設值為 [主資料管理員]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="aadf4-148">The default value is **Master Data Manager**.</span></span>|  
  
##  <a name="version-management-settings"></a><a name="Versions"></a> <span data-ttu-id="aadf4-149">版本管理設定</span><span class="sxs-lookup"><span data-stu-id="aadf4-149">Version Management Settings</span></span>  
  
|<span data-ttu-id="aadf4-150">組態管理員設定</span><span class="sxs-lookup"><span data-stu-id="aadf4-150">Configuration Manager Setting</span></span>|<span data-ttu-id="aadf4-151">系統設定</span><span class="sxs-lookup"><span data-stu-id="aadf4-151">System Setting</span></span>|<span data-ttu-id="aadf4-152">描述</span><span class="sxs-lookup"><span data-stu-id="aadf4-152">Description</span></span>|  
|-----------------------------------|--------------------|-----------------|  
|<span data-ttu-id="aadf4-153">**僅複製認可的版本**</span><span class="sxs-lookup"><span data-stu-id="aadf4-153">**Copy only committed versions**</span></span>|<span data-ttu-id="aadf4-154">**CopyOnlyCommittedVersion**</span><span class="sxs-lookup"><span data-stu-id="aadf4-154">**CopyOnlyCommittedVersion**</span></span>|<span data-ttu-id="aadf4-155">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 中，決定使用者是否可以複製狀態為 [已認可]\*\*\*\* 的模型版本，或是複製任何狀態的版本。</span><span class="sxs-lookup"><span data-stu-id="aadf4-155">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], determines whether users can copy model versions with a status of **Committed**, or versions with any status.</span></span> <span data-ttu-id="aadf4-156">預設值是 [是]\*\*\*\* 或 **1**，表示使用者只能複製 [已認可]\*\*\*\* 的版本。</span><span class="sxs-lookup"><span data-stu-id="aadf4-156">The default value is **Yes** or **1**, which indicates that users can copy **Committed** versions only.</span></span> <span data-ttu-id="aadf4-157">變更為 [否]\*\*\*\* 或 **2** 則會允許使用者複製所有版本。</span><span class="sxs-lookup"><span data-stu-id="aadf4-157">Change to **No** or **2** to allow users to copy all versions.</span></span>|  
  
 <span data-ttu-id="aadf4-158">如需詳細資訊，請參閱[版本 &#40;Master Data Services&#41;](versions-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="aadf4-158">For more information, see [Versions &#40;Master Data Services&#41;](versions-master-data-services.md).</span></span>  
  
##  <a name="staging-settings"></a><a name="Staging"></a> <span data-ttu-id="aadf4-159">暫存設定</span><span class="sxs-lookup"><span data-stu-id="aadf4-159">Staging Settings</span></span>  
  
|<span data-ttu-id="aadf4-160">組態管理員設定</span><span class="sxs-lookup"><span data-stu-id="aadf4-160">Configuration Manager Setting</span></span>|<span data-ttu-id="aadf4-161">系統設定</span><span class="sxs-lookup"><span data-stu-id="aadf4-161">System Setting</span></span>|<span data-ttu-id="aadf4-162">描述</span><span class="sxs-lookup"><span data-stu-id="aadf4-162">Description</span></span>|  
|-----------------------------------|--------------------|-----------------|  
|<span data-ttu-id="aadf4-163">**記錄所有暫存交易**</span><span class="sxs-lookup"><span data-stu-id="aadf4-163">**Log all staging transactions**</span></span>|<span data-ttu-id="aadf4-164">**StagingTransactionLogging**</span><span class="sxs-lookup"><span data-stu-id="aadf4-164">**StagingTransactionLogging**</span></span>|<span data-ttu-id="aadf4-165">僅適用於 SQL Server 2008 R2。</span><span class="sxs-lookup"><span data-stu-id="aadf4-165">Applies to SQL Server 2008 R2 only.</span></span> <span data-ttu-id="aadf4-166">決定在將暫存記錄載入 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 資料庫時，是否要記錄交易。</span><span class="sxs-lookup"><span data-stu-id="aadf4-166">Determines whether or not transactions are logged when staging records are loaded into the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="aadf4-167">預設值是 [關閉]\*\*\*\* 或 **2**。</span><span class="sxs-lookup"><span data-stu-id="aadf4-167">The default value is **Off** or **2**.</span></span> <span data-ttu-id="aadf4-168">變更為 [開啟]\*\*\*\* 或 **1** 則會開啟記錄功能。</span><span class="sxs-lookup"><span data-stu-id="aadf4-168">Change to **On** or **1** to turn on logging.</span></span>|  
|<span data-ttu-id="aadf4-169">**暫存批次間隔**</span><span class="sxs-lookup"><span data-stu-id="aadf4-169">**Staging batch interval**</span></span>|<span data-ttu-id="aadf4-170">**StagingBatchInterval**</span><span class="sxs-lookup"><span data-stu-id="aadf4-170">**StagingBatchInterval**</span></span>|<span data-ttu-id="aadf4-171">在  [整合管理][!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] \*\*\*\* 功能區域中，從選取 [啟動批次]\*\*\*\* 後到開始處理批次前所經過的秒數。</span><span class="sxs-lookup"><span data-stu-id="aadf4-171">In the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] **Integration Management** functional area, the number of seconds after you select **Start Batches** that your batch is processed.</span></span> <span data-ttu-id="aadf4-172">預設值為 **60** 秒 (1 分鐘)。</span><span class="sxs-lookup"><span data-stu-id="aadf4-172">The default value is **60** seconds (1 minute).</span></span>|  
  
 <span data-ttu-id="aadf4-173">如需詳細資訊，請參閱[資料匯入 &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="aadf4-173">For more information, see [Data Import &#40;Master Data Services&#41;](overview-importing-data-from-tables-master-data-services.md).</span></span>  
  
##  <a name="explorer-settings"></a><a name="Explorer"></a> <span data-ttu-id="aadf4-174">總管設定</span><span class="sxs-lookup"><span data-stu-id="aadf4-174">Explorer Settings</span></span>  
  
|<span data-ttu-id="aadf4-175">組態管理員設定</span><span class="sxs-lookup"><span data-stu-id="aadf4-175">Configuration Manager Setting</span></span>|<span data-ttu-id="aadf4-176">系統設定</span><span class="sxs-lookup"><span data-stu-id="aadf4-176">System Setting</span></span>|<span data-ttu-id="aadf4-177">描述</span><span class="sxs-lookup"><span data-stu-id="aadf4-177">Description</span></span>|  
|-----------------------------------|--------------------|-----------------|  
|<span data-ttu-id="aadf4-178">**階層中預設的成員數目**</span><span class="sxs-lookup"><span data-stu-id="aadf4-178">**Number of members in the hierarchy by default**</span></span>|<span data-ttu-id="aadf4-179">**HierarchyChildNodeLimit**</span><span class="sxs-lookup"><span data-stu-id="aadf4-179">**HierarchyChildNodeLimit**</span></span>|<span data-ttu-id="aadf4-180">在的 [檔案總管][!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] \*\*\*\* 功能區域中，於顯示 [...其他...]\*\*\*\* 之前，每個階層節點中所顯示的成員數目上限。</span><span class="sxs-lookup"><span data-stu-id="aadf4-180">In the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] **Explorer** functional area, the maximum number of members that are displayed in each hierarchy node before **...more...** is displayed.</span></span> <span data-ttu-id="aadf4-181">您可以按一下 [...其他...]\*\*\*\* 來顯示下一個成員群組。</span><span class="sxs-lookup"><span data-stu-id="aadf4-181">You can click **...more...** to show the next group of members.</span></span> <span data-ttu-id="aadf4-182">預設值為**50**。</span><span class="sxs-lookup"><span data-stu-id="aadf4-182">The default value is **50**.</span></span>|  
|<span data-ttu-id="aadf4-183">**顯示階層中預設的名稱**</span><span class="sxs-lookup"><span data-stu-id="aadf4-183">**Show names in hierarchy by default**</span></span>|<span data-ttu-id="aadf4-184">**ShowNamesInHierarchy**</span><span class="sxs-lookup"><span data-stu-id="aadf4-184">**ShowNamesInHierarchy**</span></span>|<span data-ttu-id="aadf4-185">在  總管[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] \*\*\*\* 功能區域中，決定檢視階層時所選取的預設設定。</span><span class="sxs-lookup"><span data-stu-id="aadf4-185">In the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] **Explorer** functional area, determines the default setting that is selected when you view hierarchies.</span></span><br /><br /> <span data-ttu-id="aadf4-186">預設值是 [是]\*\*\*\* 或 **1**，表示每個成員的名稱和程式碼都會顯示。</span><span class="sxs-lookup"><span data-stu-id="aadf4-186">The default value is **Yes** or **1**, which indicates that the name and code of each member are displayed.</span></span> <span data-ttu-id="aadf4-187">變更為 [否]\*\*\*\* 或 **2** 則只會顯示程式碼。</span><span class="sxs-lookup"><span data-stu-id="aadf4-187">Change to **No** or **2** to display the code only.</span></span>|  
|<span data-ttu-id="aadf4-188">**清單中網域屬性的數目**</span><span class="sxs-lookup"><span data-stu-id="aadf4-188">**Number of domain-based attributes in list**</span></span>|<span data-ttu-id="aadf4-189">**DBAListRowLimit**</span><span class="sxs-lookup"><span data-stu-id="aadf4-189">**DBAListRowLimit**</span></span>|<span data-ttu-id="aadf4-190">在  總管[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] \*\*\*\* 功能區域中，當您按兩下方格中的網域屬性值時所顯示的屬性數目。</span><span class="sxs-lookup"><span data-stu-id="aadf4-190">In the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] **Explorer** functional area, the number of attributes that are displayed in a list when you double-click a domain-based attribute value in the grid.</span></span> <span data-ttu-id="aadf4-191">預設值為**50**。</span><span class="sxs-lookup"><span data-stu-id="aadf4-191">The default value is **50**.</span></span> <span data-ttu-id="aadf4-192">如果有超過 50 個成員存在，則會改為顯示可搜尋對話方塊。</span><span class="sxs-lookup"><span data-stu-id="aadf4-192">If more than 50 members exist, a searchable dialog is displayed instead.</span></span>|  
||<span data-ttu-id="aadf4-193">**GridFilterDefaultFuzzySimilarityLevel**</span><span class="sxs-lookup"><span data-stu-id="aadf4-193">**GridFilterDefaultFuzzySimilarityLevel**</span></span>|<span data-ttu-id="aadf4-194">在  總管[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] \*\*\*\* 功能區域中，使用 [比對]\*\*\*\* 篩選準則時所使用的相似度層級。</span><span class="sxs-lookup"><span data-stu-id="aadf4-194">In the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] **Explorer** functional area, the level of similarity used when using the **Matches** filter criteria.</span></span> <span data-ttu-id="aadf4-195">預設值是 **0.3**。</span><span class="sxs-lookup"><span data-stu-id="aadf4-195">The default value is **0.3**.</span></span> <span data-ttu-id="aadf4-196">設定的值愈接近 **1** ，傳回的相符項目就愈接近搜尋準則。</span><span class="sxs-lookup"><span data-stu-id="aadf4-196">Set the value closer to **1** to return a match that is closer to the search criteria.</span></span> <span data-ttu-id="aadf4-197">設定成 **1** 則會傳回完全相符的項目。</span><span class="sxs-lookup"><span data-stu-id="aadf4-197">Set to **1** for an exact match.</span></span>|  
  
##  <a name="add-in-for-excel-settings"></a><a name="xls"></a><span data-ttu-id="aadf4-198">適用于 Excel 的增益集設定</span><span class="sxs-lookup"><span data-stu-id="aadf4-198">Add-in for Excel Settings</span></span>  
  
|<span data-ttu-id="aadf4-199">組態管理員設定</span><span class="sxs-lookup"><span data-stu-id="aadf4-199">Configuration Manager Setting</span></span>|<span data-ttu-id="aadf4-200">系統設定</span><span class="sxs-lookup"><span data-stu-id="aadf4-200">System Setting</span></span>|<span data-ttu-id="aadf4-201">描述</span><span class="sxs-lookup"><span data-stu-id="aadf4-201">Description</span></span>|  
|-----------------------------------|--------------------|-----------------|  
|<span data-ttu-id="aadf4-202">在網站首頁上顯示 Excel 增益集的文字</span><span class="sxs-lookup"><span data-stu-id="aadf4-202">Show Add-in for Excel text on website home page</span></span>|<span data-ttu-id="aadf4-203">ShowAddInText</span><span class="sxs-lookup"><span data-stu-id="aadf4-203">ShowAddInText</span></span>|<span data-ttu-id="aadf4-204">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 首頁上，顯示讓使用者下載 [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]的連結。</span><span class="sxs-lookup"><span data-stu-id="aadf4-204">On the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] home page, show a link for users to download the [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)].</span></span>|  
|<span data-ttu-id="aadf4-205">網站首頁 Excel 增益集的安裝路徑</span><span class="sxs-lookup"><span data-stu-id="aadf4-205">Add-in for Excel install path on website home page</span></span>|<span data-ttu-id="aadf4-206">AddInURL</span><span class="sxs-lookup"><span data-stu-id="aadf4-206">AddInURL</span></span>|<span data-ttu-id="aadf4-207">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 首頁上，如果顯示指向 [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] 的連結，則是使用者按一下連結之後前往的位置。</span><span class="sxs-lookup"><span data-stu-id="aadf4-207">On the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] home page, if the link to the [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] is displayed, the location users go to when they click the link.</span></span>|  
  
##  <a name="business-rule-settings"></a><a name="BusinessRules"></a> <span data-ttu-id="aadf4-208">商務規則設定</span><span class="sxs-lookup"><span data-stu-id="aadf4-208">Business Rule Settings</span></span>  
  
|<span data-ttu-id="aadf4-209">組態管理員設定</span><span class="sxs-lookup"><span data-stu-id="aadf4-209">Configuration Manager Setting</span></span>|<span data-ttu-id="aadf4-210">系統設定</span><span class="sxs-lookup"><span data-stu-id="aadf4-210">System Setting</span></span>|<span data-ttu-id="aadf4-211">描述</span><span class="sxs-lookup"><span data-stu-id="aadf4-211">Description</span></span>|  
|-----------------------------------|--------------------|-----------------|  
|<span data-ttu-id="aadf4-212">**要遞增新商務規則的數目依據**</span><span class="sxs-lookup"><span data-stu-id="aadf4-212">**Number to increment new business rules by**</span></span>|<span data-ttu-id="aadf4-213">**BusinessRuleDefaultPriorityIncrement**</span><span class="sxs-lookup"><span data-stu-id="aadf4-213">**BusinessRuleDefaultPriorityIncrement**</span></span>|<span data-ttu-id="aadf4-214">在  [系統管理][!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] \*\*\*\* 功能區域中，每個新商務規則之優先順序遞增的數目。</span><span class="sxs-lookup"><span data-stu-id="aadf4-214">In the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] **System Administration** functional area, the number the priority of each new business rule is incremented by.</span></span> <span data-ttu-id="aadf4-215">預設值為 **10**。</span><span class="sxs-lookup"><span data-stu-id="aadf4-215">The default value is **10**.</span></span>|  
|<span data-ttu-id="aadf4-216">**要套用商務規則的成員數目**</span><span class="sxs-lookup"><span data-stu-id="aadf4-216">**Number of members to apply business rules to**</span></span>|<span data-ttu-id="aadf4-217">**BusinessRuleRealtimeMemberCount**</span><span class="sxs-lookup"><span data-stu-id="aadf4-217">**BusinessRuleRealtimeMemberCount**</span></span>|<span data-ttu-id="aadf4-218">在  總管[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] \*\*\*\* 功能區域中，方格中要套用商務規則的成員數目上限。</span><span class="sxs-lookup"><span data-stu-id="aadf4-218">In the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] **Explorer** functional area, the maximum number of members in the grid to apply business rules to.</span></span> <span data-ttu-id="aadf4-219">在 [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]中，使用中工作表中要套用商務規則的成員數目上限。</span><span class="sxs-lookup"><span data-stu-id="aadf4-219">In the [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)], the maximum number of members in the active worksheet to apply business rules to.</span></span> <span data-ttu-id="aadf4-220">預設值為**10000**。</span><span class="sxs-lookup"><span data-stu-id="aadf4-220">The default value is **10000**.</span></span>|  
  
 <span data-ttu-id="aadf4-221">如需詳細資訊，請參閱[商務規則 &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="aadf4-221">For more information, see [Business Rules &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md).</span></span>  
  
##  <a name="notification-settings"></a><a name="Notifications"></a><span data-ttu-id="aadf4-222">通知設定</span><span class="sxs-lookup"><span data-stu-id="aadf4-222">Notification Settings</span></span>  
  
|<span data-ttu-id="aadf4-223">組態管理員設定</span><span class="sxs-lookup"><span data-stu-id="aadf4-223">Configuration Manager Setting</span></span>|<span data-ttu-id="aadf4-224">系統設定</span><span class="sxs-lookup"><span data-stu-id="aadf4-224">System Setting</span></span>|<span data-ttu-id="aadf4-225">描述</span><span class="sxs-lookup"><span data-stu-id="aadf4-225">Description</span></span>|  
|-----------------------------------|--------------------|-----------------|  
|<span data-ttu-id="aadf4-226">**通知的主資料管理員 URL**</span><span class="sxs-lookup"><span data-stu-id="aadf4-226">**Master Data Manager URL for notifications**</span></span>|<span data-ttu-id="aadf4-227">**MDMRootURL**</span><span class="sxs-lookup"><span data-stu-id="aadf4-227">**MDMRootURL**</span></span>|<span data-ttu-id="aadf4-228">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web 應用程式的 URL，其為電子郵件通知中所用的連結，例如 http://constoso/mds。</span><span class="sxs-lookup"><span data-stu-id="aadf4-228">The URL for the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application, which is used in the link in email notifications, for example http://constoso/mds.</span></span>|  
|<span data-ttu-id="aadf4-229">**通知電子郵件間隔**</span><span class="sxs-lookup"><span data-stu-id="aadf4-229">**Notification email interval**</span></span>|<span data-ttu-id="aadf4-230">**NotificationInterval**</span><span class="sxs-lookup"><span data-stu-id="aadf4-230">**NotificationInterval**</span></span>|<span data-ttu-id="aadf4-231">傳送電子郵件的頻率 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="aadf4-231">The frequency, in seconds, that email notifications are sent.</span></span> <span data-ttu-id="aadf4-232">預設值為 **120** 秒 (2 分鐘)。</span><span class="sxs-lookup"><span data-stu-id="aadf4-232">The default value is **120** seconds (2 minutes).</span></span>|  
|<span data-ttu-id="aadf4-233">**單一電子郵件中的通知數**</span><span class="sxs-lookup"><span data-stu-id="aadf4-233">**Number of notifications in a single email**</span></span>|<span data-ttu-id="aadf4-234">**NotificationsPerEmail**</span><span class="sxs-lookup"><span data-stu-id="aadf4-234">**NotificationsPerEmail**</span></span>|<span data-ttu-id="aadf4-235">將在單一通知電子郵件中列出的驗證問題最大數目。</span><span class="sxs-lookup"><span data-stu-id="aadf4-235">The maximum number of validation issues that will be listed in a single notification email.</span></span> <span data-ttu-id="aadf4-236">如果存在其他問題，則這些問題將不包含在該電子郵件中，但會在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中提供。</span><span class="sxs-lookup"><span data-stu-id="aadf4-236">Additional issues, if they exist, are not included in the email, but are available in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span>|  
|<span data-ttu-id="aadf4-237">**預設電子郵件格式**</span><span class="sxs-lookup"><span data-stu-id="aadf4-237">**Default email format**</span></span>|<span data-ttu-id="aadf4-238">**EmailFormat**</span><span class="sxs-lookup"><span data-stu-id="aadf4-238">**EmailFormat**</span></span>|<span data-ttu-id="aadf4-239">所有電子郵件通知的格式。</span><span class="sxs-lookup"><span data-stu-id="aadf4-239">The format for all email notifications.</span></span> <span data-ttu-id="aadf4-240">預設值是 **HTML** 或 **1**。</span><span class="sxs-lookup"><span data-stu-id="aadf4-240">The default value is **HTML** or **1**.</span></span> <span data-ttu-id="aadf4-241">資料庫設定 **2** 表示 [文字]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="aadf4-241">The database setting of **2** indicates **Text**.</span></span><br /><br /> <span data-ttu-id="aadf4-242">注意：您可以在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 中覆寫個別使用者的此項目，方式為在使用者的 [一般]\*\*\*\* 索引標籤上變更並儲存 [電子郵件格式]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="aadf4-242">Note: You can override this for an individual user in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], by changing and saving the **Email format** on the user's **General** tab.</span></span>|  
|<span data-ttu-id="aadf4-243">**電子郵件地址的規則運算式**</span><span class="sxs-lookup"><span data-stu-id="aadf4-243">**Regular expression for email address**</span></span>|<span data-ttu-id="aadf4-244">**EmailRegExPattern**</span><span class="sxs-lookup"><span data-stu-id="aadf4-244">**EmailRegExPattern**</span></span>|<span data-ttu-id="aadf4-245">在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] **使用者和群組的許可權**] 功能區域中，用來驗證在使用者 **[一般**] 索引標籤上輸入之電子郵件地址的正則運算式。如需正則運算式的詳細資訊，請參閱 MSDN library 中的[正則運算式語言元素](https://go.microsoft.com/fwlink/?LinkId=164401)。</span><span class="sxs-lookup"><span data-stu-id="aadf4-245">In the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] **User and Group Permissions** functional area, the regular expression used to validate the email address entered on a user's **General** tab. For more information about regular expressions, see [Regular Expression Language Elements](https://go.microsoft.com/fwlink/?LinkId=164401) in the MSDN library.</span></span>|  
|<span data-ttu-id="aadf4-246">**Database Mail 帳戶**</span><span class="sxs-lookup"><span data-stu-id="aadf4-246">**Database Mail account**</span></span>|<span data-ttu-id="aadf4-247">**EmailProfilePrincipalAccount**</span><span class="sxs-lookup"><span data-stu-id="aadf4-247">**EmailProfilePrincipalAccount**</span></span>|<span data-ttu-id="aadf4-248">顯示傳送電子郵件通知時所要使用的 Database Mail 帳戶。</span><span class="sxs-lookup"><span data-stu-id="aadf4-248">Displays the Database Mail account to use when sending email notifications.</span></span> <span data-ttu-id="aadf4-249">預設的設定檔是 **mds_email_user**。</span><span class="sxs-lookup"><span data-stu-id="aadf4-249">The default profile is **mds_email_user**.</span></span>|  
|<span data-ttu-id="aadf4-250">**Database Mail 設定檔**</span><span class="sxs-lookup"><span data-stu-id="aadf4-250">**Database Mail profile**</span></span>|<span data-ttu-id="aadf4-251">**DatabaseMailProfile**</span><span class="sxs-lookup"><span data-stu-id="aadf4-251">**DatabaseMailProfile**</span></span>|<span data-ttu-id="aadf4-252">傳送電子郵件通知時所要使用的 Database Mail 設定檔。</span><span class="sxs-lookup"><span data-stu-id="aadf4-252">The Database Mail profile to use when sending email notifications.</span></span> <span data-ttu-id="aadf4-253">預設值是空白。</span><span class="sxs-lookup"><span data-stu-id="aadf4-253">The default value is blank.</span></span>|  
||<span data-ttu-id="aadf4-254">**ValidationIssueHTML**</span><span class="sxs-lookup"><span data-stu-id="aadf4-254">**ValidationIssueHTML**</span></span>|<span data-ttu-id="aadf4-255">當商務規則驗證失敗時，使用者所取得 HTML 格式的電子郵件文字。</span><span class="sxs-lookup"><span data-stu-id="aadf4-255">In HTML format, the text of the email users get when a business rule fails validation.</span></span>|  
||<span data-ttu-id="aadf4-256">**ValidationIssueText**</span><span class="sxs-lookup"><span data-stu-id="aadf4-256">**ValidationIssueText**</span></span>|<span data-ttu-id="aadf4-257">當商務規則驗證失敗時，使用者所取得純文字格式的電子郵件文字。</span><span class="sxs-lookup"><span data-stu-id="aadf4-257">In plain text format, the text of the email users get when a business rule fails validation.</span></span>|  
||<span data-ttu-id="aadf4-258">**VersionStatusChangeText**</span><span class="sxs-lookup"><span data-stu-id="aadf4-258">**VersionStatusChangeText**</span></span>|<span data-ttu-id="aadf4-259">當版本狀態變更時，使用者所取得純文字格式的電子郵件文字。</span><span class="sxs-lookup"><span data-stu-id="aadf4-259">In plain text format, the text of the email users get when the status of a version changes.</span></span> <span data-ttu-id="aadf4-260">只有具有整個模型之 [更新]\*\*\*\* 權限的使用者才會收到此電子郵件。</span><span class="sxs-lookup"><span data-stu-id="aadf4-260">Only users with **Update** permission to the entire model receive this email.</span></span>|  
||<span data-ttu-id="aadf4-261">**VersionStatusChangeHTML**</span><span class="sxs-lookup"><span data-stu-id="aadf4-261">**VersionStatusChangeHTML**</span></span>|<span data-ttu-id="aadf4-262">當版本狀態變更時，使用者所取得 HTML 格式的電子郵件文字。</span><span class="sxs-lookup"><span data-stu-id="aadf4-262">In HTML format, the text of the email users get when the status of a version changes.</span></span> <span data-ttu-id="aadf4-263">只有具有整個模型之 [更新]\*\*\*\* 權限的使用者才會收到此電子郵件。</span><span class="sxs-lookup"><span data-stu-id="aadf4-263">Only users with **Update** permission to the entire model receive this email.</span></span>|  
  
 <span data-ttu-id="aadf4-264">如需詳細資訊，請參閱[通知 &#40;Master Data Services&#41;](../../2014/master-data-services/notifications-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="aadf4-264">For more information, see [Notifications &#40;Master Data Services&#41;](../../2014/master-data-services/notifications-master-data-services.md).</span></span>  
  
##  <a name="security-settings"></a><a name="Security"></a><span data-ttu-id="aadf4-265">安全性設定</span><span class="sxs-lookup"><span data-stu-id="aadf4-265">Security Settings</span></span>  
  
|<span data-ttu-id="aadf4-266">組態管理員設定</span><span class="sxs-lookup"><span data-stu-id="aadf4-266">Configuration Manager Setting</span></span>|<span data-ttu-id="aadf4-267">系統設定</span><span class="sxs-lookup"><span data-stu-id="aadf4-267">System Setting</span></span>|<span data-ttu-id="aadf4-268">描述</span><span class="sxs-lookup"><span data-stu-id="aadf4-268">Description</span></span>|  
|-----------------------------------|--------------------|-----------------|  
||<span data-ttu-id="aadf4-269">**SecurityMemberProcessInterval**</span><span class="sxs-lookup"><span data-stu-id="aadf4-269">**SecurityMemberProcessInterval**</span></span>|<span data-ttu-id="aadf4-270">在  [使用者及群組的權限][!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] \*\*\*\* 功能區域中，[階層成員]\*\*\*\* 索引標籤上設定之使用者和群組權限的套用頻率 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="aadf4-270">In the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] **User and Group Permissions** functional area, the frequency, in seconds, that user and group permissions set on the **Hierarchy Members** tab are applied.</span></span> <span data-ttu-id="aadf4-271">預設值為 **3600** 秒 (60 分鐘)。</span><span class="sxs-lookup"><span data-stu-id="aadf4-271">The default value is **3600** seconds (60 minutes).</span></span>|  
  
 <span data-ttu-id="aadf4-272">如需詳細資訊，請參閱[立即套用成員權限 &#40;Master Data Services&#41;](../../2014/master-data-services/immediately-apply-member-permissions-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="aadf4-272">For more information, see [Immediately Apply Member Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/immediately-apply-member-permissions-master-data-services.md).</span></span>  
  
##  <a name="not-used"></a><a name="NotUsed"></a><span data-ttu-id="aadf4-273">未使用</span><span class="sxs-lookup"><span data-stu-id="aadf4-273">Not Used</span></span>  
 <span data-ttu-id="aadf4-274">[系統設定] 資料表中不使用下列設定。</span><span class="sxs-lookup"><span data-stu-id="aadf4-274">The following settings in the System Settings table are not used.</span></span>  
  
-   <span data-ttu-id="aadf4-275">**SecurityMode**</span><span class="sxs-lookup"><span data-stu-id="aadf4-275">**SecurityMode**</span></span>  
  
-   <span data-ttu-id="aadf4-276">**MDSHubName**</span><span class="sxs-lookup"><span data-stu-id="aadf4-276">**MDSHubName**</span></span>  
  
-   <span data-ttu-id="aadf4-277">**ApplicationLogging**</span><span class="sxs-lookup"><span data-stu-id="aadf4-277">**ApplicationLogging**</span></span>  
  
-   <span data-ttu-id="aadf4-278">**ReportServer**</span><span class="sxs-lookup"><span data-stu-id="aadf4-278">**ReportServer**</span></span>  
  
-   <span data-ttu-id="aadf4-279">**ReportDirectory**</span><span class="sxs-lookup"><span data-stu-id="aadf4-279">**ReportDirectory**</span></span>  
  
-   <span data-ttu-id="aadf4-280">**BusinessRuleEngineIterationLimit**</span><span class="sxs-lookup"><span data-stu-id="aadf4-280">**BusinessRuleEngineIterationLimit**</span></span>  
  
-   <span data-ttu-id="aadf4-281">**BusinessRuleExtensibility**</span><span class="sxs-lookup"><span data-stu-id="aadf4-281">**BusinessRuleExtensibility**</span></span>  
  
-   <span data-ttu-id="aadf4-282">**AttributeExplorerMarkAllActionMemberCount**</span><span class="sxs-lookup"><span data-stu-id="aadf4-282">**AttributeExplorerMarkAllActionMemberCount**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aadf4-283">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aadf4-283">See Also</span></span>  
 [<span data-ttu-id="aadf4-284">資料庫物件安全性 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="aadf4-284">Database Object Security &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/database-object-security-master-data-services.md)  
  
  