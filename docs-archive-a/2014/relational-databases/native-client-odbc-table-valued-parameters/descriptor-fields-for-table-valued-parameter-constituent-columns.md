---
title: 資料表值參數組成資料行的描述項欄位 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), descriptor fields for constituent columns
ms.assetid: 944b3968-fd47-4847-98d6-b87e8ef2acdc
author: rothja
ms.author: jroth
ms.openlocfilehash: 7474a4a80309f6ce9754fefabfd0080c89f803b3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598861"
---
# <a name="descriptor-fields-for-table-valued-parameter-constituent-columns"></a><span data-ttu-id="5459b-102">資料表值參數組成資料行的描述項欄位</span><span class="sxs-lookup"><span data-stu-id="5459b-102">Descriptor Fields for Table-Valued Parameter Constituent Columns</span></span>
  <span data-ttu-id="5459b-103">本節中所述的資料表值參數描述項欄位是使用[SQLSetDescField](../native-client-odbc-api/sqlsetdescfield.md)和[SQLSetDescField](../native-client-odbc-api/sqlsetdescfield.md)來操作，並搭配執行參數描述元的控制碼 (IPD) 。</span><span class="sxs-lookup"><span data-stu-id="5459b-103">The table-valued parameter descriptor fields described in this section are manipulated by using [SQLSetDescField](../native-client-odbc-api/sqlsetdescfield.md) and [SQLSetDescField](../native-client-odbc-api/sqlsetdescfield.md) with the handle for the implementation parameter descriptor (IPD).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5459b-104">備註</span><span class="sxs-lookup"><span data-stu-id="5459b-104">Remarks</span></span>  
 <span data-ttu-id="5459b-105">SQL_DESC_AUTO_UNIQUE_VALUE 用於資料表值參數與其他功能。</span><span class="sxs-lookup"><span data-stu-id="5459b-105">SQL_DESC_AUTO_UNIQUE_VALUE is used for table-valued parameters as well as other features.</span></span>  
  
|<span data-ttu-id="5459b-106">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="5459b-106">Attribute name</span></span>|<span data-ttu-id="5459b-107">類型</span><span class="sxs-lookup"><span data-stu-id="5459b-107">Type</span></span>|<span data-ttu-id="5459b-108">描述</span><span class="sxs-lookup"><span data-stu-id="5459b-108">Description</span></span>|  
|--------------------|----------|-----------------|  
|<span data-ttu-id="5459b-109">SQL_DESC_AUTO_UNIQUE_VALUE</span><span class="sxs-lookup"><span data-stu-id="5459b-109">SQL_DESC_AUTO_UNIQUE_VALUE</span></span>|<span data-ttu-id="5459b-110">SQLINTEGER</span><span class="sxs-lookup"><span data-stu-id="5459b-110">SQLINTEGER</span></span>|<span data-ttu-id="5459b-111">SQL_TRUE 表示此資料行是識別資料行。</span><span class="sxs-lookup"><span data-stu-id="5459b-111">SQL_TRUE indicates that this column is an identity column.</span></span><br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="5459b-112">可以使用此資訊來優化效能，但不需要應用程式來設定識別欄位。</span><span class="sxs-lookup"><span data-stu-id="5459b-112">can use this information to optimize performance, but applications are not required to set it for identity columns.</span></span>|  
  
 <span data-ttu-id="5459b-113">下列屬性會加入到應用程式參數描述項 (APD) 和實作參數描述項 (IPD) 的所有參數類型中：</span><span class="sxs-lookup"><span data-stu-id="5459b-113">The following attributes are added to all parameter types in the application parameter descriptor (APD) and implementation parameter descriptor (IPD):</span></span>  
  
|<span data-ttu-id="5459b-114">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="5459b-114">Attribute name</span></span>|<span data-ttu-id="5459b-115">類型</span><span class="sxs-lookup"><span data-stu-id="5459b-115">Type</span></span>|<span data-ttu-id="5459b-116">描述</span><span class="sxs-lookup"><span data-stu-id="5459b-116">Description</span></span>|  
|--------------------|----------|-----------------|  
|<span data-ttu-id="5459b-117">SQL_CA_SS_COLUMN_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="5459b-117">SQL_CA_SS_COLUMN_COMPUTED</span></span>|<span data-ttu-id="5459b-118">SQLSMALLINT</span><span class="sxs-lookup"><span data-stu-id="5459b-118">SQLSMALLINT</span></span>|<span data-ttu-id="5459b-119">SQL_TRUE 表示此資料行是計算資料行。</span><span class="sxs-lookup"><span data-stu-id="5459b-119">SQL_TRUE indicates that this column is computed.</span></span><br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="5459b-120">可以使用這種資訊來優化效能，但是應用程式不需要針對計算資料行設定它。</span><span class="sxs-lookup"><span data-stu-id="5459b-120">can use this information to optimize performance, but applications are not required to set it for computed columns.</span></span><br /><br /> <span data-ttu-id="5459b-121">若是非資料表值參數資料行的繫結，會忽略此屬性。</span><span class="sxs-lookup"><span data-stu-id="5459b-121">This attribute is ignored for bindings that are not table-valued parameter columns.</span></span>|  
|<span data-ttu-id="5459b-122">SQL_CA_SS_COLUMN_IN_UNIQUE_KEY</span><span class="sxs-lookup"><span data-stu-id="5459b-122">SQL_CA_SS_COLUMN_IN_UNIQUE_KEY</span></span>|<span data-ttu-id="5459b-123">SQLSMALLINT</span><span class="sxs-lookup"><span data-stu-id="5459b-123">SQLSMALLINT</span></span>|<span data-ttu-id="5459b-124">SQL_TRUE 表示資料表值參數資料行參與唯一的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="5459b-124">SQL_TRUE indicates that a table-valued parameter column participates in a unique key.</span></span> <span data-ttu-id="5459b-125">這會使查詢效能更好。</span><span class="sxs-lookup"><span data-stu-id="5459b-125">This can result in better query performance.</span></span> <span data-ttu-id="5459b-126">若是非資料表值參數資料行的繫結，會忽略此屬性。</span><span class="sxs-lookup"><span data-stu-id="5459b-126">This attribute is ignored for bindings that are not table-valued parameter columns.</span></span>|  
|<span data-ttu-id="5459b-127">SQL_CA_SS_COLUMN_SORT_ORDER</span><span class="sxs-lookup"><span data-stu-id="5459b-127">SQL_CA_SS_COLUMN_SORT_ORDER</span></span>|<span data-ttu-id="5459b-128">SQLSMALLINT</span><span class="sxs-lookup"><span data-stu-id="5459b-128">SQLSMALLINT</span></span>|<span data-ttu-id="5459b-129">表示資料表值參數資料行的排序次序。</span><span class="sxs-lookup"><span data-stu-id="5459b-129">Indicates the sort order of a table-valued parameter column.</span></span> <span data-ttu-id="5459b-130">這會使查詢效能更好。</span><span class="sxs-lookup"><span data-stu-id="5459b-130">This can result in better query performance.</span></span> <span data-ttu-id="5459b-131">若是非資料表值參數資料行的繫結，會忽略此屬性。</span><span class="sxs-lookup"><span data-stu-id="5459b-131">This attribute is ignored for bindings that are not table-valued parameter columns.</span></span> <span data-ttu-id="5459b-132">以下是可能的值：</span><span class="sxs-lookup"><span data-stu-id="5459b-132">The possible values are the following:</span></span><br /><br /> <span data-ttu-id="5459b-133">-SQL_SS_ASCENDING_ORDER</span><span class="sxs-lookup"><span data-stu-id="5459b-133">-   SQL_SS_ASCENDING_ORDER</span></span><br /><span data-ttu-id="5459b-134">-SQL_SS_DESCENDING_ORDER</span><span class="sxs-lookup"><span data-stu-id="5459b-134">-   SQL_SS_DESCENDING_ORDER</span></span><br /><span data-ttu-id="5459b-135">-SQL_SS_ORDER_UNSPECIFIED</span><span class="sxs-lookup"><span data-stu-id="5459b-135">-   SQL_SS_ORDER_UNSPECIFIED</span></span><br /><br /> <span data-ttu-id="5459b-136">SQL_SS_ASCENDING_ORDER 和 SQL_SS_DESCENDING_ORDER 以外的值會產生 SQLSTATE HY024 的錯誤，並出現訊息「屬性值無效」，而且這些值會視為 SQL_SS_ORDER_UNSPECIFIED，也就是此屬性的預設值。</span><span class="sxs-lookup"><span data-stu-id="5459b-136">Values other than SQL_SS_ASCENDING_ORDER and SQL_SS_DESCENDING_ORDER generate an error with SQLSTATE HY024 and message 'Invalid attribute value' and are treated as SQL_SS_ORDER_UNSPECIFIED, which is the default value for this attribute.</span></span>|  
|<span data-ttu-id="5459b-137">SQL_CA_SS_COLUMN_SORT_ORDINAL</span><span class="sxs-lookup"><span data-stu-id="5459b-137">SQL_CA_SS_COLUMN_SORT_ORDINAL</span></span>|<span data-ttu-id="5459b-138">SQLSMALLINT</span><span class="sxs-lookup"><span data-stu-id="5459b-138">SQLSMALLINT</span></span>|<span data-ttu-id="5459b-139">表示在定義資料表值參數之整體順序的一組資料行中，資料表值參數資料行的序數。</span><span class="sxs-lookup"><span data-stu-id="5459b-139">Indicates the ordinal of a table-valued parameter column in the set of columns that define the overall ordering for a table-valued parameter.</span></span> <span data-ttu-id="5459b-140">這會使查詢效能更好。</span><span class="sxs-lookup"><span data-stu-id="5459b-140">This can result in better query performance.</span></span> <span data-ttu-id="5459b-141">若是非資料表值參數資料行的繫結，會忽略此屬性。</span><span class="sxs-lookup"><span data-stu-id="5459b-141">This attribute is ignored for bindings that are not table-valued parameter columns.</span></span> <span data-ttu-id="5459b-142">排序序數會從 1 開始。</span><span class="sxs-lookup"><span data-stu-id="5459b-142">Sort ordinals start at 1.</span></span> <span data-ttu-id="5459b-143">預設值 0 表示資料表值參數資料行沒有資料行順序。</span><span class="sxs-lookup"><span data-stu-id="5459b-143">A value of 0, the default, indicates that a table-valued parameter column does not have column ordering.</span></span>|  
|<span data-ttu-id="5459b-144">SQL_CA_SS_COLUMN_HAS_DEFAULT_VALUE</span><span class="sxs-lookup"><span data-stu-id="5459b-144">SQL_CA_SS_COLUMN_HAS_DEFAULT_VALUE</span></span>|<span data-ttu-id="5459b-145">SQLSMALLINT</span><span class="sxs-lookup"><span data-stu-id="5459b-145">SQLSMALLINT</span></span>|<span data-ttu-id="5459b-146">表示資料表值參數中的所有資料列對於此資料行是否有預設值。</span><span class="sxs-lookup"><span data-stu-id="5459b-146">Indicates whether all rows in the table-valued parameter will have the default value for this column.</span></span> <span data-ttu-id="5459b-147">對於資料表值參數，無法逐資料列選取預設值。</span><span class="sxs-lookup"><span data-stu-id="5459b-147">For table-valued parameters, it is not possible to select the default value on a row-by-row basis.</span></span> <span data-ttu-id="5459b-148">SQL_FALSE 的值表示這些資料列將沒有預設值。</span><span class="sxs-lookup"><span data-stu-id="5459b-148">A value of SQL_FALSE indicates that rows will have non-default values.</span></span> <span data-ttu-id="5459b-149">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="5459b-149">This is the default.</span></span> <span data-ttu-id="5459b-150">SQL_TRUE 的值表示此資料行對於所有資料列都有預設值。</span><span class="sxs-lookup"><span data-stu-id="5459b-150">A value of SQL_TRUE indicates that this column will have default values for all rows.</span></span><br /><br /> <span data-ttu-id="5459b-151">如果設定為 SQL_TRUE，則不會將任何資料傳送到伺服器。</span><span class="sxs-lookup"><span data-stu-id="5459b-151">If set to SQL_TRUE, no data will be sent to the server.</span></span><br /><br /> <span data-ttu-id="5459b-152">如果伺服器處理不需要資料行值，此欄位也可以搭配識別或計算資料行使用。</span><span class="sxs-lookup"><span data-stu-id="5459b-152">This field can also be used with identity or computed columns if the column values are not required for server processing.</span></span>|  
  
 <span data-ttu-id="5459b-153">這些屬性只適用於資料表值參數資料行。</span><span class="sxs-lookup"><span data-stu-id="5459b-153">These attributes are only valid for table-valued parameter columns.</span></span> <span data-ttu-id="5459b-154">若是其他參數，則會忽略這些屬性。</span><span class="sxs-lookup"><span data-stu-id="5459b-154">They are ignored for other parameters.</span></span>  
  
 <span data-ttu-id="5459b-155">如果針對資料表值參數資料行設定 SQL_CA_SS_COL_HAS_DEFAULT_VALUE，該資料行的 SQL_DESC_DATA_PTR 必須為 Null 指標。</span><span class="sxs-lookup"><span data-stu-id="5459b-155">If SQL_CA_SS_COL_HAS_DEFAULT_VALUE is set for a table-valued parameter column, SQL_DESC_DATA_PTR for that column must be a null pointer.</span></span> <span data-ttu-id="5459b-156">否則，SQLExecute 或 SQLExecDirect 會傳回 SQL_ERROR。</span><span class="sxs-lookup"><span data-stu-id="5459b-156">Otherwise, SQLExecute or SQLExecDirect will return SQL_ERROR.</span></span> <span data-ttu-id="5459b-157">將會產生含有 SQLSTATE = 07S01 的診斷記錄，以及「參數、資料行的預設參數用法無效」訊息 \<p> \<c> ，其中 \<p> 是參數序數，而 \<c> 是資料行序數。</span><span class="sxs-lookup"><span data-stu-id="5459b-157">A diagnostic record will be generated with SQLSTATE=07S01 and the message "Invalid use of default parameter for parameter \<p>, column \<c>", where \<p> is the parameter ordinal and \<c> is the column ordinal.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5459b-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5459b-158">See Also</span></span>  
 [<span data-ttu-id="5459b-159">ODBC&#41;&#40;的資料表值參數</span><span class="sxs-lookup"><span data-stu-id="5459b-159">Table-Valued Parameters &#40;ODBC&#41;</span></span>](table-valued-parameters-odbc.md)  
  
  