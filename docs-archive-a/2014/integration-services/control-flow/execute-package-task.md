---
title: 執行套件工作 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executepackagetask.f1
helpviewer_keywords:
- Execution Package task [Integration Services]
- child packages
- parent packages [Integration Services]
ms.assetid: 042d4ec0-0668-401c-bb3a-a25fe2602eac
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4f02594d67ad704885de1456651f5d086687ffd0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596213"
---
# <a name="execute-package-task"></a><span data-ttu-id="dd30e-102">執行封裝工作</span><span class="sxs-lookup"><span data-stu-id="dd30e-102">Execute Package Task</span></span>
  <span data-ttu-id="dd30e-103">「執行封裝」工作可讓封裝將其他封裝當做工作流程的一部分執行，以延伸 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 的企業功能。</span><span class="sxs-lookup"><span data-stu-id="dd30e-103">The Execute Package task extends the enterprise capabilities of [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] by letting packages run other packages as part of a workflow.</span></span>  
  
 <span data-ttu-id="dd30e-104">您可將「執行封裝」工作用於下列用途：</span><span class="sxs-lookup"><span data-stu-id="dd30e-104">You can use the Execute Package task for the following purposes:</span></span>  
  
-   <span data-ttu-id="dd30e-105">細分複雜的封裝工作流程。</span><span class="sxs-lookup"><span data-stu-id="dd30e-105">Breaking down complex package workflow.</span></span> <span data-ttu-id="dd30e-106">此工作可讓您將工作流程分解成多個封裝，以方便讀取、測試和維護。</span><span class="sxs-lookup"><span data-stu-id="dd30e-106">This task lets you break down workflow into multiple packages, which are easier to read, test, and maintain.</span></span> <span data-ttu-id="dd30e-107">例如，您若是將資料載入星狀結構描述，就可以建立另一個封裝以擴展每一個維度與事實資料表。</span><span class="sxs-lookup"><span data-stu-id="dd30e-107">For example, if you are loading data into a star schema, you can build a separate package to populate each dimension and the fact table.</span></span>  
  
-   <span data-ttu-id="dd30e-108">重複使用部分封裝。</span><span class="sxs-lookup"><span data-stu-id="dd30e-108">Reusing parts of packages.</span></span> <span data-ttu-id="dd30e-109">其他封裝可以重複使用封裝工作流程的各部分。</span><span class="sxs-lookup"><span data-stu-id="dd30e-109">Other packages can reuse parts of a package workflow.</span></span> <span data-ttu-id="dd30e-110">例如，您可以建置可從不同封裝呼叫的資料擷取模組。</span><span class="sxs-lookup"><span data-stu-id="dd30e-110">For example, you can build a data extraction module that can be called from different packages.</span></span> <span data-ttu-id="dd30e-111">呼叫擷取模組的每個封裝可以執行不同的資料刪除、篩選或彙總作業。</span><span class="sxs-lookup"><span data-stu-id="dd30e-111">Each package that calls the extraction module can perform different data scrubbing, filtering, or aggregation operations.</span></span>  
  
-   <span data-ttu-id="dd30e-112">群組工作單位。</span><span class="sxs-lookup"><span data-stu-id="dd30e-112">Grouping work units.</span></span> <span data-ttu-id="dd30e-113">工作的單位可以封裝到個別的封裝，並以交易式元件聯結至父封裝的工作流程。</span><span class="sxs-lookup"><span data-stu-id="dd30e-113">Units of work can be encapsulated into separate packages and joined as transactional components to the workflow of a parent package.</span></span> <span data-ttu-id="dd30e-114">例如，父封裝執行附帶封裝，並根據附帶封裝的成功或失敗認可或回復交易。</span><span class="sxs-lookup"><span data-stu-id="dd30e-114">For example, the parent package runs the accessory packages, and based on the success or failure of the accessory packages, the parent package either commits or rolls back the transaction.</span></span>  
  
-   <span data-ttu-id="dd30e-115">控制封裝安全性。</span><span class="sxs-lookup"><span data-stu-id="dd30e-115">Controlling package security.</span></span> <span data-ttu-id="dd30e-116">封裝作者只需要多封裝方案的一部分存取權。</span><span class="sxs-lookup"><span data-stu-id="dd30e-116">Package authors require access to only a part of a multipackage solution.</span></span> <span data-ttu-id="dd30e-117">您可藉由將封裝分成多個封裝，提供更高的安全性等級，這是因為您可以只將相關封裝的存取權授與給作者。</span><span class="sxs-lookup"><span data-stu-id="dd30e-117">By separating a package into multiple packages, you can provide a greater level of security, because you can grant an author access to only the relevant packages.</span></span>  
  
 <span data-ttu-id="dd30e-118">執行其他封裝的封裝一般稱為父封裝，而父工作流程執行的封裝則稱為子封裝。</span><span class="sxs-lookup"><span data-stu-id="dd30e-118">A package that runs other packages is generally referred to as the parent package, and the packages that a parent workflow runs are called child packages.</span></span>  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="dd30e-119">包含執行工作流程作業的工作，例如執行可執行檔和批次檔。</span><span class="sxs-lookup"><span data-stu-id="dd30e-119">includes tasks that perform workflow operations, such as executing executables and batch files.</span></span> <span data-ttu-id="dd30e-120">如需詳細資訊，請參閱＜ [執行處理工作](execute-process-task.md)＞。</span><span class="sxs-lookup"><span data-stu-id="dd30e-120">For more information, see [Execute Process Task](execute-process-task.md).</span></span>  
  
## <a name="running-packages"></a><span data-ttu-id="dd30e-121">執行封裝</span><span class="sxs-lookup"><span data-stu-id="dd30e-121">Running Packages</span></span>  
 <span data-ttu-id="dd30e-122">「執行封裝」工作可以執行包含父封裝之相同專案中所含的子封裝。</span><span class="sxs-lookup"><span data-stu-id="dd30e-122">The Execute Package task can run child packages that are contained in the same project that contains the parent package.</span></span> <span data-ttu-id="dd30e-123">您可以透過將 **[ReferenceType]** 屬性設定為 **[專案參考]** ，然後設定 **[PackageNameFromProjectReference]** 屬性，以便從專案中選取子封裝。</span><span class="sxs-lookup"><span data-stu-id="dd30e-123">You select a child package from the project by setting the **ReferenceType** property to **Project Reference**, and then setting the **PackageNameFromProjectReference** property.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dd30e-124">[ReferenceType]  選項是唯讀的，如果尚未將包含封裝的專案轉換為專案部署模型，則該選項設為 [外部參考]  。</span><span class="sxs-lookup"><span data-stu-id="dd30e-124">The **ReferenceType** option is ready-only and set to **External Reference** if the project that contains the package has not been converted to the project deployment model.</span></span> <span data-ttu-id="dd30e-125">如需轉換的詳細資訊，請參閱 [將專案部署至 Integration Services 伺服器](../deploy-projects-to-integration-services-server.md)。</span><span class="sxs-lookup"><span data-stu-id="dd30e-125">For more information about conversion, see [Deploy Projects to Integration Services Server](../deploy-projects-to-integration-services-server.md).</span></span>  
  
 <span data-ttu-id="dd30e-126">「執行封裝」工作也可執行儲存在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb 資料庫中的封裝，以及儲存在檔案系統中的封裝。</span><span class="sxs-lookup"><span data-stu-id="dd30e-126">The Execute Package task can also run packages stored in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] msdb database and packages stored in the file system.</span></span> <span data-ttu-id="dd30e-127">此工作使用 OLE DB 連接管理員連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，或使用檔案連接管理員存取檔案系統。</span><span class="sxs-lookup"><span data-stu-id="dd30e-127">The task uses an OLE DB connection manager to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or a File connection manager to access the file system.</span></span> <span data-ttu-id="dd30e-128">如需詳細資訊，請參閱＜ [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md) ＞和＜ [般檔案連線管理員](../connection-manager/flat-file-connection-manager.md)＞。</span><span class="sxs-lookup"><span data-stu-id="dd30e-128">For more information, see [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md) and [Flat File Connection Manager](../connection-manager/flat-file-connection-manager.md).</span></span>  
  
 <span data-ttu-id="dd30e-129">「執行封裝」工作也可執行資料庫維護計畫，讓您管理相同 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 方案中的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝和資料庫維護計畫。</span><span class="sxs-lookup"><span data-stu-id="dd30e-129">The Execute Package task can also run a database maintenance plan, which lets you manage both [!INCLUDE[ssIS](../../includes/ssis-md.md)] packages and database maintenance plans in the same [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] solution.</span></span> <span data-ttu-id="dd30e-130">資料庫維護計畫與 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 封裝類似，不過計畫只能包含資料庫維護工作，而且一律儲存在 msdb 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="dd30e-130">A database maintenance plan is similar to an [!INCLUDE[ssIS](../../includes/ssis-md.md)] package, but a plan can include only database maintenance tasks, and it is always stored in the msdb database.</span></span>  
  
 <span data-ttu-id="dd30e-131">如果您選擇儲存在檔案系統中的封裝，就必須提供封裝的名稱與位置。</span><span class="sxs-lookup"><span data-stu-id="dd30e-131">If you choose a package stored in the file system, you must provide the name and location of the package.</span></span> <span data-ttu-id="dd30e-132">封裝可存在於檔案系統中的任何位置，不必與父封裝位在相同資料夾中。</span><span class="sxs-lookup"><span data-stu-id="dd30e-132">The package can reside anywhere in the file system; it does not have to be in the same folder as the parent package.</span></span>  
  
 <span data-ttu-id="dd30e-133">子封裝可在父封裝的處理序中執行，也可在其自己的處理序中執行。</span><span class="sxs-lookup"><span data-stu-id="dd30e-133">The child package can be run in the process of the parent package, or it can be run in its own process.</span></span> <span data-ttu-id="dd30e-134">在其自己的處理序中執行子封裝需要更多記憶體，但是提供更大彈性。</span><span class="sxs-lookup"><span data-stu-id="dd30e-134">Running the child package in its own process requires more memory, but it provides more flexibility.</span></span> <span data-ttu-id="dd30e-135">例如，如果子處理序失敗，父處理序可繼續執行。</span><span class="sxs-lookup"><span data-stu-id="dd30e-135">For example, if the child process fails, the parent process can continue to run.</span></span>  
  
 <span data-ttu-id="dd30e-136">或者，有時您可能希望父封裝和子封裝當作一個單位一起失敗，或是不要產生其他處理序的額外負擔。</span><span class="sxs-lookup"><span data-stu-id="dd30e-136">Alternatively, sometimes you want the parent and child packages to fail together as one unit, or you might not want to incur the additional overhead of another process.</span></span> <span data-ttu-id="dd30e-137">例如，如果子處理序失敗，而父封裝處理序中的後續處理取決於子處理序的成功，則子封裝應該在父封裝的處理序中執行。</span><span class="sxs-lookup"><span data-stu-id="dd30e-137">For example, if a child process fails and subsequent processing in the parent process of the package depends on success of the child process, the child package should run in the process of the parent package.</span></span>  
  
 <span data-ttu-id="dd30e-138">根據預設，「執行封裝」工作的 ExecuteOutOfProcess 屬性會設定為 `False` ，而且子封裝會在與父封裝相同的進程中執行。</span><span class="sxs-lookup"><span data-stu-id="dd30e-138">By default, the ExecuteOutOfProcess property of the Execute Package task is set to `False`, and the child package runs in the same process as the parent package.</span></span> <span data-ttu-id="dd30e-139">如果您將此屬性設定為 `True`，子封裝就會在不同的處理序中執行。</span><span class="sxs-lookup"><span data-stu-id="dd30e-139">If you set this property to `True`, the child package runs in a separate process.</span></span> <span data-ttu-id="dd30e-140">這可能會降低子封裝的啟動速度。</span><span class="sxs-lookup"><span data-stu-id="dd30e-140">This may slow down the launching of the child package.</span></span> <span data-ttu-id="dd30e-141">此外，如果您將此屬性設定為 `True`，則無法在僅限工具安裝中偵錯封裝。</span><span class="sxs-lookup"><span data-stu-id="dd30e-141">In addition, if you set the property to `True`, you cannot debug the package in a tools-only install.</span></span> <span data-ttu-id="dd30e-142">您必須安裝 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="dd30e-142">You must install [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="dd30e-143">如需詳細資訊，請參閱 [安裝 Integration Services](../install-windows/install-integration-services.md)。</span><span class="sxs-lookup"><span data-stu-id="dd30e-143">For more information, see [Install Integration Services](../install-windows/install-integration-services.md)</span></span>  
  
## <a name="extending-transactions"></a><span data-ttu-id="dd30e-144">延伸交易</span><span class="sxs-lookup"><span data-stu-id="dd30e-144">Extending Transactions</span></span>  
 <span data-ttu-id="dd30e-145">父封裝使用的交易可延伸至子封裝；因此，這兩種封裝執行的工作都能認可或回復。</span><span class="sxs-lookup"><span data-stu-id="dd30e-145">The transaction that the parent package uses can extend to the child package; therefore, the work both packages perform can be committed or rolled back.</span></span> <span data-ttu-id="dd30e-146">例如，根據子封裝執行的資料庫插入，可以認可或回復父封裝所執行的資料庫插入，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="dd30e-146">For example, the database inserts that the parent package performs can be committed or rolled back, depending on the database inserts that the child package performs, and vice versa.</span></span> <span data-ttu-id="dd30e-147">如需詳細資訊，請參閱＜ [繼承的事務](../inherited-transactions.md)＞。</span><span class="sxs-lookup"><span data-stu-id="dd30e-147">For more information, see [Inherited Transactions](../inherited-transactions.md).</span></span>  
  
## <a name="propagating-logging-details"></a><span data-ttu-id="dd30e-148">傳播記錄詳細資料</span><span class="sxs-lookup"><span data-stu-id="dd30e-148">Propagating Logging Details</span></span>  
 <span data-ttu-id="dd30e-149">「執行封裝」工作執行的子封裝不一定會設定為使用記錄，但是子封裝永遠會將記錄的詳細資料轉送給父封裝。</span><span class="sxs-lookup"><span data-stu-id="dd30e-149">The child package that the Execute Package task runs may or may not be configured to use logging, but the child package will always forward the log details to the parent package.</span></span> <span data-ttu-id="dd30e-150">如果「執行封裝」工作設定為使用記錄，則此工作會記錄來自子封裝的記錄詳細資料。</span><span class="sxs-lookup"><span data-stu-id="dd30e-150">If the Execute Package task is configured to use logging, the task logs the log details from the child package.</span></span> <span data-ttu-id="dd30e-151">如需詳細資訊，請參閱 [集成服務 &#40;SSIS&#41; 記錄](../performance/integration-services-ssis-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="dd30e-151">For more information, see [Integration Services &#40;SSIS&#41; Logging](../performance/integration-services-ssis-logging.md).</span></span>  
  
## <a name="passing-values-to-child-packages"></a><span data-ttu-id="dd30e-152">將值傳遞給子封裝</span><span class="sxs-lookup"><span data-stu-id="dd30e-152">Passing Values to Child Packages</span></span>  
 <span data-ttu-id="dd30e-153">子封裝通常使用由另一個呼叫它的封裝傳遞給它的值，該封裝一般是其父封裝。</span><span class="sxs-lookup"><span data-stu-id="dd30e-153">Frequently a child package uses values passed to it by another package that calls it, ordinarily its parent package.</span></span> <span data-ttu-id="dd30e-154">使用來自父封裝的值在下列類似狀況中很有用：</span><span class="sxs-lookup"><span data-stu-id="dd30e-154">Using values from a parent package is useful in scenarios such as the following:</span></span>  
  
-   <span data-ttu-id="dd30e-155">將較大工作流程的各個部分指派給不同的封裝。</span><span class="sxs-lookup"><span data-stu-id="dd30e-155">Parts of a larger workflow are assigned to different packages.</span></span> <span data-ttu-id="dd30e-156">例如，一個封裝每晚下載資料、摘要資料、指派摘要資料值給變數，然後將值傳遞給另一個封裝進行資料的額外處理。</span><span class="sxs-lookup"><span data-stu-id="dd30e-156">For example, one package downloads data on a nightly basis, summarizes the data, assigns summary data values to variables, and then passes the values to another package for additional processing of the data.</span></span>  
  
-   <span data-ttu-id="dd30e-157">父封裝會動態協調子封裝中的工作。</span><span class="sxs-lookup"><span data-stu-id="dd30e-157">The parent package dynamically coordinates tasks in a child package.</span></span> <span data-ttu-id="dd30e-158">例如，父封裝決定本月的天數，並將該數字指派給變數，然後由子封裝執行該次數的工作。</span><span class="sxs-lookup"><span data-stu-id="dd30e-158">For example, the parent package determines the number of days in a current month and assigns the number to a variable, and the child package performs a task that number of times.</span></span>  
  
-   <span data-ttu-id="dd30e-159">子封裝需要存取由父封裝動態衍生的資料。</span><span class="sxs-lookup"><span data-stu-id="dd30e-159">A child package requires access to data that is dynamically derived by the parent package.</span></span> <span data-ttu-id="dd30e-160">例如，父封裝會從資料表擷取資料並將資料列集載入變數，子封裝則會對該資料執行其他作業。</span><span class="sxs-lookup"><span data-stu-id="dd30e-160">For example, the parent package extracts data from a table and loads the rowset into a variable, and the child package performs additional operations on the data.</span></span>  
  
 <span data-ttu-id="dd30e-161">您可以使用下列方法，將值傳遞至子封裝：</span><span class="sxs-lookup"><span data-stu-id="dd30e-161">You can use the following methods to pass values to a child package:</span></span>  
  
-   <span data-ttu-id="dd30e-162">**封裝組態**</span><span class="sxs-lookup"><span data-stu-id="dd30e-162">**Package Configurations**</span></span>  
  
     [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="dd30e-163">提供「父封裝變數」組態的組態類型，可將值從父封裝傳遞至子封裝。</span><span class="sxs-lookup"><span data-stu-id="dd30e-163">provides a configuration type, the Parent Package Variable configuration, for passing values from parent to child packages.</span></span> <span data-ttu-id="dd30e-164">組態建立在子封裝上，並使用父封裝中的變數。</span><span class="sxs-lookup"><span data-stu-id="dd30e-164">The configuration is built on the child package and uses a variable in the parent package.</span></span> <span data-ttu-id="dd30e-165">然後，組態會對應至子封裝中的變數，或是子封裝中的物件屬性。</span><span class="sxs-lookup"><span data-stu-id="dd30e-165">The configuration is mapped to a variable in the child package, or to the property of an object in the child package.</span></span> <span data-ttu-id="dd30e-166">變數也可用在指令碼工作或指令碼元件所用的指令碼中。</span><span class="sxs-lookup"><span data-stu-id="dd30e-166">The variable can also be used in the scripts used by the Script task or Script component.</span></span>  
  
-   <span data-ttu-id="dd30e-167">**參數**</span><span class="sxs-lookup"><span data-stu-id="dd30e-167">**Parameters**</span></span>  
  
     <span data-ttu-id="dd30e-168">您可以設定「執行封裝」工作將父封裝變數或參數 (或專案參數) 對應到子封裝參數。</span><span class="sxs-lookup"><span data-stu-id="dd30e-168">You can configure the Execute Package Task to map parent package variables or parameters, or project parameters, to child package parameters.</span></span> <span data-ttu-id="dd30e-169">專案必須使用專案部署模型，而且子封裝必須包含在包含父封裝的相同專案中。</span><span class="sxs-lookup"><span data-stu-id="dd30e-169">The project must use the project deployment model and the child package must be contained in the same project that contains the parent package.</span></span> <span data-ttu-id="dd30e-170">如需詳細資訊，請參閱＜ [執行封裝工作編輯器](../execute-package-task-editor.md)＞。</span><span class="sxs-lookup"><span data-stu-id="dd30e-170">For more information, see [Execute Package Task Editor](../execute-package-task-editor.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="dd30e-171">如果子封裝參數不區分大小寫，但對應到區分大小寫的父參數，則子封裝將無法執行。</span><span class="sxs-lookup"><span data-stu-id="dd30e-171">If the child package parameter is not sensitive and is mapped to a parent parameter that is sensitive, the child package will fail to run.</span></span>  
    >   
    >  <span data-ttu-id="dd30e-172">支援下列對應條件：</span><span class="sxs-lookup"><span data-stu-id="dd30e-172">The following mapping conditions are supported:</span></span>  
    >   
    >  -   <span data-ttu-id="dd30e-173">區分大小寫，子封裝參數對應到區分大小寫的父參數</span><span class="sxs-lookup"><span data-stu-id="dd30e-173">Sensitive, child package parameter is mapped to a sensitive, parent parameter</span></span>  
    > -   <span data-ttu-id="dd30e-174">區分大小寫，子封裝參數對應到不區分大小寫的父參數</span><span class="sxs-lookup"><span data-stu-id="dd30e-174">Sensitive, child package parameter is mapped to a non-sensitive, parent parameter</span></span>  
    > -   <span data-ttu-id="dd30e-175">不區分大小寫，子封裝參數對應到不區分大小寫的父參數</span><span class="sxs-lookup"><span data-stu-id="dd30e-175">Non-sensitive, child package parameter is mapped to a non-sensitive, parent parameter</span></span>  
  
 <span data-ttu-id="dd30e-176">父封裝變數可在「執行封裝」工作的範圍內定義，或是在諸如封裝的父容器中定義。</span><span class="sxs-lookup"><span data-stu-id="dd30e-176">The parent package variable can be defined in the scope of the Execute Package task or in a parent container such as the package.</span></span> <span data-ttu-id="dd30e-177">如果有多個名稱相同的變數可用，則會使用在「執行封裝」工作範圍內所定義的變數，或是最接近工作範圍的變數。</span><span class="sxs-lookup"><span data-stu-id="dd30e-177">If multiple variables with the same name are available, the variable defined in the scope of the Execute Package task is used, or the variable that is closest in scope to the task.</span></span>  
  
 <span data-ttu-id="dd30e-178">如需詳細資訊，請參閱 [在子封裝中使用變數和參數的值](../use-the-values-of-variables-and-parameters-in-a-child-package.md)。</span><span class="sxs-lookup"><span data-stu-id="dd30e-178">For more information, see [Use the Values of Variables and Parameters in a Child Package](../use-the-values-of-variables-and-parameters-in-a-child-package.md).</span></span>  
  
### <a name="accessing-parent-package-variables"></a><span data-ttu-id="dd30e-179">存取父封裝變數</span><span class="sxs-lookup"><span data-stu-id="dd30e-179">Accessing Parent Package Variables</span></span>  
 <span data-ttu-id="dd30e-180">子封裝可藉由使用指令碼工作存取父封裝變數。</span><span class="sxs-lookup"><span data-stu-id="dd30e-180">Child packages can access parent package variables by using the Script task.</span></span> <span data-ttu-id="dd30e-181">當你在 [指令碼工作編輯器]  的 [指令碼]  頁面上輸入父封裝變數的名稱時，變數名稱中請勿加上 **User:** 。</span><span class="sxs-lookup"><span data-stu-id="dd30e-181">When you enter the name of the parent package variable on the **Script** page in the **Script Task Editor**, don't include **User:** in the variable name.</span></span> <span data-ttu-id="dd30e-182">否則，在您執行父封裝時子封裝會找不到該變數。</span><span class="sxs-lookup"><span data-stu-id="dd30e-182">Otherwise, the child package doesn't locate the variable when you run the parent package.</span></span> <span data-ttu-id="dd30e-183">如需使用腳本工作存取父封裝變數的詳細資訊，請參閱此 blog 專案[： SSIS .. 存取父封裝中的變數](https://andyleonard.blog/2015/08/ssis-design-pattern-access-parent-variables-from-a-child-package-in-the-ssis-catalog/)。</span><span class="sxs-lookup"><span data-stu-id="dd30e-183">For more information about using the Script task to access parent package variables, see this blog entry, [SSIS: Accessing variables in a parent package](https://andyleonard.blog/2015/08/ssis-design-pattern-access-parent-variables-from-a-child-package-in-the-ssis-catalog/).</span></span>  
  
## <a name="configuring-the-execute-package-task"></a><span data-ttu-id="dd30e-184">設定執行封裝工作</span><span class="sxs-lookup"><span data-stu-id="dd30e-184">Configuring the Execute Package Task</span></span>  
 <span data-ttu-id="dd30e-185">您可以透過 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="dd30e-185">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="dd30e-186">如需有關可以在「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」中設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="dd30e-186">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="dd30e-187">執行封裝工作編輯器</span><span class="sxs-lookup"><span data-stu-id="dd30e-187">Execute Package Task Editor</span></span>](../execute-package-task-editor.md)  
  
-   [<span data-ttu-id="dd30e-188">運算式頁面</span><span class="sxs-lookup"><span data-stu-id="dd30e-188">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="dd30e-189">如需有關如何在「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」中設定這些屬性的詳細資訊，請按下列主題：</span><span class="sxs-lookup"><span data-stu-id="dd30e-189">For more information about how to set these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="dd30e-190">設定工作或容器的屬性</span><span class="sxs-lookup"><span data-stu-id="dd30e-190">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="related-content"></a><span data-ttu-id="dd30e-191">相關內容</span><span class="sxs-lookup"><span data-stu-id="dd30e-191">Related Content</span></span>  

<span data-ttu-id="dd30e-192">Blog 專案（SSIS）：在 andyleonard 上[存取父封裝中的變數](https://andyleonard.blog/2015/08/ssis-design-pattern-access-parent-variables-from-a-child-package-in-the-ssis-catalog/)。</span><span class="sxs-lookup"><span data-stu-id="dd30e-192">Blog entry, [SSIS: Accessing variables in a parent package](https://andyleonard.blog/2015/08/ssis-design-pattern-access-parent-variables-from-a-child-package-in-the-ssis-catalog/), on andyleonard.blog.</span></span> 
  
  