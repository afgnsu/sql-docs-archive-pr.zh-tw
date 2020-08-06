---
title: 加入、變更或刪除報表參數的預設值 (報表產生器和 SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10460"
- sql12.rtp.rptdesigner.reportparameters.defaultvalues.f1
- "10072"
ms.assetid: 6a87e069-b3a9-47b6-bcec-afcdd8aff65f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1d50fdbbe42a656ef839785c0968b36c8c829e11
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595763"
---
# <a name="add-change-or-delete-default-values-for-a-report-parameter-report-builder-and-ssrs"></a><span data-ttu-id="261a6-102">為報表參數加入、變更或刪除預設值 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="261a6-102">Add, Change, or Delete Default Values for a Report Parameter (Report Builder and SSRS)</span></span>
  <span data-ttu-id="261a6-103">當您建立報表參數以後，可以提供預設值的清單。</span><span class="sxs-lookup"><span data-stu-id="261a6-103">After you create a report parameter, you can provide a list of default values.</span></span> <span data-ttu-id="261a6-104">如果所有的參數都有有效的預設值，當您第一次檢視或預覽報表時，報表就會自動執行。</span><span class="sxs-lookup"><span data-stu-id="261a6-104">If all parameters have a valid default value, the report runs automatically when you first view or preview it.</span></span>  
  
 <span data-ttu-id="261a6-105">報表參數可代表一個值或多個值。</span><span class="sxs-lookup"><span data-stu-id="261a6-105">Report parameters can represent one value or multiple values.</span></span> <span data-ttu-id="261a6-106">如果是單一值，您可以提供常值或運算式。</span><span class="sxs-lookup"><span data-stu-id="261a6-106">For single values, you can provide a literal or expression.</span></span> <span data-ttu-id="261a6-107">如果是多個值，您可以提供靜態清單或報表資料集中的清單。</span><span class="sxs-lookup"><span data-stu-id="261a6-107">For multiple values, you can provide a static list or a list from a report dataset.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 <span data-ttu-id="261a6-108">在您發行報表之後，可以在報表伺服器上設定參數屬性值，藉以覆寫您在報表撰寫工具中定義於報表的預設值。</span><span class="sxs-lookup"><span data-stu-id="261a6-108">After you publish a report, you can override the default values that you define in the report in the report authoring tool, by setting parameter property values on the report server.</span></span> <span data-ttu-id="261a6-109">您也可以建立連結報表來提供多組預設參數值。</span><span class="sxs-lookup"><span data-stu-id="261a6-109">You can also provide multiple sets of default parameter values by creating linked reports.</span></span> <span data-ttu-id="261a6-110">如需詳細資訊，請參閱  [報表參數 &#40;報表產生器和報表設計師&#41;](report-parameters-report-builder-and-report-designer.md)</span><span class="sxs-lookup"><span data-stu-id="261a6-110">For more information, see  [Report Parameters &#40;Report Builder and Report Designer&#41;](report-parameters-report-builder-and-report-designer.md)</span></span>  
  
### <a name="to-add-or-change-the-default-values-for-a-report-parameter"></a><span data-ttu-id="261a6-111">為報表參數加入或變更預設值</span><span class="sxs-lookup"><span data-stu-id="261a6-111">To add or change the default values for a report parameter</span></span>  
  
1.  <span data-ttu-id="261a6-112">在 [報表資料] 窗格中，展開 [參數]  節點。</span><span class="sxs-lookup"><span data-stu-id="261a6-112">In the Report Data pane, expand the **Parameters** node.</span></span> <span data-ttu-id="261a6-113">以滑鼠右鍵按一下此參數，然後按一下 [編輯]  。</span><span class="sxs-lookup"><span data-stu-id="261a6-113">Right-click the parameter and click **Edit**.</span></span> <span data-ttu-id="261a6-114">**[報表參數屬性]** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="261a6-114">The **Report Parameter Properties** dialog box opens.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="261a6-115">如果看不到 [報表資料] 窗格，請按一下 [檢視]  ，然後按一下 [報表資料]  。</span><span class="sxs-lookup"><span data-stu-id="261a6-115">If the Report Data pane is not visible, click **View** and then click **Report Data**.</span></span>  
  
2.  <span data-ttu-id="261a6-116">按一下 **[預設值]** 。</span><span class="sxs-lookup"><span data-stu-id="261a6-116">Click **Default Values**.</span></span>  
  
3.  <span data-ttu-id="261a6-117">選取預設選項：</span><span class="sxs-lookup"><span data-stu-id="261a6-117">Select a default option:</span></span>  
  
    -   <span data-ttu-id="261a6-118">若要手動提供某個值或值清單，請按一下 [指定值]  。</span><span class="sxs-lookup"><span data-stu-id="261a6-118">To manually provide a value or list of values, click **Specify values**.</span></span> <span data-ttu-id="261a6-119">按一下 [新增]  ，然後在 [值]  文字方塊中輸入值。</span><span class="sxs-lookup"><span data-stu-id="261a6-119">Click **Add** and then enter the value in the **Value** text box.</span></span> <span data-ttu-id="261a6-120">您可以撰寫值的運算式。</span><span class="sxs-lookup"><span data-stu-id="261a6-120">You can write an expression for a value.</span></span> <span data-ttu-id="261a6-121">資料類型必須符合參數的資料類型。</span><span class="sxs-lookup"><span data-stu-id="261a6-121">The data type must match the data type of the parameter.</span></span> <span data-ttu-id="261a6-122">欄位名稱不能用於參數的運算式。</span><span class="sxs-lookup"><span data-stu-id="261a6-122">Field names cannot be used in an expression for a parameter.</span></span>  
  
         <span data-ttu-id="261a6-123">如果是多值參數，請重複這個步驟，盡量提供您想要的值。</span><span class="sxs-lookup"><span data-stu-id="261a6-123">For multivalue parameters, repeat this step for as many values as you want to provide.</span></span> <span data-ttu-id="261a6-124">您在這個清單中看到的項目順序會決定使用者在下拉式清單中看到它們的順序。</span><span class="sxs-lookup"><span data-stu-id="261a6-124">The order of items you see in this list determines the order that the user sees them in the drop-down list.</span></span> <span data-ttu-id="261a6-125">若要變更某個項目在清單中的順序，請按一下 [值]  文字方塊來選取此項目，然後使用向上箭頭和向下箭頭按鈕，將此項目移到清單中的更高或更低位置。</span><span class="sxs-lookup"><span data-stu-id="261a6-125">To change the order of an item in the list, click the **Value** text box to select the item, and then use the up and down arrow buttons to move the item higher or lower in the list.</span></span>  
  
    -   <span data-ttu-id="261a6-126">若要提供現有資料集名稱 (該資料集會擷取值)，請按一下 [從查詢取得值]  。</span><span class="sxs-lookup"><span data-stu-id="261a6-126">To provide the name of an existing dataset that retrieves the values, click **Get values from a query**.</span></span> <span data-ttu-id="261a6-127">在 **[資料集]** 中，選擇此資料集的名稱。</span><span class="sxs-lookup"><span data-stu-id="261a6-127">In **Dataset**, choose the name of the dataset.</span></span>  
  
         <span data-ttu-id="261a6-128">在 **[值欄位]** 中，選擇可提供參數值的欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="261a6-128">In **Value field**, choose the name of the field that provides parameter values.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-remove-the-default-values-for-a-report-parameter"></a><span data-ttu-id="261a6-129">移除報表參數的預設值</span><span class="sxs-lookup"><span data-stu-id="261a6-129">To remove the default values for a report parameter</span></span>  
  
1.  <span data-ttu-id="261a6-130">在 [報表資料] 窗格中，展開 [參數]  節點。</span><span class="sxs-lookup"><span data-stu-id="261a6-130">In the Report Data pane, expand the **Parameters** node.</span></span> <span data-ttu-id="261a6-131">以滑鼠右鍵按一下此參數，然後按一下 [編輯]  。</span><span class="sxs-lookup"><span data-stu-id="261a6-131">Right-click the parameter and click **Edit**.</span></span> <span data-ttu-id="261a6-132">**[報表參數屬性]** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="261a6-132">The **Report Parameter Properties** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="261a6-133">按一下 **[預設值]** 。</span><span class="sxs-lookup"><span data-stu-id="261a6-133">Click **Default Values**.</span></span>  
  
3.  <span data-ttu-id="261a6-134">在 [選取下列其中一個選項]  中，按一下 [沒有預設值]  。</span><span class="sxs-lookup"><span data-stu-id="261a6-134">In **Select from one of the following options**, click **No default value**.</span></span>  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="261a6-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="261a6-135">See Also</span></span>  
 <span data-ttu-id="261a6-136">[報表參數 &#40;報表產生器和報表設計師&#41;](report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="261a6-136">[Report Parameters &#40;Report Builder and Report Designer&#41;](report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="261a6-137">[將串聯參數加入至報表 &#40;報表產生器和 SSRS&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="261a6-137">[Add Cascading Parameters to a Report &#40;Report Builder and SSRS&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="261a6-138">[教學課程：將參數新增至報表 &#40;報表產生器&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="261a6-138">[Tutorial: Add a Parameter to Your Report &#40;Report Builder&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md) </span></span>  
 <span data-ttu-id="261a6-139">[新增資料集篩選、資料區篩選和群組篩選 &#40;報表產生器及 SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span><span class="sxs-lookup"><span data-stu-id="261a6-139">[Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span></span>  
 <span data-ttu-id="261a6-140">[參數集合參考 &#40;報表產生器及 SSRS&#41;](built-in-collections-parameters-collection-references-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="261a6-140">[Parameters Collection References &#40;Report Builder and SSRS&#41;](built-in-collections-parameters-collection-references-report-builder.md) </span></span>  
 <span data-ttu-id="261a6-141">[變更報表參數的順序 &#40;報表產生器及 SSRS&#41;](change-the-order-of-a-report-parameter-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="261a6-141">[Change the Order of a Report Parameter &#40;Report Builder and SSRS&#41;](change-the-order-of-a-report-parameter-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="261a6-142">[加入、變更或刪除報表參數 &#40;報表產生器及 SSRS&#41;](add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="261a6-142">[Add, Change, or Delete a Report Parameter &#40;Report Builder and SSRS&#41;](add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="261a6-143">運算式 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="261a6-143">Expressions &#40;Report Builder and SSRS&#41;</span></span>](expressions-report-builder-and-ssrs.md)  
  
  