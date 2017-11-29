---
title: "Метод ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyIdentityManager.GetReferencedAssembliesFromFile
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetReferenceAssembliesFromFile method [.NET Framework hosting]
- GetReferenceAssembliesFromFile method [.NET Framework hosting]
ms.assetid: eed63d31-d977-4c7d-9443-f9d37a2a7d81
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: abd80676fe459bd779d5fad4cf2e9c41e140741b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="iclrassemblyidentitymanagergetreferencedassembliesfromfile-method"></a><span data-ttu-id="997d4-102">Метод ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile</span><span class="sxs-lookup"><span data-stu-id="997d4-102">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile Method</span></span>
<span data-ttu-id="997d4-103">Возвращает [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) экземпляр, содержащий список сборок, ссылки из данной сборки по указанному пути.</span><span class="sxs-lookup"><span data-stu-id="997d4-103">Gets an [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) instance that contains a list of assemblies referenced by the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="997d4-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="997d4-104">Syntax</span></span>  
  
```  
HRESULT GetReferencedAssembliesFromFile (  
    [in]  LPCWSTR pwzFilePath,  
    [in]  DWORD   dwFlags,  
    [in]  ICLRAssemblyReferenceList   *pExcludeAssembliesList,  
    [out] ICLRReferenceAssemblyEnum  **ppReferenceEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="997d4-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="997d4-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="997d4-106">[in] Путь к сборке, для оценки.</span><span class="sxs-lookup"><span data-stu-id="997d4-106">[in] The path to the assembly to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="997d4-107">[in] Предоставлен для дальнейшего расширения.</span><span class="sxs-lookup"><span data-stu-id="997d4-107">[in] Provided for future extensibility.</span></span> <span data-ttu-id="997d4-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT является единственным значением, которое поддерживает текущую версию среды common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="997d4-108">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pExcludeAssembliesList`  
 <span data-ttu-id="997d4-109">[in] Указатель на [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) , представляющий сборки, которые должны быть исключены из `ppReferenceEnum`.</span><span class="sxs-lookup"><span data-stu-id="997d4-109">[in] A pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) object that represents assemblies that should be excluded from `ppReferenceEnum`.</span></span>  
  
 `ppReferenceEnum`  
 <span data-ttu-id="997d4-110">[out] Указатель на адрес `ICLRReferenceAssemblyEnum` объект, содержащий данные идентификации сборки для сборки ссылается сборка в `pwzFilePath`, за исключением сборок, представленного `pExcludeAssembliesList`.</span><span class="sxs-lookup"><span data-stu-id="997d4-110">[out] A pointer to the address of an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly at `pwzFilePath`, excluding the assemblies represented by `pExcludeAssembliesList`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="997d4-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="997d4-111">Return Value</span></span>  
  
|<span data-ttu-id="997d4-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="997d4-112">HRESULT</span></span>|<span data-ttu-id="997d4-113">Описание</span><span class="sxs-lookup"><span data-stu-id="997d4-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="997d4-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="997d4-114">S_OK</span></span>|<span data-ttu-id="997d4-115">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="997d4-115">The method returned successfully.</span></span>|  
|<span data-ttu-id="997d4-116">ЗНАЧЕНИЕ HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="997d4-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="997d4-117">Среда CLR не загружена в процесс или находится в состоянии, в котором не может выполнять управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="997d4-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="997d4-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="997d4-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="997d4-119">Истекло время ожидания вызова.</span><span class="sxs-lookup"><span data-stu-id="997d4-119">The call timed out.</span></span>|  
|<span data-ttu-id="997d4-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="997d4-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="997d4-121">Вызывающий объект не является владельцем блокировки.</span><span class="sxs-lookup"><span data-stu-id="997d4-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="997d4-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="997d4-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="997d4-123">Событие было отменено заблокированный поток или ожидал волокон.</span><span class="sxs-lookup"><span data-stu-id="997d4-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="997d4-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="997d4-124">E_FAIL</span></span>|<span data-ttu-id="997d4-125">Неизвестная Неустранимая ошибка.</span><span class="sxs-lookup"><span data-stu-id="997d4-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="997d4-126">Если метод вернет значение E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="997d4-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="997d4-127">Последующие вызовы размещение методы возвращают значение HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="997d4-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="997d4-128">Примечания</span><span class="sxs-lookup"><span data-stu-id="997d4-128">Remarks</span></span>  
 <span data-ttu-id="997d4-129">Вызывающий объект можно исключить набор известных ссылок сборок из этого списка.</span><span class="sxs-lookup"><span data-stu-id="997d4-129">The caller can choose to exclude a set of known assembly references from the returned list.</span></span> <span data-ttu-id="997d4-130">Этот набор определяется `pExcludeAssembliesList` параметра.</span><span class="sxs-lookup"><span data-stu-id="997d4-130">This set is defined by the `pExcludeAssembliesList` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="997d4-131">Требования</span><span class="sxs-lookup"><span data-stu-id="997d4-131">Requirements</span></span>  
 <span data-ttu-id="997d4-132">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="997d4-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="997d4-133">**Заголовок:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="997d4-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="997d4-134">**Библиотека:** включена как ресурс в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="997d4-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="997d4-135">**Версии платформы .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="997d4-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="997d4-136">См. также</span><span class="sxs-lookup"><span data-stu-id="997d4-136">See Also</span></span>  
 [<span data-ttu-id="997d4-137">Iclrassemblyidentitymanager-интерфейс</span><span class="sxs-lookup"><span data-stu-id="997d4-137">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="997d4-138">ICLRAssemblyReferenceList-интерфейс</span><span class="sxs-lookup"><span data-stu-id="997d4-138">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="997d4-139">ICLRReferenceAssemblyEnum-интерфейс</span><span class="sxs-lookup"><span data-stu-id="997d4-139">ICLRReferenceAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)