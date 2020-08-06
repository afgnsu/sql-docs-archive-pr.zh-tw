---
title: 篩選對話方塊 (適用於 Excel 的 MDS 增益集) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: b987b141-5abf-4161-a073-4cfc3e7f5aae
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: b58fd23fe4622515c8424574ad97d61971da9262
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599037"
---
# <a name="filter-dialog-box-mds-add-in-for-excel"></a><span data-ttu-id="3278a-102">篩選對話方塊 (適用於 Excel 的 MDS 增益集)</span><span class="sxs-lookup"><span data-stu-id="3278a-102">Filter Dialog Box (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="3278a-103">在中 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] ，您可以使用 [**篩選**] 對話方塊，在將 MDS 管理的資料載入 Excel 之前縮小其清單範圍。</span><span class="sxs-lookup"><span data-stu-id="3278a-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], use the **Filter** dialog box to narrow the list of MDS-managed data before loading it into Excel.</span></span>  
  
 <span data-ttu-id="3278a-104">這個對話方塊包含三個區段：[資料行]\*\*\*\*、[資料列]\*\*\*\* 和 [摘要]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3278a-104">This dialog box contains three sections: **Columns**, **Rows**, and **Summary**.</span></span>  
  
## <a name="columns"></a><span data-ttu-id="3278a-105">資料行</span><span class="sxs-lookup"><span data-stu-id="3278a-105">Columns</span></span>  
 <span data-ttu-id="3278a-106">使用 [資料行]\*\*\*\* 區段可決定您想要在 Excel 中顯示的屬性 (資料行)。</span><span class="sxs-lookup"><span data-stu-id="3278a-106">Use the **Columns** section to determine which attributes (columns) you want to display in Excel.</span></span>  
  
|<span data-ttu-id="3278a-107">控制項名稱</span><span class="sxs-lookup"><span data-stu-id="3278a-107">Control Name</span></span>|<span data-ttu-id="3278a-108">描述</span><span class="sxs-lookup"><span data-stu-id="3278a-108">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="3278a-109">屬性類型</span><span class="sxs-lookup"><span data-stu-id="3278a-109">Attribute type</span></span>|<span data-ttu-id="3278a-110">屬性類型會描述您想要使用的成員類型。</span><span class="sxs-lookup"><span data-stu-id="3278a-110">An attribute type describes the type of members you want to work with.</span></span> <span data-ttu-id="3278a-111">在大多數情況下，這種類型是 [分葉]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3278a-111">In most cases, this is **Leaf**.</span></span> <span data-ttu-id="3278a-112">如需成員類型的詳細資訊，請參閱[成員 &#40;Master Data Services&#41;](../members-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="3278a-112">For more information about member types, see [Members &#40;Master Data Services&#41;](../members-master-data-services.md).</span></span>|  
|<span data-ttu-id="3278a-113">明確階層</span><span class="sxs-lookup"><span data-stu-id="3278a-113">Explicit hierarchy</span></span>|<span data-ttu-id="3278a-114">如果您選擇 [合併]\*\*\*\* 屬性類型，請選擇這些合併成員所屬的階層。</span><span class="sxs-lookup"><span data-stu-id="3278a-114">If you chose the **Consolidated** attribute type, choose the hierarchy the consolidated members belong to.</span></span> <span data-ttu-id="3278a-115">如需詳細資訊，請參閱 [明確階層 &#40;Master Data Services&#41;](../explicit-hierarchies-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="3278a-115">For more information, see [Explicit Hierarchies &#40;Master Data Services&#41;](../explicit-hierarchies-master-data-services.md).</span></span>|  
|<span data-ttu-id="3278a-116">屬性群組</span><span class="sxs-lookup"><span data-stu-id="3278a-116">Attribute Groups</span></span>|<span data-ttu-id="3278a-117">屬性群組是將屬性子集分組的方式。</span><span class="sxs-lookup"><span data-stu-id="3278a-117">Attribute groups are a way of grouping subsets of attributes.</span></span> <span data-ttu-id="3278a-118">如果您想要顯示可用屬性的子集，請選擇屬性群組。</span><span class="sxs-lookup"><span data-stu-id="3278a-118">Choose an attribute group if you want to show a subset of available attributes.</span></span> <span data-ttu-id="3278a-119">如需屬性群組的詳細資訊，請參閱[屬性群組 &#40;Master Data Services&#41;](../attribute-groups-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="3278a-119">For more information about attribute groups, see [Attribute Groups &#40;Master Data Services&#41;](../attribute-groups-master-data-services.md).</span></span>|  
|<span data-ttu-id="3278a-120">全選</span><span class="sxs-lookup"><span data-stu-id="3278a-120">Select All</span></span>|<span data-ttu-id="3278a-121">按一下即可選取清單中顯示的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="3278a-121">Click to select all attributes displayed in the list.</span></span>|  
|<span data-ttu-id="3278a-122">全部清除</span><span class="sxs-lookup"><span data-stu-id="3278a-122">Clear All</span></span>|<span data-ttu-id="3278a-123">按一下即可清除清單中顯示的選取屬性。</span><span class="sxs-lookup"><span data-stu-id="3278a-123">Click to clear the selected attributes displayed in the list.</span></span><br /><br /> <span data-ttu-id="3278a-124">注意：您無法清除**名稱**和程式**代碼**。</span><span class="sxs-lookup"><span data-stu-id="3278a-124">Note: You cannot clear **Name** and **Code**.</span></span>|  
|<span data-ttu-id="3278a-125">向上箭號</span><span class="sxs-lookup"><span data-stu-id="3278a-125">Up Arrow</span></span>|<span data-ttu-id="3278a-126">按一下即可將選取的屬性在清單中向上移動。</span><span class="sxs-lookup"><span data-stu-id="3278a-126">Click to move the selected attribute up in the list.</span></span> <span data-ttu-id="3278a-127">由上至下順序會對應至資料行在工作表中顯示的由左至右順序。</span><span class="sxs-lookup"><span data-stu-id="3278a-127">The top-to-bottom order corresponds to the left-to-right order the columns are displayed in the worksheet.</span></span>|  
|<span data-ttu-id="3278a-128">向下箭號</span><span class="sxs-lookup"><span data-stu-id="3278a-128">Down Arrow</span></span>|<span data-ttu-id="3278a-129">按一下即可將選取的屬性在清單中向下移動。</span><span class="sxs-lookup"><span data-stu-id="3278a-129">Click to move the selected attribute down in the list.</span></span> <span data-ttu-id="3278a-130">由上至下順序會對應至資料行在工作表中顯示的由左至右順序。</span><span class="sxs-lookup"><span data-stu-id="3278a-130">The top-to-bottom order corresponds to the left-to-right order the columns are displayed in the worksheet.</span></span>|  
  
## <a name="rows"></a><span data-ttu-id="3278a-131">資料列</span><span class="sxs-lookup"><span data-stu-id="3278a-131">Rows</span></span>  
 <span data-ttu-id="3278a-132">使用 [資料列]\*\*\*\* 區段可決定您想要在 Excel 中顯示的成員 (資料列)。</span><span class="sxs-lookup"><span data-stu-id="3278a-132">Use the **Rows** section to determine which members (rows) you want to display in Excel.</span></span> <span data-ttu-id="3278a-133">您可以透過定義準則進行此作業，以便篩選即將顯示的資料列。</span><span class="sxs-lookup"><span data-stu-id="3278a-133">You do this by defining criteria to filter the rows that will be displayed.</span></span>  
  
|<span data-ttu-id="3278a-134">控制項名稱</span><span class="sxs-lookup"><span data-stu-id="3278a-134">Control Name</span></span>|<span data-ttu-id="3278a-135">描述</span><span class="sxs-lookup"><span data-stu-id="3278a-135">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="3278a-136">屬性</span><span class="sxs-lookup"><span data-stu-id="3278a-136">Attribute</span></span>|<span data-ttu-id="3278a-137">顯示您想要據以篩選的屬性。</span><span class="sxs-lookup"><span data-stu-id="3278a-137">Displays an attribute you want to filter by.</span></span> <span data-ttu-id="3278a-138">如果沒有列出任何屬性，這是因為尚未新增屬性。</span><span class="sxs-lookup"><span data-stu-id="3278a-138">If no attributes are listed, it's because they have not been added.</span></span><br /><br /> <span data-ttu-id="3278a-139">注意：您可以依照不想要在工作表中顯示的屬性來篩選。</span><span class="sxs-lookup"><span data-stu-id="3278a-139">Note: You can filter by attributes that you don't plan to show in the worksheet.</span></span>|  
|<span data-ttu-id="3278a-140">運算子</span><span class="sxs-lookup"><span data-stu-id="3278a-140">Operator</span></span>|<span data-ttu-id="3278a-141">顯示對應至已選取之屬性類型的運算子。</span><span class="sxs-lookup"><span data-stu-id="3278a-141">Displays operators that correspond to the type of attribute that was selected.</span></span> <span data-ttu-id="3278a-142">如需詳細資訊，請參閱[篩選運算子 &#40;Master Data Services&#41;](../filter-operators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="3278a-142">For more information, see [Filter Operators &#40;Master Data Services&#41;](../filter-operators-master-data-services.md).</span></span>|  
|<span data-ttu-id="3278a-143">準則</span><span class="sxs-lookup"><span data-stu-id="3278a-143">Criteria</span></span>|<span data-ttu-id="3278a-144">您想要據以篩選的準則。</span><span class="sxs-lookup"><span data-stu-id="3278a-144">The criteria you want to filter by.</span></span>|  
|<span data-ttu-id="3278a-145">更新摘要</span><span class="sxs-lookup"><span data-stu-id="3278a-145">Update Summary</span></span>|<span data-ttu-id="3278a-146">使用大型資料集時，按一下即可使用即將載入之資料量的詳細資料來更新 [摘要]\*\*\*\* 區段。</span><span class="sxs-lookup"><span data-stu-id="3278a-146">When working with large datasets, click to update the **Summary** section with details of the amount of data that will be loaded.</span></span>|  
|<span data-ttu-id="3278a-147">新增</span><span class="sxs-lookup"><span data-stu-id="3278a-147">Add</span></span>|<span data-ttu-id="3278a-148">如果您按一下 [資料行]\*\*\*\* 區段中的屬性，然後按一下 [加入]\*\*\*\*，屬性就會加入篩選清單中。</span><span class="sxs-lookup"><span data-stu-id="3278a-148">When you click an attribute in the **Columns** section and then click **Add**, an attribute is added to the list of filters.</span></span>|  
|<span data-ttu-id="3278a-149">全部移除</span><span class="sxs-lookup"><span data-stu-id="3278a-149">Remove All</span></span>|<span data-ttu-id="3278a-150">從清單中移除所有篩選。</span><span class="sxs-lookup"><span data-stu-id="3278a-150">Removes all filters from the list.</span></span>|  
|<span data-ttu-id="3278a-151">移除</span><span class="sxs-lookup"><span data-stu-id="3278a-151">Remove</span></span>|<span data-ttu-id="3278a-152">從清單中移除選取的篩選。</span><span class="sxs-lookup"><span data-stu-id="3278a-152">Removes selected filter from the list.</span></span>|  
  
## <a name="summary"></a><span data-ttu-id="3278a-153">總結</span><span class="sxs-lookup"><span data-stu-id="3278a-153">Summary</span></span>  
 <span data-ttu-id="3278a-154">使用 [摘要]\*\*\*\* 區段即可在載入之前檢視即將載入之資料量的相關詳細資料。</span><span class="sxs-lookup"><span data-stu-id="3278a-154">Use the **Summary** section to view details about the amount of data that will be loaded, before loading it.</span></span>  
  
|<span data-ttu-id="3278a-155">控制項名稱</span><span class="sxs-lookup"><span data-stu-id="3278a-155">Control Name</span></span>|<span data-ttu-id="3278a-156">描述</span><span class="sxs-lookup"><span data-stu-id="3278a-156">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="3278a-157">模型</span><span class="sxs-lookup"><span data-stu-id="3278a-157">Model</span></span>|<span data-ttu-id="3278a-158">模型的名稱。</span><span class="sxs-lookup"><span data-stu-id="3278a-158">The name of the model.</span></span>|  
|<span data-ttu-id="3278a-159">版本</span><span class="sxs-lookup"><span data-stu-id="3278a-159">Version</span></span>|<span data-ttu-id="3278a-160">版本的名稱。</span><span class="sxs-lookup"><span data-stu-id="3278a-160">The name of the version.</span></span>|  
|<span data-ttu-id="3278a-161">單位</span><span class="sxs-lookup"><span data-stu-id="3278a-161">Entity</span></span>|<span data-ttu-id="3278a-162">實體的名稱。</span><span class="sxs-lookup"><span data-stu-id="3278a-162">The name of the entity.</span></span>|  
|<span data-ttu-id="3278a-163">資料列</span><span class="sxs-lookup"><span data-stu-id="3278a-163">Rows</span></span>|<span data-ttu-id="3278a-164">根據 [資料列]\*\*\*\* 區段中套用的篩選，即將載入 Excel 中的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="3278a-164">The number of rows that will be loaded into Excel, based on the filters applied in the **Rows** section.</span></span>|  
|<span data-ttu-id="3278a-165">資料行</span><span class="sxs-lookup"><span data-stu-id="3278a-165">Columns</span></span>|<span data-ttu-id="3278a-166">根據 [資料行]\*\*\*\* 區段中選取的屬性，即將載入 Excel 中的資料行數目。</span><span class="sxs-lookup"><span data-stu-id="3278a-166">The number of columns that will be loaded into Excel, based on the attributes selected in the **Columns** section.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3278a-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3278a-167">See Also</span></span>  
 <span data-ttu-id="3278a-168">[載入 &#40;適用于 Excel 的 MDS 增益集之前先篩選資料&#41;](filter-data-before-exporting-mds-add-in-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="3278a-168">[Filter Data before Loading &#40;MDS Add-in for Excel&#41;](filter-data-before-exporting-mds-add-in-for-excel.md) </span></span>  
 [<span data-ttu-id="3278a-169">載入適用于 Excel 的 MDS 增益集&#41;的資料 &#40;</span><span class="sxs-lookup"><span data-stu-id="3278a-169">Loading Data &#40;MDS Add-in for Excel&#41;</span></span>](overview-exporting-data-to-excel-mds-add-in-for-excel.md)  
  
  