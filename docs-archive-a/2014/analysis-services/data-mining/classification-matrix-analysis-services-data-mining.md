---
title: 分類矩陣 (Analysis Services-資料採礦) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models [Analysis Services], validating
- validating data mining models
- viewing mining accuracy
- displaying mining accuracy
- confusion matrix [data mining]
- classification matrix [Analysis Services]
- accuracy testing [data mining]
ms.assetid: 5c12f202-2ed9-41fa-bee2-0f7ab3ff058a
author: minewiskan
ms.author: owend
ms.openlocfilehash: d880eb48e249d5e26611765fea7c9bd3b3e2216f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598682"
---
# <a name="classification-matrix-analysis-services---data-mining"></a><span data-ttu-id="f55f9-102">分類矩陣 (Analysis Services - 資料採礦)</span><span class="sxs-lookup"><span data-stu-id="f55f9-102">Classification Matrix (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="f55f9-103">「分類矩陣」\*\* 會透過判斷預測值是否符合實際值，將模型中的所有案例分類到不同的類別目錄。</span><span class="sxs-lookup"><span data-stu-id="f55f9-103">A *classification matrix* sorts all cases from the model into categories, by determining whether the predicted value matched the actual value.</span></span> <span data-ttu-id="f55f9-104">每個類別目錄中的所有案例都會計算在內，而且總數會顯示在矩陣中。</span><span class="sxs-lookup"><span data-stu-id="f55f9-104">All the cases in each category are then counted, and the totals are displayed in the matrix.</span></span> <span data-ttu-id="f55f9-105">分類矩陣是統計模型評估的標準工具，有時稱為「混淆矩陣」\*\*。</span><span class="sxs-lookup"><span data-stu-id="f55f9-105">The classification matrix is a standard tool for evaluation of statistical models and is sometimes referred to as a *confusion matrix*.</span></span>  
  
 <span data-ttu-id="f55f9-106">您選擇 [分類矩陣]\*\*\*\* 選項時所建立的圖表，會比較實際值與您指定之每個預測狀態的預測值。</span><span class="sxs-lookup"><span data-stu-id="f55f9-106">The chart that is created when you choose the **Classification Matrix** option compares actual to predicted values for each predicted state that you specify.</span></span> <span data-ttu-id="f55f9-107">矩陣的資料列代表模型的預測值，而資料行則代表實際值。</span><span class="sxs-lookup"><span data-stu-id="f55f9-107">The rows in the matrix represent the predicted values for the model, whereas the columns represent the actual values.</span></span> <span data-ttu-id="f55f9-108">用於分析的類別目錄包括「誤判」**、「真肯定」**、「誤否定」\*\* 和「真否定」\*\*</span><span class="sxs-lookup"><span data-stu-id="f55f9-108">The categories used in analysis are *false positive*, *true positive*, *false negative*, and *true negative*</span></span>  
  
 <span data-ttu-id="f55f9-109">分類矩陣是評估預測結果的重要工具，因為此工具可讓您容易了解及說明錯誤預測的影響。</span><span class="sxs-lookup"><span data-stu-id="f55f9-109">A classification matrix is an important tool for assessing the results of prediction because it makes it easy to understand and account for the effects of wrong predictions.</span></span> <span data-ttu-id="f55f9-110">透過檢視此矩陣之每個資料格中的數量和百分比，您可以快速查看模型正確預測的頻率。</span><span class="sxs-lookup"><span data-stu-id="f55f9-110">By viewing the amount and percentages in each cell of this matrix, you can quickly see how often the model predicted accurately.</span></span>  
  
 <span data-ttu-id="f55f9-111">本節將說明如何建立分類矩陣及如何解譯結果。</span><span class="sxs-lookup"><span data-stu-id="f55f9-111">This section explains how to create a classification matrix and how to interpret the results.</span></span>  
  
## <a name="understanding-the-classification-matrix"></a><span data-ttu-id="f55f9-112">了解分類矩陣</span><span class="sxs-lookup"><span data-stu-id="f55f9-112">Understanding the Classification Matrix</span></span>  
 <span data-ttu-id="f55f9-113">將您建立的模型視為資料採礦基本教學課程的一部分。</span><span class="sxs-lookup"><span data-stu-id="f55f9-113">Consider the model that you created as part of the Basic Data Mining Tutorial.</span></span> <span data-ttu-id="f55f9-114">[TM_DecisionTree] 模型可用來協助建立目標郵寄促銷活動，並可用來預測哪些客戶最有可能購買自行車。</span><span class="sxs-lookup"><span data-stu-id="f55f9-114">The [TM_DecisionTree] model is used to help create a targeted mailing campaign, and can be used to predict which customers are most likely to buy a bike.</span></span> <span data-ttu-id="f55f9-115">若要測試此模型的預期效用，您可以使用內含已知 [Bike Buyer] 結果屬性值的資料集。</span><span class="sxs-lookup"><span data-stu-id="f55f9-115">To test this expected usefulness of this model, you use a data set for which the values of the outcome attribute, [Bike Buyer], are already known.</span></span> <span data-ttu-id="f55f9-116">一般來說，您會使用當您建立用於定型此模型的採礦結構時所擱置在一旁的測試資料集。</span><span class="sxs-lookup"><span data-stu-id="f55f9-116">Typically, you would use the testing data set that you set aside when you created the mining structure that is used for training the model.</span></span>  
  
 <span data-ttu-id="f55f9-117">只有兩種可能的結果：[是] (客戶可能購買自行車) 及 [否] (客戶可能不購買自行車)。</span><span class="sxs-lookup"><span data-stu-id="f55f9-117">There are only two possible outcomes: yes (the customer is likely to buy a bike), and no (the customer will likely not purchase a bike).</span></span> <span data-ttu-id="f55f9-118">因此，產生的分類矩陣是比較簡單的。</span><span class="sxs-lookup"><span data-stu-id="f55f9-118">Therefore, the resulting classification matrix is relatively simple.</span></span>  
  
## <a name="interpreting-the-results"></a><span data-ttu-id="f55f9-119">解譯結果</span><span class="sxs-lookup"><span data-stu-id="f55f9-119">Interpreting the Results</span></span>  
 <span data-ttu-id="f55f9-120">下表顯示 TM_DecisionTree 模型的分類矩陣。</span><span class="sxs-lookup"><span data-stu-id="f55f9-120">The following table shows the classification matrix for the TM_DecisionTree model.</span></span> <span data-ttu-id="f55f9-121">請記住，此可預測的屬性若為 0，則表示 [否]；若為 1，則表示 [是]。</span><span class="sxs-lookup"><span data-stu-id="f55f9-121">Remember that for this predictable attribute, 0 means No and 1 means Yes.</span></span>  
  
|<span data-ttu-id="f55f9-122">預測的</span><span class="sxs-lookup"><span data-stu-id="f55f9-122">Predicted</span></span>|<span data-ttu-id="f55f9-123">0 (實際值)</span><span class="sxs-lookup"><span data-stu-id="f55f9-123">0 (Actual)</span></span>|<span data-ttu-id="f55f9-124">1 (實際值)</span><span class="sxs-lookup"><span data-stu-id="f55f9-124">1 (Actual)</span></span>|  
|---------------|------------------|------------------|  
|<span data-ttu-id="f55f9-125">0</span><span class="sxs-lookup"><span data-stu-id="f55f9-125">0</span></span>|<span data-ttu-id="f55f9-126">362</span><span class="sxs-lookup"><span data-stu-id="f55f9-126">362</span></span>|<span data-ttu-id="f55f9-127">144</span><span class="sxs-lookup"><span data-stu-id="f55f9-127">144</span></span>|  
|<span data-ttu-id="f55f9-128">1</span><span class="sxs-lookup"><span data-stu-id="f55f9-128">1</span></span>|<span data-ttu-id="f55f9-129">121</span><span class="sxs-lookup"><span data-stu-id="f55f9-129">121</span></span>|<span data-ttu-id="f55f9-130">373</span><span class="sxs-lookup"><span data-stu-id="f55f9-130">373</span></span>|  
  
 <span data-ttu-id="f55f9-131">第一個結果資料格包含 362 的值，表示值 0 的「真肯定」\*\* 數目。</span><span class="sxs-lookup"><span data-stu-id="f55f9-131">The first result cell, which contains the value 362, indicates the number of *true positives* for the value 0.</span></span> <span data-ttu-id="f55f9-132">由於 0 表示客戶未購買自行車，所以這個統計資料告訴您，此模型在 362 個案例中預測出非自行車買主的正確值。</span><span class="sxs-lookup"><span data-stu-id="f55f9-132">Because 0 indicates that the customer did not purchase a bike, this statistic tells you that model predicted the correct value for non bike-buyers in 362 cases.</span></span>  
  
 <span data-ttu-id="f55f9-133">該資料格正下方的資料格包含 121 的值，也就告訴您「誤判」\*\* 的數目，或是此模型預測某個人會購買自行車，但實際上卻沒有的次數。</span><span class="sxs-lookup"><span data-stu-id="f55f9-133">The cell directly underneath that one, which contains the value 121, tells you the number of *false positives*, or how many times the model predicted that someone would buy a bike when actually they did not.</span></span>  
  
 <span data-ttu-id="f55f9-134">包含 144 值的資料格，表示值 1 的「誤判」\*\* 數目。</span><span class="sxs-lookup"><span data-stu-id="f55f9-134">The cell that contains the value 144 indicates the number of *false positives* for the value 1.</span></span> <span data-ttu-id="f55f9-135">由於 1 表示客戶已購買自行車，所以這個統計資料告訴您，此模型在 144 個案例中預測出某個人不會購買自行車，但實際上卻有購買的次數。</span><span class="sxs-lookup"><span data-stu-id="f55f9-135">Because 1 means that the customer did purchase a bike, this statistic tells you that in 144 cases, the model predicted someone would not buy a bike when in fact they did.</span></span>  
  
 <span data-ttu-id="f55f9-136">最後，包含 373 值的資料格，表示目標值 1 的「真肯定」數目。</span><span class="sxs-lookup"><span data-stu-id="f55f9-136">Finally, the cell that contains the value 373 indicates the number of true positives for the target value of 1.</span></span> <span data-ttu-id="f55f9-137">換句話說，此模型在 373 個案例中，正確預測出某個人會購買自行車。</span><span class="sxs-lookup"><span data-stu-id="f55f9-137">In other words, in 373 cases the model correctly predicted that someone would buy a bike.</span></span>  
  
 <span data-ttu-id="f55f9-138">藉由彙總對角線上相鄰之資料格中的值，就可以判斷此模型的整體精確度。</span><span class="sxs-lookup"><span data-stu-id="f55f9-138">By summing the values in cells that are diagonally adjacent, you can determine the overall accuracy of the model.</span></span> <span data-ttu-id="f55f9-139">一條對角線會告訴您正確預測的總數，而其他對角線則告訴您錯誤預測的總數。</span><span class="sxs-lookup"><span data-stu-id="f55f9-139">One diagonal tells you the total number of accurate predictions, and the other diagonal tells you the total number of erroneous predictions.</span></span>  
  
### <a name="using-multiple-predictable-values"></a><span data-ttu-id="f55f9-140">使用多個可預測的值</span><span class="sxs-lookup"><span data-stu-id="f55f9-140">Using Multiple Predictable Values</span></span>  
 <span data-ttu-id="f55f9-141">[Bike Buyer] 案例特別容易解譯，因為只有兩個可能的值。</span><span class="sxs-lookup"><span data-stu-id="f55f9-141">The [Bike Buyer] case is especially easy to interpret because there are only two possible values.</span></span> <span data-ttu-id="f55f9-142">當可預測屬性有多個可能的值時，分類矩陣會針對每一個可能的實際值加入新的資料行，然後針對每一個預測值計算相符的數目。</span><span class="sxs-lookup"><span data-stu-id="f55f9-142">When the predictable attribute has multiple possible values, the classification matrix adds a new column for each possible actual value and then counts the number of matches for each predicted value.</span></span> <span data-ttu-id="f55f9-143">下表顯示不同模型上的結果，其中有三個值 (0, 1, 2) 是可能的值。</span><span class="sxs-lookup"><span data-stu-id="f55f9-143">The following table shows the results on a different model, where three values (0, 1, 2) are possible.</span></span>  
  
|<span data-ttu-id="f55f9-144">預測的</span><span class="sxs-lookup"><span data-stu-id="f55f9-144">Predicted</span></span>|<span data-ttu-id="f55f9-145">0 (實際值)</span><span class="sxs-lookup"><span data-stu-id="f55f9-145">0 (Actual)</span></span>|<span data-ttu-id="f55f9-146">1 (實際值)</span><span class="sxs-lookup"><span data-stu-id="f55f9-146">1 (Actual)</span></span>|<span data-ttu-id="f55f9-147">2 (實際值)</span><span class="sxs-lookup"><span data-stu-id="f55f9-147">2 (Actual)</span></span>|  
|---------------|------------------|------------------|------------------|  
|<span data-ttu-id="f55f9-148">0</span><span class="sxs-lookup"><span data-stu-id="f55f9-148">0</span></span>|<span data-ttu-id="f55f9-149">111</span><span class="sxs-lookup"><span data-stu-id="f55f9-149">111</span></span>|<span data-ttu-id="f55f9-150">3</span><span class="sxs-lookup"><span data-stu-id="f55f9-150">3</span></span>|<span data-ttu-id="f55f9-151">5</span><span class="sxs-lookup"><span data-stu-id="f55f9-151">5</span></span>|  
|<span data-ttu-id="f55f9-152">1</span><span class="sxs-lookup"><span data-stu-id="f55f9-152">1</span></span>|<span data-ttu-id="f55f9-153">2</span><span class="sxs-lookup"><span data-stu-id="f55f9-153">2</span></span>|<span data-ttu-id="f55f9-154">123</span><span class="sxs-lookup"><span data-stu-id="f55f9-154">123</span></span>|<span data-ttu-id="f55f9-155">17</span><span class="sxs-lookup"><span data-stu-id="f55f9-155">17</span></span>|  
|<span data-ttu-id="f55f9-156">2</span><span class="sxs-lookup"><span data-stu-id="f55f9-156">2</span></span>|<span data-ttu-id="f55f9-157">19</span><span class="sxs-lookup"><span data-stu-id="f55f9-157">19</span></span>|<span data-ttu-id="f55f9-158">0</span><span class="sxs-lookup"><span data-stu-id="f55f9-158">0</span></span>|<span data-ttu-id="f55f9-159">20</span><span class="sxs-lookup"><span data-stu-id="f55f9-159">20</span></span>|  
  
 <span data-ttu-id="f55f9-160">雖然加入多個資料行會讓報表看起來更為複雜，但是當您想要評估做出錯誤預測的累計成本時，其他詳細資料可能會非常實用。</span><span class="sxs-lookup"><span data-stu-id="f55f9-160">Although the addition of more columns makes the report look more complex, the additional detail can be very useful when you want to assess the cumulative cost of making the wrong prediction.</span></span> <span data-ttu-id="f55f9-161">若要建立對角線上的總和或是比較不同資料列組合的結果，您可以按一下 [分類矩陣]\*\*\*\* 索引標籤上提供的 [複製]\*\*\*\* 按鈕，並將報表貼到 Excel。</span><span class="sxs-lookup"><span data-stu-id="f55f9-161">To create sums on the diagonals or to compare the results for different combinations of rows, you can click the **Copy** button provided in the **Classification Matrix** tab and paste the report into Excel.</span></span> <span data-ttu-id="f55f9-162">或者，您可以使用類似適用於 Excel 的資料採礦用戶端的用戶端 (它支援 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 和更新版本)，直接在 Excel 中建立包含計數和百分比的分類報表。</span><span class="sxs-lookup"><span data-stu-id="f55f9-162">Alternatively, you can use a client such as the Data Mining Client for Excel, which supports [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions, to create a classification report directly in Excel that includes both counts and percentages.</span></span> <span data-ttu-id="f55f9-163">如需詳細資訊，請參閱 [SQL Server Data Mining](https://go.microsoft.com/fwlink/?LinkID=77733)(SQL Server 資料採礦)。</span><span class="sxs-lookup"><span data-stu-id="f55f9-163">For more information, see [SQL Server Data Mining](https://go.microsoft.com/fwlink/?LinkID=77733).</span></span>  
  
## <a name="restrictions-on-the-classification-matrix"></a><span data-ttu-id="f55f9-164">分類矩陣的限制</span><span class="sxs-lookup"><span data-stu-id="f55f9-164">Restrictions on the Classification Matrix</span></span>  
 <span data-ttu-id="f55f9-165">分類矩陣只能搭配離散的可預測屬性一起使用。</span><span class="sxs-lookup"><span data-stu-id="f55f9-165">A classification matrix can be used only with discrete predictable attributes.</span></span>  
  
 <span data-ttu-id="f55f9-166">當您在 [採礦精確度圖表]\*\*\*\* 設計師的 [輸入選擇]\*\*\*\* 索引標籤上選取模型時，雖然可以加入多個模型，但是 [分類矩陣]\*\*\*\* 索引標籤會顯示每個模型的個別矩陣。</span><span class="sxs-lookup"><span data-stu-id="f55f9-166">Although you can add multiple models when selecting models on the **Input Selection** tab of the **Mining Accuracy Chart** designer, the **Classification Matrix** tab will display a separate matrix for each model.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="f55f9-167">相關內容</span><span class="sxs-lookup"><span data-stu-id="f55f9-167">Related Content</span></span>  
 <span data-ttu-id="f55f9-168">下列主題包含您可以如何建立及使用分類矩陣及其他圖表的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="f55f9-168">The following topics contain more information about how you can build and use classification matrices and other charts.</span></span>  
  
|<span data-ttu-id="f55f9-169">主題</span><span class="sxs-lookup"><span data-stu-id="f55f9-169">Topics</span></span>|<span data-ttu-id="f55f9-170">連結</span><span class="sxs-lookup"><span data-stu-id="f55f9-170">Links</span></span>|  
|------------|-----------|  
|<span data-ttu-id="f55f9-171">提供如何為此目標郵寄模型建立增益圖的逐步解說。</span><span class="sxs-lookup"><span data-stu-id="f55f9-171">Provides a walkthrough of how to create a lift chart for the Targeted Mailing model.</span></span>|[<span data-ttu-id="f55f9-172">資料採礦基本教學課程</span><span class="sxs-lookup"><span data-stu-id="f55f9-172">Basic Data Mining Tutorial</span></span>](../../tutorials/basic-data-mining-tutorial.md)<br /><br /> [<span data-ttu-id="f55f9-173">使用增益圖測試精確度 &#40;基本資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="f55f9-173">Testing Accuracy with Lift Charts &#40;Basic Data Mining Tutorial&#41;</span></span>](../../tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)|  
|<span data-ttu-id="f55f9-174">說明相關的圖表類型。</span><span class="sxs-lookup"><span data-stu-id="f55f9-174">Explains related chart types.</span></span>|[<span data-ttu-id="f55f9-175">增益圖 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="f55f9-175">Lift Chart &#40;Analysis Services - Data Mining&#41;</span></span>](lift-chart-analysis-services-data-mining.md)<br /><br /> [<span data-ttu-id="f55f9-176">收益圖 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="f55f9-176">Profit Chart &#40;Analysis Services - Data Mining&#41;</span></span>](profit-chart-analysis-services-data-mining.md)<br /><br /> [<span data-ttu-id="f55f9-177">散佈圖 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="f55f9-177">Scatter Plot &#40;Analysis Services - Data Mining&#41;</span></span>](scatter-plot-analysis-services-data-mining.md)|  
|<span data-ttu-id="f55f9-178">描述採礦模型和採礦結構的交叉驗證用法。</span><span class="sxs-lookup"><span data-stu-id="f55f9-178">Describes uses of cross-validation for mining models and mining structures.</span></span>|[<span data-ttu-id="f55f9-179">交叉驗證 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="f55f9-179">Cross-Validation &#40;Analysis Services - Data Mining&#41;</span></span>](cross-validation-analysis-services-data-mining.md)|  
|<span data-ttu-id="f55f9-180">描述建立增益圖及其他精確度圖表的步驟。</span><span class="sxs-lookup"><span data-stu-id="f55f9-180">Describes steps for creating lift charts and other accuracy charts.</span></span>|[<span data-ttu-id="f55f9-181">測試及驗證工作與操作方法 &#40;資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="f55f9-181">Testing and Validation Tasks and How-tos &#40;Data Mining&#41;</span></span>](testing-and-validation-tasks-and-how-tos-data-mining.md)|  
  
## <a name="see-also"></a><span data-ttu-id="f55f9-182">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f55f9-182">See Also</span></span>  
 [<span data-ttu-id="f55f9-183">測試及驗證 &#40;資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="f55f9-183">Testing and Validation &#40;Data Mining&#41;</span></span>](testing-and-validation-data-mining.md)  
  
  