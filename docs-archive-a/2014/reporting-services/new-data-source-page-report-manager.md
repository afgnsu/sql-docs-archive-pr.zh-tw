---
title: 新增資料來源頁面 (報表管理員) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 35563d4c-a3d5-4f95-bf46-605da9dfcbb8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8117174f23ae85cd51c30e5ad0026ab2a01be27e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598244"
---
# <a name="new-data-source-page-report-manager"></a><span data-ttu-id="4a8b6-102">新增資料來源頁面 (報表管理員)</span><span class="sxs-lookup"><span data-stu-id="4a8b6-102">New Data Source Page (Report Manager)</span></span>
  <span data-ttu-id="4a8b6-103">使用 [新增資料來源] 頁面來建立共用資料來源項目。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-103">Use the New Data Source page to create a shared data source item.</span></span> <span data-ttu-id="4a8b6-104">共用資料來源定義外部資料來源的連接。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-104">A shared data source defines a connection to an external data source.</span></span> <span data-ttu-id="4a8b6-105">您可以利用共用資料來源來建立和維護資料來源連接的設定，與使用該資料來源的報表、模型和資料驅動訂閱分開處理。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-105">With a shared data source, you can create and maintain the settings for the data source connection separately from the reports, models, and data-driven subscriptions that use the data source.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="4a8b6-106">導覽</span><span class="sxs-lookup"><span data-stu-id="4a8b6-106">Navigation</span></span>  
 <span data-ttu-id="4a8b6-107">您可以使用下列程序，在使用者介面 (UI) 中導覽至這個位置。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-107">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-new-data-source-page"></a><span data-ttu-id="4a8b6-108">若要開啟新增資料來源頁面</span><span class="sxs-lookup"><span data-stu-id="4a8b6-108">To open the New Data Source page</span></span>  
  
1.  <span data-ttu-id="4a8b6-109">開啟報表管理員中，然後導覽至您想要在其中建立資料來源的資料夾。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-109">Open Report Manager, and navigate to the folder in which you want to create a data source.</span></span>  
  
2.  <span data-ttu-id="4a8b6-110">在工具列中，按一下 **[新增資料來源]**。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-110">In the toolbar, click **New Data Source**.</span></span> <span data-ttu-id="4a8b6-111">您必須擁有「內容管理員」權限才能建立共用資料來源。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-111">You must have Content Manager permissions to create a shared data source.</span></span>  
  
## <a name="options"></a><span data-ttu-id="4a8b6-112">選項。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-112">Options</span></span>  
 <span data-ttu-id="4a8b6-113">**名稱**</span><span class="sxs-lookup"><span data-stu-id="4a8b6-113">**Name**</span></span>  
 <span data-ttu-id="4a8b6-114">輸入共用資料來源的名稱，可用來識別報表伺服器資料夾階層中的項目。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-114">Type a name for the shared data source, which is used to identify the item within the report server folder hierarchy.</span></span>  
  
 <span data-ttu-id="4a8b6-115">**說明**</span><span class="sxs-lookup"><span data-stu-id="4a8b6-115">**Description**</span></span>  
 <span data-ttu-id="4a8b6-116">提供有關共用資料來源的資訊。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-116">Provide information about the shared data source.</span></span> <span data-ttu-id="4a8b6-117">此描述會顯示在 [內容] 頁面上。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-117">This description appears on the Contents page.</span></span>  
  
 <span data-ttu-id="4a8b6-118">**在清單檢視中隱藏**</span><span class="sxs-lookup"><span data-stu-id="4a8b6-118">**Hide in list view**</span></span>  
 <span data-ttu-id="4a8b6-119">選取這個選項可以對正在「報表管理員」中使用清單檢視模式的使用者隱藏共用資料來源。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-119">Select this option to hide the shared data source from users who are using list view mode in Report Manager.</span></span> <span data-ttu-id="4a8b6-120">清單檢視模式是瀏覽報表伺服器資料夾階層時的預設檢視格式。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-120">List view mode is the default view format when browsing the report server folder hierarchy.</span></span> <span data-ttu-id="4a8b6-121">在清單檢視中，項目名稱和描述會跨頁排列。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-121">In list view, item names and descriptions flow across the page.</span></span> <span data-ttu-id="4a8b6-122">替代格式是詳細資料檢視。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-122">The alternate format is details view.</span></span> <span data-ttu-id="4a8b6-123">詳細資料檢視會省略描述，但會包括項目的其他相關資訊。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-123">Details view omits descriptions, but includes other information about the item.</span></span> <span data-ttu-id="4a8b6-124">雖然在清單檢視中可以隱藏項目，但在詳細資料檢視中則不行。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-124">Although you can hide an item in list view, you cannot hide an item in details view.</span></span> <span data-ttu-id="4a8b6-125">如果您要限制對某個項目的存取，必須建立角色指派。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-125">If you want to restrict access to an item, you must create a role assignment</span></span>  
  
 <span data-ttu-id="4a8b6-126">**啟用此資料來源**</span><span class="sxs-lookup"><span data-stu-id="4a8b6-126">**Enable this data source**</span></span>  
 <span data-ttu-id="4a8b6-127">選取以啟用或停用共用資料來源。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-127">Select to enable or disable the shared data source.</span></span> <span data-ttu-id="4a8b6-128">您可以停用共用資料來源，以避免報表處理參考該項目的所有報表和模型。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-128">You can disable the shared data source to prevent processing for all reports and models that reference the item.</span></span>  
  
 <span data-ttu-id="4a8b6-129">**資料來源類型**</span><span class="sxs-lookup"><span data-stu-id="4a8b6-129">**Data source type**</span></span>  
 <span data-ttu-id="4a8b6-130">指定用來處理資料來源之資料的資料處理延伸模組。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-130">Specify the data processing extension that is used to process data from the data source.</span></span> <span data-ttu-id="4a8b6-131">報表伺服器包括 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 、Oracle、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 、SAP、XML、ODBC 和 OLE DB 的資料處理延伸模組。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-131">Report server includes data processing extensions for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], Oracle, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], SAP, XML, ODBC, and OLE DB.</span></span> <span data-ttu-id="4a8b6-132">其他的資料處理延伸模組可向協力廠商索取。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-132">Additional data processing extensions may be available from third-party vendors.</span></span>  
  
 <span data-ttu-id="4a8b6-133">如需遠端和非 SQL 資料來源支援的詳細資訊，請參閱[SQL Server 2012 版本支援的功能](https://go.microsoft.com/fwlink/?linkid=232473) ( HYPERLINK " <https://go.microsoft.com/fwlink/?linkid=232473> " <https://go.microsoft.com/fwlink/?linkid=232473>) 和[Reporting Services &#40;SSRS&#41;支援的資料來源](create-deploy-and-manage-mobile-and-paginated-reports.md)。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-133">For more information about remote and non-SQL data source support, see [Features Supported by the Editions of SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473) ( HYPERLINK "<https://go.microsoft.com/fwlink/?linkid=232473>" <https://go.microsoft.com/fwlink/?linkid=232473>) and [Data Sources Supported by Reporting Services &#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md).</span></span>  
  
 <span data-ttu-id="4a8b6-134">**連接字串**</span><span class="sxs-lookup"><span data-stu-id="4a8b6-134">**Connection string**</span></span>  
 <span data-ttu-id="4a8b6-135">指定報表伺服器用來連接至資料來源的連接字串。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-135">Specify the connection string that the report server uses to connect to the data source.</span></span> <span data-ttu-id="4a8b6-136">連接類型決定您應該使用的語法。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-136">The connection type determines the syntax you should use.</span></span> <span data-ttu-id="4a8b6-137">例如，XML 資料處理延伸模組的連接字串是 XML 文件的 URL。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-137">For example, a connection string for the XML data processing extension is a URL to an XML document.</span></span> <span data-ttu-id="4a8b6-138">在大部分狀況下，一般連接字串會指定資料庫伺服器和資料檔案。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-138">In most cases, a typical connection string specifies the database server and a data file.</span></span>  
  
 <span data-ttu-id="4a8b6-139">下列範例說明用來連接到資料庫的連接字串 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBnormal](../includes/sssampledbnormal-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="4a8b6-139">The following example illustrates a connection string used to connect to the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssSampleDBnormal](../includes/sssampledbnormal-md.md)] database:</span></span>  
  
```  
data source=<a SQL Server instance>;initial catalog=AdventureWorks2012  
```  
  
 <span data-ttu-id="4a8b6-140">如需有關指定連接字串之不同方式的其他範例和詳細資訊，請參閱[Reporting Services 中的資料連線、資料來源和連接字串](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-140">For more examples and information about different ways to specify a connection string, see [Data Connections, Data Sources, and Connection Strings in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md).</span></span>  
  
 <span data-ttu-id="4a8b6-141">**連接使用**</span><span class="sxs-lookup"><span data-stu-id="4a8b6-141">**Connect using**</span></span>  
 <span data-ttu-id="4a8b6-142">指定決定如何取得認證的選項。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-142">Specify options that determine how credentials are obtained.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="4a8b6-143">如果連接字串中有提供認證，則此章節中所提供的選項和值將會被忽略。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-143">If credentials are provided in the connection string, the options and values provided in this section are ignored.</span></span> <span data-ttu-id="4a8b6-144">請注意，如果您在連接字串上指定認證，這些值就會以純文字的形式顯示給檢視此頁面的所有使用者查看。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-144">Note that if you specify credentials on the connection string, the values are displayed in clear text to all users who view this page.</span></span>  
  
 <span data-ttu-id="4a8b6-145">**執行報表的使用者所提供的認證 (使用下列方式連接)**</span><span class="sxs-lookup"><span data-stu-id="4a8b6-145">**Credentials supplied by the user running the report (Connect using)**</span></span>  
 <span data-ttu-id="4a8b6-146">系統會提示每一位使用者輸入使用者名稱和密碼，以存取資料來源。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-146">Each user is prompted to type in a user name and password to access the data source.</span></span> <span data-ttu-id="4a8b6-147">您可以定義要求使用者認證的提示文字。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-147">You can define the prompt text that requests user credentials.</span></span> <span data-ttu-id="4a8b6-148">預設的文字字串是「請輸入使用者名稱和密碼以存取資料來源」。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-148">The default text string is "Enter a user name and password to access the data source."</span></span>  
  
 <span data-ttu-id="4a8b6-149">如果使用者提供的認證是 Windows 驗證認證，請選取 [連接到資料來源時作為 Windows 認證] \*\*\*\* 。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-149">Select **Use as Windows credentials when connecting to the data source** if the credentials that the user provides are Windows Authentication credentials.</span></span> <span data-ttu-id="4a8b6-150">如果您是使用資料庫驗證 (例如 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證)，請勿選取此核取方塊。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-150">Do not select this check box if you are using database authentication (for example, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication).</span></span>  
  
 <span data-ttu-id="4a8b6-151">**安全地儲存在報表伺服器中的認證 (使用下列方式連接)**</span><span class="sxs-lookup"><span data-stu-id="4a8b6-151">**Credentials stored securely in the report server (Connect using)**</span></span>  
 <span data-ttu-id="4a8b6-152">在報表伺服器資料庫中儲存加密的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-152">Store an encrypted user name and password in the report server database.</span></span> <span data-ttu-id="4a8b6-153">選擇此選項即可自動執行報表 (例如，由排程或事件啟動而不是由使用者動作啟動的報表)。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-153">Choose this option to run a report unattended (for example, reports that are initiated by schedules or events instead of user action).</span></span> <span data-ttu-id="4a8b6-154">如果您要使用預設安全性，使用者名稱就必須是 Windows 網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-154">If you are using default security, the user name must be a Windows domain account.</span></span> <span data-ttu-id="4a8b6-155">請以此格式指定帳戶： \<domain> \\<username \> 。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-155">Specify the account in this format: \<domain>\\<username\>.</span></span> <span data-ttu-id="4a8b6-156">您所指定的帳戶必須在主控報表所使用之資料來源的電腦上擁有本機登入權限。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-156">The account you specify must have log on locally permissions on the computer that hosts the data source used by the report.</span></span>  
  
 <span data-ttu-id="4a8b6-157">如果認證是 Windows 驗證認證，請選取 **[連接到資料來源時作為 Windows 認證]** 。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-157">Select **Use as Windows credentials when connecting to the data source** if the credentials are Windows Authentication credentials.</span></span> <span data-ttu-id="4a8b6-158">如果您是使用資料庫驗證 (例如 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證)，請勿選取此核取方塊。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-158">Do not select this check box if you are using database authentication (for example, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication).</span></span>  
  
 <span data-ttu-id="4a8b6-159">如果您要使用資料庫驗證，請選取 **[連接到資料來源後，模擬已驗證的使用者]** 以便允許資料庫認證的委派，但是只有在資料庫伺服器支援模擬時才應該選取此選項。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-159">If you are using database authentication, select **Impersonate the authenticated user after a connection has been made to the data source** to allow delegation of database credentials, but only if a database server supports impersonation.</span></span> <span data-ttu-id="4a8b6-160">針對 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 資料庫，此選項會設定 SETUSER 函數。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-160">For [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] databases, this option sets the SETUSER function.</span></span>  
  
 <span data-ttu-id="4a8b6-161">**Windows 整合式安全性 (使用下列方式連接)**</span><span class="sxs-lookup"><span data-stu-id="4a8b6-161">**Windows integrated security (Connect using)**</span></span>  
 <span data-ttu-id="4a8b6-162">使用目前使用者的 Windows 認證來存取資料來源。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-162">Use the Windows credentials of the current user to access the data source.</span></span> <span data-ttu-id="4a8b6-163">當用來存取資料來源的認證與用來登入網路網域的認證相同時，請選擇此選項。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-163">Choose this option when the credentials that are used to access a data source are the same as those used to log on to the network domain.</span></span> <span data-ttu-id="4a8b6-164">在針對網域啟用 Kerberos 驗證時，或者資料來源與報表伺服器是在同一部電腦上時，此選項具有最佳的效能。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-164">This option works best when Kerberos authentication is enabled for your domain, or when the data source is on the same computer as the report server.</span></span> <span data-ttu-id="4a8b6-165">如果未啟用 Kerberos 驗證，Windows 認證可以傳遞至一部其他電腦。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-165">If Kerberos authentication is not enabled, Windows credentials can be passed to one other computer.</span></span> <span data-ttu-id="4a8b6-166">如果需要其他電腦連線，您會收到錯誤而不是預期的資料。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-166">If additional computer connections are required, you will get an error instead of the data you expect.</span></span>  
  
 <span data-ttu-id="4a8b6-167">報表伺服器管理員可以停用使用 Windows 整合式安全性來存取報表資料來源的功能。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-167">A report server administrator can disable the use of Windows integrated security for accessing report data sources.</span></span> <span data-ttu-id="4a8b6-168">如果此值呈現灰色，表示這項功能無法使用。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-168">If this value is grayed out, the feature is not available.</span></span>  
  
 <span data-ttu-id="4a8b6-169">如果您打算要排程或訂閱這個報表，請勿使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-169">Do not use this option if you plan to schedule or subscribe to this report.</span></span> <span data-ttu-id="4a8b6-170">已排程或自動報表處理需要使用無需使用者輸入或目前使用者安全性內容即可取得的認證。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-170">Scheduled or unattended report processing requires credentials that can be obtained without user input or the security context of a current user.</span></span> <span data-ttu-id="4a8b6-171">只有預存認證會提供這項功能。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-171">Only stored credentials provide this capability.</span></span> <span data-ttu-id="4a8b6-172">因此，如果報表是針對 Windows 整合式安全性認證類型所設定，報表伺服器就會讓您無法排程報表或訂閱處理。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-172">For this reason, the report server prevents you from scheduling report or subscription processing if the report is configured for the Windows integrated security credential type.</span></span> <span data-ttu-id="4a8b6-173">如果您針對已經訂閱或具有排程作業的報表選擇此選項，則訂閱和排程作業將會停止。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-173">If you choose this option for a report that is already subscribed to or that has scheduled operations, the subscriptions and scheduled operations will stop.</span></span>  
  
 <span data-ttu-id="4a8b6-174">**不需要認證 (使用下列方式連接)**</span><span class="sxs-lookup"><span data-stu-id="4a8b6-174">**Credentials are not required (Connect using)**</span></span>  
 <span data-ttu-id="4a8b6-175">指定不需要認證就可以存取資料來源。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-175">Specify that credentials are not required to access the data source.</span></span> <span data-ttu-id="4a8b6-176">請注意，如果資料來源需要使用者登入，則選擇此選項將沒有作用。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-176">Note that if a data source requires a user logon, choosing this option will have no effect.</span></span> <span data-ttu-id="4a8b6-177">只有當資料來源連接不需要使用者認證時，才應該選擇此選項。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-177">You should only choose this option if the data source connection does not require user credentials.</span></span>  
  
 <span data-ttu-id="4a8b6-178">若要使用這個選項，您先前必須已針對報表伺服器部署設定了自動執行帳戶。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-178">To use this option, you must have previously configured the unattended execution account for your report server deployment.</span></span> <span data-ttu-id="4a8b6-179">當認證的其他來源無法使用時，自動執行帳戶就會用來連接至外部資料來源。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-179">The unattended execution account is used to connect to external data sources when other sources of credentials are not available.</span></span> <span data-ttu-id="4a8b6-180">如果您指定了這個選項，但是沒有設定帳戶，報表資料來源的連接將會失敗，而且報表處理將不會進行。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-180">If you specify this option and the account is not configured, the connection to the report data source will fail and report processing will not occur.</span></span> <span data-ttu-id="4a8b6-181">如需此帳戶的詳細資訊，請參閱[&#40;SSRS Configuration Manager&#41;設定自動執行帳戶](install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-181">For more information about this account, see [Configure the Unattended Execution Account &#40;SSRS Configuration Manager&#41;](install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md).</span></span>  
  
 <span data-ttu-id="4a8b6-182">**確定**</span><span class="sxs-lookup"><span data-stu-id="4a8b6-182">**OK**</span></span>  
 <span data-ttu-id="4a8b6-183">按一下即可儲存您的變更。</span><span class="sxs-lookup"><span data-stu-id="4a8b6-183">Click to save your changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a8b6-184">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a8b6-184">See Also</span></span>  
 <span data-ttu-id="4a8b6-185">[建立、刪除或修改共用資料來源 &#40;報表管理員&#41;](../../2014/reporting-services/create-delete-or-modify-a-shared-data-source-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="4a8b6-185">[Create, Delete, or Modify a Shared Data Source &#40;Report Manager&#41;](../../2014/reporting-services/create-delete-or-modify-a-shared-data-source-report-manager.md) </span></span>  
 <span data-ttu-id="4a8b6-186">[Reporting Services 中的資料連線、資料來源及連接字串](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="4a8b6-186">[Data Connections, Data Sources, and Connection Strings in Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md) </span></span>  
 <span data-ttu-id="4a8b6-187">[報表管理員 &#40;SSRS 原生模式&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="4a8b6-187">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="4a8b6-188">[[內容] 頁面 &#40;報表管理員&#41;](../../2014/reporting-services/contents-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="4a8b6-188">[Contents Page &#40;Report Manager&#41;](../../2014/reporting-services/contents-page-report-manager.md) </span></span>  
 <span data-ttu-id="4a8b6-189">[建立、修改和刪除 &#40;SSRS&#41;的共用資料來源](report-data/create-modify-and-delete-shared-data-sources-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4a8b6-189">[Create, Modify, and Delete Shared Data Sources &#40;SSRS&#41;](report-data/create-modify-and-delete-shared-data-sources-ssrs.md) </span></span>  
 <span data-ttu-id="4a8b6-190">[報表管理員 F1 說明](../../2014/reporting-services/report-manager-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="4a8b6-190">[Report Manager F1 Help](../../2014/reporting-services/report-manager-f1-help.md) </span></span>  
 [<span data-ttu-id="4a8b6-191">指定報表資料來源的認證及連線資訊</span><span class="sxs-lookup"><span data-stu-id="4a8b6-191">Specify Credential and Connection Information for Report Data Sources</span></span>](report-data/specify-credential-and-connection-information-for-report-data-sources.md)  
  
  