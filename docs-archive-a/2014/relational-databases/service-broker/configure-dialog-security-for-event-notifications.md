---
title: 設定事件通知的對話安全性 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- event notifications [SQL Server], security
ms.assetid: 12afbc84-2d2a-4452-935e-e1c70e8c53c1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d83bfe63c3a9b24c2be8d08916dd2384c59edc93
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598777"
---
# <a name="configure-dialog-security-for-event-notifications"></a><span data-ttu-id="8d42a-102">設定事件通知的對話安全性</span><span class="sxs-lookup"><span data-stu-id="8d42a-102">Configure Dialog Security for Event Notifications</span></span>
  [!INCLUDE[ssSB](../../includes/sssb-md.md)] <span data-ttu-id="8d42a-103">對話安全性。</span><span class="sxs-lookup"><span data-stu-id="8d42a-103">dialog security should be configured for event notifications that send messages to a service broker on a remote server.</span></span> <span data-ttu-id="8d42a-104">對話方塊安全性必須根據 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 對話方塊完整安全性模型來手動設定。</span><span class="sxs-lookup"><span data-stu-id="8d42a-104">Dialog security must be manually configured according to the [!INCLUDE[ssSB](../../includes/sssb-md.md)] dialog full-security model.</span></span> <span data-ttu-id="8d42a-105">完整安全性模型使傳送到遠端伺服器和自遠端伺服器傳送的訊息得以加密和解密。</span><span class="sxs-lookup"><span data-stu-id="8d42a-105">The full-security model enables encryption and decryption of messages that are sent to and from remote servers.</span></span> <span data-ttu-id="8d42a-106">雖然事件通知是以單一方向傳送，但也會以相反方向傳回其他訊息 (例如錯誤)。</span><span class="sxs-lookup"><span data-stu-id="8d42a-106">Although event notifications are sent in one direction, other messages, such as errors, are also returned in the opposite direction.</span></span>  
  
## <a name="configuring-dialog-security-for-event-notifications"></a><span data-ttu-id="8d42a-107">設定事件通知的對話方塊安全性</span><span class="sxs-lookup"><span data-stu-id="8d42a-107">Configuring Dialog Security for Event Notifications</span></span>  
 <span data-ttu-id="8d42a-108">下列步驟描述實作事件通知對話方塊安全性所需的程序。</span><span class="sxs-lookup"><span data-stu-id="8d42a-108">The process required to implement dialog security for event notification is described in the following steps.</span></span> <span data-ttu-id="8d42a-109">這些步驟包括要對來源伺服器和目標伺服器採取的動作。</span><span class="sxs-lookup"><span data-stu-id="8d42a-109">These steps include actions to take on both the source server and the target server.</span></span> <span data-ttu-id="8d42a-110">來源伺服器就是建立事件通知的伺服器。</span><span class="sxs-lookup"><span data-stu-id="8d42a-110">The source server is the server on which the event notification is being created.</span></span> <span data-ttu-id="8d42a-111">目標伺服器是接收事件通知訊息的伺服器。</span><span class="sxs-lookup"><span data-stu-id="8d42a-111">The target server is the server that receives the event notification message.</span></span> <span data-ttu-id="8d42a-112">在繼續下一步之前，您必須為來源伺服器和目標伺服器完成每一個步驟的動作。</span><span class="sxs-lookup"><span data-stu-id="8d42a-112">You must complete the actions in each step for both the source server and the target server before you continue to the next step.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8d42a-113">您必須以有效起始日和到期日建立所有憑證。</span><span class="sxs-lookup"><span data-stu-id="8d42a-113">All certificates must be created with valid start and expiration dates.</span></span>  
  
 <span data-ttu-id="8d42a-114">**步驟 1：建立 TCP 通訊埠編號和目標服務名稱。**</span><span class="sxs-lookup"><span data-stu-id="8d42a-114">**Step 1: Establish a TCP port number and target service name.**</span></span>  
  
 <span data-ttu-id="8d42a-115">建立來源伺服器和目標伺服器將接收訊息的 TCP 通訊埠。</span><span class="sxs-lookup"><span data-stu-id="8d42a-115">Establish the TCP port on which both the source server and the target server will receive messages.</span></span> <span data-ttu-id="8d42a-116">您也必須決定目標服務的名稱。</span><span class="sxs-lookup"><span data-stu-id="8d42a-116">You must also determine the name of the target service.</span></span>  
  
 <span data-ttu-id="8d42a-117">**步驟 2：為資料庫層級驗證設定加密和憑證共用。**</span><span class="sxs-lookup"><span data-stu-id="8d42a-117">**Step 2: Configure encryption and certificate sharing for database-level authentication.**</span></span>  
  
 <span data-ttu-id="8d42a-118">在來源和目標伺服器上完成下列動作。</span><span class="sxs-lookup"><span data-stu-id="8d42a-118">Complete the following actions on both the source and target servers.</span></span>  
  
|<span data-ttu-id="8d42a-119">來源伺服器</span><span class="sxs-lookup"><span data-stu-id="8d42a-119">Source server</span></span>|<span data-ttu-id="8d42a-120">目標伺服器</span><span class="sxs-lookup"><span data-stu-id="8d42a-120">Target server</span></span>|  
|-------------------|-------------------|  
|<span data-ttu-id="8d42a-121">選擇或建立資料庫來保存事件通知和主要金鑰。</span><span class="sxs-lookup"><span data-stu-id="8d42a-121">Choose or create a database to hold the event notification and master key.</span></span>|<span data-ttu-id="8d42a-122">選擇或建立資料庫來保存主要金鑰。</span><span class="sxs-lookup"><span data-stu-id="8d42a-122">Choose or create a database to hold the master key.</span></span>|  
|<span data-ttu-id="8d42a-123">如果來源資料庫沒有主要金鑰，請 [建立主要金鑰](/sql/t-sql/statements/create-master-key-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="8d42a-123">If no master key exists for the source database, [create a master key](/sql/t-sql/statements/create-master-key-transact-sql).</span></span> <span data-ttu-id="8d42a-124">來源和目標資料庫上必須有主要金鑰才能協助保護其個別憑證。</span><span class="sxs-lookup"><span data-stu-id="8d42a-124">A master key is required on both the source and target databases to help secure their respective certificates.</span></span>|<span data-ttu-id="8d42a-125">如果目標資料庫沒有主要金鑰，請建立主要金鑰。</span><span class="sxs-lookup"><span data-stu-id="8d42a-125">If no master key exists for the target database, create a master key.</span></span>|  
|<span data-ttu-id="8d42a-126">為來源資料庫[建立登入](/sql/t-sql/statements/create-login-transact-sql) 和對應的 [使用者](/sql/t-sql/statements/create-user-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="8d42a-126">[Create a login](/sql/t-sql/statements/create-login-transact-sql) and a corresponding [user](/sql/t-sql/statements/create-user-transact-sql) for the source database.</span></span>|<span data-ttu-id="8d42a-127">為目標資料庫建立登入和對應的使用者。</span><span class="sxs-lookup"><span data-stu-id="8d42a-127">Create a login and a corresponding user for the target database.</span></span>|  
|<span data-ttu-id="8d42a-128">[建立憑證](/sql/t-sql/statements/create-certificate-transact-sql) ，這是來源資料庫的使用者所擁有的憑證。</span><span class="sxs-lookup"><span data-stu-id="8d42a-128">[Create a certificate](/sql/t-sql/statements/create-certificate-transact-sql) that is owned by the user of the source database.</span></span>|<span data-ttu-id="8d42a-129">建立憑證，這是目標資料庫的使用者所擁有的憑證。</span><span class="sxs-lookup"><span data-stu-id="8d42a-129">Create a certificate that is owned by the user of the target database.</span></span>|  
|<span data-ttu-id="8d42a-130">[備份憑證](/sql/t-sql/statements/backup-certificate-transact-sql) 到可供目標伺服器存取的檔案。</span><span class="sxs-lookup"><span data-stu-id="8d42a-130">[Back up the certificate](/sql/t-sql/statements/backup-certificate-transact-sql) to a file that can be accessed by the target server.</span></span>|<span data-ttu-id="8d42a-131">備份憑證到可供來源伺服器存取的檔案。</span><span class="sxs-lookup"><span data-stu-id="8d42a-131">Back up the certificate to a file that can be accessed by the source server.</span></span>|  
|<span data-ttu-id="8d42a-132">[建立使用者](/sql/t-sql/statements/create-user-transact-sql)時，指定目標資料庫的使用者和 WITHOUT LOGIN。</span><span class="sxs-lookup"><span data-stu-id="8d42a-132">[Create a user](/sql/t-sql/statements/create-user-transact-sql), specifying the user of the target database, and WITHOUT LOGIN.</span></span> <span data-ttu-id="8d42a-133">此使用者將擁有要從備份檔案建立的目標資料庫憑證。</span><span class="sxs-lookup"><span data-stu-id="8d42a-133">This user will own the target database certificate to be created from the backup file.</span></span> <span data-ttu-id="8d42a-134">使用者不必對應到登入，因為此使用者唯一的目的是要擁有接下來的步驟 3 所建立的目標資料庫憑證。</span><span class="sxs-lookup"><span data-stu-id="8d42a-134">The user does not have to be mapped to a login, because the only purpose of this user is to own the target database certificate created in step 3 that follows.</span></span>|<span data-ttu-id="8d42a-135">建立使用者時，指定來源資料庫的使用者和 WITHOUT LOGIN。</span><span class="sxs-lookup"><span data-stu-id="8d42a-135">Create a user, specifying the user of the source database, and WITHOUT LOGIN.</span></span> <span data-ttu-id="8d42a-136">此使用者將擁有要從備份檔案建立的來源資料庫憑證。</span><span class="sxs-lookup"><span data-stu-id="8d42a-136">This user will own the source database certificate to be created from the backup file.</span></span> <span data-ttu-id="8d42a-137">使用者不必對應到登入，因為此使用者唯一的目的是要擁有接下來的步驟 3 所建立的來源資料庫憑證。</span><span class="sxs-lookup"><span data-stu-id="8d42a-137">The user does not have to be mapped to a login, because the only purpose of this user is to own the source database certificate created in step 3 that follows.</span></span>|  
  
 <span data-ttu-id="8d42a-138">**步驟 3：為資料庫層級驗證共用憑證和授與權限。**</span><span class="sxs-lookup"><span data-stu-id="8d42a-138">**Step 3: Share certificates and grant permissions for database-level authentication.**</span></span>  
  
 <span data-ttu-id="8d42a-139">在來源和目標伺服器上完成下列動作。</span><span class="sxs-lookup"><span data-stu-id="8d42a-139">Complete the following actions on both the source and target servers.</span></span>  
  
|<span data-ttu-id="8d42a-140">來源伺服器</span><span class="sxs-lookup"><span data-stu-id="8d42a-140">Source server</span></span>|<span data-ttu-id="8d42a-141">目標伺服器</span><span class="sxs-lookup"><span data-stu-id="8d42a-141">Target server</span></span>|  
|-------------------|-------------------|  
|<span data-ttu-id="8d42a-142">從目標憑證的備份檔案[建立憑證](/sql/t-sql/statements/create-certificate-transact-sql) 時，指定目標資料庫使用者作為擁有者。</span><span class="sxs-lookup"><span data-stu-id="8d42a-142">[Create a certificate](/sql/t-sql/statements/create-certificate-transact-sql) from the backup file of the target certificate, specifying the target database user as the owner.</span></span>|<span data-ttu-id="8d42a-143">從來源憑證的備份檔案建立憑證時，指定來源資料庫使用者作為擁有者。</span><span class="sxs-lookup"><span data-stu-id="8d42a-143">Create a certificate from the backup file of the source certificate, specifying the source database user as the owner.</span></span>|  
|<span data-ttu-id="8d42a-144">[授與權限](/sql/t-sql/statements/grant-transact-sql) 來建立來源資料庫使用者的事件通知。</span><span class="sxs-lookup"><span data-stu-id="8d42a-144">[Grant permission](/sql/t-sql/statements/grant-transact-sql) to create the event notification to the source database user.</span></span> <span data-ttu-id="8d42a-145">如需此權限的詳細資訊，請參閱 [CREATE EVENT NOTIFICATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-notification-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="8d42a-145">For more information about this permission, see [CREATE EVENT NOTIFICATION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-notification-transact-sql).</span></span>|<span data-ttu-id="8d42a-146">授與 REFERENCES 權限給現有的事件通知 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 合約上的目標資料庫使用者： `https://schemas.microsoft.com/SQL/Notifications/PostEventNotification`。</span><span class="sxs-lookup"><span data-stu-id="8d42a-146">Grant REFERENCES permission to the target database user on the existing event notifications [!INCLUDE[ssSB](../../includes/sssb-md.md)] contract: `https://schemas.microsoft.com/SQL/Notifications/PostEventNotification`.</span></span>|  
|<span data-ttu-id="8d42a-147">[建立遠端服務繫結](/sql/t-sql/statements/create-remote-service-binding-transact-sql) 至目標服務，並指定目標資料庫使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="8d42a-147">[Create a remote service binding](/sql/t-sql/statements/create-remote-service-binding-transact-sql) to the target service and specify the credentials of the target database user.</span></span> <span data-ttu-id="8d42a-148">遠端服務繫結保證來源資料庫使用者擁有之憑證中的公開金鑰會驗證傳送至目標伺服器的訊息。</span><span class="sxs-lookup"><span data-stu-id="8d42a-148">The remote service binding guarantees that the public key in the certificate owned by the source database user will authenticate messages that are sent to the target server.</span></span>|<span data-ttu-id="8d42a-149">[授與](/sql/t-sql/statements/grant-transact-sql) CREATE QUEUE、CREATE SERVICE 和 CREATE SCHEMA 權限給目標資料庫使用者。</span><span class="sxs-lookup"><span data-stu-id="8d42a-149">[Grant](/sql/t-sql/statements/grant-transact-sql) CREATE QUEUE, CREATE SERVICE, and CREATE SCHEMA permissions to the target database user.</span></span>|  
||<span data-ttu-id="8d42a-150">如果尚未以目標資料庫使用者連接到資料庫，請立刻執行此動作。</span><span class="sxs-lookup"><span data-stu-id="8d42a-150">If not already connected to the database as the target database user, do so now.</span></span>|  
||<span data-ttu-id="8d42a-151">[建立佇列](/sql/t-sql/statements/create-queue-transact-sql) 來接收事件通知訊息，並 [建立服務](/sql/t-sql/statements/create-service-transact-sql) 來傳遞訊息。</span><span class="sxs-lookup"><span data-stu-id="8d42a-151">[Create a queue](/sql/t-sql/statements/create-queue-transact-sql) to receive the event notification messages and [create a service](/sql/t-sql/statements/create-service-transact-sql) to deliver the messages.</span></span>|  
||<span data-ttu-id="8d42a-152">在目標服務上[授與 SEND 權限](/sql/t-sql/statements/grant-transact-sql) 給來源資料庫使用者。</span><span class="sxs-lookup"><span data-stu-id="8d42a-152">[Grant SEND permission](/sql/t-sql/statements/grant-transact-sql) on the target service to the source database user.</span></span>|  
|<span data-ttu-id="8d42a-153">提供來源資料庫的 Service Broker 識別碼給目標伺服器。</span><span class="sxs-lookup"><span data-stu-id="8d42a-153">Provide the service broker identifier of the source database to the target server.</span></span> <span data-ttu-id="8d42a-154">此識別碼可利用查詢 **sys.databases** 目錄檢視的 [service_broker_guid](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) 資料行取得。</span><span class="sxs-lookup"><span data-stu-id="8d42a-154">This identifier can be obtained by querying the **service_broker_guid** column of the [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) catalog view.</span></span> <span data-ttu-id="8d42a-155">若為伺服器層級事件通知，請使用 **msdb**的 Service Broker 識別碼。</span><span class="sxs-lookup"><span data-stu-id="8d42a-155">For a server-level event notification, use the service broker identifier of **msdb**.</span></span>|<span data-ttu-id="8d42a-156">提供目標資料庫的 Service Broker 識別碼給來源伺服器。</span><span class="sxs-lookup"><span data-stu-id="8d42a-156">Provide the service broker identifier of the target database to the source server.</span></span>|  
  
 <span data-ttu-id="8d42a-157">**步驟 4：建立路由及設定伺服器層級驗證。**</span><span class="sxs-lookup"><span data-stu-id="8d42a-157">**Step 4: Create routes and set up server-level authentication.**</span></span>  
  
 <span data-ttu-id="8d42a-158">在來源和目標伺服器上完成下列動作。</span><span class="sxs-lookup"><span data-stu-id="8d42a-158">Complete the following actions on both the source and target servers.</span></span>  
  
|<span data-ttu-id="8d42a-159">來源伺服器</span><span class="sxs-lookup"><span data-stu-id="8d42a-159">Source server</span></span>|<span data-ttu-id="8d42a-160">目標伺服器</span><span class="sxs-lookup"><span data-stu-id="8d42a-160">Target server</span></span>|  
|-------------------|-------------------|  
|<span data-ttu-id="8d42a-161">[建立路由](/sql/t-sql/statements/create-route-transact-sql) 到目標服務，並指定目標資料庫的 Service Broker 識別碼和已同意的 TCP 通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="8d42a-161">[Create a route](/sql/t-sql/statements/create-route-transact-sql) to the target service, and specify the service broker identifier of the target database and the agreed-upon TCP port number.</span></span>|<span data-ttu-id="8d42a-162">建立路由到來源服務，並指定來源資料庫的 Service Broker 識別碼和已同意的 TCP 通訊埠編號。</span><span class="sxs-lookup"><span data-stu-id="8d42a-162">Create a route to the source service, and specify the service broker identifier of the source database and the agreed-upon TCP port number.</span></span> <span data-ttu-id="8d42a-163">若要指定來源服務，請使用下列提供的服務： `https://schemas.microsoft.com/SQL/Notifications/EventNotificationService`。</span><span class="sxs-lookup"><span data-stu-id="8d42a-163">To specify the source service, use the following supplied service: `https://schemas.microsoft.com/SQL/Notifications/EventNotificationService`.</span></span>|  
|<span data-ttu-id="8d42a-164">切換到 **master** 資料庫來設定伺服器層級驗證。</span><span class="sxs-lookup"><span data-stu-id="8d42a-164">Switch to the **master** database to configure server-level authentication.</span></span>|<span data-ttu-id="8d42a-165">切換到 **master** 資料庫來設定伺服器層級驗證。</span><span class="sxs-lookup"><span data-stu-id="8d42a-165">Switch to the **master** database to configure server-level authentication.</span></span>|  
|<span data-ttu-id="8d42a-166">如果 **master** 資料庫沒有主要金鑰，請 [建立主要金鑰](/sql/t-sql/statements/create-master-key-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="8d42a-166">If no master key exists for the **master** database, [create a master key](/sql/t-sql/statements/create-master-key-transact-sql).</span></span>|<span data-ttu-id="8d42a-167">如果 **master** 資料庫沒有主要金鑰，請建立主要金鑰。</span><span class="sxs-lookup"><span data-stu-id="8d42a-167">If no master key exists for the **master** database, create a master key.</span></span>|  
|<span data-ttu-id="8d42a-168">[建立憑證](/sql/t-sql/statements/create-certificate-transact-sql) 來驗證資料庫。</span><span class="sxs-lookup"><span data-stu-id="8d42a-168">[Create a certificate](/sql/t-sql/statements/create-certificate-transact-sql) that authenticates the database.</span></span>|<span data-ttu-id="8d42a-169">建立憑證來驗證資料庫。</span><span class="sxs-lookup"><span data-stu-id="8d42a-169">Create a certificate that authenticates the database.</span></span>|  
|<span data-ttu-id="8d42a-170">[備份憑證](/sql/t-sql/statements/backup-certificate-transact-sql) 到可供目標伺服器存取的檔案。</span><span class="sxs-lookup"><span data-stu-id="8d42a-170">[Back up the certificate](/sql/t-sql/statements/backup-certificate-transact-sql) to a file that can be accessed by the target server.</span></span>|<span data-ttu-id="8d42a-171">備份憑證到可供來源伺服器存取的檔案。</span><span class="sxs-lookup"><span data-stu-id="8d42a-171">Back up the certificate to a file that can be accessed by the source server.</span></span>|  
|<span data-ttu-id="8d42a-172">[建立端點](/sql/t-sql/statements/create-endpoint-transact-sql)，並指定已同意的 TCP 通訊埠編號、FOR SERVICE_BROKER (AUTHENTICATION = CERTIFICATE 憑證名稱  ) 和驗證的憑證名稱。</span><span class="sxs-lookup"><span data-stu-id="8d42a-172">[Create an endpoint](/sql/t-sql/statements/create-endpoint-transact-sql), and specify the agreed-upon TCP port number, FOR SERVICE_BROKER (AUTHENTICATION = CERTIFICATE *certificate_name*), and the name of the authenticating certificate.</span></span>|<span data-ttu-id="8d42a-173">建立端點，並指定已同意的 TCP 通訊埠編號、FOR SERVICE_BROKER (AUTHENTICATION = CERTIFICATE 憑證名稱  ) 和驗證憑證的名稱。</span><span class="sxs-lookup"><span data-stu-id="8d42a-173">Create an endpoint, and specify the agreed-upon TCP port number, FOR SERVICE_BROKER (AUTHENTICATION = CERTIFICATE *certificate_name*), and the name of the authenticating certificate.</span></span>|  
|<span data-ttu-id="8d42a-174">[建立登入](/sql/t-sql/statements/create-login-transact-sql)，並指定目標伺服器的登入。</span><span class="sxs-lookup"><span data-stu-id="8d42a-174">[Create a login](/sql/t-sql/statements/create-login-transact-sql), and specify the login of the target server.</span></span>|<span data-ttu-id="8d42a-175">建立登入，並指定來源伺服器的登入。</span><span class="sxs-lookup"><span data-stu-id="8d42a-175">Create a login, and specify the login of the source server.</span></span>|  
|<span data-ttu-id="8d42a-176">在端點[授與 CONNECT 權限](/sql/t-sql/statements/grant-transact-sql) 給目標驗證器登入。</span><span class="sxs-lookup"><span data-stu-id="8d42a-176">[Grant CONNECT permission](/sql/t-sql/statements/grant-transact-sql) on the endpoint to the target authenticator login.</span></span>|<span data-ttu-id="8d42a-177">在端點授與 CONNECT 權限給來源驗證器登入。</span><span class="sxs-lookup"><span data-stu-id="8d42a-177">Grant CONNECT permission on the endpoint to the source authenticator login.</span></span>|  
|<span data-ttu-id="8d42a-178">[建立使用者](/sql/t-sql/statements/create-user-transact-sql)，並指定目標驗證器登入。</span><span class="sxs-lookup"><span data-stu-id="8d42a-178">[Create a user](/sql/t-sql/statements/create-user-transact-sql), and specify the target authenticator login.</span></span>|<span data-ttu-id="8d42a-179">建立使用者，並指定來源驗證器登入。</span><span class="sxs-lookup"><span data-stu-id="8d42a-179">Create a user, and specify the source authenticator login.</span></span>|  
  
 <span data-ttu-id="8d42a-180">**步驟 5：共用伺服器層級驗證的憑證並建立事件通知。**</span><span class="sxs-lookup"><span data-stu-id="8d42a-180">**Step 5: Share certificates for server-level authentication and create the event notification.**</span></span>  
  
 <span data-ttu-id="8d42a-181">在來源和目標伺服器上完成下列動作。</span><span class="sxs-lookup"><span data-stu-id="8d42a-181">Complete the following actions on both the source and target servers.</span></span>  
  
|<span data-ttu-id="8d42a-182">來源伺服器</span><span class="sxs-lookup"><span data-stu-id="8d42a-182">Source server</span></span>|<span data-ttu-id="8d42a-183">目標伺服器</span><span class="sxs-lookup"><span data-stu-id="8d42a-183">Target server</span></span>|  
|-------------------|-------------------|  
|<span data-ttu-id="8d42a-184">從目標憑證的備份檔案[建立憑證](/sql/t-sql/statements/create-certificate-transact-sql) 時，指定目標驗證器使用者作為擁有者。</span><span class="sxs-lookup"><span data-stu-id="8d42a-184">[Create a certificate](/sql/t-sql/statements/create-certificate-transact-sql) from the backup file of the target certificate, specifying the target authenticator user as the owner.</span></span>|<span data-ttu-id="8d42a-185">從來源憑證的備份檔案建立憑證時，指定來源驗證器使用者作為擁有者。</span><span class="sxs-lookup"><span data-stu-id="8d42a-185">Create a certificate from the backup file of the source certificate, specifying the source authenticator user as the owner.</span></span>|  
|<span data-ttu-id="8d42a-186">切換到要建立事件通知的來源資料庫，如果您尚未以來源資料庫使用者連接，請立刻執行此動作。</span><span class="sxs-lookup"><span data-stu-id="8d42a-186">Switch to the source database on which to create the event notification, and if you are not already connected as the source database user, do so now.</span></span>|<span data-ttu-id="8d42a-187">切換到目標資料庫來接收事件通知訊息。</span><span class="sxs-lookup"><span data-stu-id="8d42a-187">Switch to the target database to receive event notification messages.</span></span>|  
|<span data-ttu-id="8d42a-188">[建立事件通知](/sql/t-sql/statements/create-event-notification-transact-sql)，並指定 Broker Service 和目標資料庫的識別碼。</span><span class="sxs-lookup"><span data-stu-id="8d42a-188">[Create the event notification](/sql/t-sql/statements/create-event-notification-transact-sql), and specify the broker service and identifier of the target database.</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="8d42a-189">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d42a-189">See Also</span></span>  
 <span data-ttu-id="8d42a-190">[GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8d42a-190">[GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql) </span></span>  
 <span data-ttu-id="8d42a-191">[BACKUP CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-certificate-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8d42a-191">[BACKUP CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-certificate-transact-sql) </span></span>  
 <span data-ttu-id="8d42a-192">[sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8d42a-192">[sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span></span>  
 <span data-ttu-id="8d42a-193">[加密階層](../security/encryption/encryption-hierarchy.md) </span><span class="sxs-lookup"><span data-stu-id="8d42a-193">[Encryption Hierarchy](../security/encryption/encryption-hierarchy.md) </span></span>  
 <span data-ttu-id="8d42a-194">[實作事件通知](event-notifications.md) </span><span class="sxs-lookup"><span data-stu-id="8d42a-194">[Implement Event Notifications](event-notifications.md) </span></span>  
 <span data-ttu-id="8d42a-195">[CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8d42a-195">[CREATE MASTER KEY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-master-key-transact-sql) </span></span>  
 <span data-ttu-id="8d42a-196">[CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8d42a-196">[CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql) </span></span>  
 <span data-ttu-id="8d42a-197">[CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8d42a-197">[CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql) </span></span>  
 <span data-ttu-id="8d42a-198">[CREATE CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8d42a-198">[CREATE CERTIFICATE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-certificate-transact-sql) </span></span>  
 <span data-ttu-id="8d42a-199">[CREATE REMOTE SERVICE BINDING &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-remote-service-binding-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8d42a-199">[CREATE REMOTE SERVICE BINDING &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-remote-service-binding-transact-sql) </span></span>  
 <span data-ttu-id="8d42a-200">[GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8d42a-200">[GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql) </span></span>  
 <span data-ttu-id="8d42a-201">[CREATE ROUTE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-route-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8d42a-201">[CREATE ROUTE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-route-transact-sql) </span></span>  
 <span data-ttu-id="8d42a-202">[CREATE QUEUE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-queue-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8d42a-202">[CREATE QUEUE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-queue-transact-sql) </span></span>  
 <span data-ttu-id="8d42a-203">[CREATE SERVICE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-service-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8d42a-203">[CREATE SERVICE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-service-transact-sql) </span></span>  
 <span data-ttu-id="8d42a-204">[CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8d42a-204">[CREATE ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql) </span></span>  
 [<span data-ttu-id="8d42a-205">CREATE EVENT NOTIFICATION &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8d42a-205">CREATE EVENT NOTIFICATION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-event-notification-transact-sql)  
  
  