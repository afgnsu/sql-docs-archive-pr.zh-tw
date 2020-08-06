---
title: 將圖表新增至報表 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a6b595dc-f775-4a53-8554-74a0bf9335ec
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 789dd6cce10b0425833ea63f2f7941ea75970a25
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585050"
---
# <a name="add-a-chart-to-a-report-report-builder-and-ssrs"></a><span data-ttu-id="e183f-102">將圖表加入至報表 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="e183f-102">Add a Chart to a Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="e183f-103">當您想要以視覺格式摘要資料時，請使用圖表資料區域。</span><span class="sxs-lookup"><span data-stu-id="e183f-103">When you want to summarize data in a visual format, use a Chart data region.</span></span> <span data-ttu-id="e183f-104">針對您要呈現的資料類型選擇適當的圖表類型相當重要。</span><span class="sxs-lookup"><span data-stu-id="e183f-104">It is important to choose an appropriate chart type for the type of data that you are presenting.</span></span> <span data-ttu-id="e183f-105">因為這會影響以圖表形式放入資料時可以解譯資料的程度。</span><span class="sxs-lookup"><span data-stu-id="e183f-105">This affects how well the data can be interpreted when put in chart form.</span></span> <span data-ttu-id="e183f-106">如需詳細資訊，請參閱 [圖表 &#40;報表產生器及 SSRS&#41;](charts-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="e183f-106">For more information, see [Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="e183f-107">將圖表資料區加入至報表最簡單的方式就是執行新增圖表精靈。</span><span class="sxs-lookup"><span data-stu-id="e183f-107">The simplest way to add a Chart data region to your report is to run the New Chart Wizard.</span></span> <span data-ttu-id="e183f-108">該精靈提供直條圖、折線圖、圓形圖、橫條圖和區域圖。</span><span class="sxs-lookup"><span data-stu-id="e183f-108">The wizard offers column, line, pie, bar, and area charts.</span></span> <span data-ttu-id="e183f-109">您也可以透過手動方式，加入上述圖表以及其他的圖表類型。</span><span class="sxs-lookup"><span data-stu-id="e183f-109">For these and other chart types, you can also add a chart manually.</span></span>  
  
 <span data-ttu-id="e183f-110">將圖表資料區加入至設計介面之後，您可以將數值和非數值資料的報表資料集欄位拖曳到圖表的 [圖表資料] 窗格。</span><span class="sxs-lookup"><span data-stu-id="e183f-110">After you add a Chart data region to the design surface, you can drag report dataset fields for numeric and non-numeric data to the Chart Data pane of the chart.</span></span> <span data-ttu-id="e183f-111">按一下圖表即可顯示 [圖表資料] 窗格，其中包含三個區域：[數列群組]、[類別群組] 和 [值]。</span><span class="sxs-lookup"><span data-stu-id="e183f-111">Click the chart to display the Chart Data pane with its three areas: Series Groups, Category Groups, and Values.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-chart-to-a-report-by-using-the-chart-wizard"></a><span data-ttu-id="e183f-112">若要使用圖表精靈在報表中加入圖表</span><span class="sxs-lookup"><span data-stu-id="e183f-112">To add a chart to a report by using the Chart Wizard</span></span>  
  
1.  > [!NOTE]  
    >  <span data-ttu-id="e183f-113">您只能在報表產生器中使用圖表精靈。</span><span class="sxs-lookup"><span data-stu-id="e183f-113">The Chart Wizard is only available in Report Builder.</span></span>  
  
     <span data-ttu-id="e183f-114">在 [插入]  索引標籤上，按一下 [圖表]  ，然後按一下 [圖表精靈]  。</span><span class="sxs-lookup"><span data-stu-id="e183f-114">On the **Insert** tab, click **Chart**, and then click **Chart Wizard**.</span></span>  
  
2.  <span data-ttu-id="e183f-115">請遵循 [新增圖表精靈]  中的步驟執行。</span><span class="sxs-lookup"><span data-stu-id="e183f-115">Follow the steps in the **New** Chart wizard.</span></span>  
  
3.  <span data-ttu-id="e183f-116">在 **[主資料夾]** 索引標籤上，按一下 **[執行]** 查看轉譯的報表。</span><span class="sxs-lookup"><span data-stu-id="e183f-116">On the **Home** tab, click **Run** to see the rendered report.</span></span>  
  
4.  <span data-ttu-id="e183f-117">在 **[執行]** 索引標籤上，按一下 **[設計]** 繼續處理報表。</span><span class="sxs-lookup"><span data-stu-id="e183f-117">On the **Run** tab, click **Design** to continue working on the report.</span></span>  
  
### <a name="to-add-a-chart-to-a-report"></a><span data-ttu-id="e183f-118">若要將圖表加入至報表</span><span class="sxs-lookup"><span data-stu-id="e183f-118">To add a chart to a report</span></span>  
  
1.  <span data-ttu-id="e183f-119">建立報表，並定義資料集。</span><span class="sxs-lookup"><span data-stu-id="e183f-119">Create a report and define a dataset.</span></span> <span data-ttu-id="e183f-120">如需詳細資訊，請參閱[將資料加入報表 &#40;報表產生器和 SSRS&#41;](../report-data/report-datasets-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="e183f-120">For more information, see [Add Data to a Report &#40;Report Builder and SSRS&#41;](../report-data/report-datasets-ssrs.md).</span></span>  
  
2.  <span data-ttu-id="e183f-121">在 [插入]  索引標籤上，按一下 [圖表]  ，然後按一下 [插入圖表]  。</span><span class="sxs-lookup"><span data-stu-id="e183f-121">On the **Insert** tab, click **Chart**, and then click **Insert Chart**.</span></span>  
  
3.  <span data-ttu-id="e183f-122">在設計介面上您要放置圖表左上角的位置按一下，然後拖曳到您要放置圖表右下角的位置。</span><span class="sxs-lookup"><span data-stu-id="e183f-122">Click on the design surface where you want the upper-left corner of the chart, and then drag to where you want the lower-right corner of the chart.</span></span>  
  
     <span data-ttu-id="e183f-123">[選取圖表類型]  對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="e183f-123">The **Select Chart Type** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="e183f-124">選取您想要加入的圖表類型。</span><span class="sxs-lookup"><span data-stu-id="e183f-124">Select the type of chart you want to add.</span></span> [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="e183f-125">按一下圖表以顯示 [圖表資料]  窗格。</span><span class="sxs-lookup"><span data-stu-id="e183f-125">Click the chart to display the **Chart Data** pane.</span></span>  
  
6.  <span data-ttu-id="e183f-126">將一或多個欄位新增至 [值]  區域。</span><span class="sxs-lookup"><span data-stu-id="e183f-126">Add one or more fields to the **Values** area.</span></span> <span data-ttu-id="e183f-127">這些資訊將會繪製在值軸上。</span><span class="sxs-lookup"><span data-stu-id="e183f-127">This information will be plotted on the value axis.</span></span>  
  
7.  <span data-ttu-id="e183f-128">將群組欄位新增至 [類別目錄群組]  區域。</span><span class="sxs-lookup"><span data-stu-id="e183f-128">Add a grouping field to the **Category Groups** area.</span></span> <span data-ttu-id="e183f-129">當您將這個欄位新增至[類別目錄群組]  區域時，系統會自動為您建立群組欄位。</span><span class="sxs-lookup"><span data-stu-id="e183f-129">When you add this field to the **Category Groups** area, a grouping field is automatically created for you.</span></span> <span data-ttu-id="e183f-130">每一個群組都代表數列中一個資料點。</span><span class="sxs-lookup"><span data-stu-id="e183f-130">Each group represents a data point in your series.</span></span>  
  
8.  <span data-ttu-id="e183f-131">若要依據類別目錄摘要資料，請以滑鼠右鍵按一下資料欄位，然後按一下 [數列屬性]  。</span><span class="sxs-lookup"><span data-stu-id="e183f-131">To summarize the data by category, right-click the data field and click **Series Properties**.</span></span> <span data-ttu-id="e183f-132">在 [類別目錄]  方塊中，從下拉式清單選取類別目錄欄位。</span><span class="sxs-lookup"><span data-stu-id="e183f-132">In the **Category** box, select the category field from the drop-down list.</span></span> [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
9. <span data-ttu-id="e183f-133">在 **[主資料夾]** 索引標籤上，按一下 **[執行]** 查看轉譯的報表。</span><span class="sxs-lookup"><span data-stu-id="e183f-133">On the **Home** tab, click **Run** to see the rendered report.</span></span>  
  
10. <span data-ttu-id="e183f-134">在 **[執行]** 索引標籤上，按一下 **[設計]** 繼續處理報表。</span><span class="sxs-lookup"><span data-stu-id="e183f-134">On the **Run** tab, click **Design** to continue working on the report.</span></span>  
  
 <span data-ttu-id="e183f-135">在包含軸的圖表上 (如橫條圖和直條圖)，類別目錄軸可能不會顯示所有的類別目錄標籤。</span><span class="sxs-lookup"><span data-stu-id="e183f-135">On charts with axes, such as bar and column charts, the category axis may not display all the category labels.</span></span> <span data-ttu-id="e183f-136">如需如何變更軸標籤的詳細資訊，請參閱[指定軸間隔 &#40;報表產生器及 SSRS&#41;](specify-an-axis-interval-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="e183f-136">For more information about how to change the axis labels, see [Specify an Axis Interval &#40;Report Builder and SSRS&#41;](specify-an-axis-interval-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e183f-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e183f-137">See Also</span></span>  
 <span data-ttu-id="e183f-138">[圖表 &#40;報表產生器及 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e183f-138">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="e183f-139">[圖表類型 &#40;報表產生器及 SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e183f-139">[Chart Types &#40;Report Builder and SSRS&#41;](chart-types-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="e183f-140">[圖表中的空白和 Null 資料點 &#40;報表產生器及 SSRS&#41;](empty-and-null-data-points-in-charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e183f-140">[Empty and Null Data Points in Charts &#40;Report Builder and SSRS&#41;](empty-and-null-data-points-in-charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="e183f-141">[教學課程：將橫條圖新增至報表 (報表產生器)](https://go.microsoft.com/fwlink/?LinkId=198052) </span><span class="sxs-lookup"><span data-stu-id="e183f-141">[Tutorial: Adding a Bar Chart to Your Report (Report Builder)](https://go.microsoft.com/fwlink/?LinkId=198052) </span></span>  
 <span data-ttu-id="e183f-142">[教學課程：將橫條圖新增至報表 (報表設計工具)](https://go.microsoft.com/fwlink/?LinkId=198042) </span><span class="sxs-lookup"><span data-stu-id="e183f-142">[Tutorial: Adding a Bar Chart to a Report (Report Designer)](https://go.microsoft.com/fwlink/?LinkId=198042) </span></span>  
 <span data-ttu-id="e183f-143">[教學課程：將圓形圖新增至報表 (報表產生器)](https://go.microsoft.com/fwlink/?LinkId=198051) </span><span class="sxs-lookup"><span data-stu-id="e183f-143">[Tutorial: Adding a Pie Chart to Your Report (Report Builder)](https://go.microsoft.com/fwlink/?LinkId=198051) </span></span>  
 [<span data-ttu-id="e183f-144">教學課程：將圓形圖新增至報表 (報表設計工具)</span><span class="sxs-lookup"><span data-stu-id="e183f-144">Tutorial: Adding a Pie Chart to a Report (Report Designer)</span></span>](https://go.microsoft.com/fwlink/?LinkId=198041)  
  
  