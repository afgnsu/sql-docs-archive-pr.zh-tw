---
title: 擴充事件工具 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- extended events [SQL Server], using
- extended events [SQL Server], options for using
ms.assetid: d312a9ff-50ba-4721-baef-50bfd3169d38
author: rothja
ms.author: jroth
ms.openlocfilehash: 7a74080352beeda4f92ad6afa7b8266a8ebee5a2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606843"
---
# <a name="extended-events-tools"></a><span data-ttu-id="ba63c-102">擴充事件工具</span><span class="sxs-lookup"><span data-stu-id="ba63c-102">Extended Events Tools</span></span>
  <span data-ttu-id="ba63c-103">您可以使用下列工具來建立及管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 擴充事件工作階段：</span><span class="sxs-lookup"><span data-stu-id="ba63c-103">You can use the following tools to create and manage [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Extended Events sessions:</span></span>  
  
-   <span data-ttu-id="ba63c-104">資料定義語言 (DDL) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="ba63c-104">Data Definition Language (DDL) statements.</span></span> <span data-ttu-id="ba63c-105">這些可讓您建立及修改「擴充事件」工作階段。</span><span class="sxs-lookup"><span data-stu-id="ba63c-105">These enable you to create and modify an Extended Events session.</span></span>  
  
-   <span data-ttu-id="ba63c-106">動態管理檢視、目錄檢視和系統資料表。</span><span class="sxs-lookup"><span data-stu-id="ba63c-106">Dynamic management views, catalog views and system tables.</span></span> <span data-ttu-id="ba63c-107">這些可讓您使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式取得工作階段資料和中繼資料。</span><span class="sxs-lookup"><span data-stu-id="ba63c-107">These enable you to obtain session data and metadata by using [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="ba63c-108">系統資料表可幫助您判定 SQL 追蹤事件類別與資料行的現有「擴充事件」對等項目。</span><span class="sxs-lookup"><span data-stu-id="ba63c-108">The system tables help you determine the existing Extended Events equivalents for SQL Trace event classes and columns.</span></span>  
  
-   <span data-ttu-id="ba63c-109">[物件總管] 的 [擴充事件]\*\*\*\* 節點。</span><span class="sxs-lookup"><span data-stu-id="ba63c-109">The **Extended Events** node of Object Explorer.</span></span> <span data-ttu-id="ba63c-110">這可讓您啟動、停止或刪除工作階段，或是匯入及匯出工作階段範本。</span><span class="sxs-lookup"><span data-stu-id="ba63c-110">This enables you to start, stop or delete a session, or to import and export session templates.</span></span>  
  
-   <span data-ttu-id="ba63c-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell 提供者。</span><span class="sxs-lookup"><span data-stu-id="ba63c-111">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell provider.</span></span> <span data-ttu-id="ba63c-112">這是一項功能強大的工具，可讓您用來建立、更改和管理「擴充事件」工作階段。</span><span class="sxs-lookup"><span data-stu-id="ba63c-112">This is a powerful tool that you can use to create, alter, and manage Extended Events sessions.</span></span> <span data-ttu-id="ba63c-113">如需詳細資訊，請參閱 [針對擴充事件使用 PowerShell 提供者](use-the-powershell-provider-for-extended-events.md)。</span><span class="sxs-lookup"><span data-stu-id="ba63c-113">For more information, see [Use the PowerShell Provider for Extended Events](use-the-powershell-provider-for-extended-events.md).</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="ba63c-114">.</span><span class="sxs-lookup"><span data-stu-id="ba63c-114">.</span></span> <span data-ttu-id="ba63c-115">這可讓您建立及執行「擴充事件」主題中所提供的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="ba63c-115">This enables you to create and execute the code samples that are provided in the Extended Events topics.</span></span> <span data-ttu-id="ba63c-116">如需詳細資訊，請參閱 [物件總管](../../ssms/object/object-explorer.md)。</span><span class="sxs-lookup"><span data-stu-id="ba63c-116">For more information, see [Object Explorer](../../ssms/object/object-explorer.md).</span></span>  
  
 <span data-ttu-id="ba63c-117">除了您所建立的工作階段以外，伺服器上也會有預設系統健康工作階段存在。</span><span class="sxs-lookup"><span data-stu-id="ba63c-117">In addition to sessions that you create, a default system health session exists on the server.</span></span> <span data-ttu-id="ba63c-118">此工作階段會收集系統資料，讓您能夠用來協助排除效能問題。</span><span class="sxs-lookup"><span data-stu-id="ba63c-118">The session collects system data that you can use to help troubleshoot performance issues.</span></span> <span data-ttu-id="ba63c-119">如需詳細資訊，請參閱 [使用 system_health 工作階段](use-the-ssms-xe-profiler.md)。</span><span class="sxs-lookup"><span data-stu-id="ba63c-119">For more information, see [Use the system_health Session](use-the-ssms-xe-profiler.md).</span></span>  
  
## <a name="ddl-statements"></a><span data-ttu-id="ba63c-120">DDL 陳述式</span><span class="sxs-lookup"><span data-stu-id="ba63c-120">DDL Statements</span></span>  
 <span data-ttu-id="ba63c-121">使用下列 DDL 陳述式，以建立、變更和卸除「擴充事件」工作階段。</span><span class="sxs-lookup"><span data-stu-id="ba63c-121">Use the following DDL statements to create, change, and drop an Extended Events session.</span></span>  
  
|<span data-ttu-id="ba63c-122">名稱</span><span class="sxs-lookup"><span data-stu-id="ba63c-122">Name</span></span>|<span data-ttu-id="ba63c-123">描述</span><span class="sxs-lookup"><span data-stu-id="ba63c-123">Description</span></span>|  
|----------|-----------------|  
|[<span data-ttu-id="ba63c-124">CREATE EVENT SESSION &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ba63c-124">CREATE EVENT SESSION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-event-session-transact-sql)|<span data-ttu-id="ba63c-125">建立「擴充事件」工作階段物件，此物件可識別事件的來源、事件工作階段目標及事件工作階段參數。</span><span class="sxs-lookup"><span data-stu-id="ba63c-125">Creates an Extended Event session object that identifies the source of the events, the event session targets, and the event session parameters.</span></span>|  
|[<span data-ttu-id="ba63c-126">ALTER EVENT SESSION &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ba63c-126">ALTER EVENT SESSION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-event-session-transact-sql)|<span data-ttu-id="ba63c-127">啟動或停止事件工作階段，或是變更事件工作階段組態。</span><span class="sxs-lookup"><span data-stu-id="ba63c-127">Starts or stops an event session or changes an event session configuration.</span></span>|  
|[<span data-ttu-id="ba63c-128">DROP EVENT SESSION &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ba63c-128">DROP EVENT SESSION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-event-session-transact-sql)|<span data-ttu-id="ba63c-129">卸除事件工作階段。</span><span class="sxs-lookup"><span data-stu-id="ba63c-129">Drops an event session.</span></span>|  
  
## <a name="catalog-views"></a><span data-ttu-id="ba63c-130">目錄檢視</span><span class="sxs-lookup"><span data-stu-id="ba63c-130">Catalog Views</span></span>  
 <span data-ttu-id="ba63c-131">使用下列目錄檢視，以取得當您建立事件工作階段時所建立的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="ba63c-131">Use the following catalog views to obtain the metadata that is created when you create an event session.</span></span>  
  
|<span data-ttu-id="ba63c-132">名稱</span><span class="sxs-lookup"><span data-stu-id="ba63c-132">Name</span></span>|<span data-ttu-id="ba63c-133">描述</span><span class="sxs-lookup"><span data-stu-id="ba63c-133">Description</span></span>|  
|----------|-----------------|  
|[<span data-ttu-id="ba63c-134">sys.server_event_sessions &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ba63c-134">sys.server_event_sessions &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-server-event-sessions-transact-sql)|<span data-ttu-id="ba63c-135">列出所有事件工作階段定義。</span><span class="sxs-lookup"><span data-stu-id="ba63c-135">Lists all event session definitions.</span></span>|  
|[<span data-ttu-id="ba63c-136">sys.server_event_session_actions &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ba63c-136">sys.server_event_session_actions &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-server-event-session-actions-transact-sql)|<span data-ttu-id="ba63c-137">針對事件工作階段之每個事件的每個動作傳回資料列。</span><span class="sxs-lookup"><span data-stu-id="ba63c-137">Returns a row for each action on each event of an event session.</span></span>|  
|[<span data-ttu-id="ba63c-138">sys.server_event_session_events &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ba63c-138">sys.server_event_session_events &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-server-event-session-events-transact-sql)|<span data-ttu-id="ba63c-139">針對事件工作階段中的每個事件傳回資料列。</span><span class="sxs-lookup"><span data-stu-id="ba63c-139">Returns a row for each event in an event session.</span></span>|  
|[<span data-ttu-id="ba63c-140">sys.server_event_session_fields &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ba63c-140">sys.server_event_session_fields &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-server-event-session-fields-transact-sql)|<span data-ttu-id="ba63c-141">針對事件和目標上明確設定的每一個可自訂資料行傳回資料列。</span><span class="sxs-lookup"><span data-stu-id="ba63c-141">Returns a row for each customizable column that was explicitly set on events and targets.</span></span>|  
|[<span data-ttu-id="ba63c-142">sys.server_event_session_targets &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ba63c-142">sys.server_event_session_targets &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-server-event-session-targets-transact-sql)|<span data-ttu-id="ba63c-143">傳回事件工作階段中每一個事件目標的資料列。</span><span class="sxs-lookup"><span data-stu-id="ba63c-143">Returns a row for each event target for an event session.</span></span>|  
  
## <a name="dynamic-management-views"></a><span data-ttu-id="ba63c-144">動態管理檢視</span><span class="sxs-lookup"><span data-stu-id="ba63c-144">Dynamic Management Views</span></span>  
 <span data-ttu-id="ba63c-145">使用下列動態管理檢視來取得工作階段中繼資料和工作階段資料。</span><span class="sxs-lookup"><span data-stu-id="ba63c-145">Use the following dynamic management views to obtain session metadata and session data.</span></span> <span data-ttu-id="ba63c-146">中繼資料是從目錄檢視中取得，而當您啟動和執行事件工作階段時，會建立工作階段資料。</span><span class="sxs-lookup"><span data-stu-id="ba63c-146">The metadata is obtained from the catalog views, and the session data is created when you start and run an event session.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ba63c-147">這些檢視要等到工作階段啟動之後，才會包含工作階段資料。</span><span class="sxs-lookup"><span data-stu-id="ba63c-147">These views do not contain session data until a session starts.</span></span>  
  
|<span data-ttu-id="ba63c-148">名稱</span><span class="sxs-lookup"><span data-stu-id="ba63c-148">Name</span></span>|<span data-ttu-id="ba63c-149">描述</span><span class="sxs-lookup"><span data-stu-id="ba63c-149">Description</span></span>|  
|----------|-----------------|  
|[<span data-ttu-id="ba63c-150">sys.dm_os_dispatcher_pools &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ba63c-150">sys.dm_os_dispatcher_pools &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-dispatcher-pools-transact-sql)|<span data-ttu-id="ba63c-151">傳回有關工作階段發送器集區的資訊。</span><span class="sxs-lookup"><span data-stu-id="ba63c-151">Returns information about session dispatcher pools.</span></span>|  
|[<span data-ttu-id="ba63c-152">sys.dm_xe_objects &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ba63c-152">sys.dm_xe_objects &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql)|<span data-ttu-id="ba63c-153">針對事件封裝所公開的每個物件，各傳回一個資料列。</span><span class="sxs-lookup"><span data-stu-id="ba63c-153">Returns a row for each object that is exposed by an event package.</span></span>|  
|[<span data-ttu-id="ba63c-154">sys.dm_xe_object_columns &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ba63c-154">sys.dm_xe_object_columns &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-object-columns-transact-sql)|<span data-ttu-id="ba63c-155">傳回所有物件的結構描述資訊。</span><span class="sxs-lookup"><span data-stu-id="ba63c-155">Returns the schema information for all the objects.</span></span>|  
|[<span data-ttu-id="ba63c-156">sys.dm_xe_packages &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ba63c-156">sys.dm_xe_packages &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-packages-transact-sql)|<span data-ttu-id="ba63c-157">列出已向「擴充事件」引擎註冊的所有封裝。</span><span class="sxs-lookup"><span data-stu-id="ba63c-157">Lists all the packages registered with the Extended Events engine.</span></span>|  
|[<span data-ttu-id="ba63c-158">sys.dm_xe_sessions &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ba63c-158">sys.dm_xe_sessions &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-sessions-transact-sql)|<span data-ttu-id="ba63c-159">傳回使用中「擴充事件」工作階段的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="ba63c-159">Returns information about an active Extended Events session.</span></span>|  
|[<span data-ttu-id="ba63c-160">sys.dm_xe_session_targets &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ba63c-160">sys.dm_xe_session_targets &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql)|<span data-ttu-id="ba63c-161">會傳回工作階段目標的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="ba63c-161">Returns information about session targets.</span></span>|  
|[<span data-ttu-id="ba63c-162">sys.dm_xe_session_events &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ba63c-162">sys.dm_xe_session_events &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-events-transact-sql)|<span data-ttu-id="ba63c-163">傳回有關工作階段事件的資訊。</span><span class="sxs-lookup"><span data-stu-id="ba63c-163">Returns information about session events.</span></span>|  
|[<span data-ttu-id="ba63c-164">sys.dm_xe_session_event_actions &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ba63c-164">sys.dm_xe_session_event_actions &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-event-actions-transact-sql)|<span data-ttu-id="ba63c-165">傳回有關事件工作階段動作的資訊。</span><span class="sxs-lookup"><span data-stu-id="ba63c-165">Returns information about event session actions.</span></span>|  
|[<span data-ttu-id="ba63c-166">sys.dm_xe_map_values &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ba63c-166">sys.dm_xe_map_values &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-map-values-transact-sql)|<span data-ttu-id="ba63c-167">提供內部數值索引鍵與人們可讀取之文字的對應。</span><span class="sxs-lookup"><span data-stu-id="ba63c-167">Provides a mapping of internal numeric keys to human-readable text.</span></span>|  
|[<span data-ttu-id="ba63c-168">sys.dm_xe_session_object_columns &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ba63c-168">sys.dm_xe_session_object_columns &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-object-columns-transact-sql)|<span data-ttu-id="ba63c-169">顯示繫結至工作階段之物件的組態值。</span><span class="sxs-lookup"><span data-stu-id="ba63c-169">Shows the configuration values for objects that are bound to a session.</span></span>|  
  
## <a name="system-tables"></a><span data-ttu-id="ba63c-170">系統資料表</span><span class="sxs-lookup"><span data-stu-id="ba63c-170">System Tables</span></span>  
 <span data-ttu-id="ba63c-171">使用下列系統資料表，取得有關 SQL 追蹤事件類別與資料行之「擴充事件」對等項目的資訊。</span><span class="sxs-lookup"><span data-stu-id="ba63c-171">Use the following system tables to obtain information about the Extended Events equivalents for SQL Trace event classes and columns.</span></span>  
  
|<span data-ttu-id="ba63c-172">名稱</span><span class="sxs-lookup"><span data-stu-id="ba63c-172">Name</span></span>|<span data-ttu-id="ba63c-173">描述</span><span class="sxs-lookup"><span data-stu-id="ba63c-173">Description</span></span>|  
|----------|-----------------|  
|[<span data-ttu-id="ba63c-174">trace_xe_event_map &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ba63c-174">trace_xe_event_map &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-tables/extended-events-tables-trace-xe-event-map)|<span data-ttu-id="ba63c-175">針對對應至 SQL 追蹤事件類別的每個「擴充事件」事件包含一個資料列。</span><span class="sxs-lookup"><span data-stu-id="ba63c-175">Contains one row for each Extended Events event that is mapped to a SQL Trace event class.</span></span>|  
|[<span data-ttu-id="ba63c-176">trace_xe_action_map &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ba63c-176">trace_xe_action_map &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-tables/extended-events-tables-trace-xe-action-map)|<span data-ttu-id="ba63c-177">針對對應到 SQL 追蹤資料行識別碼的每個擴充事件動作包含一個資料列。</span><span class="sxs-lookup"><span data-stu-id="ba63c-177">Contains one row for each Extended Events action that is mapped to a SQL Trace column ID.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ba63c-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ba63c-178">See Also</span></span>  
 <span data-ttu-id="ba63c-179">[動態管理檢視與函數 &#40;Transact-SQL&#41;](../views/views.md) </span><span class="sxs-lookup"><span data-stu-id="ba63c-179">[Dynamic Management Views and Functions &#40;Transact-SQL&#41;](../views/views.md) </span></span>  
 <span data-ttu-id="ba63c-180">[目錄檢視 &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/catalog-views-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ba63c-180">[Catalog Views &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/catalog-views-transact-sql) </span></span>  
 <span data-ttu-id="ba63c-181">[SQL Server 擴充的事件資料表 &#40;Transact-sql&#41;](/sql/relational-databases/system-tables/system-tables-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ba63c-181">[SQL Server Extended Events Tables &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/system-tables-transact-sql) </span></span>  
 <span data-ttu-id="ba63c-182">[使用 system_health 會話](use-the-ssms-xe-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="ba63c-182">[Use the system_health Session](use-the-ssms-xe-profiler.md) </span></span>  
 [<span data-ttu-id="ba63c-183">針對擴充事件使用 PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="ba63c-183">Use the PowerShell Provider for Extended Events</span></span>](use-the-powershell-provider-for-extended-events.md)  
  
  