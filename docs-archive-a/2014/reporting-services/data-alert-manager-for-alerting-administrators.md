---
title: 警示系統管理員的資料警示管理員 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- managing, alerts
- managing, data alerts
ms.assetid: 32fd968f-1c0c-4ba8-851c-8a3b5e1fbbf2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 050107d07e976b99609a456506eb7bbfbf5e20d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597647"
---
# <a name="data-alert-manager-for-alerting-administrators"></a><span data-ttu-id="807d6-102">警示系統管理員的資料警示管理員</span><span class="sxs-lookup"><span data-stu-id="807d6-102">Data Alert Manager for Alerting Administrators</span></span>
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="807d6-103">提供 [資料警示管理員] 讓 SharePoint 警示系統管理員管理資料警示。</span><span class="sxs-lookup"><span data-stu-id="807d6-103">provides Data Alert Manager for SharePoint alerting administrators to manage data alerts.</span></span> <span data-ttu-id="807d6-104">警示系統管理員可以檢視儲存到網站之所有警示的相關資訊，以及刪除警示。</span><span class="sxs-lookup"><span data-stu-id="807d6-104">Alerting administrators can view information about all alerts saved to the site and delete alerts.</span></span> <span data-ttu-id="807d6-105">下圖說明 [資料警示管理員] 中可供 SharePoint 警示管理員使用的功能。</span><span class="sxs-lookup"><span data-stu-id="807d6-105">The following picture shows the features available to SharePoint alerting managers in Data Alert Manager.</span></span>

 <span data-ttu-id="807d6-106">![SharePoint 網站管理員的警示管理員](media/rs-alertmanagersite.gif "SharePoint 網站管理員的警示管理員")</span><span class="sxs-lookup"><span data-stu-id="807d6-106">![Alert Manager for SharePoin tsite administrators](media/rs-alertmanagersite.gif "Alert Manager for SharePoin tsite administrators")</span></span>

 <span data-ttu-id="807d6-107">啟用網站進行資料警示時，會建立 MyDataAlerts.aspx 和 SiteDataAlerts.aspx 這兩個 SharePoint 頁面，並且將其加入 SharePoint 網站中。</span><span class="sxs-lookup"><span data-stu-id="807d6-107">When the site is enabled for data alerts, two SharePoint pages, MyDataAlerts.aspx and SiteDataAlerts.aspx are created and added to the SharePoint site.</span></span> <span data-ttu-id="807d6-108">SiteDataAlerts.aspx 是警示系統管理員的 [資料警示管理員]。</span><span class="sxs-lookup"><span data-stu-id="807d6-108">SiteDataAlerts.aspx is Data Alert Manager for alerting administrators.</span></span> <span data-ttu-id="807d6-109">警示系統管理員可以從 [網站設定] SharePoint 頁面開啟 [資料警示管理員]。</span><span class="sxs-lookup"><span data-stu-id="807d6-109">Alerting administrators can open Data Alert Manager from the Site Settings SharePoint page.</span></span> <span data-ttu-id="807d6-110">警示系統管理員必須具備「SharePoint 警示管理」權限才能開啟 [資料警示管理員]。</span><span class="sxs-lookup"><span data-stu-id="807d6-110">Alerting administrators must have SharePoint Manage Alerts permission to open Data Alert Manager.</span></span>

 <span data-ttu-id="807d6-111">您也可以使用 URL 直接開啟 [資料警示管理員]。</span><span class="sxs-lookup"><span data-stu-id="807d6-111">You can also open Data Alert Manager directly by using a URL.</span></span> <span data-ttu-id="807d6-112">以下說明 URL 的語法：</span><span class="sxs-lookup"><span data-stu-id="807d6-112">The following shows the syntax of the URL:</span></span>

 `http: //<site name>/_layouts/ReportServer/ SiteDataAlerts.aspx`

> [!NOTE]
>  <span data-ttu-id="807d6-113">身為警示系統管理員，您可以授與資訊工作者存取 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 資料警示功能的權限。</span><span class="sxs-lookup"><span data-stu-id="807d6-113">As an alerting administrator, you can grant permission to information workers to access the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] data alerts features.</span></span> <span data-ttu-id="807d6-114">如需所需權限的詳細資訊，請參閱 [Reporting Services 資料警示](../ssms/agent/alerts.md)。</span><span class="sxs-lookup"><span data-stu-id="807d6-114">For more information about the required permissions, see [Reporting Services Data Alerts](../ssms/agent/alerts.md).</span></span>

##  <a name="viewing-data-alert-information"></a><a name="ViewingAlerts"></a> <span data-ttu-id="807d6-115">檢視資料警示資訊</span><span class="sxs-lookup"><span data-stu-id="807d6-115">Viewing Data Alert Information</span></span>
 <span data-ttu-id="807d6-116">在 SharePoint 中安裝並設定 Reporting Services 之後，[網站設定] SharePoint 頁面就會包含 **[Reporting Services]** 選項。</span><span class="sxs-lookup"><span data-stu-id="807d6-116">When Reporting Services is installed and configured in SharePoint, the Site Settings SharePoint page includes the **Reporting Services** options.</span></span> <span data-ttu-id="807d6-117">警示系統管理員在 Reporting Service 中按一下 **[管理資料警示]** 選項，就可以開啟 [資料警示管理員]。</span><span class="sxs-lookup"><span data-stu-id="807d6-117">Alerting administrators click the **Manage Data Alerts** option within Reporting Service to open Data Alert Manager.</span></span> <span data-ttu-id="807d6-118">下圖說明 [網站設定] 頁面上開啟 [資料警示管理員] 的位置。</span><span class="sxs-lookup"><span data-stu-id="807d6-118">The following picture shows from where on the Site Settings page you open Data Alert Manager.</span></span>

 <span data-ttu-id="807d6-119">![[網站設定] 頁面的 Reporting Services 區段](media/rs-sitesettings.gif "[網站設定] 頁面的 Reporting Services 區段")</span><span class="sxs-lookup"><span data-stu-id="807d6-119">![Reporting Services section of Site Settings page](media/rs-sitesettings.gif "Reporting Services section of Site Settings page")</span></span>

 <span data-ttu-id="807d6-120">[資料警示管理員] 包含一個資料表，其中列出警示名稱、報表名稱、警示擁有者的名稱、傳送的警示訊息數目、上一次執行警示的時間、上一次修改警示定義的時間，以及警示訊息的狀態。</span><span class="sxs-lookup"><span data-stu-id="807d6-120">Data Alert Manager includes a table that lists the alert name, report name, the name of the alert owner, the number the alert message was sent, the last time the alert was run, the last time the alert definition was modified, and the status of the alert message.</span></span> <span data-ttu-id="807d6-121">如果警示無法產生或是傳送，狀態資料行就會包含有關錯誤的資訊並協助您疑難排解警示。</span><span class="sxs-lookup"><span data-stu-id="807d6-121">If the alert cannot be generated or generated or sent, the status column contains information about the error and helps you troubleshoot the alert.</span></span> <span data-ttu-id="807d6-122">如需詳細資訊，請參閱[在資料警示管理員中管理 SharePoint 網站上的所有資料警示](manage-all-data-alerts-on-a-sharepoint-site-in-data-alert-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="807d6-122">For more information, see [Manage All Data Alerts on a SharePoint Site in Data Alert Manager](manage-all-data-alerts-on-a-sharepoint-site-in-data-alert-manager.md).</span></span>

 <span data-ttu-id="807d6-123">下表顯示 [資料警示管理員] 中資料表的範例資料。</span><span class="sxs-lookup"><span data-stu-id="807d6-123">The following table shows sample data from a table in Data Alert Manager.</span></span> <span data-ttu-id="807d6-124">當發生錯誤時，資料表的 [狀態]\*\*\*\* 欄位中會包含錯誤訊息和記錄中項目的識別碼 (GUID)。</span><span class="sxs-lookup"><span data-stu-id="807d6-124">When an error occurs, the error message and the identifier of the entry in the log (a GUID) are included in the **Status** field in the table.</span></span>

|<span data-ttu-id="807d6-125">警示名稱</span><span class="sxs-lookup"><span data-stu-id="807d6-125">Alert Name</span></span>|<span data-ttu-id="807d6-126">報表名稱</span><span class="sxs-lookup"><span data-stu-id="807d6-126">Report Name</span></span>|<span data-ttu-id="807d6-127">建立者</span><span class="sxs-lookup"><span data-stu-id="807d6-127">Created By</span></span>|<span data-ttu-id="807d6-128">傳送警示</span><span class="sxs-lookup"><span data-stu-id="807d6-128">Sent Alerts</span></span>|<span data-ttu-id="807d6-129">最後執行</span><span class="sxs-lookup"><span data-stu-id="807d6-129">Last Run</span></span>|<span data-ttu-id="807d6-130">上次修改</span><span class="sxs-lookup"><span data-stu-id="807d6-130">Last Modified</span></span>|<span data-ttu-id="807d6-131">狀態</span><span class="sxs-lookup"><span data-stu-id="807d6-131">Status</span></span>|
|----------------|-----------------|----------------|-----------------|--------------|-------------------|------------|
|<span data-ttu-id="807d6-132">SalesQTR</span><span class="sxs-lookup"><span data-stu-id="807d6-132">SalesQTR</span></span>|<span data-ttu-id="807d6-133">SalesByTerritoryAndQTR</span><span class="sxs-lookup"><span data-stu-id="807d6-133">SalesByTerritoryAndQTR</span></span>|<span data-ttu-id="807d6-134">Lauren Johnson</span><span class="sxs-lookup"><span data-stu-id="807d6-134">Lauren Johnson</span></span>|<span data-ttu-id="807d6-135">4</span><span class="sxs-lookup"><span data-stu-id="807d6-135">4</span></span>|<span data-ttu-id="807d6-136">6/12/2011</span><span class="sxs-lookup"><span data-stu-id="807d6-136">6/12/2011</span></span>|<span data-ttu-id="807d6-137">6/1/2011</span><span class="sxs-lookup"><span data-stu-id="807d6-137">6/1/2011</span></span>|<span data-ttu-id="807d6-138">上次警示執行成功，並且已傳送警示。</span><span class="sxs-lookup"><span data-stu-id="807d6-138">Last alert ran successfully and alert was sent.</span></span>|
|<span data-ttu-id="807d6-139">UnitsSold</span><span class="sxs-lookup"><span data-stu-id="807d6-139">UnitsSold</span></span>|<span data-ttu-id="807d6-140">ProductsSalesByQTR</span><span class="sxs-lookup"><span data-stu-id="807d6-140">ProductsSalesByQTR</span></span>|<span data-ttu-id="807d6-141">Michael Blythe</span><span class="sxs-lookup"><span data-stu-id="807d6-141">Michael Blythe</span></span>|<span data-ttu-id="807d6-142">2</span><span class="sxs-lookup"><span data-stu-id="807d6-142">2</span></span>|<span data-ttu-id="807d6-143">7/1/2011</span><span class="sxs-lookup"><span data-stu-id="807d6-143">7/1/2011</span></span>|<span data-ttu-id="807d6-144">6/28/2011</span><span class="sxs-lookup"><span data-stu-id="807d6-144">6/28/2011</span></span>|<span data-ttu-id="807d6-145">上次警示執行成功，但因為資料未變更所以未傳送警示。</span><span class="sxs-lookup"><span data-stu-id="807d6-145">Last alert ran successfully, but the data was unchanged and no alert was sent.</span></span>|
|<span data-ttu-id="807d6-146">InventoryCount</span><span class="sxs-lookup"><span data-stu-id="807d6-146">InventoryCount</span></span>|<span data-ttu-id="807d6-147">StockStatusByQTR</span><span class="sxs-lookup"><span data-stu-id="807d6-147">StockStatusByQTR</span></span>|<span data-ttu-id="807d6-148">Lauren Johnson</span><span class="sxs-lookup"><span data-stu-id="807d6-148">Lauren Johnson</span></span>|<span data-ttu-id="807d6-149">7</span><span class="sxs-lookup"><span data-stu-id="807d6-149">7</span></span>|<span data-ttu-id="807d6-150">7/10/2011</span><span class="sxs-lookup"><span data-stu-id="807d6-150">7/10/2011</span></span>|<span data-ttu-id="807d6-151">7/2/2011</span><span class="sxs-lookup"><span data-stu-id="807d6-151">7/2/2011</span></span>|<span data-ttu-id="807d6-152">\<error message>記錄檔包含有關錯誤的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="807d6-152">\<error message>The log file contains detailed information about the error.</span></span> <span data-ttu-id="807d6-153">請參閱識別碼為的記錄專案： \<GUID> 。</span><span class="sxs-lookup"><span data-stu-id="807d6-153">Refer to the log entry with the identifier: \<GUID>.</span></span>|
|<span data-ttu-id="807d6-154">TopPromotion</span><span class="sxs-lookup"><span data-stu-id="807d6-154">TopPromotion</span></span>|<span data-ttu-id="807d6-155">PromotionTracking</span><span class="sxs-lookup"><span data-stu-id="807d6-155">PromotionTracking</span></span>|<span data-ttu-id="807d6-156">Cristian Petculescu</span><span class="sxs-lookup"><span data-stu-id="807d6-156">Cristian Petculescu</span></span>|<span data-ttu-id="807d6-157">0</span><span class="sxs-lookup"><span data-stu-id="807d6-157">0</span></span>||<span data-ttu-id="807d6-158">5/23/2011</span><span class="sxs-lookup"><span data-stu-id="807d6-158">5/23/2011</span></span>|<span data-ttu-id="807d6-159">已建立警示。</span><span class="sxs-lookup"><span data-stu-id="807d6-159">Alert created.</span></span>|

 <span data-ttu-id="807d6-160">如需詳細資訊，請參閱[在資料警示管理員中管理 SharePoint 網站上的所有資料警示](manage-all-data-alerts-on-a-sharepoint-site-in-data-alert-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="807d6-160">For more information see, [Manage All Data Alerts on a SharePoint Site in Data Alert Manager](manage-all-data-alerts-on-a-sharepoint-site-in-data-alert-manager.md).</span></span>

 <span data-ttu-id="807d6-161">您可以檢視網站使用者建立的所有警示。</span><span class="sxs-lookup"><span data-stu-id="807d6-161">You can view all alerts created by site users.</span></span> <span data-ttu-id="807d6-162">先選擇使用者，然後選擇檢視使用者的所有警示，或是僅檢視特定報表的警示。</span><span class="sxs-lookup"><span data-stu-id="807d6-162">You choose a user and then choose whether to view all their alerts or only alerts for a specific report.</span></span>


##  <a name="delete-data-alerts"></a><a name="DeleteAlerts"></a><span data-ttu-id="807d6-163">刪除資料警示</span><span class="sxs-lookup"><span data-stu-id="807d6-163">Delete Data Alerts</span></span>
 <span data-ttu-id="807d6-164">您可從 [資料警示管理員] 中刪除警示定義。</span><span class="sxs-lookup"><span data-stu-id="807d6-164">You delete alerts definitions from Data Alert Manager.</span></span> <span data-ttu-id="807d6-165">每一個資料警示定義都有一位擁有者，也就是建立該資料警示定義的 SharePoint 使用者。</span><span class="sxs-lookup"><span data-stu-id="807d6-165">Every data alert definition has an owner, the SharePoint user who created it.</span></span> <span data-ttu-id="807d6-166">擁有者只能刪除自己建立的警示定義。</span><span class="sxs-lookup"><span data-stu-id="807d6-166">Owners can delete only the alert definitions that they created.</span></span> <span data-ttu-id="807d6-167">如需詳細資訊，請參閱 [在資料警示管理員中管理我的資料警示](manage-my-data-alerts-in-data-alert-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="807d6-167">For more information, see [Manage My Data Alerts in Data Alert Manager](manage-my-data-alerts-in-data-alert-manager.md).</span></span>

 <span data-ttu-id="807d6-168">SharePoint 警示系統管理員可以列出然後刪除網站上所有使用者建立的警示定義。</span><span class="sxs-lookup"><span data-stu-id="807d6-168">A SharePoint alerting administrators can list and then delete alert definitions created by all users of the site.</span></span> <span data-ttu-id="807d6-169">如需詳細資訊，請參閱 [在資料警示管理員中管理 SharePoint 網站上的所有資料警示](manage-all-data-alerts-on-a-sharepoint-site-in-data-alert-manager.md)</span><span class="sxs-lookup"><span data-stu-id="807d6-169">For more information, see [Manage All Data Alerts on a SharePoint Site in Data Alert Manager](manage-all-data-alerts-on-a-sharepoint-site-in-data-alert-manager.md)</span></span>

 <span data-ttu-id="807d6-170">您刪除警示定義之後，就不會再傳送任何警示。</span><span class="sxs-lookup"><span data-stu-id="807d6-170">After you delete the alert definition, no further alerts are sent.</span></span> <span data-ttu-id="807d6-171">不過，如果您查詢警示資料庫，可能會發現警示定義仍然存在。</span><span class="sxs-lookup"><span data-stu-id="807d6-171">However, if you query the alerting database you might find that the alert definition still exists.</span></span> <span data-ttu-id="807d6-172">警示服務會依照排程執行清除，而警示定義會在下一次清除時永久刪除。</span><span class="sxs-lookup"><span data-stu-id="807d6-172">The alerting service performs clean up on a schedule and the alert definition is deleted permanently in the next cleanup.</span></span> <span data-ttu-id="807d6-173">預設的清除間隔是 20 分鐘。</span><span class="sxs-lookup"><span data-stu-id="807d6-173">The default cleanup interval is 20 minutes.</span></span> <span data-ttu-id="807d6-174">此清除間隔和其他清除間隔都可以加以設定。</span><span class="sxs-lookup"><span data-stu-id="807d6-174">This and other cleanup intervals are configurable.</span></span> <span data-ttu-id="807d6-175">如需詳細資訊，請參閱 [Reporting Services 資料警示](../ssms/agent/alerts.md)。</span><span class="sxs-lookup"><span data-stu-id="807d6-175">For more information, see [Reporting Services Data Alerts](../ssms/agent/alerts.md).</span></span>


##  <a name="related-tasks"></a><a name="HowTo"></a> <span data-ttu-id="807d6-176">相關工作</span><span class="sxs-lookup"><span data-stu-id="807d6-176">Related Tasks</span></span>
 <span data-ttu-id="807d6-177">本節列出如何管理警示的程序。</span><span class="sxs-lookup"><span data-stu-id="807d6-177">This section lists a procedure that shows you how to manage your alerts.</span></span>

-   [<span data-ttu-id="807d6-178">在資料警示管理員中管理 SharePoint 網站上的所有資料警示</span><span class="sxs-lookup"><span data-stu-id="807d6-178">Manage All Data Alerts on a SharePoint Site in Data Alert Manager</span></span>](manage-all-data-alerts-on-a-sharepoint-site-in-data-alert-manager.md)


## <a name="see-also"></a><span data-ttu-id="807d6-179">另請參閱</span><span class="sxs-lookup"><span data-stu-id="807d6-179">See Also</span></span>
 [<span data-ttu-id="807d6-180">Reporting Services 資料警示</span><span class="sxs-lookup"><span data-stu-id="807d6-180">Reporting Services Data Alerts</span></span>](../ssms/agent/alerts.md)

