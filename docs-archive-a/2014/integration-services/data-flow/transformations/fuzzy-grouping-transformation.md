---
title: 模糊群組轉換 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fuzzygroupingtrans.f1
helpviewer_keywords:
- cleaning data
- comparing data
- token delimiters [Integration Services]
- temporary indexes [Integration Services]
- Fuzzy Grouping transformation
- temporary tables [Integration Services]
- grouping data
- standardizing data [Integration Services]
- columns [Integration Services], standardizing
- similarity thresholds [Integration Services]
- data cleaning [Integration Services]
- duplicate data [Integration Services]
ms.assetid: e43f17bd-9d13-4a8f-9f29-cce44cac1025
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f26948b4046d31aff934db539a3878cad99ac1ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592779"
---
# <a name="fuzzy-grouping-transformation"></a><span data-ttu-id="5a1e0-102">模糊群組轉換</span><span class="sxs-lookup"><span data-stu-id="5a1e0-102">Fuzzy Grouping Transformation</span></span>
  <span data-ttu-id="5a1e0-103">「模糊群組」轉換會透過識別可能重複的資料列並選取用於標準化資料的標準資料列，執行資料清除工作。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-103">The Fuzzy Grouping transformation performs data cleaning tasks by identifying rows of data that are likely to be duplicates and selecting a canonical row of data to use in standardizing the data.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5a1e0-104">如需模糊群組轉換 (包括效能和記憶體限制) 的詳細資訊，請參閱 [Fuzzy Lookup and Fuzzy Grouping in SQL Server Integration Services 2005](https://go.microsoft.com/fwlink/?LinkId=96604)(SQL Server Integration Services 2005 中的模糊查閱和模糊群組) 白皮書。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-104">For more detailed information about the Fuzzy Grouping transformation, including performance and memory limitations, see the white paper, [Fuzzy Lookup and Fuzzy Grouping in SQL Server Integration Services 2005](https://go.microsoft.com/fwlink/?LinkId=96604).</span></span>  
  
 <span data-ttu-id="5a1e0-105">「模糊群組」轉換需要連接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的執行個體，以建立轉換演算法執行其工作所需的暫存 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料表。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-105">The Fuzzy Grouping transformation requires a connection to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to create the temporary [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tables that the transformation algorithm requires to do its work.</span></span> <span data-ttu-id="5a1e0-106">連接必須解析為具有在資料庫中建立資料表之權限的使用者。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-106">The connection must resolve to a user who has permission to create tables in the database.</span></span>  
  
 <span data-ttu-id="5a1e0-107">若要設定轉換，您必須選取要在識別重複項目時使用的輸入資料行，還必須為每個資料行選取相符類型 (模糊或完全)。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-107">To configure the transformation, you must select the input columns to use when identifying duplicates, and you must select the type of match-fuzzy or exact-for each column.</span></span> <span data-ttu-id="5a1e0-108">完全相符保證只會將該資料行中具有相同值的那些資料列分組。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-108">An exact match guarantees that only rows that have identical values in that column will be grouped.</span></span> <span data-ttu-id="5a1e0-109">完全比對可套用到任何 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 資料類型的資料行，但 DT_TEXT、DT_NTEXT 和 DT_IMAGE 除外。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-109">Exact matching can be applied to columns of any [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] data type except DT_TEXT, DT_NTEXT, and DT_IMAGE.</span></span> <span data-ttu-id="5a1e0-110">模糊相符會將有近似相同值的資料列分組。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-110">A fuzzy match groups rows that have approximately the same values.</span></span> <span data-ttu-id="5a1e0-111">資料之近似比對的方法以使用者指定的相似度分數為基礎。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-111">The method for approximate matching of data is based on a user-specified similarity score.</span></span> <span data-ttu-id="5a1e0-112">只有具有 DT_WSTR 和 DT_STR 資料類型的資料行可用於模糊比對。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-112">Only columns with the DT_WSTR and DT_STR data types can be used in fuzzy matching.</span></span> <span data-ttu-id="5a1e0-113">如需詳細資訊，請參閱 [Integration Services 資料類型](../integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-113">For more information, see [Integration Services Data Types](../integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="5a1e0-114">轉換輸出包括所有輸入資料行、一或多個具有標準化資料的資料行，以及包含相似度分數的資料行。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-114">The transformation output includes all input columns, one or more columns with standardized data, and a column that contains the similarity score.</span></span> <span data-ttu-id="5a1e0-115">分數是介於 0 到 1 之間的十進位值。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-115">The score is a decimal value between 0 and 1.</span></span> <span data-ttu-id="5a1e0-116">標準資料列的分數是 1。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-116">The canonical row has a score of 1.</span></span> <span data-ttu-id="5a1e0-117">模糊群組中其他資料列的分數指出資料列與標準資料列的相符程度。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-117">Other rows in the fuzzy group have scores that indicate how well the row matches the canonical row.</span></span> <span data-ttu-id="5a1e0-118">分數愈接近於 1，資料列與標準資料列的相符程度就愈高。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-118">The closer the score is to 1, the more closely the row matches the canonical row.</span></span> <span data-ttu-id="5a1e0-119">如果模糊群組包括的資料列是與標準資料列完全重複的資料列，則這些資料列的分數也是 1。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-119">If the fuzzy group includes rows that are exact duplicates of the canonical row, these rows also have a score of 1.</span></span> <span data-ttu-id="5a1e0-120">轉換不會移除重複的資料列，而是建立一個將標準資料列與相似資料列產生關聯的索引鍵，將這些重複的資料列分組。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-120">The transformation does not remove duplicate rows; it groups them by creating a key that relates the canonical row to similar rows.</span></span>  
  
 <span data-ttu-id="5a1e0-121">轉換會為每個輸入資料列產生一個輸出資料列，並具有下列其他資料行：</span><span class="sxs-lookup"><span data-stu-id="5a1e0-121">The transformation produces one output row for each input row, with the following additional columns:</span></span>  
  
-   <span data-ttu-id="5a1e0-122">**_key_in**，唯一識別每個資料列的資料行。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-122">**_key_in**, a column that uniquely identifies each row.</span></span>  
  
-   <span data-ttu-id="5a1e0-123">**_key_out**，識別一組重複資料列的資料行。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-123">**_key_out**, a column that identifies a group of duplicate rows.</span></span> <span data-ttu-id="5a1e0-124">**_key_out** 資料行具有標準資料列中 **_key_in** 資料行的值。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-124">The **_key_out** column has the value of the **_key_in** column in the canonical data row.</span></span> <span data-ttu-id="5a1e0-125">具有與 **_key_out** 相同值的資料列屬於同一群組。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-125">Rows with the same value in **_key_out** are part of the same group.</span></span> <span data-ttu-id="5a1e0-126">群組的 **_key_out**值與標準資料列中 **_key_in** 的值相對應。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-126">The **_key_out**value for a group corresponds to the value of **_key_in** in the canonical data row.</span></span>  
  
-   <span data-ttu-id="5a1e0-127">**_score**，介於 0 與 1 之間的值，指出輸入資料列與標準資料列的相似度。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-127">**_score**, a value between 0 and 1 that indicates the similarity of the input row to the canonical row.</span></span>  
  
 <span data-ttu-id="5a1e0-128">以上名稱是預設資料行名稱，您可以設定「模糊分組」轉換使用其他名稱。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-128">These are the default column names and you can configure the Fuzzy Grouping transformation to use other names.</span></span> <span data-ttu-id="5a1e0-129">輸出也為參與模糊群組的每個資料行提供相似度分數。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-129">The output also provides a similarity score for each column that participates in a fuzzy grouping.</span></span>  
  
 <span data-ttu-id="5a1e0-130">「模糊群組」轉換包括兩個自訂其所執行之群組的功能：Token 分隔符號和相似度臨界值。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-130">The Fuzzy Grouping transformation includes two features for customizing the grouping it performs: token delimiters and similarity threshold.</span></span> <span data-ttu-id="5a1e0-131">轉換會提供用於Token 化資料的預設分隔符號集，但您可以加入新的分隔符號，以改進資料的 Token 化。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-131">The transformation provides a default set of delimiters used to tokenize the data, but you can add new delimiters that improve the tokenization of your data.</span></span>  
  
 <span data-ttu-id="5a1e0-132">相似度臨界值指出轉換識別重複項目的嚴格程度。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-132">The similarity threshold indicates how strictly the transformation identifies duplicates.</span></span> <span data-ttu-id="5a1e0-133">相似度臨界值可在元件和資料行層級進行設定。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-133">The similarity thresholds can be set at the component and the column levels.</span></span> <span data-ttu-id="5a1e0-134">資料行層級相似度臨界值只可用於執行模糊相符的資料行。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-134">The column-level similarity threshold is only available to columns that perform a fuzzy match.</span></span> <span data-ttu-id="5a1e0-135">相似度範圍是從 0 到 1。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-135">The similarity range is 0 to 1.</span></span> <span data-ttu-id="5a1e0-136">臨界值愈接近 1，資料列和資料行就愈近似於重複項目。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-136">The closer to 1 the threshold is, the more similar the rows and columns must be to qualify as duplicates.</span></span> <span data-ttu-id="5a1e0-137">透過在元件和資料行層級設定 MinSimilarity 屬性，可以指定資料列和資料行間的相似度臨界值。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-137">You specify the similarity threshold among rows and columns by setting the MinSimilarity property at the component and column levels.</span></span> <span data-ttu-id="5a1e0-138">為滿足在元件層級指定的相似度，所有資料列之所有資料行的相似度都必須大於或等於在元件層級指定的相似度臨界值。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-138">To satisfy the similarity that is specified at the component level, all rows must have a similarity across all columns that is greater than or equal to the similarity threshold that is specified at the component level.</span></span>  
  
 <span data-ttu-id="5a1e0-139">「模糊群組」轉換會計算相似度的內部量值，且不會將與 MinSimilarity 中指定之值不相似的資料列分組。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-139">The Fuzzy Grouping transformation calculates internal measures of similarity, and rows that are less similar than the value specified in MinSimilarity are not grouped.</span></span>  
  
 <span data-ttu-id="5a1e0-140">若要識別資料所使用的相似度臨界值，您可能必須使用不同的最小相似度臨界值，數次套用「模糊群組」轉換。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-140">To identify a similarity threshold that works for your data, you may have to apply the Fuzzy Grouping transformation several times using different minimum similarity thresholds.</span></span> <span data-ttu-id="5a1e0-141">在執行階段，轉換輸出中的分數資料行會包含群組中每個資料列的相似度分數。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-141">At run time, the score columns in transformation output contain the similarity scores for each row in a group.</span></span> <span data-ttu-id="5a1e0-142">您可以使用這些值識別適用於資料的相似度臨界值。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-142">You can use these values to identify the similarity threshold that is appropriate for your data.</span></span> <span data-ttu-id="5a1e0-143">如果您要增加相似度，則應該將 MinSimilarity 設為大於分數資料行中之值的值。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-143">If you want to increase similarity, you should set MinSimilarity to a value larger than the value in the score columns.</span></span>  
  
 <span data-ttu-id="5a1e0-144">透過在「模糊群組」轉換輸入中設定資料行的屬性，可以自訂轉換所執行的群組。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-144">You can customize the grouping that the transformation performs by setting the properties of the columns in the Fuzzy Grouping transformation input.</span></span> <span data-ttu-id="5a1e0-145">例如，FuzzyComparisonFlags 屬性會指定轉換如何比較資料行中的字串資料，ExactFuzzy 屬性則指定轉換是執行模糊相符還是完全相符。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-145">For example, the FuzzyComparisonFlags property specifies how the transformation compares the string data in a column, and the ExactFuzzy property specifies whether the transformation performs a fuzzy match or an exact match.</span></span>  
  
 <span data-ttu-id="5a1e0-146">您可以透過設定 MaxMemoryUsage 自訂屬性來設定模糊群組轉換所使用的記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-146">The amount of memory that the Fuzzy Grouping transformation uses can be configured by setting the MaxMemoryUsage custom property.</span></span> <span data-ttu-id="5a1e0-147">您可以指定百萬位元組 (MB) 數，或是使用 0 值，讓轉換能夠依據其需求與可用實體記憶體，使用動態的記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-147">You can specify the number of megabytes (MB) or use the value 0 to allow the transformation to use a dynamic amount of memory based on its needs and the physical memory available.</span></span> <span data-ttu-id="5a1e0-148">屬性運算式可以在載入封裝時更新 MaxMemoryUsage 自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-148">The MaxMemoryUsage custom property can be updated by a property expression when the package is loaded.</span></span> <span data-ttu-id="5a1e0-149">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 運算式](../../expressions/integration-services-ssis-expressions.md)、[在封裝中使用屬性運算式](../../expressions/use-property-expressions-in-packages.md)和[轉換自訂屬性](transformation-custom-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-149">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../../expressions/integration-services-ssis-expressions.md), [Use Property Expressions in Packages](../../expressions/use-property-expressions-in-packages.md), and [Transformation Custom Properties](transformation-custom-properties.md).</span></span>  
  
 <span data-ttu-id="5a1e0-150">此轉換有一個輸入和一個輸出。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-150">This transformation has one input and one output.</span></span> <span data-ttu-id="5a1e0-151">它不支援錯誤輸出。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-151">It does not support an error output.</span></span>  
  
## <a name="row-comparison"></a><span data-ttu-id="5a1e0-152">資料列比較</span><span class="sxs-lookup"><span data-stu-id="5a1e0-152">Row Comparison</span></span>  
 <span data-ttu-id="5a1e0-153">設定模糊群組轉換時，您可以指定轉換在比較轉換輸入中的資料列時所使用的比較演算法。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-153">When you configure the Fuzzy Grouping transformation, you can specify the comparison algorithm that the transformation uses to compare rows in the transformation input.</span></span> <span data-ttu-id="5a1e0-154">如果您將 [詳盡] 屬性設為 `true` ，則轉換會比較輸入中的每個資料列與輸入中的每個其他資料列。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-154">If you set the Exhaustive property to `true`, the transformation compares every row in the input to every other row in the input.</span></span> <span data-ttu-id="5a1e0-155">此比較演算法可產生更精確的結果，但很可能會讓轉換的執行速度更慢，除非輸入中的資料列數目較小。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-155">This comparison algorithm may produce more accurate results, but it is likely to make the transformation perform more slowly unless the number of rows in the input is small.</span></span> <span data-ttu-id="5a1e0-156">為避免效能問題，建議您 `true` 只在封裝開發期間將詳盡的屬性設定為。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-156">To avoid performance issues, it is advisable to set the Exhaustive property to `true` only during package development.</span></span>  
  
## <a name="temporary-tables-and-indexes"></a><span data-ttu-id="5a1e0-157">暫存資料表和索引</span><span class="sxs-lookup"><span data-stu-id="5a1e0-157">Temporary Tables and Indexes</span></span>  
 <span data-ttu-id="5a1e0-158">在執行階段，「模糊群組」轉換會在轉換連接到的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料庫中建立暫存物件，例如資料表和索引 (它們的大小可能相當大)。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-158">At run time, the Fuzzy Grouping transformation creates temporary objects such as tables and indexes, potentially of significant size, in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database that the transformation connects to.</span></span> <span data-ttu-id="5a1e0-159">資料表和索引的大小與轉換輸入中的資料列數目和「模糊群組」轉換所建立的 Token 數目成正比。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-159">The size of the tables and indexes are proportional to the number of rows in the transformation input and the number of tokens created by the Fuzzy Grouping transformation.</span></span>  
  
 <span data-ttu-id="5a1e0-160">轉換還會查詢暫存資料表。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-160">The transformation also queries the temporary tables.</span></span> <span data-ttu-id="5a1e0-161">因此，您應該考量將「模糊群組」轉換連接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]的非生產執行個體，特別是當生產伺服器的可用磁碟空間十分有限時。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-161">You should therefore consider connecting the Fuzzy Grouping transformation to a non-production instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], especially if the production server has limited disk space available.</span></span>  
  
 <span data-ttu-id="5a1e0-162">如果此轉換所使用的資料表和索引在本機電腦上，則轉換的效能會有所改進。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-162">The performance of this transformation may improve if the tables and indexes it uses are located on the local computer.</span></span>  
  
## <a name="configuration-of-the-fuzzy-grouping-transformation"></a><span data-ttu-id="5a1e0-163">模糊群組轉換的組態</span><span class="sxs-lookup"><span data-stu-id="5a1e0-163">Configuration of the Fuzzy Grouping Transformation</span></span>  
 <span data-ttu-id="5a1e0-164">您可以透過 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="5a1e0-164">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="5a1e0-165">如需可在 [模糊群組轉換編輯器]\*\*\*\* 對話方塊中設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="5a1e0-165">For more information about the properties that you can set in the **Fuzzy Grouping Transformation Editor** dialog box, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="5a1e0-166">模糊群組轉換編輯器 &#40;連線管理員索引標籤&#41;</span><span class="sxs-lookup"><span data-stu-id="5a1e0-166">Fuzzy Grouping Transformation Editor &#40;Connection Manager Tab&#41;</span></span>](../../fuzzy-grouping-transformation-editor-connection-manager-tab.md)  
  
-   [<span data-ttu-id="5a1e0-167">模糊群組轉換編輯器 &#40;資料行索引標籤&#41;</span><span class="sxs-lookup"><span data-stu-id="5a1e0-167">Fuzzy Grouping Transformation Editor &#40;Columns Tab&#41;</span></span>](../../fuzzy-grouping-transformation-editor-columns-tab.md)  
  
-   [<span data-ttu-id="5a1e0-168">模糊群組轉換編輯器 &#40;進階索引標籤&#41;</span><span class="sxs-lookup"><span data-stu-id="5a1e0-168">Fuzzy Grouping Transformation Editor &#40;Advanced Tab&#41;</span></span>](../../fuzzy-grouping-transformation-editor-advanced-tab.md)  
  
 <span data-ttu-id="5a1e0-169">如需有關可以在 **[進階編輯器]** 對話方塊中或以程式設計方式設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="5a1e0-169">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="5a1e0-170">Common Properties</span><span class="sxs-lookup"><span data-stu-id="5a1e0-170">Common Properties</span></span>](../../common-properties.md)  
  
-   [<span data-ttu-id="5a1e0-171">轉換自訂屬性</span><span class="sxs-lookup"><span data-stu-id="5a1e0-171">Transformation Custom Properties</span></span>](transformation-custom-properties.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="5a1e0-172">相關工作</span><span class="sxs-lookup"><span data-stu-id="5a1e0-172">Related Tasks</span></span>  
 <span data-ttu-id="5a1e0-173">如需有關如何設定此工作屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="5a1e0-173">For details about how to set properties of this task, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="5a1e0-174">使用模糊群組轉換來識別相似的資料列</span><span class="sxs-lookup"><span data-stu-id="5a1e0-174">Identify Similar Data Rows by Using the Fuzzy Grouping Transformation</span></span>](fuzzy-grouping-transformation.md)  
  
-   [<span data-ttu-id="5a1e0-175">設定資料流程元件的屬性</span><span class="sxs-lookup"><span data-stu-id="5a1e0-175">Set the Properties of a Data Flow Component</span></span>](../set-the-properties-of-a-data-flow-component.md)  
  
## <a name="see-also"></a><span data-ttu-id="5a1e0-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a1e0-176">See Also</span></span>  
 <span data-ttu-id="5a1e0-177">[模糊查閱轉換](lookup-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="5a1e0-177">[Fuzzy Lookup Transformation](lookup-transformation.md) </span></span>  
 [<span data-ttu-id="5a1e0-178">Integration Services 轉換</span><span class="sxs-lookup"><span data-stu-id="5a1e0-178">Integration Services Transformations</span></span>](integration-services-transformations.md)  
  
  