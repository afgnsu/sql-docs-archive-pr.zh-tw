---
title: SQL Server 的 Broker Statistics 物件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Broker Statistics
- Broker Statistics object
ms.assetid: e9e36f01-93f6-4e6e-90c6-c7f3fd121737
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e4cb8b30cd7b821294bd329cafe6f7b25b717f1f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598819"
---
# <a name="sql-server-broker-statistics-object"></a><span data-ttu-id="7c41c-102">SQL Server 的 Broker Statistics 物件</span><span class="sxs-lookup"><span data-stu-id="7c41c-102">SQL Server, Broker Statistics Object</span></span>
  <span data-ttu-id="7c41c-103">SQLServer:Broker Statistics 效能物件包含可針對 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 執行個體報告一般 [!INCLUDE[ssDE](../../includes/ssde-md.md)]資訊的效能計數器。</span><span class="sxs-lookup"><span data-stu-id="7c41c-103">The SQLServer:Broker Statistics performance object contains performance counters that report general [!INCLUDE[ssSB](../../includes/sssb-md.md)] information for an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="7c41c-104">下表列出這個物件包含的計數器：</span><span class="sxs-lookup"><span data-stu-id="7c41c-104">The following table lists the counters that this object contains:</span></span>  
  
|<span data-ttu-id="7c41c-105">SQL Server 的 Broker Statistics 計數器</span><span class="sxs-lookup"><span data-stu-id="7c41c-105">SQL Server Broker Statistics counters</span></span>|<span data-ttu-id="7c41c-106">描述</span><span class="sxs-lookup"><span data-stu-id="7c41c-106">Description</span></span>|  
|-------------------------------------------|-----------------|  
|<span data-ttu-id="7c41c-107">**Activation Errors Total**</span><span class="sxs-lookup"><span data-stu-id="7c41c-107">**Activation Errors Total**</span></span>|<span data-ttu-id="7c41c-108">[!INCLUDE[ssSB](../../includes/sssb-md.md)] 啟用預存程序已結束並發生錯誤的次數。</span><span class="sxs-lookup"><span data-stu-id="7c41c-108">The number of times a [!INCLUDE[ssSB](../../includes/sssb-md.md)] activation stored procedure exited with an error.</span></span>|  
|<span data-ttu-id="7c41c-109">**Broker Transaction Rollbacks**</span><span class="sxs-lookup"><span data-stu-id="7c41c-109">**Broker Transaction Rollbacks**</span></span>|<span data-ttu-id="7c41c-110">包含與 [!INCLUDE[ssSB](../../includes/sssb-md.md)]相關之 DML 陳述式 (例如 SEND 和 RECEIVE) 的回復交易數目。</span><span class="sxs-lookup"><span data-stu-id="7c41c-110">The number of rolled-back transactions that contained DML statements related to [!INCLUDE[ssSB](../../includes/sssb-md.md)], such as SEND and RECEIVE.</span></span>|  
|<span data-ttu-id="7c41c-111">**Corrupted Messages Total**</span><span class="sxs-lookup"><span data-stu-id="7c41c-111">**Corrupted Messages Total**</span></span>|<span data-ttu-id="7c41c-112">執行個體收到的損毀訊息數目。</span><span class="sxs-lookup"><span data-stu-id="7c41c-112">The number of corrupted messages that were received by the instance.</span></span>|  
|<span data-ttu-id="7c41c-113">**Dequeued Transmission Msgs/sec**</span><span class="sxs-lookup"><span data-stu-id="7c41c-113">**Dequeued Transmission Msgs/sec**</span></span>|<span data-ttu-id="7c41c-114">每秒從 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 傳輸佇列中移除的訊息數目。</span><span class="sxs-lookup"><span data-stu-id="7c41c-114">The number of messages that have been removed from the [!INCLUDE[ssSB](../../includes/sssb-md.md)] transmission queue per second.</span></span>|  
|<span data-ttu-id="7c41c-115">**Dialog timer event count**</span><span class="sxs-lookup"><span data-stu-id="7c41c-115">**Dialog timer event count**</span></span>|<span data-ttu-id="7c41c-116">在對話通訊協定層中使用中的計時器數目。</span><span class="sxs-lookup"><span data-stu-id="7c41c-116">The number of timers active in the dialog protocol layer.</span></span> <span data-ttu-id="7c41c-117">此數目與使用中對話的數目一致。</span><span class="sxs-lookup"><span data-stu-id="7c41c-117">This number corresponds to the number of active dialogs.</span></span>|  
|<span data-ttu-id="7c41c-118">**Dropped Messages Total**</span><span class="sxs-lookup"><span data-stu-id="7c41c-118">**Dropped Messages Total**</span></span>|<span data-ttu-id="7c41c-119">執行個體收到但是無法傳遞至佇列的訊息數目。</span><span class="sxs-lookup"><span data-stu-id="7c41c-119">The number of messages that were received by the instance, but could not be delivered to a queue.</span></span>|  
|<span data-ttu-id="7c41c-120">**Enqueued Local Messages Total**</span><span class="sxs-lookup"><span data-stu-id="7c41c-120">**Enqueued Local Messages Total**</span></span>|<span data-ttu-id="7c41c-121">在執行個體的佇列中已放置的訊息數目，但只計數透過網路傳送而未到達的訊息。</span><span class="sxs-lookup"><span data-stu-id="7c41c-121">The number of messages that have been put into the queues in the instance, counting only messages that did not arrive through the network.</span></span>|  
|<span data-ttu-id="7c41c-122">**Enqueued Local Messages/sec**</span><span class="sxs-lookup"><span data-stu-id="7c41c-122">**Enqueued Local Messages/sec**</span></span>|<span data-ttu-id="7c41c-123">在執行個體的佇列中每秒所放置的訊息數目，但只計數透過網路傳送而未到達的訊息。</span><span class="sxs-lookup"><span data-stu-id="7c41c-123">The number of messages per second that have been put into the queues in the instance, counting only messages that did not arrive through the network.</span></span>|  
|<span data-ttu-id="7c41c-124">**Enqueued Messages Total**</span><span class="sxs-lookup"><span data-stu-id="7c41c-124">**Enqueued Messages Total**</span></span>|<span data-ttu-id="7c41c-125">在執行個體的佇列中已放置的訊息總數。</span><span class="sxs-lookup"><span data-stu-id="7c41c-125">The total number of messages that have been put into the queues in the instance.</span></span>|  
|<span data-ttu-id="7c41c-126">**Enqueued Messages/sec**</span><span class="sxs-lookup"><span data-stu-id="7c41c-126">**Enqueued Messages/sec**</span></span>|<span data-ttu-id="7c41c-127">在執行個體的佇列中每秒所放置的訊息數目。</span><span class="sxs-lookup"><span data-stu-id="7c41c-127">The number of messages per second that have been put into the queues in the instance.</span></span> <span data-ttu-id="7c41c-128">這包括所有優先順序層級的訊息。</span><span class="sxs-lookup"><span data-stu-id="7c41c-128">This includes messages of all priority levels.</span></span>|  
|<span data-ttu-id="7c41c-129">**Enqueued P1 Msgs/sec**</span><span class="sxs-lookup"><span data-stu-id="7c41c-129">**Enqueued P1 Msgs/sec**</span></span>|<span data-ttu-id="7c41c-130">在執行個體的佇列中每秒所放置的優先順序 1 訊息數目。</span><span class="sxs-lookup"><span data-stu-id="7c41c-130">The number of priority 1 messages per second that have been put into the queues in the instance.</span></span>|  
|<span data-ttu-id="7c41c-131">**Enqueued P2 Msgs/sec**</span><span class="sxs-lookup"><span data-stu-id="7c41c-131">**Enqueued P2 Msgs/sec**</span></span>|<span data-ttu-id="7c41c-132">在執行個體的佇列中每秒所放置的優先順序 2 訊息數目。</span><span class="sxs-lookup"><span data-stu-id="7c41c-132">The number of priority 2 messages per second that have been put into the queues in the instance.</span></span>|  
|<span data-ttu-id="7c41c-133">**Enqueued P3 Msgs/sec**</span><span class="sxs-lookup"><span data-stu-id="7c41c-133">**Enqueued P3 Msgs/sec**</span></span>|<span data-ttu-id="7c41c-134">在執行個體的佇列中每秒所放置的優先順序 3 訊息數目。</span><span class="sxs-lookup"><span data-stu-id="7c41c-134">The number of priority 3 messages per second that have been put into the queues in the instance.</span></span>|  
|<span data-ttu-id="7c41c-135">**Enqueued P4 Msgs/sec**</span><span class="sxs-lookup"><span data-stu-id="7c41c-135">**Enqueued P4 Msgs/sec**</span></span>|<span data-ttu-id="7c41c-136">在執行個體的佇列中每秒所放置的優先順序 4 訊息數目。</span><span class="sxs-lookup"><span data-stu-id="7c41c-136">The number of priority 4 messages per second that have been put into the queues in the instance.</span></span>|  
|<span data-ttu-id="7c41c-137">**Enqueued P5 Msgs/sec**</span><span class="sxs-lookup"><span data-stu-id="7c41c-137">**Enqueued P5 Msgs/sec**</span></span>|<span data-ttu-id="7c41c-138">在執行個體的佇列中每秒所放置的優先順序 5 訊息數目。</span><span class="sxs-lookup"><span data-stu-id="7c41c-138">The number of priority 5 messages per second that have been put into the queues in the instance.</span></span>|  
|<span data-ttu-id="7c41c-139">**Enqueued P6 Msgs/sec**</span><span class="sxs-lookup"><span data-stu-id="7c41c-139">**Enqueued P6 Msgs/sec**</span></span>|<span data-ttu-id="7c41c-140">在執行個體的佇列中每秒所放置的優先順序 6 訊息數目。</span><span class="sxs-lookup"><span data-stu-id="7c41c-140">The number of priority 6 messages per second that have been put into the queues in the instance.</span></span>|  
|<span data-ttu-id="7c41c-141">**Enqueued P7 Msgs/sec**</span><span class="sxs-lookup"><span data-stu-id="7c41c-141">**Enqueued P7 Msgs/sec**</span></span>|<span data-ttu-id="7c41c-142">在執行個體的佇列中每秒所放置的優先順序 7 訊息數目。</span><span class="sxs-lookup"><span data-stu-id="7c41c-142">The number of priority 7 messages per second that have been put into the queues in the instance.</span></span>|  
|<span data-ttu-id="7c41c-143">**Enqueued P8 Msgs/sec**</span><span class="sxs-lookup"><span data-stu-id="7c41c-143">**Enqueued P8 Msgs/sec**</span></span>|<span data-ttu-id="7c41c-144">在執行個體的佇列中每秒所放置的優先順序 8 訊息數目。</span><span class="sxs-lookup"><span data-stu-id="7c41c-144">The number of priority 8 messages per second that have been put into the queues in the instance.</span></span>|  
|<span data-ttu-id="7c41c-145">**Enqueued P9 Msgs/sec**</span><span class="sxs-lookup"><span data-stu-id="7c41c-145">**Enqueued P9 Msgs/sec**</span></span>|<span data-ttu-id="7c41c-146">在執行個體的佇列中每秒所放置的優先順序 9 訊息數目。</span><span class="sxs-lookup"><span data-stu-id="7c41c-146">The number of priority 9 messages per second that have been put into the queues in the instance.</span></span>|  
|<span data-ttu-id="7c41c-147">**Enqueued P10 Msgs/sec**</span><span class="sxs-lookup"><span data-stu-id="7c41c-147">**Enqueued P10 Msgs/sec**</span></span>|<span data-ttu-id="7c41c-148">在執行個體的佇列中每秒所放置的優先順序 10 訊息數目。</span><span class="sxs-lookup"><span data-stu-id="7c41c-148">The number of priority 10 messages per second that have been put into the queues in the instance.</span></span>|  
|<span data-ttu-id="7c41c-149">**Enqueued Transmission Msgs/sec**</span><span class="sxs-lookup"><span data-stu-id="7c41c-149">**Enqueued Transmission Msgs/sec**</span></span>|<span data-ttu-id="7c41c-150">每秒在 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 傳輸佇列中放置的訊息數目。</span><span class="sxs-lookup"><span data-stu-id="7c41c-150">The number of messages that have been placed in the [!INCLUDE[ssSB](../../includes/sssb-md.md)] transmission queue per second.</span></span>|  
|<span data-ttu-id="7c41c-151">**Enqueued Transport Msg Frag Tot**</span><span class="sxs-lookup"><span data-stu-id="7c41c-151">**Enqueued Transport Msg Frag Tot**</span></span>|<span data-ttu-id="7c41c-152">在執行個體的佇列中已放置的訊息片段數目，但只計數透過網路傳送已到達的訊息。</span><span class="sxs-lookup"><span data-stu-id="7c41c-152">The number of message fragments that have been put into the queues in the instance, counting only messages that arrived through the network.</span></span>|  
|<span data-ttu-id="7c41c-153">**Enqueued Transport Msg Frags/sec**</span><span class="sxs-lookup"><span data-stu-id="7c41c-153">**Enqueued Transport Msg Frags/sec**</span></span>|<span data-ttu-id="7c41c-154">在執行個體的佇列中每秒所放置的訊息片段數目。</span><span class="sxs-lookup"><span data-stu-id="7c41c-154">The number of message fragments per second that have been put into the queues in the instance.</span></span>|  
|<span data-ttu-id="7c41c-155">**Enqueued Transport Msgs Total**</span><span class="sxs-lookup"><span data-stu-id="7c41c-155">**Enqueued Transport Msgs Total**</span></span>|<span data-ttu-id="7c41c-156">在執行個體的佇列中已放置的訊息數目，但只計數透過網路傳送已到達的訊息。</span><span class="sxs-lookup"><span data-stu-id="7c41c-156">The number of messages that have been put into the queues in the instance, counting only messages that arrived through the network.</span></span>|  
|<span data-ttu-id="7c41c-157">**Enqueued Transport Msgs/sec**</span><span class="sxs-lookup"><span data-stu-id="7c41c-157">**Enqueued Transport Msgs/sec**</span></span>|<span data-ttu-id="7c41c-158">在執行個體的佇列中每秒所放置的訊息數目，但只計數透過網路傳送已到達的訊息。</span><span class="sxs-lookup"><span data-stu-id="7c41c-158">The number of messages per second that have been put into the queues in the instance, counting only messages that arrived through the network.</span></span>|  
|<span data-ttu-id="7c41c-159">**Forwarded Messages Total**</span><span class="sxs-lookup"><span data-stu-id="7c41c-159">**Forwarded Messages Total**</span></span>|<span data-ttu-id="7c41c-160">此電腦所轉寄的 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 訊息總數。</span><span class="sxs-lookup"><span data-stu-id="7c41c-160">The total number of [!INCLUDE[ssSB](../../includes/sssb-md.md)] messages forwarded by this computer.</span></span>|  
|<span data-ttu-id="7c41c-161">**Forwarded Messages/sec**</span><span class="sxs-lookup"><span data-stu-id="7c41c-161">**Forwarded Messages/sec**</span></span>|<span data-ttu-id="7c41c-162">此電腦每秒所轉寄的訊息數目。</span><span class="sxs-lookup"><span data-stu-id="7c41c-162">The number of messages per second forwarded by this computer.</span></span>|  
|<span data-ttu-id="7c41c-163">**Forwarded Msg Byte Total**</span><span class="sxs-lookup"><span data-stu-id="7c41c-163">**Forwarded Msg Byte Total**</span></span>|<span data-ttu-id="7c41c-164">此電腦所轉寄的訊息總大小 (位元組)。</span><span class="sxs-lookup"><span data-stu-id="7c41c-164">The total size, in bytes, of the messages forwarded by this computer.</span></span>|  
|<span data-ttu-id="7c41c-165">**Forwarded Msg Bytes/sec**</span><span class="sxs-lookup"><span data-stu-id="7c41c-165">**Forwarded Msg Bytes/sec**</span></span>|<span data-ttu-id="7c41c-166">此電腦每秒所轉寄的訊息大小 (位元組)。</span><span class="sxs-lookup"><span data-stu-id="7c41c-166">The size, in bytes, of messages per second forwarded by this computer.</span></span>|  
|<span data-ttu-id="7c41c-167">**Forwarded Msg Discarded Total**</span><span class="sxs-lookup"><span data-stu-id="7c41c-167">**Forwarded Msg Discarded Total**</span></span>|<span data-ttu-id="7c41c-168">此電腦接收要轉寄的訊息數目，但並未成功轉寄。</span><span class="sxs-lookup"><span data-stu-id="7c41c-168">The number of messages that this computer received for forwarding, but did not successfully forward.</span></span>|  
|<span data-ttu-id="7c41c-169">**Forwarded Msg Discarded/sec**</span><span class="sxs-lookup"><span data-stu-id="7c41c-169">**Forwarded Msg Discarded/sec**</span></span>|<span data-ttu-id="7c41c-170">此電腦每秒接收要轉寄的訊息數目，但並未成功轉寄。</span><span class="sxs-lookup"><span data-stu-id="7c41c-170">The number of messages per second that this computer received for forwarding, but did not successfully forward.</span></span>|  
|<span data-ttu-id="7c41c-171">**Forwarded Pending Msg Bytes**</span><span class="sxs-lookup"><span data-stu-id="7c41c-171">**Forwarded Pending Msg Bytes**</span></span>|<span data-ttu-id="7c41c-172">目前保留要轉寄的訊息總大小。</span><span class="sxs-lookup"><span data-stu-id="7c41c-172">The total size of the messages currently held for forwarding.</span></span>|  
|<span data-ttu-id="7c41c-173">**Forwarded Pending Msg Count**</span><span class="sxs-lookup"><span data-stu-id="7c41c-173">**Forwarded Pending Msg Count**</span></span>|<span data-ttu-id="7c41c-174">目前保留要轉寄的訊息總數目。</span><span class="sxs-lookup"><span data-stu-id="7c41c-174">The total number of messages currently held for forwarding.</span></span>|  
|<span data-ttu-id="7c41c-175">**SQL RECEIVE Total**</span><span class="sxs-lookup"><span data-stu-id="7c41c-175">**SQL RECEIVE Total**</span></span>|<span data-ttu-id="7c41c-176">已處理的 [!INCLUDE[tsql](../../includes/tsql-md.md)] RECEIVE 陳述式總數。</span><span class="sxs-lookup"><span data-stu-id="7c41c-176">The total number of [!INCLUDE[tsql](../../includes/tsql-md.md)] RECEIVE statements processed.</span></span>|  
|<span data-ttu-id="7c41c-177">**SQL RECEIVEs/sec**</span><span class="sxs-lookup"><span data-stu-id="7c41c-177">**SQL RECEIVEs/sec**</span></span>|<span data-ttu-id="7c41c-178">每秒已處理的 [!INCLUDE[tsql](../../includes/tsql-md.md)] RECEIVE 陳述式數目。</span><span class="sxs-lookup"><span data-stu-id="7c41c-178">The number of [!INCLUDE[tsql](../../includes/tsql-md.md)] RECEIVE statements processed per second.</span></span>|  
|<span data-ttu-id="7c41c-179">**SQL SEND Total**</span><span class="sxs-lookup"><span data-stu-id="7c41c-179">**SQL SEND Total**</span></span>|<span data-ttu-id="7c41c-180">已執行的 [!INCLUDE[tsql](../../includes/tsql-md.md)] SEND 陳述式總數。</span><span class="sxs-lookup"><span data-stu-id="7c41c-180">The total number of [!INCLUDE[tsql](../../includes/tsql-md.md)] SEND statements executed.</span></span>|  
|<span data-ttu-id="7c41c-181">**SQL SENDs/sec**</span><span class="sxs-lookup"><span data-stu-id="7c41c-181">**SQL SENDs/sec**</span></span>|<span data-ttu-id="7c41c-182">每秒已執行的 [!INCLUDE[tsql](../../includes/tsql-md.md)] SEND 陳述式數目。</span><span class="sxs-lookup"><span data-stu-id="7c41c-182">The number of [!INCLUDE[tsql](../../includes/tsql-md.md)] SEND statements executed per second.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7c41c-183">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c41c-183">See Also</span></span>  
 <span data-ttu-id="7c41c-184">[SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md) </span><span class="sxs-lookup"><span data-stu-id="7c41c-184">[SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md) </span></span>  
 [<span data-ttu-id="7c41c-185">監視資源使用狀況 &#40;System Monitor&#41;</span><span class="sxs-lookup"><span data-stu-id="7c41c-185">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  