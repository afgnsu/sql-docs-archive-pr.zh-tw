---
title: Distributed Replay 安全性 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: 7e2e586d-947d-4fe2-86c5-f06200ebf139
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7b05c6bbe3998faa46d56684b77b8d2a4dec4466
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595324"
---
# <a name="distributed-replay-security"></a><span data-ttu-id="cf413-102">Distributed Replay 安全性</span><span class="sxs-lookup"><span data-stu-id="cf413-102">Distributed Replay Security</span></span>
  <span data-ttu-id="cf413-103">在安裝和使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay 功能之前，您應該先檢閱本主題中的重要安全性資訊。</span><span class="sxs-lookup"><span data-stu-id="cf413-103">Before you install and use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay feature, you should review the important security information in this topic.</span></span> <span data-ttu-id="cf413-104">本主題描述的是使用 Distributed Replay 之前必須進行的安裝後安全性設定步驟。</span><span class="sxs-lookup"><span data-stu-id="cf413-104">This topic describes the post-installation security configuration steps that are required before you can use Distributed Replay.</span></span> <span data-ttu-id="cf413-105">本主題亦描述與資料保護和重要移除步驟有關的重要考量。</span><span class="sxs-lookup"><span data-stu-id="cf413-105">This topic also describes important considerations with regard to data protection and important removal steps.</span></span>  
  
## <a name="user-and-service-accounts"></a><span data-ttu-id="cf413-106">使用者和服務帳戶</span><span class="sxs-lookup"><span data-stu-id="cf413-106">User and Service Accounts</span></span>  
 <span data-ttu-id="cf413-107">下表描述用於 Distributed Replay 的帳戶。</span><span class="sxs-lookup"><span data-stu-id="cf413-107">The following table describes the accounts that are used for Distributed Replay.</span></span> <span data-ttu-id="cf413-108">安裝 Distributed Replay 之後，您必須指派用以執行 Controller 和 Client 服務帳戶的安全性主體。</span><span class="sxs-lookup"><span data-stu-id="cf413-108">After the Distributed Replay installation, you must assign the security principals that the controller and client service accounts will run as.</span></span> <span data-ttu-id="cf413-109">因此，我們建議您在安裝 Distributed Replay 功能之前設定對應的網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="cf413-109">Therefore, we recommend that you configure the corresponding domain user accounts before you install the Distributed Replay features.</span></span>  
  
|<span data-ttu-id="cf413-110">使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="cf413-110">User Account</span></span>|<span data-ttu-id="cf413-111">需求</span><span class="sxs-lookup"><span data-stu-id="cf413-111">Requirements</span></span>|  
|------------------|------------------|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="cf413-112">Distributed Replay Controller 服務帳戶</span><span class="sxs-lookup"><span data-stu-id="cf413-112">Distributed Replay controller service account</span></span>|<span data-ttu-id="cf413-113">可以是網域使用者帳戶或本機使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="cf413-113">Can be a domain user account or local user account.</span></span> <span data-ttu-id="cf413-114">如果您使用本機使用者帳戶，管理工具、Controller 和 Client 都必須在同一部電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="cf413-114">If you use a local user account, the administration tool, controller, and client must all be running on the same computer.</span></span><br /><br /> <span data-ttu-id="cf413-115">**\*\* 安全性注意事項 \*\*** 我們建議您不要將此帳戶設定為 Windows 本機 Administrators 群組的成員。</span><span class="sxs-lookup"><span data-stu-id="cf413-115">**\*\* Security Note \*\*** We recommend that the account is not a member of the local Administrators group in Windows.</span></span>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="cf413-116">Distributed Replay Client 服務帳戶</span><span class="sxs-lookup"><span data-stu-id="cf413-116">Distributed Replay client service account</span></span>|<span data-ttu-id="cf413-117">可以是網域使用者帳戶或本機使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="cf413-117">Can be a domain user account or local user account.</span></span> <span data-ttu-id="cf413-118">如果您使用本機使用者帳戶，Controller、Client 和目標 SQL Server 都必須在同一部電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="cf413-118">If you use a local user account, the controller, client, and target SQL Server must all be running on the same computer.</span></span><br /><br /> <span data-ttu-id="cf413-119">**\*\* 安全性注意事項 \*\*** 我們建議您不要將此帳戶設定為 Windows 本機 Administrators 群組的成員。</span><span class="sxs-lookup"><span data-stu-id="cf413-119">**\*\* Security Note \*\*** We recommend that the account is not a member of the local Administrators group in Windows.</span></span>|  
|<span data-ttu-id="cf413-120">用來執行 Distributed Replay 管理工具的互動式使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="cf413-120">Interactive user account that is used to run the Distributed Replay administration tool</span></span>|<span data-ttu-id="cf413-121">可以是本機使用者或網域使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="cf413-121">Can be either a local user or a domain user account.</span></span> <span data-ttu-id="cf413-122">若要使用本機使用者帳戶，管理工具和控制器必須在同一部電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="cf413-122">To use a local user account, the administration tool and controller must be running on the same computer.</span></span>|  
  
 <span data-ttu-id="cf413-123">**重要**：當您設定 Distributed Replay Controller 時，可以指定將用來執行 Distributed Replay Client 服務的一或多個使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="cf413-123">**Important**: When you configure Distributed Replay controller, you can specify one or more user accounts that will be used to run the Distributed Replay client services.</span></span> <span data-ttu-id="cf413-124">下列是支援帳戶的清單：</span><span class="sxs-lookup"><span data-stu-id="cf413-124">The following is the list of supported accounts:</span></span>  
  
-   <span data-ttu-id="cf413-125">網域使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="cf413-125">Domain user account</span></span>  
  
-   <span data-ttu-id="cf413-126">使用者建立的本機使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="cf413-126">User created local user account</span></span>  
  
-   <span data-ttu-id="cf413-127">系統管理員</span><span class="sxs-lookup"><span data-stu-id="cf413-127">Administrator</span></span>  
  
-   <span data-ttu-id="cf413-128">虛擬帳戶和 MSA (受管理的服務帳戶)</span><span class="sxs-lookup"><span data-stu-id="cf413-128">Virtual account and MSA (Managed Service Account)</span></span>  
  
-   <span data-ttu-id="cf413-129">網路服務、本機系統和系統</span><span class="sxs-lookup"><span data-stu-id="cf413-129">Network Services, Local Services, and System</span></span>  
  
 <span data-ttu-id="cf413-130">不接受群組帳戶 (本機或網域) 和其他內建帳戶 (例如 Everyone)。</span><span class="sxs-lookup"><span data-stu-id="cf413-130">Group accounts (local or domain) and other built-in accounts (like Everyone) are not accepted.</span></span>  
  
 <span data-ttu-id="cf413-131">若要在安裝 Distributed Replay 之後設定服務帳戶或其密碼，您可以使用 Windows 服務工具。</span><span class="sxs-lookup"><span data-stu-id="cf413-131">To set the service accounts or their passwords after you install Distributed Replay, you can use the Windows Services tool.</span></span> <span data-ttu-id="cf413-132">若要變更與 Distributed Replay Controller 或 Client 服務相關聯的服務帳戶，請遵循下列步驟進行：</span><span class="sxs-lookup"><span data-stu-id="cf413-132">To change the service accounts associated with the Distributed Replay controller or client services, follow these steps:</span></span>  
  
1.  <span data-ttu-id="cf413-133">請根據作業系統執行下列其中一項作業：</span><span class="sxs-lookup"><span data-stu-id="cf413-133">Do either of the following, depending on the operating system:</span></span>  
  
    -   <span data-ttu-id="cf413-134">按一下 [**開始**]， `services.msc` 在 [**搜尋**] 方塊中輸入，然後按 enter。</span><span class="sxs-lookup"><span data-stu-id="cf413-134">Click **Start**, type `services.msc` in the **Search** box, and then press ENTER.</span></span>  
  
    -   <span data-ttu-id="cf413-135">依序按一下 [**開始**] 和 [**執行**]，輸入 `services.msc` ，然後按 enter。</span><span class="sxs-lookup"><span data-stu-id="cf413-135">Click **Start**, click **Run**, type `services.msc`, and then press ENTER.</span></span>  
  
2.  <span data-ttu-id="cf413-136">在 [服務] 對話方塊中，以滑鼠右鍵按一下您想要設定的服務，然後按一下 [內容]。</span><span class="sxs-lookup"><span data-stu-id="cf413-136">In the **Services** dialog box, right-click the service that you want to configure, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="cf413-137">在 [登入] 索引標籤上，按一下 [This account (這個帳戶)]。</span><span class="sxs-lookup"><span data-stu-id="cf413-137">On the **Log On** tab, click **This account**.</span></span>  
  
4.  <span data-ttu-id="cf413-138">設定您想要使用的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="cf413-138">Configure the user account that you want to use.</span></span>  
  
## <a name="file-and-folder-permissions"></a><span data-ttu-id="cf413-139">檔案和資料夾權限</span><span class="sxs-lookup"><span data-stu-id="cf413-139">File and Folder Permissions</span></span>  
 <span data-ttu-id="cf413-140">指定了服務帳戶之後，您必須將必要的檔案和資料夾權限授與這些服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="cf413-140">After the service accounts have been specified, you must grant the necessary file and folder permissions to those service accounts.</span></span> <span data-ttu-id="cf413-141">請根據下表設定檔案和資料夾權限：</span><span class="sxs-lookup"><span data-stu-id="cf413-141">Configure file and folder permissions according to the following table:</span></span>  
  
|<span data-ttu-id="cf413-142">帳戶</span><span class="sxs-lookup"><span data-stu-id="cf413-142">Account</span></span>|<span data-ttu-id="cf413-143">資料夾權限</span><span class="sxs-lookup"><span data-stu-id="cf413-143">Folder Permissions</span></span>|  
|-------------|------------------------|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="cf413-144">Distributed Replay Controller 服務帳戶</span><span class="sxs-lookup"><span data-stu-id="cf413-144">Distributed Replay controller service account</span></span>|<span data-ttu-id="cf413-145">`<Controller_Installation_Path>\DReplayController` (讀取、寫入、刪除)</span><span class="sxs-lookup"><span data-stu-id="cf413-145">`<Controller_Installation_Path>\DReplayController` (Read, Write, Delete)</span></span><br /><br /> <span data-ttu-id="cf413-146">`DReplayServer.xml` 檔案 (讀取、寫入)</span><span class="sxs-lookup"><span data-stu-id="cf413-146">`DReplayServer.xml` file (Read, Write)</span></span>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="cf413-147">Distributed Replay Client 服務帳戶</span><span class="sxs-lookup"><span data-stu-id="cf413-147">Distributed Replay client service account</span></span>|<span data-ttu-id="cf413-148">`<Client_Installation_Path>\DReplayClient` (讀取、寫入、刪除)</span><span class="sxs-lookup"><span data-stu-id="cf413-148">`<Client_Installation_Path>\DReplayClient` (Read, Write, Delete)</span></span><br /><br /> <span data-ttu-id="cf413-149">`DReplayClient.xml` 檔案 (讀取、寫入)</span><span class="sxs-lookup"><span data-stu-id="cf413-149">`DReplayClient.xml` file (Read, Write)</span></span><br /><br /> <span data-ttu-id="cf413-150">工作和結果目錄，分別由 `WorkingDirectory` 和 `ResultDirectory` 元素指定於 Client 組態檔中</span><span class="sxs-lookup"><span data-stu-id="cf413-150">The working and result directories, as specified in the client configuration file by the `WorkingDirectory` and `ResultDirectory` elements, respectively.</span></span> <span data-ttu-id="cf413-151">(讀取、寫入)。</span><span class="sxs-lookup"><span data-stu-id="cf413-151">(Read, Write)</span></span>|  
  
## <a name="dcom-permissions"></a><span data-ttu-id="cf413-152">DCOM 權限</span><span class="sxs-lookup"><span data-stu-id="cf413-152">DCOM Permissions</span></span>  
 <span data-ttu-id="cf413-153">DCOM 是用於 Controller 與管理工具以及 Controller 與所有 Client 之間的遠端程序呼叫 (RPC) 通訊。</span><span class="sxs-lookup"><span data-stu-id="cf413-153">DCOM is used for remote procedure call (RPC) communication between the controller and the administration tool, and between the controller and all clients.</span></span> <span data-ttu-id="cf413-154">安裝了 Distributed Replay 功能之後，您必須在 Controller 上設定整部電腦和應用程式特定的 DCOM 權限。</span><span class="sxs-lookup"><span data-stu-id="cf413-154">You must configure computer-wide and application-specific DCOM permissions on the controller after the Distributed Replay features have been installed.</span></span>  
  
 <span data-ttu-id="cf413-155">若要設定 Controller DCOM 權限，請遵循下列步驟進行：</span><span class="sxs-lookup"><span data-stu-id="cf413-155">To configure the controller DCOM permissions, follow these steps:</span></span>  
  
1.  <span data-ttu-id="cf413-156">**開啟 dcomcnfg.exe，[元件服務] 嵌入式管理單元**：此為用來設定 DCOM 權限的工具。</span><span class="sxs-lookup"><span data-stu-id="cf413-156">**Open dcomcnfg.exe, the Component Services snap-in**: This is the tool that is used to configure DCOM permissions.</span></span>  
  
    1.  <span data-ttu-id="cf413-157">在 Controller 電腦上，按一下 [開始]。</span><span class="sxs-lookup"><span data-stu-id="cf413-157">On the controller computer, click **Start**.</span></span>  
  
    2.  <span data-ttu-id="cf413-158">`dcomcnfg.exe`在 [**搜尋**] 方塊中輸入。</span><span class="sxs-lookup"><span data-stu-id="cf413-158">Type `dcomcnfg.exe` in the **Search** box.</span></span>  
  
    3.  <span data-ttu-id="cf413-159">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="cf413-159">Press ENTER.</span></span>  
  
2.  <span data-ttu-id="cf413-160">**設定整部電腦的 DCOM 權限**：針對下表所列的每個帳戶授與對應的整部電腦 DCOM 權限。</span><span class="sxs-lookup"><span data-stu-id="cf413-160">**Configure computer-wide DCOM permissions**: Grant the corresponding computer-wide DCOM permissions for each account listed in the following table.</span></span> <span data-ttu-id="cf413-161">如需如何設定整部電腦權限的詳細資訊，請參閱 [檢查清單：管理 DCOM 應用程式](https://go.microsoft.com/fwlink/?LinkId=185842)。</span><span class="sxs-lookup"><span data-stu-id="cf413-161">For more information about how to set computer-wide permissions, see [Checklist: Manage DCOM Applications](https://go.microsoft.com/fwlink/?LinkId=185842).</span></span>  
  
3.  <span data-ttu-id="cf413-162">**設定應用程式限定的 DCOM 權限**：針對下表所列的每個帳戶授與對應的應用程式限定的 DCOM 權限。</span><span class="sxs-lookup"><span data-stu-id="cf413-162">**Configure application-specific DCOM permissions**: Grant the corresponding application-specific DCOM permissions for each account listed in the following table.</span></span> <span data-ttu-id="cf413-163">控制器服務的 DCOM 應用程式名稱是 **DReplayController**。</span><span class="sxs-lookup"><span data-stu-id="cf413-163">The DCOM application name for the controller service is **DReplayController**.</span></span> <span data-ttu-id="cf413-164">如需如何設定應用程式特定權限的詳細資訊，請參閱 [檢查清單：管理 DCOM 應用程式](https://go.microsoft.com/fwlink/?LinkId=185842)。</span><span class="sxs-lookup"><span data-stu-id="cf413-164">For more information about how to set application-specific permissions, see [Checklist: Manage DCOM Applications](https://go.microsoft.com/fwlink/?LinkId=185842).</span></span>  
  
 <span data-ttu-id="cf413-165">下表描述哪些 DCOM 權限是管理工具互動式使用者帳戶和 Client 服務帳戶所需的權限：</span><span class="sxs-lookup"><span data-stu-id="cf413-165">The following table describes which DCOM permissions are required for the administration tool interactive user account and the client service accounts:</span></span>  
  
|<span data-ttu-id="cf413-166">功能</span><span class="sxs-lookup"><span data-stu-id="cf413-166">Feature</span></span>|<span data-ttu-id="cf413-167">帳戶</span><span class="sxs-lookup"><span data-stu-id="cf413-167">Account</span></span>|<span data-ttu-id="cf413-168">Controller 的必要 DCOM 權限</span><span class="sxs-lookup"><span data-stu-id="cf413-168">Required DCOM Permissions on Controller</span></span>|  
|-------------|-------------|---------------------------------------------|  
|<span data-ttu-id="cf413-169">Distributed Replay 管理工具</span><span class="sxs-lookup"><span data-stu-id="cf413-169">Distributed Replay administration tool</span></span>|<span data-ttu-id="cf413-170">互動式使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="cf413-170">The interactive user account</span></span>|<span data-ttu-id="cf413-171">本機存取</span><span class="sxs-lookup"><span data-stu-id="cf413-171">Local Access</span></span><br /><br /> <span data-ttu-id="cf413-172">遠端存取</span><span class="sxs-lookup"><span data-stu-id="cf413-172">Remote Access</span></span><br /><br /> <span data-ttu-id="cf413-173">本機啟動</span><span class="sxs-lookup"><span data-stu-id="cf413-173">Local Launch</span></span><br /><br /> <span data-ttu-id="cf413-174">遠端啟動</span><span class="sxs-lookup"><span data-stu-id="cf413-174">Remote Launch</span></span><br /><br /> <span data-ttu-id="cf413-175">本機啟用</span><span class="sxs-lookup"><span data-stu-id="cf413-175">Local Activation</span></span><br /><br /> <span data-ttu-id="cf413-176">遠端啟用</span><span class="sxs-lookup"><span data-stu-id="cf413-176">Remote Activation</span></span>|  
|<span data-ttu-id="cf413-177">Distributed Replay Client</span><span class="sxs-lookup"><span data-stu-id="cf413-177">Distributed Replay client</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="cf413-178">Distributed Replay Client 服務帳戶</span><span class="sxs-lookup"><span data-stu-id="cf413-178">Distributed Replay client service account</span></span>|<span data-ttu-id="cf413-179">本機存取</span><span class="sxs-lookup"><span data-stu-id="cf413-179">Local Access</span></span><br /><br /> <span data-ttu-id="cf413-180">遠端存取</span><span class="sxs-lookup"><span data-stu-id="cf413-180">Remote Access</span></span><br /><br /> <span data-ttu-id="cf413-181">本機啟動</span><span class="sxs-lookup"><span data-stu-id="cf413-181">Local Launch</span></span><br /><br /> <span data-ttu-id="cf413-182">遠端啟動</span><span class="sxs-lookup"><span data-stu-id="cf413-182">Remote Launch</span></span><br /><br /> <span data-ttu-id="cf413-183">本機啟用</span><span class="sxs-lookup"><span data-stu-id="cf413-183">Local Activation</span></span><br /><br /> <span data-ttu-id="cf413-184">遠端啟用</span><span class="sxs-lookup"><span data-stu-id="cf413-184">Remote Activation</span></span>|  
  
> [!IMPORTANT]  
>  <span data-ttu-id="cf413-185">為了有效抵禦惡意查詢或阻斷服務攻擊，請務必只將信任的使用者帳戶用於 Client 服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="cf413-185">To help protect against malicious queries or denial of service attacks, make sure that you only use a trusted user account for the client service account.</span></span> <span data-ttu-id="cf413-186">此帳戶將能夠針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的目標執行個體連接並重新執行工作負載。</span><span class="sxs-lookup"><span data-stu-id="cf413-186">This account will be able to connect and replay workloads against the target instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="sql-server-permissions"></a><span data-ttu-id="cf413-187">SQL Server 權限</span><span class="sxs-lookup"><span data-stu-id="cf413-187">SQL Server Permissions</span></span>  
 <span data-ttu-id="cf413-188">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Client 服務帳戶是用來連接到工作負載的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]目標執行個體。</span><span class="sxs-lookup"><span data-stu-id="cf413-188">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay client service accounts are used to connect to the workload's target instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="cf413-189">這些連接僅支援 Windows 驗證模式。</span><span class="sxs-lookup"><span data-stu-id="cf413-189">Only Windows Authentication mode is supported for these connections.</span></span>  
  
 <span data-ttu-id="cf413-190">當您在一組電腦上安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay Client 服務之後，用於這些服務帳戶的安全性主體必須被授與您要重新執行追蹤工作負載之目標 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的系統管理員伺服器角色。</span><span class="sxs-lookup"><span data-stu-id="cf413-190">After you install the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Distributed Replay client service on a set of computers, the security principal used for those service accounts must be granted the sysadmin server role on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that you intend to replay the trace workload against.</span></span> <span data-ttu-id="cf413-191">在 Distributed Replay 安裝期間，不會自動執行此步驟。</span><span class="sxs-lookup"><span data-stu-id="cf413-191">This step is not performed automatically during Distributed Replay Setup.</span></span>  
  
## <a name="data-protection"></a><span data-ttu-id="cf413-192">資料保護</span><span class="sxs-lookup"><span data-stu-id="cf413-192">Data Protection</span></span>  
 <span data-ttu-id="cf413-193">在 Distributed Replay 環境中，下列使用者帳戶會被授與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]之目標伺服器執行個體、輸入追蹤資料和結果追蹤檔案的完整存取權：</span><span class="sxs-lookup"><span data-stu-id="cf413-193">In the Distributed Replay environment, the following user accounts are granted full access to the target server instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the input trace data and result trace files:</span></span>  
  
-   <span data-ttu-id="cf413-194">用來執行管理工具的互動式使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="cf413-194">The interactive user account that is used to run the administration tool.</span></span>  
  
-   <span data-ttu-id="cf413-195">Controller 服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="cf413-195">The controller service account.</span></span>  
  
-   <span data-ttu-id="cf413-196">Client 服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="cf413-196">The client service account.</span></span>  
  
-   <span data-ttu-id="cf413-197">Controller 上本機 Administrators 群組的成員。</span><span class="sxs-lookup"><span data-stu-id="cf413-197">Members of the local Administrators group on the controller.</span></span>  
  
-   <span data-ttu-id="cf413-198">Client 上本機 Administrators 群組的成員。</span><span class="sxs-lookup"><span data-stu-id="cf413-198">Members of the local Administrators group on the clients.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="cf413-199">這些帳戶對於 Distributed Replay 所使用之追蹤、中繼、分派或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料檔案中包含的任何個人識別資訊 (PII) 或機密資訊擁有完整存取權。</span><span class="sxs-lookup"><span data-stu-id="cf413-199">These accounts have full access to any personally identifiable information (PII) or sensitive information that is contained in the trace, intermediate, dispatch, or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data files that were used by Distributed Replay.</span></span>  
  
 <span data-ttu-id="cf413-200">我們建議您採取下列安全性預防措施：</span><span class="sxs-lookup"><span data-stu-id="cf413-200">We recommend that you take the following security precautions:</span></span>  
  
-   <span data-ttu-id="cf413-201">將輸入追蹤資料、輸出追蹤結果和資料庫檔案儲存在使用 NTFS 檔案系統 (NTFS) 的位置，並且套用適當的存取控制清單 (ACL)。</span><span class="sxs-lookup"><span data-stu-id="cf413-201">Store the input trace data, output trace results, and database files in a location that uses the NTFS file system (NTFS), and apply the appropriate access control lists (ACLs).</span></span> <span data-ttu-id="cf413-202">必要時，請加密儲存在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 電腦上的資料。</span><span class="sxs-lookup"><span data-stu-id="cf413-202">If it is needed, encrypt the data that is stored on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] computer.</span></span> <span data-ttu-id="cf413-203">請注意，ACL 不會套用至追蹤檔案，因此沒有任何資料遮罩或模糊化。</span><span class="sxs-lookup"><span data-stu-id="cf413-203">Be aware that ACLs are not applied to the trace files and there is no data masking or obfuscation.</span></span> <span data-ttu-id="cf413-204">您應該在使用後盡快刪除這些檔案。</span><span class="sxs-lookup"><span data-stu-id="cf413-204">You should delete these files quickly after use.</span></span>  
  
-   <span data-ttu-id="cf413-205">將適當的 ACL 和保留原則套用至 Distributed Replay 所產生的所有中繼和分派檔案。</span><span class="sxs-lookup"><span data-stu-id="cf413-205">Apply the appropriate ACLs and retention policy to all intermediate and dispatch files that are generated by Distributed Replay.</span></span>  
  
-   <span data-ttu-id="cf413-206">使用安全通訊端層 (SSL) 來協助保護網路傳輸。</span><span class="sxs-lookup"><span data-stu-id="cf413-206">Use Secure Sockets Layer (SSL) to help secure the network transport.</span></span>  
  
## <a name="important-removal-steps"></a><span data-ttu-id="cf413-207">重要移除步驟</span><span class="sxs-lookup"><span data-stu-id="cf413-207">Important Removal Steps</span></span>  
 <span data-ttu-id="cf413-208">我們建議您僅在測試環境中使用 Distributed Replay。</span><span class="sxs-lookup"><span data-stu-id="cf413-208">We recommend that you only use Distributed Replay in a test environment.</span></span> <span data-ttu-id="cf413-209">在您完成測試之後，針對不同的工作佈建這些電腦之前，請務必執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="cf413-209">After you have completed testing, and before you provision those computers for a different task, make sure that you do the following:</span></span>  
  
-   <span data-ttu-id="cf413-210">解除安裝 Distributed Replay 功能並且從 Controller 和所有 Client 中移除相關的組態檔。</span><span class="sxs-lookup"><span data-stu-id="cf413-210">Uninstall the Distributed Replay features and remove the related configuration files from the controller and all clients.</span></span>  
  
-   <span data-ttu-id="cf413-211">刪除用於測試的任何追蹤、中繼、分派和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫檔案。</span><span class="sxs-lookup"><span data-stu-id="cf413-211">Delete any trace, intermediate, dispatch, and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database files that were used for testing.</span></span> <span data-ttu-id="cf413-212">中繼和分派檔案會分別儲存在 Controller 和 Client 的工作目錄中。</span><span class="sxs-lookup"><span data-stu-id="cf413-212">The intermediate and dispatch files are stored in the working directory on the controller and client, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf413-213">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf413-213">See Also</span></span>  
 <span data-ttu-id="cf413-214">[SQL Server Distributed Replay](sql-server-distributed-replay.md) </span><span class="sxs-lookup"><span data-stu-id="cf413-214">[SQL Server Distributed Replay](sql-server-distributed-replay.md) </span></span>  
 [<span data-ttu-id="cf413-215">安裝 Distributed Replay</span><span class="sxs-lookup"><span data-stu-id="cf413-215">Install Distributed Replay</span></span>](install-distributed-replay-overview.md)  
  
  