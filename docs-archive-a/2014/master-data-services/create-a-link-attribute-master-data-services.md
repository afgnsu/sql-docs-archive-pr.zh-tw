---
title: 建立連結屬性 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [Master Data Services], creating link attributes
- creating link attributes [Master Data Services]
ms.assetid: e6658e9c-5b08-4b8d-b556-17ec2dd041d2
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 4770d7904371c10dc6720e8d3d7f28ca797d9b80
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606959"
---
# <a name="create-a-link-attribute-master-data-services"></a><span data-ttu-id="fe057-102">建立連結屬性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="fe057-102">Create a Link Attribute (Master Data Services)</span></span>
  <span data-ttu-id="fe057-103">當您想要讓使用者輸入超連結作為屬性值 (例如 `http://www.contoso.com`) 時，可以在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 中建立連結屬性。</span><span class="sxs-lookup"><span data-stu-id="fe057-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create a link attribute when you want users to enter a hyperlink as an attribute value, such as `http://www.contoso.com`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fe057-104">當使用者輸入連結屬性的值時，字串開頭必須為 **http://** ，否則將會顯示一個錯誤。</span><span class="sxs-lookup"><span data-stu-id="fe057-104">When users enter a value for a link attribute, the string must begin with **http://** or an error will be displayed.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="fe057-105">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="fe057-105">Prerequisites</span></span>  
 <span data-ttu-id="fe057-106">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="fe057-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="fe057-107">您必須擁有存取 **[系統管理]** 功能區域的權限。</span><span class="sxs-lookup"><span data-stu-id="fe057-107">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="fe057-108">您必須是模型管理員。</span><span class="sxs-lookup"><span data-stu-id="fe057-108">You must be a model administrator.</span></span> <span data-ttu-id="fe057-109">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="fe057-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="fe057-110">建立屬性的實體必須存在。</span><span class="sxs-lookup"><span data-stu-id="fe057-110">An entity must exist to create the attribute for.</span></span> <span data-ttu-id="fe057-111">如需詳細資訊，請參閱[建立實體 &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="fe057-111">For more information, see [Create an Entity &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md).</span></span>  
  
### <a name="to-create-a-link-attribute"></a><span data-ttu-id="fe057-112">若要建立連結屬性</span><span class="sxs-lookup"><span data-stu-id="fe057-112">To create a link attribute</span></span>  
  
1.  <span data-ttu-id="fe057-113">在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[系統管理]**。</span><span class="sxs-lookup"><span data-stu-id="fe057-113">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="fe057-114">在 **[模型檢視]** 頁面上，從功能表列指向 **[管理]** ，然後按一下 **[實體]**。</span><span class="sxs-lookup"><span data-stu-id="fe057-114">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="fe057-115">在 **[實體維護]** 頁面上，選取 **[模型]** 清單中的模型。</span><span class="sxs-lookup"><span data-stu-id="fe057-115">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="fe057-116">針對要建立屬性的實體選取資料列。</span><span class="sxs-lookup"><span data-stu-id="fe057-116">Select the row for the entity that you want to create an attribute for.</span></span>  
  
5.  <span data-ttu-id="fe057-117">按一下 **[編輯選取的實體]**。</span><span class="sxs-lookup"><span data-stu-id="fe057-117">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="fe057-118">在 **[編輯實體]** 頁面上：</span><span class="sxs-lookup"><span data-stu-id="fe057-118">On the **Edit Entity** page:</span></span>  
  
    -   <span data-ttu-id="fe057-119">如果是分葉成員的屬性，則按一下 **[分葉成員屬性]** 窗格中的 **[加入分葉屬性]**。</span><span class="sxs-lookup"><span data-stu-id="fe057-119">If the attribute is for leaf members, in the **Leaf member attributes** pane, click **Add leaf attribute**.</span></span>  
  
    -   <span data-ttu-id="fe057-120">如果是合併成員的屬性，則按一下 **[合併成員屬性]** 窗格中的 **[加入合併屬性]**。</span><span class="sxs-lookup"><span data-stu-id="fe057-120">If the attribute is for consolidated members, in the **Consolidated member attributes** pane, click **Add consolidated attribute**.</span></span>  
  
    -   <span data-ttu-id="fe057-121">如果是集合的屬性，則按一下 **[集合屬性]** 窗格中的 **[加入集合屬性]**。</span><span class="sxs-lookup"><span data-stu-id="fe057-121">If the attribute is for collections, in the **Collection attributes** pane, click **Add collection attribute**.</span></span>  
  
7.  <span data-ttu-id="fe057-122">選取 **[加入屬性]** 頁面上的 **[自由格式]** 選項。</span><span class="sxs-lookup"><span data-stu-id="fe057-122">On the **Add Attribute** page, select the **Free-form** option.</span></span>  
  
8.  <span data-ttu-id="fe057-123">在 **[名稱]** 方塊中，輸入屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="fe057-123">In the **Name** box, type a name for the attribute.</span></span> <span data-ttu-id="fe057-124">如需不應當做屬性名稱使用的字組清單，請參閱[保留字 &#40;Master Data Services&#41;](../../2014/master-data-services/reserved-words-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="fe057-124">For a list of words that should not be used as attribute names, see [Reserved Words &#40;Master Data Services&#41;](../../2014/master-data-services/reserved-words-master-data-services.md).</span></span>  
  
9. <span data-ttu-id="fe057-125">在 **[顯示像素寬度]** 方塊中，輸入要在 **[總管]** 方格中顯示的屬性資料行寬度。</span><span class="sxs-lookup"><span data-stu-id="fe057-125">In the **Display pixel width** box, type the width of the attribute column to be displayed in the **Explorer** grid.</span></span>  
  
10. <span data-ttu-id="fe057-126">從 [資料類型]\*\*\*\* 清單中，選取 [連結]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fe057-126">From the **Data type** list, select **Link**.</span></span>  
  
11. <span data-ttu-id="fe057-127">在 [長度]\*\*\*\* 方塊中，輸入允許的最大字元數。</span><span class="sxs-lookup"><span data-stu-id="fe057-127">In the **Length** box, type the maximum number of characters allowed.</span></span>  
  
12. <span data-ttu-id="fe057-128">(選擇性) 選取 **[啟用變更追蹤]** 以追蹤屬性群組的變更。</span><span class="sxs-lookup"><span data-stu-id="fe057-128">Optionally, select **Enable change tracking** to track changes to groups of attributes.</span></span> <span data-ttu-id="fe057-129">如需詳細資訊，請參閱[將屬性加入至變更追蹤群組 &#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="fe057-129">For more information, see [Add Attributes to a Change Tracking Group &#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md).</span></span>  
  
13. <span data-ttu-id="fe057-130">按一下 **[儲存屬性]**。</span><span class="sxs-lookup"><span data-stu-id="fe057-130">Click **Save attribute**.</span></span>  
  
14. <span data-ttu-id="fe057-131">按一下 **[實體維護]** 頁面上的 **[儲存實體]**。</span><span class="sxs-lookup"><span data-stu-id="fe057-131">On the **Entity Maintenance** page, click **Save entity**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe057-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fe057-132">See Also</span></span>  
 <span data-ttu-id="fe057-133">[Master Data Services &#40;的屬性&#41;](../../2014/master-data-services/attributes-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="fe057-133">[Attributes &#40;Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md) </span></span>  
 <span data-ttu-id="fe057-134">[變更屬性名稱 &#40;Master Data Services&#41;](change-an-attribute-name-and-data-type-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="fe057-134">[Change an Attribute Name &#40;Master Data Services&#41;](change-an-attribute-name-and-data-type-master-data-services.md) </span></span>  
 <span data-ttu-id="fe057-135">[建立以網域為基礎的屬性 &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="fe057-135">[Create a Domain-Based Attribute &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md) </span></span>  
 [<span data-ttu-id="fe057-136">建立檔案屬性 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="fe057-136">Create a File Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-file-attribute-master-data-services.md)  
  
  