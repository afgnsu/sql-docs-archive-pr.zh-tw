---
title: Broker:Activation 事件類別 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Broker:Activation event class
ms.assetid: 481d5b13-657e-4b51-8783-ccac3595bd45
author: stevestein
ms.author: sstein
ms.openlocfilehash: 653085cd6e88fe5b18653a0a8ed82491f5b4333e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598420"
---
# <a name="brokeractivation-event-class"></a><span data-ttu-id="447ad-102">Broker:Activation 事件類別</span><span class="sxs-lookup"><span data-stu-id="447ad-102">Broker:Activation Event Class</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="447ad-103">當佇列監視器啟動一個啟用預存程序、傳送 QUEUE_ACTIVATION 通知或佇列監視器所啟動的一個啟用預存程序結束時，會產生 **Broker:Activation** 事件。</span><span class="sxs-lookup"><span data-stu-id="447ad-103">generates a **Broker:Activation** event when a queue monitor starts an activation stored procedure, sends a QUEUE_ACTIVATION notification, or when an activation stored procedure started by a queue monitor exits.</span></span>  
  
## <a name="brokeractivation-event-class-data-columns"></a><span data-ttu-id="447ad-104">Broker:Activation 事件類別資料行</span><span class="sxs-lookup"><span data-stu-id="447ad-104">Broker:Activation Event Class Data Columns</span></span>  
  
|<span data-ttu-id="447ad-105">資料行</span><span class="sxs-lookup"><span data-stu-id="447ad-105">Data column</span></span>|<span data-ttu-id="447ad-106">類型</span><span class="sxs-lookup"><span data-stu-id="447ad-106">Type</span></span>|<span data-ttu-id="447ad-107">描述</span><span class="sxs-lookup"><span data-stu-id="447ad-107">Description</span></span>|<span data-ttu-id="447ad-108">資料行編號</span><span class="sxs-lookup"><span data-stu-id="447ad-108">Column number</span></span>|<span data-ttu-id="447ad-109">可篩選</span><span class="sxs-lookup"><span data-stu-id="447ad-109">Filterable</span></span>|  
|-----------------|----------|-----------------|-------------------|----------------|  
|<span data-ttu-id="447ad-110">**ClientProcessID**</span><span class="sxs-lookup"><span data-stu-id="447ad-110">**ClientProcessID**</span></span>|`int`|<span data-ttu-id="447ad-111">主機電腦指派給用戶端應用程式執行中處理序的識別碼。</span><span class="sxs-lookup"><span data-stu-id="447ad-111">The ID assigned by the host computer to the process where the client application is running.</span></span> <span data-ttu-id="447ad-112">如果用戶端提供處理序識別碼，這個資料行就會擴展。</span><span class="sxs-lookup"><span data-stu-id="447ad-112">This data column is populated if the client process ID is provided by the client.</span></span>|<span data-ttu-id="447ad-113">9</span><span class="sxs-lookup"><span data-stu-id="447ad-113">9</span></span>|<span data-ttu-id="447ad-114">是</span><span class="sxs-lookup"><span data-stu-id="447ad-114">Yes</span></span>|  
|<span data-ttu-id="447ad-115">**DatabaseID**</span><span class="sxs-lookup"><span data-stu-id="447ad-115">**DatabaseID**</span></span>|`int`|<span data-ttu-id="447ad-116">由 USE *database* 陳述式所指定的資料庫識別碼，或者如果沒有針對指定執行個體發出 USE *database*陳述式，則是預設資料庫的識別碼。</span><span class="sxs-lookup"><span data-stu-id="447ad-116">The ID of the database specified by the USE *database* statement, or the ID of the default database if no USE *database*statement has been issued for a given instance.</span></span> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] <span data-ttu-id="447ad-117">資料行，則 **ServerName** 會顯示資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="447ad-117">displays the name of the database if the **ServerName** data column is captured in the trace and the server is available.</span></span> <span data-ttu-id="447ad-118">請使用 DB_ID 函數判斷資料庫的值。</span><span class="sxs-lookup"><span data-stu-id="447ad-118">Determine the value for a database by using the DB_ID function.</span></span>|<span data-ttu-id="447ad-119">3</span><span class="sxs-lookup"><span data-stu-id="447ad-119">3</span></span>|<span data-ttu-id="447ad-120">是</span><span class="sxs-lookup"><span data-stu-id="447ad-120">Yes</span></span>|  
|<span data-ttu-id="447ad-121">**EventClass**</span><span class="sxs-lookup"><span data-stu-id="447ad-121">**EventClass**</span></span>|`int`|<span data-ttu-id="447ad-122">擷取的事件類別類型。</span><span class="sxs-lookup"><span data-stu-id="447ad-122">The type of event class captured.</span></span> <span data-ttu-id="447ad-123">對於 **Broker:Activation** ，一律為 **163**。</span><span class="sxs-lookup"><span data-stu-id="447ad-123">Always **163** for **Broker:Activation**.</span></span>|<span data-ttu-id="447ad-124">27</span><span class="sxs-lookup"><span data-stu-id="447ad-124">27</span></span>|<span data-ttu-id="447ad-125">否</span><span class="sxs-lookup"><span data-stu-id="447ad-125">No</span></span>|  
|<span data-ttu-id="447ad-126">**EventSequence**</span><span class="sxs-lookup"><span data-stu-id="447ad-126">**EventSequence**</span></span>|`int`|<span data-ttu-id="447ad-127">此事件的序號。</span><span class="sxs-lookup"><span data-stu-id="447ad-127">Sequence number for this event.</span></span>|<span data-ttu-id="447ad-128">51</span><span class="sxs-lookup"><span data-stu-id="447ad-128">51</span></span>|<span data-ttu-id="447ad-129">否</span><span class="sxs-lookup"><span data-stu-id="447ad-129">No</span></span>|  
|<span data-ttu-id="447ad-130">**EventSubClass**</span><span class="sxs-lookup"><span data-stu-id="447ad-130">**EventSubClass**</span></span>|`nvarchar`|<span data-ttu-id="447ad-131">此事件報告的特定動作。</span><span class="sxs-lookup"><span data-stu-id="447ad-131">The specific action that this event reports.</span></span> <span data-ttu-id="447ad-132">下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="447ad-132">One of the following values:</span></span><br /><br /> <span data-ttu-id="447ad-133">**開始**：</span><span class="sxs-lookup"><span data-stu-id="447ad-133">**start**:</span></span> <br />                [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="447ad-134">已開始啟用預存程序。</span><span class="sxs-lookup"><span data-stu-id="447ad-134">started an activation stored procedure.</span></span><br /><br /> <span data-ttu-id="447ad-135">已結束：啟用預存程式正常**結束**。</span><span class="sxs-lookup"><span data-stu-id="447ad-135">**ended**: The activation stored procedure exited normally.</span></span><br /><br /> <span data-ttu-id="447ad-136">已**中止**：啟用預存程式已結束，但發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="447ad-136">**aborted**: The activation stored procedure exited with an error.</span></span>|<span data-ttu-id="447ad-137">21</span><span class="sxs-lookup"><span data-stu-id="447ad-137">21</span></span>|<span data-ttu-id="447ad-138">否</span><span class="sxs-lookup"><span data-stu-id="447ad-138">No</span></span>|  
|<span data-ttu-id="447ad-139">**HostName**</span><span class="sxs-lookup"><span data-stu-id="447ad-139">**HostName**</span></span>|`nvarchar`|<span data-ttu-id="447ad-140">執行用戶端的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="447ad-140">The name of the computer on which the client is running.</span></span> <span data-ttu-id="447ad-141">這個資料行會在用戶端提供主機名稱時填入。</span><span class="sxs-lookup"><span data-stu-id="447ad-141">This data column is populated if the host name is provided by the client.</span></span> <span data-ttu-id="447ad-142">若要判斷主機名稱，請使用 HOST_NAME 函數。</span><span class="sxs-lookup"><span data-stu-id="447ad-142">To determine the host name, use the HOST_NAME function.</span></span>|<span data-ttu-id="447ad-143">8</span><span class="sxs-lookup"><span data-stu-id="447ad-143">8</span></span>|<span data-ttu-id="447ad-144">是</span><span class="sxs-lookup"><span data-stu-id="447ad-144">Yes</span></span>|  
|<span data-ttu-id="447ad-145">**IntegerData**</span><span class="sxs-lookup"><span data-stu-id="447ad-145">**IntegerData**</span></span>|`int`|<span data-ttu-id="447ad-146">此佇列上作用中的工作數。</span><span class="sxs-lookup"><span data-stu-id="447ad-146">The number of tasks active on this queue.</span></span>|<span data-ttu-id="447ad-147">25</span><span class="sxs-lookup"><span data-stu-id="447ad-147">25</span></span>|<span data-ttu-id="447ad-148">否</span><span class="sxs-lookup"><span data-stu-id="447ad-148">No</span></span>|  
|<span data-ttu-id="447ad-149">**IsSystem**</span><span class="sxs-lookup"><span data-stu-id="447ad-149">**IsSystem**</span></span>|`int`|<span data-ttu-id="447ad-150">指出事件是發生在系統處理序或使用者處理序。</span><span class="sxs-lookup"><span data-stu-id="447ad-150">Indicates whether the event occurred on a system process or a user process.</span></span> <span data-ttu-id="447ad-151">1 = 系統，0 = 使用者。</span><span class="sxs-lookup"><span data-stu-id="447ad-151">1 = system, 0 = user.</span></span>|<span data-ttu-id="447ad-152">60</span><span class="sxs-lookup"><span data-stu-id="447ad-152">60</span></span>|<span data-ttu-id="447ad-153">否</span><span class="sxs-lookup"><span data-stu-id="447ad-153">No</span></span>|  
|<span data-ttu-id="447ad-154">**LoginSid**</span><span class="sxs-lookup"><span data-stu-id="447ad-154">**LoginSid**</span></span>|`image`|<span data-ttu-id="447ad-155">已登入之使用者的安全性識別碼 (SID)。</span><span class="sxs-lookup"><span data-stu-id="447ad-155">The security identification number (SID) of the logged-in user.</span></span> <span data-ttu-id="447ad-156">伺服器上的每一個登入之 SID 是唯一的。</span><span class="sxs-lookup"><span data-stu-id="447ad-156">Each SID is unique for each login in the server.</span></span>|<span data-ttu-id="447ad-157">41</span><span class="sxs-lookup"><span data-stu-id="447ad-157">41</span></span>|<span data-ttu-id="447ad-158">是</span><span class="sxs-lookup"><span data-stu-id="447ad-158">Yes</span></span>|  
|<span data-ttu-id="447ad-159">**NTDomainName**</span><span class="sxs-lookup"><span data-stu-id="447ad-159">**NTDomainName**</span></span>|`nvarchar`|<span data-ttu-id="447ad-160">使用者所隸屬的 Windows 網域。</span><span class="sxs-lookup"><span data-stu-id="447ad-160">The Windows domain to which the user belongs.</span></span>|<span data-ttu-id="447ad-161">7</span><span class="sxs-lookup"><span data-stu-id="447ad-161">7</span></span>|<span data-ttu-id="447ad-162">是</span><span class="sxs-lookup"><span data-stu-id="447ad-162">Yes</span></span>|  
|<span data-ttu-id="447ad-163">**NTUserName**</span><span class="sxs-lookup"><span data-stu-id="447ad-163">**NTUserName**</span></span>|`nvarchar`|<span data-ttu-id="447ad-164">擁有產生此事件之連接的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="447ad-164">The name of the user that owns the connection that generated this event.</span></span>|<span data-ttu-id="447ad-165">6</span><span class="sxs-lookup"><span data-stu-id="447ad-165">6</span></span>|<span data-ttu-id="447ad-166">是</span><span class="sxs-lookup"><span data-stu-id="447ad-166">Yes</span></span>|  
|<span data-ttu-id="447ad-167">**Exchange Spill**</span><span class="sxs-lookup"><span data-stu-id="447ad-167">**ObjectID**</span></span>|`int`|<span data-ttu-id="447ad-168">與此事件相關聯的佇列。</span><span class="sxs-lookup"><span data-stu-id="447ad-168">The queue associated with this event.</span></span>|<span data-ttu-id="447ad-169">22</span><span class="sxs-lookup"><span data-stu-id="447ad-169">22</span></span>|<span data-ttu-id="447ad-170">否</span><span class="sxs-lookup"><span data-stu-id="447ad-170">No</span></span>|  
|<span data-ttu-id="447ad-171">**ServerName**</span><span class="sxs-lookup"><span data-stu-id="447ad-171">**ServerName**</span></span>|`nvarchar`|<span data-ttu-id="447ad-172">正在追蹤之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="447ad-172">The name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] being traced.</span></span>|<span data-ttu-id="447ad-173">26</span><span class="sxs-lookup"><span data-stu-id="447ad-173">26</span></span>|<span data-ttu-id="447ad-174">否</span><span class="sxs-lookup"><span data-stu-id="447ad-174">No</span></span>|  
|<span data-ttu-id="447ad-175">**SPID**</span><span class="sxs-lookup"><span data-stu-id="447ad-175">**SPID**</span></span>|`int`|<span data-ttu-id="447ad-176">由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 指派給用戶端關聯之處理序的伺服器處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="447ad-176">The server process ID assigned by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to the process associated with the client.</span></span>|<span data-ttu-id="447ad-177">12</span><span class="sxs-lookup"><span data-stu-id="447ad-177">12</span></span>|<span data-ttu-id="447ad-178">是</span><span class="sxs-lookup"><span data-stu-id="447ad-178">Yes</span></span>|  
|<span data-ttu-id="447ad-179">**StartTime**</span><span class="sxs-lookup"><span data-stu-id="447ad-179">**StartTime**</span></span>|`datetime`|<span data-ttu-id="447ad-180">事件啟動的時間 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="447ad-180">The time at which the event started, when available.</span></span>|<span data-ttu-id="447ad-181">14</span><span class="sxs-lookup"><span data-stu-id="447ad-181">14</span></span>|<span data-ttu-id="447ad-182">是</span><span class="sxs-lookup"><span data-stu-id="447ad-182">Yes</span></span>|  
|<span data-ttu-id="447ad-183">**TransactionID**</span><span class="sxs-lookup"><span data-stu-id="447ad-183">**TransactionID**</span></span>|`bigint`|<span data-ttu-id="447ad-184">系統指派的交易識別碼。</span><span class="sxs-lookup"><span data-stu-id="447ad-184">The system-assigned ID of the transaction.</span></span>|<span data-ttu-id="447ad-185">4</span><span class="sxs-lookup"><span data-stu-id="447ad-185">4</span></span>|<span data-ttu-id="447ad-186">否</span><span class="sxs-lookup"><span data-stu-id="447ad-186">No</span></span>|  
  
  