---
title: Integration Services 容器 | Microsoft Docs
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS containers
- containers [Integration Services]
- containers [Integration Services], about containers
- control flow [Integration Services], containers
- SQL Server Integration Services containers
ms.assetid: 1b725922-ec59-4a47-9d55-e079463058f3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1b8c3904d74427d5f70bd3ae81890adf66e9f818
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594628"
---
# <a name="integration-services-containers"></a><span data-ttu-id="bfd6d-102">整合服務容器</span><span class="sxs-lookup"><span data-stu-id="bfd6d-102">Integration Services Containers</span></span>
  <span data-ttu-id="bfd6d-103">容器是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 中的物件，可提供結構給套件，並提供服務給工作。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-103">Containers are objects in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] that provide structure to packages and services to tasks.</span></span> <span data-ttu-id="bfd6d-104">它們支援封裝中的重複控制流程，且會將工作和容器分組成有意義的工作單位。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-104">They support repeating control flows in packages, and they group tasks and containers into meaningful units of work.</span></span> <span data-ttu-id="bfd6d-105">除了工作外，容器還可包含其他容器。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-105">Containers can include other containers in addition to tasks.</span></span>  
  
 <span data-ttu-id="bfd6d-106">封裝會將容器用於下列用途：</span><span class="sxs-lookup"><span data-stu-id="bfd6d-106">Packages use containers for the following purposes:</span></span>  
  
-   <span data-ttu-id="bfd6d-107">針對集合中的每個元素重複工作，例如資料夾中的檔案、結構描述或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理物件 (SMO) 的物件。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-107">Repeat tasks for each element in a collection, such as files in a folder, schemas, or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects (SMO) objects.</span></span> <span data-ttu-id="bfd6d-108">例如，封裝可執行位於多個檔案中的 Transact-SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-108">For example, a package can run Transact-SQL statements that reside in multiple files.</span></span>  
  
-   <span data-ttu-id="bfd6d-109">重複工作直到指定運算式評估結果為 `false` 為止。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-109">Repeat tasks until a specified expression evaluates to `false`.</span></span> <span data-ttu-id="bfd6d-110">例如，封裝可傳送不同的電子郵件訊息七次，一週中的每一天各一次。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-110">For example, a package can send a different e-mail message seven times, one time for every day of the week.</span></span>  
  
-   <span data-ttu-id="bfd6d-111">將必須當做一個單位同時成功或失敗的工作和容器予以分組。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-111">Group tasks and containers that must succeed or fail as a unit.</span></span> <span data-ttu-id="bfd6d-112">例如，封裝可將刪除或加入資料庫資料表中資料列的工作予以分組，然後在一個工作失敗時認可或回復所有工作。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-112">For example, a package can group tasks that delete and add rows in a database table, and then commit or roll back all the tasks when one fails.</span></span>  
  
## <a name="container-types"></a><span data-ttu-id="bfd6d-113">容器類型</span><span class="sxs-lookup"><span data-stu-id="bfd6d-113">Container Types</span></span>  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="bfd6d-114">提供四種用於建立封裝的容器類型。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-114">provides four types of containers for building packages.</span></span> <span data-ttu-id="bfd6d-115">下表列出這些容器類型。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-115">The following table lists the container types.</span></span>  
  
|<span data-ttu-id="bfd6d-116">容器</span><span class="sxs-lookup"><span data-stu-id="bfd6d-116">Container</span></span>|<span data-ttu-id="bfd6d-117">描述</span><span class="sxs-lookup"><span data-stu-id="bfd6d-117">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="bfd6d-118">Foreach 迴圈容器</span><span class="sxs-lookup"><span data-stu-id="bfd6d-118">Foreach Loop Container</span></span>](foreach-loop-container.md)|<span data-ttu-id="bfd6d-119">使用列舉值重複執行控制流程。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-119">Runs a control flow repeatedly by using an enumerator.</span></span>|  
|[<span data-ttu-id="bfd6d-120">For 迴圈容器</span><span class="sxs-lookup"><span data-stu-id="bfd6d-120">For Loop Container</span></span>](for-loop-container.md)|<span data-ttu-id="bfd6d-121">藉由測試條件重複執行控制流程。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-121">Runs a control flow repeatedly by testing a condition.</span></span>|  
|[<span data-ttu-id="bfd6d-122">時序容器</span><span class="sxs-lookup"><span data-stu-id="bfd6d-122">Sequence Container</span></span>](sequence-container.md)|<span data-ttu-id="bfd6d-123">將工作和容器分組成控制流程，這些控制流程是封裝控制流程的子集。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-123">Groups tasks and containers into control flows that are subsets of the package control flow.</span></span>|  
|[<span data-ttu-id="bfd6d-124">工作主機容器</span><span class="sxs-lookup"><span data-stu-id="bfd6d-124">Task Host Container</span></span>](task-host-container.md)|<span data-ttu-id="bfd6d-125">提供服務給單一工作。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-125">Provides services to a single task.</span></span>|  
  
 <span data-ttu-id="bfd6d-126">封裝和事件處理常式也是容器的類型。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-126">Packages and events handlers are also types of containers.</span></span> <span data-ttu-id="bfd6d-127">如需相關資訊，請參閱 [Integration Services &#40;SSIS&#41; 封裝](../integration-services-ssis-packages.md)和 [Integration Services &#40;SSIS&#41; 事件處理常式](../integration-services-ssis-event-handlers.md)。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-127">For information see [Integration Services &#40;SSIS&#41; Packages](../integration-services-ssis-packages.md) and [Integration Services &#40;SSIS&#41; Event Handlers](../integration-services-ssis-event-handlers.md).</span></span>  
  
### <a name="summary-of-container-properties"></a><span data-ttu-id="bfd6d-128">容器屬性摘要</span><span class="sxs-lookup"><span data-stu-id="bfd6d-128">Summary of Container Properties</span></span>  
 <span data-ttu-id="bfd6d-129">所有容器類型都有通用的屬性集。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-129">All container types have a set of properties in common.</span></span> <span data-ttu-id="bfd6d-130">如果您使用 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 提供的圖形工具建立封裝，[屬性] 視窗會列出下列「Foreach 迴圈」、「For 迴圈」以及「時序」容器的屬性。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-130">If you create packages using the graphical tools that [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] provides, the Properties window lists the following properties for the Foreach Loop, For Loop, and Sequence containers.</span></span> <span data-ttu-id="bfd6d-131">工作主機容器屬性會做為設定該工作主機封裝之工作的一部分來設定。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-131">The task host container properties are configured as part of configuring the task that the task host encapsulates.</span></span> <span data-ttu-id="bfd6d-132">在您設定工作時，可同時設定「工作主機」屬性。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-132">You set the Task Host properties when you configure the task.</span></span>  
  
|<span data-ttu-id="bfd6d-133">屬性</span><span class="sxs-lookup"><span data-stu-id="bfd6d-133">Property</span></span>|<span data-ttu-id="bfd6d-134">描述</span><span class="sxs-lookup"><span data-stu-id="bfd6d-134">Description</span></span>|  
|--------------|-----------------|  
|`DelayValidation`|<span data-ttu-id="bfd6d-135">布林值，指出是否延遲至執行階段才驗證容器。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-135">A Boolean value that indicates whether validation of the container is delayed until run time.</span></span> <span data-ttu-id="bfd6d-136">這個屬性的預設值為 `False`。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-136">The default value for this property is `False`.</span></span><br /><br /> <span data-ttu-id="bfd6d-137">如需詳細資訊，請參閱<xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.DelayValidation%2A>。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-137">For more information, see <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.DelayValidation%2A>.</span></span>|  
|`Description`|<span data-ttu-id="bfd6d-138">容器描述。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-138">The container description.</span></span> <span data-ttu-id="bfd6d-139">該屬性包含字串，但可能空白。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-139">The property contains a string, but may be blank.</span></span><br /><br /> <span data-ttu-id="bfd6d-140">如需詳細資訊，請參閱<xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.Description%2A>。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-140">For more information, see <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.Description%2A>.</span></span>|  
|`Disable`|<span data-ttu-id="bfd6d-141">布林值，指出容器是否執行。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-141">A Boolean value that indicates whether the container runs.</span></span> <span data-ttu-id="bfd6d-142">這個屬性的預設值為 `False`。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-142">The default value for this property is `False`.</span></span><br /><br /> <span data-ttu-id="bfd6d-143">如需詳細資訊，請參閱<xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.Disable%2A>。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-143">For more information, see <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.Disable%2A>.</span></span>|  
|`DisableEventHandlers`|<span data-ttu-id="bfd6d-144">布林值，指出與該容器關聯的事件處理常式是否執行。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-144">A Boolean value that indicates whether the event handlers associated with the container run.</span></span> <span data-ttu-id="bfd6d-145">這個屬性的預設值為 `False`。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-145">The default value for this property is `False`.</span></span>|  
|`FailPackageOnFailure`|<span data-ttu-id="bfd6d-146">布林值，指定如果容器中發生錯誤，封裝是否失敗。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-146">A Boolean value that specifies whether the package fails if an error occurs in the container.</span></span> <span data-ttu-id="bfd6d-147">這個屬性的預設值為 `False`。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-147">The default value for this property is `False`.</span></span><br /><br /> <span data-ttu-id="bfd6d-148">如需詳細資訊，請參閱<xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.FailPackageOnFailure%2A>。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-148">For more information, see <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.FailPackageOnFailure%2A>.</span></span>|  
|`FailParentOnFailure`|<span data-ttu-id="bfd6d-149">布林值，指定如果容器中發生錯誤，父容器是否失敗。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-149">A Boolean value that specifies whether the parent container fails if an error occurs in the container.</span></span> <span data-ttu-id="bfd6d-150">這個屬性的預設值為 `False`。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-150">The default value for this property is `False`.</span></span><br /><br /> <span data-ttu-id="bfd6d-151">如需詳細資訊，請參閱<xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.FailParentOnFailure%2A>。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-151">For more information, see <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.FailParentOnFailure%2A>.</span></span>|  
|`ForcedExecutionValue`|<span data-ttu-id="bfd6d-152">如果 `ForceExecutionValue` 設定為 `True`，則是包含容器之選擇性執行值的物件。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-152">If `ForceExecutionValue` is set to `True`, the object that contains the optional execution value for the container.</span></span> <span data-ttu-id="bfd6d-153">這個屬性的預設值為 **0**。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-153">The default value of this property is **0**.</span></span><br /><br /> <span data-ttu-id="bfd6d-154">如需詳細資訊，請參閱<xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.ForcedExecutionValue%2A>。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-154">For more information, see <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.ForcedExecutionValue%2A>.</span></span>|  
|`ForcedExecutionValueType`|<span data-ttu-id="bfd6d-155">`ForcedExecutionValue` 的資料類型。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-155">The data type of `ForcedExecutionValue`.</span></span> <span data-ttu-id="bfd6d-156">此屬性的預設值為 `Int32`。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-156">The default value of this property is `Int32`.</span></span>|  
|`ForceExecutionResult`|<span data-ttu-id="bfd6d-157">指定執行封裝或容器之強制結果的值。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-157">A value that specifies the forced result of running the package or container.</span></span> <span data-ttu-id="bfd6d-158">可能的值為 `None`、`Success`、`Failure` 和 `Completion`。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-158">The values are `None`, `Success`, `Failure`, and `Completion`.</span></span> <span data-ttu-id="bfd6d-159">這個屬性的預設值為 `None`。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-159">The default value for this property is `None`.</span></span><br /><br /> <span data-ttu-id="bfd6d-160">如需詳細資訊，請參閱<xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.ForceExecutionResult%2A>。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-160">For more information, see <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.ForceExecutionResult%2A>.</span></span>|  
|`ForceExecutionValue`|<span data-ttu-id="bfd6d-161">布林值，指定是否應該強制執行容器的選擇性執行值以包含特定值。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-161">A Boolean value that specifies whether the optional execution value of the container should be forced to contain a particular value.</span></span> <span data-ttu-id="bfd6d-162">此屬性的預設值為 `False`。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-162">The default value of this property is `False`.</span></span><br /><br /> <span data-ttu-id="bfd6d-163">如需詳細資訊，請參閱<xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.ForceExecutionValue%2A>。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-163">For more information, see <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.ForceExecutionValue%2A>.</span></span>|  
|`ID`|<span data-ttu-id="bfd6d-164">在建立封裝時所指派的容器 GUID。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-164">The container GUID, which is assigned when the package is created.</span></span> <span data-ttu-id="bfd6d-165">這個屬性是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-165">This property is read-only.</span></span><br /><br /> <span data-ttu-id="bfd6d-166"><xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.ID%2A>.</span><span class="sxs-lookup"><span data-stu-id="bfd6d-166"><xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.ID%2A>.</span></span>|  
|`IsolationLevel`|<span data-ttu-id="bfd6d-167">容器交易的隔離等級。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-167">The isolation level of the container transaction.</span></span> <span data-ttu-id="bfd6d-168">可能的值為 `Unspecified`、`Chaos`、`ReadUncommitted`、`ReadCommitted`、`RepeatableRead`、`Serializable` 和 `Snapshot`。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-168">The values are `Unspecified`, `Chaos`, `ReadUncommitted`, `ReadCommitted`, `RepeatableRead`, `Serializable`, and `Snapshot`.</span></span> <span data-ttu-id="bfd6d-169">此屬性的預設值為 `Serializable`。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-169">The default value of this property is `Serializable`.</span></span> <span data-ttu-id="bfd6d-170">如需詳細資訊，請參閱<xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.IsolationLevel%2A>。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-170">For more information, see <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.IsolationLevel%2A>.</span></span>|  
|`LocaleID`|<span data-ttu-id="bfd6d-171">Microsoft Win32 地區設定。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-171">A Microsoft Win32 locale.</span></span> <span data-ttu-id="bfd6d-172">此屬性的預設值為本機電腦作業系統的地區設定。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-172">The default value of this property is the locale of the operating system on the local computer.</span></span><br /><br /> <span data-ttu-id="bfd6d-173">如需詳細資訊，請參閱 <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.LocaleID%2A>。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-173">For more information, see <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.LocaleID%2A>.</span></span>|  
|`LoggingMode`|<span data-ttu-id="bfd6d-174">指定容器記錄行為的值。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-174">A value that specifies the logging behavior of the container.</span></span> <span data-ttu-id="bfd6d-175">這些值為 `Disabled`、`Enabled` 和 `UseParentSetting`。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-175">The values are `Disabled`, `Enabled`, and `UseParentSetting`.</span></span> <span data-ttu-id="bfd6d-176">此屬性的預設值為 `UseParentSetting`。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-176">The default value of this property is `UseParentSetting`.</span></span> <span data-ttu-id="bfd6d-177">如需詳細資訊，請參閱<xref:Microsoft.SqlServer.Dts.Runtime.DTSLoggingMode>。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-177">For more information, see <xref:Microsoft.SqlServer.Dts.Runtime.DTSLoggingMode>.</span></span>|  
|`MaximumErrorCount`|<span data-ttu-id="bfd6d-178">在容器停止執行之前，可發生的最大錯誤次數。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-178">The maximum number of errors that can occur before a container stops running.</span></span> <span data-ttu-id="bfd6d-179">這個屬性的預設值為 **1**。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-179">The default value of this property is **1**.</span></span><br /><br /> <span data-ttu-id="bfd6d-180">如需詳細資訊，請參閱<xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.MaximumErrorCount%2A>。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-180">For more information, see <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.MaximumErrorCount%2A>.</span></span>|  
|`Name`|<span data-ttu-id="bfd6d-181">容器的名稱。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-181">The name of the container.</span></span><br /><br /> <span data-ttu-id="bfd6d-182">如需詳細資訊，請參閱 <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.Name%2A>。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-182">For more information, see <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.Name%2A>.</span></span>|  
|`TransactionOption`|<span data-ttu-id="bfd6d-183">容器的交易式參與。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-183">The transactional participation of the container.</span></span> <span data-ttu-id="bfd6d-184">可能的值為 `NotSupported`、`Supported`、`Required`。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-184">The values are `NotSupported`, `Supported`, `Required`.</span></span> <span data-ttu-id="bfd6d-185">此屬性的預設值為 `Supported`。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-185">The default value of this property is `Supported`.</span></span> <span data-ttu-id="bfd6d-186">如需詳細資訊，請參閱 <xref:Microsoft.SqlServer.Dts.Runtime.DTSTransactionOption>。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-186">For more information, see <xref:Microsoft.SqlServer.Dts.Runtime.DTSTransactionOption>.</span></span>|  
  
 <span data-ttu-id="bfd6d-187">若要了解有關在以程式設計方式設定「Foreach 迴圈」、「For 迴圈」、「時序」及「工作主機」容器時，這些項目可用的所有屬性，請參閱下列 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] API 主題：</span><span class="sxs-lookup"><span data-stu-id="bfd6d-187">To learn about all the properties that are available to Foreach Loop, For Loop, Sequence, and Task Host containers when configure them programmatically, see the following [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] API topics:</span></span>  
  
-   <span data-ttu-id="bfd6d-188">T:Microsoft.SqlServer.Dts.Runtime.ForEachLoop</span><span class="sxs-lookup"><span data-stu-id="bfd6d-188">T:Microsoft.SqlServer.Dts.Runtime.ForEachLoop</span></span>  
  
-   <span data-ttu-id="bfd6d-189">T:Microsoft.SqlServer.Dts.Runtime.ForLoop</span><span class="sxs-lookup"><span data-stu-id="bfd6d-189">T:Microsoft.SqlServer.Dts.Runtime.ForLoop</span></span>  
  
-   <span data-ttu-id="bfd6d-190">T:Microsoft.SqlServer.Dts.Runtime.Sequence</span><span class="sxs-lookup"><span data-stu-id="bfd6d-190">T:Microsoft.SqlServer.Dts.Runtime.Sequence</span></span>  
  
-   <span data-ttu-id="bfd6d-191">T:Microsoft.SqlServer.Dts.Runtime.TaskHost</span><span class="sxs-lookup"><span data-stu-id="bfd6d-191">T:Microsoft.SqlServer.Dts.Runtime.TaskHost</span></span>  
  
## <a name="objects-that-extend-container-functionality"></a><span data-ttu-id="bfd6d-192">延伸容器功能的物件</span><span class="sxs-lookup"><span data-stu-id="bfd6d-192">Objects that Extend Container Functionality</span></span>  
 <span data-ttu-id="bfd6d-193">容器包括由可執行檔和優先順序條件約束所組成的控制流程，並可使用事件處理常式和變數。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-193">Containers include control flows that consist of executables and precedence constraints, and may use event handlers, and variables.</span></span> <span data-ttu-id="bfd6d-194">工作主機容器則是例外：由於工作主機容器會封裝單一工作，因此不會使用優先順序條件約束。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-194">The task host container is an exception: because the task host container encapsulates a single task, it does not use precedence constraints.</span></span>  
  
### <a name="executables"></a><span data-ttu-id="bfd6d-195">可執行檔</span><span class="sxs-lookup"><span data-stu-id="bfd6d-195">Executables</span></span>  
 <span data-ttu-id="bfd6d-196">可執行檔指的是容器層級工作，以及容器內的任何容器。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-196">Executables refers to the container-level tasks and any containers within the container.</span></span> <span data-ttu-id="bfd6d-197">可執行檔可以是 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 所提供的其中一個工作和容器，也可以是自訂工作。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-197">An executable can be one of the tasks and containers that [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] provides or a custom task.</span></span> <span data-ttu-id="bfd6d-198">如需詳細資訊，請參閱[Integration Services](integration-services-tasks.md)工作和[Integration Services 容器](integration-services-containers.md)。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-198">For more information, see [Integration Services Tasks](integration-services-tasks.md) and [Integration Services Containers](integration-services-containers.md).</span></span>  
  
### <a name="precedence-constraints"></a><span data-ttu-id="bfd6d-199">優先順序條件約束</span><span class="sxs-lookup"><span data-stu-id="bfd6d-199">Precedence Constraints</span></span>  
 <span data-ttu-id="bfd6d-200">優先順序條件約束可將相同父容器中的工作，連結成已排序的控制流程。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-200">Precedence constraints link containers and tasks within the same parent container into an ordered control flow.</span></span> <span data-ttu-id="bfd6d-201">如需詳細資訊，請參閱 [優先順序條件約束](precedence-constraints.md)。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-201">For more information, see [Precedence Constraints](precedence-constraints.md).</span></span>  
  
### <a name="event-handlers"></a><span data-ttu-id="bfd6d-202">事件處理常式</span><span class="sxs-lookup"><span data-stu-id="bfd6d-202">Event Handlers</span></span>  
 <span data-ttu-id="bfd6d-203">容器層級的事件處理常式，可回應由容器或其中所含物件所引發的事件。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-203">Event handlers at the container level respond to events raised by the container or the objects it includes.</span></span> <span data-ttu-id="bfd6d-204">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 事件處理常式](../integration-services-ssis-event-handlers.md)。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-204">For more information, see [Integration Services &#40;SSIS&#41; Event Handlers](../integration-services-ssis-event-handlers.md).</span></span>  
  
### <a name="variables"></a><span data-ttu-id="bfd6d-205">變數</span><span class="sxs-lookup"><span data-stu-id="bfd6d-205">Variables</span></span>  
 <span data-ttu-id="bfd6d-206">容器中所用的變數包括 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 提供的容器層級系統變數，以及容器使用的使用者定義變數。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-206">Variables that are used in containers include the container-level system variables that [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] provides and the user-defined variables that the container uses.</span></span> <span data-ttu-id="bfd6d-207">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 變數](../integration-services-ssis-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-207">For more information, see [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md).</span></span>  
  
## <a name="break-points"></a><span data-ttu-id="bfd6d-208">中斷點</span><span class="sxs-lookup"><span data-stu-id="bfd6d-208">Break Points</span></span>  
 <span data-ttu-id="bfd6d-209">當您在容器上設定中斷點，且中斷條件為 **[當容器接收 OnVariableValueChanged 事件時中斷]** 時，請在容器範圍中定義變數。</span><span class="sxs-lookup"><span data-stu-id="bfd6d-209">When you set a breakpoint on a container and the break condition is **Break when the container recevies the OnVariableValueChanged event**, define the variable in the container scope.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfd6d-210">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bfd6d-210">See Also</span></span>  
 [<span data-ttu-id="bfd6d-211">控制流程</span><span class="sxs-lookup"><span data-stu-id="bfd6d-211">Control Flow</span></span>](control-flow.md)  
  
  