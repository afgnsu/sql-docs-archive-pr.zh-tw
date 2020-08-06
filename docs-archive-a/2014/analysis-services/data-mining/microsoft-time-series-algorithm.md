---
title: Microsoft 時間序列演算法 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- ARTXP
- time series algorithms [Analysis Services]
- ARIMA
- time series [Analysis Services]
- algorithms [data mining]
- cross predictions
- series [Analysis Services]
- regression algorithms [Analysis Services]
ms.assetid: 642297cc-f32a-499b-b26e-fdc7ee24361e
author: minewiskan
ms.author: owend
ms.openlocfilehash: d840d581fe4dba1ce9d65dfef6878a1e5a697864
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594274"
---
# <a name="microsoft-time-series-algorithm"></a><span data-ttu-id="28ee3-102">Microsoft 時間序列演算法</span><span class="sxs-lookup"><span data-stu-id="28ee3-102">Microsoft Time Series Algorithm</span></span>
  <span data-ttu-id="28ee3-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)]時間序列演算法提供的回歸演算法，已針對連續值的預測（例如一段時間的產品銷售）進行優化。</span><span class="sxs-lookup"><span data-stu-id="28ee3-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Time Series algorithm provides regression algorithms that are optimized for the forecasting of continuous values, such as product sales, over time.</span></span> <span data-ttu-id="28ee3-104">雖然其他 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 演算法 (如決策樹) 需要含有新資訊的其他資料行當做輸入來預測趨勢，但是時間序列模型則不需要。</span><span class="sxs-lookup"><span data-stu-id="28ee3-104">Whereas other [!INCLUDE[msCoName](../../includes/msconame-md.md)] algorithms, such as decision trees, require additional columns of new information as input to predict a trend, a time series model does not.</span></span> <span data-ttu-id="28ee3-105">時間序列模型可以只根據用於建立此模型的原始資料集來預測趨勢。</span><span class="sxs-lookup"><span data-stu-id="28ee3-105">A time series model can predict trends based only on the original dataset that is used to create the model.</span></span> <span data-ttu-id="28ee3-106">當您做出預測並將新的資料自動納入趨勢分析時，也可以將新的資料加入此模型中。</span><span class="sxs-lookup"><span data-stu-id="28ee3-106">You can also add new data to the model when you make a prediction and automatically incorporate the new data in the trend analysis.</span></span>  
  
 <span data-ttu-id="28ee3-107">下列圖表顯示一個典型模型，其中會預測一段時間內在四個不同銷售區域的產品銷售。</span><span class="sxs-lookup"><span data-stu-id="28ee3-107">The following diagram shows a typical model for forecasting sales of a product in four different sales regions over time.</span></span> <span data-ttu-id="28ee3-108">此圖表中顯示的模型會將每一個區域的銷售繪製成紅色、黃色、紫色和藍色的線條。</span><span class="sxs-lookup"><span data-stu-id="28ee3-108">The model that is shown in the diagram shows sales for each region plotted as red, yellow, purple, and blue lines.</span></span> <span data-ttu-id="28ee3-109">每個區域的線條有兩個部分：</span><span class="sxs-lookup"><span data-stu-id="28ee3-109">The line for each region has two parts:</span></span>  
  
-   <span data-ttu-id="28ee3-110">歷程記錄資訊會出現在垂直線的左方，並表示此演算法用於建立模型的資料。</span><span class="sxs-lookup"><span data-stu-id="28ee3-110">Historical information appears to the left of the vertical line and represents the data that the algorithm uses to create the model.</span></span>  
  
-   <span data-ttu-id="28ee3-111">預測的資訊會出現在垂直線的右方，並表示此模型所做出的預測。</span><span class="sxs-lookup"><span data-stu-id="28ee3-111">Predicted information appears to the right of the vertical line and represents the forecast that the model makes.</span></span>  
  
 <span data-ttu-id="28ee3-112">來源資料和預測資料的組合稱為「序列」\*\*。</span><span class="sxs-lookup"><span data-stu-id="28ee3-112">The combination of the source data and the prediction data is called a *series*.</span></span>  
  
 <span data-ttu-id="28ee3-113">![時間序列的範例](../media/time-series.gif "時間序列的範例")</span><span class="sxs-lookup"><span data-stu-id="28ee3-113">![An example of a time series](../media/time-series.gif "An example of a time series")</span></span>  
  
 <span data-ttu-id="28ee3-114">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 時間序列演算法的重要功能之一是可以執行交叉預測。</span><span class="sxs-lookup"><span data-stu-id="28ee3-114">An important feature of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Time Series algorithm is that it can perform cross prediction.</span></span> <span data-ttu-id="28ee3-115">如果您以兩個分開但相關的序列來定型演算法，則可以使用產生的模型依據其他序列的行為來預測一個序列的結果。</span><span class="sxs-lookup"><span data-stu-id="28ee3-115">If you train the algorithm with two separate, but related, series, you can use the resulting model to predict the outcome of one series based on the behavior of the other series.</span></span> <span data-ttu-id="28ee3-116">例如，一個產品的已知銷售量會影響另一個產品的預測銷售量。</span><span class="sxs-lookup"><span data-stu-id="28ee3-116">For example, the observed sales of one product can influence the forecasted sales of another product.</span></span> <span data-ttu-id="28ee3-117">交叉預測對於建立可套用至多個序列的一般模型也很有用處。</span><span class="sxs-lookup"><span data-stu-id="28ee3-117">Cross prediction is also useful for creating a general model that can be applied to multiple series.</span></span> <span data-ttu-id="28ee3-118">例如，特定區域的預測會因為此序列缺少品質良好的資料而造成不穩定的情形。</span><span class="sxs-lookup"><span data-stu-id="28ee3-118">For example, the predictions for a particular region are unstable because the series lacks good quality data.</span></span> <span data-ttu-id="28ee3-119">您可以根據所有四個區域的平均值來定型一般模型，然後將此模型套用至個別序列，以針對每一個區域建立更穩定的預測。</span><span class="sxs-lookup"><span data-stu-id="28ee3-119">You could train a general model on an average of all four regions, and then apply the model to the individual series to create more stable predictions for each region.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28ee3-120">範例</span><span class="sxs-lookup"><span data-stu-id="28ee3-120">Example</span></span>  
 <span data-ttu-id="28ee3-121">[!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] 的管理團隊想要預測來年的每月腳踏車銷售量。</span><span class="sxs-lookup"><span data-stu-id="28ee3-121">The management team at [!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] wants to predict monthly bicycle sales for the coming year.</span></span> <span data-ttu-id="28ee3-122">此公司特別想要知道某一款自行車的銷售是否可用於預測另一款的銷售。</span><span class="sxs-lookup"><span data-stu-id="28ee3-122">The company is especially interested in whether the sale of one bike model can be used to predict the sale of another model.</span></span> <span data-ttu-id="28ee3-123">公司針對過去這 3 年的記錄資料使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 時間序列演算法，可以產生資料採礦模型來預測未來的腳踏車銷售量。</span><span class="sxs-lookup"><span data-stu-id="28ee3-123">By using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Time Series algorithm on historical data from the past three years, the company can produce a data mining model that forecasts future bike sales.</span></span> <span data-ttu-id="28ee3-124">另外，公司可以執行交叉預測，以了解個別腳踏車款的銷售趨勢是否彼此相關。</span><span class="sxs-lookup"><span data-stu-id="28ee3-124">Additionally, the company can perform cross predictions to see whether the sales trends of individual bike models are related.</span></span>  
  
 <span data-ttu-id="28ee3-125">此公司在每一季都打算以最近的銷售資料來更新此模型，並將其預測更新為模型的最近趨勢。</span><span class="sxs-lookup"><span data-stu-id="28ee3-125">Each quarter, the company plans to update the model with recent sales data and update their predictions to model recent trends.</span></span> <span data-ttu-id="28ee3-126">若要針對未能正確或一致更新銷售資料的商店做出更正，將會建立一般預測模型，並使用該模型來建立所有區域的預測。</span><span class="sxs-lookup"><span data-stu-id="28ee3-126">To correct for stores that do not accurately or consistently update sales data, they will create a general prediction model, and use that to create predictions for all regions.</span></span>  
  
## <a name="how-the-algorithm-works"></a><span data-ttu-id="28ee3-127">演算法的運作方式</span><span class="sxs-lookup"><span data-stu-id="28ee3-127">How the Algorithm Works</span></span>  
 <span data-ttu-id="28ee3-128">在中 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ， [!INCLUDE[msCoName](../../includes/msconame-md.md)] 時間序列演算法使用單一演算法 ARTXP。</span><span class="sxs-lookup"><span data-stu-id="28ee3-128">In [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Time Series algorithm used a single algorithm, ARTXP.</span></span> <span data-ttu-id="28ee3-129">ARTXP 演算法已針對短期預測進行優化，因此會預測數列中的下一個可能值。</span><span class="sxs-lookup"><span data-stu-id="28ee3-129">The ARTXP algorithm was optimized for short-term predictions, and therefore, predicted the next likely value in a series.</span></span> <span data-ttu-id="28ee3-130">從開始 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ， [!INCLUDE[msCoName](../../includes/msconame-md.md)] 時間序列演算法會使用 ARTXP 演算法和第二個演算法 ARIMA。</span><span class="sxs-lookup"><span data-stu-id="28ee3-130">Beginning in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Time Series algorithm uses both the ARTXP algorithm and a second algorithm, ARIMA.</span></span> <span data-ttu-id="28ee3-131">ARIMA 演算法已針對長期預測而最佳化。</span><span class="sxs-lookup"><span data-stu-id="28ee3-131">The ARIMA algorithm is optimized for long-term prediction.</span></span> <span data-ttu-id="28ee3-132">如需 ARTXP 和 ARIMA 演算法實作的詳細說明，請參閱 [Microsoft 時間序列演算法技術參考](microsoft-time-series-algorithm-technical-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="28ee3-132">For a detailed explanation about the implementation of the ARTXP and ARIMA algorithms, see [Microsoft Time Series Algorithm Technical Reference](microsoft-time-series-algorithm-technical-reference.md).</span></span>  
  
 <span data-ttu-id="28ee3-133">依預設， [!INCLUDE[msCoName](../../includes/msconame-md.md)] 時間序列演算法在分析模式及作出預測時，會混合使用這些演算法。</span><span class="sxs-lookup"><span data-stu-id="28ee3-133">By default, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Time Series algorithm uses a mix of the algorithms when it analyzes patterns and making predictions.</span></span> <span data-ttu-id="28ee3-134">此演算法會在相同的資料上定型兩個不同的模型：一個模型使用 ARTXP 演算法，另一個模型則使用 ARIMA 演算法。</span><span class="sxs-lookup"><span data-stu-id="28ee3-134">The algorithm trains two separate models on the same data: one model uses the ARTXP algorithm and one model uses the ARIMA algorithm.</span></span> <span data-ttu-id="28ee3-135">然後此演算法會混合這兩個模型的結果，以針對變動數目的時間配量產生最佳預測結果。</span><span class="sxs-lookup"><span data-stu-id="28ee3-135">The algorithm then blends the results of the two models to yield the best prediction over a variable number of time slices.</span></span> <span data-ttu-id="28ee3-136">因為 ARTXP 最適合用於短期預測，所以在一系列預測的開始會有較重的加權。</span><span class="sxs-lookup"><span data-stu-id="28ee3-136">Because ARTXP is best for short-term predictions, it is weighted more heavily at the beginning of a series of predictions.</span></span> <span data-ttu-id="28ee3-137">不過，隨著預測的時間配量進入未來，ARIMA 會有更重的加權。</span><span class="sxs-lookup"><span data-stu-id="28ee3-137">However, as the time slices that you are predicting move further into the future, ARIMA is weighted more heavily.</span></span>  
  
 <span data-ttu-id="28ee3-138">您也可以控制演算法的組合，以選擇偏好時間序列中的短期或長期預測。</span><span class="sxs-lookup"><span data-stu-id="28ee3-138">You can also control the mix of algorithms to favor either short- or long-term prediction in the times series.</span></span> <span data-ttu-id="28ee3-139">從 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Standard 開始，您可以指定 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 時間序列演算法使用下列其中一項設定：</span><span class="sxs-lookup"><span data-stu-id="28ee3-139">Beginning in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] Standard, you can specify that the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Time Series algorithm use one of the following settings:</span></span>  
  
-   <span data-ttu-id="28ee3-140">短期預測中只使用 ARTXP。</span><span class="sxs-lookup"><span data-stu-id="28ee3-140">Use only ARTXP for short-term prediction.</span></span>  
  
-   <span data-ttu-id="28ee3-141">長期預測中只使用 ARIMA。</span><span class="sxs-lookup"><span data-stu-id="28ee3-141">Use only ARIMA for long-term prediction.</span></span>  
  
-   <span data-ttu-id="28ee3-142">使用預設的兩種演算法混用。</span><span class="sxs-lookup"><span data-stu-id="28ee3-142">Use the default blending of the two algorithms.</span></span>  
  
 <span data-ttu-id="28ee3-143">從開始 [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] ，您可以自訂 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 時間序列演算法如何混合模型以進行預測。</span><span class="sxs-lookup"><span data-stu-id="28ee3-143">Beginning in [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)], you can customize how the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Time Series algorithm blends the models for prediction.</span></span> <span data-ttu-id="28ee3-144">當您使用混合模型時， [!INCLUDE[msCoName](../../includes/msconame-md.md)] 時間序列演算法會以下列方式來混合這兩種演算法：</span><span class="sxs-lookup"><span data-stu-id="28ee3-144">When you use a mixed model, the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Time Series algorithm blends the two algorithms in the following way:</span></span>  
  
-   <span data-ttu-id="28ee3-145">在做出最初的幾個預測時，一定只使用 ARTXP。</span><span class="sxs-lookup"><span data-stu-id="28ee3-145">Only ARTXP is always used for making the first couple of predictions.</span></span>  
  
-   <span data-ttu-id="28ee3-146">在做出最初的幾個預測之後，會使用 ARIMA 和 ARTXP 的組合。</span><span class="sxs-lookup"><span data-stu-id="28ee3-146">After the first couple of predictions, a combination of ARIMA and ARTXP is used.</span></span>  
  
-   <span data-ttu-id="28ee3-147">當預測步驟的數目增加時，預測會更依賴 ARIMA，直到 ARTXP 不再使用為止。</span><span class="sxs-lookup"><span data-stu-id="28ee3-147">As the number of prediction steps increases, predictions rely more heavily on ARIMA until ARTXP is no longer used.</span></span>  
  
-   <span data-ttu-id="28ee3-148">您可控制混合點 (也就是 ARTXP 加權減少的比率)，而且可設定 PREDICTION_SMOOTHING 參數來增加 ARIMA 的加權。</span><span class="sxs-lookup"><span data-stu-id="28ee3-148">You control the mixing point, the rate at which the weight of ARTXP is decreased, and the weight of ARIMA is increased by setting the PREDICTION_SMOOTHING parameter.</span></span>  
  
 <span data-ttu-id="28ee3-149">這兩個演算法都可以在多個層級上偵測資料中的季節性。</span><span class="sxs-lookup"><span data-stu-id="28ee3-149">Both algorithms can detect seasonality in data at multiple levels.</span></span> <span data-ttu-id="28ee3-150">例如，您的資料可能包含年週期內的巢狀月週期。</span><span class="sxs-lookup"><span data-stu-id="28ee3-150">For example, your data might contain monthly cycles nested within yearly cycles.</span></span> <span data-ttu-id="28ee3-151">若要偵測這些季節性週期，您可以提供週期提示，或是指定此演算法應該自動偵測週期。</span><span class="sxs-lookup"><span data-stu-id="28ee3-151">To detect these seasonal cycles, you can either provide a periodicity hint or specify that the algorithm should automatically detect periodicity.</span></span>  
  
 <span data-ttu-id="28ee3-152">除了週期以外，還有其他幾個參數可在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 時間序列演算法偵測週期、做出預測或分析案例時，控制此演算法的行為。</span><span class="sxs-lookup"><span data-stu-id="28ee3-152">In addition to periodicity, there are several other parameters that control the behavior of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Time Series algorithm when it detects periodicity, makes predictions, or analyzes cases.</span></span> <span data-ttu-id="28ee3-153">如需設定演算法參數的資訊，請參閱 [Microsoft 時間序列演算法技術參考](microsoft-time-series-algorithm-technical-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="28ee3-153">For information about how to set algorithm parameters, see [Microsoft Time Series Algorithm Technical Reference](microsoft-time-series-algorithm-technical-reference.md).</span></span>  
  
## <a name="data-required-for-time-series-models"></a><span data-ttu-id="28ee3-154">時間序列模型所需的資料</span><span class="sxs-lookup"><span data-stu-id="28ee3-154">Data Required for Time Series Models</span></span>  
 <span data-ttu-id="28ee3-155">當您準備資料以供任何資料採礦模型的定型使用時，請務必了解特定模型的需求及資料的使用方式。</span><span class="sxs-lookup"><span data-stu-id="28ee3-155">When you prepare data for use in training any data mining model, make sure that you understand the requirements for the particular model and how the data is used.</span></span>  
  
 <span data-ttu-id="28ee3-156">每一個預測模型都必須包含一個案例序列，它是用於指定發生變更之時間配量或其他序列的資料行。</span><span class="sxs-lookup"><span data-stu-id="28ee3-156">Each forecasting model must contain a case series, which is the column that specifies the time slices or other series over which change occurs.</span></span> <span data-ttu-id="28ee3-157">例如，上述圖表中的資料會顯示幾個月的期間內，已發生和預測的腳踏車銷售量的序列</span><span class="sxs-lookup"><span data-stu-id="28ee3-157">For example, the data in the previous diagram shows the series for historical and forecasted bicycle sales over a period of several months.</span></span> <span data-ttu-id="28ee3-158">對於此模型而言，每一個區域都是一個序列，而且日期資料行會包含時間序列 (也是案例序列)。</span><span class="sxs-lookup"><span data-stu-id="28ee3-158">For this model, each region is a series, and the date column contains the time series, which is also the case series.</span></span> <span data-ttu-id="28ee3-159">在其他模型中，案例序列可以是文字欄位或某個識別碼，例如客戶識別碼或交易識別碼。</span><span class="sxs-lookup"><span data-stu-id="28ee3-159">In other models, the case series can be a text field or some identifier such as a customer ID or transaction ID.</span></span> <span data-ttu-id="28ee3-160">但是，時間序列模型一定必須在它的案例序列中使用日期、時間或某個其他唯一的數值。</span><span class="sxs-lookup"><span data-stu-id="28ee3-160">However, a time series model must always use a date, time, or some other unique numeric value for its case series.</span></span>  
  
 <span data-ttu-id="28ee3-161">時間序列模型的需求如下：</span><span class="sxs-lookup"><span data-stu-id="28ee3-161">The requirements for a time series model are as follows:</span></span>  
  
-   <span data-ttu-id="28ee3-162">**單一索引鍵時間資料行** ：每一個模型都必須包含一個數值或日期資料行來當做案例序列使用，此序列會定義此模型將使用的時間配量。</span><span class="sxs-lookup"><span data-stu-id="28ee3-162">**A single key time column** Each model must contain one numeric or date column that is used as the case series, which defines the time slices that the model will use.</span></span> <span data-ttu-id="28ee3-163">Key Time 資料行的資料類型可以是日期時間資料類型或數值資料類型。</span><span class="sxs-lookup"><span data-stu-id="28ee3-163">The data type for the key time column can be either a datetime data type or a numeric data type.</span></span> <span data-ttu-id="28ee3-164">但是，此資料行必須包含連續的值，而且每一個序列的值都必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="28ee3-164">However, the column must contain continuous values, and the values must be unique for each series.</span></span> <span data-ttu-id="28ee3-165">時間序列模型的案例序列無法儲存於兩個資料行中，例如 Year 資料行和 Month 資料行。</span><span class="sxs-lookup"><span data-stu-id="28ee3-165">The case series for a time series model cannot be stored in two columns, such as a Year column and a Month column.</span></span>  
  
-   <span data-ttu-id="28ee3-166">**可預測資料行** ：每一個模型都至少必須包含一個可預測的資料行，演算法將在此資料行周圍建立時間序列模型。</span><span class="sxs-lookup"><span data-stu-id="28ee3-166">**A predictable column** Each model must contain at least one predictable column around which the algorithm will build the time series model.</span></span> <span data-ttu-id="28ee3-167">可預測資料行的資料類型必須有連續的值。</span><span class="sxs-lookup"><span data-stu-id="28ee3-167">The data type of the predictable column must have continuous values.</span></span> <span data-ttu-id="28ee3-168">例如，您可以預測數值屬性 (如收入、銷售或溫度) 會如何隨著時間而變化。</span><span class="sxs-lookup"><span data-stu-id="28ee3-168">For example, you can predict how numeric attributes, such as income, sales, or temperature, change over time.</span></span> <span data-ttu-id="28ee3-169">但是，您無法使用包含不連續值 (如購買狀態或教育程度) 的資料行當做可預測資料行。</span><span class="sxs-lookup"><span data-stu-id="28ee3-169">However, you cannot use a column that contains discrete values, such as purchasing status or level of education, as the predictable column.</span></span>  
  
-   <span data-ttu-id="28ee3-170">**選擇性序列索引鍵資料行** ：每一個模型都可以有其他的索引鍵資料行 (此資料行包含可識別序列的唯一值)。</span><span class="sxs-lookup"><span data-stu-id="28ee3-170">**An optional series key column** Each model can have an additional key column that contains unique values that identify a series.</span></span> <span data-ttu-id="28ee3-171">選擇性序列索引鍵資料行必須包含唯一的值。</span><span class="sxs-lookup"><span data-stu-id="28ee3-171">The optional series key column must contain unique values.</span></span> <span data-ttu-id="28ee3-172">例如，單一模型可包含許多產品型號的銷售，只要每一個時間配量的每一個產品名稱都只有一筆記錄即可。</span><span class="sxs-lookup"><span data-stu-id="28ee3-172">For example, a single model can contain sales for many product models, as long as there is only one record for each product name for every time slice.</span></span>  
  
 <span data-ttu-id="28ee3-173">您可使用幾種不同的方式來定義 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 時間序列模型的輸入資料。</span><span class="sxs-lookup"><span data-stu-id="28ee3-173">You can define input data for the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Time Series model in several different ways.</span></span> <span data-ttu-id="28ee3-174">但是，由於輸入案例的格式會影響採礦模型的定義，所以您必須考量業務需求，並據此來準備資料。</span><span class="sxs-lookup"><span data-stu-id="28ee3-174">However, because the format of the input cases affects the definition of the mining model, you must consider your business needs and prepare your data accordingly.</span></span> <span data-ttu-id="28ee3-175">下列兩個範例將說明輸入資料如何影響此模型。</span><span class="sxs-lookup"><span data-stu-id="28ee3-175">The following two examples illustrate how the input data affects the model.</span></span> <span data-ttu-id="28ee3-176">在這兩個範例中，完成的採礦模型包含四個相異序列的模式：</span><span class="sxs-lookup"><span data-stu-id="28ee3-176">In both examples, the completed mining model contains patterns for four distinct series:</span></span>  
  
-   <span data-ttu-id="28ee3-177">產品 A 的銷售</span><span class="sxs-lookup"><span data-stu-id="28ee3-177">Sales for Product A</span></span>  
  
-   <span data-ttu-id="28ee3-178">產品 B 的銷售</span><span class="sxs-lookup"><span data-stu-id="28ee3-178">Sales for Product B</span></span>  
  
-   <span data-ttu-id="28ee3-179">產品 A 的數量</span><span class="sxs-lookup"><span data-stu-id="28ee3-179">Volume for Product A</span></span>  
  
-   <span data-ttu-id="28ee3-180">產品 B 的數量</span><span class="sxs-lookup"><span data-stu-id="28ee3-180">Volume for Product B</span></span>  
  
 <span data-ttu-id="28ee3-181">在這兩個範例中，您可以針對每一個產品預測新的未來銷售和數量。</span><span class="sxs-lookup"><span data-stu-id="28ee3-181">In both examples, you can predict new future sales and volume for each product.</span></span> <span data-ttu-id="28ee3-182">您無法預測產品或時間的新值。</span><span class="sxs-lookup"><span data-stu-id="28ee3-182">You cannot predict new values for product or for time.</span></span>  
  
### <a name="example-1-time-series-data-set-with-series-represented-as-column-values"></a><span data-ttu-id="28ee3-183">範例 1：具有表示為資料行值的時間序列資料集</span><span class="sxs-lookup"><span data-stu-id="28ee3-183">Example 1: Time Series Data Set with Series Represented as Column Values</span></span>  
 <span data-ttu-id="28ee3-184">這個範例使用下列的輸入案例表：</span><span class="sxs-lookup"><span data-stu-id="28ee3-184">This example uses the following table of input cases:</span></span>  
  
|<span data-ttu-id="28ee3-185">TimeID</span><span class="sxs-lookup"><span data-stu-id="28ee3-185">TimeID</span></span>|<span data-ttu-id="28ee3-186">產品</span><span class="sxs-lookup"><span data-stu-id="28ee3-186">Product</span></span>|<span data-ttu-id="28ee3-187">Sales</span><span class="sxs-lookup"><span data-stu-id="28ee3-187">Sales</span></span>|<span data-ttu-id="28ee3-188">磁碟區</span><span class="sxs-lookup"><span data-stu-id="28ee3-188">Volume</span></span>|  
|------------|-------------|-----------|------------|  
|<span data-ttu-id="28ee3-189">1/2001</span><span class="sxs-lookup"><span data-stu-id="28ee3-189">1/2001</span></span>|<span data-ttu-id="28ee3-190">A</span><span class="sxs-lookup"><span data-stu-id="28ee3-190">A</span></span>|<span data-ttu-id="28ee3-191">1000</span><span class="sxs-lookup"><span data-stu-id="28ee3-191">1000</span></span>|<span data-ttu-id="28ee3-192">600</span><span class="sxs-lookup"><span data-stu-id="28ee3-192">600</span></span>|  
|<span data-ttu-id="28ee3-193">2/2001</span><span class="sxs-lookup"><span data-stu-id="28ee3-193">2/2001</span></span>|<span data-ttu-id="28ee3-194">A</span><span class="sxs-lookup"><span data-stu-id="28ee3-194">A</span></span>|<span data-ttu-id="28ee3-195">1100</span><span class="sxs-lookup"><span data-stu-id="28ee3-195">1100</span></span>|<span data-ttu-id="28ee3-196">500</span><span class="sxs-lookup"><span data-stu-id="28ee3-196">500</span></span>|  
|<span data-ttu-id="28ee3-197">1/2001</span><span class="sxs-lookup"><span data-stu-id="28ee3-197">1/2001</span></span>|<span data-ttu-id="28ee3-198">B</span><span class="sxs-lookup"><span data-stu-id="28ee3-198">B</span></span>|<span data-ttu-id="28ee3-199">500</span><span class="sxs-lookup"><span data-stu-id="28ee3-199">500</span></span>|<span data-ttu-id="28ee3-200">900</span><span class="sxs-lookup"><span data-stu-id="28ee3-200">900</span></span>|  
|<span data-ttu-id="28ee3-201">2/2001</span><span class="sxs-lookup"><span data-stu-id="28ee3-201">2/2001</span></span>|<span data-ttu-id="28ee3-202">B</span><span class="sxs-lookup"><span data-stu-id="28ee3-202">B</span></span>|<span data-ttu-id="28ee3-203">300</span><span class="sxs-lookup"><span data-stu-id="28ee3-203">300</span></span>|<span data-ttu-id="28ee3-204">890</span><span class="sxs-lookup"><span data-stu-id="28ee3-204">890</span></span>|  
  
 <span data-ttu-id="28ee3-205">資料表中的 TimeID 資料表包含時間識別碼，且每一天有兩個項目。</span><span class="sxs-lookup"><span data-stu-id="28ee3-205">The TimeID column in the table contains a time identifier, and has two entries for each day.</span></span> <span data-ttu-id="28ee3-206">TimeID 資料行會變成案例序列。</span><span class="sxs-lookup"><span data-stu-id="28ee3-206">The TimeID column becomes the case series.</span></span> <span data-ttu-id="28ee3-207">因此，您要將此資料行指定為時間序列模型的 Key Time 資料行。</span><span class="sxs-lookup"><span data-stu-id="28ee3-207">Therefore, you would designate this column as the key time column for the time series model.</span></span>  
  
 <span data-ttu-id="28ee3-208">Product 資料行定義資料庫中的產品。</span><span class="sxs-lookup"><span data-stu-id="28ee3-208">The Product column defines a product in the database.</span></span> <span data-ttu-id="28ee3-209">這個資料行包含產品序列。</span><span class="sxs-lookup"><span data-stu-id="28ee3-209">This column contains the product series.</span></span> <span data-ttu-id="28ee3-210">因此，您要將此資料行指定為時間序列模型的第二個索引鍵。</span><span class="sxs-lookup"><span data-stu-id="28ee3-210">Therefore, you would designate this column as a second key for the time series model.</span></span>  
  
 <span data-ttu-id="28ee3-211">Sales 資料行描述所指定產品一天的毛利，而 Volume 資料行描述所指定產品在倉庫中剩餘的數量。</span><span class="sxs-lookup"><span data-stu-id="28ee3-211">The Sales column describes the gross profits of the specified product for one day, and the Volume column describes the quantity of the specified product that remains in the warehouse.</span></span> <span data-ttu-id="28ee3-212">這兩個資料行都包含用於定型此模型的資料。</span><span class="sxs-lookup"><span data-stu-id="28ee3-212">These two columns contain the data that is used to train the model.</span></span> <span data-ttu-id="28ee3-213">對於 Product 資料行中的每一個序列而言，Sales 和 Volume 都是可以預測的屬性。</span><span class="sxs-lookup"><span data-stu-id="28ee3-213">Both Sales and Volume  can be predictable attributes for each series in the Product column.</span></span>  
  
### <a name="example-2-time-series-data-set-with-each-series-in-separate-column"></a><span data-ttu-id="28ee3-214">範例 2：時間序列資料集，其中的每一個序列都在個別資料行中</span><span class="sxs-lookup"><span data-stu-id="28ee3-214">Example 2: Time Series Data Set with Each Series in Separate Column</span></span>  
 <span data-ttu-id="28ee3-215">雖然這個範例基本上會使用與第一個範例相同的輸入資料，但是輸入資料的結構有所不同，如下表所示：</span><span class="sxs-lookup"><span data-stu-id="28ee3-215">Although this example uses basically the same input data as the first example, the input data is structured differently, as shown in the following table:</span></span>  
  
|<span data-ttu-id="28ee3-216">TimeID</span><span class="sxs-lookup"><span data-stu-id="28ee3-216">TimeID</span></span>|<span data-ttu-id="28ee3-217">A_Sales</span><span class="sxs-lookup"><span data-stu-id="28ee3-217">A_Sales</span></span>|<span data-ttu-id="28ee3-218">A_Volume</span><span class="sxs-lookup"><span data-stu-id="28ee3-218">A_Volume</span></span>|<span data-ttu-id="28ee3-219">B_Sales</span><span class="sxs-lookup"><span data-stu-id="28ee3-219">B_Sales</span></span>|<span data-ttu-id="28ee3-220">B_Volume</span><span class="sxs-lookup"><span data-stu-id="28ee3-220">B_Volume</span></span>|  
|------------|--------------|---------------|--------------|---------------|  
|<span data-ttu-id="28ee3-221">1/2001</span><span class="sxs-lookup"><span data-stu-id="28ee3-221">1/2001</span></span>|<span data-ttu-id="28ee3-222">1000</span><span class="sxs-lookup"><span data-stu-id="28ee3-222">1000</span></span>|<span data-ttu-id="28ee3-223">600</span><span class="sxs-lookup"><span data-stu-id="28ee3-223">600</span></span>|<span data-ttu-id="28ee3-224">500</span><span class="sxs-lookup"><span data-stu-id="28ee3-224">500</span></span>|<span data-ttu-id="28ee3-225">900</span><span class="sxs-lookup"><span data-stu-id="28ee3-225">900</span></span>|  
|<span data-ttu-id="28ee3-226">2/2001</span><span class="sxs-lookup"><span data-stu-id="28ee3-226">2/2001</span></span>|<span data-ttu-id="28ee3-227">1100</span><span class="sxs-lookup"><span data-stu-id="28ee3-227">1100</span></span>|<span data-ttu-id="28ee3-228">500</span><span class="sxs-lookup"><span data-stu-id="28ee3-228">500</span></span>|<span data-ttu-id="28ee3-229">300</span><span class="sxs-lookup"><span data-stu-id="28ee3-229">300</span></span>|<span data-ttu-id="28ee3-230">890</span><span class="sxs-lookup"><span data-stu-id="28ee3-230">890</span></span>|  
  
 <span data-ttu-id="28ee3-231">在此表格中，TimeID 資料行仍然包含時間序列模型的案例序列，您會將此資料行指定為 Key Time 資料行。</span><span class="sxs-lookup"><span data-stu-id="28ee3-231">In this table, the TimeID column still contains the case series for the time series model, which you designate as the key time column.</span></span> <span data-ttu-id="28ee3-232">但是，之前的 Sales 和 Volume 資料行現在已分成兩個資料行，而且每一個資料行的前面都有產品名稱。</span><span class="sxs-lookup"><span data-stu-id="28ee3-232">However, the previous Sales and Volume columns are now split into two columns and each of those columns are preceded by the product name.</span></span> <span data-ttu-id="28ee3-233">因此，TimeID 資料行中每一天只有單一項目存在。</span><span class="sxs-lookup"><span data-stu-id="28ee3-233">As a result, only a single entry exists for each day in the TimeID column.</span></span> <span data-ttu-id="28ee3-234">這會建立一個包含 4 個可預測資料行的時間序列模型：A_Sales、A_Volume、B_Sales 和 B_Volume。</span><span class="sxs-lookup"><span data-stu-id="28ee3-234">This creates a time series model that would contain four predictable columns: A_Sales, A_Volume, B_Sales, and B_Volume.</span></span>  
  
 <span data-ttu-id="28ee3-235">此外，由於您已經將產品分成不同的資料行，所以您不必指定其他的序列索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="28ee3-235">Furthermore, because you have separated the products into different columns, you do not have to specify an additional series key column.</span></span> <span data-ttu-id="28ee3-236">此模型中的所有資料行不是案例序列資料行，就是可預測資料行。</span><span class="sxs-lookup"><span data-stu-id="28ee3-236">All the columns in the model are either a case series column or a predictable column.</span></span>  
  
## <a name="viewing-a-time-series-model"></a><span data-ttu-id="28ee3-237">檢視時間序列模型</span><span class="sxs-lookup"><span data-stu-id="28ee3-237">Viewing a Time Series Model</span></span>  
 <span data-ttu-id="28ee3-238">在此模型已培訓之後，結果會儲存成一組模式，供您瀏覽或用來做出預測。</span><span class="sxs-lookup"><span data-stu-id="28ee3-238">After the model has been trained, the results are stored as a set of patterns, which you can explore or use to make predictions.</span></span>  
  
 <span data-ttu-id="28ee3-239">若要瀏覽此模型，您可以使用 [時間序列檢視器](browse-a-model-using-the-microsoft-time-series-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="28ee3-239">To explore the model, you can use the [Time Series Viewer](browse-a-model-using-the-microsoft-time-series-viewer.md).</span></span> <span data-ttu-id="28ee3-240">此檢視器包含一個圖表來顯示未來的預測，並包含樹狀檢視來顯示資料中的週期結構。</span><span class="sxs-lookup"><span data-stu-id="28ee3-240">The viewer includes a chart that displays future predictions, and a tree view of the periodic structures in the data.</span></span>  
  
 <span data-ttu-id="28ee3-241">如果您想要知道如何計算預測結果的詳細資訊，您可以在 [Microsoft 一般內容樹狀檢視器](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)中瀏覽此模型。</span><span class="sxs-lookup"><span data-stu-id="28ee3-241">If you want to know more about how the predictions are calculated, you can browse the model in the [Microsoft Generic Content Tree Viewer](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md).</span></span> <span data-ttu-id="28ee3-242">針對此模型儲存的內容包括類似以下的詳細資料：ARIMA 和 ARTXP 演算法所偵測的週期結構、用於混合演算法的方程式及其他統計資料。</span><span class="sxs-lookup"><span data-stu-id="28ee3-242">The content stored for the model includes details such as the periodic structures detected by the ARIMA and ARTXP algorithms, the equation used to blend the algorithms, and other statistics.</span></span>  
  
## <a name="creating-time-series-predictions"></a><span data-ttu-id="28ee3-243">建立時間序列預測</span><span class="sxs-lookup"><span data-stu-id="28ee3-243">Creating Time Series Predictions</span></span>  
 <span data-ttu-id="28ee3-244">依預設，當您檢視時間序列模型時， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會為您顯示此序列的五個預測。</span><span class="sxs-lookup"><span data-stu-id="28ee3-244">By default, when you view a time series model, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] shows you five predictions for the series.</span></span> <span data-ttu-id="28ee3-245">但是，您可以建立查詢來傳回變動數目的預測，而且可以將資料行擷取到預測中，以傳回描述性的統計資料。</span><span class="sxs-lookup"><span data-stu-id="28ee3-245">However, you can create queries to return a variable number of predictions, and you can extra columns to the predictions to return descriptive statistics.</span></span> <span data-ttu-id="28ee3-246">如需如何針對時間序列模型建立查詢的詳細資訊，請參閱 [時間序列模型查詢範例](time-series-model-query-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="28ee3-246">For information about how to create queries against a time series model, see [Time Series Model Query Examples](time-series-model-query-examples.md).</span></span> <span data-ttu-id="28ee3-247">如需如何使用資料採礦延伸模組 (DMX) 來做出時間序列預測的範例，請參閱 [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx)。</span><span class="sxs-lookup"><span data-stu-id="28ee3-247">For examples of how to use Data Mining Extensions (DMX) to make time series predictions, see [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx).</span></span>  
  
 <span data-ttu-id="28ee3-248">當使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 時間序列演算法進行預測時，您應該考量下列其他的限制和需求：</span><span class="sxs-lookup"><span data-stu-id="28ee3-248">When using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Time Series algorithm to make predictions, you should consider the following additional restrictions and requirements:</span></span>  
  
-   <span data-ttu-id="28ee3-249">只有當您使用混合模型或是根據 ARTXP 演算法的模型時，才可使用交叉預測。</span><span class="sxs-lookup"><span data-stu-id="28ee3-249">Cross-prediction is only available when you use a mixed model, or a model based on the ARTXP algorithm.</span></span> <span data-ttu-id="28ee3-250">如果您使用只根據 ARIMA 演算法的模型，將無法使用交叉預測。</span><span class="sxs-lookup"><span data-stu-id="28ee3-250">If you use a model based only on the ARIMA algorithm, cross-prediction is not possible.</span></span>  
  
-   <span data-ttu-id="28ee3-251">時間序列模型可根據伺服器使用的 64 位元作業系統做出不同的預測 (有時可能會有很大的差異)。</span><span class="sxs-lookup"><span data-stu-id="28ee3-251">A time series model can make predictions that differ, sometimes significantly, depending on the 64-bit operating system that the server uses.</span></span> <span data-ttu-id="28ee3-252">發生這些差異的原因是因為 [!INCLUDE[vcpritanium](../../includes/vcpritanium-md.md)]架構系統表示及處理浮點算術之數字的方式，與 [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]架構系統的計算方式不同。</span><span class="sxs-lookup"><span data-stu-id="28ee3-252">These differences occur due to the way that an [!INCLUDE[vcpritanium](../../includes/vcpritanium-md.md)]-based system represents and handles numbers for floating-point arithmetic, which differs from the way that an [!INCLUDE[vcprx64](../../includes/vcprx64-md.md)]-based system does these calculations.</span></span> <span data-ttu-id="28ee3-253">由於預測結果可能會是作業系統所特有，所以我們建議您在實際執行的相同作業系統上評估模型。</span><span class="sxs-lookup"><span data-stu-id="28ee3-253">Because prediction results can be specific to the operating system, we recommend that you evaluate models on the same operating system that you will use in production.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28ee3-254">備註</span><span class="sxs-lookup"><span data-stu-id="28ee3-254">Remarks</span></span>  
  
-   <span data-ttu-id="28ee3-255">不支援使用預測模型標記語言 (PMML) 來建立採礦模型。</span><span class="sxs-lookup"><span data-stu-id="28ee3-255">Does not support using the Predictive Model Markup Language (PMML) to create mining models.</span></span>  
  
-   <span data-ttu-id="28ee3-256">支援 OLAP 採礦模型的使用。</span><span class="sxs-lookup"><span data-stu-id="28ee3-256">Supports the use of OLAP mining models.</span></span>  
  
-   <span data-ttu-id="28ee3-257">不支援建立資料採礦維度。</span><span class="sxs-lookup"><span data-stu-id="28ee3-257">Does not support the creation of data mining dimensions.</span></span>  
  
-   <span data-ttu-id="28ee3-258">支援鑽研。</span><span class="sxs-lookup"><span data-stu-id="28ee3-258">Supports drillthrough.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28ee3-259">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28ee3-259">See Also</span></span>  
 <span data-ttu-id="28ee3-260">[資料採礦演算法 &#40;Analysis Services-資料採礦&#41;](data-mining-algorithms-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="28ee3-260">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="28ee3-261">[使用 Microsoft 時間序列檢視器流覽模型](browse-a-model-using-the-microsoft-time-series-viewer.md) </span><span class="sxs-lookup"><span data-stu-id="28ee3-261">[Browse a Model Using the Microsoft Time Series Viewer](browse-a-model-using-the-microsoft-time-series-viewer.md) </span></span>  
 <span data-ttu-id="28ee3-262">[Microsoft 時間序列演算法技術參考](microsoft-time-series-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="28ee3-262">[Microsoft Time Series Algorithm Technical Reference](microsoft-time-series-algorithm-technical-reference.md) </span></span>  
 <span data-ttu-id="28ee3-263">[時間序列模型查詢範例](time-series-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="28ee3-263">[Time Series Model Query Examples](time-series-model-query-examples.md) </span></span>  
 [<span data-ttu-id="28ee3-264">時間序列模型的採礦模型內容 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="28ee3-264">Mining Model Content for Time Series Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-time-series-models-analysis-services-data-mining.md)  
  
  