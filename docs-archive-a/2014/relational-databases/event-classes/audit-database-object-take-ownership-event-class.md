---
title: Audit Database Object Take Ownership 事件類別 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Audit Database Object Take Ownership event class
ms.assetid: 26409a60-9616-484b-b608-ca554aef08f6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 427d48eaa8f4c0812a86ab7c85851ed61afe1d1d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595023"
---
# <a name="audit-database-object-take-ownership-event-class"></a><span data-ttu-id="119ab-102">Audit Database Object Take Ownership 事件類別</span><span class="sxs-lookup"><span data-stu-id="119ab-102">Audit Database Object Take Ownership Event Class</span></span>
  <span data-ttu-id="119ab-103">**Audit Database Object Take Ownership** 事件類別會在資料庫範圍內的物件擁有者有所變更時發生。</span><span class="sxs-lookup"><span data-stu-id="119ab-103">The **Audit Database Object Take Ownership** event class occurs when a change of owner for objects within database scope occurs.</span></span>  
  
## <a name="audit-database-object-take-ownership-event-class-data-columns"></a><span data-ttu-id="119ab-104">Audit Database Object Take Ownership 事件類別資料行</span><span class="sxs-lookup"><span data-stu-id="119ab-104">Audit Database Object Take Ownership Event Class Data Columns</span></span>  
  
|<span data-ttu-id="119ab-105">資料行名稱</span><span class="sxs-lookup"><span data-stu-id="119ab-105">Data column name</span></span>|<span data-ttu-id="119ab-106">資料類型</span><span class="sxs-lookup"><span data-stu-id="119ab-106">Data type</span></span>|<span data-ttu-id="119ab-107">描述</span><span class="sxs-lookup"><span data-stu-id="119ab-107">Description</span></span>|<span data-ttu-id="119ab-108">資料行識別碼</span><span class="sxs-lookup"><span data-stu-id="119ab-108">Column ID</span></span>|<span data-ttu-id="119ab-109">可篩選</span><span class="sxs-lookup"><span data-stu-id="119ab-109">Filterable</span></span>|  
|----------------------|---------------|-----------------|---------------|----------------|  
|<span data-ttu-id="119ab-110">**ApplicationName**</span><span class="sxs-lookup"><span data-stu-id="119ab-110">**ApplicationName**</span></span>|<span data-ttu-id="119ab-111">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="119ab-111">**nvarchar**</span></span>|<span data-ttu-id="119ab-112">建立 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體連線的用戶端應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="119ab-112">Name of the client application that created the connection to an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="119ab-113">這個資料行會填入應用程式所傳送的值，而非程式的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="119ab-113">This column is populated with the values passed by the application rather than the displayed name of the program.</span></span>|<span data-ttu-id="119ab-114">10</span><span class="sxs-lookup"><span data-stu-id="119ab-114">10</span></span>|<span data-ttu-id="119ab-115">是</span><span class="sxs-lookup"><span data-stu-id="119ab-115">Yes</span></span>|  
|<span data-ttu-id="119ab-116">**DatabaseID**</span><span class="sxs-lookup"><span data-stu-id="119ab-116">**DatabaseID**</span></span>|<span data-ttu-id="119ab-117">**int**</span><span class="sxs-lookup"><span data-stu-id="119ab-117">**int**</span></span>|<span data-ttu-id="119ab-118">由 USE *database* 陳述式所指定的資料庫識別碼，或者如果沒有針對指定執行個體發出 USE *database* 陳述式，則是預設的資料庫。</span><span class="sxs-lookup"><span data-stu-id="119ab-118">ID of the database specified by the USE *database* statement or the default database if no USE *database* statement has been issued for a given instance.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="119ab-119">資料行，則 **ServerName** 會顯示資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="119ab-119">displays the name of the database if the **ServerName** data column is captured in the trace and the server is available.</span></span> <span data-ttu-id="119ab-120">請使用 DB_ID 函數判斷資料庫的值。</span><span class="sxs-lookup"><span data-stu-id="119ab-120">Determine the value for a database by using the DB_ID function.</span></span>|<span data-ttu-id="119ab-121">3</span><span class="sxs-lookup"><span data-stu-id="119ab-121">3</span></span>|<span data-ttu-id="119ab-122">是</span><span class="sxs-lookup"><span data-stu-id="119ab-122">Yes</span></span>|  
|<span data-ttu-id="119ab-123">**DatabaseName**</span><span class="sxs-lookup"><span data-stu-id="119ab-123">**DatabaseName**</span></span>|<span data-ttu-id="119ab-124">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="119ab-124">**nvarchar**</span></span>|<span data-ttu-id="119ab-125">正在執行使用者陳述式的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="119ab-125">Name of the database in which the user statement is running.</span></span>|<span data-ttu-id="119ab-126">35</span><span class="sxs-lookup"><span data-stu-id="119ab-126">35</span></span>|<span data-ttu-id="119ab-127">是</span><span class="sxs-lookup"><span data-stu-id="119ab-127">Yes</span></span>|  
|<span data-ttu-id="119ab-128">**DBUserName**</span><span class="sxs-lookup"><span data-stu-id="119ab-128">**DBUserName**</span></span>|<span data-ttu-id="119ab-129">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="119ab-129">**nvarchar**</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="119ab-130">使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="119ab-130">user name of the client.</span></span>|<span data-ttu-id="119ab-131">40</span><span class="sxs-lookup"><span data-stu-id="119ab-131">40</span></span>|<span data-ttu-id="119ab-132">是</span><span class="sxs-lookup"><span data-stu-id="119ab-132">Yes</span></span>|  
|<span data-ttu-id="119ab-133">**EventSequence**</span><span class="sxs-lookup"><span data-stu-id="119ab-133">**EventSequence**</span></span>|<span data-ttu-id="119ab-134">**int**</span><span class="sxs-lookup"><span data-stu-id="119ab-134">**int**</span></span>|<span data-ttu-id="119ab-135">要求中的給定事件順序。</span><span class="sxs-lookup"><span data-stu-id="119ab-135">Sequence of a given event within the request.</span></span>|<span data-ttu-id="119ab-136">51</span><span class="sxs-lookup"><span data-stu-id="119ab-136">51</span></span>|<span data-ttu-id="119ab-137">否</span><span class="sxs-lookup"><span data-stu-id="119ab-137">No</span></span>|  
|<span data-ttu-id="119ab-138">**HostName**</span><span class="sxs-lookup"><span data-stu-id="119ab-138">**HostName**</span></span>|<span data-ttu-id="119ab-139">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="119ab-139">**nvarchar**</span></span>|<span data-ttu-id="119ab-140">執行用戶端的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="119ab-140">Name of the computer on which the client is running.</span></span> <span data-ttu-id="119ab-141">如果用戶端提供主機名稱，這個資料行就會擴展。</span><span class="sxs-lookup"><span data-stu-id="119ab-141">This data column is populated if the client provides the host name.</span></span> <span data-ttu-id="119ab-142">若要判斷主機名稱，請使用 HOST_NAME 函數。</span><span class="sxs-lookup"><span data-stu-id="119ab-142">To determine the host name, use the HOST_NAME function.</span></span>|<span data-ttu-id="119ab-143">8</span><span class="sxs-lookup"><span data-stu-id="119ab-143">8</span></span>|<span data-ttu-id="119ab-144">是</span><span class="sxs-lookup"><span data-stu-id="119ab-144">Yes</span></span>|  
|<span data-ttu-id="119ab-145">**IsSystem**</span><span class="sxs-lookup"><span data-stu-id="119ab-145">**IsSystem**</span></span>|<span data-ttu-id="119ab-146">**int**</span><span class="sxs-lookup"><span data-stu-id="119ab-146">**int**</span></span>|<span data-ttu-id="119ab-147">指出事件是發生在系統處理序或使用者處理序。</span><span class="sxs-lookup"><span data-stu-id="119ab-147">Indicates whether the event occurred on a system process or a user process.</span></span> <span data-ttu-id="119ab-148">1 = 系統，0 = 使用者。</span><span class="sxs-lookup"><span data-stu-id="119ab-148">1 = system, 0 = user.</span></span>|<span data-ttu-id="119ab-149">60</span><span class="sxs-lookup"><span data-stu-id="119ab-149">60</span></span>|<span data-ttu-id="119ab-150">是</span><span class="sxs-lookup"><span data-stu-id="119ab-150">Yes</span></span>|  
|<span data-ttu-id="119ab-151">**LoginName**</span><span class="sxs-lookup"><span data-stu-id="119ab-151">**LoginName**</span></span>|<span data-ttu-id="119ab-152">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="119ab-152">**nvarchar**</span></span>|<span data-ttu-id="119ab-153">使用者的登入名稱 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安全性登入或 DOMAIN\username 格式的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 登入認證)。</span><span class="sxs-lookup"><span data-stu-id="119ab-153">Name of the login of the user (either the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] security login or the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows login credentials in the form of DOMAIN\username).</span></span>|<span data-ttu-id="119ab-154">11</span><span class="sxs-lookup"><span data-stu-id="119ab-154">11</span></span>|<span data-ttu-id="119ab-155">是</span><span class="sxs-lookup"><span data-stu-id="119ab-155">Yes</span></span>|  
|<span data-ttu-id="119ab-156">**LoginSid**</span><span class="sxs-lookup"><span data-stu-id="119ab-156">**LoginSid**</span></span>|<span data-ttu-id="119ab-157">**image**</span><span class="sxs-lookup"><span data-stu-id="119ab-157">**image**</span></span>|<span data-ttu-id="119ab-158">已登入之使用者的安全性識別碼 (SID)。</span><span class="sxs-lookup"><span data-stu-id="119ab-158">Security identification number (SID) of the logged-in user.</span></span> <span data-ttu-id="119ab-159">您可以在 **sys.server_principals** 目錄檢視中找到這項資訊。</span><span class="sxs-lookup"><span data-stu-id="119ab-159">You can find this information in the **sys.server_principals** catalog view.</span></span> <span data-ttu-id="119ab-160">伺服器上的每一個登入之 SID 是唯一的。</span><span class="sxs-lookup"><span data-stu-id="119ab-160">Each SID is unique for each login in the server.</span></span>|<span data-ttu-id="119ab-161">41</span><span class="sxs-lookup"><span data-stu-id="119ab-161">41</span></span>|<span data-ttu-id="119ab-162">是</span><span class="sxs-lookup"><span data-stu-id="119ab-162">Yes</span></span>|  
|<span data-ttu-id="119ab-163">**NTDomainName**</span><span class="sxs-lookup"><span data-stu-id="119ab-163">**NTDomainName**</span></span>|<span data-ttu-id="119ab-164">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="119ab-164">**nvarchar**</span></span>|<span data-ttu-id="119ab-165">使用者所隸屬的 Windows 網域。</span><span class="sxs-lookup"><span data-stu-id="119ab-165">Windows domain to which the user belongs.</span></span>|<span data-ttu-id="119ab-166">7</span><span class="sxs-lookup"><span data-stu-id="119ab-166">7</span></span>|<span data-ttu-id="119ab-167">是</span><span class="sxs-lookup"><span data-stu-id="119ab-167">Yes</span></span>|  
|<span data-ttu-id="119ab-168">**NTUserName**</span><span class="sxs-lookup"><span data-stu-id="119ab-168">**NTUserName**</span></span>|<span data-ttu-id="119ab-169">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="119ab-169">**nvarchar**</span></span>|<span data-ttu-id="119ab-170">Windows 使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="119ab-170">Windows user name.</span></span>|<span data-ttu-id="119ab-171">6</span><span class="sxs-lookup"><span data-stu-id="119ab-171">6</span></span>|<span data-ttu-id="119ab-172">是</span><span class="sxs-lookup"><span data-stu-id="119ab-172">Yes</span></span>|  
|<span data-ttu-id="119ab-173">**ObjectName**</span><span class="sxs-lookup"><span data-stu-id="119ab-173">**ObjectName**</span></span>|<span data-ttu-id="119ab-174">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="119ab-174">**nvarchar**</span></span>|<span data-ttu-id="119ab-175">正在參考之物件的名稱。</span><span class="sxs-lookup"><span data-stu-id="119ab-175">Name of the object being referenced.</span></span>|<span data-ttu-id="119ab-176">34</span><span class="sxs-lookup"><span data-stu-id="119ab-176">34</span></span>|<span data-ttu-id="119ab-177">是</span><span class="sxs-lookup"><span data-stu-id="119ab-177">Yes</span></span>|  
|<span data-ttu-id="119ab-178">**ObjectType**</span><span class="sxs-lookup"><span data-stu-id="119ab-178">**ObjectType**</span></span>|<span data-ttu-id="119ab-179">**int**</span><span class="sxs-lookup"><span data-stu-id="119ab-179">**int**</span></span>|<span data-ttu-id="119ab-180">代表參與事件之物件類型的值。</span><span class="sxs-lookup"><span data-stu-id="119ab-180">Value representing the type of the object involved in the event.</span></span> <span data-ttu-id="119ab-181">這個資料行傳回的值是 **sys.objects** 目錄檢視之 **type** 資料行中對應值與 [ObjectType 追蹤事件資料行](objecttype-trace-event-column.md)中列出值的組合。</span><span class="sxs-lookup"><span data-stu-id="119ab-181">The value returned for this column is a combination of the corresponding value in the **type** column in the **sys.objects** catalog view and the values listed in [ObjectType Trace Event Column](objecttype-trace-event-column.md).</span></span> <span data-ttu-id="119ab-182">例如，如果傳回 8277-U，則物件類型是使用者自訂資料表。</span><span class="sxs-lookup"><span data-stu-id="119ab-182">For example, if 8277-U is returned, the object type is user-defined table.</span></span>|<span data-ttu-id="119ab-183">28</span><span class="sxs-lookup"><span data-stu-id="119ab-183">28</span></span>|<span data-ttu-id="119ab-184">是</span><span class="sxs-lookup"><span data-stu-id="119ab-184">Yes</span></span>|  
|<span data-ttu-id="119ab-185">**OwnerName**</span><span class="sxs-lookup"><span data-stu-id="119ab-185">**OwnerName**</span></span>|<span data-ttu-id="119ab-186">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="119ab-186">**nvarchar**</span></span>|<span data-ttu-id="119ab-187">物件擁有者的資料庫使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="119ab-187">Database user name of the object owner.</span></span>|<span data-ttu-id="119ab-188">37</span><span class="sxs-lookup"><span data-stu-id="119ab-188">37</span></span>|<span data-ttu-id="119ab-189">是</span><span class="sxs-lookup"><span data-stu-id="119ab-189">Yes</span></span>|  
|<span data-ttu-id="119ab-190">**RequestID**</span><span class="sxs-lookup"><span data-stu-id="119ab-190">**RequestID**</span></span>|<span data-ttu-id="119ab-191">**int**</span><span class="sxs-lookup"><span data-stu-id="119ab-191">**int**</span></span>|<span data-ttu-id="119ab-192">包含陳述式之要求的識別碼。</span><span class="sxs-lookup"><span data-stu-id="119ab-192">ID of the request containing the statement.</span></span>|<span data-ttu-id="119ab-193">49</span><span class="sxs-lookup"><span data-stu-id="119ab-193">49</span></span>|<span data-ttu-id="119ab-194">是</span><span class="sxs-lookup"><span data-stu-id="119ab-194">Yes</span></span>|  
|<span data-ttu-id="119ab-195">**ServerName**</span><span class="sxs-lookup"><span data-stu-id="119ab-195">**ServerName**</span></span>|<span data-ttu-id="119ab-196">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="119ab-196">**nvarchar**</span></span>|<span data-ttu-id="119ab-197">正在追蹤之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="119ab-197">Name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] being traced.</span></span>|<span data-ttu-id="119ab-198">26</span><span class="sxs-lookup"><span data-stu-id="119ab-198">26</span></span>|<span data-ttu-id="119ab-199">否</span><span class="sxs-lookup"><span data-stu-id="119ab-199">No</span></span>|  
|<span data-ttu-id="119ab-200">**SessionLoginName**</span><span class="sxs-lookup"><span data-stu-id="119ab-200">**SessionLoginName**</span></span>|<span data-ttu-id="119ab-201">**Nvarchar**</span><span class="sxs-lookup"><span data-stu-id="119ab-201">**Nvarchar**</span></span>|<span data-ttu-id="119ab-202">引發工作階段之使用者的登入名稱。</span><span class="sxs-lookup"><span data-stu-id="119ab-202">Login name of the user who originated the session.</span></span> <span data-ttu-id="119ab-203">例如，如果您使用 Login1 連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，並以 Login2 執行陳述式，則 **SessionLoginName** 將顯示 Login1 而 **LoginName** 則顯示 Login2。</span><span class="sxs-lookup"><span data-stu-id="119ab-203">For example, if you connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Login1 and execute a statement as Login2, **SessionLoginName** shows Login1 and **LoginName** shows Login2.</span></span> <span data-ttu-id="119ab-204">此資料行將同時顯示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 Windows 登入。</span><span class="sxs-lookup"><span data-stu-id="119ab-204">This column displays both [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows logins.</span></span>|<span data-ttu-id="119ab-205">64</span><span class="sxs-lookup"><span data-stu-id="119ab-205">64</span></span>|<span data-ttu-id="119ab-206">是</span><span class="sxs-lookup"><span data-stu-id="119ab-206">Yes</span></span>|  
|<span data-ttu-id="119ab-207">**SPID**</span><span class="sxs-lookup"><span data-stu-id="119ab-207">**SPID**</span></span>|<span data-ttu-id="119ab-208">**int**</span><span class="sxs-lookup"><span data-stu-id="119ab-208">**int**</span></span>|<span data-ttu-id="119ab-209">事件發生所在之工作階段的識別碼。</span><span class="sxs-lookup"><span data-stu-id="119ab-209">ID of the session on which the event occurred.</span></span>|<span data-ttu-id="119ab-210">12</span><span class="sxs-lookup"><span data-stu-id="119ab-210">12</span></span>|<span data-ttu-id="119ab-211">是</span><span class="sxs-lookup"><span data-stu-id="119ab-211">Yes</span></span>|  
|<span data-ttu-id="119ab-212">**StartTime**</span><span class="sxs-lookup"><span data-stu-id="119ab-212">**StartTime**</span></span>|<span data-ttu-id="119ab-213">**datetime**</span><span class="sxs-lookup"><span data-stu-id="119ab-213">**datetime**</span></span>|<span data-ttu-id="119ab-214">事件啟動的時間 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="119ab-214">Time at which the event started, if available.</span></span>|<span data-ttu-id="119ab-215">14</span><span class="sxs-lookup"><span data-stu-id="119ab-215">14</span></span>|<span data-ttu-id="119ab-216">是</span><span class="sxs-lookup"><span data-stu-id="119ab-216">Yes</span></span>|  
|<span data-ttu-id="119ab-217">「成功」 </span><span class="sxs-lookup"><span data-stu-id="119ab-217">**Success**</span></span>|<span data-ttu-id="119ab-218">**int**</span><span class="sxs-lookup"><span data-stu-id="119ab-218">**int**</span></span>|<span data-ttu-id="119ab-219">1 = 成功。</span><span class="sxs-lookup"><span data-stu-id="119ab-219">1 = success.</span></span> <span data-ttu-id="119ab-220">0 = 失敗。</span><span class="sxs-lookup"><span data-stu-id="119ab-220">0 = failure.</span></span> <span data-ttu-id="119ab-221">例如，值為 1 表示權限檢查成功，值為 0 表示該檢查失敗。</span><span class="sxs-lookup"><span data-stu-id="119ab-221">For example, a value of 1 indicates success of a permissions check and a value of 0 indicates a failure of that check.</span></span>|<span data-ttu-id="119ab-222">23</span><span class="sxs-lookup"><span data-stu-id="119ab-222">23</span></span>|<span data-ttu-id="119ab-223">是</span><span class="sxs-lookup"><span data-stu-id="119ab-223">Yes</span></span>|  
|<span data-ttu-id="119ab-224">**TargetUserName**</span><span class="sxs-lookup"><span data-stu-id="119ab-224">**TargetUserName**</span></span>|<span data-ttu-id="119ab-225">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="119ab-225">**nvarchar**</span></span>|<span data-ttu-id="119ab-226">對於目標為資料庫使用者的動作 (例如，授與使用者權限)，這是該使用者的名稱。</span><span class="sxs-lookup"><span data-stu-id="119ab-226">For actions that target a database user (for example, granting permission to a user), the name of that user.</span></span>|<span data-ttu-id="119ab-227">39</span><span class="sxs-lookup"><span data-stu-id="119ab-227">39</span></span>|<span data-ttu-id="119ab-228">是</span><span class="sxs-lookup"><span data-stu-id="119ab-228">Yes</span></span>|  
|<span data-ttu-id="119ab-229">**TextData**</span><span class="sxs-lookup"><span data-stu-id="119ab-229">**TextData**</span></span>|<span data-ttu-id="119ab-230">**ntext**</span><span class="sxs-lookup"><span data-stu-id="119ab-230">**ntext**</span></span>|<span data-ttu-id="119ab-231">與追蹤中所擷取的事件類別有關的文字值。</span><span class="sxs-lookup"><span data-stu-id="119ab-231">Text value dependent on the event class captured in the trace.</span></span>|<span data-ttu-id="119ab-232">1</span><span class="sxs-lookup"><span data-stu-id="119ab-232">1</span></span>|<span data-ttu-id="119ab-233">是</span><span class="sxs-lookup"><span data-stu-id="119ab-233">Yes</span></span>|  
|<span data-ttu-id="119ab-234">**TransactionID**</span><span class="sxs-lookup"><span data-stu-id="119ab-234">**TransactionID**</span></span>|<span data-ttu-id="119ab-235">**bigint**</span><span class="sxs-lookup"><span data-stu-id="119ab-235">**bigint**</span></span>|<span data-ttu-id="119ab-236">由系統指派給交易的識別碼。</span><span class="sxs-lookup"><span data-stu-id="119ab-236">System-assigned ID of the transaction.</span></span>|<span data-ttu-id="119ab-237">4</span><span class="sxs-lookup"><span data-stu-id="119ab-237">4</span></span>|<span data-ttu-id="119ab-238">是</span><span class="sxs-lookup"><span data-stu-id="119ab-238">Yes</span></span>|  
|<span data-ttu-id="119ab-239">**XactSequence**</span><span class="sxs-lookup"><span data-stu-id="119ab-239">**XactSequence**</span></span>|<span data-ttu-id="119ab-240">**bigint**</span><span class="sxs-lookup"><span data-stu-id="119ab-240">**bigint**</span></span>|<span data-ttu-id="119ab-241">用來描述目前交易的 Token。</span><span class="sxs-lookup"><span data-stu-id="119ab-241">Token used to describe the current transaction.</span></span>|<span data-ttu-id="119ab-242">50</span><span class="sxs-lookup"><span data-stu-id="119ab-242">50</span></span>|<span data-ttu-id="119ab-243">是</span><span class="sxs-lookup"><span data-stu-id="119ab-243">Yes</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="119ab-244">另請參閱</span><span class="sxs-lookup"><span data-stu-id="119ab-244">See Also</span></span>  
 [<span data-ttu-id="119ab-245">sp_trace_setevent &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="119ab-245">sp_trace_setevent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  