---
title: 指定解決方案部署的配置設定 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services Deployment Wizard, configuration settings
- input files [Analysis Services]
- configuration options [Analysis Services]
- Analysis Services deployments, configuration settings
- deploying [Analysis Services], configuration settings
ms.assetid: 953814a3-85ef-40cc-b46a-d532aa7a6569
author: minewiskan
ms.author: owend
ms.openlocfilehash: 83b08ce2b6296a5098c1b21a3afa443668c481a1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594752"
---
# <a name="specifying-configuration-settings-for-solution-deployment"></a><span data-ttu-id="b5ae4-102">指定方案部署的組態設定</span><span class="sxs-lookup"><span data-stu-id="b5ae4-102">Specifying Configuration Settings for Solution Deployment</span></span>
  <span data-ttu-id="b5ae4-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]部署嚮導會從 .configsettings 檔案讀取您在部署腳本中使用的資料分割和角色部署選項 \<*project name*> 。</span><span class="sxs-lookup"><span data-stu-id="b5ae4-103">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard reads the partition and role deployment options that you use in the deployment script from the \<*project name*>.configsettings file.</span></span> [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]<span data-ttu-id="b5ae4-104">當您建立專案時，會建立這個檔案 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="b5ae4-104">creates this file when you build the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span> [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]<span data-ttu-id="b5ae4-105">會使用目前專案的設定值來建立 .configsettings 檔案 \<*project name*> 。</span><span class="sxs-lookup"><span data-stu-id="b5ae4-105">uses the configuration settings of the current project to create the \<*project name*>.configsettings file.</span></span>  
  
## <a name="reviewing-the-configuration-settings-for-deployment"></a><span data-ttu-id="b5ae4-106">檢閱部署的組態設定</span><span class="sxs-lookup"><span data-stu-id="b5ae4-106">Reviewing the Configuration Settings for Deployment</span></span>  
 <span data-ttu-id="b5ae4-107">以下是儲存在 .configsettings 檔案中的設定 \<*project name*> ：</span><span class="sxs-lookup"><span data-stu-id="b5ae4-107">The following are the configuration settings stored in the \<*project name*>.configsettings file:</span></span>  
  
-   <span data-ttu-id="b5ae4-108">**資料來源連接字串** ：依據 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案中指定的值，每個資料來源都有連接字串。</span><span class="sxs-lookup"><span data-stu-id="b5ae4-108">**Data Source Connection Strings** These are the connection strings for each data source based on the values specified in the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project.</span></span> <span data-ttu-id="b5ae4-109">在這個檔案中儲存連接字串的其餘部分之前，一定會從字串中移除使用者識別碼和密碼。</span><span class="sxs-lookup"><span data-stu-id="b5ae4-109">The user id and password are always removed from the connection string before the remainder of the string is stored in this file.</span></span> <span data-ttu-id="b5ae4-110">不過，如果「部署精靈」直接部署至 Analysis Services 執行個體，您就可以在精靈中加入適當的使用者識別碼和密碼資訊，以便成功處理部署資料庫。</span><span class="sxs-lookup"><span data-stu-id="b5ae4-110">However, if the Deployment Wizard is deploying directly to an Analysis Services instance, you can add the appropriate user id and password information within the wizard to enable a successful processing of the deployment database.</span></span> <span data-ttu-id="b5ae4-111">如果「部署精靈」有儲存指令碼，這項連接資訊將不會儲存在部署指令碼本身內。</span><span class="sxs-lookup"><span data-stu-id="b5ae4-111">This connection information will not be stored in the deployment script itself if one is saved by the Deployment Wizard.</span></span>  
  
-   <span data-ttu-id="b5ae4-112">**模擬帳戶** ：此設定會指定 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 在每個資料來源中用來執行陳述式的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="b5ae4-112">**Impersonation Accounts** This setting specifies the user name that [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] uses to run statements in each data source.</span></span> <span data-ttu-id="b5ae4-113">如果沒有指定模擬帳戶， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會使用其登入帳戶來執行陳述式。</span><span class="sxs-lookup"><span data-stu-id="b5ae4-113">If no impersonation account is specified, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] uses its logon account to run statements.</span></span> <span data-ttu-id="b5ae4-114">如果直接在資料來源中對 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 登入帳戶授與使用權限，則 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體之所有資料庫中的所有資料庫管理員，都有透過登入帳戶存取資料來源的權限。</span><span class="sxs-lookup"><span data-stu-id="b5ae4-114">If the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] logon account is granted permissions directly in the data source, all database administrators in all databases in the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance have access to the data source through the logon account.</span></span> <span data-ttu-id="b5ae4-115">如果指定了使用者帳戶和密碼，則在這個檔案中儲存模擬資訊之前，一定會移除這項資訊。</span><span class="sxs-lookup"><span data-stu-id="b5ae4-115">If a user account and password is specified, this information is always removed before the impersonation information is stored in this file.</span></span> <span data-ttu-id="b5ae4-116">不過，如果「部署精靈」直接部署至 Analysis Services 執行個體，您就可以在精靈中加入適當的使用者識別碼和密碼資訊，以便成功處理部署資料庫。</span><span class="sxs-lookup"><span data-stu-id="b5ae4-116">However, if the Deployment Wizard is deploying directly to an Analysis Services instance, you can add the appropriate user id and password information within the wizard to enable a successful processing of the deployment database.</span></span> <span data-ttu-id="b5ae4-117">如果「部署精靈」有儲存指令碼，這項模擬資訊將不會儲存在部署指令碼本身內。</span><span class="sxs-lookup"><span data-stu-id="b5ae4-117">This impersonation information will not be stored in the deployment script itself if one is saved by the Deployment Wizard.</span></span>  
  
-   <span data-ttu-id="b5ae4-118">**索引鍵錯誤記錄檔** ：此設定會指定資料庫中每個 Cube、量值群組、資料分割以及維度之索引鍵錯誤記錄檔的檔案名稱與路徑。</span><span class="sxs-lookup"><span data-stu-id="b5ae4-118">**Key Error Log Files** This setting specifies the file name and path of the key error log file for each cube, measure group, partition, and dimension in the database.</span></span>  
  
-   <span data-ttu-id="b5ae4-119">**儲存位置** ：此設定會指定資料庫中每個 Cube、量值群組以及資料分割的儲存位置。</span><span class="sxs-lookup"><span data-stu-id="b5ae4-119">**Storage Locations** This setting specifies the storage location for each cube, measure group, and partition in the database.</span></span> <span data-ttu-id="b5ae4-120">如果沒有為物件提供任何值，「 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 部署精靈」就會使用物件的預設位置。</span><span class="sxs-lookup"><span data-stu-id="b5ae4-120">If no value is provided for an object, the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard uses the default location for the object.</span></span> <span data-ttu-id="b5ae4-121">例如，資料分割使用量值群組的位置、量值群組使用 Cube 的位置、而 Cube 使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體上之物件的預設位置。</span><span class="sxs-lookup"><span data-stu-id="b5ae4-121">For example, partitions use the location for the measure group, measure groups use the location for the cube, and cubes use the default location for objects on the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="b5ae4-122">此儲存位置可以是本機或通用命名慣例 (UNC) 路徑。</span><span class="sxs-lookup"><span data-stu-id="b5ae4-122">The storage location can be a local or a Universal Naming Convention (UNC) path.</span></span>  
  
-   <span data-ttu-id="b5ae4-123">**報表伺服器** ：此設定會指定資料庫中內，每個 Cube 中定義之每個報表動作的報表伺服器和資料夾位置。</span><span class="sxs-lookup"><span data-stu-id="b5ae4-123">**Report Server** This setting specifies the report server and folder location for each report action defined in each cube in the database.</span></span>  
  
## <a name="modifying-the-configuration-settings-for-deployment"></a><span data-ttu-id="b5ae4-124">修改部署的組態設定</span><span class="sxs-lookup"><span data-stu-id="b5ae4-124">Modifying the Configuration Settings for Deployment</span></span>  
 <span data-ttu-id="b5ae4-125">在某些情況下，您可能需要 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 使用不同于 .configsettings 檔案中所儲存的設定來部署 \<*project name*> 專案。</span><span class="sxs-lookup"><span data-stu-id="b5ae4-125">In some cases, you may need to deploy the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project using different configuration settings than those stored in the \<*project name*>.configsettings file.</span></span> <span data-ttu-id="b5ae4-126">例如，您可能需要變更一個或多個資料來源的連接字串，或為特定的資料分割或量值群組指定儲存位置。</span><span class="sxs-lookup"><span data-stu-id="b5ae4-126">For example, you may want to change the connection string to one or more data sources, or specify storage locations for specific partitions or measure groups.</span></span>  
  
 <span data-ttu-id="b5ae4-127">若要在專案中修改資料分割和角色的部署 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，您必須在 .configsettings 檔案中變更這 \<*project name*> 項資訊，如以下程式所述。</span><span class="sxs-lookup"><span data-stu-id="b5ae4-127">To modify the deployment of partitions and roles in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project, you must change this information within the \<*project name*>.configsettings file, as described in the procedure below.</span></span> <span data-ttu-id="b5ae4-128">您無法變更專案內的資料分割和角色設定，因為中的 [ *\<project name>* **屬性頁面**] 對話方塊 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 並未顯示這些選項。</span><span class="sxs-lookup"><span data-stu-id="b5ae4-128">You cannot change the partition and roles settings within the project because the *\<project name>* **Properties Pages** dialog box in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] does not display these options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b5ae4-129">組態設定可以套用至所有物件，或僅套用至新建立的物件。</span><span class="sxs-lookup"><span data-stu-id="b5ae4-129">Configuration settings can apply to all objects or only to newly created objects.</span></span> <span data-ttu-id="b5ae4-130">唯有將其他物件部署到先前部署的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫，而且不想要覆寫現有的物件時，才會將組態設定套用至新建立的物件。</span><span class="sxs-lookup"><span data-stu-id="b5ae4-130">Apply configuration settings to newly created objects only when you are deploying additional objects to a previously deployed [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database and do not want to overwrite existing objects.</span></span> <span data-ttu-id="b5ae4-131">若要指定設定是否要套用至所有物件，或僅套用至新建立的設定，請在 d 檔案中設定此選項 \<*project name*> 。</span><span class="sxs-lookup"><span data-stu-id="b5ae4-131">To specify whether configuration settings apply to all objects or only to newly created ones, set this option in the \<*project name*>.deploymentoptions file.</span></span> <span data-ttu-id="b5ae4-132">如需詳細資訊，請參閱 [指定資料分割和角色部署選項](deployment-script-files-partition-and-role-deployment-options.md)。</span><span class="sxs-lookup"><span data-stu-id="b5ae4-132">For more information, see [Specifying Partition and Role Deployment Options](deployment-script-files-partition-and-role-deployment-options.md).</span></span>  
  
#### <a name="to-change-configuration-settings-after-the-input-files-have-been-generated"></a><span data-ttu-id="b5ae4-133">在已產生輸入檔之後，變更組態設定</span><span class="sxs-lookup"><span data-stu-id="b5ae4-133">To change configuration settings after the input files have been generated</span></span>  
  
-   <span data-ttu-id="b5ae4-134">以互動方式執行 [[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 部署精靈]，並在 [組態設定]\*\*\*\* 頁面上，指定正在部署之物件的組態設定。</span><span class="sxs-lookup"><span data-stu-id="b5ae4-134">Run the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard interactively, and on the **Configuration Settings** page, specify the configuration setting for the objects being deployed.</span></span>  
  
     <span data-ttu-id="b5ae4-135">-或-</span><span class="sxs-lookup"><span data-stu-id="b5ae4-135">-or-</span></span>  
  
-   <span data-ttu-id="b5ae4-136">在命令提示字元下執行 [ [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 部署精靈]，並將精靈設定為以回應檔案模式執行。</span><span class="sxs-lookup"><span data-stu-id="b5ae4-136">Run the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Deployment Wizard at the command prompt and set the wizard to run in answer file mode.</span></span> <span data-ttu-id="b5ae4-137">如需回應檔案模式的詳細資訊，請參閱 [執行 Analysis Services 部署精靈](running-the-analysis-services-deployment-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="b5ae4-137">For more information about answer file mode, see [Running the Analysis Services Deployment Wizard](running-the-analysis-services-deployment-wizard.md).</span></span>  
  
     <span data-ttu-id="b5ae4-138">-或-</span><span class="sxs-lookup"><span data-stu-id="b5ae4-138">-or-</span></span>  
  
-   <span data-ttu-id="b5ae4-139">\<*project name*>使用任何文字編輯器來修改 .configsettings 檔案。</span><span class="sxs-lookup"><span data-stu-id="b5ae4-139">Modify the \<*project name*>.configsettings file by using any text editor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5ae4-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b5ae4-140">See Also</span></span>  
 <span data-ttu-id="b5ae4-141">[指定安裝目標](deployment-script-files-specifying-the-installation-target.md) </span><span class="sxs-lookup"><span data-stu-id="b5ae4-141">[Specifying the Installation Target](deployment-script-files-specifying-the-installation-target.md) </span></span>  
 <span data-ttu-id="b5ae4-142">[指定資料分割和角色部署選項](deployment-script-files-partition-and-role-deployment-options.md) </span><span class="sxs-lookup"><span data-stu-id="b5ae4-142">[Specifying Partition and Role Deployment Options](deployment-script-files-partition-and-role-deployment-options.md) </span></span>  
 [<span data-ttu-id="b5ae4-143">指定處理選項</span><span class="sxs-lookup"><span data-stu-id="b5ae4-143">Specifying Processing Options</span></span>](deployment-script-files-specifying-processing-options.md)  
  
  