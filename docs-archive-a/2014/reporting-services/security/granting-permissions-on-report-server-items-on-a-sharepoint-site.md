---
title: 授與 SharePoint 網站上報表伺服器項目的權限 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- permissions [Reporting Services], SharePoint integrated mode
- SharePoint integration [Reporting Services], permissions
- permissions [Reporting Services], native mode
- security [Reporting Services], SharePoint integrated mode
ms.assetid: 0eb2f34a-3643-4b03-81c2-5741ba7ebefd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d6f273d48051b03f87d354cd5d37c18548542e45
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606067"
---
# <a name="granting-permissions-on-report-server-items-on-a-sharepoint-site"></a><span data-ttu-id="4eca6-102">授與 SharePoint 網站上報表伺服器項目的權限</span><span class="sxs-lookup"><span data-stu-id="4eca6-102">Granting Permissions on Report Server Items on a SharePoint Site</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="4eca6-103">[!INCLUDE[SPF2010](../../includes/spf2010-md.md)] 提供內建的安全性功能，可用來授與從 SharePoint 網站和文件庫存取報表伺服器項目的權限。</span><span class="sxs-lookup"><span data-stu-id="4eca6-103">[!INCLUDE[SPF2010](../../includes/spf2010-md.md)] provides built-in security features that you can use to grant access to report server items that you access from SharePoint sites and libraries.</span></span> <span data-ttu-id="4eca6-104">如果您已經指定權限給使用者，則在設定 [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] 與報表伺服器之間的整合設定之後，那些使用者就能立即存取報表伺服器項目和作業。</span><span class="sxs-lookup"><span data-stu-id="4eca6-104">If you already assigned permissions to users, those same users will have access to report server items and operations immediately after you configure the integration settings between [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] and a report server.</span></span> <span data-ttu-id="4eca6-105">您可以使用現有權限來上傳報表定義和其他文件、檢視報表、建立訂閱和管理項目。</span><span class="sxs-lookup"><span data-stu-id="4eca6-105">You can use existing permissions to upload report definitions and other documents, view reports, create subscriptions, and manage items.</span></span>  
  
 <span data-ttu-id="4eca6-106">如果您未指定權限，或是不熟悉 [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]中的安全性功能，請依照下列方針進行：</span><span class="sxs-lookup"><span data-stu-id="4eca6-106">If you have not assigned permissions or if you are not familiar with the security features in [!INCLUDE[SPF2010](../../includes/spf2010-md.md)], follow these guidelines:</span></span>  
  
1.  <span data-ttu-id="4eca6-107">在 [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]的產品文件中，閱讀有關標準 SharePoint 群組的預設安全性設定，以了解如何管理權限和使用者存取。</span><span class="sxs-lookup"><span data-stu-id="4eca6-107">In the product documentation for [!INCLUDE[SPF2010](../../includes/spf2010-md.md)], read about the default security settings for the standard SharePoint groups so that you know how to manage permissions and user access.</span></span>  
  
2.  <span data-ttu-id="4eca6-108">檢閱會明確影響報表伺服器項目和作業存取權的權限清單。</span><span class="sxs-lookup"><span data-stu-id="4eca6-108">Review the list of permissions that specifically affect access to report server items and operations.</span></span> <span data-ttu-id="4eca6-109">如需詳細資訊，請參閱 [在 Windows SharePoint Services 中使用報表伺服器項目的內建安全性](use-built-in-security-in-windows-sharepoint-services-for-report-server-items.md)。</span><span class="sxs-lookup"><span data-stu-id="4eca6-109">For more information, see [Use Built-in Security in Windows SharePoint Services for Report Server Items](use-built-in-security-in-windows-sharepoint-services-for-report-server-items.md).</span></span>  
  
3.  <span data-ttu-id="4eca6-110">指定使用者和群組帳戶給預先定義的 SharePoint 群組。</span><span class="sxs-lookup"><span data-stu-id="4eca6-110">Assign user and group accounts to predefined SharePoint groups.</span></span>  
  
4.  <span data-ttu-id="4eca6-111">或者，建立新的權限等級和群組，或修改現有的權限等級和群組，以便隨特定需要改變伺服器存取權限。</span><span class="sxs-lookup"><span data-stu-id="4eca6-111">Optionally, create new permission levels and groups, or modify existing ones to vary server access permissions as specific needs arise.</span></span>  
  
 <span data-ttu-id="4eca6-112">若要搭配報表伺服器項目使用 [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] 安全性功能，您必須擁有以 SharePoint 整合模式執行的報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="4eca6-112">To use [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] security features with report server items, you must have a report server that runs in SharePoint integrated mode.</span></span>  
  
## <a name="about-permissions-permission-levels-and-sharepoint-groups"></a><span data-ttu-id="4eca6-113">關於權限、權限等級和 SharePoint 群組</span><span class="sxs-lookup"><span data-stu-id="4eca6-113">About Permissions, Permission Levels and SharePoint Groups</span></span>  
 <span data-ttu-id="4eca6-114">下列清單提供 [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]中安全性功能的簡介。</span><span class="sxs-lookup"><span data-stu-id="4eca6-114">The following list provides a brief introduction to the security features in [!INCLUDE[SPF2010](../../includes/spf2010-md.md)].</span></span> <span data-ttu-id="4eca6-115">如需詳細資訊，請參閱 SharePoint 網站上的「Windows SharePoint 說明與使用方法」。</span><span class="sxs-lookup"><span data-stu-id="4eca6-115">For more information, see "Windows SharePoint Help and How-to" on your SharePoint site.</span></span>  
  
-   <span data-ttu-id="4eca6-116">安全物件包括網站、清單、文件庫、資料夾和文件。</span><span class="sxs-lookup"><span data-stu-id="4eca6-116">Securable objects include sites, lists, libraries, folders, and documents.</span></span>  
  
-   <span data-ttu-id="4eca6-117">權限是可執行特定工作的授權。</span><span class="sxs-lookup"><span data-stu-id="4eca6-117">A permission is an authorization to perform a specific task.</span></span> [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] <span data-ttu-id="4eca6-118">提供 33 種預先定義的權限，可合併成為權限等級。</span><span class="sxs-lookup"><span data-stu-id="4eca6-118">provides 33 predefined permissions that you can combine into a permission level.</span></span>  
  
-   <span data-ttu-id="4eca6-119">權限等級是可授與使用者或 SharePoint 群組的安全性實體物件 (例如網站、文件庫、清單、資料夾、項目或文件) 權限集合。</span><span class="sxs-lookup"><span data-stu-id="4eca6-119">A permission level is a set of permissions that can be granted to users or SharePoint groups on a securable object such as a site, library, list, folder, item, or document.</span></span> <span data-ttu-id="4eca6-120">它相當於 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]中的角色定義。</span><span class="sxs-lookup"><span data-stu-id="4eca6-120">It is equivalent to a role definition in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="4eca6-121">預先定義的權限等級有 5 個。</span><span class="sxs-lookup"><span data-stu-id="4eca6-121">There are five predefined permission levels.</span></span> <span data-ttu-id="4eca6-122">您可以進行自訂或視需要建立新的。</span><span class="sxs-lookup"><span data-stu-id="4eca6-122">You can customize them or create new ones if needed.</span></span>  
  
-   <span data-ttu-id="4eca6-123">SharePoint 群組是您可以在 SharePoint 網站上建立的使用者群組，以管理站台的權限或提供站台成員的電子郵件通訊群組清單。</span><span class="sxs-lookup"><span data-stu-id="4eca6-123">A SharePoint group is a group of users that you can create on a SharePoint site to manage permissions to the site and to provide an e-mail distribution list for site members.</span></span> <span data-ttu-id="4eca6-124">SharePoint 群組包含 Windows 使用者和群組帳戶，或使用者登入 (如果您是使用表單驗證)。</span><span class="sxs-lookup"><span data-stu-id="4eca6-124">A SharePoint group consists of Windows user and group accounts, or user logins if you are using Forms authentication.</span></span> [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] <span data-ttu-id="4eca6-125">提供三個群組。</span><span class="sxs-lookup"><span data-stu-id="4eca6-125">provides three groups.</span></span> <span data-ttu-id="4eca6-126">您可以進行自訂或視需要建立新的。</span><span class="sxs-lookup"><span data-stu-id="4eca6-126">You can customize them or create new ones if needed.</span></span>  
  
-   <span data-ttu-id="4eca6-127">權限繼承讓子網站、清單、文件庫和項目能夠繼承上層網站的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="4eca6-127">Permission inheritance allows subsites, lists and libraries, and items to inherit the security settings of the parent site.</span></span> <span data-ttu-id="4eca6-128">您可以使用繼承的權限來存取儲存在 SharePoint 文件庫中的報表伺服器項目。</span><span class="sxs-lookup"><span data-stu-id="4eca6-128">You can use inherited permissions to access report server items that are stored in a SharePoint library.</span></span> <span data-ttu-id="4eca6-129">使用權限繼承和預先定義的 SharePoint 群組有助於簡化您的部署，並可立即存取大部分報表伺服器作業。</span><span class="sxs-lookup"><span data-stu-id="4eca6-129">Using permission inheritance and the predefined SharePoint groups can help simplify your deployment and provides immediate access to most report server operations.</span></span>  
  
## <a name="who-sets-permissions"></a><span data-ttu-id="4eca6-130">誰設定權限</span><span class="sxs-lookup"><span data-stu-id="4eca6-130">Who Sets Permissions</span></span>  
 <span data-ttu-id="4eca6-131">安裝 [!INCLUDE[SPF2010](../../includes/spf2010-md.md)]、執行 SharePoint 組態精靈並建立入口網站的管理員會成為預設的入口網站擁有者。</span><span class="sxs-lookup"><span data-stu-id="4eca6-131">The administrator who installs [!INCLUDE[SPF2010](../../includes/spf2010-md.md)], runs the SharePoint Configuration Wizard, and creates the portal site becomes the default portal site owner.</span></span> <span data-ttu-id="4eca6-132">網站擁有者可以在管理中心中設定伺服陣列或獨立 SharePoint Web 應用程式的權限，也可以設定每個 SharePoint Web 應用程式於頂層網站的權限。</span><span class="sxs-lookup"><span data-stu-id="4eca6-132">The site owner can set permissions in Central Administration for a farm or a stand-alone SharePoint Web application, and can set permission at the top-level site for each SharePoint Web application.</span></span> <span data-ttu-id="4eca6-133">這個人也可以指定其他網站擁有者。</span><span class="sxs-lookup"><span data-stu-id="4eca6-133">This person can also designate additional site owners.</span></span>  
  
 <span data-ttu-id="4eca6-134">在 SharePoint Web 應用程式的頂層網站，網站集合管理員可設定整個網站階層中多個網站的權限。</span><span class="sxs-lookup"><span data-stu-id="4eca6-134">At the top-level site of a SharePoint Web application, site collection administrators can set permissions for multiple sites throughout the site hierarchy.</span></span> <span data-ttu-id="4eca6-135">個別網站擁有者可以執行與子網站相關的相同工作。</span><span class="sxs-lookup"><span data-stu-id="4eca6-135">Individual site owners can perform the same tasks relative to a subsite.</span></span>  
  
 <span data-ttu-id="4eca6-136">伺服器管理員和網站集合管理員可以設定選項，以決定其他網站擁有者能否設定權限。</span><span class="sxs-lookup"><span data-stu-id="4eca6-136">A server administrator or a site collection administrator can set options that determine whether other site owners can set permissions.</span></span> <span data-ttu-id="4eca6-137">依您擁有的不同權限等級，您或許無法建立或自訂 SharePoint 群組或權限等級。</span><span class="sxs-lookup"><span data-stu-id="4eca6-137">Depending on the level of permissions you have, you might not be able to create or customize SharePoint groups or permission levels.</span></span>  
  
## <a name="using-predefined-sharepoint-groups-and-permission-levels"></a><span data-ttu-id="4eca6-138">使用預先定義的 SharePoint 群組和權限等級</span><span class="sxs-lookup"><span data-stu-id="4eca6-138">Using Predefined SharePoint Groups and Permission Levels</span></span>  
 <span data-ttu-id="4eca6-139">[!INCLUDE[SPF2010](../../includes/spf2010-md.md)] 產品文件中的建議事項建議您使用標準 SharePoint 群組 (這些是 *Site name* **擁有者**、*Site name*  **成員**和 *Site name* **訪客**)，並於網站層級指派權限。</span><span class="sxs-lookup"><span data-stu-id="4eca6-139">Recommendations in [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] product documentation suggest that you use standard SharePoint groups (which are *Site name* **Owners**, *Site name* **Members**, and *Site name* **Visitors**) and assign permissions at the site level.</span></span> <span data-ttu-id="4eca6-140">獲您指派權限的大部分使用者應該是 *Site name* **訪客**或 *Site name* **成員**群組的成員。</span><span class="sxs-lookup"><span data-stu-id="4eca6-140">Most users that you assign permissions to should be members of the *Site name* **Visitors** or *Site name* **Members** groups.</span></span> <span data-ttu-id="4eca6-141">上層網站的權限會由整個網站階層繼承。</span><span class="sxs-lookup"><span data-stu-id="4eca6-141">Permissions on the parent site are inherited throughout the site hierarchy.</span></span> <span data-ttu-id="4eca6-142">您可以針對需要其他限制的特定項目，中斷其權限繼承。</span><span class="sxs-lookup"><span data-stu-id="4eca6-142">You can break permission inheritance for specific items that require additional restrictions.</span></span>  
  
 <span data-ttu-id="4eca6-143">下列 SharePoint 群組具有下列預先定義的權限等級：</span><span class="sxs-lookup"><span data-stu-id="4eca6-143">The following SharePoint groups have the following predefined permission levels:</span></span>  
  
-   <span data-ttu-id="4eca6-144">「 **擁有者** 」群組具有「完整控制權」權限，讓群組成員能夠變更網站內容、網頁或功能。</span><span class="sxs-lookup"><span data-stu-id="4eca6-144">The **Owners** group has Full Control permissions, which enable group members to change the site content, pages, or functionality.</span></span> <span data-ttu-id="4eca6-145">完整控制存取權應該僅限於網站管理員。</span><span class="sxs-lookup"><span data-stu-id="4eca6-145">Full Control access should be limited to site administrators only.</span></span>  
  
-   <span data-ttu-id="4eca6-146">「 **成員** 」群組具有「參與」等級權限，讓群組成員能夠檢視網頁、編輯項目、提交變更核准、加入清單項目和刪除清單項目。</span><span class="sxs-lookup"><span data-stu-id="4eca6-146">The **Members** group has Contribute level permissions, which allow group members to view pages, edit items, submit changes for approval, add, and delete items from a list.</span></span>  
  
-   <span data-ttu-id="4eca6-147"> [訪客] 群組具有「讀取」層級權限，讓群組成員能夠檢視網頁、清單項目和文件。</span><span class="sxs-lookup"><span data-stu-id="4eca6-147">The **Visitors** group has Read level permissions, which enables group members to view pages, list items, and documents.</span></span>  
  
 <span data-ttu-id="4eca6-148">SharePoint 群組具有可立即存取許多報表伺服器作業的權限等級。</span><span class="sxs-lookup"><span data-stu-id="4eca6-148">The SharePoint groups have permission levels that provide immediate access to many report server operations.</span></span> <span data-ttu-id="4eca6-149">如果您覺得內建的安全性設定無法提供您需要的存取層級，您可以建立自訂群組或權限等級。</span><span class="sxs-lookup"><span data-stu-id="4eca6-149">If you find that the built-in security settings do not provide the level of access that you need, you can create custom groups or permission levels.</span></span>  
  
 <span data-ttu-id="4eca6-150">如需透過預設安全性功能可支援哪些報表伺服器作業的詳細資訊，請參閱 [在 Windows SharePoint Services 中使用報表伺服器項目的內建安全性](use-built-in-security-in-windows-sharepoint-services-for-report-server-items.md)。</span><span class="sxs-lookup"><span data-stu-id="4eca6-150">For more information about which report server operations are supported through the default security features, see [Use Built-in Security in Windows SharePoint Services for Report Server Items](use-built-in-security-in-windows-sharepoint-services-for-report-server-items.md).</span></span>  
  
 <span data-ttu-id="4eca6-151">若要使用內建的安全性功能，您必須將 Windows 使用者或群組帳戶指定給 SharePoint 群組。</span><span class="sxs-lookup"><span data-stu-id="4eca6-151">To use the built-in security features, you must assign Windows user or group accounts to the SharePoint groups.</span></span> <span data-ttu-id="4eca6-152">但伺服器管理員和入口網站擁有者除外，因為在安裝軟體時，他們就自動具有 [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] 的存取權，至於所有其他使用者都必須經過授與權限後，才能存取伺服器。</span><span class="sxs-lookup"><span data-stu-id="4eca6-152">Except for the server administrator and portal site owner who have automatic access to [!INCLUDE[SPF2010](../../includes/spf2010-md.md)] when the software is installed, all other users must be granted permissions to access the server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4eca6-153">本節內容</span><span class="sxs-lookup"><span data-stu-id="4eca6-153">In This Section</span></span>  
 [<span data-ttu-id="4eca6-154">在 Windows SharePoint Services 中使用報表伺服器項目的內建安全性</span><span class="sxs-lookup"><span data-stu-id="4eca6-154">Use Built-in Security in Windows SharePoint Services for Report Server Items</span></span>](use-built-in-security-in-windows-sharepoint-services-for-report-server-items.md)  
 <span data-ttu-id="4eca6-155">說明如何使用預先定義的 SharePoint 群組和權限等級來存取報表伺服器項目。</span><span class="sxs-lookup"><span data-stu-id="4eca6-155">Explains how the predefined SharePoint groups and permission levels can be used to access report server items.</span></span>  
  
 [<span data-ttu-id="4eca6-156">報表伺服器項目的 SharePoint 網站和清單權限參考</span><span class="sxs-lookup"><span data-stu-id="4eca6-156">SharePoint Site and List Permission Reference for Report Server Items</span></span>](sharepoint-site-and-list-permission-reference-for-report-server-items.md)  
 <span data-ttu-id="4eca6-157">提供可用來存取報表伺服器作業之所有 SharePoint 產品權限的參考。</span><span class="sxs-lookup"><span data-stu-id="4eca6-157">Provides a reference of all SharePoint product permissions that can be used to access report server operations.</span></span>  
  
 [<span data-ttu-id="4eca6-158">設定 SharePoint Web 應用程式中報表伺服器作業的權限</span><span class="sxs-lookup"><span data-stu-id="4eca6-158">Set Permissions for Report Server Operations in a SharePoint Web Application</span></span>](set-permissions-for-report-server-operations-in-a-sharepoint-web-application.md)  
 <span data-ttu-id="4eca6-159">描述隨選報表的權限需求，並建議啟用功能的方法。</span><span class="sxs-lookup"><span data-stu-id="4eca6-159">Describes permission requirements for ad hoc reporting and suggests approaches for making features available.</span></span>  
  
 [<span data-ttu-id="4eca6-160">將 Reporting Services 中的角色和工作與 SharePoint 群組和權限做比較</span><span class="sxs-lookup"><span data-stu-id="4eca6-160">Compare Roles and Tasks in Reporting Services to SharePoint Groups and Permissions</span></span>](../reporting-services-roles-tasks-vs-sharepoint-groups-permissions.md)  
 <span data-ttu-id="4eca6-161">提供簡短摘要，將 SharePoint 群組與 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]中預先定義的角色定義做比較。</span><span class="sxs-lookup"><span data-stu-id="4eca6-161">Provides a brief summary of how the SharePoint groups compare with predefined role definitions in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="4eca6-162">設定 SharePoint 網站上報表伺服器項目的權限 &#40;SharePoint 整合模式的 Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="4eca6-162">Set Permissions for Report Server Items on a SharePoint Site &#40;Reporting Services in SharePoint Integrated Mode&#41;</span></span>](set-permissions-for-report-server-items-on-a-sharepoint-site.md)  
 <span data-ttu-id="4eca6-163">提供指示，以建立有權可啟動報表產生器和設定模型項目安全性的新 SharePoint 群組。</span><span class="sxs-lookup"><span data-stu-id="4eca6-163">Provides instructions for creating new SharePoint groups that have permission to start Report Builder and set model item security.</span></span> <span data-ttu-id="4eca6-164">本主題也包含有關為任何報表伺服器項目或作業設定自訂權限的一般指導方針。</span><span class="sxs-lookup"><span data-stu-id="4eca6-164">This topic also contains general guidelines about setting custom permissions for any report server item or operation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4eca6-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4eca6-165">See Also</span></span>  
 <span data-ttu-id="4eca6-166">[在 sharepoint 網站上設定報表伺服器專案的許可權 &#40;SharePoint 整合模式中的 Reporting Services&#41;](set-permissions-for-report-server-items-on-a-sharepoint-site.md) </span><span class="sxs-lookup"><span data-stu-id="4eca6-166">[Set Permissions for Report Server Items on a SharePoint Site &#40;Reporting Services in SharePoint Integrated Mode&#41;](set-permissions-for-report-server-items-on-a-sharepoint-site.md) </span></span>  
 [<span data-ttu-id="4eca6-167">Reporting Services 安全性與保護</span><span class="sxs-lookup"><span data-stu-id="4eca6-167">Reporting Services Security and Protection</span></span>](reporting-services-security-and-protection.md)  
  
  