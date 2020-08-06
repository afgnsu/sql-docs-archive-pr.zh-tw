---
title: SSIS 教學課程：部署封裝 |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- deployment tutorial [Integration Services]
- deploying packages [Integration Services]
- SSIS, tutorials
- Integration Services, tutorials
- deploying packages [Integration Services], installing
- SQL Server Integration Services, tutorials
- walkthroughs [Integration Services]
- deployment utility [Integration Services]
- deploying packages [Integration Services], configurations
ms.assetid: de18468c-cff3-48f4-99ec-6863610e5886
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b6cb9ad6cc0932473ded07554f9f13d57879ccd9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599613"
---
# <a name="ssis-tutorial-deploying-packages"></a><span data-ttu-id="a4971-102">SSIS 教學課程：部署封裝</span><span class="sxs-lookup"><span data-stu-id="a4971-102">SSIS Tutorial: Deploying Packages</span></span>
  [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="a4971-103">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 提供數個工具，可讓您輕鬆地將套件部署到另一部電腦。</span><span class="sxs-lookup"><span data-stu-id="a4971-103">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] provides tools that make it easy to deploy packages to another computer.</span></span> <span data-ttu-id="a4971-104">部署工具也可以用來管理任何相依性，例如封裝所需的組態和檔案。</span><span class="sxs-lookup"><span data-stu-id="a4971-104">The deployment tools also manage any dependencies, such as configurations and files that the package needs.</span></span> <span data-ttu-id="a4971-105">在這個教學課程中，您會學到如何使用這些工具，將封裝及其相依性安裝到目標電腦上。</span><span class="sxs-lookup"><span data-stu-id="a4971-105">In this tutorial, you will learn how to use these tools to install packages and their dependencies on a target computer.</span></span>

 <span data-ttu-id="a4971-106">首先，您會執行一些部署的準備工作。</span><span class="sxs-lookup"><span data-stu-id="a4971-106">First, you will perform tasks to prepare for deployment.</span></span> <span data-ttu-id="a4971-107">您會在 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 中建立一個新的 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 專案，並且將現有的封裝和資料檔加入至該專案中。</span><span class="sxs-lookup"><span data-stu-id="a4971-107">You will create a new [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] and add existing packages and data files to the project.</span></span> <span data-ttu-id="a4971-108">您不需要從頭開始建立新的封裝，而是使用針對這個教學課程所建立的已完成的封裝。</span><span class="sxs-lookup"><span data-stu-id="a4971-108">You will not create any new packages from scratch; instead, you will work only with completed packages that were created just for this tutorial.</span></span> <span data-ttu-id="a4971-109">您在這個教學課程中並不會修改封裝的功能，不過，在您將封裝加入至專案之後，若能在 [ [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師] 中開啟封裝並檢閱各個封裝的內容，可能會很有幫助。</span><span class="sxs-lookup"><span data-stu-id="a4971-109">You will not modify the functionality of the packages in this tutorial; however, after you have added the packages to the project, you might find it useful to open the packages in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer and review the contents of each package.</span></span> <span data-ttu-id="a4971-110">因為您可以藉由檢查封裝，而了解封裝的相依性 (例如記錄檔) 以及封裝的其他有趣功能。</span><span class="sxs-lookup"><span data-stu-id="a4971-110">By examining the packages, you will learn about package dependencies such as log files and about other interesting features of the packages.</span></span>

 <span data-ttu-id="a4971-111">在為部署做準備時，您還要更新封裝以使用組態。</span><span class="sxs-lookup"><span data-stu-id="a4971-111">In preparation for deployment, you will also update the packages to use configurations.</span></span> <span data-ttu-id="a4971-112">組態會使封裝和封裝物件的屬性，在執行階段變成可更新的狀態。</span><span class="sxs-lookup"><span data-stu-id="a4971-112">Configurations make the properties of packages and package objects updatable at run time.</span></span> <span data-ttu-id="a4971-113">在這個教學課程中，您會使用組態來更新記錄檔和文字檔的連接字串，以及封裝所使用之 XML 和 XSD 檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="a4971-113">In this tutorial, you will use configurations to update the connection strings of log and text files and the locations of the XML and XSD files that the package uses.</span></span> <span data-ttu-id="a4971-114">如需詳細資訊，請參閱 [封裝組態](../../2014/integration-services/package-configurations.md) 和 [建立封裝組態](../../2014/integration-services/create-package-configurations.md)。</span><span class="sxs-lookup"><span data-stu-id="a4971-114">For more information, see [Package Configurations](../../2014/integration-services/package-configurations.md) and [Create Package Configurations](../../2014/integration-services/create-package-configurations.md).</span></span>

 <span data-ttu-id="a4971-115">當您確認封裝可以在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中順利執行之後，就要建立用來安裝封裝的部署配套。</span><span class="sxs-lookup"><span data-stu-id="a4971-115">After you have verified that the packages run successfully in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], you will create the deployment bundle to use to install the packages.</span></span> <span data-ttu-id="a4971-116">這個部署配套將會包含您已加入至 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案中的封裝檔案和其他項目、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 自動納入的封裝相依性，以及您所建立的部署公用程式。</span><span class="sxs-lookup"><span data-stu-id="a4971-116">The deployment bundle will consist of the package files and other items that you added to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, the package dependencies that [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] automatically includes, and the deployment utility that you built.</span></span> <span data-ttu-id="a4971-117">如需詳細資訊，請參閱 [建立部署公用程式](../../2014/integration-services/create-a-deployment-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="a4971-117">For more information, see [Create a Deployment Utility](../../2014/integration-services/create-a-deployment-utility.md).</span></span>

 <span data-ttu-id="a4971-118">接下來，您會將部署配套複製到目標電腦上，然後執行「封裝安裝精靈」來安裝封裝和封裝相依性。</span><span class="sxs-lookup"><span data-stu-id="a4971-118">You will then copy the deployment bundle to the target computer and run the Package Installation Wizard to install the packages and package dependencies.</span></span> <span data-ttu-id="a4971-119">封裝將會安裝在 msdb SQL Server 資料庫中，而支援檔案和輔助檔案則會安裝在檔案系統中。</span><span class="sxs-lookup"><span data-stu-id="a4971-119">The packages will be installed in the msdb SQL Server database, and the supporting and ancillary files will be installed in the file system.</span></span> <span data-ttu-id="a4971-120">由於部署的封裝會使用組態，因此您要更新組態使用新值，才能讓封裝在新的環境中順利執行。</span><span class="sxs-lookup"><span data-stu-id="a4971-120">Because the deployed packages use configurations, you will update the configuration to use new values that enable packages to run successfully in the new environment.</span></span>

 <span data-ttu-id="a4971-121">最後，您會使用「執行封裝公用程式」在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中執行封裝。</span><span class="sxs-lookup"><span data-stu-id="a4971-121">Finally, you will run the packages in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] by using the Execute Package Utility.</span></span>

 <span data-ttu-id="a4971-122">這個教學課程的目標是，模擬在實際部署時可能遇到的各種問題的複雜性。</span><span class="sxs-lookup"><span data-stu-id="a4971-122">It is the goal of this tutorial to simulate the complexity of real-life deployment issues that you may encounter.</span></span> <span data-ttu-id="a4971-123">但是，如果您無法將封裝部署到其他電腦上，仍然可以進行這個教學課程，只要將封裝安裝在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]本機執行個體上的 msdb 資料庫中，然後從本機執行個體上的 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 執行封裝就可以了。</span><span class="sxs-lookup"><span data-stu-id="a4971-123">However, if it is not possible for you to deploy the packages to a different computer, you can still do this tutorial by installing the packages in the msdb database on a local instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], and then running the packages from [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] on the same instance.</span></span>

## <a name="what-you-will-learn"></a><span data-ttu-id="a4971-124">學習內容</span><span class="sxs-lookup"><span data-stu-id="a4971-124">What You Will Learn</span></span>
 <span data-ttu-id="a4971-125">若要熟悉中提供的新工具、控制項和功能，最好的方法 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 就是使用它們。</span><span class="sxs-lookup"><span data-stu-id="a4971-125">The best way to become acquainted with the new tools, controls, and features available in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] is to use them.</span></span> <span data-ttu-id="a4971-126">這個教學課程會逐步解說各個步驟，教您建立 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案，然後將封裝和其他必要檔案加入至專案中。</span><span class="sxs-lookup"><span data-stu-id="a4971-126">This tutorial walks you through the steps to create an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project and then add the packages and other necessary files to the project.</span></span> <span data-ttu-id="a4971-127">當專案完成之後，您還要建立部署配套、將部署配套複製到目的地電腦，然後將封裝安裝到目的地電腦上。</span><span class="sxs-lookup"><span data-stu-id="a4971-127">After the project is complete, you will create a deployment bundle, copy the bundle to the destination computer, and then install the packages on the destination computer.</span></span>

## <a name="requirements"></a><span data-ttu-id="a4971-128">需求</span><span class="sxs-lookup"><span data-stu-id="a4971-128">Requirements</span></span>
 <span data-ttu-id="a4971-129">本教學課程的主要物件是已經熟悉基本檔案系統作業，但對提供的新功能有所限制的使用者 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a4971-129">This tutorial is intended for users who are already familiar with fundamental file system operations, but who have limited exposure to the new features available in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="a4971-130">若要進一步瞭解 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 您將在本教學課程中使用的基本概念，您可能會發現，首先要完成下列 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 教學課程：[執行 SQL Server 匯入和匯出嚮導](import-export-data/start-the-sql-server-import-and-export-wizard.md)和[SSIS 教學課程：建立簡單的 ETL 封裝](../integration-services/ssis-how-to-create-an-etl-package.md)。</span><span class="sxs-lookup"><span data-stu-id="a4971-130">To better understand basic [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] concepts that you will put to use in this tutorial, you might find it useful to first complete the following [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] tutorials: [Run the SQL Server Import and Export Wizard](import-export-data/start-the-sql-server-import-and-export-wizard.md) and [SSIS Tutorial: Creating a Simple ETL Package](../integration-services/ssis-how-to-create-an-etl-package.md).</span></span>

 <span data-ttu-id="a4971-131">**來源電腦。**</span><span class="sxs-lookup"><span data-stu-id="a4971-131">**Source computer.**</span></span> <span data-ttu-id="a4971-132">要用來建立部署配套的電腦必須安裝下列元件：</span><span class="sxs-lookup"><span data-stu-id="a4971-132">The computer on which you will create the deployment bundle must have the following components installed:</span></span>

-   <span data-ttu-id="a4971-133">含有 AdventureWorks 資料庫的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a4971-133">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] with the AdventureWorks database.</span></span> <span data-ttu-id="a4971-134">為了加強安全性，依預設，不會安裝範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="a4971-134">To enhance security, the sample databases are not installed by default.</span></span> <span data-ttu-id="a4971-135">您可以從[CodePlex](https://msftdbprodsamples.codeplex.com/releases/view/125550)下載範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="a4971-135">You can download the sample database from [CodePlex](https://msftdbprodsamples.codeplex.com/releases/view/125550).</span></span>

-   <span data-ttu-id="a4971-136">您必須具有在 AdventureWorks 中建立和卸除資料表的權限。</span><span class="sxs-lookup"><span data-stu-id="a4971-136">You must have permission to create and drop tables in AdventureWorks.</span></span>

-   <span data-ttu-id="a4971-137">這個教學課程也需要範例資料、完成的封裝、組態和讀我檔案。</span><span class="sxs-lookup"><span data-stu-id="a4971-137">This tutorial also requires sample data, completed packages, configurations, and a Readme.</span></span> <span data-ttu-id="a4971-138">這些項目的檔案會與範例一起安裝。</span><span class="sxs-lookup"><span data-stu-id="a4971-138">The files for these items are installed together with the samples.</span></span> <span data-ttu-id="a4971-139">如果您找不到範例資料，請回到上面的程序，依所描述來完成安裝。</span><span class="sxs-lookup"><span data-stu-id="a4971-139">If you cannot find the sample data, return to the procedure above and complete installation as described.</span></span>

-   <span data-ttu-id="a4971-140">商業智慧開發環境 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a4971-140">The business intelligence development environment, [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>

 <span data-ttu-id="a4971-141">**目的地電腦。**</span><span class="sxs-lookup"><span data-stu-id="a4971-141">**Destination computer.**</span></span> <span data-ttu-id="a4971-142">要用來部署封裝的電腦必須安裝下列元件：</span><span class="sxs-lookup"><span data-stu-id="a4971-142">The computer to which you deploy packages must have the following components installed:</span></span>

-   <span data-ttu-id="a4971-143">含有 AdventureWorks 資料庫的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a4971-143">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] with the AdventureWorks database.</span></span>

-   [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]<span data-ttu-id="a4971-144">.</span><span class="sxs-lookup"><span data-stu-id="a4971-144">.</span></span>

-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="a4971-145">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a4971-145">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span>

-   <span data-ttu-id="a4971-146">您必須具有在 AdventureWorks 中建立和卸除資料表以及在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中執行封裝的權限。</span><span class="sxs-lookup"><span data-stu-id="a4971-146">You must have permission to create and drop tables in AdventureWorksand to run packages in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>

-   <span data-ttu-id="a4971-147">您必須具有 msdb 系統資料庫中 sysssispackages 資料表的 [讀取] 和 [寫入] 許可權 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a4971-147">You must have read and write permission on the sysssispackages table in the msdb[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] system database.</span></span>

 <span data-ttu-id="a4971-148">如果您計畫將封裝部署到建立部署配套時所使用的同一部電腦，則該部電腦必須同時符合來源電腦和目的地電腦的需求。</span><span class="sxs-lookup"><span data-stu-id="a4971-148">If you plan to deploy packages to the same computer as the one on which you create the deployment bundle, that computer must meet requirements for both the source and destination computers.</span></span>

 <span data-ttu-id="a4971-149">**完成這個教學課程的估計時間：** 2 小時</span><span class="sxs-lookup"><span data-stu-id="a4971-149">**Estimated time to complete this tutorial:** 2 hours</span></span>

## <a name="lessons-in-this-tutorial"></a><span data-ttu-id="a4971-150">本教學課程中的課程</span><span class="sxs-lookup"><span data-stu-id="a4971-150">Lessons in This Tutorial</span></span>
 <span data-ttu-id="a4971-151">[第1課：準備建立部署](../integration-services/lesson-1-preparing-to-create-the-deployment-bundle.md)配套在這一課，您將建立新的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案，並將封裝和其他必要檔案加入至專案，以準備部署 ETL 解決方案。</span><span class="sxs-lookup"><span data-stu-id="a4971-151">[Lesson 1: Preparing to Create the Deployment Bundle](../integration-services/lesson-1-preparing-to-create-the-deployment-bundle.md) In this lesson, you will get ready to deploy an ETL solution by creating a new [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project and adding the packages and other required files to the project.</span></span>

 <span data-ttu-id="a4971-152">[第2課：建立部署](../integration-services/lesson-2-create-the-deployment-bundle-in-ssis.md)配套在這一課，您將建立部署公用程式，並確認部署配套包含必要的檔案。</span><span class="sxs-lookup"><span data-stu-id="a4971-152">[Lesson 2: Creating the Deployment Bundle](../integration-services/lesson-2-create-the-deployment-bundle-in-ssis.md) In this lesson, you will build a deployment utility and verify that the deployment bundle includes the necessary files.</span></span>

 <span data-ttu-id="a4971-153">[第3課：安裝封裝](../integration-services/lesson-3-install-ssis-package.md)在這一課，您會將部署配套複製到目的電腦、安裝封裝，然後執行封裝。</span><span class="sxs-lookup"><span data-stu-id="a4971-153">[Lesson 3: Installing Packages](../integration-services/lesson-3-install-ssis-package.md) In this lesson, you will copy the deployment bundle to the target computer, install the packages, and then run the packages.</span></span>

<span data-ttu-id="a4971-154">![Integration Services 圖示 (小型) ](media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="a4971-154">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="a4971-155">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="a4971-155">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="a4971-156">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="a4971-156">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="a4971-157">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="a4971-157">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>
