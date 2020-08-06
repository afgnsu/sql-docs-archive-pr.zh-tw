---
title: '[新增資料庫] 對話方塊 (Analysis Services) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.newdatabase.f1
ms.assetid: ddc7804b-acb0-4ae4-a88f-e8cdf704c341
author: minewiskan
ms.author: owend
ms.openlocfilehash: 07eeee6136965671b000923dc3f240de06ce0bd0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596341"
---
# <a name="new-database-dialog-box-analysis-services"></a><span data-ttu-id="74a98-102">新增資料庫對話方塊 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="74a98-102">New Database Dialog Box (Analysis Services)</span></span>
  <span data-ttu-id="74a98-103">使用 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中的 [新增資料庫]\*\*\*\* 對話方塊，即可建立空的新 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="74a98-103">Use the **New Database** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to create a new, empty [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="74a98-104">在物件總管\*\*\*\* 中，以滑鼠右鍵按一下 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體的 [資料庫]\*\*\*\* 資料夾，然後選取 [新增資料庫]\*\*\*\*，即可顯示[新增資料庫]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="74a98-104">You can display the **New Database** dialog box by right-clicking the **Databases** folder of an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance in **Object Explorer** and selecting **New Database**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="74a98-105">選項</span><span class="sxs-lookup"><span data-stu-id="74a98-105">Options</span></span>  
  
|<span data-ttu-id="74a98-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="74a98-106">Term</span></span>|<span data-ttu-id="74a98-107">定義</span><span class="sxs-lookup"><span data-stu-id="74a98-107">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="74a98-108">**資料庫名稱**</span><span class="sxs-lookup"><span data-stu-id="74a98-108">**Database name**</span></span>|<span data-ttu-id="74a98-109">輸入新 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="74a98-109">Type the name of the new [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>|  
|<span data-ttu-id="74a98-110">**使用特定的使用者名稱和密碼**</span><span class="sxs-lookup"><span data-stu-id="74a98-110">**Use a specific user name and password**</span></span>|<span data-ttu-id="74a98-111">選取即可讓 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫使用所指定使用者帳戶的安全性認證。</span><span class="sxs-lookup"><span data-stu-id="74a98-111">Select to have the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database use the security credentials of a specified user account.</span></span> <span data-ttu-id="74a98-112">指定的認證將用於處理、ROLAP 查詢、非正規繫結、本機 Cube、採礦模型、遠端資料分割、連結物件以及從目標到來源的同步處理。</span><span class="sxs-lookup"><span data-stu-id="74a98-112">The specified credentials will be used for processing, ROLAP queries, out-of-line bindings, local cubes, mining models, remote partitions, linked objects, and synchronization from target to source.</span></span> <span data-ttu-id="74a98-113">但是，DMX OPENQUERY 陳述式將使用目前使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="74a98-113">For DMX OPENQUERY statements however, the credentials of the current user will be used.</span></span>|  
|<span data-ttu-id="74a98-114">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="74a98-114">**User name**</span></span>|<span data-ttu-id="74a98-115">輸入選取的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫所要使用之使用者帳戶的網域和名稱。</span><span class="sxs-lookup"><span data-stu-id="74a98-115">Type the domain and name of the user account to be used by the selected [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="74a98-116">請使用下列格式：</span><span class="sxs-lookup"><span data-stu-id="74a98-116">Use the following format:</span></span><br /><br /> <span data-ttu-id="74a98-117">*\<Domain name>* **\\** *\<User account name>*</span><span class="sxs-lookup"><span data-stu-id="74a98-117">*\<Domain name>* **\\** *\<User account name>*</span></span><br /><br /> <span data-ttu-id="74a98-118">注意：唯有在選取了 [使用特定的使用者名稱和密碼]\*\*\*\* 之後，才會啟用此選項。</span><span class="sxs-lookup"><span data-stu-id="74a98-118">Note: This option is enabled only if **Use a specific user name and password** is selected.</span></span>|  
|<span data-ttu-id="74a98-119">**密碼**</span><span class="sxs-lookup"><span data-stu-id="74a98-119">**Password**</span></span>|<span data-ttu-id="74a98-120">輸入 [使用者名稱]\*\*\*\* 中所指定之使用者帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="74a98-120">Type the password for the user account specified in **User name**.</span></span>|  
|<span data-ttu-id="74a98-121">**使用服務帳戶**</span><span class="sxs-lookup"><span data-stu-id="74a98-121">**Use the service account**</span></span>|<span data-ttu-id="74a98-122">選取即可讓 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫使用管理資料庫之 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 服務相關聯的安全性認證。</span><span class="sxs-lookup"><span data-stu-id="74a98-122">Select to have the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database use the security credentials that are associated with the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] service that manages the database.</span></span> <span data-ttu-id="74a98-123">服務帳戶認證將用於處理、ROLAP 查詢、遠端資料分割、連結物件以及從目標到來源的同步處理。</span><span class="sxs-lookup"><span data-stu-id="74a98-123">The service account credentials will be used for processing, ROLAP queries, remote partitions, linked objects, and synchronization from target to source.</span></span> <span data-ttu-id="74a98-124">但是，DMX OPENQUERY 陳述式、本機 Cube 和採礦模型將使用目前使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="74a98-124">For DMX OPENQUERY statements, local cubes, and mining models the credentials of the current user will be used.</span></span> <span data-ttu-id="74a98-125">非正規 (out-of-line) 繫結不支援此選項。</span><span class="sxs-lookup"><span data-stu-id="74a98-125">This option is not supported for out-of-line bindings.</span></span>|  
|<span data-ttu-id="74a98-126">**使用目前使用者的認證**</span><span class="sxs-lookup"><span data-stu-id="74a98-126">**Use the credentials of the current user**</span></span>|<span data-ttu-id="74a98-127">選取此選項即可讓 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫使用目前使用者的安全性認證來進行非正規 (out-of-line) 繫結、DMX OPENQUERY 陳述式、本機 Cube 和採礦模型。</span><span class="sxs-lookup"><span data-stu-id="74a98-127">Select to have the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database use the security credentials of the current user for out-of-line bindings, DMX OPENQUERY statements, local cubes, and mining models.</span></span> <span data-ttu-id="74a98-128">處理、ROLAP 查詢、遠端資料分割、連結物件以及從目標到來源的同步處理不支援此選項。</span><span class="sxs-lookup"><span data-stu-id="74a98-128">This option is not supported for processing, ROLAP queries, remote partitions, linked objects, and synchronization from target to source.</span></span>|  
|<span data-ttu-id="74a98-129">**預設值**</span><span class="sxs-lookup"><span data-stu-id="74a98-129">**Default**</span></span>|<span data-ttu-id="74a98-130">選取此選項即可使用 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]之預設使用者帳戶的認證。</span><span class="sxs-lookup"><span data-stu-id="74a98-130">Select to use the credentials of the default user account for [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="74a98-131">此選項會使用資料庫的預設值來處理物件、同步處理伺服器和執行 **Open Query** 資料採礦陳述式。</span><span class="sxs-lookup"><span data-stu-id="74a98-131">This option uses the default setting for the database for processing objects, synchronizing servers, and executing **Open Query** data mining statements.</span></span> <span data-ttu-id="74a98-132">如需指定在資料庫層級之預設設定的詳細資訊，請參閱[設定多維度資料庫屬性 &#40;Analysis Services&#41;](multidimensional-models/set-multidimensional-database-properties-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="74a98-132">For more information about specifying the default settings at the database level, see [Set Multidimensional Database Properties &#40;Analysis Services&#41;](multidimensional-models/set-multidimensional-database-properties-analysis-services.md).</span></span><br /><br /> <span data-ttu-id="74a98-133">根據預設，[ `DataSourceImpersonationInfo` 資料庫] 屬性會設定為 **[使用服務帳戶**]。</span><span class="sxs-lookup"><span data-stu-id="74a98-133">By default the `DataSourceImpersonationInfo` database property is set to **Use the service account**.</span></span> <span data-ttu-id="74a98-134">不論 `DataSourceImpersonationInfo` 屬性值為何，目前使用者的認證都將用於非正規 (out-of-line) 繫結、ROLAP 查詢、本機 Cube 和資料採礦模型。</span><span class="sxs-lookup"><span data-stu-id="74a98-134">Regardless of the `DataSourceImpersonationInfo` property value, the credentials of the current user will be used for out-of-line bindings, ROLAP queries, local cubes, and data mining models.</span></span>|  
|<span data-ttu-id="74a98-135">**說明**</span><span class="sxs-lookup"><span data-stu-id="74a98-135">**Description**</span></span>|<span data-ttu-id="74a98-136">輸入新 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫的描述。</span><span class="sxs-lookup"><span data-stu-id="74a98-136">Type the description for the new [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="74a98-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74a98-137">See Also</span></span>  
 <span data-ttu-id="74a98-138">[Analysis Services 的設計工具和對話方塊 &#40;多維度資料&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="74a98-138">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="74a98-139">多維度模型資料庫 &#40;SSAS&#41;</span><span class="sxs-lookup"><span data-stu-id="74a98-139">Multidimensional Model Databases &#40;SSAS&#41;</span></span>](multidimensional-models/multidimensional-model-databases-ssas.md)  
  
  