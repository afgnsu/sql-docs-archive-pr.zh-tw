---
title: 部署檢查清單：將 PowerPivot 服務器加入至 SharePoint 2010 伺服器陣列，以相應放大 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 2dbddcc7-427a-4537-a8e2-56d99b9d967d
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 91a0ff978020c29ecc5c52a336f8b7aab065fc1e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598193"
---
# <a name="deployment-checklist-scale-out-by-adding-powerpivot-servers-to-a-sharepoint-2010-farm"></a><span data-ttu-id="c7a49-102">部署檢查清單：將 PowerPivot 服務器加入至 SharePoint 2010 伺服器陣列，以向外延展</span><span class="sxs-lookup"><span data-stu-id="c7a49-102">Deployment Checklist: Scale-out by adding PowerPivot Servers to a SharePoint 2010 farm</span></span>
  <span data-ttu-id="c7a49-103">如果您預期 SharePoint 伺服器陣列中 PowerPivot 查詢處理有大量的要求，您可以加入額外的 PowerPivot for SharePoint 執行個體，以順暢地新增查詢和資料處理支援。</span><span class="sxs-lookup"><span data-stu-id="c7a49-103">If you anticipate a high volume of requests for PowerPivot query processing in a SharePoint farm, you can add an extra PowerPivot for SharePoint instance to seamlessly add new query and data processing support.</span></span>  
  
 <span data-ttu-id="c7a49-104">安裝新執行個體之後，即會有額外的容量可查詢 PowerPivot 資料或處理 PowerPivot 資料重新整理工作。</span><span class="sxs-lookup"><span data-stu-id="c7a49-104">After you install a new instance, you will have additional capacity for querying PowerPivot data or processing PowerPivot data refresh jobs.</span></span> <span data-ttu-id="c7a49-105">或者，您可以選擇設定每部伺服器處理一種要求類型：查詢或資料重新整理。</span><span class="sxs-lookup"><span data-stu-id="c7a49-105">Optionally, you will have the choice of configuring each server to handle one type of request: query or data refresh.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c7a49-106">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="c7a49-106">Prerequisites</span></span>  
 <span data-ttu-id="c7a49-107">安裝及設定 SharePoint Server 2010。</span><span class="sxs-lookup"><span data-stu-id="c7a49-107">SharePoint Server 2010 is installed and configured.</span></span>  
  
 <span data-ttu-id="c7a49-108">套用 SharePoint Server 2010 SP1 並升級伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="c7a49-108">SharePoint Server 2010 SP1 is applied and the farm is upgraded.</span></span>  
  
 <span data-ttu-id="c7a49-109">伺服器陣列中現有的 PowerPivot for SharePoint 執行個體為 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] (可以是新安裝或升級自 SQL Server 2008 R2)。</span><span class="sxs-lookup"><span data-stu-id="c7a49-109">The existing PowerPivot for SharePoint instance in the farm is [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] (either a new installation or upgraded from SQL Server 2008 R2).</span></span>  
  
 <span data-ttu-id="c7a49-110">將您要安裝新 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] PowerPivot for SharePoint 伺服器的電腦加入伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="c7a49-110">The computer on which you are installing the new [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] PowerPivot for SharePoint server is joined to the farm.</span></span> <span data-ttu-id="c7a49-111">伺服器陣列中的電腦及其他伺服器必須在同一個網域中。</span><span class="sxs-lookup"><span data-stu-id="c7a49-111">The computer and the other servers in the farm must be in the same domain.</span></span>  
  
 <span data-ttu-id="c7a49-112">請檢閱下列其他主題，以了解系統與版本需求：</span><span class="sxs-lookup"><span data-stu-id="c7a49-112">Review the following additional topics to understand system and version requirements:</span></span>  
  
-   [<span data-ttu-id="c7a49-113">在 SharePoint 2010 伺服器陣列中使用 SQL Server BI 功能的指引</span><span class="sxs-lookup"><span data-stu-id="c7a49-113">Guidance for Using SQL Server BI Features in a SharePoint 2010 Farm</span></span>](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md)  
  
> [!NOTE]  
>  <span data-ttu-id="c7a49-114">在多伺服器的伺服器陣列中，所有 PowerPivot for SharePoint 執行個體都必須是相同的版本。</span><span class="sxs-lookup"><span data-stu-id="c7a49-114">In a multi-server farm, all PowerPivot for SharePoint instances must be at the same version.</span></span> <span data-ttu-id="c7a49-115">如果您將 Service Pack 或更新套用到已經在伺服器陣列中的其他 PowerPivot 伺服器，您必須將加入的新執行個體更新為與伺服器陣列中現有執行個體相同的版本。</span><span class="sxs-lookup"><span data-stu-id="c7a49-115">If you applied service packs or updates to other PowerPivot servers that are already in the farm, the new instance you are adding must be updated to the same version as the existing instance that is already in the farm.</span></span> <span data-ttu-id="c7a49-116">套用所有更新之後，才可以使用新的執行個體。</span><span class="sxs-lookup"><span data-stu-id="c7a49-116">The new instance will be unavailable until the updates have been applied.</span></span>  
  
## <a name="steps"></a><span data-ttu-id="c7a49-117">步驟</span><span class="sxs-lookup"><span data-stu-id="c7a49-117">Steps</span></span>  
 <span data-ttu-id="c7a49-118">使用此檢查清單將其他 PowerPivot 伺服器加入至 SharePoint 伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="c7a49-118">Use this checklist to add additional PowerPivot servers to a SharePoint farm.</span></span> <span data-ttu-id="c7a49-119">這些指示假設您已經在伺服器陣列中擁有 PowerPivot for SharePoint 伺服器，而且您要加入第二部伺服器來處理額外的處理負載。</span><span class="sxs-lookup"><span data-stu-id="c7a49-119">These instructions assume that you already have a PowerPivot for SharePoint server in the farm, and that you are adding a second server to handle additional processing load.</span></span> <span data-ttu-id="c7a49-120">除了安裝需求、後續安裝組態和驗證的差異以外，部署向外延展解決方案的步驟都與將單一 PowerPivot 伺服器加入至現有伺服器陣列相同。</span><span class="sxs-lookup"><span data-stu-id="c7a49-120">Except for differences in installation requirements, post-install configuration, and verification, the steps for deploying a scale-out solution are identical to adding a single PowerPivot server to an existing farm.</span></span>  
  
|<span data-ttu-id="c7a49-121">步驟</span><span class="sxs-lookup"><span data-stu-id="c7a49-121">Step</span></span>|<span data-ttu-id="c7a49-122">連結</span><span class="sxs-lookup"><span data-stu-id="c7a49-122">Link</span></span>|  
|----------|----------|  
|<span data-ttu-id="c7a49-123">判斷已經在伺服器陣列中之 Analysis Services 執行個體的服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="c7a49-123">Determine the service account of the Analysis Services instance that is already in the farm</span></span>|<span data-ttu-id="c7a49-124">您安裝的每個額外執行個體，必須與第一個執行個體在相同的帳戶下執行。</span><span class="sxs-lookup"><span data-stu-id="c7a49-124">Each additional instance you install must run under the same account as the first instance.</span></span> <span data-ttu-id="c7a49-125">使用任一個方法來判斷此服務帳戶：</span><span class="sxs-lookup"><span data-stu-id="c7a49-125">Use either approach to determine the service account:</span></span><br /><br /> <span data-ttu-id="c7a49-126">在 [管理中心] 的 [安全性] 區段中，按一下 [**設定服務帳戶**]。</span><span class="sxs-lookup"><span data-stu-id="c7a49-126">In Central Administration, in the Security section, click **Configure Service Accounts**.</span></span> <span data-ttu-id="c7a49-127">選取 [ **Windows 服務-SQL Server Analysis Services**]。</span><span class="sxs-lookup"><span data-stu-id="c7a49-127">Select **Windows Service - SQL Server Analysis Services**.</span></span> <span data-ttu-id="c7a49-128">當您選取此服務之後，服務帳戶名稱將會出現在頁面上。</span><span class="sxs-lookup"><span data-stu-id="c7a49-128">After you select the service, the service account name will appear in the page.</span></span><br /><br /> <span data-ttu-id="c7a49-129">在已經有 PowerPivot 服務安裝的伺服器上，開啟 [系統管理工具] 中的 [**服務**] 主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="c7a49-129">On a server that already has a PowerPivot service installation, open the **Services** console application in Administrative Tools.</span></span> <span data-ttu-id="c7a49-130">按兩下 [ **SQL Server Analysis Services**]。</span><span class="sxs-lookup"><span data-stu-id="c7a49-130">Double-click **SQL Server Analysis Services**.</span></span> <span data-ttu-id="c7a49-131">按一下 [**登**入] 索引標籤以查看服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="c7a49-131">Click the **Log On** tab to view the service account.</span></span><br /><span data-ttu-id="c7a49-132">\*\* \* \* 重要 \* 事項 \* ：\*\* 只使用管理中心來變更服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="c7a49-132">**\*\* Important \*\*** Only use Central Administration to change service accounts.</span></span> <span data-ttu-id="c7a49-133">如果您使用另一個工具或方法，將無法在伺服器陣列中正確更新權限。</span><span class="sxs-lookup"><span data-stu-id="c7a49-133">If you use another tool or approach, permissions will not be updated correctly in the farm.</span></span>|  
|<span data-ttu-id="c7a49-134">執行安裝程式，以安裝第二個 PowerPivot for SharePoint 執行個體。</span><span class="sxs-lookup"><span data-stu-id="c7a49-134">Run Setup to install a second instance of PowerPivot for SharePoint</span></span>|[<span data-ttu-id="c7a49-135">安裝 PowerPivot for SharePoint 2010</span><span class="sxs-lookup"><span data-stu-id="c7a49-135">Install PowerPivot for SharePoint 2010</span></span>](../../../2014/sql-server/install/install-powerpivot-for-sharepoint-2010.md)<br /><br /> <span data-ttu-id="c7a49-136">選擇已加入伺服器陣列、但在伺服器上沒有現有的 PowerPivot 執行個體之應用程式伺服器。</span><span class="sxs-lookup"><span data-stu-id="c7a49-136">Choose an application server that is joined to the farm, but does not have an existing PowerPivot instance on the server.</span></span><br /><br /> <span data-ttu-id="c7a49-137">在安裝期間出現指定服務帳戶的提示時，輸入上一個步驟的帳戶。</span><span class="sxs-lookup"><span data-stu-id="c7a49-137">During Setup, when prompted to specify a service account, enter the account from the previous step.</span></span> <span data-ttu-id="c7a49-138">Analysis Services 服務的所有執行個體必須在相同的網域帳戶下執行。</span><span class="sxs-lookup"><span data-stu-id="c7a49-138">All instances of the Analysis Services service must run under the same domain account.</span></span> <span data-ttu-id="c7a49-139">此需求會啟用 SharePoint 的受管理帳戶功能，好讓您在一個位置為相同類型的所有服務執行個體更新密碼。</span><span class="sxs-lookup"><span data-stu-id="c7a49-139">This requirement enables the use of the managed accounts feature in SharePoint that lets you update the password in one place for all service instances of the same type.</span></span>|  
|<span data-ttu-id="c7a49-140">設定第二個執行個體</span><span class="sxs-lookup"><span data-stu-id="c7a49-140">Configure the second instance</span></span>|<span data-ttu-id="c7a49-141">您可以使用任一種方法來設定實例： [powerpivot 組態工具](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-configuration-tools)或[使用 Windows PowerShell 的 powerpivot](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-configuration-using-windows-powershell)設定</span><span class="sxs-lookup"><span data-stu-id="c7a49-141">You can use either approach to configure the instance: [PowerPivot Configuration Tools](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-configuration-tools) or [PowerPivot Configuration using Windows PowerShell](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-configuration-using-windows-powershell)</span></span><br /><br /> <span data-ttu-id="c7a49-142">設定第二個執行個體時，您只需要佈建本機服務。</span><span class="sxs-lookup"><span data-stu-id="c7a49-142">When configuring a second instance, you only need to provision the local services.</span></span> <span data-ttu-id="c7a49-143">其他所有設定工作 (例如建立服務應用程式或設定資料重新整理) 會在初始組態期間執行，並供您安裝的後續執行個體使用。</span><span class="sxs-lookup"><span data-stu-id="c7a49-143">All other configuration tasks (such as creating service applications or configuring data refresh) are performed during the initial configuration, and used by subsequent instances that you install.</span></span>|  
|<span data-ttu-id="c7a49-144">後續安裝工作</span><span class="sxs-lookup"><span data-stu-id="c7a49-144">Post-installation tasks</span></span>|<span data-ttu-id="c7a49-145">未具體要求後續的步驟。</span><span class="sxs-lookup"><span data-stu-id="c7a49-145">No further steps are specifically required.</span></span> <span data-ttu-id="c7a49-146">您不需要建立服務應用程式、啟動功能、部署方案或是變更服務應用程式識別。</span><span class="sxs-lookup"><span data-stu-id="c7a49-146">You do not need to create service applications, activate features, deploy solutions, or change service application identity.</span></span> <span data-ttu-id="c7a49-147">現有的 Web 應用程式和服務應用程式將會自動探索及使用新的伺服器軟體。</span><span class="sxs-lookup"><span data-stu-id="c7a49-147">Existing Web applications and service applications will discover and use the new server software automatically.</span></span><br /><br /> <span data-ttu-id="c7a49-148">或者，如果您安裝第二部伺服器的目的，是為了讓其中一部伺服器用於查詢，而另一部伺服器用於資料重新整理，您可以立即設定伺服器執行個體屬性，以指定每部伺服器處理的要求類型。</span><span class="sxs-lookup"><span data-stu-id="c7a49-148">Optionally, if you installed a second server for the purpose of using one server for queries and one for data refresh, you can configure server instance properties now to specify the type of requests handled by each server.</span></span> <span data-ttu-id="c7a49-149">如需詳細資訊，請參閱[設定專用資料重新整理或僅查詢處理 &#40;PowerPivot for SharePoint&#41;](../../analysis-services/configure-dedicated-data-refresh-query-only-processing-powerpivot-sharepoint.md)。</span><span class="sxs-lookup"><span data-stu-id="c7a49-149">For more information, see [Configure Dedicated Data Refresh or Query-Only Processing &#40;PowerPivot for SharePoint&#41;](../../analysis-services/configure-dedicated-data-refresh-query-only-processing-powerpivot-sharepoint.md).</span></span>|  
|<span data-ttu-id="c7a49-150">確認第二個執行個體的安裝</span><span class="sxs-lookup"><span data-stu-id="c7a49-150">Verify installation of the second instance</span></span>|<span data-ttu-id="c7a49-151">您可以使用下列步驟，在您剛才安裝的伺服器上驗證 PowerPivot 查詢處理。</span><span class="sxs-lookup"><span data-stu-id="c7a49-151">You can use the following steps to verify PowerPivot query processing on the server you just installed.</span></span><br /><br /> <span data-ttu-id="c7a49-152">1) 在 [管理中心] 中，開啟 [管理伺服器上的服務] 頁面，確認伺服器和其服務是否出現。</span><span class="sxs-lookup"><span data-stu-id="c7a49-152">1) In Central Administration, open the Manage services on server page to confirm that the server and its services appear.</span></span><br /><span data-ttu-id="c7a49-153">-在 [伺服器] 中，按一下向下箭號，按一下 [變更伺服器]，然後選取具有新 PowerPivot for SharePoint 安裝的伺服器。</span><span class="sxs-lookup"><span data-stu-id="c7a49-153">-In Server, click the down arrow, click Change Server, and then select the server that has the new PowerPivot for SharePoint installation.</span></span><br /><span data-ttu-id="c7a49-154">-確認已啟動 SQL Server Analysis Services 和 SQL Server PowerPivot 系統服務。</span><span class="sxs-lookup"><span data-stu-id="c7a49-154">-Verify that SQL Server Analysis Services and SQL Server PowerPivot System Service are started.</span></span><br /><br /> <span data-ttu-id="c7a49-155">2) 在 [管理中心] 中，停止其他 PowerPivot for SharePoint 伺服器，讓您剛安裝的伺服器是唯一可用的伺服器。</span><span class="sxs-lookup"><span data-stu-id="c7a49-155">2) In Central Administration, stop other PowerPivot for SharePoint servers so that the server you just installed is the only one available.</span></span> <span data-ttu-id="c7a49-156">如需詳細資訊，請參閱[啟動或停止 PowerPivot for SharePoint 伺服器](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/start-or-stop-a-power-pivot-for-sharepoint-server)。</span><span class="sxs-lookup"><span data-stu-id="c7a49-156">For more information, see [Start or Stop a PowerPivot for SharePoint Server](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/start-or-stop-a-power-pivot-for-sharepoint-server).</span></span><br /><br /> <span data-ttu-id="c7a49-157">3) 按一下 PowerPivot 活頁簿，從文件庫中開啟它。</span><span class="sxs-lookup"><span data-stu-id="c7a49-157">3) Click a PowerPivot workbook to open it from the library.</span></span><br /><br /> <span data-ttu-id="c7a49-158">4) 按一下交叉分析篩選器或資料透視來起始查詢。</span><span class="sxs-lookup"><span data-stu-id="c7a49-158">4) Click a slicer or pivot the data to initiate a query.</span></span> <span data-ttu-id="c7a49-159">伺服器將會在背景載入 PowerPivot 資料。</span><span class="sxs-lookup"><span data-stu-id="c7a49-159">The server will load PowerPivot data in the background.</span></span> <span data-ttu-id="c7a49-160">在下一個步驟中，您將會連接到伺服器，並確認已經載入及快取資料。</span><span class="sxs-lookup"><span data-stu-id="c7a49-160">In the next step, you will connect to the server to verify the data is loaded and cached.</span></span><br /><br /> <span data-ttu-id="c7a49-161">5) 從 [開始] 功能表中的 [Microsoft SQL Server 程式] 群組開始 SQL Server Management Studio。</span><span class="sxs-lookup"><span data-stu-id="c7a49-161">5) Start SQL Server Management Studio from the Microsoft SQL Server program group in the Start menu.</span></span> <span data-ttu-id="c7a49-162">如果伺服器上未安裝這個工具，您可以跳到最後一個步驟，確認快取檔案存在。</span><span class="sxs-lookup"><span data-stu-id="c7a49-162">If this tool is not installed on your server, you can skip to the last step to confirm the presence of cached files.</span></span><br /><br /> <span data-ttu-id="c7a49-163">6) 在 [伺服器類型] 中，選取 [ **Analysis Services**]。</span><span class="sxs-lookup"><span data-stu-id="c7a49-163">6) In Server Type, select **Analysis Services**.</span></span><br /><br /> <span data-ttu-id="c7a49-164">7) 在 [伺服器名稱] 中，輸入\*\* \<server-name> \powerpivot\*\*，其中 **\<server-name>** 是具有新 PowerPivot for SharePoint 安裝的電腦名稱稱。</span><span class="sxs-lookup"><span data-stu-id="c7a49-164">7) In Server Name, enter **\<server-name>\powerpivot**, where **\<server-name>** is the name of the computer that has the new PowerPivot for SharePoint installation.</span></span><br /><br /> <span data-ttu-id="c7a49-165">8) 按一下 **[連接]**。</span><span class="sxs-lookup"><span data-stu-id="c7a49-165">8) Click **Connect**.</span></span><br /><br /> <span data-ttu-id="c7a49-166">9) 在物件總管中，按一下 [**資料庫**] 以查看已載入的 PowerPivot 資料檔案清單。</span><span class="sxs-lookup"><span data-stu-id="c7a49-166">9) In Object Explorer, click **Databases** to view the list of PowerPivot data files that are loaded.</span></span><br /><br /> <span data-ttu-id="c7a49-167">10) 電腦檔案系統上，請檢查下列資料夾以判斷檔案是否要快取到磁片。</span><span class="sxs-lookup"><span data-stu-id="c7a49-167">10) On the computer file system, check the following folder to determine whether files are cached to disk.</span></span> <span data-ttu-id="c7a49-168">快取檔案的存在會進一步驗證您的部署是否可以運作。</span><span class="sxs-lookup"><span data-stu-id="c7a49-168">The presence of cached files is further verification that your deployment is operational.</span></span> <span data-ttu-id="c7a49-169">若要檢視檔案快取，請移至 \Program Files\Microsoft SQL Server\MSAS11.POWERPIVOT\OLAP\Backup 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c7a49-169">To view the file cache, go to the \Program Files\Microsoft SQL Server\MSAS11.POWERPIVOT\OLAP\Backup folder.</span></span><br /><br /> <span data-ttu-id="c7a49-170">11) 重新開機您稍早停止的服務。</span><span class="sxs-lookup"><span data-stu-id="c7a49-170">11) Restart the services that you stopped earlier.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c7a49-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c7a49-171">See Also</span></span>  
 <span data-ttu-id="c7a49-172">[初始設定 &#40;PowerPivot for SharePoint&#41;](../../../2014/sql-server/install/initial-configuration-powerpivot-for-sharepoint.md) </span><span class="sxs-lookup"><span data-stu-id="c7a49-172">[Initial Configuration &#40;PowerPivot for SharePoint&#41;](../../../2014/sql-server/install/initial-configuration-powerpivot-for-sharepoint.md) </span></span>  
 <span data-ttu-id="c7a49-173">[PowerPivot for SharePoint 2010 安裝](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md) </span><span class="sxs-lookup"><span data-stu-id="c7a49-173">[PowerPivot for SharePoint 2010 Installation](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md) </span></span>  
 [<span data-ttu-id="c7a49-174">管理中心的 PowerPivot 伺服器管理和設定</span><span class="sxs-lookup"><span data-stu-id="c7a49-174">PowerPivot Server Administration and Configuration in Central Administration</span></span>](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration)  
  
  