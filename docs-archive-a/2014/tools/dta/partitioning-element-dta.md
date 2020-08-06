---
title: " (DTA) 的資料分割元素 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Partitioning element
ms.assetid: 9bc5d1d5-27a7-4434-966f-c3935794af27
author: stevestein
ms.author: sstein
ms.openlocfilehash: f38626f516bd45e31a671992897f21d22a1498c4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598097"
---
# <a name="partitioning-element-dta"></a><span data-ttu-id="fe6d8-102">Partitioning 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="fe6d8-102">Partitioning Element (DTA)</span></span>
  <span data-ttu-id="fe6d8-103">包含在分析期間，Database Engine Tuning Advisor 所要使用的資料分割配置。</span><span class="sxs-lookup"><span data-stu-id="fe6d8-103">Contains the partitioning scheme that you would like Database Engine Tuning Advisor to use during analysis.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe6d8-104">語法</span><span class="sxs-lookup"><span data-stu-id="fe6d8-104">Syntax</span></span>  
  
```  
  
<DTAInput>  
...code removed...  
    <TuningOptions>  
      <Partitioning>...</Partitioning>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="fe6d8-105">元素特性</span><span class="sxs-lookup"><span data-stu-id="fe6d8-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="fe6d8-106">特性</span><span class="sxs-lookup"><span data-stu-id="fe6d8-106">Characteristic</span></span>|<span data-ttu-id="fe6d8-107">描述</span><span class="sxs-lookup"><span data-stu-id="fe6d8-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="fe6d8-108">**資料類型和長度**</span><span class="sxs-lookup"><span data-stu-id="fe6d8-108">**Data type and length**</span></span>|<span data-ttu-id="fe6d8-109">`string`，沒有最大長度。</span><span class="sxs-lookup"><span data-stu-id="fe6d8-109">`string`, no maximum length.</span></span>|  
|<span data-ttu-id="fe6d8-110">**允許的值**</span><span class="sxs-lookup"><span data-stu-id="fe6d8-110">**Allowed values**</span></span>|<span data-ttu-id="fe6d8-111">**NONE**</span><span class="sxs-lookup"><span data-stu-id="fe6d8-111">**NONE**</span></span><br /> <span data-ttu-id="fe6d8-112">沒有資料分割。</span><span class="sxs-lookup"><span data-stu-id="fe6d8-112">No partitioning.</span></span><br /><br /> <span data-ttu-id="fe6d8-113">**FULL**</span><span class="sxs-lookup"><span data-stu-id="fe6d8-113">**FULL**</span></span><br /> <span data-ttu-id="fe6d8-114">完整的資料分割。</span><span class="sxs-lookup"><span data-stu-id="fe6d8-114">Full partitioning.</span></span> <span data-ttu-id="fe6d8-115">(增強效能。)</span><span class="sxs-lookup"><span data-stu-id="fe6d8-115">(Enhances performance.)</span></span><br /><br /> <span data-ttu-id="fe6d8-116">**ALIGNED**</span><span class="sxs-lookup"><span data-stu-id="fe6d8-116">**ALIGNED**</span></span><br /> <span data-ttu-id="fe6d8-117">只有對齊的資料分割。</span><span class="sxs-lookup"><span data-stu-id="fe6d8-117">Aligned partitioning only.</span></span> <span data-ttu-id="fe6d8-118">(增強管理功能。)</span><span class="sxs-lookup"><span data-stu-id="fe6d8-118">(Enhances manageability.)</span></span><br /><br /> <span data-ttu-id="fe6d8-119">這個元素只能使用這些值的其中之一。</span><span class="sxs-lookup"><span data-stu-id="fe6d8-119">Use only one of these values with this element.</span></span><br /><br /> <span data-ttu-id="fe6d8-120">**ALIGNED** 表示在 Database Engine Tuning Advisor 所產生的建議中，每個提出的索引都完全依照索引定義基礎資料表的相同方式來分割。</span><span class="sxs-lookup"><span data-stu-id="fe6d8-120">**ALIGNED** means that in the recommendation generated by Database Engine Tuning Advisor every proposed index is partitioned in exactly the same way as the underlying table for which the index is defined.</span></span> <span data-ttu-id="fe6d8-121">索引檢視表中的非叢集索引會對齊索引檢視表。</span><span class="sxs-lookup"><span data-stu-id="fe6d8-121">Nonclustered indexes on an indexed view are aligned with the indexed view.</span></span>|  
|<span data-ttu-id="fe6d8-122">**預設值**</span><span class="sxs-lookup"><span data-stu-id="fe6d8-122">**Default value**</span></span>|<span data-ttu-id="fe6d8-123">**NONE**</span><span class="sxs-lookup"><span data-stu-id="fe6d8-123">**NONE**</span></span>|  
|<span data-ttu-id="fe6d8-124">**出現次數**</span><span class="sxs-lookup"><span data-stu-id="fe6d8-124">**Occurrence**</span></span>|<span data-ttu-id="fe6d8-125">除非使用 `TuningOptions` 元素，否則，`DropOnlyMode` 元素需要使用這個元素一次。</span><span class="sxs-lookup"><span data-stu-id="fe6d8-125">Required once for the `TuningOptions` element, unless the `DropOnlyMode` element is used.</span></span> <span data-ttu-id="fe6d8-126">如果使用 `DropOnlyMode`，您便無法使用 `Partitioning`。</span><span class="sxs-lookup"><span data-stu-id="fe6d8-126">If `DropOnlyMode` is used, you cannot use `Partitioning`.</span></span> <span data-ttu-id="fe6d8-127">這些元素互斥。</span><span class="sxs-lookup"><span data-stu-id="fe6d8-127">These elements are mutually exclusive.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="fe6d8-128">元素關聯性</span><span class="sxs-lookup"><span data-stu-id="fe6d8-128">Element Relationships</span></span>  
  
|<span data-ttu-id="fe6d8-129">關聯性</span><span class="sxs-lookup"><span data-stu-id="fe6d8-129">Relationship</span></span>|<span data-ttu-id="fe6d8-130">元素</span><span class="sxs-lookup"><span data-stu-id="fe6d8-130">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="fe6d8-131">**父元素**</span><span class="sxs-lookup"><span data-stu-id="fe6d8-131">**Parent element**</span></span>|[<span data-ttu-id="fe6d8-132">TuningOptions 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="fe6d8-132">TuningOptions Element &#40;DTA&#41;</span></span>](tuningoptions-element-dta.md)|  
|<span data-ttu-id="fe6d8-133">**子元素**</span><span class="sxs-lookup"><span data-stu-id="fe6d8-133">**Child elements**</span></span>|<span data-ttu-id="fe6d8-134">無。</span><span class="sxs-lookup"><span data-stu-id="fe6d8-134">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fe6d8-135">範例</span><span class="sxs-lookup"><span data-stu-id="fe6d8-135">Example</span></span>  
 <span data-ttu-id="fe6d8-136">如需此元素的使用範例，請參閱[簡單 XML 輸入檔範例 &#40;DTA&#41;](simple-xml-input-file-sample-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="fe6d8-136">For a usage example of this element, see the [Simple XML Input File Sample &#40;DTA&#41;](simple-xml-input-file-sample-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe6d8-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fe6d8-137">See Also</span></span>  
 [<span data-ttu-id="fe6d8-138">XML 輸入檔參考XML Input File ReferenceDatabase Engine Tuning Advisor&#41;</span><span class="sxs-lookup"><span data-stu-id="fe6d8-138">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  