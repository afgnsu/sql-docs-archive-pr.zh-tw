---
title: MSSQL_ENG021331 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021331 error
ms.assetid: 9acd75d9-fda1-44cd-ba17-20295ad53ea0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: eb14b467e9d082f396bc733d746e15aedde002a8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594496"
---
# <a name="mssql_eng021331"></a><span data-ttu-id="8840d-102">MSSQL_ENG021331</span><span class="sxs-lookup"><span data-stu-id="8840d-102">MSSQL_ENG021331</span></span>
    
## <a name="message-details"></a><span data-ttu-id="8840d-103">訊息詳細資料</span><span class="sxs-lookup"><span data-stu-id="8840d-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8840d-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="8840d-104">Product Name</span></span>|<span data-ttu-id="8840d-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="8840d-105">SQL Server</span></span>|  
|<span data-ttu-id="8840d-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="8840d-106">Event ID</span></span>|<span data-ttu-id="8840d-107">21331</span><span class="sxs-lookup"><span data-stu-id="8840d-107">21331</span></span>|  
|<span data-ttu-id="8840d-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="8840d-108">Event Source</span></span>|<span data-ttu-id="8840d-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="8840d-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="8840d-110">元件</span><span class="sxs-lookup"><span data-stu-id="8840d-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="8840d-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="8840d-111">Symbolic Name</span></span>||  
|<span data-ttu-id="8840d-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="8840d-112">Message Text</span></span>|<span data-ttu-id="8840d-113">無法將使用者指令碼檔案複製到散發者。(%ls)</span><span class="sxs-lookup"><span data-stu-id="8840d-113">Failed to copy user script file to the Distributor.(%ls)</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8840d-114">說明</span><span class="sxs-lookup"><span data-stu-id="8840d-114">Explanation</span></span>  
 <span data-ttu-id="8840d-115">當手動初始化訂閱，且由複寫產生或在複寫命令中指定的指令碼無法儲存至指定目錄時，可能會出現此錯誤。</span><span class="sxs-lookup"><span data-stu-id="8840d-115">This error can occur when a subscription is initialized manually, and the scripts generated by replication, or specified in a replication command, cannot be saved to the specified directory.</span></span> <span data-ttu-id="8840d-116">錯誤可能是權限問題所造成：當訂閱沒有使用快照集初始化，在發行者端執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務的帳戶，就必須要有散發者端之快照集資料夾的寫入權限。</span><span class="sxs-lookup"><span data-stu-id="8840d-116">The error can be caused by a permissions issue: when a subscription is initialized without using a snapshot, the account under which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service runs at the Publisher must have write permissions on the snapshot folder at the Distributor.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8840d-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="8840d-117">User Action</span></span>  
 <span data-ttu-id="8840d-118">請確定指定的快照集資料夾路徑正確，而且在發行者端執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務的帳戶具有足夠的權限。</span><span class="sxs-lookup"><span data-stu-id="8840d-118">Ensure that the correct path has been specified for the snapshot folder and that the account under which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service runs at the Publisher has sufficient permissions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8840d-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8840d-119">See Also</span></span>  
 <span data-ttu-id="8840d-120">[指定預設快照集位置](snapshot-options.md#snapshot-folder-locations) </span><span class="sxs-lookup"><span data-stu-id="8840d-120">[Specify the Default Snapshot Location](snapshot-options.md#snapshot-folder-locations) </span></span>  
 <span data-ttu-id="8840d-121">[錯誤和事件參考 &#40;複寫&#41;](errors-and-events-reference-replication.md) </span><span class="sxs-lookup"><span data-stu-id="8840d-121">[Errors and Events Reference &#40;Replication&#41;](errors-and-events-reference-replication.md) </span></span>  
 [<span data-ttu-id="8840d-122">不使用快照集初始化交易式訂閱</span><span class="sxs-lookup"><span data-stu-id="8840d-122">Initialize a Transactional Subscription Without a Snapshot</span></span>](initialize-a-transactional-subscription-without-a-snapshot.md)  
  
  