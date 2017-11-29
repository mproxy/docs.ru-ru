---
title: "Метод ICorDebugStackWalk::SetContext"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStackWalk.SetContext Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStackWalk::SetContext
helpviewer_keywords:
- SetContext method [.NET Framework debugging]
- ICorDebugStackWalk::SetContext method [.NET Framework debugging]
ms.assetid: bac0b156-31a3-4e7f-be4d-ab21789c81f1
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 374092c500d4263a172219c38cbc1b2f0ce293a8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugstackwalksetcontext-method"></a><span data-ttu-id="b0e63-102">Метод ICorDebugStackWalk::SetContext</span><span class="sxs-lookup"><span data-stu-id="b0e63-102">ICorDebugStackWalk::SetContext Method</span></span>
<span data-ttu-id="b0e63-103">Наборы [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) текущего контекста объекта действительный контекст для потока.</span><span class="sxs-lookup"><span data-stu-id="b0e63-103">Sets the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object’s current context to a valid context for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0e63-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b0e63-104">Syntax</span></span>  
  
```  
HRESULT SetContext([in] CorDebugSetContextFlag flag,  
                   [in] ULONG32 contextSize,  
                   [in, size_is(contextSize)] BYTE context[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b0e63-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="b0e63-105">Parameters</span></span>  
 `flag`  
 <span data-ttu-id="b0e63-106">[in] Объект [CorDebugSetContextFlag](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md) флаг, указывающий контекста: взят из активного кадра в стеке или контекст полученных очистить стек.</span><span class="sxs-lookup"><span data-stu-id="b0e63-106">[in] A [CorDebugSetContextFlag](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md) flag that indicates whether the context is from the active frame on the stack, or a context obtained by unwinding the stack.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="b0e63-107">[in] Выделенный размер `CONTEXT` буфера.</span><span class="sxs-lookup"><span data-stu-id="b0e63-107">[in] The allocated size of the `CONTEXT` buffer.</span></span>  
  
 `context`  
 <span data-ttu-id="b0e63-108">[in] `CONTEXT` Буфера.</span><span class="sxs-lookup"><span data-stu-id="b0e63-108">[in] The `CONTEXT` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b0e63-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="b0e63-109">Return Value</span></span>  
 <span data-ttu-id="b0e63-110">Этот метод возвращает следующие конкретные результаты HRESULT, а также ошибки HRESULT, которые указывают на сбой метода.</span><span class="sxs-lookup"><span data-stu-id="b0e63-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="b0e63-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b0e63-111">HRESULT</span></span>|<span data-ttu-id="b0e63-112">Описание</span><span class="sxs-lookup"><span data-stu-id="b0e63-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b0e63-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="b0e63-113">S_OK</span></span>|<span data-ttu-id="b0e63-114">`ICorDebugStackWalk` Был успешно установлен контекст объекта.</span><span class="sxs-lookup"><span data-stu-id="b0e63-114">The `ICorDebugStackWalk` object's context was successfully set.</span></span>|  
|<span data-ttu-id="b0e63-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b0e63-115">E_FAIL</span></span>|<span data-ttu-id="b0e63-116">`ICorDebugStackWalk` Не установлен контекст объекта.</span><span class="sxs-lookup"><span data-stu-id="b0e63-116">The `ICorDebugStackWalk` object's context was not set.</span></span>|  
|<span data-ttu-id="b0e63-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="b0e63-117">E_INVALIDARG</span></span>|<span data-ttu-id="b0e63-118">Значение контекста — null.</span><span class="sxs-lookup"><span data-stu-id="b0e63-118">The context is null.</span></span>|  
|<span data-ttu-id="b0e63-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="b0e63-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="b0e63-120">Выделен слишком малый буфер контекста.</span><span class="sxs-lookup"><span data-stu-id="b0e63-120">The context buffer is too small.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="b0e63-121">Исключения</span><span class="sxs-lookup"><span data-stu-id="b0e63-121">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0e63-122">Примечания</span><span class="sxs-lookup"><span data-stu-id="b0e63-122">Remarks</span></span>  
 <span data-ttu-id="b0e63-123">Этот метод не изменяет текущий контекст потока.</span><span class="sxs-lookup"><span data-stu-id="b0e63-123">This method does not alter the current context of the thread.</span></span>  
  
 <span data-ttu-id="b0e63-124">Установка текущего контекста недопустимого контекста может привести к непредсказуемым результатам при обходе стека.</span><span class="sxs-lookup"><span data-stu-id="b0e63-124">Setting the current context to an invalid context may cause unpredictable results from the stack walker.</span></span>  
  
 <span data-ttu-id="b0e63-125">Побитовое точную копию данного контекста можно получить путем вызова немедленно [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) метод.</span><span class="sxs-lookup"><span data-stu-id="b0e63-125">You can retrieve an exact bitwise copy of this context by immediately calling the [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0e63-126">Требования</span><span class="sxs-lookup"><span data-stu-id="b0e63-126">Requirements</span></span>  
 <span data-ttu-id="b0e63-127">**Платформы:** разделе [требования к системе для](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0e63-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0e63-128">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b0e63-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b0e63-129">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b0e63-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0e63-130">**Версии платформы .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0e63-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0e63-131">См. также</span><span class="sxs-lookup"><span data-stu-id="b0e63-131">See Also</span></span>  
 [<span data-ttu-id="b0e63-132">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="b0e63-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="b0e63-133">Отладка</span><span class="sxs-lookup"><span data-stu-id="b0e63-133">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)