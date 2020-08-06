---
title: 從命令提示字元安裝 Distributed Replay |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: ea1171da-f50e-4f16-bedc-5e468a46477f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: be7c950b886356c08050e37825d5215b62aeb8cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595322"
---
# <a name="install-distributed-replay-from-the-command-prompt"></a><span data-ttu-id="f64d0-102">從命令提示字元處安裝 Distributed Replay</span><span class="sxs-lookup"><span data-stu-id="f64d0-102">Install Distributed Replay from the Command Prompt</span></span>
  <span data-ttu-id="f64d0-103">在命令提示字元處安裝 Distributed Replay 的新執行個體，讓您可以指定安裝功能及應如何設定。</span><span class="sxs-lookup"><span data-stu-id="f64d0-103">Installing a new instance of Distributed Replay at the command prompt enables you to specify the features to install and how they should be configured.</span></span> <span data-ttu-id="f64d0-104">命令提示字元安裝支援安裝、修復、升級及解除 Distributed Replay 元件。</span><span class="sxs-lookup"><span data-stu-id="f64d0-104">The command prompt installation supports installing, repairing, upgrading, and uninstalling of the Distributed Replay components.</span></span> <span data-ttu-id="f64d0-105">透過命令提示字元安裝時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 支援使用 /Q 參數進行完整無訊息模式。</span><span class="sxs-lookup"><span data-stu-id="f64d0-105">When installing through the command prompt, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supports full quiet mode by using the /Q parameter.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f64d0-106">如果是本機安裝，您必須以管理員身分執行安裝程式。</span><span class="sxs-lookup"><span data-stu-id="f64d0-106">For local installations, you must run Setup as an administrator.</span></span> <span data-ttu-id="f64d0-107">如果您是從遠端共用位置安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，則必須使用對遠端共用位置具有讀取和執行權限的網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="f64d0-107">If you install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from a remote share, you must use a domain account that has read and execute permissions on the remote share.</span></span>  
  
## <a name="installation-parameters"></a><span data-ttu-id="f64d0-108">安裝參數</span><span class="sxs-lookup"><span data-stu-id="f64d0-108">Installation Parameters</span></span>  
 <span data-ttu-id="f64d0-109">最上層功能清單包括 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]和工具。</span><span class="sxs-lookup"><span data-stu-id="f64d0-109">The list of top-level features include [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], and Tools.</span></span> <span data-ttu-id="f64d0-110">工具功能會安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理工具、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]，以及其他共用元件。</span><span class="sxs-lookup"><span data-stu-id="f64d0-110">The Tools feature will install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Tools, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online, [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], and other shared components.</span></span> <span data-ttu-id="f64d0-111">若要安裝 Distributed Replay 元件，請指定下列參數：</span><span class="sxs-lookup"><span data-stu-id="f64d0-111">To install the Distributed Replay components, specify the following parameters:</span></span>  
  
|<span data-ttu-id="f64d0-112">元件</span><span class="sxs-lookup"><span data-stu-id="f64d0-112">Component</span></span>|<span data-ttu-id="f64d0-113">參數</span><span class="sxs-lookup"><span data-stu-id="f64d0-113">Parameter</span></span>|  
|---------------|---------------|  
|<span data-ttu-id="f64d0-114">Distributed Replay Controller</span><span class="sxs-lookup"><span data-stu-id="f64d0-114">Distributed Replay controller</span></span>|<span data-ttu-id="f64d0-115">**DREPLAY_CTLR**</span><span class="sxs-lookup"><span data-stu-id="f64d0-115">**DREPLAY_CTLR**</span></span>|  
|<span data-ttu-id="f64d0-116">Distributed Replay Client</span><span class="sxs-lookup"><span data-stu-id="f64d0-116">Distributed Replay client</span></span>|<span data-ttu-id="f64d0-117">**DREPLAY_CLT**</span><span class="sxs-lookup"><span data-stu-id="f64d0-117">**DREPLAY_CLT**</span></span>|  
|<span data-ttu-id="f64d0-118">管理工具</span><span class="sxs-lookup"><span data-stu-id="f64d0-118">Administration Tool</span></span>|<span data-ttu-id="f64d0-119">**工具**</span><span class="sxs-lookup"><span data-stu-id="f64d0-119">**Tools**</span></span>|  
  
> [!IMPORTANT]  
>  <span data-ttu-id="f64d0-120">安裝 Distributed Replay 之後，您必須在控制器電腦與用戶端電腦上建立防火牆規則，並為目標伺服器上的每個用戶端電腦授與權限。</span><span class="sxs-lookup"><span data-stu-id="f64d0-120">After you install Distributed Replay you must create firewall rules on the controller and client computers, and grant each client computer permissions on the target server.</span></span> <span data-ttu-id="f64d0-121">如需詳細資訊，請參閱 [完成安裝後步驟](complete-the-post-installation-steps.md)。</span><span class="sxs-lookup"><span data-stu-id="f64d0-121">For more information, see [Complete the Post-Installation Steps](complete-the-post-installation-steps.md).</span></span>  
  
 <span data-ttu-id="f64d0-122">您可以使用下表中的參數來開發安裝的命令列指令碼。</span><span class="sxs-lookup"><span data-stu-id="f64d0-122">Use the parameters in the following table to develop command line scripts for installation.</span></span>  
  
|<span data-ttu-id="f64d0-123">參數</span><span class="sxs-lookup"><span data-stu-id="f64d0-123">Parameter</span></span>|<span data-ttu-id="f64d0-124">描述</span><span class="sxs-lookup"><span data-stu-id="f64d0-124">Description</span></span>|<span data-ttu-id="f64d0-125">支援的值</span><span class="sxs-lookup"><span data-stu-id="f64d0-125">Supported Values</span></span>|  
|---------------|-----------------|----------------------|  
|<span data-ttu-id="f64d0-126">/CTLRSVCACCOUNT</span><span class="sxs-lookup"><span data-stu-id="f64d0-126">/CTLRSVCACCOUNT</span></span><br /><br /> <span data-ttu-id="f64d0-127">**選擇性**</span><span class="sxs-lookup"><span data-stu-id="f64d0-127">**Optional**</span></span>|<span data-ttu-id="f64d0-128">Distributed Replay Controller 服務的服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="f64d0-128">Service account for the Distributed Replay controller service.</span></span>|<span data-ttu-id="f64d0-129">檢查帳戶和密碼</span><span class="sxs-lookup"><span data-stu-id="f64d0-129">Checks account and password</span></span>|  
|<span data-ttu-id="f64d0-130">/CTLRSVCPASSWORD</span><span class="sxs-lookup"><span data-stu-id="f64d0-130">/CTLRSVCPASSWORD</span></span><br /><br /> <span data-ttu-id="f64d0-131">**選擇性**</span><span class="sxs-lookup"><span data-stu-id="f64d0-131">**Optional**</span></span>|<span data-ttu-id="f64d0-132">Distributed Replay Controller 服務帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="f64d0-132">Password for the Distributed Replay controller service account.</span></span>|<span data-ttu-id="f64d0-133">檢查帳戶和密碼</span><span class="sxs-lookup"><span data-stu-id="f64d0-133">Checks account and password</span></span>|  
|<span data-ttu-id="f64d0-134">/CTLRSTARTUPTYPE</span><span class="sxs-lookup"><span data-stu-id="f64d0-134">/CTLRSTARTUPTYPE</span></span><br /><br /> <span data-ttu-id="f64d0-135">**選擇性**</span><span class="sxs-lookup"><span data-stu-id="f64d0-135">**Optional**</span></span>|<span data-ttu-id="f64d0-136">Distributed Replay Controller 服務的啟動類型。</span><span class="sxs-lookup"><span data-stu-id="f64d0-136">Startup type for the Distributed Replay controller service.</span></span>|<span data-ttu-id="f64d0-137">自動</span><span class="sxs-lookup"><span data-stu-id="f64d0-137">Automatic</span></span><br /><br /> <span data-ttu-id="f64d0-138">已停用</span><span class="sxs-lookup"><span data-stu-id="f64d0-138">Disabled</span></span><br /><br /> <span data-ttu-id="f64d0-139">手動</span><span class="sxs-lookup"><span data-stu-id="f64d0-139">Manual</span></span>|  
|<span data-ttu-id="f64d0-140">/CTLRUSERS</span><span class="sxs-lookup"><span data-stu-id="f64d0-140">/CTLRUSERS</span></span><br /><br /> <span data-ttu-id="f64d0-141">**選擇性**</span><span class="sxs-lookup"><span data-stu-id="f64d0-141">**Optional**</span></span>|<span data-ttu-id="f64d0-142">指定哪些使用者擁有 Distributed Replay Controller 服務的權限。</span><span class="sxs-lookup"><span data-stu-id="f64d0-142">Specify which users have permissions for the Distributed Replay controller service.</span></span>|<span data-ttu-id="f64d0-143">使用者帳戶字串的集合，以 " " (空格) 作為分隔符號</span><span class="sxs-lookup"><span data-stu-id="f64d0-143">Set of user account strings using " " (space) for delimiter</span></span><br /><br /> <span data-ttu-id="f64d0-144">**重要**：當設定 Distributed Replay Controller 服務時，可指定將用來執行 Distributed Replay Client 服務的一或多個使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="f64d0-144">**Important**: When you configure the Distributed Replay controller service, you can specify one or more user accounts that will be used to run the Distributed Replay client services.</span></span> <span data-ttu-id="f64d0-145">下列是支援帳戶的清單：</span><span class="sxs-lookup"><span data-stu-id="f64d0-145">The following is the list of supported accounts:</span></span><br /><br /> <span data-ttu-id="f64d0-146">網域使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="f64d0-146">Domain user account</span></span><br /><br /> <span data-ttu-id="f64d0-147">使用者建立的本機使用者帳戶</span><span class="sxs-lookup"><span data-stu-id="f64d0-147">User created local user account</span></span><br /><br /> <span data-ttu-id="f64d0-148">系統管理員</span><span class="sxs-lookup"><span data-stu-id="f64d0-148">Administrator</span></span><br /><br /> <span data-ttu-id="f64d0-149">虛擬帳戶和 MSA (受管理的服務帳戶)</span><span class="sxs-lookup"><span data-stu-id="f64d0-149">Virtual account and MSA (Managed Service Account)</span></span><br /><br /> <span data-ttu-id="f64d0-150">網路服務、本機系統和系統</span><span class="sxs-lookup"><span data-stu-id="f64d0-150">Network Services, Local Services, and System</span></span><br /><br /> <br /><br /> <span data-ttu-id="f64d0-151">不接受群組帳戶 (本機或網域) 和其他內建帳戶 (例如 Everyone)。</span><span class="sxs-lookup"><span data-stu-id="f64d0-151">Group accounts (local or domain) and other built-in accounts (like Everyone) are not accepted.</span></span>|  
|<span data-ttu-id="f64d0-152">/CLTSVCACCOUNT</span><span class="sxs-lookup"><span data-stu-id="f64d0-152">/CLTSVCACCOUNT</span></span><br /><br /> <span data-ttu-id="f64d0-153">**選擇性**</span><span class="sxs-lookup"><span data-stu-id="f64d0-153">**Optional**</span></span>|<span data-ttu-id="f64d0-154">Distributed Replay Client 服務的服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="f64d0-154">Service account for the Distributed Replay client service.</span></span>|<span data-ttu-id="f64d0-155">檢查帳戶和密碼</span><span class="sxs-lookup"><span data-stu-id="f64d0-155">Checks account and password</span></span>|  
|<span data-ttu-id="f64d0-156">/CLTSVCPASSWORD</span><span class="sxs-lookup"><span data-stu-id="f64d0-156">/CLTSVCPASSWORD</span></span><br /><br /> <span data-ttu-id="f64d0-157">**選擇性**</span><span class="sxs-lookup"><span data-stu-id="f64d0-157">**Optional**</span></span>|<span data-ttu-id="f64d0-158">Distributed Replay 用戶端服務帳戶的密碼。</span><span class="sxs-lookup"><span data-stu-id="f64d0-158">Password for the Distributed Replay client service account.</span></span>|<span data-ttu-id="f64d0-159">檢查帳戶和密碼</span><span class="sxs-lookup"><span data-stu-id="f64d0-159">Checks account and password</span></span>|  
|<span data-ttu-id="f64d0-160">/CLTSTARTUPTYPE</span><span class="sxs-lookup"><span data-stu-id="f64d0-160">/CLTSTARTUPTYPE</span></span><br /><br /> <span data-ttu-id="f64d0-161">**選擇性**</span><span class="sxs-lookup"><span data-stu-id="f64d0-161">**Optional**</span></span>|<span data-ttu-id="f64d0-162">Distributed Replay Client 服務的啟動類型。</span><span class="sxs-lookup"><span data-stu-id="f64d0-162">Startup type for the Distributed Replay client service.</span></span>|<span data-ttu-id="f64d0-163">自動</span><span class="sxs-lookup"><span data-stu-id="f64d0-163">Automatic</span></span><br /><br /> <span data-ttu-id="f64d0-164">已停用</span><span class="sxs-lookup"><span data-stu-id="f64d0-164">Disabled</span></span><br /><br /> <span data-ttu-id="f64d0-165">手動</span><span class="sxs-lookup"><span data-stu-id="f64d0-165">Manual</span></span>|  
|<span data-ttu-id="f64d0-166">/CLTCTLRNAME</span><span class="sxs-lookup"><span data-stu-id="f64d0-166">/CLTCTLRNAME</span></span><br /><br /> <span data-ttu-id="f64d0-167">**選擇性**</span><span class="sxs-lookup"><span data-stu-id="f64d0-167">**Optional**</span></span>|<span data-ttu-id="f64d0-168">用戶端與 Distributed Replay Controller 服務通訊的電腦名稱。</span><span class="sxs-lookup"><span data-stu-id="f64d0-168">The computer name that the client communicates with for the Distributed Replay Controller service.</span></span>||  
|<span data-ttu-id="f64d0-169">/CLTWORKINGDIR</span><span class="sxs-lookup"><span data-stu-id="f64d0-169">/CLTWORKINGDIR</span></span><br /><br /> <span data-ttu-id="f64d0-170">**選擇性**</span><span class="sxs-lookup"><span data-stu-id="f64d0-170">**Optional**</span></span>|<span data-ttu-id="f64d0-171">Distributed Replay Client 服務的工作目錄。</span><span class="sxs-lookup"><span data-stu-id="f64d0-171">The working directory for the Distributed Replay Client service.</span></span>|<span data-ttu-id="f64d0-172">有效路徑</span><span class="sxs-lookup"><span data-stu-id="f64d0-172">Valid path</span></span>|  
|<span data-ttu-id="f64d0-173">/CLTRESULTDIR</span><span class="sxs-lookup"><span data-stu-id="f64d0-173">/CLTRESULTDIR</span></span><br /><br /> <span data-ttu-id="f64d0-174">**選擇性**</span><span class="sxs-lookup"><span data-stu-id="f64d0-174">**Optional**</span></span>|<span data-ttu-id="f64d0-175">Distributed Replay Client 服務的結果目錄。</span><span class="sxs-lookup"><span data-stu-id="f64d0-175">The result directory for the Distributed Replay Client service.</span></span>|<span data-ttu-id="f64d0-176">有效路徑</span><span class="sxs-lookup"><span data-stu-id="f64d0-176">Valid path</span></span>|  
  
### <a name="sample-syntax"></a><span data-ttu-id="f64d0-177">範例語法：</span><span class="sxs-lookup"><span data-stu-id="f64d0-177">Sample Syntax:</span></span>  
 <span data-ttu-id="f64d0-178">**安裝 Distributed Replay Controller 元件**</span><span class="sxs-lookup"><span data-stu-id="f64d0-178">**To install the Distributed Replay controller component**</span></span>  
  
```  
setup /q /ACTION=Install /FEATURES=DREPLAY_CTLR /IAcceptSQLServerLicenseTerms /CTLRUSERS="domain\user1" "domain\user2" /CTLRSVCACCOUNT="domain\svcuser" /CTLRSVCPASSWORD="password" /CTLRSTARTUPTYPE=Automatic  
```  
  
 <span data-ttu-id="f64d0-179">**安裝 Distributed Replay Client 元件**</span><span class="sxs-lookup"><span data-stu-id="f64d0-179">**To install the Distributed Replay client component**</span></span>  
  
```  
setup /q /ACTION=Install /FEATURES=DREPLAY_CLT /IAcceptSQLServerLicenseTerms /CLTSVCACCOUNT="domain\svcuser" /CLTSVCPASSWORD="password" /CLTSTARTUPTYPE=Automatic /CLTCTLRNAME=ControllerMachineName /CLTWORKINGDIR="C:\WorkingDir" /CLTRESULTDIR="C:\ResultDir  
```  
  
  