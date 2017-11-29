---
title: "Метод ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain3.GetCachedWinRTTypesForIIDs
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs
helpviewer_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs method, [.NET Framework debugging]
- GetCachedWinRTTypesForIIDs method, ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 23682ca0-1bcf-48e6-996e-69f7ba337682
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 84b58e3a016431eba10710ea384338cb388404ff
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a><span data-ttu-id="b5fcf-102">Метод ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs</span><span class="sxs-lookup"><span data-stu-id="b5fcf-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Method</span></span>
<span data-ttu-id="b5fcf-103">Возвращает перечислитель для кэшированных [!INCLUDE[wrt](../../../../includes/wrt-md.md)] типов в домене приложения на основе их интерфейс идентификаторов.</span><span class="sxs-lookup"><span data-stu-id="b5fcf-103">Gets an enumerator for cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types in an application domain based on their interface identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5fcf-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b5fcf-104">Syntax</span></span>  
  
```  
HRESULT GetCachedWinRTTypesForIIDs (   
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b5fcf-105">Параметры</span><span class="sxs-lookup"><span data-stu-id="b5fcf-105">Parameters</span></span>  
 `cReqTypes`  
 <span data-ttu-id="b5fcf-106">[in] Количество требуемых типов.</span><span class="sxs-lookup"><span data-stu-id="b5fcf-106">[in] The number of required types.</span></span>  
  
 `iidsToResolve`  
 <span data-ttu-id="b5fcf-107">[in] Указатель на массив, содержащий идентификаторы интерфейса, соответствующего управляемого представления [!INCLUDE[wrt](../../../../includes/wrt-md.md)] типы должны быть получены.</span><span class="sxs-lookup"><span data-stu-id="b5fcf-107">[in] A pointer to an array that contains the interface identifiers corresponding to the managed representations of the [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types to be retrieved.</span></span>  
  
 `ppTypesEnum`  
 <span data-ttu-id="b5fcf-108">[out] Указатель на адрес объекта интерфейса «ICorDebugTypeEnum», позволяет использовать кэшированные перечисления управляемых представления [!INCLUDE[wrt](../../../../includes/wrt-md.md)] типы, полученные на основе идентификаторов интерфейса в `iidsToResolve`.</span><span class="sxs-lookup"><span data-stu-id="b5fcf-108">[out] A pointer to the address of an "ICorDebugTypeEnum" interface object that allows enumeration of the cached managed representations of the [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types retrieved, based on the interface identifiers in `iidsToResolve`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5fcf-109">Примечания</span><span class="sxs-lookup"><span data-stu-id="b5fcf-109">Remarks</span></span>  
 <span data-ttu-id="b5fcf-110">Если метод не может получить сведения для идентификации определенного интерфейса, соответствующую запись в коллекции «ICorDebugTypeEnum» будет иметь тип `ELEMENT_TYPE_END` ошибок из-за проблемы извлечения данных, или `ELEMENT_TYPE_VOID` для Неизвестный интерфейс идентификаторы.</span><span class="sxs-lookup"><span data-stu-id="b5fcf-110">If the method fails to retrieve information for a specific interface identifier, the corresponding entry in the "ICorDebugTypeEnum" collection will have a type of `ELEMENT_TYPE_END` for errors due to data retrieval issues, or `ELEMENT_TYPE_VOID` for unknown interface identifiers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5fcf-111">Требования</span><span class="sxs-lookup"><span data-stu-id="b5fcf-111">Requirements</span></span>  
 <span data-ttu-id="b5fcf-112">**Платформы:**[!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5fcf-112">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span></span>  
  
 <span data-ttu-id="b5fcf-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b5fcf-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b5fcf-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b5fcf-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b5fcf-115">**Версии платформы .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5fcf-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5fcf-116">См. также</span><span class="sxs-lookup"><span data-stu-id="b5fcf-116">See Also</span></span>  
 [<span data-ttu-id="b5fcf-117">Интерфейс ICorDebugAppDomain3</span><span class="sxs-lookup"><span data-stu-id="b5fcf-117">ICorDebugAppDomain3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)