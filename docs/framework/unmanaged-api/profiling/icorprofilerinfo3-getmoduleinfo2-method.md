---
title: "Метод ICorProfilerInfo3::GetModuleInfo2"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3.GetModuleInfo2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3::GetModuleInfo2
helpviewer_keywords:
- ICorProfilerInfo3::GetModuleInfo2 method [.NET Framework profiling]
- GetModuleInfo2 method [.NET Framework profiling]
ms.assetid: f1f6b8f3-dcfc-49e8-be76-ea50ea90d5a7
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 4b891f55ab79d32814f44eabf50343aa113b0835
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo3getmoduleinfo2-method"></a><span data-ttu-id="45d7c-102">Метод ICorProfilerInfo3::GetModuleInfo2</span><span class="sxs-lookup"><span data-stu-id="45d7c-102">ICorProfilerInfo3::GetModuleInfo2 Method</span></span>
<span data-ttu-id="45d7c-103">Возвращает имя файла модуля, идентификатор родительской сборки модуля и битовую маску, описывающую свойства модуля, по идентификатору модуля.</span><span class="sxs-lookup"><span data-stu-id="45d7c-103">Given a module ID, returns the file name of the module, the ID of the module's parent assembly, and a bitmask that describes the properties of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45d7c-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="45d7c-104">Syntax</span></span>  
  
```  
HRESULT GetModuleInfo2(  
    [in]  ModuleID   moduleId,  
    [out] LPCBYTE    *ppBaseLoadAddress,  
    [in]  ULONG      cchName,  
    [out] ULONG      *pcchName,  
    [out, annotation("__out_ecount_part(cchName, *pcchName)")]  
          WCHAR      szName[] ,  
    [out] AssemblyID *pAssemblyId);  
    [out] DWORD                 *pdwModuleFlags);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="45d7c-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="45d7c-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="45d7c-106">[in] Идентификатор модуля, для которого будут извлекаться сведения.</span><span class="sxs-lookup"><span data-stu-id="45d7c-106">[in] The ID of the module for which information will be retrieved.</span></span>  
  
 `ppBaseLoadAddress`  
 <span data-ttu-id="45d7c-107">[out] Базовый адрес, по которому модуль был загружен.</span><span class="sxs-lookup"><span data-stu-id="45d7c-107">[out] The base address at which the module is loaded.</span></span>  
  
 `cchName`  
 <span data-ttu-id="45d7c-108">[in] Длина буфера возврата `szName` в символах.</span><span class="sxs-lookup"><span data-stu-id="45d7c-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="45d7c-109">[out] Указатель на общую длину возвращаемого имени файла модуля в символах.</span><span class="sxs-lookup"><span data-stu-id="45d7c-109">[out] A pointer to the total character length of the module's file name that is returned.</span></span>  
  
 `szName`  
 <span data-ttu-id="45d7c-110">[out] Буфер расширенных символов, предоставленный вызывающим объектом.</span><span class="sxs-lookup"><span data-stu-id="45d7c-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="45d7c-111">При возврате метода этот буфер содержит имя файла модуля.</span><span class="sxs-lookup"><span data-stu-id="45d7c-111">When the method returns, this buffer contains the file name of the module.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="45d7c-112">[out] Указатель на идентификатор родительской сборки модуля.</span><span class="sxs-lookup"><span data-stu-id="45d7c-112">[out] A pointer to the ID of the module's parent assembly.</span></span>  
  
 `pdwModuleFlags`  
 <span data-ttu-id="45d7c-113">[out] Битовая маска значений из [COR_PRF_MODULE_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md) перечисления, указывающего свойства модуля.</span><span class="sxs-lookup"><span data-stu-id="45d7c-113">[out] A bitmask of values from the [COR_PRF_MODULE_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md) enumeration that specify the properties of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45d7c-114">Примечания</span><span class="sxs-lookup"><span data-stu-id="45d7c-114">Remarks</span></span>  
 <span data-ttu-id="45d7c-115">Для динамических модулей параметр `szName` является именем метаданных модуля, а базовый адрес равен 0 (нулю).</span><span class="sxs-lookup"><span data-stu-id="45d7c-115">For dynamic modules, the `szName` parameter is the metadata name of the module, and the base address is 0 (zero).</span></span> <span data-ttu-id="45d7c-116">Имя метаданных — это значение в столбце Name таблицы Module в метаданных.</span><span class="sxs-lookup"><span data-stu-id="45d7c-116">The metadata name is the value in the Name column from the Module table inside metadata.</span></span> <span data-ttu-id="45d7c-117">Оно также предоставляется как <xref:System.Reflection.Module.ScopeName%2A?displayProperty=nameWithType> свойство в управляемый код и как `szName` параметр [IMetaDataImport::GetScopeProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md) клиентский код неуправляемых метаданных.</span><span class="sxs-lookup"><span data-stu-id="45d7c-117">This is also exposed as the <xref:System.Reflection.Module.ScopeName%2A?displayProperty=nameWithType> property to managed code, and as the `szName` parameter of the [IMetaDataImport::GetScopeProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md) method to unmanaged metadata client code.</span></span>  
  
 <span data-ttu-id="45d7c-118">Несмотря на то что `GetModuleInfo2` метод можно вызвать сразу существует идентификатора модуля, идентификатор родительской сборки будет недоступен до получения профилировщиком [ICorProfilerCallback::ModuleAttachedToAssembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="45d7c-118">Although the `GetModuleInfo2` method may be called as soon as the module's ID exists, the ID of the parent assembly will not be available until the profiler receives the [ICorProfilerCallback::ModuleAttachedToAssembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) callback.</span></span>  
  
 <span data-ttu-id="45d7c-119">После возврата метода `GetModuleInfo2` необходимо убедиться, что буфер `szName` был достаточно велик, чтобы вместить в себя полное имя файла модуля.</span><span class="sxs-lookup"><span data-stu-id="45d7c-119">When `GetModuleInfo2` returns, you must verify that the `szName` buffer was large enough to contain the full file name of the module.</span></span> <span data-ttu-id="45d7c-120">Для этого сравните значение, на которое указывает параметр `pcchName`, со значением параметра `cchName`.</span><span class="sxs-lookup"><span data-stu-id="45d7c-120">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="45d7c-121">Если параметр `pcchName` указывает на значение, превышающее значение `cchName`, выделите буфер `szName` большего размера, обновите параметр `cchName`, задав новый, больший размер, и вызовите метод `GetModuleInfo2` снова.</span><span class="sxs-lookup"><span data-stu-id="45d7c-121">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetModuleInfo2` again.</span></span>  
  
 <span data-ttu-id="45d7c-122">Кроме того, сначала можно вызвать метод `GetModuleInfo2` с буфером `szName` нулевой длины для получения правильного размера буфера.</span><span class="sxs-lookup"><span data-stu-id="45d7c-122">Alternatively, you can first call `GetModuleInfo2` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="45d7c-123">Затем можно задать размер буфера равным значению, возвращенному в параметре `pcchName`, и вызвать метод `GetModuleInfo2` снова.</span><span class="sxs-lookup"><span data-stu-id="45d7c-123">You can then set the buffer size to the value returned in `pcchName` and call `GetModuleInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45d7c-124">Требования</span><span class="sxs-lookup"><span data-stu-id="45d7c-124">Requirements</span></span>  
 <span data-ttu-id="45d7c-125">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45d7c-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45d7c-126">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="45d7c-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="45d7c-127">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45d7c-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45d7c-128">**Версии платформы .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45d7c-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45d7c-129">См. также</span><span class="sxs-lookup"><span data-stu-id="45d7c-129">See Also</span></span>  
 [<span data-ttu-id="45d7c-130">ICorProfilerInfo-интерфейс</span><span class="sxs-lookup"><span data-stu-id="45d7c-130">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="45d7c-131">Интерфейсы профилирования</span><span class="sxs-lookup"><span data-stu-id="45d7c-131">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="45d7c-132">Профилирование</span><span class="sxs-lookup"><span data-stu-id="45d7c-132">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)