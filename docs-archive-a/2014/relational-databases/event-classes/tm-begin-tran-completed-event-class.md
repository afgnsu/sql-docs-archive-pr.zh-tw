---
title: 'TM: Begin Tran Completed 事件類別 | Microsoft 文件'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- 'TM: Begin Tran Completed event class'
ms.assetid: 95ddd3c6-51ef-4ad1-afd0-3aed82c9f724
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6e1703afb1f34d65b92d30ae2b7f2c7e6c9b0eac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710642"
---
# <a name="tm-begin-tran-completed-event-class"></a><span data-ttu-id="4d09b-102">TM: Begin Tran Completed 事件類別</span><span class="sxs-lookup"><span data-stu-id="4d09b-102">TM: Begin Tran Completed Event Class</span></span>
  <span data-ttu-id="4d09b-103">TM: Begin Tran Completed 事件類別表示 BEGIN TRANSACTION 要求已完成。</span><span class="sxs-lookup"><span data-stu-id="4d09b-103">The TM: Begin Tran Completed event class indicates that a BEGIN TRANSACTION request has been completed.</span></span> <span data-ttu-id="4d09b-104">要求是從用戶端透過交易管理介面傳送。</span><span class="sxs-lookup"><span data-stu-id="4d09b-104">The request was sent from the client through the transaction management interface.</span></span>  
  
## <a name="tm-begin-tran-completed-event-class-data-columns"></a><span data-ttu-id="4d09b-105">TM: Begin Tran Completed 事件類別資料行</span><span class="sxs-lookup"><span data-stu-id="4d09b-105">TM: Begin Tran Completed Event Class Data Columns</span></span>  
  
|<span data-ttu-id="4d09b-106">資料行名稱</span><span class="sxs-lookup"><span data-stu-id="4d09b-106">Data column name</span></span>|<span data-ttu-id="4d09b-107">資料類型</span><span class="sxs-lookup"><span data-stu-id="4d09b-107">Data type</span></span>|<span data-ttu-id="4d09b-108">描述</span><span class="sxs-lookup"><span data-stu-id="4d09b-108">Description</span></span>|<span data-ttu-id="4d09b-109">資料行識別碼</span><span class="sxs-lookup"><span data-stu-id="4d09b-109">Column ID</span></span>|<span data-ttu-id="4d09b-110">可篩選</span><span class="sxs-lookup"><span data-stu-id="4d09b-110">Filterable</span></span>|  
|----------------------|---------------|-----------------|---------------|----------------|  
|<span data-ttu-id="4d09b-111">ApplicationName</span><span class="sxs-lookup"><span data-stu-id="4d09b-111">ApplicationName</span></span>|`nvarchar`|<span data-ttu-id="4d09b-112">建立 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體之連接的用戶端應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="4d09b-112">Name of the client application that created the connection to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="4d09b-113">這個資料行會填入應用程式所傳送的值，而非程式的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="4d09b-113">This column is populated with the values passed by the application rather than the displayed name of the program.</span></span>|<span data-ttu-id="4d09b-114">10</span><span class="sxs-lookup"><span data-stu-id="4d09b-114">10</span></span>|<span data-ttu-id="4d09b-115">是</span><span class="sxs-lookup"><span data-stu-id="4d09b-115">Yes</span></span>|  
|<span data-ttu-id="4d09b-116">ClientProcessID</span><span class="sxs-lookup"><span data-stu-id="4d09b-116">ClientProcessID</span></span>|`int`|<span data-ttu-id="4d09b-117">由主機電腦指派給處理序 (用戶端應用程式執行所在) 的識別碼。</span><span class="sxs-lookup"><span data-stu-id="4d09b-117">ID assigned by the host computer to the process where the client application is running.</span></span> <span data-ttu-id="4d09b-118">如果用戶端提供用戶端處理序識別碼，這個資料行就會擴展。</span><span class="sxs-lookup"><span data-stu-id="4d09b-118">This data column is populated if the client provides the client process ID.</span></span>|<span data-ttu-id="4d09b-119">9</span><span class="sxs-lookup"><span data-stu-id="4d09b-119">9</span></span>|<span data-ttu-id="4d09b-120">是</span><span class="sxs-lookup"><span data-stu-id="4d09b-120">Yes</span></span>|  
|<span data-ttu-id="4d09b-121">DatabaseID</span><span class="sxs-lookup"><span data-stu-id="4d09b-121">DatabaseID</span></span>|`int`|<span data-ttu-id="4d09b-122">由 USE database 陳述式所指定的資料庫識別碼，或者如果沒有針對指定執行個體發出 USE database 陳述式，則是預設的資料庫。</span><span class="sxs-lookup"><span data-stu-id="4d09b-122">ID of the database specified by the USE database statement or the default database if no USE database statement has been issued for a given instance.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="4d09b-123">如果在追蹤中擷取 ServerName 資料行，則會顯示資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="4d09b-123">displays the name of the database if the ServerName data column is captured in the trace and the server is available.</span></span> <span data-ttu-id="4d09b-124">請使用 DB_ID 函數判斷資料庫的值。</span><span class="sxs-lookup"><span data-stu-id="4d09b-124">Determine the value for a database by using the DB_ID function.</span></span>|<span data-ttu-id="4d09b-125">3</span><span class="sxs-lookup"><span data-stu-id="4d09b-125">3</span></span>|<span data-ttu-id="4d09b-126">是</span><span class="sxs-lookup"><span data-stu-id="4d09b-126">Yes</span></span>|  
|<span data-ttu-id="4d09b-127">DatabaseName</span><span class="sxs-lookup"><span data-stu-id="4d09b-127">DatabaseName</span></span>|`nvarchar`|<span data-ttu-id="4d09b-128">正在執行使用者陳述式的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="4d09b-128">Name of the database in which the user statement is running.</span></span>|<span data-ttu-id="4d09b-129">35</span><span class="sxs-lookup"><span data-stu-id="4d09b-129">35</span></span>|<span data-ttu-id="4d09b-130">是</span><span class="sxs-lookup"><span data-stu-id="4d09b-130">Yes</span></span>|  
|<span data-ttu-id="4d09b-131">錯誤</span><span class="sxs-lookup"><span data-stu-id="4d09b-131">Error</span></span>|`int`|<span data-ttu-id="4d09b-132">給定事件的錯誤號碼。</span><span class="sxs-lookup"><span data-stu-id="4d09b-132">Error number of a given event.</span></span> <span data-ttu-id="4d09b-133">通常這是存放在 sys.messages 目錄檢視中的錯誤號碼。</span><span class="sxs-lookup"><span data-stu-id="4d09b-133">Often this is the error number stored in the sys.messages catalog view.</span></span>|<span data-ttu-id="4d09b-134">31</span><span class="sxs-lookup"><span data-stu-id="4d09b-134">31</span></span>|<span data-ttu-id="4d09b-135">是</span><span class="sxs-lookup"><span data-stu-id="4d09b-135">Yes</span></span>|  
|<span data-ttu-id="4d09b-136">EventClass</span><span class="sxs-lookup"><span data-stu-id="4d09b-136">EventClass</span></span>|`int`|<span data-ttu-id="4d09b-137">事件類型 = 182。</span><span class="sxs-lookup"><span data-stu-id="4d09b-137">Type of event = 182.</span></span>|<span data-ttu-id="4d09b-138">27</span><span class="sxs-lookup"><span data-stu-id="4d09b-138">27</span></span>|<span data-ttu-id="4d09b-139">否</span><span class="sxs-lookup"><span data-stu-id="4d09b-139">No</span></span>|  
|<span data-ttu-id="4d09b-140">EventSequence</span><span class="sxs-lookup"><span data-stu-id="4d09b-140">EventSequence</span></span>|`int`|<span data-ttu-id="4d09b-141">要求中之給定事件的順序。</span><span class="sxs-lookup"><span data-stu-id="4d09b-141">The sequence of a given event within the request.</span></span>|<span data-ttu-id="4d09b-142">51</span><span class="sxs-lookup"><span data-stu-id="4d09b-142">51</span></span>|<span data-ttu-id="4d09b-143">否</span><span class="sxs-lookup"><span data-stu-id="4d09b-143">No</span></span>|  
|<span data-ttu-id="4d09b-144">GroupID</span><span class="sxs-lookup"><span data-stu-id="4d09b-144">GroupID</span></span>|`int`|<span data-ttu-id="4d09b-145">SQL 追蹤事件引發所在之工作負載群組的識別碼。</span><span class="sxs-lookup"><span data-stu-id="4d09b-145">ID of the workload group where the SQL Trace event fires.</span></span>|<span data-ttu-id="4d09b-146">66</span><span class="sxs-lookup"><span data-stu-id="4d09b-146">66</span></span>|<span data-ttu-id="4d09b-147">是</span><span class="sxs-lookup"><span data-stu-id="4d09b-147">Yes</span></span>|  
|<span data-ttu-id="4d09b-148">HostName</span><span class="sxs-lookup"><span data-stu-id="4d09b-148">HostName</span></span>|`nvarchar`|<span data-ttu-id="4d09b-149">執行用戶端的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="4d09b-149">Name of the computer on which the client is running.</span></span> <span data-ttu-id="4d09b-150">如果用戶端提供主機名稱，這個資料行就會擴展。</span><span class="sxs-lookup"><span data-stu-id="4d09b-150">This data column is populated if the client provides the host name.</span></span> <span data-ttu-id="4d09b-151">若要判斷主機名稱，請使用 HOST_NAME 函數。</span><span class="sxs-lookup"><span data-stu-id="4d09b-151">To determine the host name, use the HOST_NAME function.</span></span>|<span data-ttu-id="4d09b-152">8</span><span class="sxs-lookup"><span data-stu-id="4d09b-152">8</span></span>|<span data-ttu-id="4d09b-153">是</span><span class="sxs-lookup"><span data-stu-id="4d09b-153">Yes</span></span>|  
|<span data-ttu-id="4d09b-154">IsSystem</span><span class="sxs-lookup"><span data-stu-id="4d09b-154">IsSystem</span></span>|`int`|<span data-ttu-id="4d09b-155">指出事件是發生在系統處理序或使用者處理序。</span><span class="sxs-lookup"><span data-stu-id="4d09b-155">Indicates whether the event occurred on a system process or a user process.</span></span> <span data-ttu-id="4d09b-156">1 = 系統，0 = 使用者。</span><span class="sxs-lookup"><span data-stu-id="4d09b-156">1 = system, 0 = user.</span></span>|<span data-ttu-id="4d09b-157">60</span><span class="sxs-lookup"><span data-stu-id="4d09b-157">60</span></span>|<span data-ttu-id="4d09b-158">是</span><span class="sxs-lookup"><span data-stu-id="4d09b-158">Yes</span></span>|  
|<span data-ttu-id="4d09b-159">LoginName</span><span class="sxs-lookup"><span data-stu-id="4d09b-159">LoginName</span></span>|`nvarchar`|<span data-ttu-id="4d09b-160">使用者登入的名稱 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安全性登入或 DOMAIN\username 格式的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 登入認證)。</span><span class="sxs-lookup"><span data-stu-id="4d09b-160">Name of the login of the user (either [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] security login or the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows login credentials in the form of DOMAIN\username).</span></span>|<span data-ttu-id="4d09b-161">11</span><span class="sxs-lookup"><span data-stu-id="4d09b-161">11</span></span>|<span data-ttu-id="4d09b-162">是</span><span class="sxs-lookup"><span data-stu-id="4d09b-162">Yes</span></span>|  
|<span data-ttu-id="4d09b-163">LoginSid</span><span class="sxs-lookup"><span data-stu-id="4d09b-163">LoginSid</span></span>|`image`|<span data-ttu-id="4d09b-164">已登入之使用者的安全性識別碼 (SID)。</span><span class="sxs-lookup"><span data-stu-id="4d09b-164">Security identification number (SID) of the logged-in user.</span></span> <span data-ttu-id="4d09b-165">您可以在 sys.server_principals 目錄檢視中找到這項資訊。</span><span class="sxs-lookup"><span data-stu-id="4d09b-165">You can find this information in the sys.server_principals catalog view.</span></span> <span data-ttu-id="4d09b-166">伺服器上的每一個登入之 SID 是唯一的。</span><span class="sxs-lookup"><span data-stu-id="4d09b-166">Each SID is unique for each login in the server.</span></span>|<span data-ttu-id="4d09b-167">41</span><span class="sxs-lookup"><span data-stu-id="4d09b-167">41</span></span>|<span data-ttu-id="4d09b-168">是</span><span class="sxs-lookup"><span data-stu-id="4d09b-168">Yes</span></span>|  
|<span data-ttu-id="4d09b-169">NTDomainName</span><span class="sxs-lookup"><span data-stu-id="4d09b-169">NTDomainName</span></span>|`nvarchar`|<span data-ttu-id="4d09b-170">使用者所隸屬的 Windows 網域。</span><span class="sxs-lookup"><span data-stu-id="4d09b-170">Windows domain to which the user belongs.</span></span>|<span data-ttu-id="4d09b-171">7</span><span class="sxs-lookup"><span data-stu-id="4d09b-171">7</span></span>|<span data-ttu-id="4d09b-172">是</span><span class="sxs-lookup"><span data-stu-id="4d09b-172">Yes</span></span>|  
|<span data-ttu-id="4d09b-173">NTUserName</span><span class="sxs-lookup"><span data-stu-id="4d09b-173">NTUserName</span></span>|`nvarchar`|<span data-ttu-id="4d09b-174">Windows 使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="4d09b-174">Windows user name.</span></span>|<span data-ttu-id="4d09b-175">6</span><span class="sxs-lookup"><span data-stu-id="4d09b-175">6</span></span>|<span data-ttu-id="4d09b-176">是</span><span class="sxs-lookup"><span data-stu-id="4d09b-176">Yes</span></span>|  
|<span data-ttu-id="4d09b-177">RequestID</span><span class="sxs-lookup"><span data-stu-id="4d09b-177">RequestID</span></span>|`int`|<span data-ttu-id="4d09b-178">包含陳述式之要求的識別碼。</span><span class="sxs-lookup"><span data-stu-id="4d09b-178">ID of the request containing the statement.</span></span>|<span data-ttu-id="4d09b-179">49</span><span class="sxs-lookup"><span data-stu-id="4d09b-179">49</span></span>|<span data-ttu-id="4d09b-180">是</span><span class="sxs-lookup"><span data-stu-id="4d09b-180">Yes</span></span>|  
|<span data-ttu-id="4d09b-181">ServerName</span><span class="sxs-lookup"><span data-stu-id="4d09b-181">ServerName</span></span>|`nvarchar`|<span data-ttu-id="4d09b-182">正在追蹤之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="4d09b-182">Name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] being traced.</span></span>|<span data-ttu-id="4d09b-183">26</span><span class="sxs-lookup"><span data-stu-id="4d09b-183">26</span></span>|<span data-ttu-id="4d09b-184">否</span><span class="sxs-lookup"><span data-stu-id="4d09b-184">No</span></span>|  
|<span data-ttu-id="4d09b-185">SessionLoginName</span><span class="sxs-lookup"><span data-stu-id="4d09b-185">SessionLoginName</span></span>|`nvarchar`|<span data-ttu-id="4d09b-186">引發工作階段之使用者的登入名稱。</span><span class="sxs-lookup"><span data-stu-id="4d09b-186">Login name of the user who originated the session.</span></span> <span data-ttu-id="4d09b-187">例如，如果您使用 Login1 連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，並以 Login2 身分執行陳述式，則 SessionLoginName 將顯示 Login1 而 LoginName 則顯示 Login2。</span><span class="sxs-lookup"><span data-stu-id="4d09b-187">For example, if you connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Login1 and execute a statement as Login2, SessionLoginName shows Login1 and LoginName shows Login2.</span></span> <span data-ttu-id="4d09b-188">此資料行將同時顯示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 Windows 登入。</span><span class="sxs-lookup"><span data-stu-id="4d09b-188">This column displays both [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows logins.</span></span>|<span data-ttu-id="4d09b-189">64</span><span class="sxs-lookup"><span data-stu-id="4d09b-189">64</span></span>|<span data-ttu-id="4d09b-190">是</span><span class="sxs-lookup"><span data-stu-id="4d09b-190">Yes</span></span>|  
|<span data-ttu-id="4d09b-191">SPID</span><span class="sxs-lookup"><span data-stu-id="4d09b-191">SPID</span></span>|`int`|<span data-ttu-id="4d09b-192">事件發生所在之工作階段的識別碼。</span><span class="sxs-lookup"><span data-stu-id="4d09b-192">ID of the session on which the event occurred.</span></span>|<span data-ttu-id="4d09b-193">12</span><span class="sxs-lookup"><span data-stu-id="4d09b-193">12</span></span>|<span data-ttu-id="4d09b-194">是</span><span class="sxs-lookup"><span data-stu-id="4d09b-194">Yes</span></span>|  
|<span data-ttu-id="4d09b-195">StartTime</span><span class="sxs-lookup"><span data-stu-id="4d09b-195">StartTime</span></span>|`datetime`|<span data-ttu-id="4d09b-196">事件的開始時間 (如果可以取得的話)。</span><span class="sxs-lookup"><span data-stu-id="4d09b-196">Time at which the event started, when available.</span></span>|<span data-ttu-id="4d09b-197">14</span><span class="sxs-lookup"><span data-stu-id="4d09b-197">14</span></span>|<span data-ttu-id="4d09b-198">是</span><span class="sxs-lookup"><span data-stu-id="4d09b-198">Yes</span></span>|  
|<span data-ttu-id="4d09b-199">Success</span><span class="sxs-lookup"><span data-stu-id="4d09b-199">Success</span></span>|`int`|<span data-ttu-id="4d09b-200">1 = 成功。</span><span class="sxs-lookup"><span data-stu-id="4d09b-200">1 = success.</span></span> <span data-ttu-id="4d09b-201">0 = 失敗 (例如，1 表示權限檢查成功，而 0 表示該檢查失敗)。</span><span class="sxs-lookup"><span data-stu-id="4d09b-201">0 = failure (for example, a 1 means success of a permissions check and a 0 means a failure of that check).</span></span>|<span data-ttu-id="4d09b-202">23</span><span class="sxs-lookup"><span data-stu-id="4d09b-202">23</span></span>|<span data-ttu-id="4d09b-203">是</span><span class="sxs-lookup"><span data-stu-id="4d09b-203">Yes</span></span>|  
|<span data-ttu-id="4d09b-204">TextData</span><span class="sxs-lookup"><span data-stu-id="4d09b-204">TextData</span></span>|`ntext`|<span data-ttu-id="4d09b-205">與追蹤中所擷取的事件類別有關的文字值。</span><span class="sxs-lookup"><span data-stu-id="4d09b-205">Text value dependent on the event class captured in the trace.</span></span>|<span data-ttu-id="4d09b-206">1</span><span class="sxs-lookup"><span data-stu-id="4d09b-206">1</span></span>|<span data-ttu-id="4d09b-207">是</span><span class="sxs-lookup"><span data-stu-id="4d09b-207">Yes</span></span>|  
|<span data-ttu-id="4d09b-208">TransactionID</span><span class="sxs-lookup"><span data-stu-id="4d09b-208">TransactionID</span></span>|`bigint`|<span data-ttu-id="4d09b-209">由系統指派給交易的識別碼。</span><span class="sxs-lookup"><span data-stu-id="4d09b-209">System-assigned ID of the transaction.</span></span>|<span data-ttu-id="4d09b-210">4</span><span class="sxs-lookup"><span data-stu-id="4d09b-210">4</span></span>|<span data-ttu-id="4d09b-211">是</span><span class="sxs-lookup"><span data-stu-id="4d09b-211">Yes</span></span>|  
|<span data-ttu-id="4d09b-212">XactSequence</span><span class="sxs-lookup"><span data-stu-id="4d09b-212">XactSequence</span></span>|`bigint`|<span data-ttu-id="4d09b-213">描述目前交易的 Token。</span><span class="sxs-lookup"><span data-stu-id="4d09b-213">Token that describes the current transaction.</span></span>|<span data-ttu-id="4d09b-214">50</span><span class="sxs-lookup"><span data-stu-id="4d09b-214">50</span></span>|<span data-ttu-id="4d09b-215">是</span><span class="sxs-lookup"><span data-stu-id="4d09b-215">Yes</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4d09b-216">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d09b-216">See Also</span></span>  
 <span data-ttu-id="4d09b-217">[擴充事件](../extended-events/extended-events.md) </span><span class="sxs-lookup"><span data-stu-id="4d09b-217">[Extended Events](../extended-events/extended-events.md) </span></span>  
 <span data-ttu-id="4d09b-218">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="4d09b-218">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span></span>  
 [<span data-ttu-id="4d09b-219">BEGIN TRANSACTION &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="4d09b-219">BEGIN TRANSACTION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/begin-transaction-transact-sql)  
  
  