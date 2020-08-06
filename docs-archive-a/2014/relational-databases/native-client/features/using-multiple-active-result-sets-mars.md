---
title: 使用 Multiple Active Result Set (MARS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, MARS
- SQLNCLI, MARS
- data access [SQL Server Native Client], MARS
- Multiple Active Result Sets
- SQL Server Native Client, MARS
- MARS [SQL Server]
- SQL Server Native Client ODBC driver, MARS
ms.assetid: ecfd9c6b-7d29-41d8-af2e-89d7fb9a1d83
author: rothja
ms.author: jroth
ms.openlocfilehash: 7119048df3de23b1cfc5d6c8fb41672d82be14f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598320"
---
# <a name="using-multiple-active-result-sets-mars"></a><span data-ttu-id="4a196-102">使用 Multiple Active Result Sets (MARS)</span><span class="sxs-lookup"><span data-stu-id="4a196-102">Using Multiple Active Result Sets (MARS)</span></span>
  [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] <span data-ttu-id="4a196-103">在存取 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 的應用程式中導入了對 Multiple Active Result Set (MARS) 的支援。</span><span class="sxs-lookup"><span data-stu-id="4a196-103">introduced support for multiple active result sets (MARS) in applications accessing the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span> <span data-ttu-id="4a196-104">在舊版的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中，資料庫應用程式無法在連接上維持多個作用中陳述式。</span><span class="sxs-lookup"><span data-stu-id="4a196-104">In earlier versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], database applications could not maintain multiple active statements on a connection.</span></span> <span data-ttu-id="4a196-105">當使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 預設結果集時，應用程式必須從一個批次處理或取消所有結果集，然後才能夠在該連接上執行任何其他批次。</span><span class="sxs-lookup"><span data-stu-id="4a196-105">When using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] default result sets, the application had to process or cancel all result sets from one batch before it could execute any other batch on that connection.</span></span> [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] <span data-ttu-id="4a196-106">導入了新的連接屬性，好讓應用程式在每個連接上可以有一個以上的暫止要求，而且特別是每個連接上可以有一個以上的使用中預設結果集。</span><span class="sxs-lookup"><span data-stu-id="4a196-106">introduced a new connection attribute that allows applications to have more than one pending request per connection, and in particular, to have more than one active default result set per connection.</span></span>  
  
 <span data-ttu-id="4a196-107">MARS 會使用以下的新功能來簡化應用程式設計：</span><span class="sxs-lookup"><span data-stu-id="4a196-107">MARS simplifies application design with the following new capabilities:</span></span>  
  
-   <span data-ttu-id="4a196-108">應用程式可以開啟多個預設結果集，而且可以交錯讀取這些結果集。</span><span class="sxs-lookup"><span data-stu-id="4a196-108">Applications can have multiple default result sets open and can interleave reading from them.</span></span>  
  
-   <span data-ttu-id="4a196-109">當開啟預設結果集時，應用程式可以執行其他陳述式 (例如 INSERT、UPDATE、DELETE 和預存程序呼叫)。</span><span class="sxs-lookup"><span data-stu-id="4a196-109">Applications can execute other statements (for example, INSERT, UPDATE, DELETE, and stored procedure calls) while default result sets are open.</span></span>  
  
 <span data-ttu-id="4a196-110">以下的指導方針對於使用 MARS 的應用程式非常有用：</span><span class="sxs-lookup"><span data-stu-id="4a196-110">Applications using MARS will find the following guidelines beneficial:</span></span>  
  
-   <span data-ttu-id="4a196-111">預設結果集應該用於單一 SQL 陳述式 (SELECT、DML with OUTPUT、RECEIVE、READ TEXT 等等) 所產生的短期或簡短結果集。</span><span class="sxs-lookup"><span data-stu-id="4a196-111">Default results sets should be used for short lived or short result sets generated by single SQL statements (SELECT, DML with OUTPUT, RECEIVE, READ TEXT, and so on).</span></span>  
  
-   <span data-ttu-id="4a196-112">伺服器資料指標應該用於單一 SQL 陳述式所產生的較長期或大型結果集。</span><span class="sxs-lookup"><span data-stu-id="4a196-112">Server cursors should be used for longer lived or large result sets generated by single SQL statements.</span></span>  
  
-   <span data-ttu-id="4a196-113">一定要針對程序要求 (不論它們是否會傳回結果) 以及可傳回多個結果的批次讀取到結果結尾。</span><span class="sxs-lookup"><span data-stu-id="4a196-113">Always read to the end of results for procedural requests regardless of whether they return results or not, and for batches that return multiple results.</span></span>  
  
-   <span data-ttu-id="4a196-114">盡可能使用 API 呼叫來變更連接屬性，並優先管理交易，而非 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="4a196-114">Wherever possible, use API calls to change connection properties and manage transactions in preference to [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements.</span></span>  
  
-   <span data-ttu-id="4a196-115">在 MARS 中，當執行並行批次時會禁止工作階段範圍的模擬。</span><span class="sxs-lookup"><span data-stu-id="4a196-115">In MARS, session-scoped impersonation is prohibited while concurrent batches are running.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4a196-116">預設不會啟用 MARS 功能。</span><span class="sxs-lookup"><span data-stu-id="4a196-116">By default, MARS functionality is not enabled.</span></span> <span data-ttu-id="4a196-117">若要在利用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 連接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 時使用 MARS，您必須在連接字串中特別啟用它。</span><span class="sxs-lookup"><span data-stu-id="4a196-117">To use MARS when connecting to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, you must specifically enable it within a connection string.</span></span> <span data-ttu-id="4a196-118">如需詳細資訊，請參閱本主題稍後的「[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者」和「[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式」章節。</span><span class="sxs-lookup"><span data-stu-id="4a196-118">For more information, see the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver sections, later in this topic.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="4a196-119">Native Client 不會限制連接上作用中陳述式的數目。</span><span class="sxs-lookup"><span data-stu-id="4a196-119">Native Client does not limit the number of active statements on a connection.</span></span>  
  
 <span data-ttu-id="4a196-120">不需要有多個單一多重陳述式批次或預存程序同時執行的一般應用程式將會因為 MARS 而受益，而不必了解 MARS 的實作方式。</span><span class="sxs-lookup"><span data-stu-id="4a196-120">Typical applications which do not need to have more than a single multistatement batch or stored procedure executing at the same time will benefit from MARS without having to understand how MARS is implemented.</span></span> <span data-ttu-id="4a196-121">但是，具有更複雜需求的應用程式確實需要考量這件事。</span><span class="sxs-lookup"><span data-stu-id="4a196-121">However, applications with more complex requirements do need to take account of this.</span></span>  
  
 <span data-ttu-id="4a196-122">MARS 可啟用單一連接內多個要求的交錯執行。</span><span class="sxs-lookup"><span data-stu-id="4a196-122">MARS enables the interleaved execution of multiple requests within a single connection.</span></span> <span data-ttu-id="4a196-123">也就是說，它可允許批次執行，而且當它執行時，可允許其他要求執行。</span><span class="sxs-lookup"><span data-stu-id="4a196-123">That is, it allows a batch to run, and within its execution, it allows other requests to execute.</span></span> <span data-ttu-id="4a196-124">但是請注意，MARS 是以交錯來定義，而不是以平行執行來定義。</span><span class="sxs-lookup"><span data-stu-id="4a196-124">Note, however, that MARS is defined in terms of interleaving, not in terms of parallel execution.</span></span>  
  
 <span data-ttu-id="4a196-125">MARS 基礎結構可讓多個批次以交錯方式執行，但是只能在定義良好的點上切換執行。</span><span class="sxs-lookup"><span data-stu-id="4a196-125">The MARS infrastructure allows multiple batches to execute in an interleaved fashion, though execution can only be switched at well defined points.</span></span> <span data-ttu-id="4a196-126">此外，大多數的陳述式都必須在批次內自動執行。</span><span class="sxs-lookup"><span data-stu-id="4a196-126">In addition, most statements must run atomically within a batch.</span></span> <span data-ttu-id="4a196-127">傳回資料列給用戶端的語句（有時也稱為「*產生點*」），可以在資料列傳送到用戶端時，于完成前交錯執行，例如：</span><span class="sxs-lookup"><span data-stu-id="4a196-127">Statements which return rows to the client, which are sometimes referred to as *yield points*, are allowed to interleave execution before completion while rows are being sent to the client, for example:</span></span>  
  
-   <span data-ttu-id="4a196-128">SELECT</span><span class="sxs-lookup"><span data-stu-id="4a196-128">SELECT</span></span>  
  
-   <span data-ttu-id="4a196-129">FETCH</span><span class="sxs-lookup"><span data-stu-id="4a196-129">FETCH</span></span>  
  
-   <span data-ttu-id="4a196-130">RECEIVE</span><span class="sxs-lookup"><span data-stu-id="4a196-130">RECEIVE</span></span>  
  
 <span data-ttu-id="4a196-131">當執行可以切換到其他 MARS 要求之前，當做預存程序或批次的一部分執行的其他任何陳述式都必須執行到完成為止。</span><span class="sxs-lookup"><span data-stu-id="4a196-131">Any other statements that are executed as part of a stored procedure or batch must run to completion before execution can be switched to other MARS requests.</span></span>  
  
 <span data-ttu-id="4a196-132">批次交錯執行的確切方式會受到一些因素的影響，而且很難預測包含產生點之多個批次中將要執行命令的確切順序。</span><span class="sxs-lookup"><span data-stu-id="4a196-132">The exact manner in which batches interleave execution is influenced by a number of factors, and it is difficult to predict the exact sequence in which commands from multiple batches that contain yield points will be executed.</span></span> <span data-ttu-id="4a196-133">請小心避免因為這類複雜批次的交錯執行所產生之不必要的副作用。</span><span class="sxs-lookup"><span data-stu-id="4a196-133">Be careful to avoid unwanted side effects due to interleaved execution of such complex batches.</span></span>  
  
 <span data-ttu-id="4a196-134">若要避免問題的發生，請使用 API 呼叫 (而非 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式) 來管理連接狀態 (SET、USE) 和交易 (BEGIN TRAN、COMMIT、ROLLBACK)，其方式是不要將這些陳述式併入同樣包含產生點的多重陳述式批次內，以及取用或取消所有結果來序列化這類批次的執行。</span><span class="sxs-lookup"><span data-stu-id="4a196-134">Avoid problems by using API calls rather than [!INCLUDE[tsql](../../../includes/tsql-md.md)] statements to manage connection state (SET, USE) and transactions (BEGIN TRAN, COMMIT, ROLLBACK) by not including these statements in multi-statement batches that also contain yield points, and by serializing execution of such batches by consuming or canceling all results.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4a196-135">在啟用 MARS 時啟動手動或隱含交易的批次或預存程序必須先完成交易，然後才能結束批次。</span><span class="sxs-lookup"><span data-stu-id="4a196-135">A batch or stored procedure which starts a manual or implicit transaction when MARS is enabled must complete the transaction before the batch exits.</span></span> <span data-ttu-id="4a196-136">如果不是這樣的話，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 會在批次完成時回復交易所做的所有變更。</span><span class="sxs-lookup"><span data-stu-id="4a196-136">If it does not, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] rolls back all changes made by the transaction when the batch finishes.</span></span> <span data-ttu-id="4a196-137">這類交易是由 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 當做批次範圍的交易來管理。</span><span class="sxs-lookup"><span data-stu-id="4a196-137">Such a transaction is managed by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] as a batch-scoped transaction.</span></span> <span data-ttu-id="4a196-138">[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 中導入了新類型的交易，好讓現有行為良好的預存程序在啟用 MARS 時可以使用。</span><span class="sxs-lookup"><span data-stu-id="4a196-138">This is a new type of transaction introduced in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] to enable existing well-behaved stored procedures to be used when MARS is enabled.</span></span> <span data-ttu-id="4a196-139">如需批次範圍交易的詳細資訊，請參閱[交易陳述式 &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transactions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="4a196-139">For more information about batch-scoped transactions, see [Transaction Statements &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/transactions-transact-sql).</span></span>  
  
 <span data-ttu-id="4a196-140">如需從 ADO 使用 MARS 的範例，請參閱搭配[使用 ado 與 SQL Server Native Client](../applications/using-ado-with-sql-server-native-client.md)。</span><span class="sxs-lookup"><span data-stu-id="4a196-140">For an example of using MARS from ADO, see [Using ADO with SQL Server Native Client](../applications/using-ado-with-sql-server-native-client.md).</span></span>  
  
## <a name="sql-server-native-client-ole-db-provider"></a><span data-ttu-id="4a196-141">SQL Server Native Client OLE DB 提供者</span><span class="sxs-lookup"><span data-stu-id="4a196-141">SQL Server Native Client OLE DB Provider</span></span>  
 <span data-ttu-id="4a196-142">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者透過加入 SSPROP_INIT_MARSCONNECTION 資料來源初始化屬性（在 DBPROPSET_SQLSERVERDBINIT 屬性集內執行）來支援 MARS。</span><span class="sxs-lookup"><span data-stu-id="4a196-142">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports MARS through the addition of the SSPROP_INIT_MARSCONNECTION data source initialization property, which is implemented in the DBPROPSET_SQLSERVERDBINIT property set.</span></span> <span data-ttu-id="4a196-143">此外，也已經加入新的連接字串關鍵字 `MarsConn`。</span><span class="sxs-lookup"><span data-stu-id="4a196-143">In addition, a new connection string keyword, `MarsConn`, as been added.</span></span> <span data-ttu-id="4a196-144">它可接受 `true` 或 `false` 值；`false` 是預設值。</span><span class="sxs-lookup"><span data-stu-id="4a196-144">It accepts `true` or `false` values; `false` is the default.</span></span>  
  
 <span data-ttu-id="4a196-145">資料來源屬性 DBPROP_MULTIPLECONNECTIONS 預設為 VARIANT_TRUE。</span><span class="sxs-lookup"><span data-stu-id="4a196-145">The data source property DBPROP_MULTIPLECONNECTIONS defaults to VARIANT_TRUE.</span></span> <span data-ttu-id="4a196-146">這表示，為了支援多個並行命令和資料列集物件，此提供者將會繁衍多個連接。</span><span class="sxs-lookup"><span data-stu-id="4a196-146">This means the provider will spawn multiple connections in order to support multiple concurrent command and rowset objects.</span></span> <span data-ttu-id="4a196-147">當 MARS 啟用時， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 可以在單一連接上支援多個命令和資料列集物件，因此 MULTIPLE_CONNECTIONS 預設會設定為 VARIANT_FALSE。</span><span class="sxs-lookup"><span data-stu-id="4a196-147">When MARS is enabled, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client can support multiple command and rowset objects on a single connection, so MULTIPLE_CONNECTIONS is set to VARIANT_FALSE by default.</span></span>  
  
 <span data-ttu-id="4a196-148">如需對 DBPROPSET_SQLSERVERDBINIT 屬性集所做之增強功能的詳細資訊，請參閱[初始化和授權屬性](../../native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="4a196-148">For more information about enhancements made to the DBPROPSET_SQLSERVERDBINIT property set, see [Initialization and Authorization Properties](../../native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md).</span></span>  
  
### <a name="sql-server-native-client-ole-db-provider-example"></a><span data-ttu-id="4a196-149">SQL Server Native Client OLE DB 提供者範例</span><span class="sxs-lookup"><span data-stu-id="4a196-149">SQL Server Native Client OLE DB Provider Example</span></span>  
 <span data-ttu-id="4a196-150">在此範例中，會使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 原生 OLE DB 提供者建立資料來源物件，而且在建立會話物件之前，會使用 DBPROPSET_SQLSERVERDBINIT 屬性集來啟用 MARS。</span><span class="sxs-lookup"><span data-stu-id="4a196-150">In this example, a data source object is created using the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native OLE DB provider, and MARS is enabled using the DBPROPSET_SQLSERVERDBINIT property set before the session object is created.</span></span>  
  
```  
#include <sqlncli.h>  
  
IDBInitialize *pIDBInitialize = NULL;  
IDBCreateSession *pIDBCreateSession = NULL;  
IDBProperties *pIDBProperties = NULL;  
  
// Create the data source object.  
hr = CoCreateInstance(CLSID_SQLNCLI10, NULL,  
   CLSCTX_INPROC_SERVER,  
   IID_IDBInitialize,   
    (void**)&pIDBInitialize);  
  
hr = pIDBInitialize->QueryInterface(IID_IDBProperties, (void**)&pIDBProperties);  
  
// Set the MARS property.  
DBPROP rgPropMARS;  
  
// The following is necessary since MARS is off by default.  
rgPropMARS.dwPropertyID = SSPROP_INIT_MARSCONNECTION;  
rgPropMARS.dwOptions = DBPROPOPTIONS_REQUIRED;  
rgPropMARS.dwStatus = DBPROPSTATUS_OK;  
rgPropMARS.colid = DB_NULLID;  
V_VT(&(rgPropMARS.vValue)) = VT_BOOL;  
V_BOOL(&(rgPropMARS.vValue)) = VARIANT_TRUE;  
  
// Create the structure containing the properties.  
DBPROPSET PropSet;  
PropSet.rgProperties = &rgPropMARS;  
PropSet.cProperties = 1;  
PropSet.guidPropertySet = DBPROPSET_SQLSERVERDBINIT;  
  
// Get an IDBProperties pointer and set the initialization properties.  
pIDBProperties->SetProperties(1, &PropSet);  
pIDBProperties->Release();  
  
// Initialize the data source object.  
hr = pIDBInitialize->Initialize();  
  
//Create a session object from a data source object.  
IOpenRowset * pIOpenRowset = NULL;  
hr = IDBInitialize->QueryInterface(IID_IDBCreateSession, (void**)&pIDBCreateSession));  
hr = pIDBCreateSession->CreateSession(  
   NULL,             // pUnkOuter  
   IID_IOpenRowset,  // riid  
  &pIOpenRowset ));  // ppSession  
  
// Create a rowset with a firehose mode cursor.  
IRowset *pIRowset = NULL;  
DBPROP rgRowsetProperties[2];  
  
// To get a firehose mode cursor request a   
// forward only read only rowset.  
rgRowsetProperties[0].dwPropertyID = DBPROP_IRowsetLocate;  
rgRowsetProperties[0].dwOptions = DBPROPOPTIONS_REQUIRED;  
rgRowsetProperties[0].dwStatus = DBPROPSTATUS_OK;  
rgRowsetProperties[0].colid = DB_NULLID;  
VariantInit(&(rgRowsetProperties[0].vValue));  
rgRowsetProperties[0].vValue.vt = VARIANT_BOOL;  
rgRowsetProperties[0].vValue.boolVal = VARIANT_FALSE;  
  
rgRowsetProperties[1].dwPropertyID = DBPROP_IRowsetChange;  
rgRowsetProperties[1].dwOptions = DBPROPOPTIONS_REQUIRED;  
rgRowsetProperties[1].dwStatus = DBPROPSTATUS_OK;  
rgRowsetProperties[1].colid = DB_NULLID;  
VariantInit(&(rgRowsetProperties[1].vValue));  
rgRowsetProperties[1].vValue.vt = VARIANT_BOOL;  
rgRowsetProperties[1].vValue.boolVal = VARIANT_FALSE;  
  
DBPROPSET rgRowsetPropSet[1];  
rgRowsetPropSet[0].rgProperties = rgRowsetProperties  
rgRowsetPropSet[0].cProperties = 2  
rgRowsetPropSet[0].guidPropertySet = DBPROPSET_ROWSET;  
  
hr = pIOpenRowset->OpenRowset (NULL,  
   &TableID,  
   NULL,  
   IID_IRowset,  
   1,  
   rgRowsetPropSet  
   (IUnknown**)&pIRowset);  
```  
  
## <a name="sql-server-native-client-odbc-driver"></a><span data-ttu-id="4a196-151">SQL Server Native Client ODBC 驅動程式</span><span class="sxs-lookup"><span data-stu-id="4a196-151">SQL Server Native Client ODBC Driver</span></span>  
 <span data-ttu-id="4a196-152">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驅動程式透過[SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md)和[SQLGetConnectAttr](../../native-client-odbc-api/sqlgetconnectattr.md)函式的新增功能支援 MARS。</span><span class="sxs-lookup"><span data-stu-id="4a196-152">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver supports MARS through additions to the [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) and [SQLGetConnectAttr](../../native-client-odbc-api/sqlgetconnectattr.md) functions.</span></span> <span data-ttu-id="4a196-153">已經加入 SQL_COPT_SS_MARS_ENABLED 來接受 SQL_MARS_ENABLED_YES 或 SQL_MARS_ENABLED_NO，而預設值為 SQL_MARS_ENABLED_NO。</span><span class="sxs-lookup"><span data-stu-id="4a196-153">SQL_COPT_SS_MARS_ENABLED has been added to accept either SQL_MARS_ENABLED_YES or SQL_MARS_ENABLED_NO, with SQL_MARS_ENABLED_NO being the default.</span></span> <span data-ttu-id="4a196-154">此外，也已經加入新的連接字串關鍵字 `Mars_Connection`。</span><span class="sxs-lookup"><span data-stu-id="4a196-154">In addition, a new connection string keyword, `Mars_Connection`, as been added.</span></span> <span data-ttu-id="4a196-155">它可接受 "yes" 或 "no" 值；預設值是 "no"。</span><span class="sxs-lookup"><span data-stu-id="4a196-155">It accepts "yes" or "no" values; "no" is the default.</span></span>  
  
### <a name="sql-server-native-client-odbc-driver-example"></a><span data-ttu-id="4a196-156">SQL Server Native Client ODBC 驅動程式範例</span><span class="sxs-lookup"><span data-stu-id="4a196-156">SQL Server Native Client ODBC Driver Example</span></span>  
 <span data-ttu-id="4a196-157">在此範例中， **SQLSetConnectAttr**函數是用來在呼叫**SQLDriverConnect**函式來連接資料庫之前啟用 MARS。</span><span class="sxs-lookup"><span data-stu-id="4a196-157">In this example, the **SQLSetConnectAttr** function is used to enable MARS before calling the **SQLDriverConnect** function to connect the database.</span></span> <span data-ttu-id="4a196-158">一旦建立連接，就會呼叫兩個**SQLExecDirect**函數，以在相同的連接上建立兩個不同的結果集。</span><span class="sxs-lookup"><span data-stu-id="4a196-158">Once the connection is made, two **SQLExecDirect** functions are called to create two separate result sets on the same connection.</span></span>  
  
```  
#include <sqlncli.h>  
  
SQLSetConnectAttr(hdbc, SQL_COPT_SS_MARS_ENABLED, SQL_MARS_ENABLED_YES, SQL_IS_UINTEGER);  
SQLDriverConnect(hdbc, hwnd,   
   "DRIVER=SQL Server Native Client 10.0;  
   SERVER=(local);trusted_connection=yes;", SQL_NTS, szOutConn,   
   MAX_CONN_OUT, &cbOutConn, SQL_DRIVER_COMPLETE);  
  
SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt1);  
SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt2);  
  
// The 2nd execute would have failed with connection busy error if  
// MARS were not enabled.  
SQLExecDirect(hstmt1, L"SELECT * FROM Authors", SQL_NTS);  
SQLExecDirect(hstmt2, L"SELECT * FROM Titles", SQL_NTS);  
  
// Result set processing can interleave.  
SQLFetch(hstmt1);  
SQLFetch(hstmt2);  
```  
  
## <a name="see-also"></a><span data-ttu-id="4a196-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a196-159">See Also</span></span>  
 <span data-ttu-id="4a196-160">[SQL Server Native Client 功能](sql-server-native-client-features.md) </span><span class="sxs-lookup"><span data-stu-id="4a196-160">[SQL Server Native Client Features](sql-server-native-client-features.md) </span></span>  
 [<span data-ttu-id="4a196-161">使用 QL Server 預設結果集</span><span class="sxs-lookup"><span data-stu-id="4a196-161">Using SQL Server Default Result Sets</span></span>](../../native-client-odbc-cursors/implementation/using-sql-server-default-result-sets.md)  
  
  