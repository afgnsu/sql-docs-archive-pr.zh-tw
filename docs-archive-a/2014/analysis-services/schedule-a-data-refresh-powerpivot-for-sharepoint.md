---
title: 排程資料重新整理 (PowerPivot for SharePoint) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- unattended data refresh [Analysis Services with SharePoint]
- scheduled data refresh [Analysis Services with SharePoint]
- data refresh [Analysis Services with SharePoint]
ms.assetid: 8571208f-6aae-4058-83c6-9f916f5e2f9b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9d6078cf59c27c15ead8f22047ba9add20757be7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592923"
---
# <a name="schedule-a-data-refresh-powerpivot-for-sharepoint"></a><span data-ttu-id="d03f1-102">排程資料重新整理 (PowerPivot for SharePoint)</span><span class="sxs-lookup"><span data-stu-id="d03f1-102">Schedule a Data Refresh (PowerPivot for SharePoint)</span></span>
  <span data-ttu-id="d03f1-103">您可以排程資料重新整理，以取得已發行到 SharePoint 網站之 Excel 活頁簿內對 PowerPivot 資料的自動更新。</span><span class="sxs-lookup"><span data-stu-id="d03f1-103">You can schedule data refresh to get automatic updates to PowerPivot data inside an Excel workbook that you published to a SharePoint site.</span></span>  
  
 <span data-ttu-id="d03f1-104">**[!INCLUDE[applies](../includes/applies-md.md)]** SharePoint 2010</span><span class="sxs-lookup"><span data-stu-id="d03f1-104">**[!INCLUDE[applies](../includes/applies-md.md)]**  SharePoint 2010</span></span>  
  
 <span data-ttu-id="d03f1-105">**本主題內容：**</span><span class="sxs-lookup"><span data-stu-id="d03f1-105">**In this topic:**</span></span>  
  
 [<span data-ttu-id="d03f1-106">先決條件</span><span class="sxs-lookup"><span data-stu-id="d03f1-106">Prerequisites</span></span>](#prereq)  
  
 [<span data-ttu-id="d03f1-107">資料重新整理概觀</span><span class="sxs-lookup"><span data-stu-id="d03f1-107">Data Refresh Overview</span></span>](#intro)  
  
 [<span data-ttu-id="d03f1-108">啟用和排程資料重新整理</span><span class="sxs-lookup"><span data-stu-id="d03f1-108">Enable and schedule data refresh</span></span>](#drenablesched)  
  
 [<span data-ttu-id="d03f1-109">確認資料重新整理</span><span class="sxs-lookup"><span data-stu-id="d03f1-109">Verify Data Refresh</span></span>](#drverify)  
  
> [!NOTE]  
>  <span data-ttu-id="d03f1-110">PowerPivot 資料重新整理是由在 SharePoint 伺服陣列中的 Analysis Services 伺服器執行個體所執行。</span><span class="sxs-lookup"><span data-stu-id="d03f1-110">PowerPivot data refresh is performed by Analysis Services server instances in the SharePoint farm.</span></span> <span data-ttu-id="d03f1-111">它與在 Excel Services 中提供的資料重新整理功能不相關。</span><span class="sxs-lookup"><span data-stu-id="d03f1-111">It is not related to the data refresh feature that is provided in Excel Services.</span></span> <span data-ttu-id="d03f1-112">PowePivot 排程資料重新整理功能不會重新整理非 PowerPivot 資料。</span><span class="sxs-lookup"><span data-stu-id="d03f1-112">The PowePivot Schedule data refresh feature will not refresh non PowerPivot data.</span></span>  
  
##  <a name="prerequisites"></a><a name="prereq"></a> <span data-ttu-id="d03f1-113">必要條件</span><span class="sxs-lookup"><span data-stu-id="d03f1-113">Prerequisites</span></span>  
 <span data-ttu-id="d03f1-114">您必須在活頁簿上擁有「參與」權限層級或更高的權限層級，才能建立資料重新整理排程。</span><span class="sxs-lookup"><span data-stu-id="d03f1-114">You must have Contribute level of permission or greater on the workbook to create a data refresh schedule.</span></span>  
  
 <span data-ttu-id="d03f1-115">在資料重新整理期間所存取的外部資料來源必須是可用的，而且您在排程中指定的認證必須具有存取這些資料來源的權限。</span><span class="sxs-lookup"><span data-stu-id="d03f1-115">External data sources that are accessed during data refresh must be available and the credentials you specify in the schedule must have permission to access those data sources.</span></span> <span data-ttu-id="d03f1-116">排程資料重新整理需要可透過網路連線存取的資料來源位置 (例如，從網路檔案共用，而非您工作站上的本機資料夾)。</span><span class="sxs-lookup"><span data-stu-id="d03f1-116">Scheduled data refresh requires a data source location that is accessible over a network connection (for example, from a network file share rather than a local folder on your workstation).</span></span>  
  
 <span data-ttu-id="d03f1-117">資料來源不得為 Office 文件或 Access 資料庫。</span><span class="sxs-lookup"><span data-stu-id="d03f1-117">The data source cannot be an Office document or Access database.</span></span> <span data-ttu-id="d03f1-118">Office 不支援在伺服器環境中使用 Office 資料連接元件。</span><span class="sxs-lookup"><span data-stu-id="d03f1-118">Office does not support the use of the Office data connectivity components in a server environment.</span></span> <span data-ttu-id="d03f1-119">如果您的活頁簿中包含這些來源中的資料，請務必從資料重新整理排程中的資料來源清單移除這些來源。</span><span class="sxs-lookup"><span data-stu-id="d03f1-119">If your workbook contains data from these sources, be sure to remove those sources from the data source list in your data refresh schedule.</span></span>  
  
 <span data-ttu-id="d03f1-120">活頁簿必須是 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 版本。</span><span class="sxs-lookup"><span data-stu-id="d03f1-120">The workbook must be a [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] version.</span></span> <span data-ttu-id="d03f1-121">如果您使用在舊版 PowerPivot for Excel 中建立的活頁簿，除非您將資料庫升級到最新版本，否則排程資料重新整理無法運作。</span><span class="sxs-lookup"><span data-stu-id="d03f1-121">If you use workbooks that were created in the previous release of PowerPivot for Excel, schedule data refresh will not work unless you upgrade the database to the most recent version.</span></span>  
  
 <span data-ttu-id="d03f1-122">在完成重新整理作業時必須簽入活頁簿。</span><span class="sxs-lookup"><span data-stu-id="d03f1-122">The workbook must be checked in at the time the refresh operation is finished.</span></span> <span data-ttu-id="d03f1-123">活頁簿的鎖定是在資料重新整理結束時，在儲存檔案時對檔案施加鎖定，而不是在重新整理開始時。</span><span class="sxs-lookup"><span data-stu-id="d03f1-123">A lock on the workbook is placed on the file at the end of data refresh, when the file is saved, rather than when refresh starts.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d03f1-124">當資料重新整理正在進行中時，伺服器不會鎖定活頁簿。</span><span class="sxs-lookup"><span data-stu-id="d03f1-124">The server does not lock the workbook while the data refresh is in progress.</span></span> <span data-ttu-id="d03f1-125">不過，它會在資料重新整理結束時鎖定檔案，以簽入更新的檔案。</span><span class="sxs-lookup"><span data-stu-id="d03f1-125">However, it does lock the file at the end of data refresh for the purpose of checking in the updated file.</span></span> <span data-ttu-id="d03f1-126">如果目前已將檔案簽出給另一個使用者，將會擲回重新整理的資料。同樣地，如果檔案已簽入，但它與在資料重新整理開始時所抓取的複本截然不同，則會捨棄重新整理的資料。</span><span class="sxs-lookup"><span data-stu-id="d03f1-126">If at this time, the file is checked out to another user, the refreshed data will be thrown out. Similarly, if the file is checked in, but it is significantly different from the copy retrieved by the server at the start of data refresh, the refreshed data will be discarded.</span></span>  
  
##  <a name="data-refresh-overview"></a><a name="intro"></a><span data-ttu-id="d03f1-127">資料重新整理總覽</span><span class="sxs-lookup"><span data-stu-id="d03f1-127">Data Refresh Overview</span></span>  
 <span data-ttu-id="d03f1-128">Excel 活頁簿中的 PowerPivot 資料可能源自多個外部資料來源，包括您從遠端伺服器或網路檔案共用存取的外部資料庫或資料檔案。</span><span class="sxs-lookup"><span data-stu-id="d03f1-128">PowerPivot data in an Excel workbook can originate from multiple external data sources, including external databases or data files that you access from remote servers or network file shares.</span></span> <span data-ttu-id="d03f1-129">對於包含從連接或外部資料來源匯入之資料的 PowerPivot 活頁簿，您可以設定資料重新整理，以便排程從這些原始來源自動匯入更新資料。</span><span class="sxs-lookup"><span data-stu-id="d03f1-129">For PowerPivot workbooks that contain imported data from connected or external data sources, you can configure data refresh to schedule an automatic import of updated data from those original sources.</span></span>  
  
 <span data-ttu-id="d03f1-130">外部資料來源是透過您指定的內嵌連接字串、URL 或 UNC 路徑來存取，這些是您在使用 PowerPivot 用戶端應用程式，將原始資料匯入活頁簿時所指定。</span><span class="sxs-lookup"><span data-stu-id="d03f1-130">An external data source is accessed through an embedded connection string, URL, or UNC path that you specified when you imported the original data into the workbook using the PowerPivot client application.</span></span> <span data-ttu-id="d03f1-131">儲存在 PowerPivot 活頁簿中的原始連接資訊會在後續的資料重新整理作業中重複使用。</span><span class="sxs-lookup"><span data-stu-id="d03f1-131">Original connection information that is stored in the PowerPivot workbook is reused for subsequent data refresh operations.</span></span> <span data-ttu-id="d03f1-132">您可以覆寫用來連接資料來源的認證，但是您無法覆寫用於資料重新整理的連接字串；僅能使用現有的連接資訊。</span><span class="sxs-lookup"><span data-stu-id="d03f1-132">Although you can overwrite credentials used to connect to data sources, you cannot overwrite connection strings for data refresh purposes; only existing connection information is used.</span></span>  
  
 <span data-ttu-id="d03f1-133">每個活頁簿中，只有一個資料重新整理排程頁面，在該頁面上指定所有排程資訊。</span><span class="sxs-lookup"><span data-stu-id="d03f1-133">There is only one data refresh schedule page for each workbook, and all schedule information is specified on that page.</span></span> <span data-ttu-id="d03f1-134">一般而言，撰寫活頁簿的人員會定義排程。</span><span class="sxs-lookup"><span data-stu-id="d03f1-134">Typically, the person who authored the workbook defines the schedule.</span></span>  
  
 <span data-ttu-id="d03f1-135">身為排程擁有者，您將會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="d03f1-135">As the schedule owner, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="d03f1-136">定義預設排程。</span><span class="sxs-lookup"><span data-stu-id="d03f1-136">Define the default schedule.</span></span> <span data-ttu-id="d03f1-137">這就是在資料來源層級上沒有定義排程時所用的排程。</span><span class="sxs-lookup"><span data-stu-id="d03f1-137">This is the schedule that is used if there are no scheduled defined at the data source level.</span></span>  
  
-   <span data-ttu-id="d03f1-138">指定用來執行資料重新整理的認證。</span><span class="sxs-lookup"><span data-stu-id="d03f1-138">Specify the credentials used to run data refresh</span></span>  
  
-   <span data-ttu-id="d03f1-139">選擇要包含在重新整理作業中的資料來源。</span><span class="sxs-lookup"><span data-stu-id="d03f1-139">Choose which data sources to include in the refresh operation.</span></span>  
  
-   <span data-ttu-id="d03f1-140">選擇性地為資料重新整理期間查詢的每個資料來源，指定內嵌、個別的排程及認證。</span><span class="sxs-lookup"><span data-stu-id="d03f1-140">Optionally, specify in-line, individual schedules and credentials for each data source that is queried during data refresh.</span></span> <span data-ttu-id="d03f1-141">每個資料來源可獨立重新整理。</span><span class="sxs-lookup"><span data-stu-id="d03f1-141">Each data source can be refreshed independently.</span></span> <span data-ttu-id="d03f1-142">如果您為每個資料來源建立自訂排程，就會忽略預設排程。</span><span class="sxs-lookup"><span data-stu-id="d03f1-142">If you create custom schedules for every data source, the default schedule is ignored.</span></span>  
  
 <span data-ttu-id="d03f1-143">為個別的資料來源建立細微的排程，可讓您使重新整理排程符合外部資料來源的波動。</span><span class="sxs-lookup"><span data-stu-id="d03f1-143">Creating granular schedules for individual data sources enables you to match the refresh schedule to fluctuations in the external data sources.</span></span> <span data-ttu-id="d03f1-144">例如，如果外部資料來源包含在一天內產生的交易資料，則可以為該資料來源建立個別的資料重新整理排程，以取得它每晚的更新資訊。</span><span class="sxs-lookup"><span data-stu-id="d03f1-144">For example, if an external data source contains transactional data that is generated throughout the day, you can create an individual data refresh schedule for that data source to get its updated information nightly.</span></span>  
  
##  <a name="enable-and-schedule-data-refresh"></a><a name="drenablesched"></a><span data-ttu-id="d03f1-145">啟用和排程資料重新整理</span><span class="sxs-lookup"><span data-stu-id="d03f1-145">Enable and schedule data refresh</span></span>  
 <span data-ttu-id="d03f1-146">請使用下列指示，來為已發行到 SharePoint 文件庫之 Excel 活頁簿中的 PowerPivot 資料，排程資料重新整理。</span><span class="sxs-lookup"><span data-stu-id="d03f1-146">Use the following instructions to schedule data refresh for PowerPivot data in an Excel workbook that is published to a SharePoint library.</span></span>  
  
1.  <span data-ttu-id="d03f1-147">在包含活頁簿的文件庫中選取活頁簿，然後按一下向下箭號以顯示命令清單。</span><span class="sxs-lookup"><span data-stu-id="d03f1-147">In the library that contains the workbook, select the workbook and then click the down arrow to display a list of commands.</span></span>  
  
2.  <span data-ttu-id="d03f1-148">按一下 **[管理 PowerPivot 資料重新整理]**。</span><span class="sxs-lookup"><span data-stu-id="d03f1-148">Click **Manage PowerPivot Data Refresh**.</span></span> <span data-ttu-id="d03f1-149">如果已經定義資料重新整理排程，則會改看到 [檢視資料重新整理] 記錄頁面。</span><span class="sxs-lookup"><span data-stu-id="d03f1-149">If a data refresh schedule is already defined, you will see the View Data Refresh history page instead.</span></span> <span data-ttu-id="d03f1-150">您可以按一下 **[設定資料重新整理]** 以開啟排程定義頁面。</span><span class="sxs-lookup"><span data-stu-id="d03f1-150">You can click **Configure data refresh** to open the schedule definition page.</span></span>  
  
3.  <span data-ttu-id="d03f1-151">在排程定義頁面中，選取 **[啟用]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="d03f1-151">In the schedule definition page, select the **Enable** checkbox.</span></span>  
  
4.  <span data-ttu-id="d03f1-152">在 [排程詳細資料] 中，指定排程的類型並指定其詳細資料。</span><span class="sxs-lookup"><span data-stu-id="d03f1-152">In Schedule Details, specify the type of schedule and specify its details.</span></span> <span data-ttu-id="d03f1-153">此步驟建立預設排程。</span><span class="sxs-lookup"><span data-stu-id="d03f1-153">This step creates the default schedule.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="d03f1-154">請務必選取 **[並且盡快重新整理]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="d03f1-154">Be sure to select the **Also refresh as soon as possible** checkbox.</span></span> <span data-ttu-id="d03f1-155">此選項可讓您驗證此活頁簿的資料重新整理功能是否可運作。</span><span class="sxs-lookup"><span data-stu-id="d03f1-155">Doing so lets you verify that data refresh is operational for this workbook.</span></span> <span data-ttu-id="d03f1-156">請注意，當您儲存排程時，最多可能需要一分鐘的時間，資料重新整理功能才會開始執行。</span><span class="sxs-lookup"><span data-stu-id="d03f1-156">Note that after you save schedule, it can take up to a minute for data refresh to start.</span></span>  
  
5.  <span data-ttu-id="d03f1-157">在 [最早開始時間] 中選擇下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="d03f1-157">In Earliest Start Time, choose one of the following:</span></span>  
  
    1.  <span data-ttu-id="d03f1-158">**[下班後]** 會指定下班之後的處理時段，此時資料庫伺服器很有可能已經收集到整個工作日所產生的最新資料。</span><span class="sxs-lookup"><span data-stu-id="d03f1-158">**After business hours** specifies an off-hours processing period when database servers are more likely to have current data that was generated throughout the business day.</span></span>  
  
    2.  <span data-ttu-id="d03f1-159">**[特定最早開始時間]** 是將資料重新整理要求加入處理佇列當日最早的時分。</span><span class="sxs-lookup"><span data-stu-id="d03f1-159">**Specific earliest start time** is the hour and minutes of the earliest time of day the data refresh request is added to a process queue.</span></span> <span data-ttu-id="d03f1-160">您可以用 15 分鐘的間隔指定分鐘。</span><span class="sxs-lookup"><span data-stu-id="d03f1-160">You can specify minutes in 15-minute intervals.</span></span> <span data-ttu-id="d03f1-161">此設定會套用到目前日期及未來日期。</span><span class="sxs-lookup"><span data-stu-id="d03f1-161">The setting applies to the current day as well as future dates.</span></span> <span data-ttu-id="d03f1-162">例如，如果您指定的值為早上 6 點 30 分，</span><span class="sxs-lookup"><span data-stu-id="d03f1-162">For example, if you specify a value of 6:30 A.M.</span></span> <span data-ttu-id="d03f1-163">而目前時間為下午 4 點 30 分，重新整理要求將會加入目前日期的佇列，因為下午 4 點 30 分</span><span class="sxs-lookup"><span data-stu-id="d03f1-163">and the current time is 4:30 P.M., the refresh request will be added to the queue in the current day because 4:30 P.M.</span></span> <span data-ttu-id="d03f1-164">在早上 6 點 30 分之後。</span><span class="sxs-lookup"><span data-stu-id="d03f1-164">is after 6:30 A.M.</span></span>  
  
     <span data-ttu-id="d03f1-165">[最早開始時間] 定義要求加入處理佇列的時間。</span><span class="sxs-lookup"><span data-stu-id="d03f1-165">Earliest start time defines when a request is added to the process queue.</span></span> <span data-ttu-id="d03f1-166">實際的處理會發生於伺服器有足夠的資源開始資料處理。</span><span class="sxs-lookup"><span data-stu-id="d03f1-166">Actual processing occurs when the server has adequate resources to begin data processing.</span></span> <span data-ttu-id="d03f1-167">在處理完成後，就會將實際處理時間記錄在資料重新整理記錄中。</span><span class="sxs-lookup"><span data-stu-id="d03f1-167">Actual processing time will be recorded in data refresh history after processing is complete.</span></span>  
  
6.  <span data-ttu-id="d03f1-168">選取 **[並且盡快重新整理]** 核取方塊，以便在伺服器可以處理資料重新整理時，盡快執行。</span><span class="sxs-lookup"><span data-stu-id="d03f1-168">Select the checkbox **Also refresh as soon as possible** to run data refresh as soon as the server can process it.</span></span> <span data-ttu-id="d03f1-169">成功的資料重新整理作業結果會確認資料來源可以使用，而且權限和伺服器組態的設定正確。</span><span class="sxs-lookup"><span data-stu-id="d03f1-169">A successful outcome of a data refresh job verifies that the data sources are available and that permissions and server configuration are set correctly.</span></span>  
  
7.  <span data-ttu-id="d03f1-170">在 [電子郵件通知] 中，輸入發生處理錯誤時要通知之人員的電子郵件地址。</span><span class="sxs-lookup"><span data-stu-id="d03f1-170">In E-mail notifications, enter the e-mail address of the person who should be notified in the event of a processing error.</span></span>  
  
8.  <span data-ttu-id="d03f1-171">在 [認證] 中，指定用來執行資料重新整理作業的帳戶。</span><span class="sxs-lookup"><span data-stu-id="d03f1-171">In Credentials, specify an account used to run the data refresh job.</span></span> <span data-ttu-id="d03f1-172">此帳戶必須在活頁簿上具有「參與」權限，讓它可以開啟活頁簿來重新整理其資料。</span><span class="sxs-lookup"><span data-stu-id="d03f1-172">The account must have Contribute permissions on the workbook so that it can open the workbook to refresh its data.</span></span> <span data-ttu-id="d03f1-173">它必須是 Windows 網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="d03f1-173">It must be a Windows domain user account.</span></span> <span data-ttu-id="d03f1-174">在許多情況下，此帳戶也必須擁有資料重新整理期間所使用之外部資料來源的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="d03f1-174">In many cases, this account must also have read permissions on the external data sources used during data refresh.</span></span> <span data-ttu-id="d03f1-175">具體地說，如果您原本使用 [使用 Windows 驗證] 選項匯入資料，則會建立連接字串來使用目前使用者的 Windows 認證。</span><span class="sxs-lookup"><span data-stu-id="d03f1-175">Specifically, if you originally imported the data using the Use Windows Authentication option, then the connection string is built to use the Windows credentials of the current user.</span></span> <span data-ttu-id="d03f1-176">如果目前的使用者是資料重新整理帳戶，該帳戶必須擁有外部資料來源的讀取權限，資料重新整理才會成功。</span><span class="sxs-lookup"><span data-stu-id="d03f1-176">If the current user is the data refresh account, that account must have read permissions on the external data source in order for data refresh to succeed.</span></span> <span data-ttu-id="d03f1-177">選擇下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="d03f1-177">Choose one of the following options:</span></span>  
  
    1.  <span data-ttu-id="d03f1-178">選擇 **[使用系統管理員設定的資料重新整理帳戶]** 來使用 PowerPivot 自動資料重新整理帳戶處理資料重新整理作業。</span><span class="sxs-lookup"><span data-stu-id="d03f1-178">Choose **Use the data refresh account configured by the administrator** to process the data refresh operation using the PowerPivot unattended data refresh account.</span></span>  
  
    2.  <span data-ttu-id="d03f1-179">如果您想要輸入使用者名稱和密碼，選擇 **[使用下列 Windows 使用者認證連接]** 。</span><span class="sxs-lookup"><span data-stu-id="d03f1-179">Choose **Connect using the following Windows user credentials** if you want to enter a user name and password.</span></span> <span data-ttu-id="d03f1-180">請以 domain\user 的格式輸入帳戶資訊。</span><span class="sxs-lookup"><span data-stu-id="d03f1-180">Enter the account information in domain\user format.</span></span>  
  
    3.  <span data-ttu-id="d03f1-181">如果您知道目標應用程式的識別碼 (其中包含您要使用之先前儲存的認證)，選擇 **[使用儲存在 Secure Store Service 中的認證連接]** 。</span><span class="sxs-lookup"><span data-stu-id="d03f1-181">Choose **Connect using the credentials saved in Secure Store Service** if you know the ID of a target application that contains previously stored credentials you want to use.</span></span>  
  
     <span data-ttu-id="d03f1-182">如需這些選項的詳細資訊，請參閱[設定 Powerpivot 資料重新整理的預存認證 &#40;PowerPivot for SharePoint&#41;](configure-stored-credentials-data-refresh-powerpivot-sharepoint.md)並[設定 Powerpivot 無人看管的資料重新整理帳戶 &#40;PowerPivot for SharePoint&#41;](configure-unattended-data-refresh-account-powerpivot-sharepoint.md)。</span><span class="sxs-lookup"><span data-stu-id="d03f1-182">For more information about these options, see [Configure Stored Credentials for PowerPivot Data Refresh &#40;PowerPivot for SharePoint&#41;](configure-stored-credentials-data-refresh-powerpivot-sharepoint.md) and [Configure the PowerPivot Unattended Data Refresh Account &#40;PowerPivot for SharePoint&#41;](configure-unattended-data-refresh-account-powerpivot-sharepoint.md).</span></span>  
  
9. <span data-ttu-id="d03f1-183">如果您要資料重新整理重新查詢所有的原始資料來源，則選取 [資料來源] 中的 **[所有資料來源]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="d03f1-183">In Data Sources, select the **All data sources** checkbox if you want data refresh to re-query all of the original data sources.</span></span>  
  
     <span data-ttu-id="d03f1-184">如果您選取這個選項，提供 PowerPivot 資料的任何外部資料來源都會自動包含在重新整理中，即使隨著您加入或移除提供資料給活頁簿的資料來源，而使得資料來源清單經過一段時間後已變更也是如此。</span><span class="sxs-lookup"><span data-stu-id="d03f1-184">If you select this option, any external data source that provides PowerPivot data is automatically included in the refresh, even if the list of data sources changes over time as you add or remove data sources that provide data to the workbook.</span></span>  
  
     <span data-ttu-id="d03f1-185">如果您要以手動方式選取要併入處理的資料來源，請清除 **[所有資料來源]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="d03f1-185">Clear the **All data sources** checkbox if you want to manually select which data sources to include.</span></span> <span data-ttu-id="d03f1-186">如果您稍後會加入新資料來源以修改活頁簿，請務必更新排程中的資料來源清單。</span><span class="sxs-lookup"><span data-stu-id="d03f1-186">If you later modify the workbook by adding a new data source, be sure to update the data source list in the schedule.</span></span> <span data-ttu-id="d03f1-187">否則，較新的資料來源將不會包含在重新整理作業中。</span><span class="sxs-lookup"><span data-stu-id="d03f1-187">Otherwise, newer data sources will not be included in the refresh operation.</span></span>  
  
     <span data-ttu-id="d03f1-188">您可以選擇的資料來源清單是在開啟活頁簿的 [管理 PowerPivot 資料重新整理] 頁面時，從 PowerPivot 活頁簿擷取的。</span><span class="sxs-lookup"><span data-stu-id="d03f1-188">The list of data sources that you can choose from is retrieved from the PowerPivot workbook when you open the Manage PowerPivot Data Refresh page for the workbook.</span></span>  
  
     <span data-ttu-id="d03f1-189">請務必只選取符合下列準則的資料來源：</span><span class="sxs-lookup"><span data-stu-id="d03f1-189">Be sure to select only those data sources that meet the following criteria:</span></span>  
  
    -   <span data-ttu-id="d03f1-190">資料來源必須可在執行資料重新整理時使用，並且也可在指定的位置使用。</span><span class="sxs-lookup"><span data-stu-id="d03f1-190">The data source must be available at the time that data refresh occurs and at the stated location.</span></span> <span data-ttu-id="d03f1-191">如果原始資料來源是位於撰寫活頁簿之人員的本機磁碟機上，則必須從資料重新整理作業排除該資料來源，或設法將該資料來源發行到可透過網路連接存取的位置。</span><span class="sxs-lookup"><span data-stu-id="d03f1-191">If the original data source is on a local disk drive of the person who authored the workbook, you must either exclude that data source from the data refresh operation, or find a way to publish that data source to a location that is accessible through a network connection.</span></span> <span data-ttu-id="d03f1-192">如果您將資料來源移至某個網路位置，請務必在 [!INCLUDE[ssGeminiClient](../includes/ssgeminiclient-md.md)] 中開啟活頁簿，並更新資料來源連接資訊。</span><span class="sxs-lookup"><span data-stu-id="d03f1-192">If you move a data source to a network location, be sure to open the workbook in [!INCLUDE[ssGeminiClient](../includes/ssgeminiclient-md.md)] and update the data source connection information.</span></span> <span data-ttu-id="d03f1-193">這是重新建立儲存在 PowerPivot 活頁簿的連接資訊所必須執行的動作。</span><span class="sxs-lookup"><span data-stu-id="d03f1-193">This is necessary to re-establish the connection information that is stored in the PowerPivot workbook.</span></span>  
  
    -   <span data-ttu-id="d03f1-194">您必須使用內嵌在 PowerPivot 活頁簿或是在排程中指定的認證資訊，來存取資料來源。</span><span class="sxs-lookup"><span data-stu-id="d03f1-194">The data source must be accessed using the credential information that is embedded in the PowerPivot workbook or that is specified in the schedule.</span></span> <span data-ttu-id="d03f1-195">當您使用 PowerPivot for Excel 匯入資料時，會在 PowerPivot 活頁簿中儲存內嵌的認證資訊。</span><span class="sxs-lookup"><span data-stu-id="d03f1-195">Embedded credential information is stored in the PowerPivot workbook when you import data using PowerPivot for Excel.</span></span> <span data-ttu-id="d03f1-196">內嵌的認證資訊通常是 SSPI=IntegratedSecurity 或 SSPI=TrustedConnection，表示使用目前使用者的認證連接到資料來源。</span><span class="sxs-lookup"><span data-stu-id="d03f1-196">Embedded credential information is often SSPI=IntegratedSecurity or SSPI=TrustedConnection, which means use the credentials of the current user to connect to the data source.</span></span> <span data-ttu-id="d03f1-197">如果您要覆寫資料重新整理排程中的認證資訊，可以指定預先定義的預存認證。</span><span class="sxs-lookup"><span data-stu-id="d03f1-197">If you want to override the credential information in your data refresh schedule, you can specify predefined, stored credentials.</span></span> <span data-ttu-id="d03f1-198">如需詳細資訊，請參閱[設定 PowerPivot 資料重新整理的預存認證 &#40;PowerPivot for SharePoint&#41;](configure-stored-credentials-data-refresh-powerpivot-sharepoint.md)。</span><span class="sxs-lookup"><span data-stu-id="d03f1-198">For more information, see [Configure Stored Credentials for PowerPivot Data Refresh &#40;PowerPivot for SharePoint&#41;](configure-stored-credentials-data-refresh-powerpivot-sharepoint.md).</span></span>  
  
    -   <span data-ttu-id="d03f1-199">您指定的所有資料來源的都必須能夠順利執行資料重新整理。</span><span class="sxs-lookup"><span data-stu-id="d03f1-199">Data refresh must succeed for all of the data sources that you specify.</span></span> <span data-ttu-id="d03f1-200">否則，這項作業會捨棄重新整理的資料，僅保留活頁簿最後儲存的版本。</span><span class="sxs-lookup"><span data-stu-id="d03f1-200">Otherwise, the refreshed data is discarded, leaving you with the last saved version of the workbook.</span></span> <span data-ttu-id="d03f1-201">請排除任何您不確定的資料來源。</span><span class="sxs-lookup"><span data-stu-id="d03f1-201">Exclude any data sources that you are not sure about.</span></span>  
  
    -   <span data-ttu-id="d03f1-202">資料重新整理必須不能使活頁簿中的其他資料失效。</span><span class="sxs-lookup"><span data-stu-id="d03f1-202">Data refresh must not invalidate other data in your workbook.</span></span> <span data-ttu-id="d03f1-203">當您重新整理資料子集時，請務必了解一旦較新的資料與不是來自相同時間週期的靜態資料彙總後，活頁簿是否仍然為有效。</span><span class="sxs-lookup"><span data-stu-id="d03f1-203">When you refresh a subset of your data, it is important that you understand whether the workbook is still valid once newer data is aggregated with static data that is not from the same time period.</span></span> <span data-ttu-id="d03f1-204">身為活頁簿的作者，您必須知道資料的相依性，並確定資料重新整理是否適用於活頁簿本身。</span><span class="sxs-lookup"><span data-stu-id="d03f1-204">As a workbook author, it is up to you to know your data dependencies and ensure that data refresh is appropriate for the workbook itself.</span></span>  
  
10. <span data-ttu-id="d03f1-205">您可以選擇性地定義特定資料來源的個別排程。</span><span class="sxs-lookup"><span data-stu-id="d03f1-205">Optionally, you can define individual schedules for specific data sources.</span></span> <span data-ttu-id="d03f1-206">這對於您將原始資料來源設定成按照排程自行更新非常有用。</span><span class="sxs-lookup"><span data-stu-id="d03f1-206">This is useful if you have original data sources that are themselves updated on a schedule.</span></span> <span data-ttu-id="d03f1-207">例如，如果 PowerPivot 資料來源使用的資料，是來自每週一凌晨 02:00 會重新整理的資料超市，則可以為資料超市定義內嵌排程，以便在每週一的凌晨 04:00 擷取其重新整理的資料。</span><span class="sxs-lookup"><span data-stu-id="d03f1-207">For example, if a PowerPivot data source uses data from a data mart that is refreshed every Monday at 02:00 hours, you can define an inline schedule for the data mart to retrieve its refreshed data every Monday at 04:00 hours.</span></span>  
  
11. <span data-ttu-id="d03f1-208">按一下 **[確定]** 以儲存排程。</span><span class="sxs-lookup"><span data-stu-id="d03f1-208">Click **OK** to save your schedule.</span></span>  
  
##  <a name="verify-data-refresh"></a><a name="drverify"></a><span data-ttu-id="d03f1-209">確認資料重新整理</span><span class="sxs-lookup"><span data-stu-id="d03f1-209">Verify Data Refresh</span></span>  
 <span data-ttu-id="d03f1-210">確認資料重新整理最好的方式，就是立即執行資料重新整理，然後檢閱記錄頁面來查看是否成功完成。</span><span class="sxs-lookup"><span data-stu-id="d03f1-210">The best way to verify data refresh is to execute data refresh right away and then review the history page to see whether it completed successfully.</span></span> <span data-ttu-id="d03f1-211">選取排程上的 **[並且盡快重新整理]** 核取方塊將會提供資料重新整理可以運作的驗證。</span><span class="sxs-lookup"><span data-stu-id="d03f1-211">Selecting the **Also refresh as soon as possible** checkbox on your schedule will provide the verification that data refresh is operational.</span></span>  
  
 <span data-ttu-id="d03f1-212">您可以在活頁簿的 [資料重新整理記錄] 頁面中，檢視資料重新整理作業的目前和過去記錄。</span><span class="sxs-lookup"><span data-stu-id="d03f1-212">You can view the current and past record of data refresh operations in the Data Refresh History page for the workbook.</span></span> <span data-ttu-id="d03f1-213">這個頁面只有在已經為活頁簿排程資料重新整理才會出現。</span><span class="sxs-lookup"><span data-stu-id="d03f1-213">This page only appears if data refresh has been scheduled for a workbook.</span></span> <span data-ttu-id="d03f1-214">如果沒有任何資料重新整理排程，就會改出現排程定義頁面。</span><span class="sxs-lookup"><span data-stu-id="d03f1-214">If there is no data refresh schedule, the schedule definition page appears instead.</span></span>  
  
 <span data-ttu-id="d03f1-215">您必須擁有「參與」權限或更大的權限，才能檢視資料重新整理記錄。</span><span class="sxs-lookup"><span data-stu-id="d03f1-215">You must have Contribute permissions or greater to view data refresh history.</span></span>  
  
1.  <span data-ttu-id="d03f1-216">在 SharePoint 網站上，開啟包含 PowerPivot 活頁簿的文件庫。</span><span class="sxs-lookup"><span data-stu-id="d03f1-216">On a SharePoint site, open the library that contains a PowerPivot workbook.</span></span>  
  
     <span data-ttu-id="d03f1-217">沒有任何視覺指標，可識別在 SharePoint 文件庫中的哪個活頁簿包含 PowerPivot 資料。</span><span class="sxs-lookup"><span data-stu-id="d03f1-217">There is no visual indicator that identifies which workbooks in a SharePoint library contain PowerPivot data.</span></span> <span data-ttu-id="d03f1-218">您必須事先知道哪個活頁簿包含可重新整理的 PowerPivot 資料。</span><span class="sxs-lookup"><span data-stu-id="d03f1-218">You must know in advance which workbooks contain refreshable PowerPivot data.</span></span>  
  
2.  <span data-ttu-id="d03f1-219">選取文件，然後按一下出現在右邊的向下箭號。</span><span class="sxs-lookup"><span data-stu-id="d03f1-219">Select the document, and then click the down arrow that appears to the right.</span></span>  
  
3.  <span data-ttu-id="d03f1-220">選取 **[管理 PowerPivot 資料重新整理]**。</span><span class="sxs-lookup"><span data-stu-id="d03f1-220">Select **Manage PowerPivot Data Refresh**.</span></span>  
  
 <span data-ttu-id="d03f1-221">隨即顯示記錄頁面，以顯示在目前 Excel 活頁簿中為 PowerPivot 資料顯示所有重新整理活動的完整記錄，包含最近的資料重新整理作業狀態。</span><span class="sxs-lookup"><span data-stu-id="d03f1-221">The history page appears, showing a complete record for all refresh activity for PowerPivot data in the current Excel workbook, including the status of the most recent data refresh operation.</span></span>  
  
 <span data-ttu-id="d03f1-222">在某些情況下，您可能會看到實際的處理時間，與您指定的時間並不同。</span><span class="sxs-lookup"><span data-stu-id="d03f1-222">In some cases, you might see actual processing times that differ from the time you specified.</span></span> <span data-ttu-id="d03f1-223">如果在伺服器上處理負載繁重，就會發生這樣的情況。</span><span class="sxs-lookup"><span data-stu-id="d03f1-223">This will occur if there is a heavy processing load on the server.</span></span> <span data-ttu-id="d03f1-224">在繁重的負載下， [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] 服務執行個體將會等到有足夠的系統資源釋放後，才開始進行資料重新整理。</span><span class="sxs-lookup"><span data-stu-id="d03f1-224">Under heavy load, the [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] service instance will wait until enough system resources are free before it begins a data refresh.</span></span>  
  
 <span data-ttu-id="d03f1-225">在完成重新整理作業時必須簽入活頁簿。</span><span class="sxs-lookup"><span data-stu-id="d03f1-225">The workbook must be checked in when the refresh operation is finished.</span></span> <span data-ttu-id="d03f1-226">活頁簿會在該時間隨重新整理的資料一起儲存。</span><span class="sxs-lookup"><span data-stu-id="d03f1-226">The workbook will be saved with the refreshed data at that time.</span></span> <span data-ttu-id="d03f1-227">如果檔案已簽出，則會略過資料重新整理，直到下一個排程時間為止。</span><span class="sxs-lookup"><span data-stu-id="d03f1-227">If the file is checked out, data refresh is skipped until the next scheduled time.</span></span>  
  
 <span data-ttu-id="d03f1-228">如果您看到非預期的狀態訊息 (例如，重新整理作業失敗或已取消)，則可以檢查權限和伺服器可用性，來調查該問題。</span><span class="sxs-lookup"><span data-stu-id="d03f1-228">If you see a status message that is unexpected (for example, a refresh operation failed or was cancelled), you can investigate the problem by checking permissions and server availability.</span></span>  
  
 <span data-ttu-id="d03f1-229">請檢閱 TechNet WIKI 上的 PowerPivot 資料重新整理疑難排解頁面，以取得解決資料重新整理問題的協助。</span><span class="sxs-lookup"><span data-stu-id="d03f1-229">Review the PowerPivot data refresh troubleshooting page on the TechNet WIKI for help on resolving data refresh problems.</span></span> <span data-ttu-id="d03f1-230">如需詳細資訊，請參閱 [PowerPivot 資料重新整理疑難排解](https://go.microsoft.com/fwlink/?LinkId=251594)。</span><span class="sxs-lookup"><span data-stu-id="d03f1-230">For more information see [Troubleshooting PowerPivot Data Refresh](https://go.microsoft.com/fwlink/?LinkId=251594).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d03f1-231">SharePoint 管理員可以透過在管理中心的 PowerPivot 管理儀表板中檢視合併的資料重新整理報表來協助您疑難排解資料重新整理問題。</span><span class="sxs-lookup"><span data-stu-id="d03f1-231">SharePoint administrators can help you troubleshoot data refresh problems by viewing the consolidated data refresh reports in the PowerPivot Management Dashboard in Central Administration.</span></span> <span data-ttu-id="d03f1-232">如需詳細資訊，請參閱＜ [PowerPivot Management Dashboard and Usage Data](power-pivot-sharepoint/power-pivot-management-dashboard-and-usage-data.md)＞。</span><span class="sxs-lookup"><span data-stu-id="d03f1-232">For more information, see [PowerPivot Management Dashboard and Usage Data](power-pivot-sharepoint/power-pivot-management-dashboard-and-usage-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d03f1-233">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d03f1-233">See Also</span></span>  
 <span data-ttu-id="d03f1-234">[PowerPivot 資料重新整理與 SharePoint 2010](powerpivot-data-refresh-with-sharepoint-2010.md) </span><span class="sxs-lookup"><span data-stu-id="d03f1-234">[PowerPivot Data Refresh with SharePoint 2010](powerpivot-data-refresh-with-sharepoint-2010.md) </span></span>  
 <span data-ttu-id="d03f1-235">[查看資料重新整理記錄 &#40;PowerPivot for SharePoint&#41;](power-pivot-sharepoint/view-data-refresh-history-power-pivot-for-sharepoint.md) </span><span class="sxs-lookup"><span data-stu-id="d03f1-235">[View Data Refresh History &#40;PowerPivot for SharePoint&#41;](power-pivot-sharepoint/view-data-refresh-history-power-pivot-for-sharepoint.md) </span></span>  
 [<span data-ttu-id="d03f1-236">設定 PowerPivot 資料重新整理的預存認證 &#40;PowerPivot for SharePoint&#41;</span><span class="sxs-lookup"><span data-stu-id="d03f1-236">Configure Stored Credentials for PowerPivot Data Refresh &#40;PowerPivot for SharePoint&#41;</span></span>](configure-stored-credentials-data-refresh-powerpivot-sharepoint.md)  
  
  