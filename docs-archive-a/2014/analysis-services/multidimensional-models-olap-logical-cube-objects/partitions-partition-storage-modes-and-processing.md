---
title: 分割區儲存模式和處理 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- storage [Analysis Services], partitions
- hybrid OLAP
- data storage [Analysis Services]
- relational OLAP
- multidimensional OLAP
- partitions [Analysis Services], storage
- storing data [Analysis Services], partitions
- HOLAP
- MOLAP
- ROLAP
ms.assetid: 86d17547-a0b6-47ac-876c-d7a5b15ac327
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9b97bee2099ea82508ba9e66414bb9527a3c3a8c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607120"
---
# <a name="partition-storage-modes-and-processing"></a><span data-ttu-id="23d74-102">資料分割儲存模式及處理</span><span class="sxs-lookup"><span data-stu-id="23d74-102">Partition Storage Modes and Processing</span></span>
  <span data-ttu-id="23d74-103">資料分割的儲存模式會影響查詢及處理效能、儲存需求，以及此資料分割的儲存位置及其父量值群組和 Cube。</span><span class="sxs-lookup"><span data-stu-id="23d74-103">The storage mode of a partition affects the query and processing performance, storage requirements, and storage locations of the partition and its parent measure group and cube.</span></span> <span data-ttu-id="23d74-104">儲存模式的選擇也會影響處理選擇。</span><span class="sxs-lookup"><span data-stu-id="23d74-104">The choice of storage mode also affects processing choices.</span></span>  
  
 <span data-ttu-id="23d74-105">資料分割可以使用三種基本儲存模式之一：</span><span class="sxs-lookup"><span data-stu-id="23d74-105">A partition can use one of three basic storage modes:</span></span>  
  
-   <span data-ttu-id="23d74-106">多維度 OLAP (MOLAP)</span><span class="sxs-lookup"><span data-stu-id="23d74-106">Multidimensional OLAP (MOLAP)</span></span>  
  
-   <span data-ttu-id="23d74-107">關聯式 OLAP (ROLAP)</span><span class="sxs-lookup"><span data-stu-id="23d74-107">Relational OLAP (ROLAP)</span></span>  
  
-   <span data-ttu-id="23d74-108">混合式 OLAP (HOLAP)</span><span class="sxs-lookup"><span data-stu-id="23d74-108">Hybrid OLAP (HOLAP)</span></span>  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="23d74-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 支援所有三種基本儲存模式。</span><span class="sxs-lookup"><span data-stu-id="23d74-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] supports all three basic storage modes.</span></span> <span data-ttu-id="23d74-110">另外也支援主動式快取，可以讓您結合 ROLAP 和 MOLAP 儲存的特性，提供資料的立即性和查詢效能。</span><span class="sxs-lookup"><span data-stu-id="23d74-110">It also supports proactive caching, which enables you to combine the characteristics of ROLAP and MOLAP storage for both immediacy of data and query performance.</span></span> <span data-ttu-id="23d74-111">如需詳細資訊，請參閱[主動式快取 &#40;資料分割&#41;](partitions-proactive-caching.md)。</span><span class="sxs-lookup"><span data-stu-id="23d74-111">For more information, see [Proactive Caching &#40;Partitions&#41;](partitions-proactive-caching.md).</span></span>  
  
## <a name="molap"></a><span data-ttu-id="23d74-112">MOLAP</span><span class="sxs-lookup"><span data-stu-id="23d74-112">MOLAP</span></span>  
 <span data-ttu-id="23d74-113">MOLAP 儲存模式會產生資料分割的彙總，並在處理此資料分割時，將其來源資料的副本儲存在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的多維度結構中；</span><span class="sxs-lookup"><span data-stu-id="23d74-113">The MOLAP storage mode causes the aggregations of the partition and a copy of its source data to be stored in a multidimensional structure in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] when the partition is processed.</span></span> <span data-ttu-id="23d74-114">這個 MOLAP 結構會高度最佳化，以發揮最大的查詢效能。</span><span class="sxs-lookup"><span data-stu-id="23d74-114">This MOLAP structure is highly optimized to maximize query performance.</span></span> <span data-ttu-id="23d74-115">儲存位置可以在定義資料分割的電腦上，或是在執行 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的另一部電腦上。</span><span class="sxs-lookup"><span data-stu-id="23d74-115">The storage location can be on the computer where the partition is defined or on another computer running [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="23d74-116">由於來源資料的副本會位於多維度結構中，所以可以在不存取資料分割之來源資料的情況下解析查詢；</span><span class="sxs-lookup"><span data-stu-id="23d74-116">Because a copy of the source data resides in the multidimensional structure, queries can be resolved without accessing the partition's source data.</span></span> <span data-ttu-id="23d74-117">查詢回應時間會因為使用彙總而大幅縮減。</span><span class="sxs-lookup"><span data-stu-id="23d74-117">Query response times can be decreased substantially by using aggregations.</span></span> <span data-ttu-id="23d74-118">此資料分割之 MOLAP 結構中的資料只會維持在與此資料分割的最新處理一樣的最新狀態。</span><span class="sxs-lookup"><span data-stu-id="23d74-118">The data in the partition's MOLAP structure is only as current as the most recent processing of the partition.</span></span>  
  
 <span data-ttu-id="23d74-119">隨著來源資料的變更，必須要定期處理 MOLAP 儲存中的物件，以便納入這些變更，並將這些變更提供給使用者。</span><span class="sxs-lookup"><span data-stu-id="23d74-119">As the source data changes, objects in MOLAP storage must be processed periodically to incorporate those changes and make them available to users.</span></span> <span data-ttu-id="23d74-120">處理時會更新 MOLAP 結構中的資料 (完整更新或累加更新)。</span><span class="sxs-lookup"><span data-stu-id="23d74-120">Processing updates the data in the MOLAP structure, either fully or incrementally.</span></span> <span data-ttu-id="23d74-121">某一個處理和下一個處理之間的時間，會產生一段延遲期間，在這段期間內，OLAP 物件中的資料可能會與來源資料不相符。</span><span class="sxs-lookup"><span data-stu-id="23d74-121">The time between one processing and the next creates a latency period during which data in OLAP objects may not match the source data.</span></span> <span data-ttu-id="23d74-122">您可以用累加或完整方式來更新 MOLAP 儲存中的物件，而不用讓資料分割或 Cube 離線工作；</span><span class="sxs-lookup"><span data-stu-id="23d74-122">You can incrementally or fully update objects in MOLAP storage without taking the partition or cube offline.</span></span> <span data-ttu-id="23d74-123">但是在一些情況下，您可能需要讓 Cube 離線工作，才能夠處理對 OLAP 物件的某些結構性變更。</span><span class="sxs-lookup"><span data-stu-id="23d74-123">However, there are situations that may require you to take a cube offline to process certain structural changes to OLAP objects.</span></span> <span data-ttu-id="23d74-124">您可以在臨時伺服器上更新和處理 Cube，並使用資料庫同步處理，將處理好的物件複製到實際伺服器，以減少更新 MOLAP 儲存所需的停機時間。</span><span class="sxs-lookup"><span data-stu-id="23d74-124">You can minimize the downtime required to update MOLAP storage by updating and processing cubes on a staging server and using database synchronization to copy the processed objects to the production server.</span></span> <span data-ttu-id="23d74-125">您也可以使用主動式快取，來減少延遲並提高可用性，同時還保持 MOLAP 儲存的大部分效能優點。</span><span class="sxs-lookup"><span data-stu-id="23d74-125">You can also use proactive caching to minimize latency and maximize availability while retaining much of the performance advantage of MOLAP storage.</span></span> <span data-ttu-id="23d74-126">如需詳細資訊，請參閱主動式快取 &#40;分割區[&#41;](partitions-proactive-caching.md)、[同步處理 Analysis Services 資料庫](../multidimensional-models/synchronize-analysis-services-databases.md)，以及多[維度模型物件處理](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="23d74-126">For more information, see [Proactive Caching &#40;Partitions&#41;](partitions-proactive-caching.md), [Synchronize Analysis Services Databases](../multidimensional-models/synchronize-analysis-services-databases.md), and [Multidimensional Model Object Processing](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md).</span></span>  
  
## <a name="rolap"></a><span data-ttu-id="23d74-127">ROLAP</span><span class="sxs-lookup"><span data-stu-id="23d74-127">ROLAP</span></span>  
 <span data-ttu-id="23d74-128">ROLAP 儲存模式會將資料分割的彙總儲存在關聯式資料庫內的索引檢視中 (這個關聯式資料庫是指定於資料分割的資料來源中)。</span><span class="sxs-lookup"><span data-stu-id="23d74-128">The ROLAP storage mode causes the aggregations of the partition to be stored in indexed views in the relational database that was specified in the partition's data source.</span></span> <span data-ttu-id="23d74-129">與 MOLAP 儲存模式不同，ROLAP 並不會在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料夾中儲存來源資料的副本。</span><span class="sxs-lookup"><span data-stu-id="23d74-129">Unlike the MOLAP storage mode, ROLAP does not cause a copy of the source data to be stored in the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] data folders.</span></span> <span data-ttu-id="23d74-130">而是在無法從查詢快取中衍生結果時，存取資料來源中的索引檢視來回答查詢。</span><span class="sxs-lookup"><span data-stu-id="23d74-130">Instead, when results cannot be derived from the query cache, the indexed views in the data source is accessed to answer queries.</span></span> <span data-ttu-id="23d74-131">使用 ROLAP 儲存模式的查詢回應通常會比使用 MOLAP 或 HOLAP 儲存模式的查詢回應慢。</span><span class="sxs-lookup"><span data-stu-id="23d74-131">Query response is generally slower with ROLAP storage than with the MOLAP or HOLAP storage modes.</span></span> <span data-ttu-id="23d74-132">使用 ROLAP 的處理時間通常也比較慢。</span><span class="sxs-lookup"><span data-stu-id="23d74-132">Processing time is also typically slower with ROLAP.</span></span> <span data-ttu-id="23d74-133">但是，ROLAP 會讓使用者即時檢視資料，而且當您在使用不常被查詢的大型資料集 (例如，純綷的記錄資料) 時，可以節省儲存空間。</span><span class="sxs-lookup"><span data-stu-id="23d74-133">However, ROLAP enables users to view data in real time and can save storage space when you are working with large datasets that are infrequently queried, such as purely historical data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="23d74-134">使用 ROLAP 時，如果合併使用聯結與 GROUP BY 子句，則 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 可能會傳回與未知成員相關的不正確資訊。</span><span class="sxs-lookup"><span data-stu-id="23d74-134">When using ROLAP, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] may return incorrect information related to the unknown member if a join is combined with a GROUP BY clause.</span></span> <span data-ttu-id="23d74-135">而 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會消除關聯式完整性錯誤，而非傳回未知的成員值。</span><span class="sxs-lookup"><span data-stu-id="23d74-135">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] eliminates relational integrity errors instead of returning the unknown member value.</span></span>  
  
 <span data-ttu-id="23d74-136">如果資料分割使用 ROLAP 儲存模式，而其來源資料儲存在 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 中，則 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會嘗試建立索引檢視，以包含資料分割的彙總。</span><span class="sxs-lookup"><span data-stu-id="23d74-136">If a partition uses the ROLAP storage mode and its source data is stored in [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] tries to create indexed views to contain aggregations of the partition.</span></span> <span data-ttu-id="23d74-137">如果 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 無法建立索引檢視，則不會建立彙總資料表。</span><span class="sxs-lookup"><span data-stu-id="23d74-137">If [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] cannot create indexed views, it does not create aggregation tables.</span></span> <span data-ttu-id="23d74-138">雖然 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會處理在 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 上建立索引檢視的工作階段需求，但是 ROLAP 資料分割及其結構描述中的資料表必須符合下列條件，才能讓 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 建立彙總的索引檢視：</span><span class="sxs-lookup"><span data-stu-id="23d74-138">Although [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] handles the session requirements for creating indexed views on [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], the following conditions must be met by the ROLAP partition and the tables in its schema in order for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to create indexed views for aggregations:</span></span>  
  
-   <span data-ttu-id="23d74-139">資料分割不能包含使用 `Min` 或 `Max` 彙總函式的量值。</span><span class="sxs-lookup"><span data-stu-id="23d74-139">The partition cannot contain measures that use the `Min` or `Max` aggregate functions.</span></span>  
  
-   <span data-ttu-id="23d74-140">ROLAP 資料分割之結構描述中的每份資料表都只能使用一次。</span><span class="sxs-lookup"><span data-stu-id="23d74-140">Each table in the schema of the ROLAP partition must be used only one time.</span></span> <span data-ttu-id="23d74-141">例如，結構描述不能包含 [dbo].[address] AS "Customer Address" 和 [dbo].[address] AS "SalesRep Address"。</span><span class="sxs-lookup"><span data-stu-id="23d74-141">For example, the schema cannot contain [dbo].[address] AS "Customer Address" and [dbo].[address] AS "SalesRep Address".</span></span>  
  
-   <span data-ttu-id="23d74-142">每個資料表都必須是一個資料表，而不是一個檢視。</span><span class="sxs-lookup"><span data-stu-id="23d74-142">Each table must be a table, not a view.</span></span>  
  
-   <span data-ttu-id="23d74-143">資料分割之結構描述中的所有資料表名稱都必須具有擁有者的完整名稱 (例如，[dbo].[customer])。</span><span class="sxs-lookup"><span data-stu-id="23d74-143">All table names in the partition's schema must be qualified with the owner name, for example, [dbo].[customer].</span></span>  
  
-   <span data-ttu-id="23d74-144">資料分割之結構描述中的所有資料表都必須具有相同的擁有者；例如，您不可擁有參考 [tk].[customer]、[john].[store] 和 [dave].[sales_fact_2004] 資料表的 FROM 子句。</span><span class="sxs-lookup"><span data-stu-id="23d74-144">All tables in the partition's schema must have the same owner; for example, you cannot have a FROM clause that references the tables [tk].[customer], [john].[store], and [dave].[sales_fact_2004].</span></span>  
  
-   <span data-ttu-id="23d74-145">資料分割之量值的來源資料行不可為 Null。</span><span class="sxs-lookup"><span data-stu-id="23d74-145">The source columns of the partition's measures must not be nullable.</span></span>  
  
-   <span data-ttu-id="23d74-146">用於檢視中的所有資料表，必須在下列選項設定成 ON 的情況下建立：</span><span class="sxs-lookup"><span data-stu-id="23d74-146">All tables used in the view must have been created with the following options set to ON:</span></span>  
  
    -   <span data-ttu-id="23d74-147">ANSI_NULLS</span><span class="sxs-lookup"><span data-stu-id="23d74-147">ANSI_NULLS</span></span>  
  
    -   <span data-ttu-id="23d74-148">QUOTED_IDENTIFIER</span><span class="sxs-lookup"><span data-stu-id="23d74-148">QUOTED_IDENTIFIER</span></span>  
  
-   <span data-ttu-id="23d74-149">在 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 中，索引鍵的大小總計不可能超過 900 個位元組。</span><span class="sxs-lookup"><span data-stu-id="23d74-149">The total size of the index key, in [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], cannot exceed 900 bytes.</span></span> [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]<span data-ttu-id="23d74-150">會在處理 CREATE INDEX 語句時，根據固定長度的索引鍵資料行來判斷提示此條件。</span><span class="sxs-lookup"><span data-stu-id="23d74-150">will assert this condition based on the fixed length key columns when the CREATE INDEX statement is processed.</span></span> <span data-ttu-id="23d74-151">不過，如果索引鍵中有可變長度的資料行， [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 也會針對基表的每次更新判斷提示此條件。</span><span class="sxs-lookup"><span data-stu-id="23d74-151">However, if there are variable length columns in the index key, [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] will also assert this condition for every update to the base tables.</span></span> <span data-ttu-id="23d74-152">因為不同彙總有不同的檢視定義，所以會依彙總設計而定，使用索引檢視的 ROLAP 處理可能成功也可能失敗。</span><span class="sxs-lookup"><span data-stu-id="23d74-152">Because different aggregations have different view definitions, ROLAP processing using indexed views can succeed or fail depending on the aggregation design.</span></span>  
  
-   <span data-ttu-id="23d74-153">建立索引檢視的工作階段必須將下列選項設為 ON：ARITHABORT、CONCAT_NULL_YEILDS_NULL、QUOTED_IDENTIFIER、ANSI_NULLS、ANSI_PADDING 和 ANSI_WARNING。</span><span class="sxs-lookup"><span data-stu-id="23d74-153">The session creating the indexed view must have the following options set to ON: ARITHABORT, CONCAT_NULL_YEILDS_NULL, QUOTED_IDENTIFIER, ANSI_NULLS, ANSI_PADDING, and ANSI_WARNING.</span></span> <span data-ttu-id="23d74-154">您可以在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中變更這項設定。</span><span class="sxs-lookup"><span data-stu-id="23d74-154">This setting can be made in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
-   <span data-ttu-id="23d74-155">建立索引檢視的工作階段必須將下列選項設為 OFF：NUMERIC_ROUNDABORT。</span><span class="sxs-lookup"><span data-stu-id="23d74-155">The session creating the indexed view must have the following option set to OFF: NUMERIC_ROUNDABORT.</span></span> <span data-ttu-id="23d74-156">您可以在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中變更這項設定。</span><span class="sxs-lookup"><span data-stu-id="23d74-156">This setting can be made in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
## <a name="holap"></a><span data-ttu-id="23d74-157">HOLAP</span><span class="sxs-lookup"><span data-stu-id="23d74-157">HOLAP</span></span>  
 <span data-ttu-id="23d74-158">HOLAP 儲存模式會結合 MOLAP 和 ROLAP 的屬性。</span><span class="sxs-lookup"><span data-stu-id="23d74-158">The HOLAP storage mode combines attributes of both MOLAP and ROLAP.</span></span> <span data-ttu-id="23d74-159">就像 MOLAP 一樣，HOLAP 會使資料分割的匯總儲存在實例的多維度結構中 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="23d74-159">Like MOLAP, HOLAP causes the aggregations of the partition to be stored in a multidimensional structure in an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="23d74-160">HOLAP 不會儲存來源資料的副本。</span><span class="sxs-lookup"><span data-stu-id="23d74-160">HOLAP does not cause a copy of the source data to be stored.</span></span> <span data-ttu-id="23d74-161">針對只存取資料分割彙總之摘要資料的查詢，HOLAP 相當於 MOLAP。</span><span class="sxs-lookup"><span data-stu-id="23d74-161">For queries that access only summary data in the aggregations of a partition, HOLAP is the equivalent of MOLAP.</span></span> <span data-ttu-id="23d74-162">存取來源資料的查詢-例如，如果您想要向下切入到沒有匯總資料的不可部份完成 cube 資料格，則必須從關係資料庫中取出資料，而且如果來源資料儲存在 MOLAP 結構中，其速度將不會快上。</span><span class="sxs-lookup"><span data-stu-id="23d74-162">Queries that access source data-for example, if you want to drill down to an atomic cube cell for which there is no aggregation data-must retrieve data from the relational database and will not be as fast as they would be if the source data were stored in the MOLAP structure.</span></span> <span data-ttu-id="23d74-163">在 HOLAP 儲存模式下，使用者經常會遇到查詢時間有大幅差異的情況，而這是根據可以從快取或彙總來解析查詢，還是從來源資料本身解析查詢而定。</span><span class="sxs-lookup"><span data-stu-id="23d74-163">With HOLAP storage mode, users will typically experience substantial differences in query times depending upon whether the query can be resolved from cache or aggregations versus from the source data itself.</span></span>  
  
 <span data-ttu-id="23d74-164">因為儲存為 HOLAP 的資料分割不包含來源資料，所以會比同等的 MOLAP 資料分割還小，而且針對涉及摘要資料之查詢的回應速度也會比 ROLAP 資料分割還快。</span><span class="sxs-lookup"><span data-stu-id="23d74-164">Partitions stored as HOLAP are smaller than the equivalent MOLAP partitions because they do not contain source data and respond faster than ROLAP partitions for queries involving summary data.</span></span> <span data-ttu-id="23d74-165">HOLAP 儲存模式一般是適用於 Cube 中的資料分割，而這類資料分割需要根據大量來源資料以快速回應摘要查詢。</span><span class="sxs-lookup"><span data-stu-id="23d74-165">HOLAP storage mode is generally suited for partitions in cubes that require rapid query response for summaries based on a large amount of source data.</span></span> <span data-ttu-id="23d74-166">但是，如果使用者產生必須接觸分葉層級資料的查詢 (例如計算中間值)，MOLAP 通常是較好的選擇。</span><span class="sxs-lookup"><span data-stu-id="23d74-166">However, where users generate queries that must touch leaf level data, such as for calculating median values, MOLAP is generally a better choice.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23d74-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23d74-167">See Also</span></span>  
 <span data-ttu-id="23d74-168">[主動式快取 &#40;分割區&#41;](partitions-proactive-caching.md) </span><span class="sxs-lookup"><span data-stu-id="23d74-168">[Proactive Caching &#40;Partitions&#41;](partitions-proactive-caching.md) </span></span>  
 <span data-ttu-id="23d74-169">[同步處理 Analysis Services 資料庫](../multidimensional-models/synchronize-analysis-services-databases.md) </span><span class="sxs-lookup"><span data-stu-id="23d74-169">[Synchronize Analysis Services Databases](../multidimensional-models/synchronize-analysis-services-databases.md) </span></span>  
 [<span data-ttu-id="23d74-170">資料分割 &#40;Analysis Services - 多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="23d74-170">Partitions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](partitions-analysis-services-multidimensional-data.md)  
  
  