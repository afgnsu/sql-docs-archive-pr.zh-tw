---
title: 資料列壓縮實作 | Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- compression [SQL Server], row
- row compression [Database Engine]
ms.assetid: dcd97ac1-1c85-4142-9594-9182e62f6832
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9fd2262ef7e892ef79366dbbf2ed7705a66978b9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599000"
---
# <a name="row-compression-implementation"></a><span data-ttu-id="e7a19-102">資料列壓縮實作</span><span class="sxs-lookup"><span data-stu-id="e7a19-102">Row Compression Implementation</span></span>
  <span data-ttu-id="e7a19-103">本主題摘要說明 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 如何實作資料列壓縮。</span><span class="sxs-lookup"><span data-stu-id="e7a19-103">This topic summarizes how [!INCLUDE[ssDE](../../includes/ssde-md.md)] implements row compression.</span></span> <span data-ttu-id="e7a19-104">這個摘要提供協助您計畫資料所需之儲存空間的基本資訊。</span><span class="sxs-lookup"><span data-stu-id="e7a19-104">This summary provides basic information to help you plan the storage space that you need for your data.</span></span>  
  
 <span data-ttu-id="e7a19-105">啟用壓縮僅會變更與資料類型 (但不與其語法或語意) 相關聯之資料的實體儲存格式。</span><span class="sxs-lookup"><span data-stu-id="e7a19-105">Enabling compression only changes the physical storage format of the data that is associated with a data type but not its syntax or semantics.</span></span> <span data-ttu-id="e7a19-106">當啟用一或多個資料表的壓縮時，不需要變更應用程式。</span><span class="sxs-lookup"><span data-stu-id="e7a19-106">Application changes are not required when one or more tables are enabled for compression.</span></span> <span data-ttu-id="e7a19-107">新的記錄儲存格式具有下列的主要變更：</span><span class="sxs-lookup"><span data-stu-id="e7a19-107">The new record storage format has the following main changes:</span></span>  
  
-   <span data-ttu-id="e7a19-108">降低與記錄相關聯的中繼資料負擔。</span><span class="sxs-lookup"><span data-stu-id="e7a19-108">It reduces the metadata overhead that is associated with the record.</span></span> <span data-ttu-id="e7a19-109">此中繼資料是有關資料行、其長度和位移的資訊。</span><span class="sxs-lookup"><span data-stu-id="e7a19-109">This metadata is information about columns, their lengths and offsets.</span></span> <span data-ttu-id="e7a19-110">在某些情況下，中繼資料負擔可能會比舊的儲存格式還大。</span><span class="sxs-lookup"><span data-stu-id="e7a19-110">In some cases, the metadata overhead might be larger than the old storage format.</span></span>  
  
-   <span data-ttu-id="e7a19-111">針對數值類型 (例如 `integer`、`decimal` 和 `float`) 以及依據數值的類型 (例如 `datetime` 和 `money`) 使用可變長度儲存格式。</span><span class="sxs-lookup"><span data-stu-id="e7a19-111">It uses variable-length storage format for numeric types (for example `integer`, `decimal`, and `float`) and the types that are based on numeric (for example `datetime` and `money`).</span></span>  
  
-   <span data-ttu-id="e7a19-112">使用可變長度格式 (不儲存空白字元) 而儲存固定字元字串。</span><span class="sxs-lookup"><span data-stu-id="e7a19-112">It stores fixed character strings by using variable-length format by not storing the blank characters.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e7a19-113">所有資料類型的 NULL 和 0 值都經過最佳化而不使用任何位元組。</span><span class="sxs-lookup"><span data-stu-id="e7a19-113">NULL and 0 values across all data types are optimized and take no bytes.</span></span>  
  
## <a name="how-row-compression-affects-storage"></a><span data-ttu-id="e7a19-114">資料列壓縮如何影響儲存</span><span class="sxs-lookup"><span data-stu-id="e7a19-114">How Row Compression Affects Storage</span></span>  
 <span data-ttu-id="e7a19-115">下表描述資料列壓縮如何影響 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的現有類型。</span><span class="sxs-lookup"><span data-stu-id="e7a19-115">The following table describes how row compression affects the existing types in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e7a19-116">此表格不包含可藉由使用頁面壓縮而達成的節省量。</span><span class="sxs-lookup"><span data-stu-id="e7a19-116">The table does not include the savings that can be achieved by using page compression.</span></span>  
  
|<span data-ttu-id="e7a19-117">資料類型</span><span class="sxs-lookup"><span data-stu-id="e7a19-117">Data type</span></span>|<span data-ttu-id="e7a19-118">儲存是否受到影響？</span><span class="sxs-lookup"><span data-stu-id="e7a19-118">Is storage affected?</span></span>|<span data-ttu-id="e7a19-119">描述</span><span class="sxs-lookup"><span data-stu-id="e7a19-119">Description</span></span>|  
|---------------|--------------------------|-----------------|  
|`tinyint`|<span data-ttu-id="e7a19-120">否</span><span class="sxs-lookup"><span data-stu-id="e7a19-120">No</span></span>|<span data-ttu-id="e7a19-121">所需的最小儲存區是 1 個位元組。</span><span class="sxs-lookup"><span data-stu-id="e7a19-121">1 byte is the minimum storage needed.</span></span>|  
|`smallint`|<span data-ttu-id="e7a19-122">是</span><span class="sxs-lookup"><span data-stu-id="e7a19-122">Yes</span></span>|<span data-ttu-id="e7a19-123">如果 1 個位元組能容納此值，只會使用 1 個位元組。</span><span class="sxs-lookup"><span data-stu-id="e7a19-123">If the value fits in 1 byte, only 1 byte will be used.</span></span>|  
|`int`|<span data-ttu-id="e7a19-124">是</span><span class="sxs-lookup"><span data-stu-id="e7a19-124">Yes</span></span>|<span data-ttu-id="e7a19-125">僅使用所需的位元組。</span><span class="sxs-lookup"><span data-stu-id="e7a19-125">Uses only the bytes that are needed.</span></span> <span data-ttu-id="e7a19-126">例如，如果值可以儲存在 1 個位元組內，則儲存只會使用 1 個位元組。</span><span class="sxs-lookup"><span data-stu-id="e7a19-126">For example, if a value can be stored in 1 byte, storage will take only 1 byte.</span></span>|  
|`bigint`|<span data-ttu-id="e7a19-127">是</span><span class="sxs-lookup"><span data-stu-id="e7a19-127">Yes</span></span>|<span data-ttu-id="e7a19-128">僅使用所需的位元組。</span><span class="sxs-lookup"><span data-stu-id="e7a19-128">Uses only the bytes that are needed.</span></span> <span data-ttu-id="e7a19-129">例如，如果值可以儲存在 1 個位元組內，則儲存只會使用 1 個位元組。</span><span class="sxs-lookup"><span data-stu-id="e7a19-129">For example, if a value can be stored in 1 byte, storage will take only 1 byte.</span></span>|  
|`decimal`|<span data-ttu-id="e7a19-130">是</span><span class="sxs-lookup"><span data-stu-id="e7a19-130">Yes</span></span>|<span data-ttu-id="e7a19-131">此儲存與 Vardecimal 儲存格式完全相同。</span><span class="sxs-lookup"><span data-stu-id="e7a19-131">This storage is exactly same as the vardecimal storage format.</span></span>|  
|`numeric`|<span data-ttu-id="e7a19-132">是</span><span class="sxs-lookup"><span data-stu-id="e7a19-132">Yes</span></span>|<span data-ttu-id="e7a19-133">此儲存與 Vardecimal 儲存格式完全相同。</span><span class="sxs-lookup"><span data-stu-id="e7a19-133">This storage is exactly same as the vardecimal storage format.</span></span>|  
|`bit`|<span data-ttu-id="e7a19-134">是</span><span class="sxs-lookup"><span data-stu-id="e7a19-134">Yes</span></span>|<span data-ttu-id="e7a19-135">中繼資料負荷將此設為 4 個位元。</span><span class="sxs-lookup"><span data-stu-id="e7a19-135">The metadata overhead brings this to 4 bits.</span></span>|  
|`smallmoney`|<span data-ttu-id="e7a19-136">是</span><span class="sxs-lookup"><span data-stu-id="e7a19-136">Yes</span></span>|<span data-ttu-id="e7a19-137">藉由使用 4 位元組整數來使用整數資料表示。</span><span class="sxs-lookup"><span data-stu-id="e7a19-137">Uses the integer data representation by using a 4-byte integer.</span></span> <span data-ttu-id="e7a19-138">貨幣值會乘以 10000，再移除小數點之後的任何數字以儲存產生的整數值。</span><span class="sxs-lookup"><span data-stu-id="e7a19-138">Currency value is multiplied by 10000 and the resulting integer value is stored by removing any digits after the decimal point.</span></span> <span data-ttu-id="e7a19-139">此類型的儲存最佳化與整數類型類似。</span><span class="sxs-lookup"><span data-stu-id="e7a19-139">This type has a storage optimization similar to that for integer types.</span></span>|  
|`money`|<span data-ttu-id="e7a19-140">是</span><span class="sxs-lookup"><span data-stu-id="e7a19-140">Yes</span></span>|<span data-ttu-id="e7a19-141">藉由使用 8 位元組整數來使用整數資料表示。</span><span class="sxs-lookup"><span data-stu-id="e7a19-141">Uses the integer data representation by using an 8-byte integer.</span></span> <span data-ttu-id="e7a19-142">貨幣值會乘以 10000，再移除小數點之後的任何數字以儲存產生的整數值。</span><span class="sxs-lookup"><span data-stu-id="e7a19-142">Currency value is multiplied by 10000 and the resulting integer value is stored by removing any digits after the decimal point.</span></span> <span data-ttu-id="e7a19-143">此類型的範圍比 `smallmoney` 大。</span><span class="sxs-lookup"><span data-stu-id="e7a19-143">This type has a larger range than `smallmoney`.</span></span> <span data-ttu-id="e7a19-144">此類型的儲存最佳化與整數類型類似。</span><span class="sxs-lookup"><span data-stu-id="e7a19-144">This type has a storage optimization similar to that for integer types.</span></span>|  
|`float`|<span data-ttu-id="e7a19-145">是</span><span class="sxs-lookup"><span data-stu-id="e7a19-145">Yes</span></span>|<span data-ttu-id="e7a19-146">將不會儲存最小顯著性位元組為零的項目。</span><span class="sxs-lookup"><span data-stu-id="e7a19-146">Least significant bytes with zeros are not stored.</span></span> <span data-ttu-id="e7a19-147">`float` 壓縮主要適用於尾數中的非小數值。</span><span class="sxs-lookup"><span data-stu-id="e7a19-147">`float` compression is applicable mostly for nonfractional values in mantissa.</span></span>|  
|`real`|<span data-ttu-id="e7a19-148">是</span><span class="sxs-lookup"><span data-stu-id="e7a19-148">Yes</span></span>|<span data-ttu-id="e7a19-149">將不會儲存最小顯著性位元組為零的項目。</span><span class="sxs-lookup"><span data-stu-id="e7a19-149">Least significant bytes with zeros are not stored.</span></span> <span data-ttu-id="e7a19-150">`real` 壓縮主要適用於尾數中的非小數值。</span><span class="sxs-lookup"><span data-stu-id="e7a19-150">`real` compression is applicable mostly for nonfractional values in mantissa.</span></span>|  
|`smalldatetime`|<span data-ttu-id="e7a19-151">否</span><span class="sxs-lookup"><span data-stu-id="e7a19-151">No</span></span>|<span data-ttu-id="e7a19-152">藉由使用兩個 2 位元組整數來使用整數資料表示法。</span><span class="sxs-lookup"><span data-stu-id="e7a19-152">Uses the integer data representation by using two 2-byte integers.</span></span> <span data-ttu-id="e7a19-153">日期會使用 2 個位元組，</span><span class="sxs-lookup"><span data-stu-id="e7a19-153">The date takes 2 bytes.</span></span> <span data-ttu-id="e7a19-154">是 1901 年 1 月 1 日之後的日數。</span><span class="sxs-lookup"><span data-stu-id="e7a19-154">It is the number of days since 1/1/1901.</span></span> <span data-ttu-id="e7a19-155">這需要 2 個位元組，從 1902 開始；</span><span class="sxs-lookup"><span data-stu-id="e7a19-155">This needs 2 bytes starting from 1902.</span></span> <span data-ttu-id="e7a19-156">因此在該時間點後就無法進行節省。</span><span class="sxs-lookup"><span data-stu-id="e7a19-156">Therefore, there is no savings after that point.</span></span><br /><br /> <span data-ttu-id="e7a19-157">時間是午夜之後的分鐘數。</span><span class="sxs-lookup"><span data-stu-id="e7a19-157">The time is the number of minutes since midnight.</span></span> <span data-ttu-id="e7a19-158">稍微超過 4AM 的時間值會開始使用第二個位元組。</span><span class="sxs-lookup"><span data-stu-id="e7a19-158">Time values that are slightly past 4AM start to use the second byte.</span></span><br /><br /> <span data-ttu-id="e7a19-159">如果 `smalldatetime` 只會用來表示日期 (常見的情況)，則時間是 0.0。</span><span class="sxs-lookup"><span data-stu-id="e7a19-159">If a `smalldatetime` is only used to represent a date (a common case), the time is 0.0.</span></span> <span data-ttu-id="e7a19-160">壓縮會針對資料列壓縮以最大顯著性位元組格式儲存時間而節省 2 個位元組。</span><span class="sxs-lookup"><span data-stu-id="e7a19-160">Compression saves 2 bytes by storing the time in most significant byte format for row compression.</span></span>|  
|`datetime`|<span data-ttu-id="e7a19-161">是</span><span class="sxs-lookup"><span data-stu-id="e7a19-161">Yes</span></span>|<span data-ttu-id="e7a19-162">藉由使用兩個 4 位元組整數來使用整數資料表示。</span><span class="sxs-lookup"><span data-stu-id="e7a19-162">Uses the integer data representation by using two 4-byte integers.</span></span> <span data-ttu-id="e7a19-163">整數值代表日數，基底日期則是 1900 年 1 月 1 日。</span><span class="sxs-lookup"><span data-stu-id="e7a19-163">The integer value represents the number of days with base date of 1/1/1900.</span></span> <span data-ttu-id="e7a19-164">第一個 2 位元組最多可代表到 2079 年。</span><span class="sxs-lookup"><span data-stu-id="e7a19-164">The first 2 bytes can represent up to the year 2079.</span></span> <span data-ttu-id="e7a19-165">在該時間點之前，此處的壓縮一定可以節省 2 個位元組。</span><span class="sxs-lookup"><span data-stu-id="e7a19-165">Compression can always save 2 bytes here until that point.</span></span> <span data-ttu-id="e7a19-166">每個整數值都代表 3.33 毫秒。</span><span class="sxs-lookup"><span data-stu-id="e7a19-166">Each integer value represents 3.33 milliseconds.</span></span> <span data-ttu-id="e7a19-167">壓縮在第一個五分鐘內就會用盡第一個 2 個位元組，而需要在 4PM 之後使用第四個位元組。</span><span class="sxs-lookup"><span data-stu-id="e7a19-167">Compression exhausts the first 2 bytes in first five minutes and needs the fourth byte after 4PM.</span></span> <span data-ttu-id="e7a19-168">因此，在 4PM 之後僅能節省 1 個位元組。</span><span class="sxs-lookup"><span data-stu-id="e7a19-168">Therefore, compression can save only 1 byte after 4PM.</span></span> <span data-ttu-id="e7a19-169">當 `datetime` 像任何其他整數一樣進行壓縮時，壓縮可以在日期中節省 2 個位元組。</span><span class="sxs-lookup"><span data-stu-id="e7a19-169">When `datetime` is compressed like any other integer, compression saves 2 bytes in the date.</span></span>|  
|`date`|<span data-ttu-id="e7a19-170">否</span><span class="sxs-lookup"><span data-stu-id="e7a19-170">No</span></span>|<span data-ttu-id="e7a19-171">藉由使用 3 個位元組來使用整數資料表示法。</span><span class="sxs-lookup"><span data-stu-id="e7a19-171">Uses the integer data representation by using 3 bytes.</span></span> <span data-ttu-id="e7a19-172">這代表從 0001 年 1 月 1 日開始的日期。</span><span class="sxs-lookup"><span data-stu-id="e7a19-172">This represents the date from 1/1/0001.</span></span> <span data-ttu-id="e7a19-173">對於現代的日期而言，資料列壓縮會使用所有 3 個位元組。</span><span class="sxs-lookup"><span data-stu-id="e7a19-173">For contemporary dates, row compression uses all 3 bytes.</span></span> <span data-ttu-id="e7a19-174">如此不會達成任何節省量。</span><span class="sxs-lookup"><span data-stu-id="e7a19-174">This achieves no savings.</span></span>|  
|`time`|<span data-ttu-id="e7a19-175">否</span><span class="sxs-lookup"><span data-stu-id="e7a19-175">No</span></span>|<span data-ttu-id="e7a19-176">藉由使用 3 到 6 個位元組來使用整數資料表示法。</span><span class="sxs-lookup"><span data-stu-id="e7a19-176">Uses the integer data representation by using 3 to 6 bytes.</span></span> <span data-ttu-id="e7a19-177">有多個以 0 到 9 的有效位數可以使用 3 到 6 個位元組。</span><span class="sxs-lookup"><span data-stu-id="e7a19-177">There are various precisions that start with 0 to 9 that can take 3 to 6 bytes.</span></span> <span data-ttu-id="e7a19-178">請注意，資料列壓縮的儲存沒有變更。</span><span class="sxs-lookup"><span data-stu-id="e7a19-178">Note that there is no change in storage for row compression.</span></span> <span data-ttu-id="e7a19-179">整體而言，無法預期從壓縮 `time` 資料類型達到很大的節省量。</span><span class="sxs-lookup"><span data-stu-id="e7a19-179">Overall, not much savings can be expected from compressing the `time` data type.</span></span> <span data-ttu-id="e7a19-180">壓縮空間的用法如下所示：</span><span class="sxs-lookup"><span data-stu-id="e7a19-180">Compressed space is used as follows:</span></span><br /><br /> <span data-ttu-id="e7a19-181">Precision = 0。</span><span class="sxs-lookup"><span data-stu-id="e7a19-181">Precision = 0.</span></span> <span data-ttu-id="e7a19-182">Bytes = 3。</span><span class="sxs-lookup"><span data-stu-id="e7a19-182">Bytes = 3.</span></span> <span data-ttu-id="e7a19-183">每個整數值都代表一秒。</span><span class="sxs-lookup"><span data-stu-id="e7a19-183">Each integer value represents a second.</span></span> <span data-ttu-id="e7a19-184">壓縮可藉由使用 2 個位元組而最多代表到 6PM 的時間，因而可能節省 1 個位元組。</span><span class="sxs-lookup"><span data-stu-id="e7a19-184">Compression can represent time up to 6PM by using 2 bytes, potentially saving 1 byte.</span></span><br /><br /> <span data-ttu-id="e7a19-185">Precision = 1。</span><span class="sxs-lookup"><span data-stu-id="e7a19-185">Precision = 1.</span></span> <span data-ttu-id="e7a19-186">Bytes = 3。</span><span class="sxs-lookup"><span data-stu-id="e7a19-186">Bytes = 3.</span></span> <span data-ttu-id="e7a19-187">每個整數值都代表 1/10 秒。</span><span class="sxs-lookup"><span data-stu-id="e7a19-187">Each integer value represents 1/10 seconds.</span></span> <span data-ttu-id="e7a19-188">壓縮在 2AM 之前會使用第三個位元組。</span><span class="sxs-lookup"><span data-stu-id="e7a19-188">Compression uses the third byte before 2AM.</span></span> <span data-ttu-id="e7a19-189">產生的節省量很少。</span><span class="sxs-lookup"><span data-stu-id="e7a19-189">Results in little savings.</span></span><br /><br /> <span data-ttu-id="e7a19-190">Precision = 2。</span><span class="sxs-lookup"><span data-stu-id="e7a19-190">Precision = 2.</span></span> <span data-ttu-id="e7a19-191">Bytes = 3。</span><span class="sxs-lookup"><span data-stu-id="e7a19-191">Bytes = 3.</span></span> <span data-ttu-id="e7a19-192">與前例類似，不太可能達到節省量。</span><span class="sxs-lookup"><span data-stu-id="e7a19-192">Similar to the previous case, it is unlikely to achieve savings.</span></span><br /><br /> <span data-ttu-id="e7a19-193">Precision = 3。</span><span class="sxs-lookup"><span data-stu-id="e7a19-193">Precision = 3.</span></span> <span data-ttu-id="e7a19-194">Bytes = 4。</span><span class="sxs-lookup"><span data-stu-id="e7a19-194">Bytes = 4.</span></span> <span data-ttu-id="e7a19-195">因為在 5AM 之前就會使用了第一個 3 位元組，所以節省的量很少。</span><span class="sxs-lookup"><span data-stu-id="e7a19-195">Because the first 3 bytes are taken by 5AM, achieves little savings.</span></span><br /><br /> <span data-ttu-id="e7a19-196">Precision = 4。</span><span class="sxs-lookup"><span data-stu-id="e7a19-196">Precision = 4.</span></span> <span data-ttu-id="e7a19-197">Bytes = 4。</span><span class="sxs-lookup"><span data-stu-id="e7a19-197">Bytes = 4.</span></span> <span data-ttu-id="e7a19-198">在第一個 27 秒內就會使用第一個 3 位元組。</span><span class="sxs-lookup"><span data-stu-id="e7a19-198">The first 3 bytes are taken in the first 27 seconds.</span></span> <span data-ttu-id="e7a19-199">不預期有任何節省量。</span><span class="sxs-lookup"><span data-stu-id="e7a19-199">No savings are expected.</span></span><br /><br /> <span data-ttu-id="e7a19-200">Precision = 5，Bytes = 5。</span><span class="sxs-lookup"><span data-stu-id="e7a19-200">Precision = 5, Bytes = 5.</span></span> <span data-ttu-id="e7a19-201">在中午 12 點之後會使用第五個位元組。</span><span class="sxs-lookup"><span data-stu-id="e7a19-201">Fifth byte will be used after 12-noon.</span></span><br /><br /> <span data-ttu-id="e7a19-202">Precision = 6 和 7，Bytes = 5。</span><span class="sxs-lookup"><span data-stu-id="e7a19-202">Precision = 6 and 7, Bytes = 5.</span></span> <span data-ttu-id="e7a19-203">不會達到任何節省量。</span><span class="sxs-lookup"><span data-stu-id="e7a19-203">Achieves no savings.</span></span><br /><br /> <span data-ttu-id="e7a19-204">Precision = 8，Bytes = 6。</span><span class="sxs-lookup"><span data-stu-id="e7a19-204">Precision = 8, Bytes = 6.</span></span> <span data-ttu-id="e7a19-205">在 3AM 之後會使用第六個位元組。</span><span class="sxs-lookup"><span data-stu-id="e7a19-205">Sixth byte will be used after 3AM.</span></span>|  
|`datetime2`|<span data-ttu-id="e7a19-206">是</span><span class="sxs-lookup"><span data-stu-id="e7a19-206">Yes</span></span>|<span data-ttu-id="e7a19-207">藉由使用 6 到 9 個位元組來使用整數資料表示。</span><span class="sxs-lookup"><span data-stu-id="e7a19-207">Uses the integer data representation by using 6 to 9 bytes.</span></span> <span data-ttu-id="e7a19-208">第一個 4 位元組代表日期。</span><span class="sxs-lookup"><span data-stu-id="e7a19-208">The first 4 bytes represent the date.</span></span> <span data-ttu-id="e7a19-209">由時間所使用的位元組會依所指定時間的有效位數而定。</span><span class="sxs-lookup"><span data-stu-id="e7a19-209">The bytes taken by the time will depend on the precision of the time that is specified.</span></span><br /><br /> <span data-ttu-id="e7a19-210">整數值代表自 0001 年 1 月 1 日開始的日數，上限則是 9999 年 12 月 31 日。</span><span class="sxs-lookup"><span data-stu-id="e7a19-210">The integer value represents the number of days since 1/1/0001 with an upper bound of 12/31/9999.</span></span> <span data-ttu-id="e7a19-211">為了代表 2005 年中的日期，壓縮會使用 3 個位元組。</span><span class="sxs-lookup"><span data-stu-id="e7a19-211">To represent a date in year 2005, compression takes 3 bytes.</span></span><br /><br /> <span data-ttu-id="e7a19-212">不會節省任何時間，因為它針對不同的時間有效位數而允許 2 到 4 個位元組。</span><span class="sxs-lookup"><span data-stu-id="e7a19-212">There is no savings on time because it allows for 2 to 4 bytes for various time precisions.</span></span> <span data-ttu-id="e7a19-213">因此，對於一秒鐘的時間有效位數而言，壓縮會為時間使用 2 個位元組，而在 255 秒之後使用第二個位元組。</span><span class="sxs-lookup"><span data-stu-id="e7a19-213">Therefore, for one-second time precision, compression uses 2 bytes for time, which takes the second byte after 255 seconds.</span></span>|  
|`datetimeoffset`|<span data-ttu-id="e7a19-214">是</span><span class="sxs-lookup"><span data-stu-id="e7a19-214">Yes</span></span>|<span data-ttu-id="e7a19-215">類似 `datetime2`，但此格式 (HH:MM) 的時區有 2 個位元組。</span><span class="sxs-lookup"><span data-stu-id="e7a19-215">Resembles `datetime2`, except that there are 2 bytes of time zone of the format (HH:MM).</span></span><br /><br /> <span data-ttu-id="e7a19-216">與 `datetime2` 類似，壓縮可節省 2 個位元組。</span><span class="sxs-lookup"><span data-stu-id="e7a19-216">Like `datetime2`, compression can save 2 bytes.</span></span><br /><br /> <span data-ttu-id="e7a19-217">對於時區值，MM 值在多數情況下可能是 0。</span><span class="sxs-lookup"><span data-stu-id="e7a19-217">For time zone values, MM value might be 0 for most cases.</span></span> <span data-ttu-id="e7a19-218">因此，壓縮可能可以節省 1 個位元組。</span><span class="sxs-lookup"><span data-stu-id="e7a19-218">Therefore, compression can possibly save 1 byte.</span></span><br /><br /> <span data-ttu-id="e7a19-219">資料列壓縮的儲存沒有變更。</span><span class="sxs-lookup"><span data-stu-id="e7a19-219">There are no changes in storage for row compression.</span></span>|  
|`char`|<span data-ttu-id="e7a19-220">是</span><span class="sxs-lookup"><span data-stu-id="e7a19-220">Yes</span></span>|<span data-ttu-id="e7a19-221">會移除尾端填補字元。</span><span class="sxs-lookup"><span data-stu-id="e7a19-221">Trailing padding characters are removed.</span></span> <span data-ttu-id="e7a19-222">請注意，不論使用的定序為何， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 都會插入相同的填補字元。</span><span class="sxs-lookup"><span data-stu-id="e7a19-222">Note that the [!INCLUDE[ssDE](../../includes/ssde-md.md)] inserts the same padding character regardless of the collation that is used.</span></span>|  
|`varchar`|<span data-ttu-id="e7a19-223">否</span><span class="sxs-lookup"><span data-stu-id="e7a19-223">No</span></span>|<span data-ttu-id="e7a19-224">沒有影響。</span><span class="sxs-lookup"><span data-stu-id="e7a19-224">No effect.</span></span>|  
|`text`|<span data-ttu-id="e7a19-225">否</span><span class="sxs-lookup"><span data-stu-id="e7a19-225">No</span></span>|<span data-ttu-id="e7a19-226">沒有影響。</span><span class="sxs-lookup"><span data-stu-id="e7a19-226">No effect.</span></span>|  
|`nchar`|<span data-ttu-id="e7a19-227">是</span><span class="sxs-lookup"><span data-stu-id="e7a19-227">Yes</span></span>|<span data-ttu-id="e7a19-228">會移除尾端填補字元。</span><span class="sxs-lookup"><span data-stu-id="e7a19-228">Trailing padding characters are removed.</span></span> <span data-ttu-id="e7a19-229">請注意，不論使用的定序為何， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 都會插入相同的填補字元。</span><span class="sxs-lookup"><span data-stu-id="e7a19-229">Note that the [!INCLUDE[ssDE](../../includes/ssde-md.md)] inserts the same padding character regardless of the collation that is used.</span></span>|  
|`nvarchar`|<span data-ttu-id="e7a19-230">否</span><span class="sxs-lookup"><span data-stu-id="e7a19-230">No</span></span>|<span data-ttu-id="e7a19-231">沒有影響。</span><span class="sxs-lookup"><span data-stu-id="e7a19-231">No effect.</span></span>|  
|`ntext`|<span data-ttu-id="e7a19-232">否</span><span class="sxs-lookup"><span data-stu-id="e7a19-232">No</span></span>|<span data-ttu-id="e7a19-233">沒有影響。</span><span class="sxs-lookup"><span data-stu-id="e7a19-233">No effect.</span></span>|  
|`binary`|<span data-ttu-id="e7a19-234">是</span><span class="sxs-lookup"><span data-stu-id="e7a19-234">Yes</span></span>|<span data-ttu-id="e7a19-235">會移除尾端的零。</span><span class="sxs-lookup"><span data-stu-id="e7a19-235">Trailing zeros are removed.</span></span>|  
|`varbinary`|<span data-ttu-id="e7a19-236">否</span><span class="sxs-lookup"><span data-stu-id="e7a19-236">No</span></span>|<span data-ttu-id="e7a19-237">沒有影響。</span><span class="sxs-lookup"><span data-stu-id="e7a19-237">No effect.</span></span>|  
|`image`|<span data-ttu-id="e7a19-238">否</span><span class="sxs-lookup"><span data-stu-id="e7a19-238">No</span></span>|<span data-ttu-id="e7a19-239">沒有影響。</span><span class="sxs-lookup"><span data-stu-id="e7a19-239">No effect.</span></span>|  
|`cursor`|<span data-ttu-id="e7a19-240">否</span><span class="sxs-lookup"><span data-stu-id="e7a19-240">No</span></span>|<span data-ttu-id="e7a19-241">沒有影響。</span><span class="sxs-lookup"><span data-stu-id="e7a19-241">No effect.</span></span>|  
|`timestamp` / `rowversion`|<span data-ttu-id="e7a19-242">是</span><span class="sxs-lookup"><span data-stu-id="e7a19-242">Yes</span></span>|<span data-ttu-id="e7a19-243">藉由 8 個位元組以使用整數資料表示法。</span><span class="sxs-lookup"><span data-stu-id="e7a19-243">Uses the integer data representation by using 8 bytes.</span></span> <span data-ttu-id="e7a19-244">有針對每個資料庫維護時間戳記計數器，且其值從 0 開始。</span><span class="sxs-lookup"><span data-stu-id="e7a19-244">There is a timestamp counter that is maintained for each database, and its value starts from 0.</span></span> <span data-ttu-id="e7a19-245">這可以像任何其他整數值一般進行壓縮。</span><span class="sxs-lookup"><span data-stu-id="e7a19-245">This can be compressed like any other integer value.</span></span>|  
|`sql_variant`|<span data-ttu-id="e7a19-246">否</span><span class="sxs-lookup"><span data-stu-id="e7a19-246">No</span></span>|<span data-ttu-id="e7a19-247">沒有影響。</span><span class="sxs-lookup"><span data-stu-id="e7a19-247">No effect.</span></span>|  
|`uniqueidentifier`|<span data-ttu-id="e7a19-248">否</span><span class="sxs-lookup"><span data-stu-id="e7a19-248">No</span></span>|<span data-ttu-id="e7a19-249">沒有影響。</span><span class="sxs-lookup"><span data-stu-id="e7a19-249">No effect.</span></span>|  
|`table`|<span data-ttu-id="e7a19-250">否</span><span class="sxs-lookup"><span data-stu-id="e7a19-250">No</span></span>|<span data-ttu-id="e7a19-251">沒有影響。</span><span class="sxs-lookup"><span data-stu-id="e7a19-251">No effect.</span></span>|  
|`xml`|<span data-ttu-id="e7a19-252">否</span><span class="sxs-lookup"><span data-stu-id="e7a19-252">No</span></span>|<span data-ttu-id="e7a19-253">沒有影響。</span><span class="sxs-lookup"><span data-stu-id="e7a19-253">No effect.</span></span>|  
|<span data-ttu-id="e7a19-254">使用者定義型別</span><span class="sxs-lookup"><span data-stu-id="e7a19-254">User-defined types</span></span>|<span data-ttu-id="e7a19-255">否</span><span class="sxs-lookup"><span data-stu-id="e7a19-255">No</span></span>|<span data-ttu-id="e7a19-256">這在內部表示為 `varbinary`。</span><span class="sxs-lookup"><span data-stu-id="e7a19-256">This is represented internally as `varbinary`.</span></span>|  
|<span data-ttu-id="e7a19-257">FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="e7a19-257">FILESTREAM</span></span>|<span data-ttu-id="e7a19-258">否</span><span class="sxs-lookup"><span data-stu-id="e7a19-258">No</span></span>|<span data-ttu-id="e7a19-259">這在內部表示為 `varbinary`。</span><span class="sxs-lookup"><span data-stu-id="e7a19-259">This is represented internally as `varbinary`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e7a19-260">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7a19-260">See Also</span></span>  
 <span data-ttu-id="e7a19-261">[資料壓縮](data-compression.md) </span><span class="sxs-lookup"><span data-stu-id="e7a19-261">[Data Compression](data-compression.md) </span></span>  
 [<span data-ttu-id="e7a19-262">頁面壓縮實作</span><span class="sxs-lookup"><span data-stu-id="e7a19-262">Page Compression Implementation</span></span>](page-compression-implementation.md)  
  
  