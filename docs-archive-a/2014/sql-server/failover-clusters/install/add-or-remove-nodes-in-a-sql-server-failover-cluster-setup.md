---
title: 在 SQL Server 容錯移轉叢集中加入或移除節點 (安裝程式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- adding nodes
- nodes [Faillover Clustering], removing
- nodes [Faillover Clustering], adding
- failover clustering [SQL Server], nodes
- deleting nodes
- cluster maintenance [SQL Server]
- removing nodes
ms.assetid: fe20dca9-a4c1-4d32-813d-42f1782dfdd3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 07405083c498db7e5bdb03bc67d2f03311ef7fb1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595595"
---
# <a name="add-or-remove-nodes-in-a-sql-server-failover-cluster-setup"></a><span data-ttu-id="8a100-102">在 SQL Server 容錯移轉叢集中加入或移除節點 (安裝程式)</span><span class="sxs-lookup"><span data-stu-id="8a100-102">Add or Remove Nodes in a SQL Server Failover Cluster (Setup)</span></span>
  <span data-ttu-id="8a100-103">您可以使用此程序來管理現有 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 容錯移轉叢集執行個體的節點。</span><span class="sxs-lookup"><span data-stu-id="8a100-103">Use this procedure to manage nodes to an existing [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster instance.</span></span>  
  
 <span data-ttu-id="8a100-104">若要更新或移除 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 容錯移轉叢集，您必須是本機管理員，而且擁有在容錯移轉叢集之所有節點上登入成為服務的權限。</span><span class="sxs-lookup"><span data-stu-id="8a100-104">To update or remove a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster, you must be a local administrator with permission to log in as a service on all nodes of the failover cluster.</span></span> <span data-ttu-id="8a100-105">如果是本機安裝，您必須以管理員身分執行安裝程式。</span><span class="sxs-lookup"><span data-stu-id="8a100-105">For local installations, you must run Setup as an administrator.</span></span> <span data-ttu-id="8a100-106">如果您是從遠端共用位置安裝 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]，則必須使用對遠端共用位置具有讀取和執行權限的網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="8a100-106">If you install [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] from a remote share, you must use a domain account that has read and execute permissions on the remote share.</span></span>  
  
 <span data-ttu-id="8a100-107">若要將節點加入至現有的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 容錯移轉叢集，您必須在要加入至 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 容錯移轉叢集執行個體的節點上執行 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="8a100-107">To add a node to an existing [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster, you must run [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Setup on the node that is to be added to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster instance.</span></span> <span data-ttu-id="8a100-108">請勿在使用中節點上執行安裝程式。</span><span class="sxs-lookup"><span data-stu-id="8a100-108">Do not run Setup on the active node.</span></span>  
  
 <span data-ttu-id="8a100-109">若要從現有的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 容錯移轉叢集中移除節點，您必須在即將從 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 容錯移轉叢集執行個體中移除的節點上執行 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="8a100-109">To remove a node from an existing [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster, you must run [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Setup on the node that is to be removed from the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster instance.</span></span>  
  
 <span data-ttu-id="8a100-110">若要檢視加入或移除節點的程序性步驟，請選取下列其中一個作業：</span><span class="sxs-lookup"><span data-stu-id="8a100-110">To view procedural steps to add or remove nodes, select one of the following operations:</span></span>  
  
-   [<span data-ttu-id="8a100-111">將節點加入現有的 SQL Server 容錯移轉叢集</span><span class="sxs-lookup"><span data-stu-id="8a100-111">Add a node to an existing SQL Server failover cluster</span></span>](#Add)  
  
-   [<span data-ttu-id="8a100-112">從現有的 SQL Server 容錯移轉叢集中移除節點</span><span class="sxs-lookup"><span data-stu-id="8a100-112">Remove a node from an existing SQL Server failover cluster</span></span>](#Remove)  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8a100-113">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安裝位置的作業系統磁碟機代號在加入至 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 容錯移轉叢集的所有節點上都必須符合。</span><span class="sxs-lookup"><span data-stu-id="8a100-113">The operating system drive letter for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] install locations must match on all the nodes added to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster.</span></span>  
  
##  <a name="add-node"></a><a name="Add"></a> <span data-ttu-id="8a100-114">加入節點</span><span class="sxs-lookup"><span data-stu-id="8a100-114">Add Node</span></span>  
  
#### <a name="to-add-a-node-to-an-existing-ssnoversion-failover-cluster"></a><span data-ttu-id="8a100-115">將節點加入現有的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 容錯移轉叢集</span><span class="sxs-lookup"><span data-stu-id="8a100-115">To add a node to an existing [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster</span></span>  
  
1.  <span data-ttu-id="8a100-116">插入 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安裝媒體，然後在根資料夾中，按兩下 Setup.exe。</span><span class="sxs-lookup"><span data-stu-id="8a100-116">Insert the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installation media, and from the root folder, double-click Setup.exe.</span></span> <span data-ttu-id="8a100-117">若要從網路共用進行安裝，請導覽至共用上的根資料夾，然後按兩下 Setup.exe。</span><span class="sxs-lookup"><span data-stu-id="8a100-117">To install from a network share, navigate to the root folder on the share, and then double-click Setup.exe.</span></span>  
  
2.  <span data-ttu-id="8a100-118">安裝精靈將會啟動 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安裝中心。</span><span class="sxs-lookup"><span data-stu-id="8a100-118">The Installation Wizard will launch the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Installation Center.</span></span> <span data-ttu-id="8a100-119">若要將節點加入至現有的容錯移轉叢集執行個體，請在左側窗格中按一下 [安裝]  。</span><span class="sxs-lookup"><span data-stu-id="8a100-119">To add a node to an existing failover cluster instance, click **Installation** in the left-hand pane.</span></span> <span data-ttu-id="8a100-120">然後，請選取 [將節點加入到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 容錯移轉叢集]。</span><span class="sxs-lookup"><span data-stu-id="8a100-120">Then, select **Add node to a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster**.</span></span>  
  
3.  <span data-ttu-id="8a100-121">系統組態檢查將會在電腦上執行探索作業。</span><span class="sxs-lookup"><span data-stu-id="8a100-121">The System Configuration Checker will run a discovery operation on your computer.</span></span> <span data-ttu-id="8a100-122">若要繼續，請[!INCLUDE[clickOK](../../../includes/clickok-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8a100-122">To continue, [!INCLUDE[clickOK](../../../includes/clickok-md.md)].</span></span>  
  
4.  <span data-ttu-id="8a100-123">如果您在當地語系化的作業系統上安裝，而且安裝媒體包含英文以及與作業系統對應之語言的語言套件，您便可以在 [語言選擇] 頁面上指定 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的語言。</span><span class="sxs-lookup"><span data-stu-id="8a100-123">On the Language Selection page, you can specify the language for your instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] if you are installing on a localized operating system and the installation media includes language packs for both English and the language corresponding to the operating system.</span></span> <span data-ttu-id="8a100-124">如需跨語言支援和安裝考量的詳細資訊，請參閱 [SQL Server 中的地區語言版本](../../install/local-language-versions-in-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="8a100-124">For more information about cross-language support and installation considerations, see [Local Language Versions in SQL Server](../../install/local-language-versions-in-sql-server.md).</span></span>  
  
     <span data-ttu-id="8a100-125">若要繼續進行，請按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="8a100-125">To continue, click **Next**.</span></span>  
  
5.  <span data-ttu-id="8a100-126">在 [產品金鑰] 頁面上，針對產品的實際執行版本指定 PID 金鑰。</span><span class="sxs-lookup"><span data-stu-id="8a100-126">On the Product key page, specify the PID key for a production version of the product.</span></span> <span data-ttu-id="8a100-127">請注意，您針對此安裝輸入的產品金鑰必須與安裝在使用中節點上的版本具有相同的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 版本。</span><span class="sxs-lookup"><span data-stu-id="8a100-127">Note that the product key you enter for this installation must be for the same [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] edition as that which is installed on the active node.</span></span>  
  
6.  <span data-ttu-id="8a100-128">在 [授權條款] 頁面上，閱讀授權合約，然後選取要接受授權條款和條件的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="8a100-128">On the License Terms page, read the license agreement, and then select the check box to accept the licensing terms and conditions.</span></span> <span data-ttu-id="8a100-129">若要協助提升 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]，您也可以啟用功能使用方式選項，並傳送報告給 [!INCLUDE[msCoName](../../../includes/msconame-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8a100-129">To help improve [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], you can also enable the feature usage option and send reports to [!INCLUDE[msCoName](../../../includes/msconame-md.md)].</span></span> <span data-ttu-id="8a100-130">若要繼續進行，請按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="8a100-130">To continue, click **Next**.</span></span> <span data-ttu-id="8a100-131">若要結束安裝程式，請按一下 **[取消]** 。</span><span class="sxs-lookup"><span data-stu-id="8a100-131">To end Setup, click **Cancel**.</span></span>  
  
7.  <span data-ttu-id="8a100-132">系統組態檢查將會先確認電腦的系統狀態，然後安裝程式才會繼續進行。</span><span class="sxs-lookup"><span data-stu-id="8a100-132">The System Configuration Checker will verify the system state of your computer before Setup continues.</span></span> <span data-ttu-id="8a100-133">檢查完成之後，請按 **[下一步]** 繼續進行。</span><span class="sxs-lookup"><span data-stu-id="8a100-133">After the check is complete, click **Next** to continue.</span></span>  
  
8.  <span data-ttu-id="8a100-134">在 [叢集節點組態] 頁面上，使用下拉式方塊來指定將要在此安裝程式作業期間修改之 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 容錯移轉叢集執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="8a100-134">On the Cluster Node Configuration page, use the drop-down box to specify the name of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster instance that will be modified during this Setup operation.</span></span>  
  
9. <span data-ttu-id="8a100-135">在 [伺服器設定 - 服務帳戶] 頁面中，指定 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服務的登入帳戶。</span><span class="sxs-lookup"><span data-stu-id="8a100-135">On the Server Configuration - Service Accounts page, specify login accounts for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] services.</span></span> <span data-ttu-id="8a100-136">在這個頁面上所設定的實際服務隨著您選取要安裝的功能而不同。</span><span class="sxs-lookup"><span data-stu-id="8a100-136">The actual services that are configured on this page depend on the features you selected to install.</span></span> <span data-ttu-id="8a100-137">若為容錯移轉叢集安裝，系統就會根據針對使用中節點所提供的設定，在這個頁面上預先填入帳戶名稱和啟動類型資訊。</span><span class="sxs-lookup"><span data-stu-id="8a100-137">For failover cluster installations, account name and startup type information will be pre-populated on this page based on settings provided for the active node.</span></span> <span data-ttu-id="8a100-138">不過，您必須提供每個帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="8a100-138">You must provide passwords for each account.</span></span> <span data-ttu-id="8a100-139">如需詳細資訊，請參閱 [伺服器組態 - 服務帳戶](../../install/server-configuration-service-accounts.md) 和 [設定 Windows 服務帳戶與權限](../../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)。</span><span class="sxs-lookup"><span data-stu-id="8a100-139">For more information, see [Server Configuration - Service Accounts](../../install/server-configuration-service-accounts.md) and [Configure Windows Service Accounts and Permissions](../../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md).</span></span>  
  
     <span data-ttu-id="8a100-140">**安全性注意事項** [!INCLUDE[ssNoteStrongPass](../../../includes/ssnotestrongpass-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a100-140">**Security Note** [!INCLUDE[ssNoteStrongPass](../../../includes/ssnotestrongpass-md.md)]</span></span>  
  
     <span data-ttu-id="8a100-141">當您完成針對 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服務指定登入資訊之後，請按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="8a100-141">When you are finished specifying login information for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] services, click **Next**.</span></span>  
  
10. <span data-ttu-id="8a100-142">在 [報告] 頁面上，指定您想要傳送給 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 的資訊，以便改善 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8a100-142">On the Reporting page, specify the information you would like to send to [!INCLUDE[msCoName](../../../includes/msconame-md.md)] to improve [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="8a100-143">錯誤報告選項預設為啟用。</span><span class="sxs-lookup"><span data-stu-id="8a100-143">By default, option for error reporting is enabled.</span></span>  
  
11. <span data-ttu-id="8a100-144">系統組態檢查將會執行一組額外的規則，以便使用您已指定的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 功能來驗證電腦組態。</span><span class="sxs-lookup"><span data-stu-id="8a100-144">The System Configuration Checker will run one more set of rules to validate your computer configuration with the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] features you have specified.</span></span>  
  
12. <span data-ttu-id="8a100-145">[準備加入節點] 頁面會顯示在安裝期間指定之安裝選項的樹狀檢視。</span><span class="sxs-lookup"><span data-stu-id="8a100-145">The Ready to Add Node page displays a tree view of installation options that were specified during Setup.</span></span>  
  
13. <span data-ttu-id="8a100-146">[加入節點進度] 頁面會提供狀態，所以您可以在安裝程式進行時監視安裝進度。</span><span class="sxs-lookup"><span data-stu-id="8a100-146">Add Node Progress page provides status so you can monitor installation progress as Setup proceeds.</span></span>  
  
14. <span data-ttu-id="8a100-147">安裝之後，[完成] 頁面會提供安裝和其他重要注意事項之摘要記錄檔的連結。</span><span class="sxs-lookup"><span data-stu-id="8a100-147">After installation, the Complete page provides a link to the summary log file for the installation and other important notes.</span></span> <span data-ttu-id="8a100-148">若要完成 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安裝程序，請按一下 **[關閉]** 。</span><span class="sxs-lookup"><span data-stu-id="8a100-148">To complete the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installation process, click **Close**.</span></span>  
  
15. <span data-ttu-id="8a100-149">如果指示您重新啟動電腦，請立刻執行。</span><span class="sxs-lookup"><span data-stu-id="8a100-149">If you are instructed to restart the computer, do so now.</span></span> <span data-ttu-id="8a100-150">當您完成安裝時，請務必閱讀安裝精靈所提供的訊息。</span><span class="sxs-lookup"><span data-stu-id="8a100-150">It is important to read the message from the Installation Wizard when you are done with Setup.</span></span> <span data-ttu-id="8a100-151">如需安裝程式記錄檔的詳細資訊，請參閱 [檢視與讀取 SQL Server 安裝程式記錄檔](../../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)。</span><span class="sxs-lookup"><span data-stu-id="8a100-151">For more information about Setup log files, see [View and Read SQL Server Setup Log Files](../../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md).</span></span>  
  
##  <a name="remove-node"></a><a name="Remove"></a> <span data-ttu-id="8a100-152">移除節點</span><span class="sxs-lookup"><span data-stu-id="8a100-152">Remove Node</span></span>  
  
#### <a name="to-remove-a-node-from-an-existing-ssnoversion-failover-cluster"></a><span data-ttu-id="8a100-153">從現有的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 容錯移轉叢集中移除節點</span><span class="sxs-lookup"><span data-stu-id="8a100-153">To remove a node from an existing [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster</span></span>  
  
1.  <span data-ttu-id="8a100-154">插入 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安裝媒體。</span><span class="sxs-lookup"><span data-stu-id="8a100-154">Insert the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installation media.</span></span> <span data-ttu-id="8a100-155">在根資料夾中，按兩下 setup.exe。</span><span class="sxs-lookup"><span data-stu-id="8a100-155">From the root folder, double-click setup.exe.</span></span> <span data-ttu-id="8a100-156">若要從網路共用進行安裝，請導覽至共用上的根資料夾，然後按兩下 Setup.exe。</span><span class="sxs-lookup"><span data-stu-id="8a100-156">To install from a network share, navigate to the root folder on the share, and then double-click Setup.exe.</span></span>  
  
2.  <span data-ttu-id="8a100-157">安裝精靈會啟動 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安裝中心。</span><span class="sxs-lookup"><span data-stu-id="8a100-157">The Installation Wizard launches the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Installation Center.</span></span> <span data-ttu-id="8a100-158">若要從現有的容錯移轉叢集執行個體中移除節點，請在左側窗格中按一下 [維護]，然後選取 [從 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 容錯移轉叢集移除節點]。</span><span class="sxs-lookup"><span data-stu-id="8a100-158">To remove a node to an existing failover cluster instance, click **Maintenance** in the left-hand pane, and then select **Remove node from a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster**.</span></span>  
  
3.  <span data-ttu-id="8a100-159">系統組態檢查將會在電腦上執行探索作業。</span><span class="sxs-lookup"><span data-stu-id="8a100-159">The System Configuration Checker will run a discovery operation on your computer.</span></span> <span data-ttu-id="8a100-160">若要繼續，請[!INCLUDE[clickOK](../../../includes/clickok-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8a100-160">To continue, [!INCLUDE[clickOK](../../../includes/clickok-md.md)].</span></span>  
  
4.  <span data-ttu-id="8a100-161">按一下 [安裝程式支援檔案] 頁面上的 [安裝] 後，[系統組態檢查] 會在安裝程式繼續前檢查系統狀態。</span><span class="sxs-lookup"><span data-stu-id="8a100-161">After you click install on the Setup Support Files page, the System Configuration Checker verifies the system state of your computer before Setup continues.</span></span> <span data-ttu-id="8a100-162">檢查完成之後，請按 **[下一步]** 繼續進行。</span><span class="sxs-lookup"><span data-stu-id="8a100-162">After the check is complete, click **Next** to continue.</span></span>  
  
5.  <span data-ttu-id="8a100-163">在 [叢集節點組態] 頁面上，使用下拉式方塊來指定將要在此安裝程式作業期間修改之 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 容錯移轉叢集執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="8a100-163">On the Cluster Node Configuration page, use the drop-down box to specify the name of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster instance to be modified during this Setup operation.</span></span> <span data-ttu-id="8a100-164">將要移除的節點就會列在 **[此節點的名稱]** 欄位中。</span><span class="sxs-lookup"><span data-stu-id="8a100-164">The node to be removed is listed in the **Name of this node** field.</span></span>  
  
6.  <span data-ttu-id="8a100-165">[準備移除節點] 頁面會顯示在安裝期間指定之選項的樹狀檢視。</span><span class="sxs-lookup"><span data-stu-id="8a100-165">The Ready to Remove Node page displays a tree view of options that were specified during Setup.</span></span> <span data-ttu-id="8a100-166">若要繼續，請按一下 **[移除]** 。</span><span class="sxs-lookup"><span data-stu-id="8a100-166">To continue, click **Remove**.</span></span>  
  
7.  <span data-ttu-id="8a100-167">在移除作業期間，[移除節點進度] 頁面將提供狀態。</span><span class="sxs-lookup"><span data-stu-id="8a100-167">During the remove operation, the Remove Node Progress page provides status.</span></span>  
  
8.  <span data-ttu-id="8a100-168">[完成] 頁面會提供移除節點作業和其他重要注意事項之摘要記錄檔的連結。</span><span class="sxs-lookup"><span data-stu-id="8a100-168">The Complete page provides a link to the summary log file for the remove node operation and other important notes.</span></span> <span data-ttu-id="8a100-169">若要完成 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 移除節點作業，請按一下 **[關閉]** 。</span><span class="sxs-lookup"><span data-stu-id="8a100-169">To complete the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] remove node, click **Close**.</span></span> <span data-ttu-id="8a100-170">如需安裝程式記錄檔的詳細資訊，請參閱 [檢視與讀取 SQL Server 安裝程式記錄檔](../../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)。</span><span class="sxs-lookup"><span data-stu-id="8a100-170">For more information about Setup log files, see [View and Read SQL Server Setup Log Files](../../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a100-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a100-171">See Also</span></span>  
 [<span data-ttu-id="8a100-172">檢視與讀取 SQL Server 安裝程式記錄檔</span><span class="sxs-lookup"><span data-stu-id="8a100-172">View and Read SQL Server Setup Log Files</span></span>](../../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)  
  
  