---
title: 在作業步驟中使用 Token | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- job steps [SQL Server Agent]
- security [SQL Server Agent], enabling alert job step tokens
- SQL Server Agent jobs, job steps
- tokens [SQL Server]
- escape macros [SQL Server Agent]
ms.assetid: 105bbb66-0ade-4b46-b8e4-f849e5fc4d43
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9d90b6660dd4b65e4e1d9b832b39ffaa275c83bc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710090"
---
# <a name="use-tokens-in-job-steps"></a><span data-ttu-id="3d4d2-102">在作業步驟中使用 Token</span><span class="sxs-lookup"><span data-stu-id="3d4d2-102">Use Tokens in Job Steps</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="3d4d2-103">Agent 可讓您在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 作業步驟指令碼中使用 Token。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-103">Agent allows you to use tokens in [!INCLUDE[tsql](../../includes/tsql-md.md)] job step scripts.</span></span> <span data-ttu-id="3d4d2-104">撰寫作業步驟時使用 Token，所賦予您的彈性與撰寫軟體程式時使用的變數一樣。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-104">Using tokens when you write your job steps gives you the same flexibility that variables provide when you write software programs.</span></span> <span data-ttu-id="3d4d2-105">在作業步驟指令碼中插入 Token 後， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 就會先在執行階段取代此 Token，然後再由 [!INCLUDE[tsql](../../includes/tsql-md.md)] 子系統執行作業步驟。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-105">After you insert a token in a job step script, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent replaces the token at run time, before the job step is executed by the [!INCLUDE[tsql](../../includes/tsql-md.md)] subsystem.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3d4d2-106">從 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 1 開始， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業步驟的 Token 語法已變更。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-106">Starting with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 1, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job step token syntax changed.</span></span> <span data-ttu-id="3d4d2-107">因此，逸出巨集現在必須伴隨著作業步驟中使用的所有 Token 一起執行，否則這些作業步驟將會失敗。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-107">As a result, an escape macro must now accompany all tokens used in job steps, or else those job steps will fail.</span></span> <span data-ttu-id="3d4d2-108">下列「了解如何使用 Token」、「 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Token 和巨集」及「將作業步驟更新成使用巨集」各節中將說明如何使用逸出巨集以及如何更新使用 Token 的[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業步驟。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-108">Using escape macros and updating your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job steps that use tokens are described in the following sections, "Understanding Using Tokens," "[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Tokens and Macros," and "Updating Job Steps to Use Macros."</span></span> <span data-ttu-id="3d4d2-109">此外，原本使用方括號來呼叫 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] Agent 作業步驟 Token (例如 " [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ") 的`[DATE]`語法也已變更。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-109">In addition, the [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] syntax, which used square brackets to call out [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job step tokens (for example, "`[DATE]`") has also changed.</span></span> <span data-ttu-id="3d4d2-110">現在必須改用括號括住 Token 名稱，並且在 Token 語法的開頭加上錢幣符號 (`$`)。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-110">You must now enclose token names in parentheses and place a dollar sign (`$`) at the beginning of the token syntax.</span></span> <span data-ttu-id="3d4d2-111">例如：</span><span class="sxs-lookup"><span data-stu-id="3d4d2-111">For example:</span></span>  
>   
>  <span data-ttu-id="3d4d2-112">`$(ESCAPE_` *macro name* `(DATE))`</span><span class="sxs-lookup"><span data-stu-id="3d4d2-112">`$(ESCAPE_` *macro name* `(DATE))`</span></span>  
  
## <a name="understanding-using-tokens"></a><span data-ttu-id="3d4d2-113">了解如何使用 Token</span><span class="sxs-lookup"><span data-stu-id="3d4d2-113">Understanding Using Tokens</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3d4d2-114">對 Windows 事件記錄檔具有寫入權限的任何 Windows 使用者，都可以存取由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 警示或 WMI 警示啟動的作業步驟。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-114">Any Windows user with write permissions on the Windows Event Log can access job steps that are activated by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent alerts or WMI alerts.</span></span> <span data-ttu-id="3d4d2-115">為了避免此安全性風險，依預設會停用在警示啟動的作業中可以使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Token。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-115">To avoid this security risk, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent tokens that can be used in jobs activated by alerts are disabled by default.</span></span> <span data-ttu-id="3d4d2-116">這些權杖包括： **DBN**、 **SVR**、 **a-ERR**、**嚴重性**、 **a-MSG**和\**WMI (*`property`\*) \*\*。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-116">These tokens are: **A-DBN**, **A-SVR**, **A-ERR**, **A-SEV**, **A-MSG**., and **WMI(*`property`*)**.</span></span> <span data-ttu-id="3d4d2-117">請注意在此版本中，Token 的使用擴充到所有警示。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-117">Note that in this release, use of tokens is extended to all alerting.</span></span>  
>   
>  <span data-ttu-id="3d4d2-118">如果需要使用這些 Token，請先確定只有受信任的 Windows 安全性群組的成員 (例如 Administrators 群組) 才對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所在電腦的事件記錄檔具有寫入權限。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-118">If you need to use these tokens, first ensure that only members of trusted Windows security groups, such as the Administrators group, have write permissions on the Event Log of the computer where [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] resides.</span></span> <span data-ttu-id="3d4d2-119">然後以滑鼠右鍵按一下物件總管中的 [SQL Server Agent]\*\*\*\*、選取 [屬性]\*\*\*\*，然後在 [警示系統]\*\*\*\* 頁面上選取 [取代回應警示之所有作業的 Token]\*\*\*\*，以啟用這些 Token。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-119">Then, right-click **SQL Server Agent** in Object Explorer, select **Properties**, and on the **Alert System** page, select **Replace tokens for all job responses to alerts** to enable these tokens.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="3d4d2-120">Agent Token 取代功能既簡單又有效率： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 會使用精確的常值字串值來取代 Token。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-120">Agent token replacement is simple and efficient: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent replaces an exact literal string value for the token.</span></span> <span data-ttu-id="3d4d2-121">所有 Token 需區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-121">All tokens are case-sensitive.</span></span> <span data-ttu-id="3d4d2-122">您的作業步驟必須將這點納入考量，並且必須正確引用您所用的 Token 或將取代字串轉換成正確的資料類型。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-122">Your job steps must take this into account and correctly quote the tokens you use or convert the replacement string to the correct data type.</span></span>  
  
 <span data-ttu-id="3d4d2-123">例如，您可能會使用下列陳述式，在作業步驟中列印資料庫的名稱：</span><span class="sxs-lookup"><span data-stu-id="3d4d2-123">For example, you might use the following statement to print the name of the database in a job step:</span></span>  
  
 `PRINT N'Current database name is $(ESCAPE_SQUOTE(A-DBN))' ;`  
  
 <span data-ttu-id="3d4d2-124">在此範例中， **ESCAPE_SQUOTE** 巨集是使用 **A-DBN** Token 插入的。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-124">In this example, the **ESCAPE_SQUOTE** macro is inserted with the **A-DBN** token.</span></span> <span data-ttu-id="3d4d2-125">在執行階段， **A-DBN** Token 將會被取代成正確的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-125">At run time, the **A-DBN** token will be replaced with the appropriate database name.</span></span> <span data-ttu-id="3d4d2-126">逸出巨集會逸出不慎傳入 Token 取代字串的任何單引號。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-126">The escape macro escapes any single quotation marks that may be inadvertently passed in the token replacement string.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="3d4d2-127">Agent 將在最終字串中使用兩個單引號來取代一個單引號。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-127">Agent will replace one single quotation mark with two single quotation marks in the final string.</span></span>  
  
 <span data-ttu-id="3d4d2-128">例如，如果針對取代 Token 所傳遞的字串是 `AdventureWorks2012'SELECT @@VERSION --`，則由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業步驟所執行的命令將會是：</span><span class="sxs-lookup"><span data-stu-id="3d4d2-128">For example, if the string passed to replace the token is `AdventureWorks2012'SELECT @@VERSION --`, the command executed by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job step will be:</span></span>  
  
 `PRINT N'Current database name is AdventureWorks2012''SELECT @@VERSION --' ;`  
  
 <span data-ttu-id="3d4d2-129">在此情況下，插入的陳述式 `SELECT @@VERSION`不會執行。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-129">In this case, the inserted statement, `SELECT @@VERSION`, does not execute.</span></span> <span data-ttu-id="3d4d2-130">額外的單引號反而會導致伺服器將插入的陳述式剖析成字串。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-130">Instead, the extra single quotation mark causes the server to parse the inserted statement as a string.</span></span> <span data-ttu-id="3d4d2-131">如果 Token 取代字串不包含單引號，就不會逸出任何字元，而且包含 Token 的作業步驟會如預期方式執行。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-131">If the token replacement string does not contain a single quotation mark, no characters are escaped and the job step containing the token executes as intended.</span></span>  
  
 <span data-ttu-id="3d4d2-132">若要在作業步驟中偵錯 Token 的使用方式，請使用 PRINT 陳述式 (例如 `PRINT N'$(ESCAPE_SQUOTE(SQLDIR))'`)，並將作業步驟輸出儲存至檔案或資料表。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-132">To debug token usage in your job steps, use print statements such as `PRINT N'$(ESCAPE_SQUOTE(SQLDIR))'` and save job step output to a file or table.</span></span> <span data-ttu-id="3d4d2-133">您可以使用 [作業步驟屬性]\*\*\*\* 對話方塊的 [進階]\*\*\*\* 頁面來指定作業步驟輸出檔或資料表。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-133">Use the **Advanced** page of the **Job Step Properties** dialog box to specify a job step output file or table.</span></span>  
  
## <a name="sql-server-agent-tokens-and-macros"></a><span data-ttu-id="3d4d2-134">SQL Server Agent Token 和巨集</span><span class="sxs-lookup"><span data-stu-id="3d4d2-134">SQL Server Agent Tokens and Macros</span></span>  
 <span data-ttu-id="3d4d2-135">下表將列出並描述 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 支援的 Token 和巨集。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-135">The following tables list and describe the tokens and macros that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent supports.</span></span>  
  
### <a name="sql-server-agent-tokens"></a><span data-ttu-id="3d4d2-136">SQL Server Agent Token</span><span class="sxs-lookup"><span data-stu-id="3d4d2-136">SQL Server Agent Tokens</span></span>  
  
|<span data-ttu-id="3d4d2-137">Token</span><span class="sxs-lookup"><span data-stu-id="3d4d2-137">Token</span></span>|<span data-ttu-id="3d4d2-138">描述</span><span class="sxs-lookup"><span data-stu-id="3d4d2-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3d4d2-139">**(A-DBN)**</span><span class="sxs-lookup"><span data-stu-id="3d4d2-139">**(A-DBN)**</span></span>|<span data-ttu-id="3d4d2-140">資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-140">Database name.</span></span> <span data-ttu-id="3d4d2-141">若作業是由警示執行，則資料庫名稱值會自動取代作業步驟中的此 Token。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-141">If the job is run by an alert, the database name value automatically replaces this token in the job step.</span></span>|  
|<span data-ttu-id="3d4d2-142">**(A-SVR)**</span><span class="sxs-lookup"><span data-stu-id="3d4d2-142">**(A-SVR)**</span></span>|<span data-ttu-id="3d4d2-143">伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-143">Server name.</span></span> <span data-ttu-id="3d4d2-144">若作業是由警示執行，則伺服器名稱值會自動取代作業步驟中的此 Token。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-144">If the job is run by an alert, the server name value automatically replaces this token in the job step.</span></span>|  
|<span data-ttu-id="3d4d2-145">**(A-ERR)**</span><span class="sxs-lookup"><span data-stu-id="3d4d2-145">**(A-ERR)**</span></span>|<span data-ttu-id="3d4d2-146">錯誤號碼。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-146">Error number.</span></span> <span data-ttu-id="3d4d2-147">若作業是由警示執行，則錯誤號碼值會自動取代作業步驟中的此 Token。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-147">If the job is run by an alert, the error number value automatically replaces this token in the job step.</span></span>|  
|<span data-ttu-id="3d4d2-148">**(A-SEV)**</span><span class="sxs-lookup"><span data-stu-id="3d4d2-148">**(A-SEV)**</span></span>|<span data-ttu-id="3d4d2-149">錯誤的重要性。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-149">Error severity.</span></span> <span data-ttu-id="3d4d2-150">若作業是由警示執行，則錯誤嚴重性值會自動取代作業步驟中的此 Token。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-150">If the job is run by an alert, the error severity value automatically replaces this token in the job step.</span></span>|  
|<span data-ttu-id="3d4d2-151">**(A-MSG)**</span><span class="sxs-lookup"><span data-stu-id="3d4d2-151">**(A-MSG)**</span></span>|<span data-ttu-id="3d4d2-152">訊息文字。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-152">Message text.</span></span> <span data-ttu-id="3d4d2-153">若作業是由警示執行，則訊息文字值會自動取代作業步驟中的此 Token。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-153">If the job is run by an alert, the message text value automatically replaces this token in the job step.</span></span>|  
|<span data-ttu-id="3d4d2-154">\*\* (日期) \*\*</span><span class="sxs-lookup"><span data-stu-id="3d4d2-154">**(DATE)**</span></span>|<span data-ttu-id="3d4d2-155">目前日期 (格式為 YYYYMMDD)。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-155">Current date (in YYYYMMDD format).</span></span>|  
|<span data-ttu-id="3d4d2-156">\*\* (INST) \*\*</span><span class="sxs-lookup"><span data-stu-id="3d4d2-156">**(INST)**</span></span>|<span data-ttu-id="3d4d2-157">執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-157">Instance name.</span></span> <span data-ttu-id="3d4d2-158">如果是預設執行個體，此 Token 將具有預設執行個體名稱：MSSQLSERVER。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-158">For a default instance, this token will have the default instance name: MSSQLSERVER.</span></span>|  
|<span data-ttu-id="3d4d2-159">\*\* (JOBID) \*\*</span><span class="sxs-lookup"><span data-stu-id="3d4d2-159">**(JOBID)**</span></span>|<span data-ttu-id="3d4d2-160">作業識別碼。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-160">Job ID.</span></span>|  
|<span data-ttu-id="3d4d2-161">**(MACH)**</span><span class="sxs-lookup"><span data-stu-id="3d4d2-161">**(MACH)**</span></span>|<span data-ttu-id="3d4d2-162">電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-162">Computer name.</span></span>|  
|<span data-ttu-id="3d4d2-163">**(MSSA)**</span><span class="sxs-lookup"><span data-stu-id="3d4d2-163">**(MSSA)**</span></span>|<span data-ttu-id="3d4d2-164">主要 SQLServerAgent 服務名稱。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-164">Master SQLServerAgent service name.</span></span>|  
|<span data-ttu-id="3d4d2-165">**(OSCMD)**</span><span class="sxs-lookup"><span data-stu-id="3d4d2-165">**(OSCMD)**</span></span>|<span data-ttu-id="3d4d2-166">用於執行 **CmdExec** 作業步驟之程式的前置詞。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-166">Prefix for the program used to run **CmdExec** job steps.</span></span>|  
|<span data-ttu-id="3d4d2-167">**(SQLDIR)**</span><span class="sxs-lookup"><span data-stu-id="3d4d2-167">**(SQLDIR)**</span></span>|<span data-ttu-id="3d4d2-168">安裝有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的目錄。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-168">The directory in which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed.</span></span> <span data-ttu-id="3d4d2-169">根據預設，此一值為 C:\Program Files\Microsoft SQL Server\MSSQL。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-169">By default, this value is C:\Program Files\Microsoft SQL Server\MSSQL.</span></span>|  
|<span data-ttu-id="3d4d2-170">**(SQLLOGDIR)**</span><span class="sxs-lookup"><span data-stu-id="3d4d2-170">**(SQLLOGDIR)**</span></span>|<span data-ttu-id="3d4d2-171">SQL Server 錯誤記錄檔資料夾路徑的取代 Token，例如 $(ESCAPE_SQUOTE(SQLLOGDIR))。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-171">Replacement token for the SQL Server error log folder path - for example, $(ESCAPE_SQUOTE(SQLLOGDIR)).</span></span>|  
|<span data-ttu-id="3d4d2-172">**(STEPCT)**</span><span class="sxs-lookup"><span data-stu-id="3d4d2-172">**(STEPCT)**</span></span>|<span data-ttu-id="3d4d2-173">此步驟已執行之次數的計數 (不包含重試)。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-173">A count of the number of times this step has executed (excluding retries).</span></span> <span data-ttu-id="3d4d2-174">可利用步驟命令來強制結束多重步驟迴圈 (Loop)。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-174">Can be used by the step command to force termination of a multistep loop.</span></span>|  
|<span data-ttu-id="3d4d2-175">**(STEPID)**</span><span class="sxs-lookup"><span data-stu-id="3d4d2-175">**(STEPID)**</span></span>|<span data-ttu-id="3d4d2-176">步驟識別碼。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-176">Step ID.</span></span>|  
|<span data-ttu-id="3d4d2-177">**(SRVR)**</span><span class="sxs-lookup"><span data-stu-id="3d4d2-177">**(SRVR)**</span></span>|<span data-ttu-id="3d4d2-178">執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-178">Name of the computer running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="3d4d2-179">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 是具名執行個體，這也包括執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-179">If the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance is a named instance, this includes the instance name.</span></span>|  
|<span data-ttu-id="3d4d2-180">\*\* (時間) \*\*</span><span class="sxs-lookup"><span data-stu-id="3d4d2-180">**(TIME)**</span></span>|<span data-ttu-id="3d4d2-181">目前時間 (格式為 HHMMSS)。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-181">Current time (in HHMMSS format).</span></span>|  
|<span data-ttu-id="3d4d2-182">**(STRTTM)**</span><span class="sxs-lookup"><span data-stu-id="3d4d2-182">**(STRTTM)**</span></span>|<span data-ttu-id="3d4d2-183">開始執行作業的時間 (格式為 HHMMSS)。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-183">The time (in HHMMSS format) that the job began executing.</span></span>|  
|<span data-ttu-id="3d4d2-184">**(STRTDT)**</span><span class="sxs-lookup"><span data-stu-id="3d4d2-184">**(STRTDT)**</span></span>|<span data-ttu-id="3d4d2-185">開始執行作業的日期 (格式為 YYYYMMDD)。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-185">The date (in YYYYMMDD format) that the job began executing.</span></span>|  
|<span data-ttu-id="3d4d2-186">**(WMI(** \*\* **<屬性>))**</span><span class="sxs-lookup"><span data-stu-id="3d4d2-186">**(WMI(** *property* **))**</span></span>|<span data-ttu-id="3d4d2-187">對於回應 WMI 警示所執行的作業，這是 <屬性>\*\* 指定的屬性值。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-187">For jobs that run in response to WMI alerts, the value of the property specified by *property*.</span></span> <span data-ttu-id="3d4d2-188">例如，`$(WMI(DatabaseName))` 提供造成警示執行之 WMI 事件的 **DatabaseName** 屬性值。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-188">For example, `$(WMI(DatabaseName))` provides the value of the **DatabaseName** property for the WMI event that caused the alert to run.</span></span>|  
  
### <a name="sql-server-agent-escape-macros"></a><span data-ttu-id="3d4d2-189">SQL Server Agent 逸出巨集</span><span class="sxs-lookup"><span data-stu-id="3d4d2-189">SQL Server Agent Escape Macros</span></span>  
  
|<span data-ttu-id="3d4d2-190">逸出巨集</span><span class="sxs-lookup"><span data-stu-id="3d4d2-190">Escape Macros</span></span>|<span data-ttu-id="3d4d2-191">描述</span><span class="sxs-lookup"><span data-stu-id="3d4d2-191">Description</span></span>|  
|-------------------|-----------------|  
|<span data-ttu-id="3d4d2-192">**$(ESCAPE_SQUOTE(** *token_name* **))**</span><span class="sxs-lookup"><span data-stu-id="3d4d2-192">**$(ESCAPE_SQUOTE(** *token_name* **))**</span></span>|<span data-ttu-id="3d4d2-193">在 Token 取代字串中逸出單引號 (')。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-193">Escapes single quotation marks (') in the token replacement string.</span></span> <span data-ttu-id="3d4d2-194">使用兩個單引號來取代一個單引號。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-194">Replaces one single quotation mark with two single quotation marks.</span></span>|  
|<span data-ttu-id="3d4d2-195">**$(ESCAPE_DQUOTE(** *token_name* **))**</span><span class="sxs-lookup"><span data-stu-id="3d4d2-195">**$(ESCAPE_DQUOTE(** *token_name* **))**</span></span>|<span data-ttu-id="3d4d2-196">在 Token 取代字串中逸出雙引號 (")。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-196">Escapes double quotation marks (") in the token replacement string.</span></span> <span data-ttu-id="3d4d2-197">使用兩個雙引號來取代一個雙引號。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-197">Replaces one double quotation mark with two double quotation marks.</span></span>|  
|<span data-ttu-id="3d4d2-198">**$(ESCAPE_RBRACKET(** *token_name* **))**</span><span class="sxs-lookup"><span data-stu-id="3d4d2-198">**$(ESCAPE_RBRACKET(** *token_name* **))**</span></span>|<span data-ttu-id="3d4d2-199">在 Token 取代字串中逸出右方括號 (])。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-199">Escapes right brackets (]) in the token replacement string.</span></span> <span data-ttu-id="3d4d2-200">使用兩個右方括號來取代一個右方括號。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-200">Replaces one right bracket with two right brackets.</span></span>|  
|<span data-ttu-id="3d4d2-201">**$(ESCAPE_NONE(** *token_name* **))**</span><span class="sxs-lookup"><span data-stu-id="3d4d2-201">**$(ESCAPE_NONE(** *token_name* **))**</span></span>|<span data-ttu-id="3d4d2-202">取代 Token，但不逸出字串中的任何字元。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-202">Replaces token without escaping any characters in the string.</span></span> <span data-ttu-id="3d4d2-203">提供這個巨集的目的，是為了在 Token 取代字串只能由受信任使用者提供的環境下，支援回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-203">This macro is provided to support backward compatibility in environments where token replacement strings are only expected from trusted users.</span></span> <span data-ttu-id="3d4d2-204">如需詳細資訊，請參閱本主題後面的「將作業步驟更新成使用巨集」。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-204">For more information, see "Updating Job Steps to Use Macros," later in this topic.</span></span>|  
  
## <a name="updating-job-steps-to-use-macros"></a><span data-ttu-id="3d4d2-205">將作業步驟更新成使用巨集</span><span class="sxs-lookup"><span data-stu-id="3d4d2-205">Updating Job Steps to Use Macros</span></span>  
 <span data-ttu-id="3d4d2-206">從 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 1 開始，包含 Token 但不含逸出巨集的作業步驟將會失敗，而且會傳回一則錯誤訊息，表示作業步驟含有一或多個在執行作業之前必須使用巨集更新的 Token。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-206">Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 1, job steps that contain tokens without escape macros will fail and return an error message indicating the job step contains one or more tokens that must be updated with a macro before the job can run.</span></span>  
  
 <span data-ttu-id="3d4d2-207">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 知識庫文件 915845 中有提供指令碼： [SQL Server Agent Job Steps That Use Tokens Fail in SQL Server 2005 Service Pack 1](https://support.microsoft.com/kb/915845)(使用 Token 的 SQL Server Agent 作業步驟在 SQL Server 2005 Service Pack 1 中失敗)。您可以使用這個指令碼來更新使用 Token 搭配 **ESCAPE_NONE** 巨集的所有作業步驟。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-207">A script is provided with [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base article 915845: [SQL Server Agent Job Steps That Use Tokens Fail in SQL Server 2005 Service Pack 1](https://support.microsoft.com/kb/915845).You can use this script to update all of your job steps that use tokens with the **ESCAPE_NONE** macro.</span></span> <span data-ttu-id="3d4d2-208">使用這個指令碼之後，我們建議您盡快檢閱使用 Token 的作業步驟，並且使用適用於此作業步驟內容的逸出巨集來取代 **ESCAPE_NONE** 巨集。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-208">After using this script, we recommend that you review your job steps that use tokens as soon as possible, and replace the **ESCAPE_NONE** macro with an escape macro that is appropriate for the job step context.</span></span>  
  
 <span data-ttu-id="3d4d2-209">下表說明 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 如何處理取代 Token。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-209">The following table describes how token replacement is handled by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span> <span data-ttu-id="3d4d2-210">若要開啟或關閉取代 Token，請以滑鼠右鍵按一下物件總管中的 [SQL Server Agent]\*\*\*\*，並選取 [屬性]\*\*\*\*，然後在 [警示系統]\*\*\*\* 頁面上選取或清除 [取代回應警示之所有作業的 Token]\*\*\*\* 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-210">To turn alert token replacement on or off, right-click **SQL Server Agent** in Object Explorer, select **Properties**, and on the **Alert System** page, select or clear the **Replace tokens for all job responses to alerts** check box.</span></span>  
  
|<span data-ttu-id="3d4d2-211">Token 語法</span><span class="sxs-lookup"><span data-stu-id="3d4d2-211">Token syntax</span></span>|<span data-ttu-id="3d4d2-212">警示 Token 取代開啟</span><span class="sxs-lookup"><span data-stu-id="3d4d2-212">Alert token replacement on</span></span>|<span data-ttu-id="3d4d2-213">警示 Token 取代關閉</span><span class="sxs-lookup"><span data-stu-id="3d4d2-213">Alert token replacement off</span></span>|  
|------------------|--------------------------------|---------------------------------|  
|<span data-ttu-id="3d4d2-214">使用 ESCAPE 巨集</span><span class="sxs-lookup"><span data-stu-id="3d4d2-214">ESCAPE macro used</span></span>|<span data-ttu-id="3d4d2-215">作業中的所有 Token 都會順利被取代。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-215">All tokens in jobs are successfully replaced.</span></span>|<span data-ttu-id="3d4d2-216">由警示啟動的 Token 不會被取代。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-216">Tokens activated by alerts are not replaced.</span></span> <span data-ttu-id="3d4d2-217">這些權杖是 **-DBN**、 **SVR**、 **a-ERR**、**嚴重性**、 **a-MSG**和\**WMI (*`property`\*) \*\*。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-217">These tokens are **A-DBN**, **A-SVR**, **A-ERR**, **A-SEV**, **A-MSG**, and **WMI(*`property`*)**.</span></span> <span data-ttu-id="3d4d2-218">其他靜態 Token 則會順利被取代。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-218">Other static tokens are replaced successfully.</span></span>|  
|<span data-ttu-id="3d4d2-219">不使用 ESCAPE 巨集</span><span class="sxs-lookup"><span data-stu-id="3d4d2-219">No ESCAPE macro used</span></span>|<span data-ttu-id="3d4d2-220">所有包含 Token 的作業都會失敗。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-220">Any jobs containing tokens fail.</span></span>|<span data-ttu-id="3d4d2-221">所有包含 Token 的作業都會失敗。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-221">Any jobs containing tokens fail.</span></span>|  
  
## <a name="token-syntax-update-examples"></a><span data-ttu-id="3d4d2-222">Token 語法更新範例</span><span class="sxs-lookup"><span data-stu-id="3d4d2-222">Token Syntax Update Examples</span></span>  
  
### <a name="a-using-tokens-in-non-nested-strings"></a><span data-ttu-id="3d4d2-223">A.</span><span class="sxs-lookup"><span data-stu-id="3d4d2-223">A.</span></span> <span data-ttu-id="3d4d2-224">在非巢狀字串中使用 Token</span><span class="sxs-lookup"><span data-stu-id="3d4d2-224">Using tokens in non-nested strings</span></span>  
 <span data-ttu-id="3d4d2-225">下列範例將說明如何使用正確的逸出巨集來更新簡單的非巢狀指令碼。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-225">The following example shows how to update a simple non-nested script with the appropriate escape macro.</span></span> <span data-ttu-id="3d4d2-226">執行更新指令碼之前，下列作業步驟指令碼會使用一個作業步驟 Token 來列印正確的資料庫名稱：</span><span class="sxs-lookup"><span data-stu-id="3d4d2-226">Before running the update script, the following job step script uses a job step token to print the appropriate database name:</span></span>  
  
 `PRINT N'Current database name is $(A-DBN)' ;`  
  
 <span data-ttu-id="3d4d2-227">執行更新指令碼之後，會在 `ESCAPE_NONE` Token 前面插入 `A-DBN` 巨集。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-227">After running the update script, an `ESCAPE_NONE` macro is inserted before the `A-DBN` token.</span></span> <span data-ttu-id="3d4d2-228">由於單引號是用來分隔 PRINT 字串，所以您必須依照下列方式插入 `ESCAPE_SQUOTE` 巨集，藉以更新此作業步驟：</span><span class="sxs-lookup"><span data-stu-id="3d4d2-228">Because single quotation marks are used to delimit the print string, you must update the job step by inserting the `ESCAPE_SQUOTE` macro as follows:</span></span>  
  
 `PRINT N'Current database name is $(ESCAPE_SQUOTE(A-DBN))' ;`  
  
### <a name="b-using-tokens-in-nested-strings"></a><span data-ttu-id="3d4d2-229">B.</span><span class="sxs-lookup"><span data-stu-id="3d4d2-229">B.</span></span> <span data-ttu-id="3d4d2-230">在巢狀字串中使用 Token</span><span class="sxs-lookup"><span data-stu-id="3d4d2-230">Using tokens in nested strings</span></span>  
 <span data-ttu-id="3d4d2-231">在 Token 用於巢狀字串或陳述式的作業步驟指令碼中，巢狀陳述式應該先重新撰寫成多個陳述式，然後再插入正確的逸出巨集。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-231">In job step scripts where tokens are used in nested strings or statements, the nested statements should be rewritten as multiple statements before inserting the appropriate escape macros.</span></span>  
  
 <span data-ttu-id="3d4d2-232">例如，請考慮下列使用 `A-MSG` Token 而且尚未使用逸出巨集更新的作業步驟：</span><span class="sxs-lookup"><span data-stu-id="3d4d2-232">For example, consider the following job step, which uses the `A-MSG` token and has not been updated with an escape macro:</span></span>  
  
 `PRINT N'Print ''$(A-MSG)''' ;`  
  
 <span data-ttu-id="3d4d2-233">執行更新指令碼之後，會使用此 Token 插入 `ESCAPE_NONE` 巨集。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-233">After running the update script, an `ESCAPE_NONE` macro is inserted with the token.</span></span> <span data-ttu-id="3d4d2-234">不過，在此情況下，您必須依照下列方式重新撰寫不使用巢狀的指令碼，並插入 `ESCAPE_SQUOTE` 巨集，以便適當逸出可能會傳入 Token 取代字串的分隔符號：</span><span class="sxs-lookup"><span data-stu-id="3d4d2-234">However, in this case, you would have to rewrite the script without using nesting as follows and insert the `ESCAPE_SQUOTE` macro to properly escape delimiters that may be passed in the token replacement string:</span></span>  
  
 `DECLARE @msgString nvarchar(max)`  
  
 `SET @msgString = '$(ESCAPE_SQUOTE(A-MSG))'`  
  
 `SET @msgString = QUOTENAME(@msgString,'''')`  
  
 `PRINT N'Print ' + @msgString ;`  
  
 <span data-ttu-id="3d4d2-235">此外，請注意此範例中，QUOTENAME 函數會設定引號字元。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-235">Note also in this example that the QUOTENAME function sets the quote character.</span></span>  
  
### <a name="c-using-tokens-with-the-escape_none-macro"></a><span data-ttu-id="3d4d2-236">C.</span><span class="sxs-lookup"><span data-stu-id="3d4d2-236">C.</span></span> <span data-ttu-id="3d4d2-237">使用 Token 搭配 ESCAPE_NONE 巨集</span><span class="sxs-lookup"><span data-stu-id="3d4d2-237">Using tokens with the ESCAPE_NONE macro</span></span>  
 <span data-ttu-id="3d4d2-238">下列範例是指令碼的一部分，而這個指令碼會從 `job_id` 資料表擷取 `sysjobs` 並使用 `JOBID` Token 來擴展 `@JobID` 變數 (之前在指令碼中宣告成二進位資料類型)。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-238">The following example is part of a script that retrieves the `job_id` from the `sysjobs` table and uses the `JOBID` token to populate the `@JobID` variable, which was declared earlier in the script as a binary data type.</span></span> <span data-ttu-id="3d4d2-239">請注意，由於二進位資料類型不需要任何分隔符號，所以 `ESCAPE_NONE` 巨集會搭配 `JOBID` Token 使用。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-239">Note that because no delimiters are required for binary data types, the `ESCAPE_NONE` macro is used with the `JOBID` token.</span></span> <span data-ttu-id="3d4d2-240">您不需要在執行更新指令碼之後，更新此作業步驟。</span><span class="sxs-lookup"><span data-stu-id="3d4d2-240">You would not need to update this job step after running the update script.</span></span>  
  
 `SELECT * FROM msdb.dbo.sysjobs`  
  
 `WHERE @JobID = CONVERT(uniqueidentifier, $(ESCAPE_NONE(JOBID))) ;`  
  
## <a name="see-also"></a><span data-ttu-id="3d4d2-241">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3d4d2-241">See Also</span></span>  
 <span data-ttu-id="3d4d2-242">[實作作業](implement-jobs.md) </span><span class="sxs-lookup"><span data-stu-id="3d4d2-242">[Implement Jobs](implement-jobs.md) </span></span>  
 [<span data-ttu-id="3d4d2-243">管理作業步驟</span><span class="sxs-lookup"><span data-stu-id="3d4d2-243">Manage Job Steps</span></span>](manage-job-steps.md)  
  
  