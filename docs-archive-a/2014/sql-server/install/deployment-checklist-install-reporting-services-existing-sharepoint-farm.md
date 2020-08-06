---
title: 部署檢查清單：將 Reporting Services 安裝到現有的 SharePoint 伺服器陣列 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 436b4c3d-3f2f-464a-be7e-5c051d9ffb8f
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 041e038fdbc3198ff80fad82dd1a05bad2ff6fe2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710185"
---
# <a name="deployment-checklist-install-reporting-services-into-an-existing-sharepoint-farm"></a><span data-ttu-id="16fd4-102">部署檢查清單：將 Reporting Services 安裝至現有的 SharePoint 伺服器陣列</span><span class="sxs-lookup"><span data-stu-id="16fd4-102">Deployment Checklist: Install Reporting Services into an Existing SharePoint Farm</span></span>
  <span data-ttu-id="16fd4-103">您可以將 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 報表伺服器安裝至新的 SharePoint 伺服器陣列中，或安裝至現有的 SharePoint 伺服器陣列中。</span><span class="sxs-lookup"><span data-stu-id="16fd4-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint report servers can be installed into a new SharePoint Farm or into an existing SharePoint farm.</span></span> <span data-ttu-id="16fd4-104">此主題描述將 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安裝至現有 SharePoint 伺服器陣列中的可能案例和最佳作法。</span><span class="sxs-lookup"><span data-stu-id="16fd4-104">This topic describes the possible scenarios and best practices for installing [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] into and existing SharePoint farm.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="16fd4-105">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="16fd4-105">Prerequisites</span></span>  
 <span data-ttu-id="16fd4-106">執行安裝程式之前，請檢閱下列資訊：</span><span class="sxs-lookup"><span data-stu-id="16fd4-106">Before you run Setup, review the following information:</span></span>  
  
|<span data-ttu-id="16fd4-107">步驟</span><span class="sxs-lookup"><span data-stu-id="16fd4-107">Step</span></span>|<span data-ttu-id="16fd4-108">連結</span><span class="sxs-lookup"><span data-stu-id="16fd4-108">Link</span></span>|  
|----------|----------|  
|<span data-ttu-id="16fd4-109">建立或識別報表伺服器部署中使用的帳戶。</span><span class="sxs-lookup"><span data-stu-id="16fd4-109">Create or identify the accounts used in a report server deployment.</span></span> <span data-ttu-id="16fd4-110">您必須擁有報表伺服器服務的服務帳戶，以及連接到報表伺服器資料庫的認證</span><span class="sxs-lookup"><span data-stu-id="16fd4-110">You must have a service account for the Report Server service, and credentials for connecting to the report server database</span></span>||  
|<span data-ttu-id="16fd4-111">決定主控報表伺服器資料庫的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="16fd4-111">Decide on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to host the report server database.</span></span> <span data-ttu-id="16fd4-112">您可以使用本機或遠端 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體。</span><span class="sxs-lookup"><span data-stu-id="16fd4-112">You can use a local or remote instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="16fd4-113">您所選擇之執行個體所在的電腦上，應有足以容納您報表的儲存容量。</span><span class="sxs-lookup"><span data-stu-id="16fd4-113">You should choose an instance that is on a computer that has the storage capacity to accommodate your reports.</span></span>||  
|<span data-ttu-id="16fd4-114">(選擇性) 如果您想要在訂閱中使用報表伺服器電子郵件，請尋找會對組織提供電子郵件服務之 SMTP 伺服器或閘道的名稱</span><span class="sxs-lookup"><span data-stu-id="16fd4-114">(Optional) Find the name of the SMTP server or gateway that provides e-mail service to your organization if you want to use report server e-mail in subscriptions</span></span>|[<span data-ttu-id="16fd4-115">針對 &#40;SSRS Configuration Manager 的電子郵件傳遞設定報表伺服器&#41;</span><span class="sxs-lookup"><span data-stu-id="16fd4-115">Configure a Report Server for E-Mail Delivery &#40;SSRS Configuration Manager&#41;</span></span>](../../../2014/sql-server/install/configure-a-report-server-for-e-mail-delivery-ssrs-configuration-manager.md)|  
|<span data-ttu-id="16fd4-116">注意：如果您要從先前的 CTP 版本升級電腦 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ，而且已對設定檔進行自訂變更，則在升級至之後，您必須對設定檔進行相同的變更 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="16fd4-116">Note: If you are upgrading a computer from a previous CTP release [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] and you had made custom changes to the configuration files, you will need to make the same changes to the configuration files, following the upgrade to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="16fd4-117">受影響的檔案會**web.config**和**client.config**。</span><span class="sxs-lookup"><span data-stu-id="16fd4-117">The affected files are **web.config** and **client.config**.</span></span>||  
  
## <a name="installation-scenarios"></a><span data-ttu-id="16fd4-118">安裝案例</span><span class="sxs-lookup"><span data-stu-id="16fd4-118">Installation Scenarios</span></span>  
 <span data-ttu-id="16fd4-119">下表說明將 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安裝至現有 SharePoint 伺服器陣列中的可能案例。</span><span class="sxs-lookup"><span data-stu-id="16fd4-119">The following table describes the possible scenarios when you are installing [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] into and existing SharePoint Farm.</span></span> <span data-ttu-id="16fd4-120">本機模式可讓您從 SharePoint 文件庫本機轉譯報表，而不需要與 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 報表伺服器整合。</span><span class="sxs-lookup"><span data-stu-id="16fd4-120">Local mode allows reports to be rendered locally from the SharePoint document library, without integration with a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report server.</span></span> <span data-ttu-id="16fd4-121">需要 SharePoint 產品的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 增益集，但不需要 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="16fd4-121">The [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in for SharePoint products is required but a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report server is not.</span></span> <span data-ttu-id="16fd4-122">如需原生模式的詳細資訊，請參閱[報表檢視器中的原生模式與連接模式報表 &#40;在 Sharepoint 模式中 Reporting Services&#41;](../../../2014/reporting-services/local-vs-connected-mode-report-viewer-reporting-services-sharepoint-mode.md)以及[尋找適用于 sharepoint 產品之 Reporting Services 增益集的位置](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)。</span><span class="sxs-lookup"><span data-stu-id="16fd4-122">For more information on local mode, see [Local Mode vs. Connected Mode Reports in the Report Viewer &#40;Reporting Services in SharePoint Mode&#41;](../../../2014/reporting-services/local-vs-connected-mode-report-viewer-reporting-services-sharepoint-mode.md) and [Where to find the Reporting Services add-in for SharePoint Products](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).</span></span>  
  
|<span data-ttu-id="16fd4-123">正在啟動組態</span><span class="sxs-lookup"><span data-stu-id="16fd4-123">Starting Configuration</span></span>|<span data-ttu-id="16fd4-124">工作流程</span><span class="sxs-lookup"><span data-stu-id="16fd4-124">Workflow</span></span>|<span data-ttu-id="16fd4-125">正在結束組態</span><span class="sxs-lookup"><span data-stu-id="16fd4-125">Ending Configuration</span></span>|<span data-ttu-id="16fd4-126">註解</span><span class="sxs-lookup"><span data-stu-id="16fd4-126">Comments</span></span>|  
|----------------------------|--------------|--------------------------|--------------|  
|<span data-ttu-id="16fd4-127">本機模式的 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16fd4-127">[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] in Local mode</span></span>|<span data-ttu-id="16fd4-128">安裝</span><span class="sxs-lookup"><span data-stu-id="16fd4-128">Installation</span></span>|<span data-ttu-id="16fd4-129">已連接模式 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="16fd4-129">Connected mode [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>||  
|<span data-ttu-id="16fd4-130">已連接模式  或 </span><span class="sxs-lookup"><span data-stu-id="16fd4-130">Connected Mode [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] or [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]</span></span>|<span data-ttu-id="16fd4-131">就地升級</span><span class="sxs-lookup"><span data-stu-id="16fd4-131">In place upgrade</span></span>|<span data-ttu-id="16fd4-132">已連接模式 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="16fd4-132">Connected mode [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>||  
|<span data-ttu-id="16fd4-133">已連接模式  或 </span><span class="sxs-lookup"><span data-stu-id="16fd4-133">Connected Mode [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] or [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]</span></span>|<span data-ttu-id="16fd4-134">遷移</span><span class="sxs-lookup"><span data-stu-id="16fd4-134">Migration</span></span>|<span data-ttu-id="16fd4-135">已連接模式 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="16fd4-135">Connected mode [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>||  
  
## <a name="installation-and-in-place-upgrade-checklist"></a><span data-ttu-id="16fd4-136">安裝和就地升級檢查清單</span><span class="sxs-lookup"><span data-stu-id="16fd4-136">Installation and in place Upgrade Checklist</span></span>  
 <span data-ttu-id="16fd4-137">下表摘要說明您應檢閱及用於安裝的步驟、工具及資訊：</span><span class="sxs-lookup"><span data-stu-id="16fd4-137">The following table summarizes the steps, tools, and information you should review and use for the installation:</span></span>  
  
|<span data-ttu-id="16fd4-138">步驟</span><span class="sxs-lookup"><span data-stu-id="16fd4-138">Step</span></span>|<span data-ttu-id="16fd4-139">連結</span><span class="sxs-lookup"><span data-stu-id="16fd4-139">Link</span></span>|  
|----------|----------|  
|<span data-ttu-id="16fd4-140">**安裝和初始組態**</span><span class="sxs-lookup"><span data-stu-id="16fd4-140">**Installation and initial configuration**</span></span>||  
|<span data-ttu-id="16fd4-141">在所有 Web 前端 (WFE) 電腦上安裝 SharePoint 增益集。</span><span class="sxs-lookup"><span data-stu-id="16fd4-141">Install the SharePoint add-in on all Web front-end (WFE) computers.</span></span>|[<span data-ttu-id="16fd4-142">將其他 Reporting Services Web 前端加入至伺服器陣列</span><span class="sxs-lookup"><span data-stu-id="16fd4-142">Add an Additional Reporting Services Web Front-end to a Farm</span></span>](../../reporting-services/install-windows/add-an-additional-reporting-services-web-front-end-to-a-farm.md)|  
|<span data-ttu-id="16fd4-143">安裝 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Reporting Services 和 Database Engine。</span><span class="sxs-lookup"><span data-stu-id="16fd4-143">Install SQL Server [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Reporting Services and the Database engine.</span></span>|[<span data-ttu-id="16fd4-144">安裝 SharePoint 2010 Reporting Services SharePoint 模式</span><span class="sxs-lookup"><span data-stu-id="16fd4-144">Install Reporting Services SharePoint Mode for SharePoint 2010</span></span>](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)|  
|<span data-ttu-id="16fd4-145">至少建立一個 SSRS 服務應用程式並設定服務應用程式關聯。</span><span class="sxs-lookup"><span data-stu-id="16fd4-145">Create at least one SSRS service application and configure service app association.</span></span>|<span data-ttu-id="16fd4-146">請參閱[安裝適用于 sharepoint 2010 的 Reporting Services Sharepoint 模式](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)中的「服務應用程式」一節</span><span class="sxs-lookup"><span data-stu-id="16fd4-146">See the 'Service Application' section in [Install Reporting Services SharePoint Mode for SharePoint 2010](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)</span></span>|  
|<span data-ttu-id="16fd4-147">**其他設定**</span><span class="sxs-lookup"><span data-stu-id="16fd4-147">**Additional Configuration**</span></span>||  
|<span data-ttu-id="16fd4-148">將 SSRS 內容類型加入您的文件庫。</span><span class="sxs-lookup"><span data-stu-id="16fd4-148">Add SSRS content types to your document library.</span></span>|[<span data-ttu-id="16fd4-149">將報表伺服器內容類型加入至 SharePoint 整合模式下的程式庫 &#40;Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="16fd4-149">Add Report Server Content Types to a Library &#40;Reporting Services in SharePoint Integrated Mode&#41;</span></span>](../../../2014/reporting-services/add-reporting-services-content-types-to-a-sharepoint-library.md)|  
|<span data-ttu-id="16fd4-150">佈建 SQL Server Agent</span><span class="sxs-lookup"><span data-stu-id="16fd4-150">Provision SQL Server Agent</span></span>|[<span data-ttu-id="16fd4-151">SSRS 服務應用程式的佈建訂閱及警示</span><span class="sxs-lookup"><span data-stu-id="16fd4-151">Provision Subscriptions and Alerts for SSRS Service Applications</span></span>](../../reporting-services/install-windows/provision-subscriptions-and-alerts-for-ssrs-service-applications.md)|  
|<span data-ttu-id="16fd4-152">設定服務應用程式的電子郵件設定</span><span class="sxs-lookup"><span data-stu-id="16fd4-152">Configure e-mail settings for your Service application</span></span>|[<span data-ttu-id="16fd4-153">設定 Reporting Services 服務應用程式的電子郵件 &#40;SharePoint 2010 和 SharePoint 2013&#41;</span><span class="sxs-lookup"><span data-stu-id="16fd4-153">Configure E-mail for a Reporting Services Service Application &#40;SharePoint 2010 and SharePoint 2013&#41;</span></span>](../../reporting-services/install-windows/configure-e-mail-for-a-reporting-services-service-application.md)|  
|<span data-ttu-id="16fd4-154">設定對 Windows Token 服務的宣告 (c2WTS)</span><span class="sxs-lookup"><span data-stu-id="16fd4-154">Configure Claims to Windows Token Service (c2WTS)</span></span>|[<span data-ttu-id="16fd4-155">對 Windows Token 服務的宣告 &#40;C2WTS&#41; 和 Reporting Services</span><span class="sxs-lookup"><span data-stu-id="16fd4-155">Claims to Windows Token Service &#40;C2WTS&#41; and Reporting Services</span></span>](../../../2014/sql-server/install/claims-to-windows-token-service-c2wts-and-reporting-services.md)|  
  
## <a name="migration-checklist"></a><span data-ttu-id="16fd4-156">移轉檢查清單</span><span class="sxs-lookup"><span data-stu-id="16fd4-156">Migration Checklist</span></span>  
 <span data-ttu-id="16fd4-157">以下是從現有安裝移轉至新安裝的基本步驟清單。</span><span class="sxs-lookup"><span data-stu-id="16fd4-157">The following is a list of the basic steps for a migration from an existing installation to a new installation.</span></span>  
  
|<span data-ttu-id="16fd4-158">步驟</span><span class="sxs-lookup"><span data-stu-id="16fd4-158">Step</span></span>|<span data-ttu-id="16fd4-159">連結</span><span class="sxs-lookup"><span data-stu-id="16fd4-159">Link</span></span>|  
|----------|----------|  
|<span data-ttu-id="16fd4-160">安裝及設定新伺服器。</span><span class="sxs-lookup"><span data-stu-id="16fd4-160">Install and configure your new server.</span></span> <span data-ttu-id="16fd4-161">這包括下列項目：</span><span class="sxs-lookup"><span data-stu-id="16fd4-161">This includes the following:</span></span><br /><br /> <span data-ttu-id="16fd4-162">SharePoint 產品準備工具</span><span class="sxs-lookup"><span data-stu-id="16fd4-162">SharePoint Products Preparation Tool</span></span><br /><br /> <span data-ttu-id="16fd4-163">SharePoint 2010 產品</span><span class="sxs-lookup"><span data-stu-id="16fd4-163">SharePoint 2010 Product</span></span><br /><br /> <span data-ttu-id="16fd4-164">SharePoint 2010 SP1</span><span class="sxs-lookup"><span data-stu-id="16fd4-164">SharePoint 2010 SP1</span></span><br /><br /> <span data-ttu-id="16fd4-165">SharePoint 模式的 </span><span class="sxs-lookup"><span data-stu-id="16fd4-165">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] in SharePoint Mode</span></span><br /><br /> <span data-ttu-id="16fd4-166">SharePoint 2010 產品的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 增益集</span><span class="sxs-lookup"><span data-stu-id="16fd4-166">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] add-in for SharePoint 2010 products</span></span>|[<span data-ttu-id="16fd4-167">安裝 SharePoint 2010 Reporting Services SharePoint 模式</span><span class="sxs-lookup"><span data-stu-id="16fd4-167">Install Reporting Services SharePoint Mode for SharePoint 2010</span></span>](../../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)|  
|<span data-ttu-id="16fd4-168">至少建立一個 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服務應用程式</span><span class="sxs-lookup"><span data-stu-id="16fd4-168">Create at least one [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application</span></span>||  
|<span data-ttu-id="16fd4-169">備份 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 資料庫</span><span class="sxs-lookup"><span data-stu-id="16fd4-169">Backup [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Databases</span></span>||  
|<span data-ttu-id="16fd4-170">備份 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 加密金鑰</span><span class="sxs-lookup"><span data-stu-id="16fd4-170">Backup [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Encryption keys</span></span>||  
|<span data-ttu-id="16fd4-171">還原 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 資料庫和加密金鑰</span><span class="sxs-lookup"><span data-stu-id="16fd4-171">Restore [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] database and Encryption keys</span></span>||  
|<span data-ttu-id="16fd4-172">將所有 Web 應用程式對應至新的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]服務應用程式</span><span class="sxs-lookup"><span data-stu-id="16fd4-172">Map all web applications to new [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]service application(s)</span></span>|<span data-ttu-id="16fd4-173">\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="16fd4-173">The new installation **is now functional**</span></span>|  
|<span data-ttu-id="16fd4-174">移除舊伺服器上的整合 URL。</span><span class="sxs-lookup"><span data-stu-id="16fd4-174">Remove the Integration URL on the old server.</span></span>|<span data-ttu-id="16fd4-175">從 SharePoint 管理中心的 **[一般應用程式設定]** 頁面上，按一下 **[Reporting Services 整合]**。</span><span class="sxs-lookup"><span data-stu-id="16fd4-175">From SharePoint Central Administration, on the **General Application Settings** Page, click **Reporting Services Integration**.</span></span>|  
|<span data-ttu-id="16fd4-176">視需要從舊安裝解除安裝 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="16fd4-176">Uninstall [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] from the old installation, if desired.</span></span>||  
  
## <a name="next-steps"></a><span data-ttu-id="16fd4-177">後續步驟</span><span class="sxs-lookup"><span data-stu-id="16fd4-177">Next Steps</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16fd4-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16fd4-178">See Also</span></span>  
 <span data-ttu-id="16fd4-179">[Sharepoint 2010 和 SharePoint 2013 Reporting Services SharePoint 模式安裝 &#40;&#41;](../../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md) </span><span class="sxs-lookup"><span data-stu-id="16fd4-179">[Reporting Services SharePoint Mode Installation &#40;SharePoint 2010 and SharePoint 2013&#41;](../../reporting-services/install-windows/install-reporting-services-sharepoint-mode.md) </span></span>  
 <span data-ttu-id="16fd4-180">[在 SharePoint 2010 伺服器陣列中使用 SQL Server BI 功能的指引](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md) </span><span class="sxs-lookup"><span data-stu-id="16fd4-180">[Guidance for Using SQL Server BI Features in a SharePoint 2010 Farm](../../../2014/sql-server/install/guidance-for-using-sql-server-bi-features-in-a-sharepoint-2010-farm.md) </span></span>  
 [<span data-ttu-id="16fd4-181">支援的 SharePoint 和 Reporting Services 伺服器與增益集的組合 &#40;SQL Server 2014&#41;</span><span class="sxs-lookup"><span data-stu-id="16fd4-181">Supported Combinations of SharePoint and Reporting Services Server and Add-in &#40;SQL Server 2014&#41;</span></span>](../../reporting-services/install-windows/supported-combinations-of-sharepoint-and-reporting-services-server.md)  
  
  