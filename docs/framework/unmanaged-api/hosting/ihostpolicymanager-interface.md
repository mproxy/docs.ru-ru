---
title: "Интерфейс IHostPolicyManager"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostPolicyManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostPolicyManager
helpviewer_keywords: IHostPolicyManager interface [.NET Framework hosting]
ms.assetid: 8c4aa124-5e00-46d9-b1e8-57ba6574bb0d
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8f49474f1a75af91ac5296be866914e05732e755
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="ihostpolicymanager-interface"></a><span data-ttu-id="73eab-102">Интерфейс IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="73eab-102">IHostPolicyManager Interface</span></span>
<span data-ttu-id="73eab-103">Предоставляет методы, уведомляющие основное приложение действий, которые выполняет общеязыковой среды выполнения (CLR) в случае возникновения прерываний, время ожидания или сбоев.</span><span class="sxs-lookup"><span data-stu-id="73eab-103">Provides methods that notify the host of the actions the common language runtime (CLR) performs in case of aborts, timeouts, or failures.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="73eab-104">Методы</span><span class="sxs-lookup"><span data-stu-id="73eab-104">Methods</span></span>  
  
|<span data-ttu-id="73eab-105">Метод</span><span class="sxs-lookup"><span data-stu-id="73eab-105">Method</span></span>|<span data-ttu-id="73eab-106">Описание</span><span class="sxs-lookup"><span data-stu-id="73eab-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="73eab-107">Ondefaultaction-метод</span><span class="sxs-lookup"><span data-stu-id="73eab-107">OnDefaultAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ondefaultaction-method.md)|<span data-ttu-id="73eab-108">Уведомляет основное приложение, среда CLR намерена выполнить действие по умолчанию, заданное с помощью вызова [ICLRPolicyManager::SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) в ответ на поток прервать или <xref:System.AppDomain> выгрузки.</span><span class="sxs-lookup"><span data-stu-id="73eab-108">Notifies the host that the CLR is about to take the default action specified by a call to [ICLRPolicyManager::SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) in response to a thread abort or <xref:System.AppDomain> unload.</span></span>|  
|[<span data-ttu-id="73eab-109">OnFailure-метод</span><span class="sxs-lookup"><span data-stu-id="73eab-109">OnFailure Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-onfailure-method.md)|<span data-ttu-id="73eab-110">Уведомляет основное приложение, среда CLR пытается выполнить действие, заданное вызовом [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) в ответ на ошибку выделения и освобождения ресурсов.</span><span class="sxs-lookup"><span data-stu-id="73eab-110">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) in response to a resource allocation or reclamation failure.</span></span>|  
|[<span data-ttu-id="73eab-111">OnTimeout-метод</span><span class="sxs-lookup"><span data-stu-id="73eab-111">OnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ontimeout-method.md)|<span data-ttu-id="73eab-112">Уведомляет основное приложение, среда CLR пытается выполнить действие, заданное вызовом [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) в ответ на время ожидания.</span><span class="sxs-lookup"><span data-stu-id="73eab-112">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) in response to a timeout.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="73eab-113">Требования</span><span class="sxs-lookup"><span data-stu-id="73eab-113">Requirements</span></span>  
 <span data-ttu-id="73eab-114">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73eab-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73eab-115">**Заголовок:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="73eab-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="73eab-116">**Библиотека:** включена как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="73eab-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="73eab-117">**Версии платформы .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73eab-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73eab-118">См. также</span><span class="sxs-lookup"><span data-stu-id="73eab-118">See Also</span></span>  
 [<span data-ttu-id="73eab-119">EClrFailure-перечисление</span><span class="sxs-lookup"><span data-stu-id="73eab-119">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [<span data-ttu-id="73eab-120">EClrOperation-перечисление</span><span class="sxs-lookup"><span data-stu-id="73eab-120">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [<span data-ttu-id="73eab-121">EPolicyAction-перечисление</span><span class="sxs-lookup"><span data-stu-id="73eab-121">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [<span data-ttu-id="73eab-122">Интерфейс ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="73eab-122">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="73eab-123">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="73eab-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)