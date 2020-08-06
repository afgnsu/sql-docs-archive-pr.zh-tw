---
title: Audit Database Object Access 事件類別 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Audit Database Object Access event class
ms.assetid: 0294ba51-6085-4de2-a52d-dac1a87fbd4d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0549e6b4980dd0e0e0e569b9dd95cf404b216c29
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584542"
---
# <a name="audit-database-object-access-event-class"></a><span data-ttu-id="164e2-102">稽核資料庫物件存取事件類別</span><span class="sxs-lookup"><span data-stu-id="164e2-102">Audit Database Object Access Event Class</span></span>
  <span data-ttu-id="164e2-103">存取資料庫物件 (例如：結構描述) 時，會發生 **Audit Database Object Access** 事件類別。</span><span class="sxs-lookup"><span data-stu-id="164e2-103">The **Audit Database Object Access** event class occurs when database objects, such as schemas, are accessed.</span></span>  
  
## <a name="audit-database-object-access-event-class-data-columns"></a><span data-ttu-id="164e2-104">Audit Database Object Access 事件類別資料行</span><span class="sxs-lookup"><span data-stu-id="164e2-104">Audit Database Object Access Event Class Data Columns</span></span>  
  
|<span data-ttu-id="164e2-105">資料行名稱</span><span class="sxs-lookup"><span data-stu-id="164e2-105">Data column name</span></span>|<span data-ttu-id="164e2-106">資料類型</span><span class="sxs-lookup"><span data-stu-id="164e2-106">Data type</span></span>|<span data-ttu-id="164e2-107">描述</span><span class="sxs-lookup"><span data-stu-id="164e2-107">Description</span></span>|<span data-ttu-id="164e2-108">資料行識別碼</span><span class="sxs-lookup"><span data-stu-id="164e2-108">Column ID</span></span>|<span data-ttu-id="164e2-109">可篩選</span><span class="sxs-lookup"><span data-stu-id="164e2-109">Filterable</span></span>|  
|----------------------|---------------|-----------------|---------------|----------------|  
|<span data-ttu-id="164e2-110">**ApplicationName**</span><span class="sxs-lookup"><span data-stu-id="164e2-110">**ApplicationName**</span></span>|<span data-ttu-id="164e2-111">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="164e2-111">**nvarchar**</span></span>|<span data-ttu-id="164e2-112">建立 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體連線的用戶端應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="164e2-112">Name of the client application that created the connection to an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="164e2-113">這個資料行會填入應用程式所傳送的值，而非程式的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="164e2-113">This column is populated with the values passed by the application rather than the displayed name of the program.</span></span>|<span data-ttu-id="164e2-114">10</span><span class="sxs-lookup"><span data-stu-id="164e2-114">10</span></span>|<span data-ttu-id="164e2-115">是</span><span class="sxs-lookup"><span data-stu-id="164e2-115">Yes</span></span>|  
|<span data-ttu-id="164e2-116">**DatabaseID**</span><span class="sxs-lookup"><span data-stu-id="164e2-116">**DatabaseID**</span></span>|<span data-ttu-id="164e2-117">**int**</span><span class="sxs-lookup"><span data-stu-id="164e2-117">**int**</span></span>|<span data-ttu-id="164e2-118">由 USE *database* 陳述式所指定的資料庫識別碼，或者如果沒有針對指定執行個體發出 USE *database* 陳述式，則是預設的資料庫。</span><span class="sxs-lookup"><span data-stu-id="164e2-118">ID of the database specified by the USE *database* statement or the default database if no USE *database* statement has been issued for a given instance.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="164e2-119">資料行，則 **ServerName** 會顯示資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="164e2-119">displays the name of the database if the **ServerName** data column is captured in the trace and the server is available.</span></span> <span data-ttu-id="164e2-120">請使用 DB_ID 函數判斷資料庫的值。</span><span class="sxs-lookup"><span data-stu-id="164e2-120">Determine the value for a database by using the DB_ID function.</span></span>|<span data-ttu-id="164e2-121">3</span><span class="sxs-lookup"><span data-stu-id="164e2-121">3</span></span>|<span data-ttu-id="164e2-122">是</span><span class="sxs-lookup"><span data-stu-id="164e2-122">Yes</span></span>|  
|<span data-ttu-id="164e2-123">**DatabaseName**</span><span class="sxs-lookup"><span data-stu-id="164e2-123">**DatabaseName**</span></span>|<span data-ttu-id="164e2-124">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="164e2-124">**nvarchar**</span></span>|<span data-ttu-id="164e2-125">正在執行使用者陳述式的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="164e2-125">Name of the database in which the user statement is running.</span></span>|<span data-ttu-id="164e2-126">35</span><span class="sxs-lookup"><span data-stu-id="164e2-126">35</span></span>|<span data-ttu-id="164e2-127">是</span><span class="sxs-lookup"><span data-stu-id="164e2-127">Yes</span></span>|  
|<span data-ttu-id="164e2-128">**DBUserName**</span><span class="sxs-lookup"><span data-stu-id="164e2-128">**DBUserName**</span></span>|<span data-ttu-id="164e2-129">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="164e2-129">**nvarchar**</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="164e2-130">使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="164e2-130">user name of the client.</span></span>|<span data-ttu-id="164e2-131">40</span><span class="sxs-lookup"><span data-stu-id="164e2-131">40</span></span>|<span data-ttu-id="164e2-132">是</span><span class="sxs-lookup"><span data-stu-id="164e2-132">Yes</span></span>|  
|<span data-ttu-id="164e2-133">**EventSequence**</span><span class="sxs-lookup"><span data-stu-id="164e2-133">**EventSequence**</span></span>|<span data-ttu-id="164e2-134">**int**</span><span class="sxs-lookup"><span data-stu-id="164e2-134">**int**</span></span>|<span data-ttu-id="164e2-135">要求中的給定事件順序。</span><span class="sxs-lookup"><span data-stu-id="164e2-135">Sequence of a given event within the request.</span></span>|<span data-ttu-id="164e2-136">51</span><span class="sxs-lookup"><span data-stu-id="164e2-136">51</span></span>|<span data-ttu-id="164e2-137">否</span><span class="sxs-lookup"><span data-stu-id="164e2-137">No</span></span>|  
|<span data-ttu-id="164e2-138">**HostName**</span><span class="sxs-lookup"><span data-stu-id="164e2-138">**HostName**</span></span>|<span data-ttu-id="164e2-139">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="164e2-139">**nvarchar**</span></span>|<span data-ttu-id="164e2-140">執行用戶端的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="164e2-140">Name of the computer on which the client is running.</span></span> <span data-ttu-id="164e2-141">如果用戶端提供主機名稱，這個資料行就會擴展。</span><span class="sxs-lookup"><span data-stu-id="164e2-141">This data column is populated if the client provides the host name.</span></span> <span data-ttu-id="164e2-142">若要判斷主機名稱，請使用 HOST_NAME 函數。</span><span class="sxs-lookup"><span data-stu-id="164e2-142">To determine the host name, use the HOST_NAME function.</span></span>|<span data-ttu-id="164e2-143">8</span><span class="sxs-lookup"><span data-stu-id="164e2-143">8</span></span>|<span data-ttu-id="164e2-144">是</span><span class="sxs-lookup"><span data-stu-id="164e2-144">Yes</span></span>|  
|<span data-ttu-id="164e2-145">**IsSystem**</span><span class="sxs-lookup"><span data-stu-id="164e2-145">**IsSystem**</span></span>|<span data-ttu-id="164e2-146">**int**</span><span class="sxs-lookup"><span data-stu-id="164e2-146">**int**</span></span>|<span data-ttu-id="164e2-147">指出事件是發生在系統處理序或使用者處理序。</span><span class="sxs-lookup"><span data-stu-id="164e2-147">Indicates whether the event occurred on a system process or a user process.</span></span> <span data-ttu-id="164e2-148">1 = 系統，0 = 使用者。</span><span class="sxs-lookup"><span data-stu-id="164e2-148">1 = system, 0 = user.</span></span>|<span data-ttu-id="164e2-149">60</span><span class="sxs-lookup"><span data-stu-id="164e2-149">60</span></span>|<span data-ttu-id="164e2-150">是</span><span class="sxs-lookup"><span data-stu-id="164e2-150">Yes</span></span>|  
|<span data-ttu-id="164e2-151">**LoginName**</span><span class="sxs-lookup"><span data-stu-id="164e2-151">**LoginName**</span></span>|<span data-ttu-id="164e2-152">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="164e2-152">**nvarchar**</span></span>|<span data-ttu-id="164e2-153">使用者的登入名稱 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安全性登入或 DOMAIN\username 格式的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 登入認證)。</span><span class="sxs-lookup"><span data-stu-id="164e2-153">Name of the login of the user (either the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] security login or the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows login credentials in the form of DOMAIN\username).</span></span>|<span data-ttu-id="164e2-154">11</span><span class="sxs-lookup"><span data-stu-id="164e2-154">11</span></span>|<span data-ttu-id="164e2-155">是</span><span class="sxs-lookup"><span data-stu-id="164e2-155">Yes</span></span>|  
|<span data-ttu-id="164e2-156">**LoginSid**</span><span class="sxs-lookup"><span data-stu-id="164e2-156">**LoginSid**</span></span>|<span data-ttu-id="164e2-157">**image**</span><span class="sxs-lookup"><span data-stu-id="164e2-157">**image**</span></span>|<span data-ttu-id="164e2-158">已登入之使用者的安全性識別碼 (SID)。</span><span class="sxs-lookup"><span data-stu-id="164e2-158">Security identification number (SID) of the logged-in user.</span></span> <span data-ttu-id="164e2-159">您可以在 **sys.server_principals** 目錄檢視中找到這項資訊。</span><span class="sxs-lookup"><span data-stu-id="164e2-159">You can find this information in the **sys.server_principals** catalog view.</span></span> <span data-ttu-id="164e2-160">伺服器上的每一個登入之 SID 是唯一的。</span><span class="sxs-lookup"><span data-stu-id="164e2-160">Each SID is unique for each login in the server.</span></span>|<span data-ttu-id="164e2-161">41</span><span class="sxs-lookup"><span data-stu-id="164e2-161">41</span></span>|<span data-ttu-id="164e2-162">是</span><span class="sxs-lookup"><span data-stu-id="164e2-162">Yes</span></span>|  
|<span data-ttu-id="164e2-163">**NTDomainName**</span><span class="sxs-lookup"><span data-stu-id="164e2-163">**NTDomainName**</span></span>|<span data-ttu-id="164e2-164">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="164e2-164">**nvarchar**</span></span>|<span data-ttu-id="164e2-165">使用者所隸屬的 Windows 網域。</span><span class="sxs-lookup"><span data-stu-id="164e2-165">Windows domain to which the user belongs.</span></span>|<span data-ttu-id="164e2-166">7</span><span class="sxs-lookup"><span data-stu-id="164e2-166">7</span></span>|<span data-ttu-id="164e2-167">是</span><span class="sxs-lookup"><span data-stu-id="164e2-167">Yes</span></span>|  
|<span data-ttu-id="164e2-168">**NTUserName**</span><span class="sxs-lookup"><span data-stu-id="164e2-168">**NTUserName**</span></span>|<span data-ttu-id="164e2-169">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="164e2-169">**nvarchar**</span></span>|<span data-ttu-id="164e2-170">Windows 使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="164e2-170">Windows user name.</span></span>|<span data-ttu-id="164e2-171">6</span><span class="sxs-lookup"><span data-stu-id="164e2-171">6</span></span>|<span data-ttu-id="164e2-172">是</span><span class="sxs-lookup"><span data-stu-id="164e2-172">Yes</span></span>|  
|<span data-ttu-id="164e2-173">**ObjectName**</span><span class="sxs-lookup"><span data-stu-id="164e2-173">**ObjectName**</span></span>|<span data-ttu-id="164e2-174">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="164e2-174">**nvarchar**</span></span>|<span data-ttu-id="164e2-175">正在參考之物件的名稱。</span><span class="sxs-lookup"><span data-stu-id="164e2-175">Name of the object being referenced.</span></span>|<span data-ttu-id="164e2-176">34</span><span class="sxs-lookup"><span data-stu-id="164e2-176">34</span></span>|<span data-ttu-id="164e2-177">是</span><span class="sxs-lookup"><span data-stu-id="164e2-177">Yes</span></span>|  
|<span data-ttu-id="164e2-178">**ObjectType**</span><span class="sxs-lookup"><span data-stu-id="164e2-178">**ObjectType**</span></span>|<span data-ttu-id="164e2-179">**int**</span><span class="sxs-lookup"><span data-stu-id="164e2-179">**int**</span></span>|<span data-ttu-id="164e2-180">代表參與事件之物件類型的值。</span><span class="sxs-lookup"><span data-stu-id="164e2-180">Value representing the type of the object involved in the event.</span></span> <span data-ttu-id="164e2-181">這個值會對應到 **sys.objects** 目錄檢視中的類型資料行。</span><span class="sxs-lookup"><span data-stu-id="164e2-181">This value corresponds to the type column in the **sys.objects** catalog view.</span></span> <span data-ttu-id="164e2-182">針對各值，請參閱 [ObjectType 追蹤事件資料行](objecttype-trace-event-column.md)。</span><span class="sxs-lookup"><span data-stu-id="164e2-182">For values, see [ObjectType Trace Event Column](objecttype-trace-event-column.md).</span></span>|<span data-ttu-id="164e2-183">28</span><span class="sxs-lookup"><span data-stu-id="164e2-183">28</span></span>|<span data-ttu-id="164e2-184">是</span><span class="sxs-lookup"><span data-stu-id="164e2-184">Yes</span></span>|  
|<span data-ttu-id="164e2-185">**OwnerName**</span><span class="sxs-lookup"><span data-stu-id="164e2-185">**OwnerName**</span></span>|<span data-ttu-id="164e2-186">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="164e2-186">**nvarchar**</span></span>|<span data-ttu-id="164e2-187">物件擁有者的資料庫使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="164e2-187">Database user name of the object owner.</span></span>|<span data-ttu-id="164e2-188">37</span><span class="sxs-lookup"><span data-stu-id="164e2-188">37</span></span>|<span data-ttu-id="164e2-189">是</span><span class="sxs-lookup"><span data-stu-id="164e2-189">Yes</span></span>|  
|<span data-ttu-id="164e2-190">**權限**</span><span class="sxs-lookup"><span data-stu-id="164e2-190">**Permissions**</span></span>|<span data-ttu-id="164e2-191">**bigint**</span><span class="sxs-lookup"><span data-stu-id="164e2-191">**bigint**</span></span>|<span data-ttu-id="164e2-192">代表被檢查之權限類型的整數值。</span><span class="sxs-lookup"><span data-stu-id="164e2-192">Integer value representing the type of permissions checked.</span></span><br /><br /> <span data-ttu-id="164e2-193">1 = SELECT ALL</span><span class="sxs-lookup"><span data-stu-id="164e2-193">1 = SELECT ALL</span></span><br /><br /> <span data-ttu-id="164e2-194">2 = UPDATE ALL</span><span class="sxs-lookup"><span data-stu-id="164e2-194">2 = UPDATE ALL</span></span><br /><br /> <span data-ttu-id="164e2-195">4 = REFERENCES ALL</span><span class="sxs-lookup"><span data-stu-id="164e2-195">4 = REFERENCES ALL</span></span><br /><br /> <span data-ttu-id="164e2-196">8 = INSERT</span><span class="sxs-lookup"><span data-stu-id="164e2-196">8 = INSERT</span></span><br /><br /> <span data-ttu-id="164e2-197">16 = DELETE</span><span class="sxs-lookup"><span data-stu-id="164e2-197">16 = DELETE</span></span><br /><br /> <span data-ttu-id="164e2-198">32 = EXECUTE (限程序)</span><span class="sxs-lookup"><span data-stu-id="164e2-198">32 = EXECUTE (procedures only)</span></span>|<span data-ttu-id="164e2-199">19</span><span class="sxs-lookup"><span data-stu-id="164e2-199">19</span></span>|<span data-ttu-id="164e2-200">是</span><span class="sxs-lookup"><span data-stu-id="164e2-200">Yes</span></span>|  
|<span data-ttu-id="164e2-201">**RequestID**</span><span class="sxs-lookup"><span data-stu-id="164e2-201">**RequestID**</span></span>|<span data-ttu-id="164e2-202">**int**</span><span class="sxs-lookup"><span data-stu-id="164e2-202">**int**</span></span>|<span data-ttu-id="164e2-203">包含陳述式之要求的識別碼。</span><span class="sxs-lookup"><span data-stu-id="164e2-203">ID of the request containing the statement.</span></span>|<span data-ttu-id="164e2-204">49</span><span class="sxs-lookup"><span data-stu-id="164e2-204">49</span></span>|<span data-ttu-id="164e2-205">是</span><span class="sxs-lookup"><span data-stu-id="164e2-205">Yes</span></span>|  
|<span data-ttu-id="164e2-206">**ServerName**</span><span class="sxs-lookup"><span data-stu-id="164e2-206">**ServerName**</span></span>|<span data-ttu-id="164e2-207">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="164e2-207">**nvarchar**</span></span>|<span data-ttu-id="164e2-208">正在追蹤之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="164e2-208">Name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] being traced.</span></span>|<span data-ttu-id="164e2-209">26</span><span class="sxs-lookup"><span data-stu-id="164e2-209">26</span></span>|<span data-ttu-id="164e2-210">否</span><span class="sxs-lookup"><span data-stu-id="164e2-210">No</span></span>|  
|<span data-ttu-id="164e2-211">**SessionLoginName**</span><span class="sxs-lookup"><span data-stu-id="164e2-211">**SessionLoginName**</span></span>|<span data-ttu-id="164e2-212">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="164e2-212">**nvarchar**</span></span>|<span data-ttu-id="164e2-213">引發工作階段的使用者登入名稱。</span><span class="sxs-lookup"><span data-stu-id="164e2-213">The login name of the user who originated the session.</span></span> <span data-ttu-id="164e2-214">例如，如果您使用 Login1 連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，並以 Login2 執行陳述式，則 **SessionLoginName** 將顯示 Login1 而 **LoginName** 則顯示 Login2。</span><span class="sxs-lookup"><span data-stu-id="164e2-214">For example, if you connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Login1 and execute a statement as Login2, **SessionLoginName** shows Login1 and **LoginName** shows Login2.</span></span> <span data-ttu-id="164e2-215">此資料行將同時顯示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 Windows 登入。</span><span class="sxs-lookup"><span data-stu-id="164e2-215">This column displays both [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows logins.</span></span>|<span data-ttu-id="164e2-216">64</span><span class="sxs-lookup"><span data-stu-id="164e2-216">64</span></span>|<span data-ttu-id="164e2-217">是</span><span class="sxs-lookup"><span data-stu-id="164e2-217">Yes</span></span>|  
|<span data-ttu-id="164e2-218">**SPID**</span><span class="sxs-lookup"><span data-stu-id="164e2-218">**SPID**</span></span>|<span data-ttu-id="164e2-219">**int**</span><span class="sxs-lookup"><span data-stu-id="164e2-219">**int**</span></span>|<span data-ttu-id="164e2-220">事件發生所在之工作階段的識別碼。</span><span class="sxs-lookup"><span data-stu-id="164e2-220">ID of the session on which the event occurred.</span></span>|<span data-ttu-id="164e2-221">12</span><span class="sxs-lookup"><span data-stu-id="164e2-221">12</span></span>|<span data-ttu-id="164e2-222">是</span><span class="sxs-lookup"><span data-stu-id="164e2-222">Yes</span></span>|  
|<span data-ttu-id="164e2-223">**StartTime**</span><span class="sxs-lookup"><span data-stu-id="164e2-223">**StartTime**</span></span>|<span data-ttu-id="164e2-224">**datetime**</span><span class="sxs-lookup"><span data-stu-id="164e2-224">**datetime**</span></span>|<span data-ttu-id="164e2-225">事件啟動的時間 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="164e2-225">Time at which the event started, if available.</span></span>|<span data-ttu-id="164e2-226">14</span><span class="sxs-lookup"><span data-stu-id="164e2-226">14</span></span>|<span data-ttu-id="164e2-227">是</span><span class="sxs-lookup"><span data-stu-id="164e2-227">Yes</span></span>|  
|<span data-ttu-id="164e2-228">「成功」 </span><span class="sxs-lookup"><span data-stu-id="164e2-228">**Success**</span></span>|<span data-ttu-id="164e2-229">**int**</span><span class="sxs-lookup"><span data-stu-id="164e2-229">**int**</span></span>|<span data-ttu-id="164e2-230">1 = 成功。</span><span class="sxs-lookup"><span data-stu-id="164e2-230">1 = success.</span></span> <span data-ttu-id="164e2-231">0 = 失敗。</span><span class="sxs-lookup"><span data-stu-id="164e2-231">0 = failure.</span></span> <span data-ttu-id="164e2-232">例如，值為 1 指出權限檢查成功，而值為 0 指出該檢查失敗。</span><span class="sxs-lookup"><span data-stu-id="164e2-232">For example, a value of 1 indicates success of a permissions check and a value of 0 indicates failure of that check.</span></span>|<span data-ttu-id="164e2-233">23</span><span class="sxs-lookup"><span data-stu-id="164e2-233">23</span></span>|<span data-ttu-id="164e2-234">是</span><span class="sxs-lookup"><span data-stu-id="164e2-234">Yes</span></span>|  
|<span data-ttu-id="164e2-235">**TextData**</span><span class="sxs-lookup"><span data-stu-id="164e2-235">**TextData**</span></span>|<span data-ttu-id="164e2-236">**ntext**</span><span class="sxs-lookup"><span data-stu-id="164e2-236">**ntext**</span></span>|<span data-ttu-id="164e2-237">與追蹤中所擷取的事件類別有關的文字值。</span><span class="sxs-lookup"><span data-stu-id="164e2-237">Text value dependent on the event class captured in the trace.</span></span>|<span data-ttu-id="164e2-238">1</span><span class="sxs-lookup"><span data-stu-id="164e2-238">1</span></span>|<span data-ttu-id="164e2-239">是</span><span class="sxs-lookup"><span data-stu-id="164e2-239">Yes</span></span>|  
|<span data-ttu-id="164e2-240">**TransactionID**</span><span class="sxs-lookup"><span data-stu-id="164e2-240">**TransactionID**</span></span>|<span data-ttu-id="164e2-241">**bigint**</span><span class="sxs-lookup"><span data-stu-id="164e2-241">**bigint**</span></span>|<span data-ttu-id="164e2-242">由系統指派給交易的識別碼。</span><span class="sxs-lookup"><span data-stu-id="164e2-242">System-assigned ID of the transaction.</span></span>|<span data-ttu-id="164e2-243">4</span><span class="sxs-lookup"><span data-stu-id="164e2-243">4</span></span>|<span data-ttu-id="164e2-244">是</span><span class="sxs-lookup"><span data-stu-id="164e2-244">Yes</span></span>|  
|<span data-ttu-id="164e2-245">**XactSequence**</span><span class="sxs-lookup"><span data-stu-id="164e2-245">**XactSequence**</span></span>|<span data-ttu-id="164e2-246">**bigint**</span><span class="sxs-lookup"><span data-stu-id="164e2-246">**bigint**</span></span>|<span data-ttu-id="164e2-247">用來描述目前交易的 Token。</span><span class="sxs-lookup"><span data-stu-id="164e2-247">Token used to describe the current transaction.</span></span>|<span data-ttu-id="164e2-248">50</span><span class="sxs-lookup"><span data-stu-id="164e2-248">50</span></span>|<span data-ttu-id="164e2-249">是</span><span class="sxs-lookup"><span data-stu-id="164e2-249">Yes</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="164e2-250">另請參閱</span><span class="sxs-lookup"><span data-stu-id="164e2-250">See Also</span></span>  
 <span data-ttu-id="164e2-251">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="164e2-251">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span></span>  
 [<span data-ttu-id="164e2-252">SQL Server Profiler</span><span class="sxs-lookup"><span data-stu-id="164e2-252">SQL Server Profiler</span></span>](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  