---
title: SQLColAttribute |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLColAttribute function
ms.assetid: a5387d9e-a243-4cfe-b786-7fad5842b1d6
author: rothja
ms.author: jroth
ms.openlocfilehash: 10207fe12a7bea5b5edb8c6e558aec6ce3b2f148
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594997"
---
# <a name="sqlcolattribute"></a><span data-ttu-id="6ee2a-102">SQLColAttribute</span><span class="sxs-lookup"><span data-stu-id="6ee2a-102">SQLColAttribute</span></span>
  <span data-ttu-id="6ee2a-103">您可以使用 `SQLColAttribute` ，針對已備妥或已執行的 ODBC 語句，抓取結果集資料行的屬性。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-103">You can use `SQLColAttribute` to retrieve an attribute of a result set column for either prepared or executed ODBC statements.</span></span> <span data-ttu-id="6ee2a-104">`SQLColAttribute`在備妥的語句上呼叫會導致往返 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-104">Calling `SQLColAttribute` on prepared statements causes a roundtrip to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="6ee2a-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驅動程式會在執行語句時接收結果集資料行資料，因此，在 `SQLColAttribute` **SQLExecute**或**SQLExecDirect**完成時呼叫之後，不會牽涉到伺服器往返。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-105">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver receives result set column data as part of statement execution, so calling `SQLColAttribute` after the completion of **SQLExecute** or **SQLExecDirect** does not involve a server roundtrip.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6ee2a-106">ODBC 資料行識別碼屬性並非在所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 結果集上都有提供。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-106">ODBC column identifier attributes are not available on all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] result sets.</span></span>  
  
|<span data-ttu-id="6ee2a-107">欄位識別碼</span><span class="sxs-lookup"><span data-stu-id="6ee2a-107">Field identifier</span></span>|<span data-ttu-id="6ee2a-108">描述</span><span class="sxs-lookup"><span data-stu-id="6ee2a-108">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="6ee2a-109">SQL_COLUMN_TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="6ee2a-109">SQL_COLUMN_TABLE_NAME</span></span>|<span data-ttu-id="6ee2a-110">可用於擷取自產生伺服器資料指標之陳述式的結果集，或包含 FOR BROWSE 子句之已執行 SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-110">Available on result sets retrieved from statements that generate server cursors or on executed SELECT statements containing a FOR BROWSE clause.</span></span>|  
|<span data-ttu-id="6ee2a-111">SQL_DESC_BASE_COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="6ee2a-111">SQL_DESC_BASE_COLUMN_NAME</span></span>|<span data-ttu-id="6ee2a-112">可用於擷取自產生伺服器資料指標之陳述式的結果集，或包含 FOR BROWSE 子句之已執行 SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-112">Available on result sets retrieved from statements that generate server cursors or on executed SELECT statements containing a FOR BROWSE clause.</span></span>|  
|<span data-ttu-id="6ee2a-113">SQL_DESC_BASE_TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="6ee2a-113">SQL_DESC_BASE_TABLE_NAME</span></span>|<span data-ttu-id="6ee2a-114">可用於擷取自產生伺服器資料指標之陳述式的結果集，或包含 FOR BROWSE 子句之已執行 SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-114">Available on result sets retrieved from statements that generate server cursors or on executed SELECT statements containing a FOR BROWSE clause.</span></span>|  
|<span data-ttu-id="6ee2a-115">SQL_DESC_CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="6ee2a-115">SQL_DESC_CATALOG_NAME</span></span>|<span data-ttu-id="6ee2a-116">資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-116">Database name.</span></span> <span data-ttu-id="6ee2a-117">可用於擷取自產生伺服器資料指標之陳述式的結果集，或包含 FOR BROWSE 子句之已執行 SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-117">Available on result sets retrieved from statements that generate server cursors or on executed SELECT statements containing a FOR BROWSE clause.</span></span>|  
|<span data-ttu-id="6ee2a-118">SQL_DESC_LABEL</span><span class="sxs-lookup"><span data-stu-id="6ee2a-118">SQL_DESC_LABEL</span></span>|<span data-ttu-id="6ee2a-119">可用於所有結果集上。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-119">Available on all result sets.</span></span> <span data-ttu-id="6ee2a-120">此值與 SQL_DESC_NAME 欄位的值相同。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-120">The value is identical to the value of the SQL_DESC_NAME field.</span></span><br /><br /> <span data-ttu-id="6ee2a-121">只有在資料行為運算式的結果，而且運算式不包含標籤指派時，欄位的長度才為零。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-121">The field is zero length only if a column is the result of an expression and the expression does not contain a label assignment.</span></span>|  
|<span data-ttu-id="6ee2a-122">SQL_DESC_NAME</span><span class="sxs-lookup"><span data-stu-id="6ee2a-122">SQL_DESC_NAME</span></span>|<span data-ttu-id="6ee2a-123">可用於所有結果集上。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-123">Available on all result sets.</span></span> <span data-ttu-id="6ee2a-124">此值與 SQL_DESC_LABEL 欄位的值相同。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-124">The value is identical to the value of the SQL_DESC_LABEL field.</span></span><br /><br /> <span data-ttu-id="6ee2a-125">只有在資料行為運算式的結果，而且運算式不包含標籤指派時，欄位的長度才為零。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-125">The field is zero length only if a column is the result of an expression and the expression does not contain a label assignment.</span></span>|  
|<span data-ttu-id="6ee2a-126">SQL_DESC_SCHEMA_NAME</span><span class="sxs-lookup"><span data-stu-id="6ee2a-126">SQL_DESC_SCHEMA_NAME</span></span>|<span data-ttu-id="6ee2a-127">擁有者名稱。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-127">Owner name.</span></span> <span data-ttu-id="6ee2a-128">可用於擷取自產生伺服器資料指標之陳述式的結果集，或包含 FOR BROWSE 子句之已執行 SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-128">Available on result sets retrieved from statements that generate server cursors or on executed SELECT statements containing a FOR BROWSE clause.</span></span><br /><br /> <span data-ttu-id="6ee2a-129">只有在 SELECT 陳述式中針對資料行指定擁有者名稱時才適用。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-129">Available only if the owner name is specified for the column in the SELECT statement.</span></span>|  
|<span data-ttu-id="6ee2a-130">SQL_DESC_TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="6ee2a-130">SQL_DESC_TABLE_NAME</span></span>|<span data-ttu-id="6ee2a-131">可用於擷取自產生伺服器資料指標之陳述式的結果集，或包含 FOR BROWSE 子句之已執行 SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-131">Available on result sets retrieved from statements that generate server cursors or on executed SELECT statements containing a FOR BROWSE clause.</span></span>|  
|<span data-ttu-id="6ee2a-132">SQL_DESC_UNNAMED</span><span class="sxs-lookup"><span data-stu-id="6ee2a-132">SQL_DESC_UNNAMED</span></span>|<span data-ttu-id="6ee2a-133">除非資料行是運算式的結果，而且該運算式在執行時不包含標籤指派，否則為結果集中所有資料行的 SQL_NAMED。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-133">SQL_NAMED for all columns in a result set unless a column is the result of an expression that does not contain a label assignment as part of the expression.</span></span> <span data-ttu-id="6ee2a-134">當 SQL_DESC_UNNAMED 傳回 SQL_UNNAMED 時，資料行的所有 ODBC 資料行識別碼屬性都包含零長度字串。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-134">When SQL_DESC_UNNAMED returns SQL_UNNAMED, all ODBC column identifier attributes contain zero length strings for the column.</span></span>|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="6ee2a-135">Native Client ODBC 驅動程式會使用 SET SET FMTONLY 語句，以在 `SQLColAttribute` 針對已備妥但未執行的語句呼叫時減少伺服器額外負荷。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-135">Native Client ODBC driver uses the SET FMTONLY statement to reduce server overhead when `SQLColAttribute` is called for prepared but unexecuted statements.</span></span>  
  
 <span data-ttu-id="6ee2a-136">對於大數數值型別， `SQLColAttribute` 會傳回下列值：</span><span class="sxs-lookup"><span data-stu-id="6ee2a-136">For large value types, `SQLColAttribute` will return the following values:</span></span>  
  
|<span data-ttu-id="6ee2a-137">欄位識別碼</span><span class="sxs-lookup"><span data-stu-id="6ee2a-137">Field identifier</span></span>|<span data-ttu-id="6ee2a-138">變更的描述</span><span class="sxs-lookup"><span data-stu-id="6ee2a-138">Description of change</span></span>|  
|----------------------|---------------------------|  
|<span data-ttu-id="6ee2a-139">SQL_DESC_DISPLAY_SIZE</span><span class="sxs-lookup"><span data-stu-id="6ee2a-139">SQL_DESC_DISPLAY_SIZE</span></span>|<span data-ttu-id="6ee2a-140">這是從資料行顯示資料所需的最大字元數。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-140">This is the maximum number of characters required to display data from the column.</span></span> <span data-ttu-id="6ee2a-141">對於大數值類型資料行，傳回的值為 SQL_SS_LENGTH_UNLIMITED。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-141">For large value type columns, the value returned is SQL_SS_LENGTH_UNLIMITED.</span></span>|  
|<span data-ttu-id="6ee2a-142">SQL_DESC_LENGTH</span><span class="sxs-lookup"><span data-stu-id="6ee2a-142">SQL_DESC_LENGTH</span></span>|<span data-ttu-id="6ee2a-143">傳回結果集中資料行的實際長度。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-143">Returns the actual length of the column in the result set.</span></span> <span data-ttu-id="6ee2a-144">對於大數值類型資料行，傳回的值為 SQL_SS_LENGTH_UNLIMITED。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-144">For large value type columns, the value returned is SQL_SS_LENGTH_UNLIMITED.</span></span>|  
|<span data-ttu-id="6ee2a-145">SQL_DESC_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="6ee2a-145">SQL_DESC_OCTET_LENGTH</span></span>|<span data-ttu-id="6ee2a-146">傳回大數值類型資料行的最大長度。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-146">Returns the maximum length of a large value type column.</span></span> <span data-ttu-id="6ee2a-147">SQL_SS_LENGTH_UNLIMITED 用來表示無限制的大小。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-147">SQL_SS_LENGTH_UNLIMITED is used to indicate unlimited size.</span></span>|  
|<span data-ttu-id="6ee2a-148">SQL_DESC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="6ee2a-148">SQL_DESC_PRECISION</span></span>|<span data-ttu-id="6ee2a-149">對於大數值類型資料行，傳回 SQL_SS_LENGTH_UNLIMITED 值。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-149">Returns the value SQL_SS_LENGTH_UNLIMITED for large value type columns.</span></span>|  
|<span data-ttu-id="6ee2a-150">SQL_DESC_TYPE</span><span class="sxs-lookup"><span data-stu-id="6ee2a-150">SQL_DESC_TYPE</span></span>|<span data-ttu-id="6ee2a-151">對於大數值類型，傳回 SQL_VARCHAR, SQL_WVARCHAR 和 SQL_VARBINARY。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-151">Returns SQL_VARCHAR, SQL_WVARCHAR, and SQL_VARBINARY for large value types.</span></span>|  
|<span data-ttu-id="6ee2a-152">SQL_DESC_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="6ee2a-152">SQL_DESC_TYPE_NAME</span></span>|<span data-ttu-id="6ee2a-153">對於大數值類型，傳回 "varchar"、"varbinary"、"nvarchar"。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-153">Returns "varchar", "varbinary", "nvarchar" for the large value types.</span></span>|  
  
 <span data-ttu-id="6ee2a-154">對於所有版本，當已備妥的 SQL 陳述式批次產生多個結果集時，只有第一個結果集會報告資料行屬性。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-154">For all versions, column attributes are reported for only the first result set when multiple result sets are generated by a prepared batch of SQL statements.</span></span>  
  
 <span data-ttu-id="6ee2a-155">下列資料行屬性是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驅動程式所公開的延伸模組。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-155">The following column attributes are extensions exposed by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span> <span data-ttu-id="6ee2a-156">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驅動程式會傳回*NumericAttrPtr*參數中的所有值。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-156">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver returns all values in the *NumericAttrPtr* parameter.</span></span> <span data-ttu-id="6ee2a-157">除了 SQL_CA_SS_COMPUTE_BYLIST (WORD 陣列的指標) 之外，這些值會當做 SDWORD (signed long) 傳回。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-157">The values are returned as SDWORD (signed long) except SQL_CA_SS_COMPUTE_BYLIST, which is a pointer to a WORD array.</span></span>  
  
|<span data-ttu-id="6ee2a-158">欄位識別碼</span><span class="sxs-lookup"><span data-stu-id="6ee2a-158">Field identifier</span></span>|<span data-ttu-id="6ee2a-159">傳回的值</span><span class="sxs-lookup"><span data-stu-id="6ee2a-159">Value returned</span></span>|  
|----------------------|--------------------|  
|<span data-ttu-id="6ee2a-160">SQL_CA_SS_COLUMN_HIDDEN\*</span><span class="sxs-lookup"><span data-stu-id="6ee2a-160">SQL_CA_SS_COLUMN_HIDDEN\*</span></span>|<span data-ttu-id="6ee2a-161">如果參考的資料行是針對支援包含 FOR BROWSE 之 Transact-SQL SELECT 陳述式所建立的隱藏主索引鍵一部分，則為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-161">TRUE if the column referenced is part of a hidden primary key created to support a Transact-SQL SELECT statement containing FOR BROWSE.</span></span>|  
|<span data-ttu-id="6ee2a-162">SQL_CA_SS_COLUMN_ID</span><span class="sxs-lookup"><span data-stu-id="6ee2a-162">SQL_CA_SS_COLUMN_ID</span></span>|<span data-ttu-id="6ee2a-163">在目前的 Transact-SQL SELECT 陳述式中，COMPUTE 子句結果資料行的序數位置。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-163">Ordinal position of a COMPUTE clause result column within the current Transact-SQL SELECT statement.</span></span>|  
|<span data-ttu-id="6ee2a-164">SQL_CA_SS_COLUMN_KEY\*</span><span class="sxs-lookup"><span data-stu-id="6ee2a-164">SQL_CA_SS_COLUMN_KEY\*</span></span>|<span data-ttu-id="6ee2a-165">如果參考的資料行是資料列的主索引鍵一部分，而且 Transact-SQL SELECT 陳述式包含 FOR BROWSE，則為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-165">TRUE if the column referenced is part of a primary key for the row and the Transact-SQL SELECT statement contains FOR BROWSE.</span></span>|  
|<span data-ttu-id="6ee2a-166">SQL_CA_SS_COLUMN_OP</span><span class="sxs-lookup"><span data-stu-id="6ee2a-166">SQL_CA_SS_COLUMN_OP</span></span>|<span data-ttu-id="6ee2a-167">指定在 COMPUTE 子句資料行中負責值之彙總運算子的整數。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-167">Integer specifying the aggregate operator responsible for the value in a COMPUTE clause column.</span></span> <span data-ttu-id="6ee2a-168">整數值的定義位於 sqlncli.h。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-168">Definitions of the integer values are in sqlncli.h.</span></span>|  
|<span data-ttu-id="6ee2a-169">SQL_CA_SS_COLUMN_ORDER</span><span class="sxs-lookup"><span data-stu-id="6ee2a-169">SQL_CA_SS_COLUMN_ORDER</span></span>|<span data-ttu-id="6ee2a-170">在 ODBC 或 Transact-SQL SELECT 陳述式的 ORDER BY 子句中，資料行的序數位置。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-170">Ordinal position of the column within an ODBC or Transact-SQL SELECT statement's ORDER BY clause.</span></span>|  
|<span data-ttu-id="6ee2a-171">SQL_CA_SS_COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="6ee2a-171">SQL_CA_SS_COLUMN_SIZE</span></span>|<span data-ttu-id="6ee2a-172">將擷取自資料行的資料值繫結至 SQL_C_BINARY 變數的最大長度 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-172">Maximum length, in bytes, required to bind a data value retrieved from the column to a SQL_C_BINARY variable.</span></span>|  
|<span data-ttu-id="6ee2a-173">SQL_CA_SS_COLUMN_SSTYPE</span><span class="sxs-lookup"><span data-stu-id="6ee2a-173">SQL_CA_SS_COLUMN_SSTYPE</span></span>|<span data-ttu-id="6ee2a-174">儲存在 SQL Server 資料行中之資料的原生資料類型。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-174">Native data type of data stored in the SQL Server column.</span></span> <span data-ttu-id="6ee2a-175">類型值的定義位於 sqlncli.h。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-175">Definitions of the type values are in sqlncli.h.</span></span>|  
|<span data-ttu-id="6ee2a-176">SQL_CA_SS_COLUMN_UTYPE</span><span class="sxs-lookup"><span data-stu-id="6ee2a-176">SQL_CA_SS_COLUMN_UTYPE</span></span>|<span data-ttu-id="6ee2a-177">SQL Server 資料行之使用者定義資料類型的基底資料類型。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-177">Base data type of the SQL Server column's user-defined data type.</span></span> <span data-ttu-id="6ee2a-178">類型值的定義位於 sqlncli.h。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-178">Definitions of the type values are in sqlncli.h.</span></span>|  
|<span data-ttu-id="6ee2a-179">SQL_CA_SS_COLUMN_VARYLEN</span><span class="sxs-lookup"><span data-stu-id="6ee2a-179">SQL_CA_SS_COLUMN_VARYLEN</span></span>|<span data-ttu-id="6ee2a-180">如果資料行的資料長度可以改變，則為 TRUE，否則為 FALSE。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-180">TRUE if the column's data can vary in length, FALSE otherwise.</span></span>|  
|<span data-ttu-id="6ee2a-181">SQL_CA_SS_COMPUTE_BYLIST</span><span class="sxs-lookup"><span data-stu-id="6ee2a-181">SQL_CA_SS_COMPUTE_BYLIST</span></span>|<span data-ttu-id="6ee2a-182">WORD (unsigned short) 陣列的指標，指定在 COMPUTE 子句之 BY 片語中所使用的資料行。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-182">Pointer to an array of WORD (unsigned short) specifying the columns used in the BY phrase of a COMPUTE clause.</span></span> <span data-ttu-id="6ee2a-183">如果 COMPUTE 子句沒有指定 BY 片語，則會傳回 NULL 指標。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-183">If the COMPUTE clause does not specify a BY phrase, a NULL pointer is returned.</span></span><br /><br /> <span data-ttu-id="6ee2a-184">陣列的第一個元素包含 BY 清單資料行的計數。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-184">The first element of the array contains the count of BY list columns.</span></span> <span data-ttu-id="6ee2a-185">其他元素為資料行序數。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-185">Additional elements are the column ordinals.</span></span>|  
|<span data-ttu-id="6ee2a-186">SQL_CA_SS_COMPUTE_ID</span><span class="sxs-lookup"><span data-stu-id="6ee2a-186">SQL_CA_SS_COMPUTE_ID</span></span>|<span data-ttu-id="6ee2a-187">在目前的 Transact-sql SELECT 語句中，是 COMPUTE 子句結果的資料列*computeid* 。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-187">*computeid* of a row that is the result of a COMPUTE clause in the current Transact-SQL SELECT statement.</span></span>|  
|<span data-ttu-id="6ee2a-188">SQL_CA_SS_NUM_COMPUTES</span><span class="sxs-lookup"><span data-stu-id="6ee2a-188">SQL_CA_SS_NUM_COMPUTES</span></span>|<span data-ttu-id="6ee2a-189">在目前的 Transact-SQL SELECT 陳述式中指定的 COMPUTE 子句數目。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-189">Number of COMPUTE clauses specified in the current Transact-SQL SELECT statement.</span></span>|  
|<span data-ttu-id="6ee2a-190">SQL_CA_SS_NUM_ORDERS</span><span class="sxs-lookup"><span data-stu-id="6ee2a-190">SQL_CA_SS_NUM_ORDERS</span></span>|<span data-ttu-id="6ee2a-191">在 ODBC 或 Transact-SQL SELECT 陳述式的 ORDER BY 子句中指定之資料行的數目。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-191">Number of columns specified in an ODBC or Transact-SQL SELECT statement's ORDER BY clause.</span></span>|  
  
 <span data-ttu-id="6ee2a-192">\*如果語句屬性 SQL_SOPT_SS_HIDDEN_COLUMNS 設定為 SQL_HC_ON，則可使用。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-192">\*   Available if statement attribute SQL_SOPT_SS_HIDDEN_COLUMNS is set to SQL_HC_ON.</span></span>  
  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]<span data-ttu-id="6ee2a-193">引進驅動程式專屬的描述項欄位來提供其他資訊，分別代表 XML 架構集合名稱、架構名稱和目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-193">introduced driver-specific descriptor fields to provide additional information to denote the XML schema collection name, the schema name, and the catalog name, respectively.</span></span> <span data-ttu-id="6ee2a-194">如果這些屬性包含非英數字元，則它們不需要引號或逸出字元。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-194">These properties do not require quotation marks or an escape character if they contain non-alphanumeric characters.</span></span> <span data-ttu-id="6ee2a-195">下表列出這些新的描述項欄位：</span><span class="sxs-lookup"><span data-stu-id="6ee2a-195">The following table lists these new descriptor fields:</span></span>  
  
|<span data-ttu-id="6ee2a-196">資料行名稱</span><span class="sxs-lookup"><span data-stu-id="6ee2a-196">Column name</span></span>|<span data-ttu-id="6ee2a-197">類型</span><span class="sxs-lookup"><span data-stu-id="6ee2a-197">Type</span></span>|<span data-ttu-id="6ee2a-198">描述</span><span class="sxs-lookup"><span data-stu-id="6ee2a-198">Description</span></span>|  
|-----------------|----------|-----------------|  
|<span data-ttu-id="6ee2a-199">SQL_CA_SS_XML_SCHEMACOLLECTION_CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="6ee2a-199">SQL_CA_SS_XML_SCHEMACOLLECTION_CATALOG_NAME</span></span>|<span data-ttu-id="6ee2a-200">CharacterAttributePtr</span><span class="sxs-lookup"><span data-stu-id="6ee2a-200">CharacterAttributePtr</span></span>|<span data-ttu-id="6ee2a-201">定義 XML 結構描述集合名稱所在目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-201">The name of the catalog where an XML schema collection name is defined.</span></span> <span data-ttu-id="6ee2a-202">如果找不到目錄名稱，則此變數包含空字串。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-202">If the catalog name cannot be found, then this variable contains an empty string.</span></span><br /><br /> <span data-ttu-id="6ee2a-203">此資訊會從 IRD 的 SQL_DESC_SS_XML_SCHEMACOLLECTION_CATALOG_NAME 記錄欄位傳回，該欄位為唯讀欄位。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-203">This information is returned from the SQL_DESC_SS_XML_SCHEMACOLLECTION_CATALOG_NAME record field of the IRD, which is a read-write field.</span></span>|  
|<span data-ttu-id="6ee2a-204">SQL_CA_SS_XML_SCHEMACOLLECTION_SCHEMA_NAM E</span><span class="sxs-lookup"><span data-stu-id="6ee2a-204">SQL_CA_SS_XML_SCHEMACOLLECTION_SCHEMA_NAM E</span></span>|<span data-ttu-id="6ee2a-205">CharacterAttributePtr</span><span class="sxs-lookup"><span data-stu-id="6ee2a-205">CharacterAttributePtr</span></span>|<span data-ttu-id="6ee2a-206">定義 XML 結構描述集合名稱所在結構描述的名稱。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-206">The name of the schema where an XML schema collection name is defined.</span></span> <span data-ttu-id="6ee2a-207">如果找不到結構描述名稱，則此變數包含空字串。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-207">If the schema name cannot be found, then this variable contains an empty string.</span></span><br /><br /> <span data-ttu-id="6ee2a-208">此資訊會從 IRD 的 SQL_DESC_SS_XML_SCHEMACOLLECTION_SCHEMA_NAME 記錄欄位傳回，該欄位為唯讀欄位。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-208">This information is returned from the SQL_DESC_SS_XML_SCHEMACOLLECTION_SCHEMA_NAME record field of the IRD, which is a read-write field.</span></span>|  
|<span data-ttu-id="6ee2a-209">SQL_CA_SS_XML_SCHEMACOLLECTION_NAME</span><span class="sxs-lookup"><span data-stu-id="6ee2a-209">SQL_CA_SS_XML_SCHEMACOLLECTION_NAME</span></span>|<span data-ttu-id="6ee2a-210">CharacterAttributePtr</span><span class="sxs-lookup"><span data-stu-id="6ee2a-210">CharacterAttributePtr</span></span>|<span data-ttu-id="6ee2a-211">XML 結構描述集合的名稱。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-211">The name of an XML schema collection.</span></span> <span data-ttu-id="6ee2a-212">如果找不到名稱，則此變數包含空字串。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-212">If the name cannot be found, then this variable contains an empty string.</span></span><br /><br /> <span data-ttu-id="6ee2a-213">此資訊會從 IRD 的 SQL_DESC_SS_XML_SCHEMACOLLECTION_NAME 記錄欄位傳回，該欄位為唯讀欄位。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-213">This information is returned from the SQL_DESC_SS_XML_SCHEMACOLLECTION_NAME record field of the IRD, which is a read-write field.</span></span>|  
  
 <span data-ttu-id="6ee2a-214">同時，[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 推出新的驅動程式專屬描述項欄位，針對結果集的使用者定義型別 (UDT) 資料行或預存程序或參數化查詢的 UDT 參數，提供額外的資訊。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-214">Also, [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] introduced new driver-specific descriptor fields to provide additional information for either a user-defined type (UDT) column of a result set or a UDT parameter of a stored procedure or parameterized query.</span></span> <span data-ttu-id="6ee2a-215">如果這些屬性包含非英數字元，則它們不需要引號或逸出字元。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-215">These properties do not require quotation marks or an escape character if they contain non-alphanumeric characters.</span></span> <span data-ttu-id="6ee2a-216">下表列出這些新的描述項欄位：</span><span class="sxs-lookup"><span data-stu-id="6ee2a-216">The following table lists these new descriptor fields:</span></span>  
  
|<span data-ttu-id="6ee2a-217">資料行名稱</span><span class="sxs-lookup"><span data-stu-id="6ee2a-217">Column Name</span></span>|<span data-ttu-id="6ee2a-218">類型</span><span class="sxs-lookup"><span data-stu-id="6ee2a-218">Type</span></span>|<span data-ttu-id="6ee2a-219">描述</span><span class="sxs-lookup"><span data-stu-id="6ee2a-219">Description</span></span>|  
|-----------------|----------|-----------------|  
|<span data-ttu-id="6ee2a-220">SQL_CA_SS_UDT_CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="6ee2a-220">SQL_CA_SS_UDT_CATALOG_NAME</span></span>|<span data-ttu-id="6ee2a-221">CharacterAttributePtr</span><span class="sxs-lookup"><span data-stu-id="6ee2a-221">CharacterAttributePtr</span></span>|<span data-ttu-id="6ee2a-222">包含 UDT 之目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-222">The name of the catalog containing the UDT.</span></span>|  
|<span data-ttu-id="6ee2a-223">SQL_CA_SS_UDT_SCHEMA_NAME</span><span class="sxs-lookup"><span data-stu-id="6ee2a-223">SQL_CA_SS_UDT_SCHEMA_NAME</span></span>|<span data-ttu-id="6ee2a-224">CharacterAttributePtr</span><span class="sxs-lookup"><span data-stu-id="6ee2a-224">CharacterAttributePtr</span></span>|<span data-ttu-id="6ee2a-225">包含 UDT 之結構描述的名稱。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-225">The name of the schema containing the UDT.</span></span>|  
|<span data-ttu-id="6ee2a-226">SQL_CA_SS_UDT_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="6ee2a-226">SQL_CA_SS_UDT_TYPE_NAME</span></span>|<span data-ttu-id="6ee2a-227">CharacterAttributePtr</span><span class="sxs-lookup"><span data-stu-id="6ee2a-227">CharacterAttributePtr</span></span>|<span data-ttu-id="6ee2a-228">UDT 的名稱。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-228">The name of the UDT.</span></span>|  
|<span data-ttu-id="6ee2a-229">SQL_CA_SS_UDT_ASSEMBLY_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="6ee2a-229">SQL_CA_SS_UDT_ASSEMBLY_TYPE_NAME</span></span>|<span data-ttu-id="6ee2a-230">CharacterAttributePtr</span><span class="sxs-lookup"><span data-stu-id="6ee2a-230">CharacterAttributePtr</span></span>|<span data-ttu-id="6ee2a-231">UDT 的組件完整名稱。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-231">The assembly qualified name of the UDT.</span></span>|  
  
 <span data-ttu-id="6ee2a-232">現有的描述項欄位識別碼 SQL_DESC_TYPE_NAME 用來表示 UDT 的名稱。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-232">The existing descriptor field identifier SQL_DESC_TYPE_NAME is used to indicate the name of the UDT.</span></span> <span data-ttu-id="6ee2a-233">適用於 UDT 類型資料行的 SQL_DESC_TYPE 欄位為 SQL_SS_UDT。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-233">The SQL_DESC_TYPE field for a UDT type column is SQL_SS_UDT.</span></span>  
  
## <a name="sqlcolattribute-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="6ee2a-234">增強型日期和時間功能的 SQLColAttribute 支援</span><span class="sxs-lookup"><span data-stu-id="6ee2a-234">SQLColAttribute Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="6ee2a-235">如需日期/時間類型傳回的值，請參閱[參數和結果中繼資料](../native-client-odbc-date-time/metadata-parameter-and-result.md)中的「IRD 欄位中傳回的資訊」一節。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-235">For the values returned for date/time types, see the "Information Returned in IRD Fields" section in [Parameter and Result Metadata](../native-client-odbc-date-time/metadata-parameter-and-result.md).</span></span>  
  
 <span data-ttu-id="6ee2a-236">如需詳細資訊，請參閱[ODBC&#41;&#40;的日期和時間改善](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-236">For more information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="sqlcolattribute-support-for-large-clr-udts"></a><span data-ttu-id="6ee2a-237">大型 CLR UDT 的 SQLColAttribute 支援</span><span class="sxs-lookup"><span data-stu-id="6ee2a-237">SQLColAttribute Support for Large CLR UDTs</span></span>  
 <span data-ttu-id="6ee2a-238">`SQLColAttribute` 支援大型 CLR 使用者定義型別 (UDT)。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-238">`SQLColAttribute` supports large CLR user-defined types (UDTs).</span></span> <span data-ttu-id="6ee2a-239">如需詳細資訊，請參閱[&#40;ODBC&#41;的大型 CLR 使用者定義類型](../native-client/odbc/large-clr-user-defined-types-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-239">For more information, see [Large CLR User-Defined Types &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).</span></span>  
  
## <a name="sqlcolattribute-support-for-sparse-columns"></a><span data-ttu-id="6ee2a-240">疏鬆資料行的 SQLColAttribute 支援</span><span class="sxs-lookup"><span data-stu-id="6ee2a-240">SQLColAttribute Support for Sparse Columns</span></span>  
 <span data-ttu-id="6ee2a-241">SQLColAttribute 會查詢新的執行資料列描述項 (IRD) 欄位 SQL_CA_SS_IS_COLUMN_SET，以判斷資料行是否為數據行 `column_set` 。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-241">SQLColAttribute queries the new implementation row descriptor (IRD) field, SQL_CA_SS_IS_COLUMN_SET, to determine if a column is a `column_set` column.</span></span>  
  
 <span data-ttu-id="6ee2a-242">如需詳細資訊，請參閱[&#40;ODBC&#41;的稀疏資料行支援](../native-client/odbc/sparse-columns-support-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="6ee2a-242">For more information, see [Sparse Columns Support &#40;ODBC&#41;](../native-client/odbc/sparse-columns-support-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ee2a-243">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ee2a-243">See Also</span></span>  
 <span data-ttu-id="6ee2a-244">[SQLColAttribute 函式](https://go.microsoft.com/fwlink/?LinkId=59334) </span><span class="sxs-lookup"><span data-stu-id="6ee2a-244">[SQLColAttribute Function](https://go.microsoft.com/fwlink/?LinkId=59334) </span></span>  
 <span data-ttu-id="6ee2a-245">[ODBC API 的執行詳細資料](odbc-api-implementation-details.md) </span><span class="sxs-lookup"><span data-stu-id="6ee2a-245">[ODBC API Implementation Details](odbc-api-implementation-details.md) </span></span>  
 [<span data-ttu-id="6ee2a-246">SQLSetStmtAttr</span><span class="sxs-lookup"><span data-stu-id="6ee2a-246">SQLSetStmtAttr</span></span>](sqlsetstmtattr.md)  
  
  