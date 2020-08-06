---
title: 使用物件總管管理物件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.SQLSERVEROBJECTEXPLORER.DHELP
helpviewer_keywords:
- Object Explorer F1 Help
- OE F1 Help
- OE Help
ms.assetid: e60367a7-3fdd-40b8-82bb-9e819d78de5a
author: stevestein
ms.author: sstein
ms.openlocfilehash: dc510c40cf98a1f08660bcafda8854281b70d9f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708901"
---
# <a name="manage-objects-by-using-object-explorer"></a><span data-ttu-id="df345-102">使用物件總管管理物件</span><span class="sxs-lookup"><span data-stu-id="df345-102">Manage Objects by Using Object Explorer</span></span>
  <span data-ttu-id="df345-103">您可以使用物件總管管理像是資料庫、資料表和預存程序等物件。</span><span class="sxs-lookup"><span data-stu-id="df345-103">You can use Object Explorer to manage objects such as databases, tables and stored procedures.</span></span>  
  
## <a name="viewing-objects-in-object-explorer"></a><span data-ttu-id="df345-104">在物件總管中檢視物件</span><span class="sxs-lookup"><span data-stu-id="df345-104">Viewing Objects in Object Explorer</span></span>  
 <span data-ttu-id="df345-105">物件總管會利用樹狀結構，將資訊分組成資料夾。</span><span class="sxs-lookup"><span data-stu-id="df345-105">Object Explorer uses a tree structure to group information into folders.</span></span> <span data-ttu-id="df345-106">若要展開資料夾，請按一下加號 (+)，或按兩下資料夾。</span><span class="sxs-lookup"><span data-stu-id="df345-106">To expand folders, click the plus sign (+) or double-click the folder.</span></span> <span data-ttu-id="df345-107">展開資料夾來顯示更詳細的資訊。</span><span class="sxs-lookup"><span data-stu-id="df345-107">Expand folders to show more detailed information.</span></span> <span data-ttu-id="df345-108">以滑鼠右鍵按一下資料夾或物件來執行一般工作。</span><span class="sxs-lookup"><span data-stu-id="df345-108">Right-click folders or objects to perform common tasks.</span></span> <span data-ttu-id="df345-109">請按兩下物件來執行最平常的工作。</span><span class="sxs-lookup"><span data-stu-id="df345-109">Double-click objects to perform the most common task.</span></span>  
  
 <span data-ttu-id="df345-110">您第一次展開資料夾時，物件總管會查詢伺服器來找出擴展樹狀結構的資訊。</span><span class="sxs-lookup"><span data-stu-id="df345-110">The first time you expand a folder, Object Explorer will query the server for information to populate the tree.</span></span> <span data-ttu-id="df345-111">當擴展樹狀結構時，您可以執行其他功能。</span><span class="sxs-lookup"><span data-stu-id="df345-111">You can perform other functions while the tree is populating.</span></span> <span data-ttu-id="df345-112">當物件總管在擴展樹狀結構時，您可以按一下 [停止]  來中止這個程序。</span><span class="sxs-lookup"><span data-stu-id="df345-112">While Object Explorer is populating the tree, you can click **Stop** to halt the process.</span></span> <span data-ttu-id="df345-113">進一步的動作 (如篩選清單) 只會作用於資料夾擴展的部分，除非您重新整理資料夾來重新開始擴展。</span><span class="sxs-lookup"><span data-stu-id="df345-113">Further actions, such as filtering the list, will only act upon the portion of the folder that was populated, unless you refresh the folder to start population again.</span></span>  
  
 <span data-ttu-id="df345-114">為了在有許多物件時能夠節省資源，[物件總管] 樹狀結構中的資料夾不會自動重新整理他們的內容清單。</span><span class="sxs-lookup"><span data-stu-id="df345-114">To conserve resources when there are many objects, the folders in the Object Explorer tree do not automatically refresh their list of contents.</span></span> <span data-ttu-id="df345-115">若要重新整理資料夾內的物件清單，請以滑鼠右鍵按一下資料夾，再按一下 [重新整理]  。</span><span class="sxs-lookup"><span data-stu-id="df345-115">To refresh the list of objects within a folder, right-click the folder, and then click **Refresh**.</span></span>  
  
 <span data-ttu-id="df345-116">[物件總管] 只能顯示最多 65,536 個物件。</span><span class="sxs-lookup"><span data-stu-id="df345-116">Object Explorer can only display up to 65,536 objects.</span></span> <span data-ttu-id="df345-117">超出 65,536 個現有的物件之後，您便無法在 [物件總管] 樹狀檢視中，捲動瀏覽其他物件。</span><span class="sxs-lookup"><span data-stu-id="df345-117">After you have exceeded 65,536 visible objects, you cannot scroll through additional objects in the Object Explorer tree view.</span></span> <span data-ttu-id="df345-118">在 [物件總管] 中檢視其他物件，請關閉未使用的節點，或套用篩選來減少物件數目。</span><span class="sxs-lookup"><span data-stu-id="df345-118">To view additional objects in Object Explorer, close nodes that you are not using or apply filtering to reduce the number of objects.</span></span>  
  
## <a name="filtering-the-list-of-objects-in-object-explorer"></a><span data-ttu-id="df345-119">在 [物件總管] 中篩選物件清單</span><span class="sxs-lookup"><span data-stu-id="df345-119">Filtering the List of Objects in Object Explorer</span></span>  
 <span data-ttu-id="df345-120">當資料夾包含大量物件時，可能很不容易找到您要找的物件。</span><span class="sxs-lookup"><span data-stu-id="df345-120">When a folder contains a large number of objects, it may be difficult to find the object you are looking for.</span></span> <span data-ttu-id="df345-121">在這種情況下，請利用 [物件總管] 的篩選功能來縮減清單大小。</span><span class="sxs-lookup"><span data-stu-id="df345-121">In such cases, use the filter feature of Object Explorer to reduce the list to a smaller size.</span></span> <span data-ttu-id="df345-122">例如，您可能會想在包含數百個物件的清單中，尋找特定資料庫使用者或最近建立的資料表。</span><span class="sxs-lookup"><span data-stu-id="df345-122">For example, you may want to find a specific database user or the most recently created table in lists that contain hundreds of objects.</span></span> <span data-ttu-id="df345-123">請按一下您要篩選的資料夾，再按一下篩選按鈕來開啟 [篩選設定]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="df345-123">Click on the folder that you want to filter, and then click the filter button to open the **Filter Settings** dialog box.</span></span> <span data-ttu-id="df345-124">您可以依名稱、建立日期來篩選清單，有時也可以利用結構描述來篩選，且可以提供 [開頭為]  、[包含]  和 [介於]  之類的其他篩選運算子。</span><span class="sxs-lookup"><span data-stu-id="df345-124">You can filter the list by name, create date, and sometimes schema, and provide additional filtering operators like **Starts with**, **Contains**, and **Between**.</span></span>  
  
## <a name="multi-select"></a><span data-ttu-id="df345-125">複選</span><span class="sxs-lookup"><span data-stu-id="df345-125">Multi-select</span></span>  
 <span data-ttu-id="df345-126">在 [物件總管] 中，每次只能選取一個物件。</span><span class="sxs-lookup"><span data-stu-id="df345-126">Only one object can be selected at a time in Object Explorer.</span></span> <span data-ttu-id="df345-127">若要選取多個項目，請按 **F7** 開啟 [物件總管詳細資料]  頁面。</span><span class="sxs-lookup"><span data-stu-id="df345-127">To select multiple items, press **F7** to open the **Object Explorer Details Page**.</span></span> <span data-ttu-id="df345-128">[物件總管詳細資料]  頁面支援多重選取。</span><span class="sxs-lookup"><span data-stu-id="df345-128">The **Object Explorer Details Page** supports multi-select.</span></span>  
  
## <a name="register-a-server-from-object-explorer"></a><span data-ttu-id="df345-129">從物件總管註冊伺服器</span><span class="sxs-lookup"><span data-stu-id="df345-129">Register a Server from Object Explorer</span></span>  
 <span data-ttu-id="df345-130">當連接到伺服器時，您便很容易註冊伺服器，供未來使用。</span><span class="sxs-lookup"><span data-stu-id="df345-130">When connected to a server, you can easily register the server for future use.</span></span> <span data-ttu-id="df345-131">在物件總管中，以滑鼠右鍵按一下伺服器名稱，然後按一下 [註冊]  。</span><span class="sxs-lookup"><span data-stu-id="df345-131">In Object Explorer, right-click the server name, and then click **Register**.</span></span> <span data-ttu-id="df345-132">在 [已註冊的伺服器]  對話方塊中，指定伺服器在伺服器群組樹狀結構中的放置位置。</span><span class="sxs-lookup"><span data-stu-id="df345-132">In the **Register Server** dialog box, specify where in the server group tree you want to place the server.</span></span> <span data-ttu-id="df345-133">在 [伺服器名稱]  方塊中，您可以將伺服器名稱改成更有意義的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="df345-133">In the **Server name** box, you can replace the server name with a more meaningful server name.</span></span> <span data-ttu-id="df345-134">例如，您可以利用類似 " **Accounts Payable** " 等更有意義的名稱來註冊**APSQL02**伺服器。</span><span class="sxs-lookup"><span data-stu-id="df345-134">For example, you could register server **APSQL02** with a more meaningful name such as "**Accounts Payable**".</span></span>  
  
## <a name="performing-actions-on-object-explorer-nodes"></a><span data-ttu-id="df345-135">在物件總管節點上執行動作</span><span class="sxs-lookup"><span data-stu-id="df345-135">Performing Actions on Object Explorer Nodes</span></span>  
 <span data-ttu-id="df345-136">以滑鼠右鍵按一下表示物件的物件總管節點，針對物件執行動作。</span><span class="sxs-lookup"><span data-stu-id="df345-136">You perform actions on objects by right clicking the Object Explorer node representing the object.</span></span> <span data-ttu-id="df345-137">每種物件類型都支援一組唯一的按右鍵動作。</span><span class="sxs-lookup"><span data-stu-id="df345-137">Each type of object supports a unique set of right-click actions.</span></span> <span data-ttu-id="df345-138">您可以使用按右鍵功能表執行的某些動作類型包括：</span><span class="sxs-lookup"><span data-stu-id="df345-138">Some of the types of actions you can perform by using the right-click menus include:</span></span>  
  
### <a name="open-a-connected-query-editor"></a><span data-ttu-id="df345-139">開啟連接的查詢編輯器</span><span class="sxs-lookup"><span data-stu-id="df345-139">Open a Connected Query Editor</span></span>  
 <span data-ttu-id="df345-140">當物件總管連接到伺服器時，您可以利用 [物件總管] 的連接設定來開啟新的 [程式碼編輯器] 視窗。</span><span class="sxs-lookup"><span data-stu-id="df345-140">When Object Explorer is connected to a server, you can open a new Code Editor window using the connection settings of Object Explorer.</span></span> <span data-ttu-id="df345-141">若要開啟新的 [程式碼編輯器] 視窗，請在物件總管中，以滑鼠右鍵按一下伺服器名稱，再按一下 [新增查詢]  。</span><span class="sxs-lookup"><span data-stu-id="df345-141">To open a new Code Editor window, right-click the server name in Object Explorer, and then click **New Query**.</span></span> <span data-ttu-id="df345-142">若要利用特定資料庫來開啟 [程式碼編輯器] 視窗，請以滑鼠右鍵按一下資料庫名稱，再按一下 [新增查詢]  。</span><span class="sxs-lookup"><span data-stu-id="df345-142">To open a Code Editor window using a particular database, right-click the database name, and then click **New Query**.</span></span> <span data-ttu-id="df345-143">當開啟 Analysis Services 伺服器的新查詢時，您可以選取 DMX、MDX 或 XMLA 查詢。</span><span class="sxs-lookup"><span data-stu-id="df345-143">When opening a new query for an Analysis Services server, you can select DMX, MDX, or XMLA queries.</span></span>  
  
### <a name="start-powershell"></a><span data-ttu-id="df345-144">啟動 PowerShell</span><span class="sxs-lookup"><span data-stu-id="df345-144">Start PowerShell</span></span>  
 <span data-ttu-id="df345-145">您可以啟動 PowerShell 工作階段，其方式是以滑鼠右鍵按一下物件總管樹狀結構中的大多數資料夾和物件，然後選取 [啟動 PowerShell]  。</span><span class="sxs-lookup"><span data-stu-id="df345-145">You can start a PowerShell session by right-clicking most folders and objects in the Object Explorer tree and selecting **Start PowerShell**.</span></span> <span data-ttu-id="df345-146">這樣會啟動 PowerShell 工作階段，此工作階段已啟用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell 支援，而且路徑會設定為您在 [物件總管] 中以滑鼠右鍵按一下的物件。</span><span class="sxs-lookup"><span data-stu-id="df345-146">This starts a PowerShell session that has the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell support enabled, and the path set to the object you right-clicked in Object Explorer.</span></span> <span data-ttu-id="df345-147">然後您可以在互動式 PowerShell 環境中輸入 PowerShell 命令。</span><span class="sxs-lookup"><span data-stu-id="df345-147">You can then enter PowerShell commands in an interactive PowerShell environment.</span></span> <span data-ttu-id="df345-148">如需詳細資訊，請參閱 [SQL Server PowerShell](../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="df345-148">For more information, see [SQL Server PowerShell](../../powershell/sql-server-powershell.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df345-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df345-149">See Also</span></span>  
 <span data-ttu-id="df345-150">[物件總管](object-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="df345-150">[Object Explorer](object-explorer.md) </span></span>  
 <span data-ttu-id="df345-151">[開啟並設定物件總管](open-and-configure-object-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="df345-151">[Open and Configure Object Explorer](open-and-configure-object-explorer.md) </span></span>  
 <span data-ttu-id="df345-152">[從物件總管連接到實例](connect-to-an-instance-from-object-explorer.md) </span><span class="sxs-lookup"><span data-stu-id="df345-152">[Connect to an Instance From Object Explorer](connect-to-an-instance-from-object-explorer.md) </span></span>  
 <span data-ttu-id="df345-153">[物件總管詳細資料窗格](object-explorer-details-pane.md) </span><span class="sxs-lookup"><span data-stu-id="df345-153">[Object Explorer Details Pane](object-explorer-details-pane.md) </span></span>  
 [<span data-ttu-id="df345-154">Management Studio 中的自訂報表</span><span class="sxs-lookup"><span data-stu-id="df345-154">Custom Reports in Management Studio</span></span>](custom-reports-in-management-studio.md)  
  
  