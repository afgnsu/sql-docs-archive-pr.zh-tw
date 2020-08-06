---
title: DMX 查詢編輯器 (Analysis Services 資料採礦) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.startpage.dmx.f1
ms.assetid: 7ac877a1-0f29-46b9-9a51-73b02172bef1
author: minewiskan
ms.author: owend
ms.openlocfilehash: cc14281cebe3a8e5e401acb7b84367f1688ad0ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599257"
---
# <a name="dmx-query-editor-analysis-services---data-mining"></a><span data-ttu-id="7b71d-102">DMX 查詢編輯器 (Analysis Services - 資料採礦)</span><span class="sxs-lookup"><span data-stu-id="7b71d-102">DMX Query Editor (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="7b71d-103">使用 [DMX 查詢編輯器] 即可設計和執行以資料採礦延伸模組 (DMX) 語言撰寫的陳述式。</span><span class="sxs-lookup"><span data-stu-id="7b71d-103">Use the DMX Query Editor to design and execute statements written in the Data Mining Extensions (DMX) language.</span></span>  
  
## <a name="features"></a><span data-ttu-id="7b71d-104">特性</span><span class="sxs-lookup"><span data-stu-id="7b71d-104">Features</span></span>  
  
-   <span data-ttu-id="7b71d-105">在 [DMX 查詢編輯器] 的查詢編輯器窗格中鍵入指令碼。</span><span class="sxs-lookup"><span data-stu-id="7b71d-105">Type scripts in the query editor pane of DMX Query Editor.</span></span>  
  
-   <span data-ttu-id="7b71d-106">若要執行指令碼，請按 **F5**，或者在工具列或 **[查詢]** 功能表上按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="7b71d-106">To execute scripts press **F5**, or click **Execute** on the toolbar or on the **Query** menu.</span></span> <span data-ttu-id="7b71d-107">如果已選取部份程式碼，則僅執行該部份程式碼。</span><span class="sxs-lookup"><span data-stu-id="7b71d-107">If a portion of the code is selected, only that portion is executed.</span></span> <span data-ttu-id="7b71d-108">如果未選取程式碼，則會執行整個 DMX 查詢編輯器的內容。</span><span class="sxs-lookup"><span data-stu-id="7b71d-108">If no code is selected, the entire content of the DMX Query Editor is executed.</span></span>  
  
-   <span data-ttu-id="7b71d-109">在中繼資料窗格中，可以檢視 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫所包含的 Cube 和其他物件的中繼資料</span><span class="sxs-lookup"><span data-stu-id="7b71d-109">View metadata for cubes and other objects contained in an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database in the metadata pane</span></span>  
  
-   <span data-ttu-id="7b71d-110">如需 DMX 的語法說明，請在 [DMX 查詢編輯器] 中選取關鍵字，然後按一下 **F1**。</span><span class="sxs-lookup"><span data-stu-id="7b71d-110">For help with DMX syntax, select a keyword in DMX Query Editor, and then click **F1**.</span></span>  
  
-   <span data-ttu-id="7b71d-111">如需 DMX 語法的動態說明，請在 **[說明]** 功能表上，按一下 **[動態說明]** ，以開啟動態說明元件。</span><span class="sxs-lookup"><span data-stu-id="7b71d-111">For dynamic help with DMX syntax, on the **Help** menu, click **Dynamic Help** to open the Dynamic Help component.</span></span> <span data-ttu-id="7b71d-112">使用動態說明時，在查詢編輯器中鍵入關鍵字，說明主題就會顯示在 **[動態說明]** 視窗內。</span><span class="sxs-lookup"><span data-stu-id="7b71d-112">With Dynamic Help, help topics appear in the **Dynamic Help** window when keywords are typed in Query Editor.</span></span>  
  
## <a name="sql-server-analysis-services-editors-toolbar"></a><span data-ttu-id="7b71d-113">SQL Server Analysis Services 編輯器工具列</span><span class="sxs-lookup"><span data-stu-id="7b71d-113">SQL Server Analysis Services Editors Toolbar</span></span>  
 <span data-ttu-id="7b71d-114">當 [DMX 查詢編輯器] 開啟時，顯示的 **[SQL Server Analysis Services 編輯器]** 工具列中，會包含下表列出的按鈕。</span><span class="sxs-lookup"><span data-stu-id="7b71d-114">When DMX Query Editor is open, the **SQL Server Analysis Services Editors** toolbar appears with the buttons listed in the following table.</span></span>  
  
|<span data-ttu-id="7b71d-115">詞彙</span><span class="sxs-lookup"><span data-stu-id="7b71d-115">Term</span></span>|<span data-ttu-id="7b71d-116">定義</span><span class="sxs-lookup"><span data-stu-id="7b71d-116">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="7b71d-117">**[連接]**</span><span class="sxs-lookup"><span data-stu-id="7b71d-117">**Connect**</span></span>|<span data-ttu-id="7b71d-118">開啟 **[連接到伺服器]** 對話方塊，以建立與 Analysis Services 執行個體的連接。</span><span class="sxs-lookup"><span data-stu-id="7b71d-118">Opens the **Connect to Server** dialog box, to establish a connection to an Analysis Services instance.</span></span>|  
|<span data-ttu-id="7b71d-119">**中斷連線**</span><span class="sxs-lookup"><span data-stu-id="7b71d-119">**Disconnect**</span></span>|<span data-ttu-id="7b71d-120">中斷 DMX 查詢編輯器與 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體的連接。</span><span class="sxs-lookup"><span data-stu-id="7b71d-120">Disconnects the DMX Query Editor from an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.</span></span>|  
|<span data-ttu-id="7b71d-121">**變更連接**</span><span class="sxs-lookup"><span data-stu-id="7b71d-121">**Change Connection**</span></span>|<span data-ttu-id="7b71d-122">開啟 **[連接到伺服器]** 對話方塊，以建立另一個 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體的連接。</span><span class="sxs-lookup"><span data-stu-id="7b71d-122">Opens the **Connect to Server** dialog box, to establish a connection to a different [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.</span></span>|  
|<span data-ttu-id="7b71d-123">**使用目前的連接新增查詢**</span><span class="sxs-lookup"><span data-stu-id="7b71d-123">**New Query with Current Connection**</span></span>|<span data-ttu-id="7b71d-124">開啟新 DMX 查詢編輯器視窗，使用目前 DMX 查詢編輯器視窗的連接資訊。</span><span class="sxs-lookup"><span data-stu-id="7b71d-124">Opens a new DMX Query Editor window, using the connection information from the current DMX Query Editor window.</span></span>|  
|<span data-ttu-id="7b71d-125">**可用的資料庫**</span><span class="sxs-lookup"><span data-stu-id="7b71d-125">**Available Databases**</span></span>|<span data-ttu-id="7b71d-126">變更連接到同一執行個體的另一個 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="7b71d-126">Changes the connection to a different [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database on the same instance.</span></span>|  
|<span data-ttu-id="7b71d-127">**執行**</span><span class="sxs-lookup"><span data-stu-id="7b71d-127">**Execute**</span></span>|<span data-ttu-id="7b71d-128">執行選取的程式碼，如果未選取程式碼，此選項會執行 DMX 查詢編輯器中的所有程式碼。</span><span class="sxs-lookup"><span data-stu-id="7b71d-128">Executes the selected code, or if no code is selected, this option executes the entire code in the DMX Query Editor.</span></span>|  
|<span data-ttu-id="7b71d-129">**剖析**</span><span class="sxs-lookup"><span data-stu-id="7b71d-129">**Parse**</span></span>|<span data-ttu-id="7b71d-130">檢查所選取程式碼的語法。</span><span class="sxs-lookup"><span data-stu-id="7b71d-130">Checks the syntax of the selected code.</span></span> <span data-ttu-id="7b71d-131">如果未選取程式碼，此選項會檢查整個 DMX 查詢編輯器視窗的語法。</span><span class="sxs-lookup"><span data-stu-id="7b71d-131">If no code is selected, this option checks the syntax of the entire DMX Query Editor window.</span></span>|  
|<span data-ttu-id="7b71d-132">**取消執行查詢**</span><span class="sxs-lookup"><span data-stu-id="7b71d-132">**Cancel Executing Query**</span></span>|<span data-ttu-id="7b71d-133">將取消要求傳送到伺服器。</span><span class="sxs-lookup"><span data-stu-id="7b71d-133">Sends a cancellation request to the server.</span></span> <span data-ttu-id="7b71d-134">部份查詢無法立即取消，必須等候適當的取消條件。</span><span class="sxs-lookup"><span data-stu-id="7b71d-134">Some queries cannot be canceled immediately, but must wait for a suitable cancellation condition.</span></span> <span data-ttu-id="7b71d-135">取消之後，交易回復時可能會發生延遲。</span><span class="sxs-lookup"><span data-stu-id="7b71d-135">When canceled, delays may occur while transactions are rolled back.</span></span>|  
  
## <a name="dmx-query-editor-window"></a><span data-ttu-id="7b71d-136">DMX 查詢編輯器視窗</span><span class="sxs-lookup"><span data-stu-id="7b71d-136">DMX Query Editor Window</span></span>  
 <span data-ttu-id="7b71d-137">下表列出的選項，是可以在 DMX 查詢編輯器中使用的選項。</span><span class="sxs-lookup"><span data-stu-id="7b71d-137">The options listed in the following table are available in DMX Query Editor.</span></span>  
  
|<span data-ttu-id="7b71d-138">詞彙</span><span class="sxs-lookup"><span data-stu-id="7b71d-138">Term</span></span>|<span data-ttu-id="7b71d-139">定義</span><span class="sxs-lookup"><span data-stu-id="7b71d-139">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="7b71d-140">**查詢編輯器視窗**</span><span class="sxs-lookup"><span data-stu-id="7b71d-140">**Query editor window**</span></span>|<span data-ttu-id="7b71d-141">鍵入要由 DMX 查詢編輯器執行的 DMX 陳述式和指令碼。</span><span class="sxs-lookup"><span data-stu-id="7b71d-141">Type DMX statements and scripts to be executed by the DMX Query Editor.</span></span><br /><br /> <span data-ttu-id="7b71d-142">查詢編輯器的內容功能表提供下列選項：</span><span class="sxs-lookup"><span data-stu-id="7b71d-142">The context menu for the query editor provides the following options:</span></span><br /><br /> <span data-ttu-id="7b71d-143">**剪**下：將目前選取範圍複製到剪貼簿，並從 [查詢編輯器] 視窗中移除選取範圍。</span><span class="sxs-lookup"><span data-stu-id="7b71d-143">**Cut**: Copies the current selection to the clipboard and removes the selection from the query editor window.</span></span><br /><br /> <span data-ttu-id="7b71d-144">**複製**：將目前選取範圍複製到剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="7b71d-144">**Copy**: Copies the current selection to the clipboard.</span></span><br /><br /> <span data-ttu-id="7b71d-145">**貼**上：將剪貼簿的內容貼入目前的選取範圍。</span><span class="sxs-lookup"><span data-stu-id="7b71d-145">**Paste**: Pastes the contents of the clipboard to the current selection.</span></span><br /><br /> <span data-ttu-id="7b71d-146">**連接**：開啟 [連接到伺服器]\*\*\*\* 對話方塊，以建立與 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體的連接。</span><span class="sxs-lookup"><span data-stu-id="7b71d-146">**Connect**: Opens the **Connect to Server** dialog box, to establish a connection to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.</span></span><br /><br /> <span data-ttu-id="7b71d-147">**中斷連接**：中斷目前查詢編輯器與實例的連線 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="7b71d-147">**Disconnect**: Disconnects the current query editor from an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.</span></span><br /><br /> <span data-ttu-id="7b71d-148">**中斷所有查詢的連接**：中斷連接所有開啟的查詢編輯器。</span><span class="sxs-lookup"><span data-stu-id="7b71d-148">**Disconnect All Queries**: Disconnects all open query editors.</span></span><br /><br /> <span data-ttu-id="7b71d-149">**變更連接**：開啟 [**連接到伺服器**] 對話方塊，以建立與其他實例的連接 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="7b71d-149">**Change Connection**: Opens the **Connect to Server** dialog box, to establish a connection to a different [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.</span></span><br /><br /> <span data-ttu-id="7b71d-150">**在物件總管中開啟伺服器**：開啟 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 目前查詢編輯器連接的目標實例**物件總管**。</span><span class="sxs-lookup"><span data-stu-id="7b71d-150">**Open Server in Object Explorer**: Opens the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance to which the current query editor is connected in **Object Explorer**.</span></span><br /><br /> <span data-ttu-id="7b71d-151">**執行**：執行選取的程式碼，如果未選取任何程式碼，則執行目前查詢編輯器中的完整程式碼。</span><span class="sxs-lookup"><span data-stu-id="7b71d-151">**Execute**: Executes the selected code, or if no code is selected, executes the entire code in the current query editor.</span></span><br /><br /> <span data-ttu-id="7b71d-152">**屬性視窗**：在中，顯示目前查詢視窗的 [**屬性**] 視窗 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="7b71d-152">**Properties Window**: Displays the **Properties** window in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] for the current query window.</span></span><br /><br /> <span data-ttu-id="7b71d-153">**查詢選項**：顯示 [**查詢選項**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="7b71d-153">**Query Options**: Displays the **Query Options** dialog box.</span></span>|  
|<span data-ttu-id="7b71d-154">**中繼資料視窗**</span><span class="sxs-lookup"><span data-stu-id="7b71d-154">**Metadata window**</span></span>|<span data-ttu-id="7b71d-155">顯示目前連接之 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="7b71d-155">Displays metadata for the currently connected [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>|  
|<span data-ttu-id="7b71d-156">**Cube**</span><span class="sxs-lookup"><span data-stu-id="7b71d-156">**Cube**</span></span>|<span data-ttu-id="7b71d-157">選取目前連接之 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫內的 Cube，即可在 **[中繼資料]** 索引標籤中顯示與 Cube 相關聯的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="7b71d-157">Select a cube in the currently connected [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database to display the metadata associated with the cube in the **Metadata** tab.</span></span>|  
|<span data-ttu-id="7b71d-158">**中繼資料**</span><span class="sxs-lookup"><span data-stu-id="7b71d-158">**Metadata**</span></span>|<span data-ttu-id="7b71d-159">顯示在 **[Cube]** 中選取之 Cube 的中繼資料，包括量值群組與量值、關鍵效能指標、維度、階層、層級、成員及成員屬性。</span><span class="sxs-lookup"><span data-stu-id="7b71d-159">Displays the metadata for the cube selected in **Cube**, including measure groups and measures, key performance indicators, dimensions, hierarchies, levels, members, and member properties.</span></span> <span data-ttu-id="7b71d-160">若要擷取物件的完整索引鍵，請：</span><span class="sxs-lookup"><span data-stu-id="7b71d-160">To retrieve the fully qualified key of an object, either:</span></span><br /><br /> <span data-ttu-id="7b71d-161">從 **[中繼資料]** 索引標籤，將物件拖曳至查詢窗格。</span><span class="sxs-lookup"><span data-stu-id="7b71d-161">Drag the object from the **Metadata** tab to the query pane.</span></span><br /><br /> <span data-ttu-id="7b71d-162">或：</span><span class="sxs-lookup"><span data-stu-id="7b71d-162">Or:</span></span><br /><br /> <span data-ttu-id="7b71d-163">以滑鼠右鍵按一下物件，然後選取 **[複製]**，再以滑鼠右鍵按一下查詢窗格，然後選取 **[貼上]**。</span><span class="sxs-lookup"><span data-stu-id="7b71d-163">Right-click the object and select **Copy**, and then right-click the query pane and select **Paste**.</span></span>|  
|<span data-ttu-id="7b71d-164">**函式**</span><span class="sxs-lookup"><span data-stu-id="7b71d-164">**Functions**</span></span>|<span data-ttu-id="7b71d-165">顯示從 DMSCHEMA_MINING_FUNCTIONS 結構描述資料列集所擷取，且 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫可以使用之 DMX 函數的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="7b71d-165">Displays the metadata for DMX functions available to the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, as retrieved from the DMSCHEMA_MINING_FUNCTIONS schema rowset.</span></span><br /><br /> <span data-ttu-id="7b71d-166">若要擷取函數的語法，請：</span><span class="sxs-lookup"><span data-stu-id="7b71d-166">To retrieve the syntax of a function, either:</span></span><br /><br /> <span data-ttu-id="7b71d-167">從 **[函數]** 索引標籤，將物件拖曳至查詢窗格。</span><span class="sxs-lookup"><span data-stu-id="7b71d-167">Drag the object from the **Functions** tab to the query pane.</span></span><br /><br /> <span data-ttu-id="7b71d-168">或：</span><span class="sxs-lookup"><span data-stu-id="7b71d-168">Or:</span></span><br /><br /> <span data-ttu-id="7b71d-169">以滑鼠右鍵按一下函數，然後選取 **[複製]**，再以滑鼠右鍵按一下查詢窗格，然後選取 **[貼上]**。</span><span class="sxs-lookup"><span data-stu-id="7b71d-169">Right-click the function and select **Copy**, and then right-click the query pane and select **Paste**.</span></span>|  
|<span data-ttu-id="7b71d-170">**結果視窗**</span><span class="sxs-lookup"><span data-stu-id="7b71d-170">**Results window**</span></span>|<span data-ttu-id="7b71d-171">在方格中顯示 DMX 陳述式的結果。</span><span class="sxs-lookup"><span data-stu-id="7b71d-171">Displays the results of a DMX statement in a grid.</span></span>|  
|<span data-ttu-id="7b71d-172">**訊息視窗**</span><span class="sxs-lookup"><span data-stu-id="7b71d-172">**Messages window**</span></span>|<span data-ttu-id="7b71d-173">顯示有關 DMX 陳述式如何執行的資訊。</span><span class="sxs-lookup"><span data-stu-id="7b71d-173">Displays information about how a DMX statement executed.</span></span> <span data-ttu-id="7b71d-174">例如，這個視窗會顯示執行期間發生的錯誤，或執行之後擷取的資料格數目。</span><span class="sxs-lookup"><span data-stu-id="7b71d-174">For example, this window displays any errors encountered during execution or the number of cells retrieved after execution.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7b71d-175">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b71d-175">See Also</span></span>  
 <span data-ttu-id="7b71d-176">[Analysis Services 的設計工具和對話方塊 &#40;多維度資料&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="7b71d-176">[Analysis Services Designers and Dialog Boxes &#40;Multidimensional Data&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md) </span></span>  
 <span data-ttu-id="7b71d-177">[資料採礦延伸模組 &#40;DMX&#41; 參考](/sql/dmx/data-mining-extensions-dmx-reference) </span><span class="sxs-lookup"><span data-stu-id="7b71d-177">[Data Mining Extensions &#40;DMX&#41; Reference](/sql/dmx/data-mining-extensions-dmx-reference) </span></span>  
 <span data-ttu-id="7b71d-178">[MDX 查詢編輯器 &#40;Analysis Services-多維度資料&#41;](mdx-query-editor-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="7b71d-178">[MDX Query Editor &#40;Analysis Services - Multidimensional Data&#41;](mdx-query-editor-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="7b71d-179">[XMLA 查詢編輯器 &#40;Analysis Services-多維度資料&#41;](xmla-query-editor-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="7b71d-179">[XMLA Query Editor &#40;Analysis Services - Multidimensional Data&#41;](xmla-query-editor-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="7b71d-180">[查詢和文字編輯器 &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/query-and-text-editors-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="7b71d-180">[Query and Text Editors &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/query-and-text-editors-sql-server-management-studio.md) </span></span>  
 <span data-ttu-id="7b71d-181">[SQL Server Management Studio 鍵盤快速鍵](../ssms/sql-server-management-studio-keyboard-shortcuts.md) </span><span class="sxs-lookup"><span data-stu-id="7b71d-181">[SQL Server Management Studio Keyboard Shortcuts](../ssms/sql-server-management-studio-keyboard-shortcuts.md) </span></span>  
 <span data-ttu-id="7b71d-182">[自訂功能表和快速鍵](../ssms/customize-menus-and-shortcut-keys.md) </span><span class="sxs-lookup"><span data-stu-id="7b71d-182">[Customize Menus and Shortcut Keys](../ssms/customize-menus-and-shortcut-keys.md) </span></span>  
 [<span data-ttu-id="7b71d-183">查詢編輯器中的色彩編碼</span><span class="sxs-lookup"><span data-stu-id="7b71d-183">Color Coding in Query Editors</span></span>](../relational-databases/scripting/color-coding-in-query-editors.md)  
  
  