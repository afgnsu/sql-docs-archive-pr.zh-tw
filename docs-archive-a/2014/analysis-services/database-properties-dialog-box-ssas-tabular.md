---
title: '[資料庫屬性] 對話方塊 (SSAS-表格式) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.ssmsimbi.DatabaseProperties.f1
ms.assetid: 0f0ec02f-7b55-40ea-8a04-ed0deb1efd7a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 41bf7838a714c35e2149e8163e21a7b8044a77c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607153"
---
# <a name="database-properties-dialog-box-ssas---tabular"></a><span data-ttu-id="660f3-102">資料庫屬性對話方塊 (SSAS - 表格式)</span><span class="sxs-lookup"><span data-stu-id="660f3-102">Database Properties Dialog Box (SSAS - Tabular)</span></span>
  <span data-ttu-id="660f3-103">此對話方塊提供時間戳記和其他描述性資訊，再加上決定資料庫是否使用快取資料的可自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="660f3-103">This dialog box provides timestamps and other descriptive information, plus customizable properties that determine whether the database uses cached data.</span></span> <span data-ttu-id="660f3-104">其他可自訂屬性包含變更資料庫名稱和指定模擬選項。</span><span class="sxs-lookup"><span data-stu-id="660f3-104">Other customizable properties include changing the database name and specifying the impersonation options.</span></span>  
  
## <a name="options"></a><span data-ttu-id="660f3-105">選項</span><span class="sxs-lookup"><span data-stu-id="660f3-105">Options</span></span>  
  
|<span data-ttu-id="660f3-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="660f3-106">Term</span></span>|<span data-ttu-id="660f3-107">定義</span><span class="sxs-lookup"><span data-stu-id="660f3-107">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="660f3-108">**名稱**</span><span class="sxs-lookup"><span data-stu-id="660f3-108">**Name**</span></span>|<span data-ttu-id="660f3-109">**[名稱]** 是唯一識別伺服器資料庫的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="660f3-109">**Name** is the database name that uniquely identifies the database on the server.</span></span> <span data-ttu-id="660f3-110">在變更資料庫名稱時，請考慮對現有連接字串中使用目前名稱的報表和用戶端應用程式造成的影響。</span><span class="sxs-lookup"><span data-stu-id="660f3-110">When changing the database name, consider the impact on reports and client applications that use the current name in existing connection strings.</span></span> <span data-ttu-id="660f3-111">您需要更新現有報告中的連接字串，以避免存取被拒錯誤。</span><span class="sxs-lookup"><span data-stu-id="660f3-111">You will need to update connection strings in existing reports to avoid access denied errors.</span></span> <span data-ttu-id="660f3-112">此外，此資料庫的來源表格式模型最可能使用原始名稱。</span><span class="sxs-lookup"><span data-stu-id="660f3-112">In addition, the tabular model that is the source of this database most likely uses the original name.</span></span> <span data-ttu-id="660f3-113">請考慮更新模型中的資料庫部署屬性，以確保該模型未來的更新會發行至預期的資料庫。</span><span class="sxs-lookup"><span data-stu-id="660f3-113">Consider updating the database deployment properties in the model to ensure that future updates to that model are published to the intended database.</span></span>|  
|<span data-ttu-id="660f3-114">**識別碼**</span><span class="sxs-lookup"><span data-stu-id="660f3-114">**ID**</span></span>|<span data-ttu-id="660f3-115">顯示資料庫的識別碼。</span><span class="sxs-lookup"><span data-stu-id="660f3-115">Displays the identifier of the database.</span></span>|  
|<span data-ttu-id="660f3-116">**說明**</span><span class="sxs-lookup"><span data-stu-id="660f3-116">**Description**</span></span>|<span data-ttu-id="660f3-117">鍵入以變更資料庫的描述。</span><span class="sxs-lookup"><span data-stu-id="660f3-117">Type to change the description of the database.</span></span>|  
|<span data-ttu-id="660f3-118">**建立時間戳記**</span><span class="sxs-lookup"><span data-stu-id="660f3-118">**Create Timestamp**</span></span>|<span data-ttu-id="660f3-119">顯示建立資料庫的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="660f3-119">Displays the date and time the database was created.</span></span>|  
|<span data-ttu-id="660f3-120">**上次結構描述更新**</span><span class="sxs-lookup"><span data-stu-id="660f3-120">**Last Schema Update**</span></span>|<span data-ttu-id="660f3-121">顯示上次更新資料庫的中繼資料的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="660f3-121">Displays the date and time the metadata for the database was last updated.</span></span>|  
|<span data-ttu-id="660f3-122">**上次更新**</span><span class="sxs-lookup"><span data-stu-id="660f3-122">**Last Update**</span></span>|<span data-ttu-id="660f3-123">顯示上次更新資料庫之資料的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="660f3-123">Displays the date and time the data for the database was last updated.</span></span>|  
|<span data-ttu-id="660f3-124">**讀寫模式**</span><span class="sxs-lookup"><span data-stu-id="660f3-124">**Read-Write Mode**</span></span>|<span data-ttu-id="660f3-125">這是唯讀屬性，但是您可以利用一連串的 [中斷連結]\*\*\*\* 與 [連結]\*\*\*\* 命令加以變更，因為此屬性是 [連結]\*\*\*\* 命令的參數。</span><span class="sxs-lookup"><span data-stu-id="660f3-125">This is a read-only property, but you can change it using a sequence of **Detach** and **Attach** commands, where the property is a parameter of the **Attach** command.</span></span> <span data-ttu-id="660f3-126">如需詳細資訊，請參閱 [資料庫 ReadWriteModes](multidimensional-models/database-readwritemodes.md)。</span><span class="sxs-lookup"><span data-stu-id="660f3-126">For more information, see [Database ReadWriteModes](multidimensional-models/database-readwritemodes.md).</span></span>|  
|<span data-ttu-id="660f3-127">**DirectQueryMode**</span><span class="sxs-lookup"><span data-stu-id="660f3-127">**DirectQueryMode**</span></span>|<span data-ttu-id="660f3-128">指定資料庫只使用記憶體中儲存體 (沒有磁碟儲存體)、只使用磁碟儲存體，或使用兩者的某種組合。</span><span class="sxs-lookup"><span data-stu-id="660f3-128">Specifies whether the database uses only in-memory storage (no disk storage), only disk-based storage, or some combination of the two.</span></span> <span data-ttu-id="660f3-129">有效值是 InMemory、DirectQuery、InMemoryWithDirectQuery (大部分是以記憶體為主，少部分分頁至磁碟)，或 DirectQueryWithInMemory (大部分是以磁碟為主，少部分是記憶體中儲存體)。</span><span class="sxs-lookup"><span data-stu-id="660f3-129">Valid values are InMemory, DirectQuery, InMemoryWithDirectQuery (mostly memory-based with some paging to disk), or DirectQueryWithInMemory (mostly disk-based with some in-memory storage).</span></span> <span data-ttu-id="660f3-130">如需詳細資訊，請參閱[DirectQuery 部署案例 &#40;SSAS 表格式&#41;](directquery-deployment-scenarios-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="660f3-130">For more information, see [DirectQuery Deployment Scenarios &#40;SSAS Tabular&#41;](directquery-deployment-scenarios-ssas-tabular.md).</span></span>|  
|<span data-ttu-id="660f3-131">**資料來源模擬資訊**</span><span class="sxs-lookup"><span data-stu-id="660f3-131">**Data Source Impersonation Info**</span></span>|<span data-ttu-id="660f3-132">指定用於下列項目的模擬帳戶：在處理或重新整理本機或遠端資料分割的資料時的資料庫連接、針對關聯式資料存放區執行的查詢 (透過 DirectQuery)、非正規 (out-of-line) 繫結，以及從目標到來源的資料庫同步處理。</span><span class="sxs-lookup"><span data-stu-id="660f3-132">Specifies the impersonation account used for database connections when processing or refreshing data on local or remote partitions, queries that run against a relational data store (via DirectQuery), out-of-line bindings, and database synchronization from target to source.</span></span><br /><br /> <span data-ttu-id="660f3-133">有效值包含 Analysis Services 服務帳戶或一組特定的 Windows 認證。</span><span class="sxs-lookup"><span data-stu-id="660f3-133">Valid values include the Analysis Services service account or a specific set of Windows credentials.</span></span> <span data-ttu-id="660f3-134">請勿指定 **[使用目前使用者的認證]**。</span><span class="sxs-lookup"><span data-stu-id="660f3-134">Do not specify **Use the credentials of the current user**.</span></span> <span data-ttu-id="660f3-135">表格式模型資料庫不支援該認證選項。</span><span class="sxs-lookup"><span data-stu-id="660f3-135">That credential option is not supported for a tabular model database.</span></span>|  
|<span data-ttu-id="660f3-136">**上次處理**</span><span class="sxs-lookup"><span data-stu-id="660f3-136">**Last Processed**</span></span>|<span data-ttu-id="660f3-137">顯示上次處理資料庫的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="660f3-137">Displays the date and time the database was last processed.</span></span>|  
|<span data-ttu-id="660f3-138">**估計的大小**</span><span class="sxs-lookup"><span data-stu-id="660f3-138">**Estimated Size**</span></span>|<span data-ttu-id="660f3-139">顯示資料庫之估計的大小。</span><span class="sxs-lookup"><span data-stu-id="660f3-139">Displays the estimated size of the database.</span></span>|  
|<span data-ttu-id="660f3-140">**儲存位置**</span><span class="sxs-lookup"><span data-stu-id="660f3-140">**Storage Location**</span></span>|<span data-ttu-id="660f3-141">指定資料庫的位置。</span><span class="sxs-lookup"><span data-stu-id="660f3-141">Specifies the location of the database.</span></span> <span data-ttu-id="660f3-142">如果資料庫位於預設資料目錄中，此值為空白。</span><span class="sxs-lookup"><span data-stu-id="660f3-142">If the database is located in the default Data directory, this value will be empty.</span></span>|  
  
  