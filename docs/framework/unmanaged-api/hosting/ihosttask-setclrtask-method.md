---
title: "Метод IHostTask::SetCLRTask"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTask.SetCLRTask
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTask::SetCLRTask
helpviewer_keywords:
- SetCLRTask method [.NET Framework hosting]
- IHostTask::SetCLRTask method [.NET Framework hosting]
ms.assetid: e9d39c80-41a1-49e7-bb5e-ea3433bfb5d7
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 54706b1c3a6ea1864137e2eca135fa6bd883b345
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttasksetclrtask-method"></a><span data-ttu-id="7d41a-102">Метод IHostTask::SetCLRTask</span><span class="sxs-lookup"><span data-stu-id="7d41a-102">IHostTask::SetCLRTask Method</span></span>
<span data-ttu-id="7d41a-103">Связывает `ICLRTask` экземпляра с текущим [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) экземпляра.</span><span class="sxs-lookup"><span data-stu-id="7d41a-103">Associates an `ICLRTask` instance with the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d41a-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7d41a-104">Syntax</span></span>  
  
```  
HRESULT SetCLRTask (  
    [in] ICLRTask *pCLRTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7d41a-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="7d41a-105">Parameters</span></span>  
 `pCLRTask`  
 <span data-ttu-id="7d41a-106">[in] Указатель интерфейса `ICLRTask` экземпляр должен иметь связанный с текущим `IHostTask` экземпляра.</span><span class="sxs-lookup"><span data-stu-id="7d41a-106">[in] An interface pointer to the `ICLRTask` instance to be associated with the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7d41a-107">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="7d41a-107">Return Value</span></span>  
  
|<span data-ttu-id="7d41a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7d41a-108">HRESULT</span></span>|<span data-ttu-id="7d41a-109">Описание</span><span class="sxs-lookup"><span data-stu-id="7d41a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7d41a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7d41a-110">S_OK</span></span>|<span data-ttu-id="7d41a-111">`SetCLRTask`успешно возвращен.</span><span class="sxs-lookup"><span data-stu-id="7d41a-111">`SetCLRTask` returned successfully.</span></span>|  
|<span data-ttu-id="7d41a-112">ЗНАЧЕНИЕ HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7d41a-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7d41a-113">Общеязыковая среда выполнения (CLR) не был загружен в процесс или находится в состоянии, в котором не может выполнять управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="7d41a-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7d41a-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7d41a-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7d41a-115">Истекло время ожидания вызова.</span><span class="sxs-lookup"><span data-stu-id="7d41a-115">The call timed out.</span></span>|  
|<span data-ttu-id="7d41a-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7d41a-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7d41a-117">Вызывающий объект не является владельцем блокировки.</span><span class="sxs-lookup"><span data-stu-id="7d41a-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7d41a-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7d41a-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7d41a-119">Событие было отменено заблокированный поток или ожидал волокон.</span><span class="sxs-lookup"><span data-stu-id="7d41a-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7d41a-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7d41a-120">E_FAIL</span></span>|<span data-ttu-id="7d41a-121">Неизвестная Неустранимая ошибка.</span><span class="sxs-lookup"><span data-stu-id="7d41a-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7d41a-122">Если метод вернет значение E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="7d41a-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7d41a-123">Последующие вызовы размещение методы возвращают значение HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7d41a-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d41a-124">Примечания</span><span class="sxs-lookup"><span data-stu-id="7d41a-124">Remarks</span></span>  
 <span data-ttu-id="7d41a-125">Среда CLR вызывает `SetCLRTask` связываемый `ICLRTask` экземпляра с текущим `IHostTask` экземпляр, который был создан с помощью вызова [IHostTaskManager::CreateTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md).</span><span class="sxs-lookup"><span data-stu-id="7d41a-125">The CLR calls `SetCLRTask` to associate an `ICLRTask` instance with the current `IHostTask` instance, which was created by a call to [IHostTaskManager::CreateTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d41a-126">Требования</span><span class="sxs-lookup"><span data-stu-id="7d41a-126">Requirements</span></span>  
 <span data-ttu-id="7d41a-127">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d41a-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d41a-128">**Заголовок:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7d41a-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7d41a-129">**Библиотека:** включена как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7d41a-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7d41a-130">**Версии платформы .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d41a-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d41a-131">См. также</span><span class="sxs-lookup"><span data-stu-id="7d41a-131">See Also</span></span>  
 [<span data-ttu-id="7d41a-132">ICLRTask-интерфейс</span><span class="sxs-lookup"><span data-stu-id="7d41a-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="7d41a-133">ICLRTaskManager-интерфейс</span><span class="sxs-lookup"><span data-stu-id="7d41a-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="7d41a-134">IHostTask-интерфейс</span><span class="sxs-lookup"><span data-stu-id="7d41a-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="7d41a-135">IHostTaskManager-интерфейс</span><span class="sxs-lookup"><span data-stu-id="7d41a-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)